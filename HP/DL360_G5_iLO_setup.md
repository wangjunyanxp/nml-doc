
#HP DL 360 G5的Integrated Lights-Out 2设置


###主要配置三个东西，一个是网络、一个是账户、还有就是iLO的参数设置

1. 服务器加电启动，当系统提示时按F8键进入HP的Integrated Lights-Out 2的配置界面。

1. 首先配置网络

    2.1) 选择Network的下拉菜单NIC and TCP/IP，如图1所示。

    ![alt text][1]

    选择DNS/DHCP，如图2所示，将DHCP Enable设置为OFF模式（目前先支持了静态IP地址分配，在未来支持DHCP模式后可以使用DHCP来进行设置）。

    ![alt text][2]

    2.2) 参照图3的配置进行配置。需要注意的是，**请记录下这里的MAC地址，未来当使用DHCP模式进行IP地址的设置时，将会使用到此参数**。

    ![alt text][3]

1. 然后进行账户的配置，如图4所示，选择User下的Add，进入帐号添加界面。

    ![alt text][4]

    按照图5的方式进行相同的配置。其中，账户是hpdl360g5，密码是********。

    ![alt text][5]

1. 最后，进行iLO的参数设置，如图6所示。

    ![alt text][6]

    选择Setting界面下的CLI，按照图7的模式进行相同的设置，注意波特率设置成115200。

    ![alt text][7]

1. 至此，完成了HP ProLiant DL 360 G5的iLO设置。







[1]: http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?w=120&h=90&media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:hpdl360g5_network_config.jpg "图1 网络设置菜单"

[2]: http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?w=120&h=90&media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:hpdl360g5_network_dnsdhcp.jpg "图2 关闭DHCP"

[3]: http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?w=120&h=90&media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:hpdl360g5_network_nic_tcpip.jpg "图3 配置网络地址等参数"

[4]: http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?w=120&h=90&media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:hpdl360g5_user.jpg "图4 账户设置"

[5]: http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?w=120&h=90&media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:hpdl360g5_user_add.jpg "图5 添加帐号"

[6]: http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?w=120&h=90&media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:hpdl360g5_setting.jpg "图6 设置iLO参数"

[7]: http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?w=120&h=90&media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:hpdl360g5_setting_cli.jpg "图7 设置CLI波特率"