``````
shutdown -h now 立刻进行关机  
shutdown -r now 现在重新启动  
reboot 现在重启计
``````

### vi编辑器 使用  
``````
1.vi hello.js  
2.输入i[进入插入模式]  
3.输入Esc[进入命令模式]    
4.输入：[wq表示退出并保存，q!退出不保存  

ls 查看当前目录下的文件 ls -l 查看时间文件大小等内容  
cd /根路径  
pwd 查看当前目录 
``````
  
 

#### Linux 目录  
#### root 存放root用户的相关文件  
#### home 存放普通用户的相关文件  
#### bin 存放常用命令  
#### sbin 要具有一定权限才能使用的命令  
#### mnt 默认挂在光驱和软驱的根目录  
#### boot 存放引相关的文件  
#### etc 存放配置相关的文件  
#### var 存放经常变化的数据  
 
#### 添加用户命令  
``````
useradd 小明  
password  
``````
#### 文件操作  
``````
mkdir建立目录  
touch新建空目录  
cp复制  
``````
#### 管道命令 |
``````
more  分页显示  
Less  显示文件内容带分页  
grep 在文本中检查内容 
``````

#### 询问使用man + 命令  
``````
find /name  
ls -l >a.txt 列表的内容写入文件a.txt中（覆盖写)  
ls -al >> aa.txt 列表的内容追加到哪见aa.txt的末尾  
``````

#### 查看linux所有组的信息  
``````
cat /etc/group  
vi /etc/group 
``````

``````
-rw-r—r—  
权限分为3中 r可读(用4表示) w可写(用2表示) x可执行(用1表示）  
``````

``````
chmod 777修改权限命令（1+2+4=7）  
df /路径挂载分区  
Who am I 查看我是什么用户 
``````

``````
samba服务，用于windows访问linux  
shell 解析成内核可以执行的代码（功能模块）  
查看目前使用的shell  
env [该命令可以显示当前操作系统的环境变量]  
chsh -s 输入信的shell /bin/bash   
``````

##### history查看历史  
``````
！xxx执行该条历史的命令  

tcp/ip 一组协议（tcp, ip,udp,arp,rarp等协议）  
``````

##### 追踪路由命令  
``````
traceroute + 网址  
windows下查看ip地址 ipconfig  
Linux下查看ip地址 ifconfig  
netsend “xxx” 192.168.255.255 局域网广播  
``````

#### 配置ip  
``````
第一种方法  
Setup进入配置界面  
/etc/rc.d/init.d/network restart   
第二种方法 //临时生效  
Ifconfig eth0  xxx.xxx.xx.xx 对网卡进行设置  
``````

#### crontab任务调度命令  
``````
1.crontab -e  
2.每隔一定时间执行命令  
1.crontab -r取消调度  
``````

#### netstat 目前系统在监听的内容  
``````
ps -avx显示进程  
kill +进程号 -9 强制结束  
killall结束进程及其子进程   
top检测进程  
cal  2009 查看日历
``````

``````
netstat网络链接状态信息  
cp拷贝文件 cp -rf workspace/ /home  
gerp -n “12” /root/abc.js /home/123.js 在文件里面是否存12的内容  
``````

``````
find /home -amin -10  
find  /home -atime -10  
find /home -cmin -10  
find /home -ctime +10  
find /home -size +10k  
``````

``````
zip -r aa.zip zip 压缩文件夹  
unzip解压  
``````

### 编辑快捷命令    
``````
vim .bash_profile
alias qc='commod'
source .bash_profile
``````

