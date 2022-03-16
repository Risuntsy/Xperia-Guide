  - **从Xperifirm上下载你对应地区的固件，Windows下需提前装好绿灯(FlashMode)驱动**  
     **如果你想用newflasher刷打包成FTF格式的固件，需要一些改动**
  - **连接数据线到电脑，且同时在手机关机的状态下按住音量减连接电脑**
  - **待手机呼吸灯变成绿灯，Windows可以到设备管理器里找到SMOC Flash Device，你的手机就连接成功了**
  - **去下载最新版“newflasher”，把压缩包里对应系统(比如Windows/arm64安卓/Linux-x64/Mac应使用的对应的后缀是exe/arm64/x64/darwin64)的newflasher放到固件文件夹里**
  - **直接运行newflasher程序，或者在终端里运行。**
  - **直到程序跑完且没有报错，就可以拔下数据线开机了**

----
注意: 
  * 检查固件内是否带simlock，如果有删掉再刷机。
  * 如果你想保留数据强刷，清除数据是appslog_X.sin，dag_X.sin，Qnovo_X.sin，ssd_X.sin和userdata_X.sin。把这几个删掉再刷。
  * 如果你想正常获得OTA，那么需要把所有文件都刷了（<color #ed1c24>**1II以及以后的机型，跨地区刷固件无法接收OTA，并且确保自己的所刷固件版本号大于或者等于自己机型的版本号，否则黑砖**</color>）


