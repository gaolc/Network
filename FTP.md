FTP基于TCP 支持认证及权限

TFTP基于UDP 不支持认证及权限

####      FTP 工作原理

FTP传输模式

ASCII模式 传输文本

二进制模式 图片或程序文件

####    FTP 基本配置 

ftp server enable 

set default ftp-directory flash 

aaa 

local-user huawei password cipher huawei

local-user huawei  service-type ftp 

local-user huawei access-limit 200     #设置连接数

local-user huawei idle-timeout  0 0    #显示超时时间

local-user huawei privilege level 3 



FTP 服务默认使用服务器的那些端口 ？

主动模式（port） 控制21 数据20 

用户反馈反馈没钱权限访问FTP服务器上的目录，应该如何解决 ？

set default ftp-directory  <flash>

 ```English
[AR2]ftp server enable
[AR2]set default ftp-directory flash 
[AR2]aaa 
[AR2-aaa]local-user huawei password cipher huawei
[AR2-aaa]local-user huawei  service-type ftp
[AR2-aaa]local-user huawei access-limit 200
[AR2-aaa]local-user huawei idle-timeout  0 0 
[AR2-aaa]local-user huawei privilege level 3 
[AR2-aaa]local-user huawei ftp-directory flash    #eNSP 中设置
 ```









