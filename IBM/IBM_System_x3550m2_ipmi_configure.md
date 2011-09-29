
#IBM x3550 M2的IPMI配置与访问

###需要完成三个部分的配置，包括硬件、UEFI与IMM（Integrated Management Module）的Web配置。

1. 硬件上，需要将电源插好，并插入eth0的网线。

1. 开机，按F1进入UEFI配置，进入System Setting，如图1所示。

    ![alt text][1]

1. 在System Setting中要配置两项，分别是Devices and I/O Ports与Integrated Management Module。进入Devices and I/O 配置，在这里完成SOL的配置，如图2所示。

    ![alt text][2]

1. 进入Console Redirection Setting，配置Console重定向，如图3所示。 

    ![alt text][3]

1. 按照图4进行相同的配置。其中

        Remote Console Enable将开启Remote Console Redirection。
        Serial Port Sharing Enable将开启IPMI功能。
        Serial Port Access Mode必须选Dedicated，代表Console每次只能独占，避免多用户一起访问造成混乱。 
        SP Redirection代表Serial Port Redirection Through Telnet or SSH，选择Disable。若选择Enable，则可在此界面开启COM 2的配置，并可以通过Telnet或SSH进行控制。建议SP Redirection选择Disable。 
        Legacy Option ROM Display选COM Port 1、COM Port 2都行，建议选COM Port 1。

    ![alt text][4]

1. 按照图5配置COM1与COM2，COM2与COM1的配置一致。（SP Redirection选Disable将不提供COM 2的配置）

    ![alt text][5]

1. 返回到System Setting界面，进入Integrated Management Module，如图6所示。

    ![alt text][6]

1. 选定POST Watchdog Timer，将开启看门狗功能，当服务器宕机时将由IMM操作服务器硬件，完成重启等功能。如图7所示。在这里，可以选择本界面的Reset IMM功能来重置IMM设置。

    ![alt text][7]

1. 进入Network Configuration，按照图8的方式进行相同的配置。注意在此界面中进行保存。

        Network Interface Port 选择Shared，业务与管理将共享eth0端口。
        地址分配采用静态方式分配，另外，请记录MAC地址，这将作为DHCP方式分配IP的重要依据，本MAC信息也可以从随机纸条上记录，即BMC1 MAC。

    ![alt text][8]

1. 至此，完成UEFI配置，接着进行IMM Web配置，在Web配置中完成帐户的设置，这是非必要步骤，可采用默认帐户远程管理。使用浏览器访问刚才分配的管理IP地址，如图9所示。用户名USERID，密码PASSW0RD。注意，密码中间是数字0，不是字母O。

    ![alt text][9]

1. 进入系统欢迎界面，在这里选择自动退出时间，选择5-15分钟皆可，在此时间内没有操作将自动登出，增强安全性。如图10所示。

    ![alt text][10]

1. 选择IMM Control下的Login Profiles，如图11所示

    ![alt text][11]

1. 点Add User，在这里可以增加用户，在这里增加用户ibm3550m2，密码XXXXXXXX，权限为Supervisor，并点击右下角Save保存配置，如图12所示。

    ![alt text][12]

1. 帐户也可以删除，进入帐户ibm3550m2，点击右下角的Clear Login Profile，可以删除帐户。如图13所示。

    ![alt text][13]

1. 至此，完成整个IBM x3550 M2的IPMI配置。


[1]: http://images.proadm.net/ibm/x3550m2/enter_uefi.jpg "图1 UEFI界面"

[2]: http://images.proadm.net/ibm/x3550m2/enter_devices_and_io.jpg  "图2 设置Devices and I/O"

[3]: http://images.proadm.net/ibm/x3550m2/enter_console_redirect.jpg   "图3 进入Console重定向"

[4]: http://images.proadm.net/ibm/x3550m2/set_console_redirection.jpg "图4 配置Console重定向"

[5]: http://images.proadm.net/ibm/x3550m2/set_console_port.jpg  "图5 设置COM口参数"

[6]: http://images.proadm.net/ibm/x3550m2/enter_imm_setup.jpg  "图6 进入IMM设置"

[7]: http://images.proadm.net/ibm/x3550m2/set_post_watchdog.jpg "图7 设置IMM

[8]: http://images.proadm.net/ibm/x3550m2/set_net_conf.jpg "图8 设置网络参数"

[9]: http://images.proadm.net/ibm/x3550m2/login_to_web_imm.jpg  "图9 使用Web登录"

[10]: http://images.proadm.net/ibm/x3550m2/imm_welcome_inf.jpg  "图10 设置自动退出时间"

[11]: http://images.proadm.net/ibm/x3550m2/imm_account_setup.jpg  "图11 管理帐户信息"

[12]: http://images.proadm.net/ibm/x3550m2/add_imm_account.jpg  "图12 增加帐户"

[13]: http://images.proadm.net/ibm/x3550m2/deleate_imm_account.jpg  "图13 删除帐户"
