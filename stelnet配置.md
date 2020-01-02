````
[Quidway]aaa     //配置用户信息

[Quidway-aaa]local-user huawei password cipher huawei

[Quidway-aaa]local-user huawei service-type ssh telnet

[Quidway-aaa]local-user huawei privilege level 15

[Quidway-aaa]quit

[Quidway]stelnet server enable

[Quidway]user-interface vty 0 4

[Quidway-ui-vty0-4]authentication-mode aaa

[Quidway-ui-vty0-4]protocol inbound all

[Quidway-ui-vty0-4]quit

[Quidway]rsa local-key-pair create   //创建公钥，以便分发给客户端

The range of public key size is (512 ~ 2048).

[Quidway]ssh user huawei authentication-type password  //配置ssh验证及业务，**非常重要** 

[Quidway]ssh user huawei service-type stelnet
````



关于SSH版本：

版本主要有1.3，1.5，2.0。

交换机做SSH服务器时，默认同时支持SSH1.x和SSH 2，登陆设备后会显示SSH 1.99，其实就是v1 v2的兼容模式。

[HUAWEI] **ssh server compatible-ssh1x enable （默认开启）**


    如果客户端的协议版本号低于1.3或高于2.0，则版本协商失败，断开连接。

​    如果客户端的协议版本为大于等于1.3并且小于1.99，如果系统配置为兼容SSH1.X方式，则进入SSH1.5 SERVER模块，后续进行SSH1.x协议流程，否则版本协商失败，断开与客户端的连接。

​    如客户端协议版本为1.99或2.0，则进入SSH2.0 SERVER模块，后续进行SSH2.0协议流程。