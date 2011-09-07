
#工具iLO简介

+ IBM服务器主要通过IPMI接口协议和ipmitool来管理服务器并监视其状态，而HP公司则在ipmi接口的基础上重新进行了封装与功能增强，形成了iLO。

+ iLO有三个版本，iLO 1、2、3，其中，在iLO 1 版本里，可以使用ipmi工具，但是在iLO 2和iLO 3的版本里，默认禁掉了udp 623端口，即ipmi专用端口，因此只能通过IE与SSH方式来访问服务器进行管理。此外，由于iLO 1已经非常古老，目前公司的服务器大多是iLO 2和iLO 3版本的。

+ HP的iLO是基于ipmi的再封装，优点是增加了HP自身开发的功能，并且在IE模式下可以轻松控制，利于可视化管理，但最大缺点是命令行并不与ipmi兼容，这样在公司的多品牌的环境下并不能良好的进行统一管理，所以建议通过升级固件的方式使HP服务器支持ipmi命令来进行管理。

+ 幸运的是，在iLO 2系列里，可以通过升级服务器的固件Firmware（这里的固件是HP服务器上的用于远程管理的硬件内的固件），从1.4X版本升级到2.06版本后，将开启ipmi的udp 623端口，可以使用ipmi工具进行管理，并且命令是与IBM服务器上的ipmi想兼容的。另外，目前还没有对iLO 3系列进行测试。


#iLO的使用

###使用前准备
+ 为了使用iLO，必须在此之前做好设置，在连接之前，必须在服务器端加电启动后进入Integrated Lights-Out 2后设置好参数，包括ip地址、帐号密码（也可以使用默认帐号密码）等，详情请参照文档DL360_G5_iLO_setup.md。此外，必须需要使用Licensing激活iLO，激活方式是使用服务器上的纸条上的License输入到iLO的IE界面里的Administration标签页里面的Licensing选项，在页面下方的5个方框里输入License号码并点击Install键即可完成。License号码可以看图1。

    ![alt text][1]

+ 首次登陆时，需要安装相应的程序插件，IE会自动弹出，安装并使用插件即可。


###登录使用
1. 使用https协议下的管理网卡地址进行登录，例如使用URL https://10.132.17.206 进行登录，输入帐号名和密码可以登录。

2. iLO还可以通过SSH来使用，使用SSH远程登录到服务器的管理IP的22端口，输入帐号密码后，就可以使用iLO的命令行进行管理，但是由于命令与ipmi并不兼容，所以现在仅使用此功能来升级固件。


#升级固件firmware
固件升级条件： 服务器插好电源开机、网线插好、服务器端加电启动后进入Integrated Lights-Out 2后的参数已设置好，此外，由于HP服务器出厂前会自动有一个默认的iLO账户及密码，可以通过此帐户直接登录。 

###获取固件包
事实上，固件包是从HP网站上下载相应的包来得到的，可通过google来搜索“hp iLO2 firmware download”找到HP官网的相关下载链接。补充一点，固件版本是不与服务器型号相关的。
下载得到的是一个CP014890.scexe文件，这个文件是一个将shell脚本和固件的二进制文件结合在一起的自解压文件 ，使用linux或cygwin进入文件所在目录并执行命令`sudo sh CP014890.scexe --unpack=.`（在cygwin环境下使用`sh CP014890.scexe --unpack=.`）命令即可将文件解压，文件解压出来 后，可以得到若干的文件，其中只有.bin文件对于我们有用，其固件是iLO2_206.bin。

###固件升级

+ 方法1 命令行升级固件模式
通过SSH方式登录到HP服务器上，IP是服务器的管理IP，端口22，用户名hpdl360g5，密码********。
登录到服务器后，执行以下命令：
cd /map1/firmware
load –source http://10.241.33.27/download/ilo2_206.bin （目标服务器的http路径）
即进入到目录里并从目标地址处下载并自动升级固件。
执行完这两条命令后，将会看到执行结果status和status_tag，当status=0; 且status_tag=COMMAND COMPLIANT后，代表固件升级成功，此时，由于服务器固件升级，与服务器管理IP的SSH连接将自动断开。固件将很快更新好，几秒之后再次SSH，即可连接上。
此外，再补充一下，不一定是所有的目录都是/map1/firmware1，目前已验证1U的服务器均是这个地址，对于其他服务器尚未验证。
+ 方法2 通过iLO的IE界面进行固件升级
登录到服务器管理IP对应的https网页，选择标签页Administrator里的iLO 2 Firmware，然后选择文件，并点击Send firmware image键进行固件升级，服务器会自动进行固件升级过程，在按键Send firmware image下面有一个进度条可以看到升级过程。需要注意的是，使用IE升级，受到IE经常无响应、速度可能卡、以及不一定能固件升级成功等因素影响，建议使用SSH方式来进行固件升级，日常操作建议使用ipmi工具来操作。



[1]: http://wiki.op.sdo.com/dokuwiki/lib/exe/fetch.php?w=120&h=90&media=%E8%BF%90%E7%BB%B4%E4%B8%AD%E5%BF%83:%E8%BF%90%E8%90%A5%E7%BB%B4%E6%8A%A4:lisence_of_hp_dl360g5.jpg "图1 iLO的License信息"