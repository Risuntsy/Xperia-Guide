# 蓝灯模式 (也就是Fastboot模式)

处于该模式时手机呼吸灯为蓝色 , 所以大家都叫做蓝灯模式 ( 应该吧 , 我瞎说的 :D )

特点:

* 需 [解锁BL](#解锁bl)
* 解锁后可以刷入任意第三方固件 (前提是适配手机的， 否则...也可以刷, 能不能开机是另一回事 )
* 可以读写底层分区/固件, 但是损坏后几乎必永久变砖, 索尼在底层上的各种验证是我见过的最丧心病狂的... ( 或许作为对比的是LG? )

## 查看设备解锁允许

解锁前，需先检查设备解锁允许状态:  

* 打开拨号，拨号 **\*#\*#7378423#\*#\*** ( 7378423也就是9键的 Service )
* 在打开的页面依次点击 **Service info** > **Configuration** , 查看 **Rooting Status**
* 如果 **Bootloader unlock allowed** 后是 **Yes** , 则可以解锁  
    如果是 **No** , 则官方不允许解锁, 可以使用第三方工具 **qUnlockTool** 等...变成 **Yes** 后正常解锁  
    如果是 **Yes after SIM UNLOCK** 则在解除网络锁后可正常解锁

## 部署ADB&&Fastboot环境

*Windows下需要 [安装驱动](./Driver.md)*

**最新版 platform-tools :**
[Windows](https://dl.google.com/android/repository/platform-tools-latest-windows.zip) ,
[Mac](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip)  ,
[Linux](https://dl.google.com/android/repository/platform-tools-latest-linux.zip)<br>
点击蓝色链接下载，解压后在fastboot所在目录打开终端运行即可  
( 可选 ) [Windows添加环境变量](https://sspai.com/post/40471)  
Windows按住Shift右击即可打开CMD或者PowerShell  
在打开的终端里输入命令即可  
Windows PowerShell 需要在命令前加上 .\，比如:

    .\fastboot <具体命令>

Linux用户建议用自带的软件包管理器从官方源安装  
 ( 绝大多数Linux发行版官方源里都有 )  

## 进入Fastboot模式

Fastboot相关的操作都是手机在Fastboot模式下进行的  
进入Fastboot模式:  
手机 **关机后** 按住按键 **音量加** ，数据线连接电脑和手机的USB接口 , 待手机呼吸灯变成**蓝色** 并且能在连接的USB设备里找到你的设备，就连接成功了

## 解锁

* [确定自己的设备可以解锁](#查看设备解锁允许)
* 到 [索尼官网](https://developer.sony.com/develop/open-devices/get-started/unlock-bootloader) 获取解锁码  
    * 需要科学上网，否则可能出现人机验证且一直失败
    * 翻到网站最底下选择机型  (其实随便选择也行...都是同样的算法生成的)  
    * 输入IMEI，确保你已经知道解锁可能带来的风险后勾选下面的选项，随后点击提交（Submit）按钮  
* 打开 **开发者选项** 里面的 **OEM解锁** 选项  
如果你的OEM解锁选项是灰色的，请确保你没有冻结Google Play相关组件并在确保 **网络可用** 后打开Play商店等待加载 ( 无需登录账号 ) ，之后再尝试打开OEM解锁  
* 解锁命令: 

        fastboot oem unlock 0x<你的解锁码>


## Fastboot 刷机

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
     可以直接提取Boot分区或者解包固件中的boot/kernel .sin
   * 使用 Magisk APP 修补镜像, 将修补得到的镜像刷写到 boot 分区
   * 开机后安装 Magisk APP 即可管理 ROOT 权限

## 可能遇到的问题

......
