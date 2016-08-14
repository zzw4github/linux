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


