﻿# musicpy

[[中文](README.md)][English]

### Ever wondered making music with codes?

I've been working on many python libraries in my spare time, including those for statistics, games and music. In fact I've been trying to write something for AI but that's only in the early phase. Today I wanna introduce to you a library that lets you write music with code: **musicpy**.

This library enables you to express a sequence of notes and beats in a music piece with very clean and simple syntax, along with the ability to output as midi format with ease. I recommend using this library with some pre-knowledge about music theory so it would not make confusion. On the other hand, you should be able to play around with them after having a look at this [wiki](https://github.com/Rainbow-Dreamer/musicpy/wiki) I wrote if you are familiar with music theory.

Installation：

Make sure you have at least python 3.6 installed first.  
Execute the following command in the terminal.

```shell
pip install musicpy
```
Importing:

Place this line at the start of the files you want to have it used in.

```python
from musicpy import *
```

Introduction and Tutorial video series part 1: [BV1754y197a9](https://www.bilibili.com/video/BV1754y197a9/) (The current version of musicpy is very different to that in the tutorial. I'll remake this tutorial some time to keep it updated)

Demo of writing music with musicpy: [BV18z4y1r7Pk](https://www.bilibili.com/video/BV18z4y1r7Pk/)

musicpy's data sturctures, basic syntax and usage is detailed in this [wiki](https://github.com/Rainbow-Dreamer/musicpy/wiki), I'll try to make sure everything is detailed and clear. 

`note`, `chord`, `scale` are the basic classes in musicpy that builds up the base of music programming.

Because of musicpy's data structure design, the `note` class is congruent to integers, which means that it can be used as int directly.

The `chord` class is the set of `note`s, which means that it itself can be seen as a set of integers, a vector, or even a matrix (e.g. a set of chord progressions can be seen as a combination of multiple vectors, which results in a form of matrix with lines and columns indexed)

Because of that, `note`, `chord` and `scale` classes can all be arithmetically used in calculation, with examples of Linear Algebra and Discrete Mathmetics. It is also possible to write an algorithm following music theory logics using this library's data structure, or to perform experiments on music with the help of pure mathematics logics.

Many experimental music styles nowadays, like serialism, aleatoric music, postmodern music (like minimalist music), are theoretically possible to make upon the arithmetically performable data structures provided in this library. Of course this library can be used to write any kind of classical music, jazz, or pop music.

I make updates to this library about every three days. You can checkout this [changelog](./更新日志Changelog.txt) for detailed and fully explained new features sorted by date.

我开发这个语言主要的初衷有两点，第一，比起工程文件和 midi 文件单纯存储音符，力度，速度等单位化的信息，如果能够按照乐理上的角度来表示一段音乐从作曲上的角度是如何实现的，那就更加有表示的意义了。而且只要不是现代主义无调性音乐，大部分的音乐都是极其具有乐理上的规律性的，这些规律抽象成乐理逻辑语句可以大大地精简化。（比如一个 midi 文件 1000 个音符，实际上按照乐理角度可能可以简化到几句代码）。第二，开发这个语言是为了让作曲 AI 能够在真正懂得乐理的情况下来作曲（而不是深度学习，喂大量的数据），这个语言也算是一个接口，AI 只要把乐理的语法搞懂了，那作曲就会拥有和人一样的思维。我们可以把乐理上的规则，做什么好不做什么好告诉 AI，这些东西还是可以量化的，所以这个乐理库也可以作为一个乐理接口，沟通人和 AI 之间的音乐。因此，比如想让 AI 学习某个人的作曲风格，那么在乐理上面也同样可以量化这个人的风格，每种风格对应着一些不同的乐理逻辑规则，这些只要写给 AI，经过我这个库，AI 就可以实现模仿那个人的风格了。如果是 AI 自己原创风格，那就是从各种复杂的作曲规则里寻找可能性。

我在想不用深度学习，神经网络这些东西，直接教给 AI 乐理和某个人的风格化的乐理规则，那么 AI 或许可以做的比深度学习大数据训练出来的更好。因为大数据训练只是给 AI 模仿数据本身而已，这样其实 AI 并没有真正地和人类自己一样理解作曲是什么，乐理是什么，所以我才想通过这个库实现把人的乐理同样教给 AI，让 AI 真正意义上地理解乐理，这样的话，作曲起来就不会生硬了，没有机器和随机的感觉了。所以我写这个库的初衷之一就是避开深度学习那一套。但是感觉抽象出不同音乐人的乐理规则确实很有难度，我会加油写好这个算法的qwq 另外其实也可以音乐人自己告诉 AI 他自己乐理上喜欢怎么写（也就是自己独特的乐理偏好规则），那么 AI 就会模仿的很到位，因为 AI 那时候确实懂得乐理了，作曲不可能会有机器感和随机感，此时 AI 脑子里想的就和音乐人脑子里想的是完全一样的东西。

AI 不必完全按照我们给他的乐理逻辑规则来创作，我们可以设置一个“偏好度”的概念给 AI，AI 在自己作曲时会有一定程度地偏好某种风格，但是除此之外会有自己在“符合正确乐理”的规则里面找到的独特的风格，这样 AI 就可以说“受到了某些音乐人的影响下自己原创的作曲风格了”。当这个偏好度为 0 时，AI 的作曲将会完全是自己通过乐理寻找到的风格，就像一个人自己学习了乐理之后，开始摸索自己的作曲风格一样。一个懂得乐理的 AI 很容易找到自己独特的风格来作曲，我们甚至都不需要给他数据来训练，而只要教给 AI 乐理就行。

那么怎么教给 AI 乐理呢？在音乐上面，暂时不考虑现代主义音乐的范畴，那么绝大部分的音乐都是遵循着一些很基本的乐理规则的。这里的规则指的是，怎么样写乐理上 OK，怎么样写犯了乐理上的错误。比如写和声的时候，四部同向往往是要避免的，尤其是在编曲时写管弦乐的部分。比如写一个和弦，如果和弦里面的音出现小二度（或者小九度）会听着比较打架。比如当 AI 自己决定一首曲子要从 A 大调开始写，那么他应该从 A 大调音阶里按照级数来选取和弦，有可能适当地离调一下，加几个副属和弦，写完主歌部分可能按照五度圈转个调，或者大三度/小三度转调，同主音大小调转调等等。我们需要做的事情就是告诉 AI 作曲的时候怎么写是正确的，更进一步的，怎么写听着比较有水平。AI 学好了乐理，不会忘记，也比较难犯错，因此可以写出真正属于 AI 自己的音乐。他们会真正懂得音乐是什么，乐理是什么。因为这个库的语言做的事情就是把乐理抽象成逻辑语句，那么我们每次给 AI “上课”，就是把人自己的乐理概念用这个库的语言来表述，然后写进 AI 的数据库里。通过这种方式，AI 真正的学习到了乐理。这样的作曲 AI，不需要深度学习，不需要训练集，不需要大数据，而与之相比，那些深度学习训练出来的作曲 AI 实际上根本就不懂乐理是什么，也没有音乐的概念，他们只是从海量的训练数据里面照葫芦画瓢而已。还有一个重点是，既然可以用具体的逻辑来描述的事情，其实是不需要机器学习的。如果是文字识别，图像分类这些比较难以用抽象的逻辑来描述的事情，那才是深度学习的用武之地。

这个库我也上传到 pypi 上了，大家 `pip install musicpy` 就可以使用了。

我从去年的 10 月份开始开发 musicpy，目前这个项目还在初期进度，不过已经有一套比较完整的乐理逻辑语法了。这个库的使用教程视频我会持续更新。我之前发的专栏也有一部分的使用教学。

感谢大家的支持~
