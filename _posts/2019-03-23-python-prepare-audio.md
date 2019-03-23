---
layout:            post
title:             "python语音处理"
menutitle:         "python语音处理"
category:          "speech signal processing"
author:            chuyu zhang
tags:              原创
---

这是一篇python语音处理基础指南，旨在安装python以及一些语音包。

## python安装
python安装，推荐使用[anaconda](https://www.anaconda.com/),它与matlab十分相似，对matlab使用者很友好。此外，anaconda预装了很多库，例如科学计算需要的numpy、pandas，机器学习需要的scikit-learn，对初学者很友好，深度学习库需要自己安装，十分简单，后续会介绍。

安装过程中，它会提示你是否安装vscode，建议安装，这个开发环境十分的简洁，后续python熟练后，就可以抛弃anaconda自带开发环境spyder，转向vscode，另外也可以转向pycharm，后者强烈推荐。

安装完成后，它会安装四个东西，如下图：
<figure>
   <img src="{{ "/media/img/anaconda.jpg" | absolute_url }}" />
</figure>

anaconda navigator:图像化环境管理工具，可以通过这个安装库，比较方便，可以批量安装，缺点就是很多库没有，因为它是通过Anaconda Cloud搜索库的，本篇blog不使用这个。

anaconda prompt:一个终端，类似于windows的cmd。这里用这个安装库，先打开它，不输入任何命令，后续使用。

spyder：anaconda自带的集成开发环境。

jupyter-notebook：十分强大的工具，网上很多代码教程使用这个。它可以让你在浏览器中写代码，对于数据挖掘来说，要学会使用它，能极大的帮助完成数据可视化任务。这里不介绍

## pip 与 conda介绍
在安装库之前，先来介绍一下pip与conda，不多说，上链接，[点我](https://www.toutiao.com/i6632773927758201347/).

## 语音库
这里使用pip安装，conda安装也差不多。具体安装：pyAudio,pyAudioAnalysis，DTW.
先到[pypi](https://pypi.org/),搜索需要安装的包，例如搜索pyAudioAnalysis:
<figure>
   <img src="{{ "/media/img/pypi.JPG" | absolute_url }}" />
</figure>

点击search，就能得到搜索结果，在结果中选择你需要的库，点击进去：
<figure>
   <img src="{{ "/media/img/pypi_result.JPG" | absolute_url }}" />
</figure>

**注意：右边latest version要留意，有时候不是最新版，需要自己点击一下**，这个作者有点懒，没有给文档。一般这些库，都会在github上放源码，注意左下角的Homepage。

复制**pip install xxxx** 这行代码，前面打开了anaconda prompt，直接将代码复制执行即可。
如果成功了，那就可以调用试试了，没有成功的话，两种解决办法。

1. 百度谷歌找解决方案，要相信不是你一个人踩坑。
2. 点击Homepage，到它的官网看一下说明，有时候他会要求一些依赖库，按照它的说明，安装依赖。

遇到bug，按照上述两种方法解决。

安装过程中，会出现hmmlearn不能编译，参考这个安装[hmmlearn 安装](https://blog.csdn.net/qq_39516859/article/details/80178751),注意修改你安装的hmmlearn版本，就可以。

## 深度学习库（可选）
前面提到深度学习库，这里就安装一下，目前深度学习有几个流行的库，tensorflow、pytorch等等，这里以tensorflow为例。
安装tensorflow之前，先到它的官网瞅瞅，[点这里](https://tensorflow.google.cn/),好了，你自己看官网安装吧，哈哈。
之前看到过，说用conda安装tensorflow会好些，[点这里](https://zhuanlan.zhihu.com/p/46599887)。
