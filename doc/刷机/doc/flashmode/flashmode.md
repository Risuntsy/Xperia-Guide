# 绿灯模式 (SOMC FlashMode)

因为处于该模式时手机呼吸灯为绿色，所以很多人叫绿灯模式 （ 我猜的 **:D**

----

## 特点:
   * 无需解锁
   * 只能刷除了DO版本外的同索尼的处理器平台的 **官方固件** ，索尼打包的SIN文件包含固件签名，绿灯通信时会验证  
   *日版DO版本似乎修改了绿灯的验证  
   *日本地区的运营商定制版都支持Felica，与其他地区的不同，(之前) 协议也不兼容，所以会出现日版机器刷了其他地区的固件导致NFC没用、不能深度睡眠，甚至随机重启的问题
   * 绿灯下可以读写部分TA单元

## 进入绿灯模式

关机状态下按住 **音量减** 键用数据线连接手机和电脑

## 可选择的刷机工具

*( 点击蓝色链接查看具体使用方法 )*

*   [xflasher](./FlashModeTools/xFlasher.md)  
    仅支持17年之前的设备

*   [newflasher](./FlashModeTools/newflasher.md) (建议支持的设备使用)  
    仅支持17年及之后的设备

*   [FlashTool](./FlashModeTools/FlashTool.md)  
    界面友好, 但有些兼容性问题, 且年久失修

*   [Xperia Companion](./FlashModeTools/Xperia%20Companion.md)  
    索尼官方的刷机工具, 仅支持BL锁定的设备

*   [Sony Emma](./FlashModeTools/Sony%20Emma.md)  
    索尼官方的刷机工具, 仅支持已解锁BL的设备, 一般只有公开版设备的固件, 且型号不全
