# Http 介绍

HTTP Hyper Text Transfer Protocol 超文本传输协议

## 前置知识

### IP

- IP ： Internet Protocol 互联网协议 ① 如何定位一台设备 ② 如何封装数据报文，以跟其他设备交流
- 内网，外网：内部连接路由器的设备连接内网，路由器连接的 DNS 和运营服务商是外网
- 外网 IP :通过路由器连接如电信等运营服务商的服务器，就可以获得一个外网 IP，如“14.17.32.211"，重启路由器可能获得一个新的外网 IP
- 内网 IP :路由器创建的内网会给自己分配一个内网 IP,然后给每一个设备分配一个内网 IP
- 路由器也称网关，内网外网互相访问需要路由器
- 特殊的 IP
  127.0.0.1 表示自己
  localhost 通过 hosts 指定为自己
  0.0.0.0 不表示任何设备

### 端口

- 一台机器可以提供很多服务，每个服务一个号码，这个号码就是端口
- 要提供 HTTP 服务最后使用 80 端口，HTTPS 最好 443，FTP 最好 21，一共 65535 个端口，具体什么服务对应什么端口查询维基百科，一般 0-1023 是系统使用，平常使用 8080 测试网页

#### IP 用来定位设备，端口用来确定服务，两者缺一不可

### 域名 IP

- 对 IP 的别称，一个域名可以对应不同 IP,称为均衡负载，一个 IP 可以对应不同域名，称为共享主机
- 域名和 IP 是通过 DNS 对应起来的
- nslookup 看域名对应的 IP 地址
- **输入一个网站如 baidu.com 发生了什么**
  你的 Chrome 浏览器会向电信/联通提供的 DNS 服务器询问 baidu.com 对应什么 IP
  电信/联通会回答一个 IP
  然后 Chrome 会回答对应 IP 的 80/443 端口发送请求
  请求内容是查看 baidu.com 的网页

- 相同域名不同路径可以到不同网页，同一页面查询参数可以进入到特定网页 ？，同一页面设置锚点可以进入特定内容

### URL 统一资源定位符

- 举例分析
  https://www.baidu.com/s?wd=hello&rsv_spt=1#5
  协议 域名 路径 查询参数 锚点
  URL 协议+域名或 IP+端口号+路径+查询字符串+锚点

### curl 命令

- curl -v http://baidu.com 发送 HTTP 请求 默认 Get 加-X POST 为 Post,详情 curl -help

## HTTP 详解

### 使用 nodejs 实现一个简单的 http server

[项目地址](https://github.com/HITLiBo/nodejs-http-server)

- 请求
  请求动词 路径加查询参数 协议名/版本
  Host:域名或 IP
  Accept:表示我想接受什么格式的文件，一般是 text/html
  Content-Type:请求体的格式
  回车空行
  请求体（上传内容）
  一般 Get 无请求体，大小写不敏感

- 响应
  协议名/版本 状态码 OK
  Date:日期
  Connetion:
  Keep-Alive:
  Transfer-Encoding:
  回车空行
  响应体（下载内容）
