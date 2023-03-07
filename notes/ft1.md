## Fault Tolerance 

### Split Brain

Server 1 跟 Server 2 中间的网络通信断了  
与此同时  
Client 1 只能跟 Server 1 通信
Client 2 只能跟 Server 2 通信  

client 1 发送 set 请求到 Server 1
client 2 发送 set 请求到 Server 2  
两台机器在没有中间网络共识的情况下都会认为自己是 Primary 的 Server  
对于这种情况：
1. 等待 2 台服务器重新共识，放弃容错性
2. 等待 1 台服务器的返回，放弃正确性  

第二种不正确的返回结果就叫做 Split Brain 脑裂  


### Majority Votes  

2 of 3  
如果你有 2f+1 台机器，就可以容忍 f 台机器宕机/停机   

Raft 有一个特点比其他的特点重要：  
上次选举的 Majority 必然与这次选举的 Majority 有重叠的部分（两个大于 1/2 的集合必然存在交集）   
新产生的 Leader 都可以保证知道上一任 Leader 的 term   







