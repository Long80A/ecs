# Scenarios {#concept_j5s_nwq_ydb .concept}

ECS is a highly flexible solution.  It can be used independently as a simple web server, or used with other Alibaba Cloud products, such as OSS and CDN, to provide advanced solutions.

ECS can be used in applications such as:

## Official corporate websites and simple web applications {#section_ur2_4wq_ydb .section}

In the initial stage, corporate websites have low traffic volumes and require only low-configuration ECS instances to run applications, databases, storage files, and other resources.  As your business expands,  you can upgrade the ECS configuration and increase the number of ECS instances at any time.  You no longer need to worry about insufficient resources during peak traffic.

## Multimedia and large-traffic apps or websites {#section_vr2_4wq_ydb .section}

ECS can be used with OSS to store static images, videos, and downloaded packages, reducing storage fees. In addition, ECS can be used with CDN or Server Load Balancer to greatly reduce user access waiting time, reduce bandwidth fees, and improve availability.

## Databases {#section_wr2_4wq_ydb .section}

Supports databases with high requirements for I/O. A high-configuration I/O-optimized ECS instance can be used with an SSD cloud disk  to support high I/O concurrency with higher data reliability.  Alternatively, multiple lower-configuration I/O-optimized ECS instances can be used with Server Load Balancer to deliver a highly available architecture.

## Apps or websites with large traffic fluctuations {#section_xr2_4wq_ydb .section}

Some applications may encounter large traffic fluctuations within a short period. When ECS is used with Auto Scaling, the number of ECS instances is automatically adjusted based on traffic. This feature allows you to meet resource requirements while maintaining a low cost.  ECS can be used with Server Load Balancer to deliver a high availability architecture.

