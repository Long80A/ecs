# DDoS基础防护 {#concept_j1h_3rw_ydb .concept}

阿里云云盾默认为ECS实例免费提供5 Gbit/s恶意流量攻击，即 DDoS基础防护能力。这一功能可以有效防止云服务器ECS实例受到恶意攻击，从而保证ECS系统的稳定，即当流入ECS实例的流量超出实例规格对应的限制时，云盾就会帮助ECS实例限流，避免ECS系统出现问题。

## DDoS基础防护工作原理 {#section_qxq_3rw_ydb .section}

启用DDoS基础防护后，云盾会实时监控进入ECS实例的流量。当监测到超大流量或者包括DDoS攻击在内的异常流量时，在不影响正常业务的前提下，云盾会将可疑流量从原始网络路径中重定向到净化产品上，识别并剥离恶意流量，并将还原的合法流量回注到原始网络中转发给目标ECS实例。这一过程，就是 **流量清洗**。更详细的信息，请参见 DDoS基础防护 -产品架构。

**说明：** 启用了DDoS基础防护的ECS实例，当来自互联网的流量大于5 Gbit/s时，为保护整个集群的安全，阿里云会让相应ECS实例进入黑洞，丢弃进入该实例的所有流量，屏蔽公网对它的所有访问。详细信息，请参见 DDoS防护指南 -阿里云黑洞策略。

流量清洗的触发条件包括：

-   流量模型的特征。当流量符合攻击流量特征时，就会触发清洗。
-   流量大小。DDoS攻击一般流量都非常大，通常都以Gbit/s为单位，因此，当进入ECS实例的流量达到设置的阈值时，无论是否为正常业务流量，云盾都会启动流量清洗。

流量清洗的方法包括：过滤攻击报文、限制流量速度、限制数据包速度等。

所以，在使用DDoS基础防护时，您需要设置以下阈值：

-   BPS清洗阈值：当入方向流量超过BPS清洗阈值时，会触发流量清洗。
-   PPS清洗阈值：当入方向数据包数超过PPS清洗阈值时，会触发流量清洗。

## 云服务器ECS的清洗阈值 {#section_uxq_3rw_ydb .section}

云服务器ECS的清洗阈值由实例规格决定。下表列出了目前 在售 和 已停售 的部分实例规格的清洗阈值。

