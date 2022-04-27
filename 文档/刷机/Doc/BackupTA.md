# 备份TA

## 什么是TA ?

TA 是 **所有** 索尼手机都有的一个[分区](https://segmentfault.com/a/1190000021601415)，里面存储了一些 **非常重要的** 手机信息和数据  
比如:

* **手机的唯一标识信息**，包括但不仅限于型号、版本(零售/测试)、IMEI、手机颜色、SIMLOCK (包括解锁允许)、运营商/地区等等
* **[DRM](https://zh.wikipedia.org/wiki/%E6%95%B0%E5%AD%97%E7%89%88%E6%9D%83%E7%AE%A1%E7%90%86) 密钥**，用于访问索尼的一些专有功能，比如视频增强和相机图像处理的算法等等  
* 与Bootloader?相关的一些验证
* 各种日志记录

----

## 为什么要备份TA ?

使用官方手段解锁Bootloader会 **不可避免** 地造成DRM密钥丢失，这会导致包括上面所说的一些专有功能失效。  
比如DRM 等级 L3 Netflix 不能看1080P影片  
幸运的是，我们可以使用某些手段[备份和恢复TA分区](#备份和恢复ta)，或者使用[DRM修复补丁](#drm修复补丁)

----

## 备份和恢复TA

注意:


<font color=#FFB6C1 > <b> 注意：   
*  骁龙845处理器平台的设备 ( 即XZ2、XZ2C、XZ2P、XZ3 )即使备份且恢复了TA，DRM功能也不能使用  
*  骁龙855以及之后的处理器平台的设备 ( 即Xperia 1/5以及之后 ) 的设备 **没有必要** 备份TA, 使用fastboot回锁后会恢复DRM密钥  
( 甚至隐藏解锁状态就可以正常使用部分功能 </b> </font>

[Dirtycow-based TA Dumper for Sony Xperia Devices. (v2.0)](https://forum.xda-developers.com/t/universal-dirtycow-based-ta-backup-v2.3514236/)  
可用于:  

* Xperia Z1  
* Xperia ZL  
* Xperia Z2  
* Xperia Z3  
* Xperia Z5  
* Xperia Z5 Compact  
* Xperia E5  
* Xperia M5  
* Xperia M4 Aqua  
* Xperia C5  
* Xperia X  
* Xperia XA  
* Xperia XA Ultra  
* Xperia X Performance  
* Xperia X Compact  
* Xperia XZ  

可通过漏洞获取临时ROOT的设备:  

* Xperia XZs  
  [由XDA用户@nlra发布](https://forum.xda-developers.com/t/possible-way-to-backup-ta-drm-keys-maybe.4149145/post-85387751) (最新安卓8.0固件可用)

* Xperia XZP/XZ1/XZ1c  
  [renoroot](https://forum.xda-developers.com/t/xz1c-xz1-xzp-temp-root-exploit-to-backup-drm-keys-implemented.3795510/)  
  [bindershell](https://forum.xda-developers.com/t/xz1c-xz1-xzp-temp-root-exploit-via-cve-2019-2215-including-magisk-setup-locked-bl.4046641/)
* Xperia XZ2/XZ2P/XZ2c/XZ3  
  [tama-mroot](https://forum.xda-developers.com/t/xz2-xz2c-xz2p-xz3-temp-root-exploit-via-cve-2020-0041-including-magisk-setup.4099131/)
* Xperia 1/5  
  [x1x5-mroot](https://forum.xda-developers.com/t/xperia-1-5-temp-root-exploit-via-cve-2020-0041-including-magisk-setup.4146103/)

----

## DRM修复补丁

* Xperia XZs  
  [ROOT/DRM fix for Xperia XZs Oreo 41.3.A.2.247](https://forum.xda-developers.com/t/root-drm-fix-for-xperia-xzs-oreo-41-3-a-2-247.3726911/)