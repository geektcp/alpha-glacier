# 冰川断点续传服务
# 概述
>2020了，国内还长期处于adsl网络环境中，上传至有50KB，下载却可以达到1MB，上传速度是级慢极耗时的。
如果要上传3个小时以上，上传中断是很常见的情形。
这个断点续传程序就是为了解决上传大文件中断的问题。

## 如何使用
先在服务器启动服务端 startup.sh
然后启动客户端，
客户端会扫描配置指定的目录里面的文件并断点上传，
服务端接收文件存入配置文件指定的目录中


## 客户端模式
### 命令行模式
```
用于客户端为Linux服务器，或者Windows服务器
```

### 图形模式
```
使用SWING图形化，也兼容Linux和Windows服务器
```


### 服务端
提供可视化管理控制台；
数据库使用H2库，上传进度记录在数据库中
提供上传进度条日志功能
采用多线程，支持同时上传多个大文件


### 协议
客户端和服务端通信协议采用grpc协议


### 接口设计

- 接口清单
/api/progress    查询上传进度


输入
 ```
 {
     "fileName": "test.zip"
 }
 ```
 
输出：
```
 {
     "fileName": "test.zip",
     "progress": 80, //上传百度比
     "savePath": "/data/upload"
 }
```

### 文件默认存储路径
- 服务端接收文件存储位置
glacier/data/client/

- 服务端接收文件存储位置
glacier/data/server/