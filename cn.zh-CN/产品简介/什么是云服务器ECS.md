# 什么是云服务器ECS {#concept_rhf_xgv_tdb .concept}

通过本文档，您可以了解什么是阿里云云服务器ECS，以及它所涉及的资源和服务。

云服务器Elastic Compute Service（ECS）是阿里云提供的一种基础云计算服务。使用云服务器ECS就像使用水、电、煤气等资源一样便捷、高效。您无需提前采购硬件设备，而是根据业务需要，随时创建所需数量的云服务器ECS实例。在使用过程中，随着业务的扩展，您可以随时扩容磁盘、增加带宽。如果不再需要云服务器，也能随时释放资源，节省费用。

下图列出了ECS涉及的所有资源，包括实例规格、块存储、镜像、快照、带宽和安全组。您可以通过 [云服务器管理控制台](https://ecs.console.aliyun.com/#/home)或者 [阿里云 App](https://help.aliyun.com/product/48842.html) 配置您的ECS资源。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9543/4794_zh-CN.png)

## 相关概念 {#section_jkn_4qj_ydb .section}

在使用ECS之前，您需要了解以下概念：

-   [地域和可用区](https://help.aliyun.com/document_detail/40654.html)：是指ECS资源所在的物理位置。
-   [实例](cn.zh-CN/产品简介/实例.md#)：等同于一台虚拟机，包含CPU、内存、操作系统、网络、磁盘等最基础的计算组件。
-   [实例规格](cn.zh-CN/产品简介/实例规格族.md#)：是指实例的不同配置，包括vCPU核数、内存、网络性能等。实例规格决定了ECS实例的计算和存储能力。
-   [镜像](cn.zh-CN/产品简介/镜像.md#)：是指ECS实例运行环境的模板，一般包括操作系统和预装的软件。操作系统支持多种Linux发行版本和不同的Windows版本。
-   [块存储](cn.zh-CN/产品简介/块存储.md#)：包括基于分布式存储架构的 [弹性块存储](cn.zh-CN/产品简介/块存储/弹性块存储.md#)，以及基于物理机本地硬盘的 [本地存储](cn.zh-CN/产品简介/块存储/本地存储.md#)。
-   [快照](cn.zh-CN/产品简介/快照.md#)：是指某一个时间点上一块弹性块存储的数据备份。
-   [网络类型](cn.zh-CN/产品简介/网络和安全性/网络类型.md#)：包括
    -   专有网络：基于阿里云构建的一个隔离的网络环境，专有网络之间逻辑上彻底隔离。更多信息，请参考 [专有网络VPC](../../cn.zh-CN/产品简介/什么是专有网络.md#)。
    -   经典网络：统一部署在阿里云公共基础内，规划和管理由阿里云负责。
-   [安全组](cn.zh-CN/产品简介/网络和安全性/安全组.md#)：由同一地域内具有相同保护需求并相互信任的实例组成，是一种虚拟防火墙，用于设置不同实例的网络访问控制。
-   [SSH 密钥对](cn.zh-CN/产品简介/网络和安全性/SSH 密钥对.md#) ：远程登录Linux ECS实例的验证方式，阿里云存储公钥，您需要自己妥善保管私钥。您也可以选择使用 [用户名密码](../cn.zh-CN/用户指南/连接实例/使用用户名密码验证连接 Linux 实例.md#) 验证登录Linux ECS实例。
-   IP地址：包括用于 [内网通信](cn.zh-CN/产品简介/网络和安全性/内网.md#) 的内网IP或私有IP，以及用于访问Internet的公网IP。
-   [弹性公网IP](https://help.aliyun.com/product/61789.html)：可以与实例反复绑定或解绑的静态公网IP地址。
-   [云服务器管理控制台](https://ecs.console.aliyun.com/#/home)：是指ECS的Web操作界面。
-   [云服务器管理控制台](https://partners-intl.console.aliyun.com/#/ecs)：是指ECS的Web操作界面。

## 相关服务 {#section_cdb_tqj_ydb .section}

您可以从 [云市场](https://market.aliyun.com/) 获取由第三方服务商提供的基础软件、企业软件、网站建设、代运维、云安全、数据及API、解决方案等相关的各类软件和服务。您也可以成为云市场服务供应商。更多信息，请参考 [云市场文档](https://help.aliyun.com/product/30488.html)。

您可以根据业务需求和策略的变化自动调整ECS资源。更多信息，请参考 [弹性伸缩文档](https://help.aliyun.com/product/25855.html)。

您可以在一组云服务器ECS上通过Docker容器管理应用生命周期。更多信息，请参考 [容器服务（Container Service）文档](https://help.aliyun.com/product/25972.html)。

您可以对多台云服务器ECS进行流量分发的负载均衡服务。更多信息，请参考 [负载均衡（Server Load Balancer）文档](https://help.aliyun.com/product/27537.html)。

您可以监控ECS实例、系统盘和公网带宽等。更多信息，请参考 [云监控（CloudMonitor）文档](https://help.aliyun.com/product/28572.html)。

您可以使用安骑士保障云服务器ECS的安全。更多信息，请参考 [安骑士文档](https://help.aliyun.com/product/28449.html)。

对于部署在云服务器ECS上的应用，阿里云为您提供了免费的 [DDoS基础防护](https://help.aliyun.com/document_detail/55256.html)，您也可以使用DDoS高防IP保障源站的稳定可靠。更多信息，请参考 [DDoS基础防护文档](https://help.aliyun.com/product/28396.html) 和 [DDoS高防IP文档](https://help.aliyun.com/product/28461.html)。

您可以编写代码调用阿里云开发者工具包（SDK）访问阿里云的产品和服务，更多信息，请参考 [阿里云开发工具包\(SDK\)](https://develop.aliyun.com/tools/sdk?#/java)。您可以使用 [OpenAPI Explorer](https://api.aliyun.com/) 在线调试ECS API，并生成对应SDK Demo代码。

## 使用ECS {#section_lsd_yqj_ydb .section}

阿里云提供了Web服务页面，方便您管理云服务器ECS。您可以登录 [ECS管理控制台](https://ecs.console.aliyun.com/#/home) 操作ECS实例。关于管理控制台的操作，请参考 [操作指南](../cn.zh-CN/用户指南/常用操作导航.md#)。

阿里云也提供了API接口方便您管理云服务器ECS。关于API说明，请参考 [API参考](../cn.zh-CN/API参考/简介.md#)。您也可以使用阿里云命令行工具CLI（Alibaba Cloud CLI）调用API管理ECS，更多信息，请参考 [命令行工具CLI](https://help.aliyun.com/product/29991.html)。

## ECS定价 {#section_vq5_brj_ydb .section}

ECS支持预付费和按量付费。更多信息，请参考 [产品计价](../cn.zh-CN/产品定价/计费概述.md#) 文档。

ECS及相关资源的价格信息，请参考 [云产品定价页](https://www.aliyun.com/price/product#/ecs/detail)。

