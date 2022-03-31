# 蓝灯模式 (也就是Fastboot模式)

处于该模式时手机呼吸灯为蓝色 , 所以大家都叫做蓝灯模式 ( 应该吧 , 我瞎说的 :D )

特点:

* 需解锁BL
* 解锁后可以刷入任意第三方固件 (前提是适配手机的， 否则...也可以刷, 能不能开机是另一回事 )
* 可以读写底层分区/固件, 但是损坏后几乎必永久变砖, 索尼在底层上的各种验证是我见过的最丧心病狂的... ( 或许作为对比的是LG? )

## 进入Fastboot模式

手机 **关机后** 按住按键 **音量加** ，数据线连接电脑和手机的USB接口

## Fastboot工具

*Windows下需要 [安装驱动](./Driver.md)*

**最新版 platform-tools :**
[Windows](https://dl.google.com/android/repository/platform-tools-latest-windows.zip) ,
[Mac](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip)  ,
[Linux](https://dl.google.com/android/repository/platform-tools-latest-linux.zip)<br>
下载解压后在fastboot所在目录打开终端运行即可  
Windows按住Shift右击即可打开CMD或者PowerShell

Windows PowerShell 需要在命令前加上 .\，比如:

    .\fastboot <具体命令>

非Windows用户建议用自带的软件包管理器从官方源安装  
 ( 绝大多数Linux发行版官方源里都有 )<br>

## 解锁BL

<font color=#FFB6C1 > **部分设备解锁前可以选择备份TA , 具体可以看: [备份TA](./BackupTA.md)** </font>

<font color=#FFB6C1 > **注意：  
&emsp;&emsp;&emsp;解锁了一定会有记录  
&emsp;&emsp;&emsp;解锁后容易导致设备永久损坏  
&emsp;&emsp;&emsp;解锁或将失去官方保修 ( 官方对此的定界比较暧昧 )  
&emsp;&emsp;&emsp;解锁前请三思！！** </font>

解锁前，需先检查设备解锁允许状态:  

* 打开拨号，拨号 **\*#\*#7378423#\*#\*** ( 7378423也就是9键的 Service )
* 在打开的页面依次点击 **Service info** > **Configuration** , 查看 **Rooting Status**
* 如果 **Bootloader unlock allowed** 后是 **Yes** , 则可以解锁  
    如果是 **No** , 则官方不允许解锁, 可以使用第三方工具 **qUnlockTool** 等...变成 **Yes** 后正常解锁  
    如果是 **Yes after SIM UNLOCK** 则在解除网络锁后可正常解锁

## 刷机

fastboot具体使用方法可以调用Fastboot，看Fastboot的介绍

    fastboot --help

这里只列举几个我认为常用的命令:  

    fastboot devices                        # 查看已连接的设备
    fastboot oem unlock 0x<你的解锁码>       # 解锁BL, 0x后面直接输入解锁码，没有<>
    fastboot oem lock                       # 回锁BL ( 仅部分设备可用 )
    fastboot -w                             # 清除数据
    fastboot getvar current-slot            # 查看当前活动分区
    fastboot --set-active=a                 # 切换活动分区为a分区, b同理
    fastboot flash <分区名> <分区文件路径>    # 刷写分区
    fastboot --disable-verity --disable-verification flash vbmeta <官方固件里的vbmeta分区镜像>      # 关闭DM校验

## ROOT ( 可选 )

建议使用开源的 [**Magisk**](https://github.com/topjohnwu/Magisk) 获取和管理Root权限

方法:

   * 从固件或当前系统内提取 boot/kernel 镜像
   * 使用 Magisk APP 修补镜像, 将修补得到的镜像刷到写到 boot 分区
   * 开机后安装 Magisk APP 即可管理 ROOT 权限

## 可能遇到的问题

......
