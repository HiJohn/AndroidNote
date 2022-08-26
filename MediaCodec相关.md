# MediaCodec相关

MediaMuxer 以及 MediaCodec MediaExtractor 的用法相关 MediaExtractor 一般步骤：&#x20;

1.设置数据源 setDataSource&#x20;

2.分离轨道 getTrackCount，getTrackFormat&#x20;

3.选择轨道 selectTrack，unselectTrack&#x20;

4.读取数据 readSampleData

5.下一帧 advance&#x20;

6.释放 release

MediaMuxer 一般步骤： 1.//添加轨道 addTrack 2.写数据 writeSampleData 3.释放 release

![image](https://github.com/HiJohn/SeekBarTest/raw/master/mediaCodec.jpg) ![image](https://github.com/HiJohn/AndroidNote/raw/master/MediaCodecWorkFlow.png)
