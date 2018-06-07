# API 概览 {#AvailableActions .reference}

我们为您汇总了云服务器 ECS 所有可调用 API，具体接口信息请参阅相关文档。

更多 API 资源，请访问 [API Explorer](https://api.aliyun.com/)。

## 实例相关接口 {#section_vvj_q2h_vdb .section}

|接口|描述|
|:-|:-|
|[RunInstances](cn.zh-CN/API参考/实例/RunInstances.md#)|创建一台或者多台按量付费（Pay-As-You-Go）实例。|
|[CreateInstance](cn.zh-CN/API参考/实例/CreateInstance.md#)|创建一台实例。|
|[StartInstance](cn.zh-CN/API参考/实例/StartInstance.md#)|启动一台指定的实例。|
|[StopInstance](cn.zh-CN/API参考/实例/StopInstance.md#)|停止运行一台指定的实例。|
|[RebootInstance](cn.zh-CN/API参考/实例/RebootInstance.md#)|重启指定的实例。|
|[DeleteInstance](cn.zh-CN/API参考/实例/DeleteInstance.md#)|根据传入的实例名称释放您的实例资源。|
|[AttachInstanceRamRole](cn.zh-CN/API参考/实例/AttachInstanceRamRole.md#)|为您的实例授予实例 RAM 角色。|
|[DetachInstanceRamRole](cn.zh-CN/API参考/实例/DetachInstanceRamRole.md#)|收回实例的实例 RAM 角色。|
|[DescribeInstanceStatus](cn.zh-CN/API参考/实例/DescribeInstanceStatus.md#)|批量获取当前用户所有实例的状态信息。|
|[DescribeInstances](cn.zh-CN/API参考/实例/DescribeInstances.md#)|查询所有实例的详细信息。|
|[DescribeInstanceVncUrl](cn.zh-CN/API参考/实例/DescribeInstanceVncUrl.md#)|查询实例的 Web 管理终端地址。|
|[DescribeUserdata](cn.zh-CN/API参考/实例/DescribeUserdata.md#)|查询您的实例的自定义数据。|
|[DescribeInstanceAutoRenewAttribute](cn.zh-CN/API参考/实例/DescribeInstanceAutoRenewAttribute.md#)|查询实例自动续费状态。|
|[DescribeInstanceRamRole](cn.zh-CN/API参考/实例/DescribeInstanceRamRole.md#)|查询一台或者多台实例上的已赋予的实例 RAM 角色的信息。|
|[DescribeSpotPriceHistory](cn.zh-CN/API参考/实例/DescribeSpotPriceHistory.md#)|查询竞价实例历史价格。最多能查询 30 天内的历史价格记录。|
|[DescribeInstanceTypeFamilies](cn.zh-CN/API参考/实例/DescribeInstanceTypeFamilies.md#)|查询云服务器 ECS 提供的实例规格族资源。|
|[DescribeInstanceTypes](cn.zh-CN/API参考/实例/DescribeInstanceTypes.md#)|查询云服务器 ECS 提供的实例规格资源。|
|[ModifyInstanceVpcAttribute](cn.zh-CN/API参考/实例/ModifyInstanceVpcAttribute.md#)|修改实例的 VPC 属性。|
|[ModifyInstanceAttribute](cn.zh-CN/API参考/实例/ModifyInstanceAttribute.md#)|修改实例密码、实例名称和安全组等属性信息。|
|[ModifyInstanceVncPasswd](cn.zh-CN/API参考/实例/ModifyInstanceVncPasswd.md#)|修改实例的 Web 管理终端密码。|
|[ModifyInstanceAutoReleaseTime](cn.zh-CN/API参考/实例/ModifyInstanceAutoReleaseTime.md#)|为实例设定自动释放时间。|
|[ModifyInstanceAutoRenewAttribute](cn.zh-CN/API参考/实例/ModifyInstanceAutoRenewAttribute.md#)|设置实例的自动续费状态。|
|[ModifyInstanceChargeType](cn.zh-CN/API参考/实例/ModifyInstanceChargeType.md#)|修改实例付费类型，支持按量付费实例换成预付费实例。|
|[ModifyInstanceSpec](cn.zh-CN/API参考/实例/ModifyInstanceSpec.md#)|调整按量付费实例的实例规格和公网带宽大小。|
|[ModifyPrepayInstanceSpec](cn.zh-CN/API参考/实例/ModifyPrepayInstanceSpec.md#)|升级或者降低预付费实例规格。|
|[RenewInstance](cn.zh-CN/API参考/实例/RenewInstance.md#)|为预付费（包年包月）实例续费。|

## 磁盘相关接口 {#section_t3s_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[CreateDisk](cn.zh-CN/API参考/磁盘/CreateDisk.md#)|创建可卸载云盘的数据盘。|
|[DeleteDisk](cn.zh-CN/API参考/磁盘/DeleteDisk.md#)|释放一块云盘。|
|[DescribeDisks](cn.zh-CN/API参考/磁盘/DescribeDisks.md#)|查询您已经创建的磁盘。|
|[AttachDisk](cn.zh-CN/API参考/磁盘/AttachDisk.md#)|为实例挂载数据盘。|
|[DetachDisk](cn.zh-CN/API参考/磁盘/DetachDisk.md#)|将一块云盘从一台实例上卸载。|
|[ModifyDiskAttribute](cn.zh-CN/API参考/磁盘/ModifyDiskAttribute.md#)|修改您的磁盘的属性或者明细。|
|[ReplaceSystemDisk](cn.zh-CN/API参考/磁盘/ReplaceSystemDisk.md#)|更换实例的系统盘或者操作系统。|
|[ReInitDisk](cn.zh-CN/API参考/磁盘/ReInitDisk.md#)|初始化云盘到创建时的初始状态。|
|[ResetDisk](cn.zh-CN/API参考/磁盘/ResetDisk.md#)|使用磁盘的历史快照回滚至某一阶段的磁盘状态。|
|[ResizeDisk](cn.zh-CN/API参考/磁盘/ResizeDisk.md#)|扩容一块磁盘。|

## 镜像相关接口 {#section_image_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[CreateImage](cn.zh-CN/API参考/镜像/CreateImage.md#)|创建一份自定义镜像。|
|[ImportImage](cn.zh-CN/API参考/镜像/ImportImage.md#)|导入您已有的镜像文件到云服务器 ECS 环境中，并作为自定义镜像出现在相应地域中。|
|[ExportImage](cn.zh-CN/API参考/镜像/ExportImage.md#)|导出自定义镜像到与该自定义镜像同一地域的对象存储 OSS bucket 里。|
|[CopyImage](cn.zh-CN/API参考/镜像/CopyImage.md#)|将一个地域下的自定义镜像复制到其他地域。|
|[CancelCopyImage](cn.zh-CN/API参考/镜像/CancelCopyImage.md#)|取消正在进行中的复制镜像（`CopyImage`）任务。|
|[DescribeImages](cn.zh-CN/API参考/镜像/DescribeImages.md#)|查询您可以使用的镜像资源。|
|[DeleteImage](cn.zh-CN/API参考/镜像/DeleteImage.md#)|删除一份自定义镜像。|
|[DescribeImageSharePermission](cn.zh-CN/API参考/镜像/DescribeImageSharePermission.md#)|查询一份自定义镜像已经共享的所有用户。|
|[ModifyImageAttribute](cn.zh-CN/API参考/镜像/ModifyImageAttribute.md#)|修改自定义镜像的名称和描述。|
|[ModifyImageSharePermission](cn.zh-CN/API参考/镜像/ModifyImageSharePermission.md#)|管理镜像共享权限。|

## 快照相关接口 {#section_snapshot_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[CreateSnapshot](cn.zh-CN/API参考/快照/CreateSnapshot.md#)|为指定的磁盘创建快照。|
|[CreateAutoSnapshotPolicy](cn.zh-CN/API参考/快照/CreateAutoSnapshotPolicy.md#)|创建一条自动快照策略。|
|[ApplyAutoSnapshotPolicy](cn.zh-CN/API参考/快照/ApplyAutoSnapshotPolicy.md#)|为一块或者多块磁盘应用自动快照策略。|
|[DeleteSnapshot](cn.zh-CN/API参考/快照/DeleteSnapshot.md#)|删除指定的快照。|
|[CancelAutoSnapshotPolicy](cn.zh-CN/API参考/快照/CancelAutoSnapshotPolicy.md#)|取消一块或者多块磁盘的自动快照策略。|
|[DeleteAutoSnapshotPolicy](cn.zh-CN/API参考/快照/DeleteAutoSnapshotPolicy.md#)|删除一条自动快照策略。|
|[DescribeAutoSnapshotPolicyEx](cn.zh-CN/API参考/快照/DescribeAutoSnapshotPolicyEx.md#)|查询您已创建的自动快照策略。|
|[DescribeSnapshots](cn.zh-CN/API参考/快照/DescribeSnapshots.md#)|查询某台实例磁盘设备所有的快照列表。|
|[DescribeSnapshotLinks](cn.zh-CN/API参考/快照/DescribeSnapshotLinks.md#)|查询磁盘快照链。|
|[ModifyAutoSnapshotPolicyEx](cn.zh-CN/API参考/快照/ModifyAutoSnapshotPolicyEx.md#)|修改一条自动快照策略。|

## 网络相关接口 {#section_network_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[AllocatePublicIpAddress](cn.zh-CN/API参考/网络/AllocatePublicIpAddress.md#)|为一台实例分配一个公网 IP 地址。|
|[ConvertNatPublicIpToEip](cn.zh-CN/API参考/网络/ConvertNatPublicIpToEip.md#)|将一台网络类型为 VPC 类型的实例的公网 IP（NatPublicIp）转化为 弹性公网 IP（EIP）。|
|[AttachClassicLinkVpc](cn.zh-CN/API参考/网络/AttachClassicLinkVpc.md#)|将一台经典网络类型实例连接到 VPC 中，使经典网络类型实例可以和 VPC 中的云资源私网互通。|
|[DetachClassicLinkVpc](cn.zh-CN/API参考/网络/DetachClassicLinkVpc.md#)|取消经典网络类型实例与 VPC 的连接（ClassicLink）。|
|[DescribeBandwidthLimitation](cn.zh-CN/API参考/网络/DescribeBandwidthLimitation.md#)|查询带宽资源列表。|
|[DescribeClassicLinkInstances](cn.zh-CN/API参考/网络/DescribeClassicLinkInstances.md#)|查询一台或者多台与 VPC 建立了连接的经典网络类型实例。|
|[ModifyInstanceNetworkSpec](cn.zh-CN/API参考/网络/ModifyInstanceNetworkSpec.md#)|修改实例的带宽配置。|

专有网络 VPC 相关的接口，请参阅 [专有网络 VPC API 参考](../../cn.zh-CN/API 参考/API概览.md#)。

## 安全组相关接口 {#section_securitygroup_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[CreateSecurityGroup](cn.zh-CN/API参考/安全组/CreateSecurityGroup.md#)|新建一个安全组。|
|[AuthorizeSecurityGroup](cn.zh-CN/API参考/安全组/AuthorizeSecurityGroup.md#)|增加一条安全组入方向规则。|
|[AuthorizeSecurityGroupEgress](cn.zh-CN/API参考/安全组/AuthorizeSecurityGroupEgress.md#)|增加一条安全组出方向规则。|
|[RevokeSecurityGroup](cn.zh-CN/API参考/安全组/RevokeSecurityGroup.md#)|删除一条安全组入方向规则。|
|[RevokeSecurityGroupEgress](cn.zh-CN/API参考/安全组/RevokeSecurityGroupEgress.md#)|删除一条安全组出方向规则。|
|[JoinSecurityGroup](cn.zh-CN/API参考/安全组/JoinSecurityGroup.md#)|将一台实例加入到指定的安全组。|
|[LeaveSecurityGroup](cn.zh-CN/API参考/安全组/LeaveSecurityGroup.md#)|将一台实例移出指定的安全组。|
|[DeleteSecurityGroup](cn.zh-CN/API参考/安全组/DeleteSecurityGroup.md#)|删除一个安全组。|
|[DescribeSecurityGroupAttribute](cn.zh-CN/API参考/安全组/DescribeSecurityGroupAttribute.md#)|查询安全组详情。|
|[DescribeSecurityGroups](cn.zh-CN/API参考/安全组/DescribeSecurityGroups.md#)|查询您创建的安全组的基本信息，例如安全组 ID 和安全组描述等。|
|[DescribeSecurityGroupReferences](cn.zh-CN/API参考/安全组/DescribeSecurityGroupReferences.md#)|查询一个安全组和其他哪些安全组有安全组级别的授权行为。|
|[ModifySecurityGroupAttribute](cn.zh-CN/API参考/安全组/ModifySecurityGroupAttribute.md#)|修改指定安全组的属性，包括修改安全组名称和描述。|
|[ModifySecurityGroupPolicy](cn.zh-CN/API参考/安全组/ModifySecurityGroupPolicy.md#)|修改安全组内网连通策略。|
|[ModifySecurityGroupRule](cn.zh-CN/API参考/安全组/ModifySecurityGroupRule.md#)|修改一条安全组入方向规则的描述信息。|

## SSH 密钥对相关接口 {#section_keypair_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[CreateKeyPair](cn.zh-CN/API参考/SSH 密钥对/CreateKeyPair.md#)|创建一对 SSH 密钥对。|
|[ImportKeyPair](cn.zh-CN/API参考/SSH 密钥对/ImportKeyPair.md#)|导入由其他工具产生的 SSH 密钥对的公钥部分。|
|[AttachKeyPair](cn.zh-CN/API参考/SSH 密钥对/AttachKeyPair.md#)|绑定 SSH 密钥对到一台或者多台 Linux 实例。|
|[DetachKeyPair](cn.zh-CN/API参考/SSH 密钥对/DetachKeyPair.md#)|为一台或者多台 Linux 实例解绑 SSH 密钥对。|
|[DeleteKeyPairs](cn.zh-CN/API参考/SSH 密钥对/DeleteKeyPairs.md#)|删除一对或多对 SSH 密钥对。|
|[DescribeKeyPairs](cn.zh-CN/API参考/SSH 密钥对/DescribeKeyPairs.md#)|查询一对或者多对 SSH 密钥对。|

## 弹性网卡相关接口 {#section_networkinterface_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[CreateNetworkInterface](cn.zh-CN/API参考/弹性网卡/CreateNetworkInterface.md#)|创建一张弹性网卡（ENI）。|
|[AttachNetworkInterface](cn.zh-CN/API参考/弹性网卡/AttachNetworkInterface.md#)|附加弹性网卡（ENI）到 VPC 类型实例上。|
|[DetachNetworkInterface](cn.zh-CN/API参考/弹性网卡/DetachNetworkInterface.md#)|从实例上分离弹性网卡（ENI）。|
|[DeleteNetworkInterface](cn.zh-CN/API参考/弹性网卡/DeleteNetworkInterface.md#)|删除一张弹性网卡（ENI）。|
|[DescribeNetworkInterfaces](cn.zh-CN/API参考/弹性网卡/DescribeNetworkInterfaces.md#)|查看弹性网卡（ENI）列表。|
|[ModifyNetworkInterfaceAttribute](cn.zh-CN/API参考/弹性网卡/ModifyNetworkInterfaceAttribute.md#)|修改一张弹性网卡（ENI）的属性。|

## 地域相关接口 {#section_region_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md#)|查询您可以使用的阿里云地域。|
|[DescribeZones](cn.zh-CN/API参考/地域/DescribeZones.md#)|查询某一阿里云地域下的可用区。|

## 运维与监控相关接口 {#section_monitor_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[DescribeDisksFullStatus](cn.zh-CN/API参考/运维与监控/DescribeDisksFullStatus.md#)|查询磁盘的全部状态信息。|
|[DescribeDiskMonitorData](cn.zh-CN/API参考/运维与监控/DescribeDiskMonitorData.md#)|查询一块磁盘指定时间内的使用信息。|
|[DescribeInstancesFullStatus](cn.zh-CN/API参考/运维与监控/DescribeInstancesFullStatus.md#)|查询实例的全状态信息。|
|[DescribeInstanceHistoryEvents](cn.zh-CN/API参考/SSH 密钥对/CreateKeyPair.md#)|查询指定实例的已经处于非活跃状态的历史事件，指定查询事件的最大时长必须小于等于 2 个月。|
|[DescribeInstanceMonitorData](cn.zh-CN/API参考/运维与监控/DescribeInstanceMonitorData.md#)|查询您某一台实例所有相关的监控信息，查询结果可以分页显示。|

## 标签相关接口 {#section_tag_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[AddTags](cn.zh-CN/API参考/标签/AddTags.md#)|添加或者覆盖一个或者多个标签到云服务器 ECS 的各项资源上。|
|[RemoveTags](cn.zh-CN/API参考/标签/RemoveTags.md#)|从云服务器 ECS 资源上解绑一个或多个标签，例如，实例、磁盘、快照、镜像和安全组等。|
|[DescribeTags](cn.zh-CN/API参考/标签/DescribeTags.md#)|查询可以供您使用的标签。|

## 云助手相关接口 {#section_cloudassistant_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[CreateCommand](cn.zh-CN/API参考/云助手/CreateCommand.md#)|新建 [云助手](https://help.aliyun.com/document_detail/64601.html) 命令。|
|[InvokeCommand](cn.zh-CN/API参考/云助手/InvokeCommand.md#)|为目标实例触发指定的命令。|
|[StopInvocation](cn.zh-CN/API参考/云助手/StopInvocation.md#)|停止实例中正在进行中（`Running`）的云助手命令进程。|
|[DeleteCommand](cn.zh-CN/API参考/云助手/DeleteCommand.md#)|删除已创建的云助手命令。|
|[DescribeCommands](cn.zh-CN/API参考/云助手/DescribeCommands.md#)|查询您已经创建的云助手命令。|
|[DescribeInvocations](cn.zh-CN/API参考/云助手/DescribeInvocations.md#)|查询您的实例中的云助手命令执行列表及状态。|
|[DescribeInvocationResults](cn.zh-CN/API参考/云助手/DescribeInvocationResults.md#)|查看云助手命令的执行结果，即在指定实例中的实际输出信息（Output）。|
|[ModifyCommand](cn.zh-CN/API参考/云助手/ModifyCommand.md#)|修改已创建的云助手命令相关参数以及命令内容。|

## 其它接口 {#section_other_t2h_vdb .section}

|接口|描述|
|:-|:-|
|[CancelTask](cn.zh-CN/API参考/其他接口/CancelTask.md#)|取消一件正在运行的任务。|
|[DescribeAvailableResource](cn.zh-CN/API参考/其他接口/DescribeAvailableResource.md#)|查询某一可用区的资源列表。|
|[DescribeResourcesModification](cn.zh-CN/API参考/其他接口/DescribeResourcesModification.md#)|查询升级和降配实例规格或者系统盘时，某一可用区的可用资源信息。|
|[DescribeTasks](cn.zh-CN/API参考/其他接口/DescribeTasks.md#)|查询指定的异步请求的进度。|
|[DescribeTaskAttribute](cn.zh-CN/API参考/其他接口/DescribeTaskAttribute.md#)|查询异步任务的详细信息。目前，可以查询的异步任务有导入镜像（[ImportImage](cn.zh-CN/API参考/镜像/ImportImage.md#)）和导出镜像（[ExportImage](cn.zh-CN/API参考/镜像/ExportImage.md#)）两种。|

