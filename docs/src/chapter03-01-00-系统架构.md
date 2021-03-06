## 系统架构

Flink是一个用于有状态的并行数据流处理的分布式系统。它由多个进程构成，这些进程一般会分布运行在不同的机器上。对于分布式系统来说，面对的常见问题有：集群中资源的分配和管理、进程协调调度、持久化和高可用的数据存储，以及故障恢复。

对于这些分布式系统的经典问题，业内已有比较成熟的解决方案和服务。所以Flink并不会自己去处理所有的问题，而是利用了现有的集群架构和服务，这样它就可以把精力集中在核心工作——分布式数据流处理上了。Flink与一些集群资源管理工具有很好的集成，比如Apache Mesos、YARN和Kubernetes；同时，也可以配置为独立（stand-alone）集群运行。Flink自己并不提供持久化的分布式存储，而是直接利用了已有的分布式文件系统（比如HDFS）或者对象存储（比如S3）。对于高可用的配置，Flink需要依靠Apache ZooKeeper来完成。

在本节中，我们将介绍Flink的不同组件，以及在运行程序时它们如何相互作用。我们会讨论部署Flink应用程序的两种模式，并且了解每种模式下分发和执行任务的方式。最后，我们还会解释一下Flink的高可用性模式是如何工作的。

