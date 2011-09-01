
#无人值守系统之 IBM System x3550配置


### 服务器上配置

1. 确认服务器关机，并插好电源；电源线插好后风扇会一直转，手放在散热口可以感觉到暖风
2. 插好管理口与eth1上的网线；网线的连接如图1所示，其中左边网线为eth1，右边网线为管理口，需要注意的是，管理口网线插好后网口处的灯依然是不会亮的
![Alt 图1](http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:ibm_system_x3550_1.jpg  "图1 网线连接")

### BIOS设置
1. 开机，按F1键进入BIOS设置界面，如图2所示
![Alt 图2](http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:ibm_system_x3550_2.jpg  "图2 BIOS主界面")
2. 进入Advanced Setup界面，按照图3显示进行完全相同的配置
![Alt 图3](http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:ibm_system_x3550_3.jpg  "图3 Advanced Setup界面")
3. 接着，进入本界面倒数第二行的BaseBoard Management Controller(BMC) Setting，进入后按照图4的方式进行完全相同的配置
![Alt 图4](http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:ibm_system_x3550_4.jpg  "图4 BMC设置")
4. 进入本界面倒数第三行的BMC Network Configuration界面，将服务器的网络参数填写好，可以参考图5的方式进行配置（注：图5是服务器采用静态地址的方式，如果采用DHCP获取网络信息，则在DHCP Control选项中设置成DHCP模式，设置好主机名即可）
![Alt 图5](http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:ibm_system_x3550_5.jpg  "图5 网络配置")
5. 退回BIOS主界面，进入Devices and I/O Ports设置中，按照图6的方式进行完全相同的设置
![Alt 图6](http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:ibm_system_x3550_7.jpg  "图6 Devices and I/O Ports配置")
6. 进入当前页面里的Remote Console Redirection设置中，按照图7的方式进行完全相同的配置
![Alt 图7](http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:ibm_system_x3550_8.jpg  "图7 Remote Console Redirection设置")
7. 保存配置并退出。至此，已完成整个设置
