
#使用ipmitool进行远程连接

最初无人值守系统的远程管理，是在本地使用终端来登录到目标服务器，需要本地安装ipmitool，并使用终端进行访问；不同的OS需要不同的ipmitool工具与terminal，此外，Windows的配置也比较复杂。现在，将使用Web进行管理，只需要一个浏览器即可实现远程管理。

现在做的一个daemon如下：

    http://10.132.17.108/ipmi/shell
    http://10.132.17.108/ipmi/console

###系统介绍

首先，这个Web访问使用的是纯JavaScript的实现，是一个`Shell in a box`系统，无需ActiveX控件与applet的支持，直接访问即可，支持多种浏览器，包括IE 6、7、8，Firefox 5、6，Chrome 13、Opera 15、Safari 5.1等浏览器，目前仅发现对IE 9的支持不是很好。

这个URL中的10.132.17.108代表的并不是被管理的服务器，而是代表提供这个web服务的服务器，现在在其上面配置的是管理服务器10.132.17.200，如下图所示。未来将进一步增加更多服务器并改进访问方式。

![alt text][1]

###http://10.132.17.108/ipmi/shell 简介

http://10.132.17.108/ipmi/shell ，是一个纯粹的ipmi下的环境，可以直接执行ipmi命令，以最重要的开关机功能为例，只需要输入`power cycle`即可重启，`power off`即可关机，`power on`即可开机，需要注意的是，如果开启输入法，是不会有任何信息输入到这里的。

此外，由于每次使用浏览器进行访问的时候，提供`Shell in a box`的服务器会起一个相应的进程，直接关闭浏览器并不能kill掉服务器上的进程，只有在每次退出登录的时候输入`Ctrl+d`，这时服务器将显示`Session closed`，浏览器中心显示`Connent`按钮，这时才真正将服务器上的对应进程kill掉。

另外，由于ipmi功能其实包含Console功能，输入`sol activate`命令即可进入console管理界面，显示与http://10.132.17.108/ipmi/console 的界面一样，并且可以输入`～.`即可退回到ipmi界面。

需要注意的是，当输入`sol activate`命令进入console界面时，会出现`[SOL Session operational.  Use ～? for help]`提示，这时，需要再多敲几个回车即可进入到console界面。而从console界面退出至ipmi界面时，需要输入`～.`，有时进入console界面时正好是登录界面，在输入`～.`后，系统有时会将其作为登录帐户名，这时需要多尝试几次；有时在输入`～`之后系统没有显示该字符，这时无需担心，输入完`～.`后即可退回至ipmi界面。

另外，若上一个登录用户在没有使用`Ctrl+d`退出时，输入`sol activate`命令也会看到`Info: SOL payload already active on another session`信息，这时，可以使用`sol deactivate`命令强制关闭现有连接，然后再输入`sol activate`命令，这时可以正常进入console界面。为了避免断开其他用户的正常连接，此命令请慎用，另外，`每次登出系统时，务必输入Ctrl+d命令！！`

###http://10.132.17.108/ipmi/console 功能简介

http://10.132.17.108/ipmi/console ，将直接进入服务器的控制台，相当于服务器的屏幕，可以实现完全的交互，输入命令并看到服务器的显示，同时，也包含了服务器重启关机、重启等普通终端无法实现的功能。另外，受限于BMC的限制，同一时刻只有一个连接到服务器，这样也能避免多个同时登录导致的混乱。当已经有用户连接到服务器上的时候，系统会显示`Info: SOL payload already active on another session`与`Session closed.`，表明其他用户正在占用SOL。另外，在console界面输入`～.`同样可以进入ipmi界面。


[1]: http://images.proadm.net/shell_in_a_box_system.jpg "图1 系统结构"

