一直很想学一下写手机App，但一直对ios、android讳莫如深，不敢下手，最近偶闻RN能一统江湖，顿时来了兴趣。

一、Emulator（非必须）

由于跟电信签了个三年协议，因此不得继续使用Le X620（祝贾老板好运），但这个手机似乎有点问题，连上电脑总不能被识别，于是决定搭个模拟器（Emulator）。

一开始想的是官方方案，安装Android Studio，可怜我的X200（尽管已经SSD+8GRAM)跑个模拟器基本就处于半废状态了，于是就只能另辟蹊径了，我是个不想重复劳动的人，因此就想到用Docker容器来建一个，感谢Docker-Android（ https://github.com/butomo1989/docker-android ）提供了一个案例，经过一番折腾，终于搭出了一个模拟器，甚至也可以在上面跑个简单的RN程序。

由于docker容器耗费系统资源（8C16G）较大，仍然卡的不行，所以还得想别的办法。

二、Expo

后经人介绍，有一工具可以简化RN程序编译发布过程，叫做Expo：（参考 https://www.jianshu.com/p/abfb55c60684）

Expo is a free and open source toolchain built around React Native to help you build native iOS and Android projects using JavaScript and React.

费九牛二虎之力下齐create-react-native-app和expo client app, 于是开启了我的手机App开发之旅。

Expo详细使用请参考官网文档： https://docs.expo.io/versions/latest/index.html

参考 https://github.com/ajchambeaud/video-recorder 作了个视频播放和录制的App（调试中......)。

在使用过程中遇到几个问题，在此备注一下：

1.异常： Error: Watchman error: A non-recoverable condition has triggered.  Watchman needs your help!
The triggering condition was at timestamp=1520319521: inotify-add-watch(/root/github/video-recorder/node_modules/lottie-react-native/src/android/build/tmp/expandedArchives/classes.jar_5gdp4bb5izj6gs3qq6f6ejit7/com/facebook/react/module/annotations) -> The user limit on the total number of inotify watches was reached; increase the fs.inotify.max_user_watches sysctl
All requests will continue to fail with this message until you resolve

解决：

$ watchman watch-del-all

$ watchman shutdown-server

在Mac或Linux环境下使用Expo，需要安装watchman,有时会出现上述异常，请参考解决


2. 由于我安装的是"expo": "25.0.0"（最新版本）、"react": "16.2.0"、"react-native": "0.52.0", Github上很多例子用的是不同版本，因此需要调整package.json和app.json文件，最好的办法是用create-react-native-app建一个空项目专门用来比较这两个文件，以便对这两个文件做调整。









