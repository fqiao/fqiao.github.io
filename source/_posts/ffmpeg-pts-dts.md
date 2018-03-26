---
title: 浅析pts、dts以及time_base
tags:
  - FFMPEG
categories:
  - FFMPEG
year: 2018
month: 3
day: 26
thumbnail: 'http://img.blog.csdn.net/20151123175857395'
date: 2018-03-26 18:09:52
---


![](http://i1-news.softpedia-static.com/images/news-700/FFmpeg-2-0-1-Officially-Released.png)

PTS：Presentation Time Stamp.PTS主要用于度量解码后的视频帧什么时候被显示出来
DTS：Decode Time Stamp.DTS主要是标识读入内存中的bit流在什么时候开始送入解码器中进行解码
即PTS表示帧什么时候开始显示,DTS表示数据流什么时候开始解码

<!-- more -->
对于新手而言，这里有一个坑：假如我有一帧视频要在第5秒显示，他的pts就是5，这里千万不能这么想。在解释原因之前我们先来认识一下time_base

### time_base
time_base你可以这样理解：就是为了获取更精确的时间，把1s分为N份，那么每一份的时间长度就是1/N,那么此时time_base=[1,N]。所谓的time_base就是每一份的时间长度。

### pts， dts
pts或者dts就代表占用了多少份
也只有知道了pts或者dts和time_base才能精确的获取时间。
在ffmpeg中，av_q2d(time_base) == 每份为多少秒应该也不难理解 pts *  av_q2d(time_base) 才是某一帧的显示时间戳