# NTFD 服务设置
 机器未安装ntp服务，使用如下命令安装服务
  ```shell
    git clone git@git.avlyun.org:inf/inf-environments.git
    cd inf-environments/ntp
    sh intall.sh
   ```
##时间服务器配置
  ntp conf配置修改
   ```shell
   vi /etc/ntp.conf 
   #####漂移时间存放文件路径
   driftfile /var/lib/ntp/drift
   #####放行上层time server
   restrict 182.92.12.11 
   #####指定网段内的服务器通过这台NTP Server进行时间同步 nomodify设置client 不能修改 server 时间配置
   restrict 192.168.1.0 mask 255.255.255.0 nomodify
   #####上层时间服务主机设定
    server 182.92.12.11  prefer 
   ```
   启动服务
   ```shell
   #####启动服务
     service ntpd restart|start|stop
   #####测试与上层时间服务器连接情况
     ntpstat
   #####上层ntp服务监控
     ntpq -p
   ```
   ##客户端时间配置
   客户端ntp服务配置
```shell
    cd /home/work
    git clone git@git.avlyun.org:inf/inf-environments.git
    cd inf-environments/ntp
    sh intall.sh
    #####配置时间服务器IP
    vi synctime.sh
    ntpdate 192.168.11.183
    crontab -e 
    ######每天23:59定时从时间服务器同步
    59 23 * * * cd /home/work/inf-environments&& sh synctime.sh
   ```
   
