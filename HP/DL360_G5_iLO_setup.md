
#HP DL 360 G5的Integrated Lights-Out 2设置


###HP的远程管理功能叫做iLO，即Integrated Lights-Out，iLO的配置主要包括三项，网络、账户、波特率。

1. 服务器加电启动，当系统提示时按F8键进入HP的Integrated Lights-Out 2的配置界面。

1. 首先配置网络

    2.1) 选择Network的下拉菜单NIC and TCP/IP，如图1所示。

    ![alt text][1]

    选择DNS/DHCP，如图2所示，将DHCP Enable设置为OFF模式（下一步工作将支持DHCP模式分配管理IP）。

    ![alt text][2]

    2.2) 参照图3的配置进行配置。请注意，`记录下这里的MAC地址，MAC地址是使用DHCP模式分配管理IP的重要参数`。

    ![alt text][3]

1. 接着进行管理账户的配置，如图4所示，选择User下的Add，进入帐号添加界面。

    ![alt text][4]

    按照图5的方式进行相同的配置。其中，账户是XXXXXX，密码是XXXXXX。

    ![alt text][5]

1. 最后，进行iLO的命令行模式的参数设置，如图6所示。

    ![alt text][6]

    选择Setting界面下的CLI，按照图7的模式进行相同的设置，注意波特率设置成`115200`。

    ![alt text][7]

1. 至此，完成了HP ProLiant DL 360 G5的iLO设置。







[1]: http://images.proadm.net/hp/dl360g5/network_config.jpg "图1 网络设置菜单"

[2]: http://images.proadm.net/hp/dl360g5/network_nic_tcp.jpg "图2 关闭DHCP"

[3]: http://images.proadm.net/hp/dl360g5/network_dns_dhcp.jpg "图3 配置网络地址等参数"

[4]: http://images.proadm.net/hp/dl360g5/user.jpg "图4 账户设置"

[5]: http://images.proadm.net/hp/dl360g5/user_add.jpg "图5 添加帐号"

[6]: http://images.proadm.net/hp/dl360g5/setting.jpg "图6 设置iLO参数"

[7]: http://images.proadm.net/hp/dl360g5/setting_cli.jpg "图7 设置CLI波特率"