
#无人值守系统之 IBM System x3550配置

配置主要包含以下三个部分，分别是服务器硬件配置、BIOS设置与操作系统设置。

### 服务器硬件配置

1. 确认服务器关机，并插好电源；电源线插好后风扇会一直转，手放在散热口可以感觉到暖风。

1. 插好管理口与eth1上的网线；网线的连接如图1所示，其中左边网线为eth1，右边网线为管理口，需要注意的是，管理口网线插好后网口处的灯依然是不会亮的。

    ![alt text][1]


### BIOS设置

1. 开机，按F1键进入BIOS设置界面，如图2所示。

    ![alt text][2]

1. 进入`Advanced Setup`界面，按照图3显示进行完全相同的配置。

    ![alt text][3]

1. 进入本界面的`CPU Options`，将`Intel Virtualization Technlogy`设置成Enable(一般默认enable，但请验证一下)，如图4所示，然后返回上一界面。

    ![alt text][4]

1. 接着，进入倒数第二行的`Baseboard Management Controller(BMC) Settings`，进入后按照图5的方式进行完全相同的配置。

    ![alt text][5]

1. 进入本界面倒数第三行的`BMC Network Configuration`界面，填写`Host Name`为IBM3550，并将服务器的网络参数填写好，可以参考图6的方式进行配置（注：图6是服务器采用静态地址的方式，如果采用DHCP获取网络信息，则在DHCP Control选项中设置成DHCP模式），`特别需要注意的是，请务必在当前页面里进行保存`，之后返回上一界面。

    ![alt text][6]

1. 进入`User Account Setting`设置，选择UserID 2 USERID，如图7所示。

    ![alt text][7]

1. 设置帐号Enable，Username为XXXXXXXX，Password设置成XXXXXXXX（因为BIOS设置界面里不识别符号，所以没有#），`Privileged Limit`为`Administrator`，如图8所示。`同时也务必注意，在当前页面里进行保存`。

    ![alt text][8]

1. 退回BIOS主界面，进入`Devices and I/O Ports`设置中，按照图9的方式进行完全相同的设置。然后，进入`System MAC Addresses`界面，并记录好网卡的MAC地址，这些地址将在DHCP模式设置网卡IP时起到重要作用。操作完毕后返回上一界面。

    ![alt text][9]

1. 进入当前页面里的`Remote Console Redirection`设置中，按照图10的方式进行相同的配置，但在最后一行的`Remote Console Flow Control`模式选为Disable。

    ![alt text][10]

1. 保存配置并退出。至此，已完成BIOS设置。








[1]: http://images.proadm.net/ibm/x3550/cable_plugin.jpg "图1 网线连接"

[2]: http://images.proadm.net/ibm/x3550/bios_setup.jpg  "图2 BIOS主界面"

[3]: http://images.proadm.net/ibm/x3550/advanced_setup.jpg   "图3 Advanced Setup界面"

[4]: http://images.proadm.net/ibm/x3550/cpu_vt_enable.jpg "图4 CPU 虚拟功能Enable"

[5]: http://images.proadm.net/ibm/x3550/bmc_setting.jpg  "图5 BMC设置"

[6]: http://images.proadm.net/ibm/x3550/bmc_network_setup.jpg  "图6 网络配置"

[7]: http://images.proadm.net/ibm/x3550/bmc_account.jpg "图7 BMC帐号设置"

[8]: http://images.proadm.net/ibm/x3550/bmc_account_add.jpg "图8 设置帐号UserID2"

[9]: http://images.proadm.net/ibm/x3550/serialport_setup.jpg  "图9 Devices and I/O Ports配置"

[10]: http://images.proadm.net/ibm/x3550/remote_console_redirection.jpg  "图10 Remote Console Redirection设置"