|实例规格|最大BPS清洗阈值（Mbit/s）|最大PPS清洗阈值（PPS）|
|:---|:----------------|:-------------|
|ecs.g5.16xlarge|20000|4000000|
|ecs.g5.22xlarge|30000|4500000|
|ecs.g5.2xlarge|2500|800000|
|ecs.g5.4xlarge|5000|1000000|
|ecs.g5.6xlarge|7500|1500000|
|ecs.g5.8xlarge|10000|2000000|
|ecs.g5.large|1000|300000|
|ecs.g5.xlarge|1500|500000|
|ecs.sn2ne.14xlarge|10000|4500000|
|ecs.sn2ne.2xlarge|2000|1000000|
|ecs.sn2ne.4xlarge|3000|1600000|
|ecs.sn2ne.8xlarge|6000|2500000|
|ecs.sn2ne.large|1000|300000|
|ecs.sn2ne.xlarge|1500|500000|
|ecs.c5.16xlarge|20000|4000000|
|ecs.c5.2xlarge|2500|800000|
|ecs.c5.4xlarge|5000|1000000|
|ecs.c5.6xlarge|7500|1500000|
|ecs.c5.8xlarge|10000|2000000|
|ecs.c5.large|1000|300000|
|ecs.c5.xlarge|1500|500000|
|ecs.sn1ne.2xlarge|2000|1000000|
|ecs.sn1ne.4xlarge|3000|1600000|
|ecs.sn1ne.8xlarge|6000|2500000|
|ecs.sn1ne.large|1000|300000|
|ecs.sn1ne.xlarge|1500|500000|
|ecs.r5.16xlarge|20000|4000000|
|ecs.r5.22xlarge|30000|4500000|
|ecs.r5.2xlarge|2500|800000|
|ecs.r5.4xlarge|5000|1000000|
|ecs.r5.6xlarge|7500|1500000|
|ecs.r5.8xlarge|10000|2000000|
|ecs.r5.large|1000|300000|
|ecs.r5.xlarge|1500|500000|
|ecs.re4.20xlarge|15000|2000000|
|ecs.re4.40xlarge|30000|4000000|
|ecs.se1ne.14xlarge|10000|4500000|
|ecs.se1ne.2xlarge|2000|1000000|
|ecs.se1ne.4xlarge|3000|1600000|
|ecs.se1ne.8xlarge|6000|2500000|
|ecs.se1ne.large|1000|300000|
|ecs.se1ne.xlarge|1500|500000|
|ecs.se1.14xlarge|10000|1200000|
|ecs.se1.2xlarge|1500|400000|
|ecs.se1.4xlarge|3000|500000|
|ecs.se1.8xlarge|6000|800000|
|ecs.se1.large|500|100000|
|ecs.d1ne.2xlarge|6000|1000000|
|ecs.d1ne.4xlarge|12000|1600000|
|ecs.d1ne.6xlarge|16000|2000000|
|ecs.d1ne.8xlarge|20000|2500000|
|ecs.d1ne.14xlarge|35000|4500000|
|ecs.d1.2xlarge|3000|300000|
|ecs.d1.4xlarge|6000|600000|
|ecs.d1.6xlarge|8000|800000|
|ecs.d1.8xlarge|10000|1000000|
|ecs.d1-c8d3.8xlarge|10000|1000000|
|ecs.d1.14xlarge|17000|1800000|
|ecs.d1-c14d3.14xlarge|17000|1400000|
|ecs.i2.xlarge|1000|500000|
|ecs.i2.2xlarge|2000|1000000|
|ecs.i2.4xlarge|3000|1500000|
|ecs.i2.8xlarge|6000|2000000|
|ecs.i2.16xlarge|10000|4000000|
|ecs.i1.xlarge|800|200000|
|ecs.i1.2xlarge|1500|400000|
|ecs.i1.4xlarge|3000|500000|
|ecs.i1-c10d1.8xlarge|6000|800000|
|ecs.i1-c5d1.4xlarge|3000|400000|
|ecs.i1.14xlarge|10000|1200000|
|ecs.hfc5.large|1000|300000|
|ecs.hfc5.xlarge|1500|500000|
|ecs.hfc5.2xlarge|2000|1000000|
|ecs.hfc5.4xlarge|3000|1600000|
|ecs.hfc5.6xlarge|4500|2000000|
|ecs.hfc5.8xlarge|6000|2500000|
|ecs.hfg5.large|1000|300000|
|ecs.hfg5.xlarge|1500|500000|
|ecs.hfg5.2xlarge|2000|1000000|
|ecs.hfg5.4xlarge|3000|1600000|
|ecs.hfg5.6xlarge|4500|2000000|
|ecs.hfg5.8xlarge|6000|2500000|
|ecs.hfg5.14xlarge|10000|4000000|
|ecs.c4.2xlarge|3000|400000|
|ecs.c4.4xlarge|6000|800000|
|ecs.c4.xlarge|1500|200000|
|ecs.ce4.xlarge|1500|200000|
|ecs.cm4.4xlarge|6000|800000|
|ecs.cm4.6xlarge|10000|1200000|
|ecs.cm4.xlarge|1500|200000|
|ecs.gn5-c28g1.14xlarge|10000|4500000|
|ecs.gn5-c4g1.xlarge|3000|300000|
|ecs.gn5-c4g1.2xlarge|5000|1000000|
|ecs.gn5-c8g1.2xlarge|3000|400000|
|ecs.gn5-c8g1.4xlarge|5000|1000000|
|ecs.gn5-c28g1.7xlarge|5000|2250000|
|ecs.gn5-c8g1.8xlarge|10000|2000000|
|ecs.gn5-c8g1.14xlarge|25000|4000000|
|ecs.gn5i-c2g1.large|1000|100000|
|ecs.gn5i-c4g1.xlarge|1500|200000|
|ecs.gn5i-c8g1.2xlarge|2000|400000|
|ecs.gn5i-c16g1.4xlarge|3000|800000|
|ecs.gn5i-c28g1.14xlarge|10000|2000000|
|ecs.gn4-c4g1.xlarge|3000|300000|
|ecs.gn4-c8g1.2xlarge|3000|400000|
|ecs.gn4-c4g1.2xlarge|5000|500000|
|ecs.gn4-c8g1.4xlarge|5000|500000|
|ecs.gn4.8xlarge|6000|800000|
|ecs.gn4.14xlarge|10000|1200000|
|ecs.ga1.xlarge|1000|200000|
|ecs.ga1.2xlarge|1500|300000|
|ecs.ga1.4xlarge|3000|500000|
|ecs.ga1.8xlarge|6000|800000|
|ecs.ga1.14xlarge|10000|1200000|
|ecs.f1-c28f1.7xlarge|5000|2000000|
|ecs.f1-c8f1.2xlarge|2000|800000|
|ecs.f2-c28f1.14xlarge|10000|2000000|
|ecs.f2-c28f1.7xlarge|5000|1000000|
|ecs.f2-c8f1.2xlarge|2000|400000|
|ecs.f2-c8f1.4xlarge|5000|1000000|
|ecs.t5-c1m1.2xlarge|1200|400000|
|ecs.t5-c1m1.large|500|100000|
|ecs.t5-c1m1.xlarge|800|200000|
|ecs.t5-c1m2.2xlarge|1200|400000|
|ecs.t5-c1m2.large|500|100000|
|ecs.t5-c1m2.xlarge|800|200000|
|ecs.t5-c1m4.2xlarge|1200|400000|
|ecs.t5-c1m4.large|500|100000|
|ecs.t5-c1m4.xlarge|800|200000|
|ecs.t5-lc1m1.small|200|60000|
|ecs.t5-lc1m2.large|400|100000|
|ecs.t5-lc1m2.small|200|60000|
|ecs.t5-lc1m4.large|400|100000|
|ecs.t5-lc2m1.nano|100|40000|
|ecs.ebmg4.8xlarge|10000|4500000|
|ecs.ebmg5.24xlarge|10000|4500000|
|ecs.sccg5.24xlarge|10000|4500000|
|ecs.xn4.small|500|50000|
|ecs.mn4.small|500|50000|
|ecs.mn4.large|500|100000|
|ecs.mn4.xlarge|800|150000|
|ecs.mn4.2xlarge|1200|300000|
|ecs.mn4.4xlarge|2500|400000|
|ecs.n4.small|500|50000|
|ecs.n4.large|500|100000|
|ecs.n4.xlarge|800|150000|
|ecs.n4.2xlarge|1200|300000|
|ecs.n4.4xlarge|2500|400000|
|ecs.n4.8xlarge|5000|500000|
|ecs.e4.small|500|50000|
|ecs.sn1.medium|500|100000|
|ecs.sn1.large|800|200000|
|ecs.sn1.xlarge|1500|400000|
|ecs.sn1.3xlarge|3000|500000|
|ecs.sn1.7xlarge|6000|800000|
|ecs.sn2.medium|500|100000|
|ecs.sn2.large|800|200000|
|ecs.sn2.xlarge|1500|400000|
|ecs.sn2.3xlarge|3000|500000|
|ecs.sn2.7xlarge|6000|800000|
|ecs.sn2.13xlarge|10000|120000|

## 相关操作 {#section_u1r_3rw_ydb .section}

云服务器ECS默认开启DDoS基础防护。ECS实例创建后，您可以执行以下操作：

-   设置清洗阈值：ECS实例创建后，默认按实例规格对应的最大阈值执行DDoS基础防护。但是，部分实例规格的最大清洗阈值（BPS）可能过大，无法起到应有的防护作用，所以，您需要根据实际情况调整清洗阈值，具体操作，请参见 DDoS基础防护用户指南-DDoS基础防护设置 。

-   （不推荐）取消流量清洗：当进入ECS实例的流量达到清洗阈值时，无论是否为正常业务流量，云盾都会启动流量清洗，此时，可能会导致正常业务不可用或受影响。为了保证正常业务，您可以手动取消流量清洗。具体操作，请参见 DDoS基础防护用户指南-如何取消流量清洗 。

    **警告：** 取消流量清洗后，当流入ECS实例的流量超过5 Gbit/s时，您的ECS实例会被打进黑洞。**请谨慎操作。**


