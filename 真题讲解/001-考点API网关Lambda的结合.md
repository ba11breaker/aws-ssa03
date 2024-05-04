# 真题解析

A solutions architect is designing a a new service behind `Amazon API Gateway`. The request patterns for the service will be `unpredicatable` and can change suddenly from 0 requests to `over 500 per second`. `The total size of the data that needs to be persisted in a backend database is currently less than 1 GB` with `unpredicatable` future growth Data can be queried using `simple key-value` requests. Which combination of AWS services would meet these  requirements? (select Two)

```
A. AWS Fargate
B. AWS Lambda
C. Amazon DynamoDB
D. Amazan EC2 Auto Scaling
E. MySQL compatible Amazon Aurora
```

## 分析
```
AWS Fargate - 容器管理服务
AWS Lambda - Serverless计算服务
Amazon DynamoDB - key-value性数据库
Amazan EC2 Auto Scaling - 虚拟机
MySQL compatible Amazon Aurora - 兼容SQL的Aurora数据库
```

首先排除D，因为需要key-value非关系型数据库，所以先选C，再排除A和D。因为 `can change suddenly from 0 requests to over 500 per second`, 只有lambda才可以满足。

0 -> 500 -> 1000/

A和D不是不行，但是A和D的启动时间偏慢。

EC2的启动时间以分钟为计量单位，Lambda以秒为计量单位。

### AWS Fargate

https://aws.amazon.com/fargate/

AWS Fargate 是 Amazon Web Services 提供的一种无服务器计算引擎，用于运行容器。Fargate 让用户能够运行容器而无需管理服务器或集群，这简化了容器的部署和管理过程。

以下是 AWS Fargate 的一些主要特点：

- 无服务器架构：Fargate 允许用户专注于应用程序的构建和部署，而不用担心底层的服务器或集群的管理。这意味着不需要选择服务器类型、决定何时扩展集群或优化集群管理。
- 易于使用：通过 Fargate，用户只需指定应用程序的CPU和内存需求，选择网络和身份管理政策，Fargate 就会处理剩余的部署和扩展过程。
成本效益：与传统的容器管理服务相比，Fargate 允许按实际使用的计算资源付费，而不是按预配置的服务器大小付费，这有助于优化成本。
- 安全：Fargate 在隔离环境中运行每个容器，提供任务级的安全隔离。此外，还集成了 AWS 的各种安全服务，如IAM（Identity and Access Management）用于- 精细控制访问权限。
- 集成：Fargate 与 AWS 的其他服务高度集成，如 Elastic Container Service (ECS) 和 Elastic Kubernetes Service (EKS)，这为运行基于容器的应用程序提供了灵活性。
- 可扩展性：Fargate 支持自动扩展，可以根据设定的指标自动增加或减少任务的数量，确保应用程序按需快速扩展。