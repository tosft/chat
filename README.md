# chat(聊天）
[![Build Status](https://travis-ci.org/GameGophers/chat.svg)](https://travis-ci.org/GameGophers/chat)

## 设计理念

     EndPoint:  消息收发点（对应到一个玩家的聊天，或者一个联盟聊天） 
     PubSub: 对任意EndPoint进行发布，订阅

聊天服务器并不关心一个EndPoint对应的是一个玩家，还是一个联盟，需要在游戏逻辑中自己管理。     
通常在玩家注册的时候，会创建一个EndPoint，创建一个联盟的时候，也会创建一个EndPoint。     
玩家登陆后，会订阅到自己的EndPoint和所属联盟的EndPoint，以便接受实时聊天消息。      
CHAT会保留一定数量的消息在内存中（默认128条），这个消息队列会定期持久化到本地磁盘，以便重启时候加载 。      

