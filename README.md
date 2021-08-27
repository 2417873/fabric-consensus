# fabric-consensus
orderer节点的集群工作模式，consensus部分包含共识插件的主要逻辑实现，配合其他集群通信、多通道处理、账本资源处理、proto等部分。

1.cluster通信：在orderer中使用了两个rpc服务，一个用于与peer节点通信，一个用于orderer节点间通信，cluster指orderer节点间通信部分，
2.Orderer消息过滤：包括了合法性验证、安全验证等
3.Raft接入逻辑：包括整个共识插件接入时对于交易的消息，如何进入共识层、使用chainsupport打包、共识、执行等处理的逻辑，可以参考raft如何实现chain接口。
通道处理：包括消息如何分配给相对应的通道，系统通道对应用通道的管理。
4.Orderer启动：启动过程涉及初始化各种资源，rpc资源、账本资源、存储，未正常启动的inactive的链实例。
5.共识的proto：在整个排序过程中都会大量用到，保存节点id、交易id、证书等，参考raft的proto设计。
