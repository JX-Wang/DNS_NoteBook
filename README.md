# DNS_NoteBook
This is a repo for recording DNS knowledge
#### 1. Root DNS Server  
根DNS服务器全球有13台，以A~M字母命令，方便管理，域名格式为```字母.root-servers.net```，中国地区没有根DNS服务器，亚洲唯一的一台根DNS服务器在```日本，东京```，由WIDE Project管理，全球的```root-server```分布在[Here](https://root-servers.org/)，所有的根DNS服务器都是以维护一份根域文件（Root Zone file，文件命名为root.zone）来返回顶级域名对应的权威服务器(包括通用顶级域和国家顶级域，很多大型公司都有自己的TLD，比如奇虎360，百度，IBM等)，这份文件大小为2MB，
