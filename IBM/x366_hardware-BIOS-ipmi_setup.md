
#����ֵ��ϵͳ֮ IBM System x366����

������Ҫ����������Ӳ��������BIOS���á�

### ������Ӳ������

1. ȷ�Ϸ������ػ�������õ�Դ����Դ�߲�ú���Ȼ�һֱת���ַ���ɢ�ȿڿ��Ըо���ů�硣

1. ��ù������eth1�ϵ����ߣ����ߵ�������ͼ1��ʾ�������������Ϊeth1���ұ�����Ϊ����ڣ���Ҫע����ǣ���������߲�ú����ڴ��ĵ���Ȼ�ǲ������ġ�

    ![alt text][1]


### BIOS����

1. ��������F1������BIOS���ý��棬��ͼ2��ʾ��

    ![alt text][2]

1. ����`Advanced Setup`���棬����ͼ3��ʾ������ȫ��ͬ�����á�

    ![alt text][3]

1. ���뱾�����`CPU Options`����`Intel Virtualization Technlogy`���ó�Enable(һ��Ĭ��enable��������֤һ��)����ͼ4��ʾ��Ȼ�󷵻���һ���档

    ![alt text][4]

1. ���ţ����뵹���ڶ��е�`Baseboard Management Controller(BMC) Settings`���������ͼ5�ķ�ʽ������ȫ��ͬ�����á�

    ![alt text][5]

1. ���뱾���浹�������е�`BMC Network Configuration`���棬��д`Host Name`ΪIBM366�����������������������д�ã����Բο�ͼ6�ķ�ʽ�������ã�ע��ͼ6�Ƿ��������þ�̬��ַ�ķ�ʽ���������DHCP��ȡ������Ϣ������DHCP Controlѡ�������ó�DHCPģʽ����`�ر���Ҫע����ǣ�������ڵ�ǰҳ������б���`��֮�󷵻���һ���档

    ![alt text][6]

1. ����`User Account Setting`���ã�ѡ��UserID 2 USERID����ͼ7��ʾ��

    ![alt text][7]

1. �����ʺ�Enable��UsernameΪUSERID��Password���ó�PASSW0RD�������IBMĬ�ϵ��û������룬�����е�0������0��������ĸo��`Privileged Limit`Ϊ`Administrator`����ͼ8��ʾ��`ͬʱҲ���ע�⣬�ڵ�ǰҳ������б���`��

    ![alt text][8]

1. �˻�BIOS�����棬����`Devices and I/O Ports`�����У�����ͼ9�ķ�ʽ������ȫ��ͬ�����á�Ȼ�󣬽���`System MAC Addresses`���棬����¼��������MAC��ַ����Щ��ַ����DHCPģʽ��������IPʱ����Ҫ���á�������Ϻ󷵻���һ���档

    ![alt text][9]

1. ���뵱ǰҳ�����`Remote Console Redirection`�����У�����ͼ10�ķ�ʽ������ͬ�����ã��������һ�е�`Remote Console Flow Control`ģʽѡΪDisable��

    ![alt text][10]

1. �������ò��˳������ˣ������BIOS���á�

### IPMI����

IBM x366��֧��IPMI2.0�����֧��IPMI1.5���ڸ�ģʽ�£�������ipmitool -I lanplusѡ����⣬������SOLʱʹ��isol��

������˵

    ipmitool -U USERID -H 10.241.31.100 -P PASSW0RD isol set non-volatile-bit-rate 115.2    ���ò�����
    ipmitool -U USERID -H 10.241.31.100 -P PASSW0RD isol set volatile-bit-rate 115.2        ���ò�����
    ipmitool -U USERID -H 10.241.31.100 -P PASSW0RD isol activate      ����SOL����
    ipmitool -U USERID -H 10.241.31.100 -P PASSW0RD isol deactivate    �ر�sol����
    ipmitool -U USERID -H 10.241.31.100 -P PASSW0RD power status     �鿴�������ӵ����
    ipmitool -U USERID -H 10.241.31.100 -P PASSW0RD power off        ǿ�ƹػ����൱�ڰε�Դ��
    ipmitool -U USERID -H 10.241.31.100 -P PASSW0RD power on         �������ӵ�
    ipmitool -U USERID -H 10.241.31.100 -P PASSW0RD power cycle      ����������




[1]: http://images.proadm.net/ibm/x3550/cable_plugin.jpg "ͼ1 ��������"

[2]: http://images.proadm.net/ibm/x3550/bios_setup.jpg  "ͼ2 BIOS������"

[3]: http://images.proadm.net/ibm/x3550/advanced_setup.jpg   "ͼ3 Advanced Setup����"

[4]: http://images.proadm.net/ibm/x3550/cpu_vt_enable.jpg "ͼ4 CPU ���⹦��Enable"

[5]: http://images.proadm.net/ibm/x3550/bmc_setting.jpg  "ͼ5 BMC����"

[6]: http://images.proadm.net/ibm/x3550/bmc_network_setup.jpg  "ͼ6 ��������"

[7]: http://images.proadm.net/ibm/x3550/bmc_account.jpg "ͼ7 BMC�ʺ�����"

[8]: http://images.proadm.net/ibm/x3550/bmc_account_add.jpg "ͼ8 �����ʺ�UserID2"

[9]: http://images.proadm.net/ibm/x3550/serialport_setup.jpg  "ͼ9 Devices and I/O Ports����"

[10]: http://images.proadm.net/ibm/x3550/remote_console_redirection.jpg  "ͼ10 Remote Console Redirection����"
