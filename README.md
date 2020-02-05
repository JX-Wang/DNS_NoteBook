# DNS_NoteBook
This is a repo for recording DNS knowledge
### 1. Root DNS Server  
> 根DNS服务器全球有13台，以A~M字母命令，方便管理，域名格式为```字母.root-servers.net```，中国地区没有根DNS服务器，大部分根DNS服务器在美国，亚洲唯一的一台根DNS服务器在```日本，东京```，由WIDE Project管理，全球的```root-server```分布情况[Here](https://root-servers.org/)，所有的根DNS服务器都是以维护一份根域文件（Root Zone file，文件命名为root.zone）来返回顶级域名对应的权威服务器(包括通用顶级域和国家顶级域，很多大型公司都有自己的TLD，比如奇虎360，百度，IBM等)，这份文件大小为```2MB```左右，截至到2017年9月，一共记录大概有1500+个顶级域，没有被收录的顶级域不会参与DNS解析过程  
### 2. Root DNS 镜像
> 为了分担全球DNS解析的压力，提供更快的服务，现在通过任播技术架设DNS镜像服务器来分担全世界的DNS解析服务，所以现在实时运行的```Root DNS Server```数量远远大于13台，截至2019年8月，全球共有1008台Root DNS Server在为全世界的DNS解析提供服务
> 中国的Root DNS 镜像
### 3. 任播技术


