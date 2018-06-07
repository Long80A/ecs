# AttachNetworkInterface {#AttachNetworkInterface .reference}

附加弹性网卡（ENI）到专有网络（VPC）类型实例上。

## 描述 {#section_wwz_f34_ydb .section}

-   弹性网卡必须处于 **可用**（`Available`）状态。

-   实例必须处于 **运行中**（`Running`）或者 **已停止**（`Stopped`）状态。

-   弹性网卡只能附加到 VPC 类型实例，且必须与实例在同一 VPC 内。

-   一个弹性网卡只能同时附加到一台实例上。

-   一台实例可以同时附加多个弹性网卡，参阅 [弹性网卡](../cn.zh-CN/产品简介/网络和安全性/弹性网卡.md#) 查看每台实例规格能附加的弹性网卡数量。

-   由于 VPC 虚拟交换机不能跨可用区，弹性网卡附加的实例与弹性网卡所在的交换机必须属于同一可用区。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：AttachNetworkInterface|
|RegionId|String|是|实例所在地域的 ID。您可以调用 [DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|NetworkInterfaceId|String|是|弹性网卡 ID。|
|InstanceId|String|是|实例 ID。|

## 返回参数 {#section_f54_lk5_xdb .section}

全是公共返回参数。参阅 [公共参数](cn.zh-CN/API参考/调用方式/公共参数.md#)。

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=AttachNetworkInterface
&RegionId=cn-hangzhou
&NetworkInterfaceId=[networkInterfaceId]
&InstanceId=AY121018033933eae8xxxxx
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<AttachNetworkInterfaceResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</AttachNetworkInterfaceResponse>
```

 **JSON 格式** 

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|UnsupportedParameter|The parameters is unsupported.|400|该参数不存在，或者不支持该参数。|
|InvalidOperation.InvalidEcsState|The operation is not allowed in the current ECS state.|400|当前实例状态不支持该操作。|
|InvalidOperation.DetachPrimaryEniNotAllowed|Detaching primary ENI from ECS instance is not allowed.|400|不允许从实例上解绑主网卡。|
|MissingParameter|The input parameter that is mandatory for processing this request is not supplied.|400|缺少必需参数。|
|Abs.InvalidAccount.NotFound|The Account is not found or ak is expired.|403|您的阿里云账号不存在，或者您的 AccessKey 已经过期。|
|Forbidden.NotSupportRAM|This action does not support accessed by RAM mode.|403|不允许 RAM 用户执行该操作。|
|Forbidden.SubUser|The specified action is not available for you.|403|不允许 RAM 用户执行该操作。|
|EniPerInstanceLimitExceeded|The number of ENI exceeds the limit for the type of instance you are trying to launch.|403|弹性网卡的数量超过了指定实例类型允许的最大值。|
|InvalidOperation.VpcMismatch|The VPC of the specified ENI and security group are not in the same VPC.|403|指定的弹性网卡和安全组 ID 不在同一个 VPC。|
|SecurityGroupInstanceLimitExceed|The maximum number of instances in a security group is exceeded.|403|该安全组内已有的实例数量已超出最大限制。|
|InvalidOperation.InvalidEniType|The operation is not allowed in the current ENI type.|403|当前弹性网卡类型不支持该操作。|
|InvalidEcsId.NotFound|The specified EcsId is not found.|404|指定的实例 ID 不存在。|

