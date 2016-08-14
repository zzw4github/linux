http://blog.csdn.net/zzxian/article/details/25487951


删除一个PPA源  
1,到 源的 目 录:cd  /etc/apt/sources.list.d/
2,可以看 到 关 于 源的 文件,删除即可 .


### no enough free disk /boot
Usually it means that there are too many old kernels on the boot partition (and the boot partition by default is only about 200MB, so fills up pretty fast).

You can see that by running 
```
df -h /boot
```

Filesystem Size Used Avail Use% Mounted on
/dev/sda2 237M 141M 84M 63% /boot

To clear old kernels off the system, you need to do this:  
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```
That gets a list of installed kernels, filters out the one you’re currently running, and then passes the rest of the list to apt-get for removal.

Then run df again, and you should see more space in the boot partition:


Filesystem Size Used Avail Use% Mounted on
/dev/sda2 237M 54M 171M 24% /boot

Now run the updater again, and should all work.

- ubuntu 无法sudo apt-get 了
这个很难讲，可能是依赖关系问题，也可能是源冲突，或者本来源就不好

你sudo apt-get -f install试一下看看

不行的话这样

cd /var/lib/dpkg
sudo mv info info.bak
sudo mkdir info

然后apt-get install 或者 apt-get upgrade
再把info替换回去应该就可以了

-
rm -rf /etc/nginx/  
rm -rf /usr/sbin/nginx  
rm /usr/share/man/man1/nginx.1.gz  
apt-get remove nginx*  


- 
apt-get update  
apt-get upgrade  

ubuntu中查找软件的安装位置

ubuntu中的软件可通过图形界面的软件中心安装，也可以通过命令行apt-get install安装。但是安装后的软件在哪个位置呢？这点跟windows环境下安装软件的路径选择不一样。ubuntu中可供调用的终端大都在/usr/bin或者/opt，但也不尽然。可尝试用下面的方法快速找到软件的位置。

1.执行该程序；

2.用命令 ps -e 找到该程序的名字；

3.用 find 或 whereis 命令查找文件位置。

此外，如果知道使用apt-get install命令安装的软件，可直接用命令 dpkg -S softwarename 显示包含此软件包的所有位置，dpkg -L softwarename 显示安装路径。

 

PS：

aptitude show softearename  或 dpkg -l softwarename 查看软件版本


