# 专有网络的IP {#concept_olx_cjw_ydb .concept}

VPC类型ECS实例有2种IP地址：私有IP地址和公网IP地址。

## 私有IP地址 {#section_zkh_djw_ydb .section}

根据实例所属的VPC和交换机网段，VPC类型ECS实例一经创建即被分配一个私有IP地址。

## 应用场景 {#section_alh_djw_ydb .section}

私有IP地址可以用于以下情况：

-   负载均衡
-   同一局域网内ECS实例之间内网互访
-   同一局域网内ECS实例与其他云服务（如OSS、RDS）之间内网互访

关于更多内网通讯的信息，参见 [内网](cn.zh-CN/产品简介/网络和安全性/内网.md#)。

## 修改私有IP地址 {#section_clh_djw_ydb .section}

您可以根据业务需要，在ECS管理控制台上修改私有IP地址。详细信息，请参见 [修改VPC类型ECS实例的私有IP地址](../cn.zh-CN/用户指南/实例/修改IP地址/修改私有IP地址.md#)。

## 公网IP地址 {#section_dlh_djw_ydb .section}

VPC类型的ECS实例支持以下2种公网IP地址：

-   ECS系统分配的公网IP地址（NatPublicIp）。
-   弹性公网IP（EIP）地址。详细信息，请参见 弹性公网IP文档。

一台VPC类型的ECS实例最多只能关联一个公网IP地址，可以是NatPublicIp或者EIP。

VPC类型的ECS实例的公网访问通过私有网卡映射完成，所以，无论您的实例是否分配或者绑定了公网IP地址，在实例内部您都无法查询公网网卡。

## 使用场景 {#section_flh_djw_ydb .section}

NatPublicIp与EIP的使用场景不同：

-   NatPublicIp：如果希望在创建VPC类型的ECS实例时由ECS系统自动分配一个公网IP地址，释放实例时这个公网IP地址随实例一起释放，不保留该公网IP地址，您可以选择NatPublicIp。

-   EIP：如果希望长期保留某个公网IP地址，根据业务需要将它绑定或解绑指定的VPC类型ECS实例上，您可以选择弹性公网IP（EIP）。


## 获取方式 {#section_qnq_hsr_zdb .section}

-   NatPublicIp：在创建VPC类型的ECS实例时，如果您选择 **分配公网IP地址**，实例即被分配一个NatPublicIp。

-   EIP：您可以单独申请EIP地址，并绑定到未分配NatPublicIp的VPC类型ECS实例上。更多信息，请参见 弹性公网IP文档。


## 释放公网IP地址 {#section_hbl_4sr_zdb .section}

-   NatPublicIp一经分配，只能释放，不能解绑。根据ECS实例计费方式不同，您可以选择不同的方式释放NatPublicIp：
    -   预付费实例：您可以通过 续费降配 将带宽值设置为0 Mbit/s，进入新的计费周期后，NatPublicIp即释放。
    -   按量付费实例：您可以通过 按量实例更改带宽 将带宽值设置为0 Mbit/s，使NatPublicIp立即释放。
-   EIP：如果您不再需要一个EIP地址，先将其与ECS实例解绑，再登录EIP管理控制台释放EIP。详细信息，请参见 弹性网卡IP文档 。

## 计费 {#section_llh_djw_ydb .section}

阿里云只对公网出网带宽收取费用，入网带宽免费。更多公网带宽的计费信息，请参考 产品定价-公网带宽计费。

