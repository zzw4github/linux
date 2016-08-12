# linux
sudo apt-get update
sudo apt-get install vsftpd
sudo service vsftpd restart
sudo mkdir /home/uftp
chmod -R 777 /home/uftp
sudo ls /home"
sudo useradd -d /home/uftp -s /bin/bash uftp
sudo passwd uftp
sudo vi /etc/vsftpd.conf
添加 
userlist_deny=NO
userlist_enable=YES 
userlist_file=/etc/allowed_users
seccomp_sandbox=NO
local_enable=YES
write_enable=YES
sudo vi /etc/ftpusers

新建
sudo vi /etc/allowed_users
输入uftp

sudo vi /etc/ftpusers
记录的是不能访问FTP服务器的用户清单。



vsftpd 550 

原因：vsftp默认配置不允许上传文件。
解决：修改/etc/vsftpd.conf
将“write_enable=YES”前面的#取消。
重启vsftp服务器。

553
chmod -R 777 /home/uftp


ubuntu开启SSH服务
SSH分客户端openssh-client和openssh-server
如果你只是想登陆别的机器的SSH只需要安装openssh-client（ubuntu有默认安装，如果没有则sudo apt-get install openssh-client）
sudo apt-get install openssh-server
然后确认sshserver是否启动了：
ps -e |grep ssh
如果看到sshd那说明ssh-server已经启动了。
如果没有则可以这样启动：sudo /etc/init.d/ssh start
ssh-server配置文件位于/ etc/ssh/sshd_config，在这里可以定义SSH的服务端口，默认端口是22，你可以自己定义成其他端口号，如222。
然后重启SSH服务：
sudo /etc/init.d/ssh stop
sudo /etc/init.d/ssh start
然后使用以下方式登陆SSH：
ssh username@192.168.1.112 username为192.168.1.112 机器上的用户，需要输入密码。
断开连接：exit
