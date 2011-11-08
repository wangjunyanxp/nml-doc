
##安装文件包ipmitool工具`OpenIPMI-tools`
    yum -y install ipmitool
    apt-get install ipmitool


##设置波特率，与服务器硬件设置的参数一致，为115200bps

    ipmitool -I lanplus -U USERID -H 10.241.31.100 -P PASSW0RD sol set non-volatile-bit-rate 115.2
    ipmitool -I lanplus -U USERID -H 10.241.31.100 -P PASSW0RD sol set volatile-bit-rate 115.2

所有的ipmi命令都需要登录并进行设置，`-I lanplus`是ipmi选项，`-U USERID`与`-P PASSW0RD`分别是登录名与密码，`-H 10.241.31.100`是远程登录的服务器地址


##sol连接管理

    ipmitool -I lanplus -U USERID -H 10.241.31.100 -P PASSW0RD sol activate     激活连接
    ipmitool -I lanplus -U USERID -H 10.241.31.100 -P PASSW0RD sol deactivate   关闭sol连接（用于强制踢掉占用sol口的其他用户）

##电源管理
    ipmitool -I lanplus -U USERID -H 10.241.31.100 -P PASSW0RD power status   查看服务器加电情况
    ipmitool -I lanplus -U USERID -H 10.241.31.100 -P PASSW0RD power off      强制关机（相当于拔电源）
    ipmitool -I lanplus -U USERID -H 10.241.31.100 -P PASSW0RD power on       服务器加电
    ipmitool -I lanplus -U USERID -H 10.241.31.100 -P PASSW0RD power cycle    服务器重启
