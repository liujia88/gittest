# NTFD 服务设置
 机器未安装ntp服务，使用如下命令安装服务
  ```shell
    git clone git@git.avlyun.org:inf/inf-environments.git
    cd inf-environments/ntp
    sh intall.sh
   ```
##时间服务器配置
  ###ntpd conf配置修改
   ```shell
   vi /etc/ntpd.conf 
   #####漂移时间存放文件路径
   driftfile /var/lib/ntp/drift
   #####放行上层time server
   restrict 182.92.12.11 
   #####指定网段内的服务器通过这台NTP Server进行时间同步 nomodify设置client 不能修改 server 时间配置
   restrict 192.168.1.0 mask 255.255.255.0 nomodify
   #####上层时间服务主机设定
    server 182.92.12.11  prefer 
   ```
   
   
