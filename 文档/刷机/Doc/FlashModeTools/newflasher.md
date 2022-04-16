0. 安装绿灯(FlashMode)驱动(仅Windows需要)
1.  ( 建议 ) 从Xperifirm上下载对应型号的固件  
如果你想用newflasher刷打包成FTF格式的固件，需要一些改动[<sup> 1</sup>](#refer-anchor-1)
2. 去下载<font color=#FFB6C1 > 最新版 </font> [newflasher](https://forum.xda-developers.com/t/tool-newflasher-xperia-command-line-flasher.3619426/) ，把压缩包里对应系统的newflasher程序放到固件文件夹里  
(比如Windows/arm64安卓/Linux-x86_64/Mac 应使用的对应的后缀是exe/arm64/x64/darwin64)
3. 连接数据线到电脑, 手机完全关机后按住<font color=#FFB6C1 > 音量减 </font>连接数据线
4. 待手机呼吸灯变成绿灯，且能在连接的usb设备里找到你的设备，就连接成功了，Windows可以到设备管理器里找到SMOC Flash Device
5. (仅Windows)运行newflasher程序，或者在终端里运行。根据newflasher提示刷机
6. newflasher刷完会自动将设备启动到一开始选择的模式 (部分设备似乎没效果...) ，如果刷完没有报错也没有重启可以拔掉数据线手动重启...

----

注意:  

  * 永远用最新版本 newflasher !
  * 使用newflasher刷写固件不需要删除任何文件（可能影响手机功能的newflasher会自动跳过）
  * Xperifirm下载的固件无需任何改动
  * 如果你想保留数据强刷，**最新版** newflasher会询问是否跳过刷写userdata，根据提示刷机即可, 或者手动删掉userdata_***_X.sin再刷
  * 如果你想正常获得OTA，需要刷 **完整固件** ( <font color=#FFB6C1 > **1II以及以后的机型，跨地区刷固件无法接收OTA，并且确保自己的所刷固件的安全补丁版本大于或者等于自己现在的版本，否则不开机，只能刷回最新版固件** </font> )
  * **骁龙888处理器平台的设备*<font color=#FFB6C1 > 可能 </font> ( 至少1 III上要，5 III 和 Pro I 如果刷完固件不开机可以试试 )* 需先将活动分区切换到a分区[<sup> 2 </sup>](#refer-anchor-2)再刷写固件，否则不开机

----

<div id="refer-anchor-1"></div>

1. 用newflasher刷写ftf格式的固件：  
    * 把FTF后缀名改成zip并解压
    * <font color=#FFB6C1> 如果 </font>有 *boot.zip* 或 *partition.zip* 先解压文件到对应文件夹  
    比如boot.zip中的文件解压到固件目录的 *boot* 文件夹，没有文件夹就手动创建
    * 把固件目录下面 ***boot_delivery.xml*** 和 ***partition_delivery.xml*** 移动到对应的boot和partition文件夹中 , 如果没有 ***partition_delivery.xml*** 的话需要到同型号的固件里拿 , 否则newflasher不会刷写partition的内容 , 这样刷的固件是不完整的，且会导致各种问题  
    *比如 : 相机无法对焦，解锁状态丢失，随机重启，收不到 OTA更新或者 OTA更新失败*  
    （个人理解，如果有错还请指出）  

<div id="refer-anchor-2"></div>

2. 切换活动分区  

    在终端调用具体程序即可

    绿灯下调用newflasher ( 无需解锁 ) : 

        newflasher set_active:a

    蓝灯下调用fastboot ( 需解锁BL ) :

        fastboot --set-active=a      #切换活动分区为a

