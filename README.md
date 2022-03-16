### Xperia-Guide
### 画饼
只是基于我自己的理解不完善的索尼Xperia设备指南，欢迎补充、纠正。  
入门  
总有人照着过时的教程刷机而出现各种问题，也有部分人不明所以就写教程去误导别人（虽然但是，希望我自己写的东西不会变成那样）  

如何验机   
一般来说，有气密的机器大概率是原装   
版本区别    
外观...  
单双卡 IMEI  
硬件  部分日版机型的闪存和内存容量比其他地区小，部分国行机型独享更高的内存或闪存  
频段 不同运营商/地区的机器频段支持基本不同，一般日版支持的频段最少，对其他地区的兼容支持最低，具体可以在运营商官网查询  
部分运营商还可能限制VOLTE和5G的支持  
NFC   NFC芯片不同，日本地区的运营商定制版都支持Felica，与其他地区的不同，协议也不兼容，所以会出现日版机器刷了其他地区的固件导致NFC没用、不能深度睡眠，甚至随机重启的问题  
能否互刷固件  除了较新（大概14年之后）的日本DOCOMO版本基本不能在绿灯下跨地区刷固件，因为绿灯的验证和其他设备不同，同处理器平台的机器绿灯验证一般相同同平台的不同机型互刷可能开机，但是一般有BUG，特别是显示/触摸之类的  
刷机    
刷机前，最好先备份系统分区或用newflasher导出部分TA，防止死砖  
绿灯(Flashmode) 无需解锁 只能刷官方固件，SIN文件包含固件签名，绿灯通信时会验证   
同时绿灯下还可以读写部分TA单元  
17年（骁龙820平台）以及之前的设备请用Flashtool或者Xflasher    
newflasher只支持骁龙835平台及之后的设备  
newflasher刷机过程：  
	部分A/B分区的设备需要先切换A分区为活动分区，否则会不开机，具体...  
	Windows下需先安装索尼的Flashmode驱动  
	使用Xperifirm下载固件（一般不需要删任何文件，比如SIMLOCK.TA，newflasher会自动跳过）  
	注意！：用newflasher刷写打包成FTF格式的固件需要一些改动：...，旧版newflasher可能会因为文件名而错误地把A/B分区的文件刷到同一个分区导致系统损坏（可以重新刷写正确的固件救回）  
	把！！最新版！！newflasher程序放进固件文件夹运行  
	按照newflasher提示刷机即可  
Fastboot 刷机    
解锁Bootloader    
注意！：解锁可能导致设备永久损坏，失去官方保修，解锁前请三思！！！  
解锁前，需确认你的设备是否能解锁  
拨号*#*#7378423#*#* 在打开的界面里选择Service info————Configuration，查看Bootloader unlock allowed:后的内容
    如果是Bootloader unlock allow : No，则您的设备的运营商政策不允许解锁，无法通过常规途径解锁。但可以使用部分解网络锁的工具(eg:qUnlockTool)，在工具解锁后Bootloader unlock allowed就会变成Yes，即可解锁Bl  
    如果Bootloader unlock allow后显示 "Yes after SIM UNLOCK"，则在解除网络锁后会变成Yes，之后可以解锁Bl  
（可选）备份TA  
骁龙845平台（Xperia XZ2同处理器的设备）即使备份并恢复TA分区也不会恢复DRM，而且无法回锁BL。骁龙855平台以及之后的旗舰设备（Xperia 1同处理器的设备）在回锁BL后会恢复DRM  
索尼官网(https://developer.sony.com/develop/open-devices/get-started/unlock-bootloader)获取解锁码（需要科学上网，否则可能出现人机验证且一直失败）  
翻到最底下选择机型(其实随便选择也行...都是同样的算法生成的)，输入IMEI，确保你以及知道解锁可能带来的风险后勾选下面的选项，随后点击提交（Submit）按钮    
  刷第三方ROM  
  第三方ROM一般只刷写boot vendor system product系统（不同设备有变化），基于SODP的ROM还需要刷写索尼提供的OEM文件到OEM分区  
  获取Root权限 用Magisk修补boot分区镜像后刷入（动态分区的设备官方的boot镜像要稍作修改）  
 运营商定制版设备VOLTE的实现（ 支持5G的设备似乎默认支持全地区VOLTE  
  已解Bl  
  修改OEM或者root后QPST修改NV  
  未解锁Bl  
   部分设备可以用漏洞临时Root后修改OEM或者QPST修改NV  
   刷指定地区固件里的OEM  
    可用设备：Xperia 1/5：刷对应型号的对应安卓版本的日本地区的双卡公开版型号里的OEM  
    副作用：无法通过SafetyNet  
