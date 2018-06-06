# Benefits of ECS {#concept_c1y_bp2_vdb .concept}

Compared with Internet Data Centers \(IDCs\) and server vendors, the ECS has the benefits in the following aspects:Availability , Security, Elasticity

## Availability {#section_jrm_cv4_ydb .section}

Alibaba Cloud adopts more stringent IDC standards, server access standards, and O&M standards to guarantee data reliability and high availability of cloud computing infrastructure and cloud servers.

In addition, each region of Alibaba Cloud consists of multiple zones. For greater fault tolerance, you can build active/standby or active/active services in multiple zones.  For a finance-oriented solution with three IDCs in two regions, you can build fault tolerant systems in multiple regions and zones.  Those services include disaster tolerance and backup, which are supported by the mature solutions built by Alibaba Cloud.

Switching between services is smooth within the Alibaba Cloud framework. For more information, see [E-Commerce Solutions](https://www.alibabacloud.com/zh/solutions/gaming).  Both three centres, e-commerce and video services, etc, you can find the corresponding industry solutions in ALI cloud.

Alibaba Cloud provides you with the following support services:

-   Products and services for availability improvement, including cloud servers, Server Load Balancer, multi-backup databases, and Data Transmission Services \(DTS\).
-   Industry partners and ecosystem partners that help you build a more advanced and stable architecture and guarantee service continuity.
-   Diverse training services that enable you to connect with high availability from the business end to the underlying basic service end.

## Security {#section_lrm_cv4_ydb .section}

Users of cloud computing are most concerned about security and stability.  Alibaba Cloud has recently passed a host of international information security certifications, including ISO 27001 and MTCS, which demand strict confidentiality of user data and user information and user privacy protection.  [Alibaba Cloud VPC](https://www.alibabacloud.com/help/zh/product/27706.htm) is the prime choice for providing your cloud computing services.

-   **Alibaba Cloud VPC offers more business possibilities.** You only need to perform simple configuration to connect your business environment to global IDCs, making your business more flexible, stable, and extensible.

-   **For the original self-built IDC computer room, there will be no problems.** Alibaba Cloud VPC can connect to your IDC through a leased line to build a hybrid cloud architecture. You can build a more flexible business with the robust networking derived from Alibaba Cloud’s various hybrid cloud solutions and network products.  A superior business ecosystem is possible with Alibaba Cloud’s ecosystem.

-   **Alibaba Cloud VPC is more stable and secure.**

    **Stable:** After you build your business on VPC, you can update your network architecture and obtain new network functions on a daily basis as the network infrastructure evolves constantly, allowing your business to run steadily. You can divide, configure, and manage your network on VPC according to your needs.

    **Secure:** VPC features traffic isolation and attack isolation to protect your services from endless attack traffic on the Internet. After you build your business on VPC, the first line of defense is established.


VPC provides a stable, secure, fast-deliverable, self-managed, and controllable network environment.  The capability and architecture of VPC hybrid cloud bring the technical advantages of cloud computing to traditional industries and industries and enterprises that are not engaged in cloud computing.

## Elasticity {#section_nrm_cv4_ydb .section}

Elasticity is a key benefit of cloud computing. By using Alibaba Cloud, you can have all the necessary IT resources provisioned within minutes to build an IT company of medium size. The resources and capacity of this size can meet the requirements of most companies for their applications built on the cloud to handle huge volume of transactions without problems.

## Elastic computing {#section_orm_cv4_ydb .section}

**Vertical scaling involves modifying the configurations of a server. ** It is difficult to make configurations in the traditional IDC model. After you purchase ECS or storage capacity of Alibaba Cloud, you can configure your server with great flexibility based on your actual transaction volume. For more information about vertical scaling, see [Change configurations](../intl.en-US/User Guide/Instances/Change configurations.md#).

**Horizontal scaling** For example, at peak hours for game or live video streaming apps, in the traditional IDC model, your hands may be tied when the request for additional resources arises. Cloud computing now leverages elasticity to tide you over that period.  When the period ends, you release unnecessary resources to reduce your business cost. By using both horizontal scaling and auto-scaling that Alibaba Cloud provides, you can determine how and when you scale your resources or apply your scaling based on business loads. For more information about horizontal scaling, see [Auto Scaling](https://www.alibabacloud.com/help/zh/doc-detail/25857.htm?spm=a2c63.p38356.a3.4.290d241cM77MOY).

**Horizontal scaling** For example, at peak hours for game or live video streaming apps, in the traditional IDC model, your hands may be tied when the request for additional resources arises. Cloud computing now leverages elasticity to tide you over that period.  When the period ends, you release unnecessary resources to reduce your business cost. By using both horizontal scaling and auto-scaling that Alibaba Cloud provides, you can determine how and when you scale your resources or apply your scaling based on business loads. For more information about horizontal scaling, see Auto Scaling.

## Elastic storage {#section_prm_cv4_ydb .section}

Alibaba Cloud has elastic storage.  When more storage space is required, in the traditional IDC model, you can only add servers, but the number of servers that you can add is limited. However, in the cloud computing model, the sky is the limit. Order as you want to guarantee the sufficient storage space.  For more information about elastic storage, see  [Resize a disk](../intl.en-US/User Guide/Cloud disks/Resize cloud disks.md#) .

## Elastic network {#section_qrm_cv4_ydb .section}

Alibaba Cloud features elastic network as well.  When you purchase the Alibaba Virtual Private Cloud \(VPC\), you can have the network configurations the same as those of data centers. In addition, you can have the following benefits: Interconnection between data centers , Separate secure domains in data centers , Flexible network configurations and planning within the VPC. For more information about elastic network, see [Virtual Private Cloud](https://www.alibabacloud.com/help/zh/product/27706.htm).

Elasticity of Alibaba Cloud is a combination of elastic computing, storage, network, and the elasticity to redesign business architecture.  By using Alibaba Cloud, you can work out your business portfolio in whatever way you want.

## Comparison between ECS and traditional IDCs {#section_rrm_cv4_ydb .section}

The table lists the benefits of ECS compared with the traditional IDCs.

| |ECS|Traditional IDCs|
|:-|:--|:---------------|
|Equipment rooms|Provides independently developed DC powered servers with low PUE.|Provides traditional AC powered servers with high PUE.|
|Provides backbone equipment rooms with high outbound bandwidth and dedicated bandwidth.|Provides equipment rooms with various quality levels and shared bandwidth primarily, difficult for users to choose.|
|Provides multiline BGP equipment rooms, enabling smooth and balanced access throughout the country.|Provides equipment rooms with single or dual line primarily.|
|Ease of operation|Provides built-in mainstream operating systems, including activated Windows OS.|Purchases and installs operating system manually.|
|Switches operating systems online.|Reinstalls operating systems manually.|
|Provides a Web-based console for online management.|Manages and maintains manually.|
|Provides mobile phone verification for password setting, increasing data security.|Has difficulty in resetting passwords, and exposes high risk of password cracking.|
|Disaster recovery and backup|Users can customize automatic snapshot policies to create automatic snapshots for data recovery.|Users must restore all corrupted data manually.|
|User-Defined snapshots|Faults cannot be recovered automatically.|
|Faults can be recovered fast and automatically.|Failed to prevent MAC spoofing and ARP attacks.|
|Security and reliability|Effectively prevents MAC spoofing and ARP attacks.|Failed to prevent MAC spoofing and ARP attacks.|
|Effectively defend against DDoS attacks by using black holes and cleaning traffic.|Needs additional costs for devices for traffic cleaning and black hole shielding systems|
|Provides additional services, such as port scanning, Trojan scanning, and vulnerability scanning.|Typically encountered problems such as vulnerability, Trojan, and port scanning.|
|Flexible scalability|Activates cloud servers on demand and upgrades configurations online.|Needs long time for server delivery.|
|Adjusts outbound bandwidth whenever required.|One-off purchase of outbound bandwidth, unable to adjust.|
|Combines with Server Load Balancer online, enabling scaling up applications quickly and easily.|Uses hardware-based server load balancing, which is expensive and extremely difficult to set up.|
|Cost effectiveness|Costs low.| Costs high.|
|Invests a little up front.|Invests a lot up front, causing serious waste of resources.|
|Purchases on demand and pay as you go, meeting requirements for constant business changes.|Purchases up front to meet configuration requirements for peak hours.|

