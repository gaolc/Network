### **1. 华为交换机Console密码重置**

1、通过Console口连接交换机，并重启交换机。
2、当界面出现以下打印信息时，及时按下快捷键“Ctrl+B”并输入BootROM/BootLoad密码，进入BootROM/BootLoad主菜单
3、密码： Admin@huawei.com A必须大写。
4、选着7 Clear password for console user （选择清除console用户密码模式）。
5、选择1 Boot with default mode（键入1启动默认模式），进入后更改Console 及telnet密码。

### **2. 设备初始化**

1、登录华为交换机
2、输入：reset saved-configuration 接着问你是否初始化 选择“Y”
3、初始化之后，需要重启交换机才能生效 "reboot"

 

### **3.** 默认用户名和密码

华为交换机的默认用户名是admin，密码是admin@huawei.com





# 恢复Console口登录密码

如果忘记了Console口登录密码，用户可以通过以下两种方式来设置新的Console口登录密码。



![img](mk:@MSITStore:E:\INESA-MYWORK\网络资料\S5700,%20S6700%20V200R019C00%20产品文档.chm::/public_sys-resources/notice_3.0-zh-cn.png) 

使用Telnet协议存在安全风险，建议用户使用STelnet V2登录设备。

这种方法的前提是：用户拥有STelnet/Telnet账号并且具有管理员的权限。以下涉及的命令行及回显信息以STelnet登录设备修改Console口密码为例。用户通过STelnet账号登录交换机后，请按照如下步骤进行配置。

\# 以登录用户界面的认证方式为密码认证，密码为**Huawei@123**为例，配置如下。

```
<HUAWEI> system-view
[HUAWEI] user-interface console 0
[HUAWEI-ui-console0] authentication-mode password
[HUAWEI-ui-console0] set authentication password cipher Huawei@123
[HUAWEI-ui-console0] return
<HUAWEI> save
```

\# 以登录用户界面的认证方式为AAA认证，用户名为**admin123**，密码为**Huawei@123**为例，配置如下。

```
<HUAWEI> system-view
[HUAWEI] user-interface console 0
[HUAWEI-ui-console0] authentication-mode aaa
[HUAWEI-ui-console0] quit
[HUAWEI] aaa
[HUAWEI-aaa] local-user admin123 password irreversible-cipher Huawei@123
[HUAWEI-aaa] local-user admin123 service-type terminal
[HUAWEI-aaa] return
<HUAWEI> save
```

#### 通过BootROM/BootLoad清除Console口登录密码

![img](mk:@MSITStore:E:\INESA-MYWORK\网络资料\S5700,%20S6700%20V200R019C00%20产品文档.chm::/public_sys-resources/icon-note.gif) 说明： 

交换机的BootROM/BootLoad提供了清除Console口登录密码的功能，用户可以在交换机启动后修改Console口登录密码，然后保存配置。请按照如下步骤进行配置。

1. 通过Console口连接交换机，并重启交换机。当界面出现以下打印信息时，及时按下快捷键“Ctrl+B”或者“Ctrl+E”并输入BootROM/BootLoad密码，进入BootROM/BootLoad主菜单。

   ```
   Press Ctrl+B or Ctrl+E to enter BootLoad menu ... 2
   password:      //输入BootLoad密码
   ```

   ![img](mk:@MSITStore:E:\INESA-MYWORK\网络资料\S5700,%20S6700%20V200R019C00%20产品文档.chm::/public_sys-resources/icon-note.gif) 说明： 

2. 在BootROM/BootLoad主菜单下选择“Clear password for console user”清除Console口登录密码。

3. 根据交换机的提示，在BootROM/BootLoad主菜单下选择“Boot with default mode”启动设备。

   ![img](mk:@MSITStore:E:\INESA-MYWORK\网络资料\S5700,%20S6700%20V200R019C00%20产品文档.chm::/public_sys-resources/icon-note.gif) 说明： 

4. 完成系统启动后，通过Console口登录时不需要认证，登录后按照系统提示配置验证密码。（V200R009及之后版本，完成系统启动后，通过Console口登录时认证方式为None，系统启动后不会提示配置验证密码。）

5. 登录交换机后，用户可以根据需要配置Console用户界面的认证方式及密码。

#### 相关信息

**视频**

[如何恢复Console口密码](http://forum.huawei.com/enterprise/thread-208373.html)

