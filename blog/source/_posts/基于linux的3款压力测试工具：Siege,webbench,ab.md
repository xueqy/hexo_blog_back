### 基于linux的3款压力测试工具：Siege,webbench,ab
1.Siege
一款开源的压力测试工具，可以根据配置对一个WEB站点进行多用户的并发访问，记录每个用户所有请求过程的相应时间，并在一定数量的并发访问下重复进行。
获取：http://www.joedog.org/
官方提供ftp下载

解压：
``` # tar -zxf siege-latest.tar.gz```
进入解压目录：
``` # cd siege-2.65/```
安装：
``` #./configure ; make``` 

有时下面的一步会出错,如果出错了可以``` apt-get  install gcc``` 安装一下gcc
``` #make install```

使用
``` siege -c 200 -r 10 -f example.url```
-c是并发量，-r是重复次数。 url文件就是一个文本，每行都是一个url，它会从里面随机访问的。

example.url内容:

http://www.taoav.com
http://www.tuhaoduo.com
http://www.tiaonv.com

结果说明
>Lifting the server siege… done.
Transactions: 3419263 hits //完成419263次处理
Availability: 100.00 % //100.00 % 成功率
Elapsed time: 5999.69 secs //总共用时
Data transferred: 84273.91 MB //共数据传输84273.91 MB
Response time: 0.37 secs //相应用时1.65秒：显示网络连接的速度
Transaction rate: 569.91 trans/sec //均每秒完成 569.91 次处理：表示服务器后
Throughput: 14.05 MB/sec //平均每秒传送数据
Concurrency: 213.42 //实际最高并发数
Successful transactions: 2564081 //成功处理次数
Failed transactions: 11 //失败处理次数
Longest transaction: 29.04 //每次传输所花最长时间
Shortest transaction: 0.00 //每次传输所花最短时间

**2.webbench**

获取并安装
``` 
wget http://home.tiscali.cz:8080/~cz210552/distfiles/webbench-1.5.tar.gz
tar zxvf webbench-1.5.tar.gz
cd webbench-1.5
make && make install
``` 
**ab 已经介绍过了在我的blog中**