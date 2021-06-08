# FFmpeg

## 简介

FFmpeg是一个用C写的多媒体框架。

## 概念

帧

- I帧 关键帧，包含完整数据
- P帧 向前预测帧，需要和之前的帧一起才能解码出完整数据
- B帧 双向预测帧，需要和前后的帧一起配合

时间戳

- PTS 播放时间戳
- DTS 解码时间戳

## 应用

### 音视频同步

一般是基于音频或者视频的PTS，由一个向另一个靠拢。常见的就是用音频做完基准，让视频去靠拢。

## 参考

- [About FFmpeg](http://ffmpeg.org/about.html)
- [Android FFmpeg系列——5 音视频同步播放_JohanMan的博客-CSDN博客](https://blog.csdn.net/JohanMan/article/details/83176144)