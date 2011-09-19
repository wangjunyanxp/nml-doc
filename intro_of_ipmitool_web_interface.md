
#使用ipmitool进行远程连接

无人值守系统之初，是本机OS上安装ipmitool，并使用终端访问进行管理，不同OS需要不同的ipmitool工具与terminal搭配，Windows下更为复杂。现在，系统采用Web浏览器访问方式，有浏览器即可实现服务器远程管理。

现在做的一个daemon如下：

    http://10.132.17.108/ipmi/shell
    http://10.132.17.108/ipmi/console

###系统介绍

1. 这个Web访问使用纯JavaScript实现，无需ActiveX与Java applet支持，兼容多种浏览器，包含IE 6、7、8，Firefox 5、6，Chrome 13、Opera 15、Safari 5.1等，在IE 9下无发正常使用，详情[见此][1]。系统实现原理是[shell in a box项目][2]。

1. URL中的10.132.17.108代表的并不是被管理的服务器，而是代表提供这个shell in a box服务的服务器，现在在其上面配置的是管理服务器10.132.17.200，如下图所示。未来将进一步增加更多服务器并改进访问方式。

![alt text][3]

###/ipmi/shell简介

http://10.132.17.108/ipmi/shell ，是一个纯粹的ipmi下的环境，可以直接执行ipmi命令。

+ help         查看可执行命令
+ power status 服务器加电状态（每次重启时先进行查看）
+ power soft   服务器关机
+ power on     服务器开机

###/ipmi/console功能简介

访问http://10.132.17.108/ipmi/console ，即连接到服务器的console口，看到与服务器屏幕相同的显示内容，可以看到服务器启动，BIOS信息等普通终端无法显示的信息。

受到BMC硬件限制，同一时刻只能有一个连接访问console服务。


###使用注意


1. 如果开启输入法，将无法将输入任何信息。

1. 正确退出系统的方法是先输入`Ctrl+d`，再退出浏览器。原因是每使用浏览器建立一个连接的同时，shell in a box服务器会创建一个进程，只有用这种方法，才会kill掉对应进程。输入`Ctrl+d`后，浏览器显示`Session closed`，出现`Connent`按钮。

1. 因为ipmi功能包含console功能，在ipmi界面里输入`sol activate`命令即可进console界面；在console界面下，输入`~.`即可退出至ipmi界面。

1. 当输入`sol activate`命令进入console界面时，浏览器提示`[SOL Session operational.  Use ~? for help]`，此时，需多敲几个回车才能进入到console界面。

1. 退出console界面至ipmi界面时，需输入`~.`，当console界面是登录界面时，有时OS会将其作为帐户名，这是需要多尝试几次；有时输入`~`之后系统没有显示该字符，这时无需担心，输入完`~.`后即可退回至ipmi界面。

1. 由于BMC硬件限制同一时刻只能有一个连接连接到服务器console口，因此，当其他用户正在console访问时，用户登录console口浏览器显示`Info: SOL payload already active on another session`与`Session closed.`，并拒绝用户使用。

1. 若上一个登录用户在没有`Ctrl+d`使用退出时console端口时，其他用户访问时同样会显示`Info: SOL payload already active on another session`信息并拒绝用户访问，这时，使用`sol deactivate`命令强制关闭现有连接，再次输入`sol activate`命令，这时可以正常进入console界面。由于强制断开现有console连接可能会影响正常用户操作，所以此功能慎用。

1. 再次强调，务必请输入`Ctrl+d`再关闭浏览器来退出系统！


[1]: http://code.google.com/p/shellinabox/issues/detail?id=118&q=ie9
[2]: http://code.google.com/p/shellinabox/
[3]: http://images.proadm.net/shell_in_a_box_system.jpg "图1 系统结构"

