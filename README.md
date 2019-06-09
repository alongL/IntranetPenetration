# IntranetPenetration
golang实现的内网穿透



高性能http代理服务器，主要应用与内网穿透。支持多站点配置、客户端与服务端连接中断自动重连，多路传输，大大的提高请求处理速度，go语言编写，无第三方依赖，经过测试内存占用小，普通场景下，仅占用10m内存。


## 特点

- [x] 支持多站点配置
- [x] 断线自动重连
- [x] 支持多路传输,提高并发
- [x] 跨站自动匹配替换


1. 源码安装
> go get github.com/alongL/IntranetPenetration
- 编译（无第三方模块）
> go build

## 使用 
- 服务端 

```
./IntranetPenetration -mode server -vkey DKibZF5TXvic1g3kY -tcpport=8284 -httpport=8024
```

名称 | 含义
---|---
mode | 运行模式(client、server不写默认client)
vkey | 验证密钥
tcpport | 服务端与客户端通信端口
httpport | 代理的http端口（与nginx配合使用）

- 客户端


```
建立配置文件 config.json
```


```
./easyProxy -config config.json  
```


 名称 | 含义
---|---
config | 配置文件路径
## 配置文件config.json

```
{
  "Server": {
    "ip": "123.206.77.88",
    "tcp": 8284,
    "vkey": "DKibZF5TXvic1g3kY",
    "num": 10
  },
  "SiteList": [
    {
      "host": "server1.abc.com",
      "url": "10.1.50.203",
      "port": 80
    },
    {
      "host": "server2.abc.com",
      "url": "10.1.50.196",
      "port": 4000
    }
  ],
  "Replace": 0
}
```
 名称 | 含义
---|---
ip | 服务端ip地址
tcp | 服务端与客户端通信端口
vkey | 验证密钥
num | 服务端与客户端通信连接数
SiteList | 本地解析的域名列表
host | 域名地址
url | 内网代理的地址
port | 内网代理的地址对应的端口




## 操作系统支持  
支持Windows、Linux、MacOSX等，无第三方依赖库。


## 参考
https://github.com/cnlh/nps
