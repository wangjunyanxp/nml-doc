
#DELL PowerEdge R410的iDRAC设置

###DELL服务器用于远程管理的系统叫做iDRAC，即Integrated Dell Remote Access Card系统，为了实现远程远程管理，在iDRAC和BIOS上需要配置三个信息，一个是网络信息、一个是管理帐号、一个是SOL（Serial Over LAN）的配置。

1. 服务器加电启动，当系统提示时按F2键进入DELL的系统设置的配置界面。

1. 当系统提示按`Ctrl-E`时进入远程管理设置界面，如图1所示。

    ![alt text][1]

1. 将iDRAC LAN功能和IPMI Over LAN功能启用，如图2所示。

    ![alt text][2]

1. 进入LAN Parameters配置界面，配置好网络参数。将网卡设置为共享模式，禁用掉VLAN，关闭DHCP分配IP选项。如图3所示。另外，`请记录下MAC地址信息，此信息是使用DHCP模式分配管理IP的重要参数`。

    ![alt text][3]

    启用LAN Alert功能，并设置将报警信息到指定地址，如图4所示。

    ![alt text][4]

1. 设置远程管理使用的IPv4信息，使用静态IP地址，如图5所示。

    ![alt text][5]

1. 参照图6完成远程管理使用的IPv6信息设置。

    ![alt text][6]

1. 完成网络的配置后返回上一界面，进入System Services设置界面，参照图7完成设置。

    ![alt text][7]

1. 设置远程管理使用的账户信息，权限设置为Admin，帐户名为XXXXXX，密码为XXXXXX，如图8所示。

    ![alt text][8]

1. 保存并退出iDRAC设置，至此完成远程管理设置。为了将服务器的屏幕信息显示到本地，需要继续在BIOS里完成SOL设置。退出iDRAC设置后`按F2`进入BIOS设置界面，如图9所示，BIOS设置中主要需要完成Intergrated Devices和Serial Communication设置。

    ![alt text][9]

1. 进入Intergrated Devices设置，按照图10进行相同的配置，特别注意的是，为了实现远程安装OS，Embedded Gb NIC1和Embedded Gb NIC2必须设置成`Enabled with PXE`。

    ![alt text][10]

1. 返回上一界面，进入Serial Communication设置,参照图11设置好使用的终端、波特率、串口信息，其中Serial Communication必须选成`On with Console Redirection via COM2`，另外，`Redirection After Boot选择成Enable`！

    ![alt text][11]

1. 至此，完成了整个远程管理的设置。







[1]: http://images.proadm.net/dell/r410/enter_in_remote_setup.jpg  "图1 进入DELL iDRAC设置"

[2]: http://images.proadm.net/dell/r410/idrac_config.jpg  "图2 开启iDRAC与IPMI功能"

[3]: http://images.proadm.net/dell/r410/idrac_lan_1.jpg  "图3 配置LAN参数之通用参数"

[4]: http://images.proadm.net/dell/r410/idrac_lan_2.jpg  "图4 配置LAN Alert功能"

[5]: http://images.proadm.net/dell/r410/idrac_lan_3.jpg  "图5 配置LAN参数之IPv4参数"

[6]: http://images.proadm.net/dell/r410/idrac_lan_4.jpg   "图6 配置LAN参数之IPv6参数"

[7]: http://images.proadm.net/dell/r410/idrac_system_services.jpg  "图7 配置System Services"

[8]: http://images.proadm.net/dell/r410/idrac_lan_user.jpg  "图8 配置iDRAC的账户信息"

[9]: http://images.proadm.net/dell/r410/bios_integrated_devices.jpg  "图9 BIOS界面"

[10]: http://images.proadm.net/dell/r410/bios_integrated_devices_setup.jpg  "图10 配置Intergrated Devices"

[11]: http://images.proadm.net/dell/r410/bios_serial_communication.jpg  "图11 配置Serial Communication"