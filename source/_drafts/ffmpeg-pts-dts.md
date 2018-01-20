---
title: 浅析pts、dts以及time_base
tags:
- FFMPEG
categories:
- FFMPEG
year: 2018
month: 03
day: 26
thumbnail: http://img.blog.csdn.net/20151123175857395
---

![](http://i1-news.softpedia-static.com/images/news-700/FFmpeg-2-0-1-Officially-Released.png)

PTS：Presentation Time Stamp.PTS主要用于度量解码后的视频帧什么时候被显示出来
DTS：Decode Time Stamp.DTS主要是标识读入内存中的bit流在什么时候开始送入解码器中进行解码
即PTS表示帧什么时候开始显示,DTS表示数据流什么时候开始解码

<!-- more -->

### pts

### dts

### time_base