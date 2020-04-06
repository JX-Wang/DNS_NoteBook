# DNS_NoteBook
This is a repo for recording DNS knowledge



### DNS（Domain Name System）
这篇文章属于DNS笔记系列，但是不会介绍最基本的DNS知识，较偏向DNS细节和进阶，但是会包含基础的DNS原理，新手可以阅读，但可能会有一些困难，希望本文能带给大家些许帮助

### 1. Root DNS Server  
根DNS服务器属于DNS系统中最重要的基础设施，负责最基本的解析工作，根DNS服务器全球有13台，以A~M字母命令，为方便管理，其域名格式为```字母.root-servers.net```，中国地区没有根DNS服务器，大部分根DNS服务器在美国，亚洲唯一的一台根DNS服务器在```日本，东京```，由```WIDE Project```进行管理，全球的```root-server```分布情况见 [IANA](https://root-servers.org/)，所有的根DNS服务器都是以维护一份根域文件（Root Zone file，文件命名为root.zone）来返回顶级域名对应的权威服务器（包括通用顶级域和国家顶级域，很多大型公司都有自己的TLD，比如IBM等），这份根域文件文件大小为```2MB```左右，截至到2020年2月4日，共记录有1516个顶级域（数据来自 [IANA](https://data.iana.org/TLD/tlds-alpha-by-domain.txt)），没有被收录的顶级域不会参与DNS解析过程. 

### 2. Root DNS 镜像
为了分担全球DNS解析的压力，提供更快的服务，现在通过任播技术架设DNS镜像服务器来分担全世界的DNS解析服务，所以现在实时运行的```Root DNS Server```数量远远大于13台，截至2020年2月5日，全球共有1039台Root DNS Server在为全世界的DNS解析提供服务.  

来说说中国的```Root DNS Server```，截止时间2020年2月5日在 [IANA](https://root-servers.org/) 官网所展示的中国包含的```Root DNS Server镜像```有```L, K, J, F, I, E, A, H```这八种，主要分布在北京市(5，J，F，K，L，I)，香港(9，I，A，J，H，（3，F），（2，E）)和台北市(6，E，I，L，K，（2，F）)，其中杭州(1，F)，上海(1，I)，武汉(1，L)，郑州(1，L)，贵阳(1，K)和西宁市(1，L)
![中国根DNS镜像](https://img-blog.csdnimg.cn/20200206145811769.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dVX0RFTkc5NDk1,size_16,color_FFFFFF,t_70)
图中最下面的数字16包含了越南首都河内（Hanoi）的一台根DNS镜像服务器，所以数量应为15，目前中国的 ```Root DNS Mirror Server```数量应该为26台.
![CNBEIJINGDNSMirror](https://img-blog.csdnimg.cn/20200206151647694.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dVX0RFTkc5NDk1,size_16,color_FFFFFF,t_70)
之前因为中国大陆境内多次的DNS污染影响到了外网，所以中国大陆境内的```Root DNS Server```曾经被关停一段时间，不过目前现在中国大陆境内仍有```F、I、J、L```这4个根域的6台DNS镜像（```L```有三台镜像）在提供服务. 

### 3. 任播 anycast
根DNS镜像采用任播技术实现了对全球13台根DNS服务器的扩充，什么是任播呢，简单来说就是每一个地址对应一群接收节点，不同于广播和多播的是，每一次发送只允许其中一个链路上最优结点接收发送端发来的消息
![多种路由策略](https://img-blog.csdnimg.cn/20200206153713503.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1dVX0RFTkc5NDk1,size_16,color_FFFFFF,t_70)
任播的好处有负载均衡，提高冗余性，安全性，用户层面能提高客户端的响应速度.  

### 4. Root Zone 文件
```Root Zone```文件记录了全球的顶级域的DNS信息，通过```Http```协议可以在 [Internic](http://www.internic.net/domain/root.zone) 下载```Root Zone```文件，同时也可以通过```FTP```下载，其格式如下（部分为例） 

TLD  |  TTL |   Internet|  Record Type | Record Value
---|---|---|---|---
dnsc.ad.	|	172800 |  IN  |   A        |  194.158.74.10
dnsc.ad.   |  172800 |   IN  |  AAAA |  2a02:8060:32fa:0:0:0:0:b
dnsm.ad.  |	172800 | 	IN  |  A         |  194.158.74.9
dnsm.ad.  |	172800 |	IN  |	AAAA   |   2a02:8060:32fa:0:0:0:0:a
adac.        |	172800 |	IN  |	NS       |	a.nic.adac.
adac.        |	172800 |	IN  |	NS       |	b.nic.adac.
adac.        |	172800 |	IN  |	NS       |	c.nic.adac.
adac.        |	172800 |	IN  |	NS       |	d.nic.adac.

更多DNS记录类型以及相关规定可在 [RFC1035](https://tools.ietf.org/html/rfc1035) 进行查询

### 5. waitting
