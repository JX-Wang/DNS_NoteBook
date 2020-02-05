# DNS_NoteBook
This is a repo for recording DNS knowledge

### 1. Root DNS Server  
> 根DNS服务器全球有13台，以A~M字母命令，方便管理，域名格式为```字母.root-servers.net```，中国地区没有根DNS服务器，大部分根DNS服务器在美国，亚洲唯一的一台根DNS服务器在```日本，东京```，由WIDE Project管理，全球的```root-server```分布情况[Here](https://root-servers.org/)，所有的根DNS服务器都是以维护一份根域文件（Root Zone file，文件命名为root.zone）来返回顶级域名对应的权威服务器(包括通用顶级域和国家顶级域，很多大型公司都有自己的TLD，比如奇虎360，百度，IBM等)，这份文件大小为```2MB```左右，截至到2017年9月，一共记录大概有1500+个顶级域，没有被收录的顶级域不会参与DNS解析过程.  

### 2. Root DNS 镜像
> 为了分担全球DNS解析的压力，提供更快的服务，现在通过任播技术架设DNS镜像服务器来分担全世界的DNS解析服务，所以现在实时运行的```Root DNS Server```数量远远大于13台，截至2020年2月5日，全球共有1039台Root DNS Server在为全世界的DNS解析提供服务.  
> 中国的```Root DNS Server```，截止时间2020年2月5日在[IANA](https://root-servers.org/)官网所展示的中国内包含的```Root DNS Server镜像```有```L, K, J, F, I, E, A, H```这八种，主要集中在北京市(5)，香港(9)和台北市(6)，其中杭州(1)，上海(1)，武汉(1)，郑州(1)，贵阳(1)和西宁市(1)，之前因为中国大陆境内多次的DNS污染影响到了外网，所以中国境内的```Root DNS Server```曾经被关停一段时间，emmmmmmm，应该是GFW的原因.  

### 3. 任播 anycast
> 每一个地址对应一群接收节点，不同于广播和多播的是，每一次发送只允许其中一个链路上最优结点接收发送端发来的消息，任播的好处有负载均衡，提高冗余性，安全性，用户层面能提高客户端的响应速度.  
