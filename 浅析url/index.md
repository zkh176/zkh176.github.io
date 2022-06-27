# 浅析URL


URL的组成

URL：中文意思为统一资源定位符、英语：Uniform Resource Locator，是因特网上标准的资源的地址（Address），如同在网络上的门牌。它最初是由蒂姆·伯纳斯-李发明用来作为万维网的地址，现在它已经被万维网联盟编制为因特网标准RFC 1738。

由以下这些部分组成

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/40dd3ae68b7847958ec67baf4bd28c29~tplv-k3u1fbpfcp-zoom-1.image)

\


***

## DNS的作用

1.  将域名解析为IP 地址；
1.  客户端向DNS服务器（DNS服务器有自己的IP地址）发送域名查询请求；
1.  DNS服务器告知客户机Web服务器的IP 地址；
1.  客户机与Web 服务器通信。

***

## nslookup的作用

以百度为例使用cmder 输入nslookup [www.baidu.com](https://link.juejin.cn/?target=http%3A%2F%2Fwww.baidu.com) 便会出现下面各项反应： nslookup [www.baidu.com](https://link.juejin.cn/?target=http%3A%2F%2Fwww.baidu.com) 服务器: UnKnown Address: 192.168.1.1 非权威应答: 名称: [www.a.shifen.com](https://link.juejin.cn/?target=http%3A%2F%2Fwww.a.shifen.com) Addresses: 110.242.68.3 110.242.68.4 Aliases: [www.baidu.com](https://link.juejin.cn/?target=http%3A%2F%2Fwww.baidu.com)

***

\


## IP

英文全称:Internet Protocal

作用：

1.  如何定位一台设备。
1.  如何封装数据报文，以跟其他设备交流。

特殊IP：

1.  127.0.0.1表示自己。
1.  localhost通过hosts指定为自己。
1.  0.0.0.0不表示任何设备。

***

## PING命令

PING：（Packet Internet Groper），因特网包探索器，用于测试网络连接量的程序 。ping 是工作在 TCP/IP 网络体系结构中应用层的一个服务命令， 主要是向特定的目的主机发送 ICMP（Internet Control Message Protocol 因特网报文控制协议）Echo 请求报文，测试目的站是否可达及了解其有关状态。

用法：

以百度为例使用cmder输入ping baidu.com表会出现以下示例：

λ ping [baidu.com](http://baidu.com/)

\


正在 Ping [baidu.com](http://baidu.com/) [220.181.38.251] 具有 32 字节的数据:

来自 220.181.38.251 的回复: 字节=32 时间=41ms TTL=52

来自 220.181.38.251 的回复: 字节=32 时间=40ms TTL=52

来自 220.181.38.251 的回复: 字节=32 时间=40ms TTL=52

来自 220.181.38.251 的回复: 字节=32 时间=42ms TTL=52

\


220.181.38.251 的 Ping 统计信息:

数据包: 已发送 = 4，已接收 = 4，丢失 = 0 (0% 丢失)，

往返行程的估计时间(以毫秒为单位):

最短 = 40ms，最长 = 42ms，平均 = 40ms

\


***

## 域名

域名是什么：

以.com、.nei、.ort结尾的字符串，域名就是对IP的别称。一个域名可以对应不同的IP，这叫均衡负载，防止一台机器扛不住，一个IP也可以对应不同的域名。

\


域名的分类：

1.  域名的第一级是[顶级域]，它包括[通用顶级域]，例如[.com]、[.net]和[.org]；以及[国家和地区顶级域]，例如[.us]。
1.  baidu.com是二级域名（俗称一级域名）。
1.  www.baidu.com是三级域名（俗称二级域名）。
