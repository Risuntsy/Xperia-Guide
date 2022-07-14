# 分区

仅个人拙见，如有错误或疑惑欢迎指正、讨论.

安卓设备的存储(ROM)被分为许多分区, 不同的分区存放不同的内容, 不同的 芯片供应商/厂商/出场系统版本 的设备, 系统分区大多数时候并不相同 ( 差距也不太大 )

在 **Sony Xperia设备** 上大概有这几种分区:  

A-Only

* 有独立recovery分区
* 出场系统版本Android 8.0以下
* 无独立vendor分区, vendor包含在system分区, 默认不支持 PT (Project Treble)

A/B:

* 需要OTA更新的分区分成a/b两个**独立**分区, 分区名后的后缀就是对应的分区，如boot_a/boot_b


* 非动态分区
    * A/B分区之间互相独立, 默认OTA到当前活动分区之外的分区，OTA时无需关机重启
    * 系统会将OTA后的系统安装到另一个分区, 安装完成后第一次重启自动启动到另一个分区的系统

* 动态分区
    * 除super分区外与无动态分区的A/B分区基本无区别
    * 系统为设备分配一个 super 分区，其中的子分区可动态地调整大小。
        * 支持的子分区: system、vendor、product、odm
        * super 分区在内部处理 A/B 槽位，因此 A/B 设备不需要单独的 super_a 和 super_b 分区。
    * boot/dtbo等分区仍具有A/B分区

V(irtual)A/B





在索尼设备上，**一般**能看到这些分区:  

* abl/xbl/xfl/xflkerstore 等分区  
底层/Bootloader相关，绝大多数时候并不需要修改也不能修改 (非常容易导致设备永久变砖，且含有各种验证)

* TA 分区  
详情: [备份TA](../../backup_ta.md)


* boot/system/vendor/oem 分区  
**boot** 包含用来启动设备的内核(kernel)  
**system|product** 主要包含 Android 框架  
**vendor|odm** 包含一些厂商专有的驱动和软件  
**oem** 包含运营商的定制功能或限制的软件和配置
