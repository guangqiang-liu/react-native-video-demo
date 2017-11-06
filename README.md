# 前言
> videoPlayer视频播放器Demo是从作者前段时间开源的RN项目[OneM](https://github.com/guangqiang-liu/OneM)中抽离出来的独立的Demo示例，[如果想看完整的OneM项目请点击](https://github.com/guangqiang-liu/OneM)。Demo示例支持iOS、Android双平台运行。

# 预览效果图
![gif](http://ovyjkveav.bkt.clouddn.com/17-11-6/47022859.jpg)

# 播放器支持功能
* 支持播放 \ 暂停
* 支持横竖屏切换
* 支持锁屏
* 支持缓存播放及缓存进度
* 支持播放进度拖拽到指定位置播放

# 使用到的技术点
* 项目使用到`react-native-video`媒体播放组件
* IconFont字体`react-native-vector-icons`，以及自定义的字体库
* 使用到`react-native-orientation`组件来完成横竖屏切换

# 核心代码
```
<Video source={{uri: url}}
               ref={ref => this.player = ref}
               rate={this.state.rate}
               volume={1.0}
               muted={false}
               paused={this.state.paused}
               resizeMode="cover"
               repeat={true}
               playInBackground={false}
               playWhenInactive={false}
               ignoreSilentSwitch={"ignore"}
               progressUpdateInterval={250.0}
               onLoadStart={(data) => this.loadStart(data)}
               onLoad={data => this.setDuration(data)}
               onProgress={(data) => this.setTime(data)}
               onEnd={(data) => this.onEnd(data)}
               onError={(data) => this.videoError(data)}
               onBuffer={(data) => this.onBuffer(data)}
               onTimedMetadata={(data) => this.onTimedMetadata(data)}
               style={[styles.videoPlayer]}
        />
```

# react-native-video 组件使用讲解

```
<Video source={{uri: "background"}}   // Can be a URL or a local file.
       ref={(ref) => {
         this.player = ref
       }}                                      // Store reference
       rate={1.0}                              // 0 is paused, 1 is normal.
       volume={1.0}                            // 0 is muted, 1 is normal.
       muted={false}                           // Mutes the audio entirely.
       paused={false}                          // Pauses playback entirely.
       resizeMode="cover"                      // Fill the whole screen at aspect ratio.*
       repeat={true}                           // Repeat forever.
       playInBackground={false}                // Audio continues to play when app entering background.
       playWhenInactive={false}                // [iOS] Video continues to play when control or notification center are shown.
       ignoreSilentSwitch={"ignore"}           // [iOS] ignore | obey - When 'ignore', audio will still play with the iOS hard silent switch set to silent. When 'obey', audio will toggle with the switch. When not specified, will inherit audio settings as usual.
       progressUpdateInterval={250.0}          // [iOS] Interval to fire onProgress (default to ~250ms)
       onLoadStart={this.loadStart}            // Callback when video starts to load
       onLoad={this.setDuration}               // Callback when video loads
       onProgress={this.setTime}               // Callback every ~250ms with currentTime
       onEnd={this.onEnd}                      // Callback when playback finishes
       onError={this.videoError}               // Callback when video cannot be loaded
       onBuffer={this.onBuffer}                // Callback when remote video is buffering
       onTimedMetadata={this.onTimedMetadata}  // Callback when the stream receive some metadata
       style={styles.backgroundVideo} />
       
```

### Android拓展用法

```
<Video source={{uri: "background", mainVer: 1, patchVer: 0}} // Looks for .mp4 file (background.mp4) in the given expansion version.
       rate={1.0}                   // 0 is paused, 1 is normal.
       volume={1.0}                 // 0 is muted, 1 is normal.
       muted={false}                // Mutes the audio entirely.
       paused={false}               // Pauses playback entirely.
       resizeMode="cover"           // Fill the whole screen at aspect ratio.
       repeat={true}                // Repeat forever.
       onLoadStart={this.loadStart} // Callback when video starts to load
       onLoad={this.setDuration}    // Callback when video loads
       onProgress={this.setTime}    // Callback every ~250ms with currentTime
       onEnd={this.onEnd}           // Callback when playback finishes
       onError={this.videoError}    // Callback when video cannot be loaded
       style={styles.backgroundVideo} />
```

**详细的`react-native-video`使用方法请参照官方文档：[https://github.com/react-native-community/react-native-video](https://github.com/react-native-community/react-native-video)**

# react-native-video组件使用步骤
* `npm install react-native-video --save`
* `react-native link react-native-video --save`

# 简书详解地址
**[http://www.jianshu.com/p/1c5c36b3c19b](http://www.jianshu.com/p/1c5c36b3c19b)**

# 查看IconFont功能请参考
**[自定义IconFont库](http://www.jianshu.com/p/9f6db8e38852)**

# 同时作者使用*react-native-video*组件也开源了一个音乐播放器Demo示例，有兴趣的同学也可以点击查看学习。
**[http://www.jianshu.com/p/7ddaf6ae9dd2](http://www.jianshu.com/p/7ddaf6ae9dd2)**

# 总结
##### 视频播放器功能和作者开源的音乐播放器差不多，都是使用`react-native-video`组件进行封装的，很多地方的处理逻辑都是一样的，建议同学们两个示例项目结合着学习。如果感觉这篇文章对你有帮助 请 给个 **`star `** 给个**`关注 `** 谢谢。