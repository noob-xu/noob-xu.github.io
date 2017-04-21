title: 树莓派花生壳（内网版）攻略
date: 2015-10-11 12:24:17
categories: 
- 树莓派
tags: 
- 树莓派
- 花生壳
---
 * ## 下载安装包
 > http://download.oray.com/peanuthull/embed/phddns_raspberry.tgz
 ``` bash
pi@raspberrypi ~/Desktop/hsk $ wget http://download.oray.com/peanuthull/embed/phddns_raspberry.tgz
--2015-10-11 12:23:16--  http://download.oray.com/peanuthull/embed/phddns_raspberry.tgz
正在解析主机 download.oray.com (download.oray.com)... 61.152.96.115, 202.105.21.208
正在连接 download.oray.com (download.oray.com)|61.152.96.115|:80... 已连接。
已发出 HTTP 请求，正在等待回应... 200 OK
长度：801473 (783K) [application/octet-stream]
正在保存至: “phddns_raspberry.tgz”

phddns_raspberry.tg 100%[=====================>] 782.69K   571KB/s 用时 1.4s

2015-10-11 12:23:17 (571 KB/s) - 已保存 “phddns_raspberry.tgz” [801473/801473])

 ```
 * ## 解压并安装
 > 解压	
 ``` bash
pi@raspberrypi ~/Desktop/hsk $ tar zxvf phddns_raspberry.tgz
phddns2/
phddns2/oraynewph
phddns2/oraynewph.tgz
phddns2/oray_serve
phddns2/parse
 ```
 > 安装
 *安装需要在root权限下运行*
 ``` bash
root@raspberrypi:/home/pi/Desktop/hsk# cd phddns2
root@raspberrypi:/home/pi/Desktop/hsk/phddns2# ./oraynewph start
bin/
bin/oraynewph
bin/oraysl
./oraynewph: 19: kill: Usage: kill [-s sigspec | -signum | -sigspec] [pid | job]... or
kill -l [exitstatus]
./oraynewph: 20: kill: Usage: kill [-s sigspec | -signum | -sigspec] [pid | job]... or
kill -l [exitstatus]
2015-10-11 12:35:43             0x00000001      install ddns services...
2015-10-11 12:35:43             0x00000001      [ddns_manager] get_config_account begin
2015-10-11 12:35:43             0x00000004      [fw_service] load config file failed
CAccountTread::CAccountTread()
2015-10-11 12:35:43             0x00000001      [ddns] loginning...
2015-10-11 12:35:43             0x00000004      [ddns] login parameters is invald
2015-10-11 12:35:43             0x00000002      [fw_service] load config file failed

SN:***************** #这里是你的SN
Please visit http://b.oray.com
Oraynewph start success !
 ```
 *如果最后一行提示'Oraynewph start success !'*说明启动成功*
 * ## 查看运行状态及SN码
 *在任意目录下执行在任意路径命令行执行 oraynewph status 即可看到花生壳运行状态以及SN码*
 ``` bash
root@raspberrypi:/home/pi/Desktop/hsk/phddns2# oraynewph status
sh: 0: getcwd() failed: No such file or directory
sh: 0: getcwd() failed: No such file or directory
RUNSTATUS= ONLINE
SN= ***************** #这里是你的SN
LoginAddress= http://b.oray.com/

 ```
* ## 登录管理后台并设置内网映射
	* 在浏览器输入地址：b.oray.com，在花生壳管理页面，输入SN码与密码（首次登录默认密码 admin）
	* 首次登录需要修改默认密码，完善手机验证和邮箱信息完成初始化
	* 树莓派跟花生棒不一样，没有内置帐号，需要绑定花生壳账号使用
	* 绑定登录成功，可以直接点击页面中间橙色模块 内网映射 添加映射
	* 映射添加完成，然后复制外网访问地址 http://zhuocc.imwork.net/
	* 接下来就可以愉快的玩耍了
* ## 花生壳重置，停止服务和卸载
	* 花生壳重置
	*在任意路径下运行命令 oraynewph reset，重新登录花生壳管理后台，使用初始密码admin登录重置。*
	* 停止服务
	*在任意路径命令行执行 oraynewph stop 即可关闭运行中的花生壳服务*
	* 卸载花生壳
	*在任意路径执行 oraynewph uninstall 即可卸载花生壳服务。
	 我们可以通过命令 oraynewph status 确认花生壳服务已经成功卸载。*
	
