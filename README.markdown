 Storm是一个免费开源、分布式、高容错的实时计算系统。Storm令持续不断的流计算变得容易，弥补了Hadoop批处理所不能满足的实时要求。Storm经常用于在实时分析、在线机器学习、持续计算、分布式远程调用和ETL等领域。Storm的部署管理非常简单，而且，在同类的流式计算工具，Storm的性能也是非常出众的。

    Storm主要分为两种组件Nimbus和Supervisor。这两种组件都是快速失败的，没有状态。任务状态和心跳信息等都保存在Zookeeper上的，提交的代码资源都在本地机器的硬盘上。

Nimbus负责在集群里面发送代码，分配工作给机器，并且监控状态。全局只有一个。
Supervisor会监听分配给它那台机器的工作，根据需要启动/关闭工作进程Worker。每一个要运行Storm的机器上都要部署一个，并且，按照机器的配置设定上面分配的槽位数。
Zookeeper是Storm重点依赖的外部资源。Nimbus和Supervisor甚至实际运行的Worker都是把心跳保存在Zookeeper上的。Nimbus也是根据Zookeerper上的心跳和任务运行状况，进行调度和任务分配的。
Storm提交运行的程序称为Topology。
Topology处理的最小的消息单位是一个Tuple，也就是一个任意对象的数组。
Topology由Spout和Bolt构成。Spout是发出Tuple的结点。Bolt可以随意订阅某个Spout或者Bolt发出的Tuple。Spout和Bolt都统称为component。



## IMPORTANT NOTE!!!
Storm has Moved to Apache. The official Storm git repository is now hosted by Apache, and is mirrored on github here:

[https://github.com/apache/incubator-storm](https://github.com/apache/incubator-storm)


### Contributing
Source code contributions can be submitted either by [sumitting a pull request](https://github.com/apache/incubator-storm/pulls) or by creating an issue in [JIRA](https://issues.apache.org/jira/browse/STORM) and attaching patches.

### Migrating Git Repos from nathanmarz/storm to apache/incubator-storm
If you have an existing fork/clone of nathanmarz/storm, you can migrate to apache/incubator-storm by doing the following:

1. Create a new fork of [apache/incubator-storm]()
2. Point your existing clone to the new fork:


		git remote remove origin
		git remote add origin git@github.com:username/incubator-storm.git



### Issue Tracking
The official issue tracker for Storm is Apache JIRA:

[https://issues.apache.org/jira/browse/STORM](https://issues.apache.org/jira/browse/STORM)



### User Mailing List
Storm users should send messages and subscribe to [user@storm.incubator.apache.org](mailto:user@storm.incubator.apache.org).

You can subscribe to this list by sending an email to [user-subscribe@storm.incubator.apache.org](mailto:user-subscribe@storm.incubator.apache.org). Likewise, you can cancel a subscription by sending an email to [user-unsubscribe@storm.incubator.apache.org](mailto:user-unsubscribe@storm.incubator.apache.org).

You can view the archives of the mailing list [here](http://mail-archives.apache.org/mod_mbox/incubator-storm-user/).

### Developer Mailing List
Storm developers should send messages and subscribe to [dev@storm.incubator.apache.org](mailto:dev@storm.incubator.apache.org).

You can subscribe to this list by sending an email to [dev-subscribe@storm.incubator.apache.org](mailto:dev-subscribe@storm.incubator.apache.org). Likewise, you can cancel a subscription by sending an email to [dev-unsubscribe@storm.incubator.apache.org](mailto:dev-unsubscribe@storm.incubator.apache.org).

You can view the archives of the mailing list [here](http://mail-archives.apache.org/mod_mbox/incubator-storm-dev/).

### Which list should I send/subscribe to?
If you are using a pre-built binary distribution of Storm, then chances are you should send questions, comments, storm-related announcements, etc. to [user@storm.apache.incubator.org](user@storm.apache.incubator.org). 

If you are building storm from source, developing new features, or otherwise hacking storm source code, then [dev@storm.incubator.apache.org](dev@storm.incubator.apache.org) is more appropriate. 

### What will happen with storm-user@googlegroups.com?
All existing messages will remain archived there, and can be accessed/searched [here](https://groups.google.com/forum/#!forum/storm-user).

New messages sent to storm-user@googlegroups.com will either be rejected/bounced or replied to with a message to direct the email to the appropriate Apache-hosted group.
