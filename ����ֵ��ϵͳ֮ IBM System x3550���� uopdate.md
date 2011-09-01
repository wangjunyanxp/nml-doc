
#无人值守系统之 IBM System x3550配置

配置主要包含以下三个部分，分别是服务器硬件配置、BIOS设置与操作系统设置

### 服务器硬件配置

1. 确认服务器关机，并插好电源；电源线插好后风扇会一直转，手放在散热口可以感觉到暖风
2. 插好管理口与eth1上的网线；网线的连接如图1所示，其中左边网线为eth1，右边网线为管理口，需要注意的是，管理口网线插好后网口处的灯依然是不会亮的

### BIOS设置
1. 开机，按F1键进入BIOS设置界面，如图2所示
2. 进入Advanced Setup界面，按照图3显示进行完全相同的配置
3. 进入本界面的CPU Options，将CPU Virtualizatin Technoly设置成enable(一般默认enable，但请验证一下)，然后返回上一界面
4. 接着，进入倒数第二行的BaseBoard Management Controller(BMC) Setting，进入后按照图4的方式进行完全相同的配置
5. 进入本界面倒数第三行的BMC Network Configuration界面，将服务器的网络参数填写好，可以参考图5的方式进行配置（注：图5是服务器采用静态地址的方式，如果采用DHCP获取网络信息，则在DHCP Control选项中设置成DHCP模式，设置好主机名即可），特别需要注意的是，请务必在当前页面里进行保存，返回上一界面
6. 进入User Account Setting设置，选择第二个帐号，设置帐号Enable，帐号为ibm3550，密码设置成WDsd7258（因为BIOS设置界面里不识别符号，所以没有#），同时也务必注意，在当前页面里进行保存
7. 退回BIOS主界面，进入Devices and I/O Ports设置中，按照图6的方式进行完全相同的设置
8. 进入当前页面里的Remote Console Redirection设置中，按照图7的方式进行完全相同的配置
9. 保存配置并退出。至此，已完成BIOS设置