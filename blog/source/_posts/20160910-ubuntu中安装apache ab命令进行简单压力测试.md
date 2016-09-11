---
title: ubuntu中安装apache ab命令进行简单压力测试
permalink: ubuntu中安装apache ab命令进行简单压力测试
comments: true
date: 2016-09-10 22:30:00
toc: true
tags:
   - linux
description: ubuntu中安装apache ab命令进行简单压力测试
---
&emsp;&emsp; ubuntu中安装apache ab命令进行简单压力测试
<!-- more -->
###  ubuntu中安装apache ab命令进行简单压力测试
#### 1. 安裝ab命令

sudo apt-get install apache2-utils 

#### 2.ab命令参数说明

```

    Usage: ab [options] [http[s]://]hostname[:port]/path  
    Options are:  
      
    //总的请求数   
    -n requests Number of requests to perform宅   
      
    //一次同时并发的请求数 总的请求数(n)=次数*一次并发数(c)   
    -c concurrency Number of multiple requests to make  
      
    -t timelimit Seconds to max. wait for responses  
    -b windowsize Size of TCP send/receive buffer, in bytes  
    -p postfile File containing data to POST. Remember also to set -T  
    -u putfile File containing data to PUT. Remember also to set -T  
    -T content-type Content-type header for POSTing, eg.  
    'application/x-www-form-urlencoded'  
    Default is 'text/plain'  
    -v verbosity How much troubleshooting info to print  
    -w Print out results in HTML tables  
    -i Use HEAD instead of GET  
    -x attributes String to insert as table attributes  
    -y attributes String to insert as tr attributes  
    -z attributes String to insert as td or th attributes  
    -C attribute Add cookie, eg. 'Apache=1234. (repeatable)  
    -H attribute Add Arbitrary header line, eg. 'Accept-Encoding: gzip'  
    Inserted after all normal header lines. (repeatable)  
    -A attribute Add Basic WWW Authentication, the attributes  
    are a colon separated username and password.  
    -P attribute Add Basic Proxy Authentication, the attributes  
    are a colon separated username and password.  
    -X proxy:port Proxyserver and port number to use  
    -V Print version number and exit  
    -k Use HTTP KeepAlive feature  
    -d Do not show percentiles served table.  
    -S Do not show confidence estimators and warnings.  
    -g filename Output collected data to gnuplot format file.  
    -e filename Output CSV file with percentages served  
    -r Don't exit on socket receive errors.  
    -h Display usage information (this message)  
    -Z ciphersuite Specify SSL/TLS cipher suite (See openssl ciphers)  
    -f protocol Specify SSL/TLS protocol (SSL2, SSL3, TLS1, or ALL)  
```
#### 3.运行 ab -n 100 -c 10 http://www.meetu.hk/ 对 http://www.meetu.hk/ 进行100次请求，10个并发请求压力测试结果。

```

    Server Software: lighttpd/1.4.20  
    Server Hostname: www.meetu.hk  
    Server Port: 80  
      
    Document Path: /  
    Document Length: 2095 bytes  
      
    Concurrency Level: 10  
      
    //整个测试持续的时间   
    Time taken for tests: 3.303 seconds  
      
    //完成的请求数量   
    Complete requests: 100  
    Failed requests: 0  
    Write errors: 0  
    Total transferred: 235200 bytes  
    HTML transferred: 209500 bytes  
      
    //平均每秒处理30个请求   
    Requests per second: 30.27 [#/sec] (mean)  
      
    //平均每个请求处理时间为330毫秒 注:这里将一次10个并发请求看成一个整体   
    Time per request: 330.335 [ms] (mean)  
      
    //平均每个并发请求处理 时间 为33毫秒   
    Time per request: 33.034 [ms] (mean, across all concurrent requests)  
    Transfer rate: 69.53 [Kbytes/sec] received  
      
    Connection Times (ms)  
    min mean[+/-sd] median max  
    Connect: 51 170 35.9 178 230  
    Processing: 60 153 64.5 121 263  
    Waiting: 55 148 64.4 115 258  
    Total: 235 322 59.9 299 437  
      
    Percentage of the requests served within a certain time (ms)  
      
    //在这100个请求中有50%在299毫秒内完成   
    50% 299  
      
    //在这100个请求中有66%在312毫秒内完成   
    66% 312  
    75% 383  
    80% 412  
    90% 431  
    95% 432  
    98% 436  
    99% 437  
    100% 437 (longest request)  
```
