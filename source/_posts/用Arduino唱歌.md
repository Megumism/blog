---
title: 用Arduino唱歌
index_img: /img/covers/default.jpg
categories: 技术文档
date: 2020-04-09 21:34:15
tags:
  - C++
  - Arduino
---

有音响的地方，就应该有 Bad Apple。

<!--more-->

## 理论

&emsp;&emsp;按照**十二平均律系统**，我们可以以 f 为基准音，在区间[f,2f]内得到 13 个不同的单音，它们的频率分别为：$f\times2^{\frac{0}{12}}$，$f\times2^{\frac{1}{12}}$，…，$f\times2^{\frac{12}{12}}$，f 可以视为 $f\times2^{\frac{0}{12}}$，2f 可以视为 $f\times2^{\frac{0}{12}}$。如果将 f 设定为 440Hz **(即中央 C 右侧的第一个 A)**，从 f 到 2f 这 13 个单音的频率就可以用前述公式算出。

另外附上一个 88 键频率对照表：<http://www.360doc.com/content/17/1219/11/913305_714446291.shtml>

## 实现代码

主调映射：

```Cpp
enum TONE {C,UC,D,UD,E,F,UF,G,UG,A,UA,B};
int ToneX(enum TONE main, int SoundIN, bool up) //主调映射函数
{
    int Sound2Tone;
    int Sound2Height;
    int SoundOUT;
    if (SoundIN >= 0){
        Sound2Tone = SoundIN % 10;
        Sound2Height = SoundIN / 10;
    }
    else{
        Sound2Tone = (-SoundIN) % 10;
        Sound2Height = -(((-SoundIN) / 10) + 1);
        // Serial.println(Sound2Tone);
        // Serial.println(Sound2Height);
    }
    //从简谱到五线谱的映射
    if (Sound2Tone == 1)
        Sound2Tone = 0;
    else if (Sound2Tone == 2)
        Sound2Tone = 2;
    else if (Sound2Tone == 3)
        Sound2Tone = 4;
    else if (Sound2Tone == 4)
        Sound2Tone = 5;
    else if (Sound2Tone == 5)
        Sound2Tone = 7;
    else if (Sound2Tone == 6)
        Sound2Tone = 9;
    else if (Sound2Tone == 7)
        Sound2Tone = 11;
    SoundOUT = main - A + up + Sound2Tone + Sound2Height * 12;
    //主调-A调（因为以fA=440Hz计算的音律）+升调+距离中央A的距离
    return int(pow(2, SoundOUT / 12.0) * 440.0 + 0.5);
    //这里加0.5实现四舍五入
}
```

歌唱处理：

```Cpp
//
void Sing(enum TONE Main, float Song[], int length, int beat)
//主调 歌谱数列 歌谱长度 最小单元长度（ms）
{
    int sing;
    bool up;
    for (int i = 0; i < length; i++)
    {
        if (Song[i] != 0)
        {
            if (int(Song[i] * 2) % 2)
            //这里判断传进来的数字有没有0.5的尾数，如果有，升半调
                up = true;
            else
                up = false;
            sing = Song[i];
            tone(singer, ToneX(Main, sing, up));
        }
        else
            noTone(singer);//休止
        delay(beat);
    }
}
```

最后附上歌谱：
源地址<https://www.qinyipu.com/jianpu/jianpudaquan/32121.html>

```cpp
Sing(UF, sizeof(BadApple) / sizeof(BadApple[0]), length, 210);
//当然这个放到数组后面去，这里提前是为了看的方便
//另外要注意，一定要除一个sizeof(a[0])，不然就等着溢出吧
float BadApple[] = {
    -6, -7, 1, 2, 3, 3, 6, 5,
    3, 3, -6, -6, 3, 2, 1, -7,
    -6, -7, 1, 2, 3, 3, 2, 1,
    -7, -6, -7, 1, -7, -6, -5.5, -7,

    -6, -7, 1, 2, 3, 3, 6, 5,
    3, 3, -6, -6, 3, 2, 1, -7,
    -6, -7, 1, 2, 3, 3, 2, 1,
    -7, -7, 1, 1, 2, 2, 3, 3,

    5, 6, 3, 2, 3, 3, 2, 3,
    5, 6, 3, 2, 3, 3, 2, 3,
    2, 1, -7, -5, -6, -6, -5, -6,
    -7, 1, 2, 3, -6, -6, 3, 5,

    5, 6, 3, 2, 3, 3, 2, 3,
    5, 6, 3, 2, 3, 3, 2, 3,
    2, 1, -7, -5, -6, -6, -5, -6,
    -7, 1, 2, 3, -6, -6, 3, 5,

    5, 6, 3, 2, 3, 3, 2, 3,
    5, 6, 3, 2, 3, 3, 2, 3,
    2, 1, -7, -5, -6, -6, -5, -6,
    -7, 1, 2, 3, -6, -6, 3, 5,

    5, 6, 3, 2, 3, 3, 2, 3,
    5, 6, 3, 2, 3, 3, 6, 7,
    11, 7, 6, 5, 3, 3, 2, 3,
    2, 1, -7, -5, -6, -6, 3, 5};
```
