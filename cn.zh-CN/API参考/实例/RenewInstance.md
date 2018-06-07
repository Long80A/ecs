# RenewInstance {#RenewInstance .reference}

续费一台预付费实例。

## 描述 {#section_ut4_lk5_xdb .section}

调用该接口时，您需要注意：

-   该接口仅支持续费包年包月 ECS 实例。

-   除 0 折账号外，付款时，默认优先使用您的账号下可用的优惠券。

-   您的账号必须支持账号余额支付或信用支付。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数，取值：RenewInstance。|
|InstanceId|String|是|指定的需要实例规格的实例 ID。|
|Period|Integer|是|预付费续费时长。取值范围：-   \[1, 9\]
-   12
-   24
-   36
-   48
-   60

|
|PeriodUnit|String|否|预付费参数 `Period` 的单位。取值范围：-   Week
-   Month

默认值：Month-   取值为 `Week` 时，参数 `Period` 的取值范围为 \{1, 2, 3, 4\}。
-   取值为 `Month` 时，参数 `Period` 的取值范围为 \{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, 60\}。

|
|ClientToken|String|否|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一。只支持 ASCII 字符，且不能超过 64 个字符。更多详情，请参阅 [如何保证幂等性](cn.zh-CN/API参考/附录/如何保证幂等性.md#)。|

## 返回参数 {#section_f54_lk5_xdb .section}

全是公共返回参数。参阅 [公共参数](cn.zh-CN/API参考/调用方式/公共参数.md#commonResponseParameters)

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=RenewInstance
&InstanceId=i-instance1
&Period=1
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<ModifyInstanceSpecResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</ModifyInstanceSpecResponse>
```

 **JSON 格式** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|IdempotenceParamNotMatch|Request uses a client token in a previous request but is not identical to that request.|400|与相同 ClientToken 的请求参数不符合。|
|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|400|ClientToken 参数值不合法，不能包含 ASCII 以外的字符。|
|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records.|400|指定的 InstanceChargeType 不存在。|
|InvalidInstanceType.codeUnauthorized|The specified InstanceType is not authorized.|400|指定的 InstanceType 未授权使用。|
|InvalidInstanceType.NotSupported|The specified InstanceType is not Supported.|400|指定的 InstanceType 不支持。|
|InvalidInstanceType.ValueNotSupported|The specified InstanceType beyond the permitted range.|400|指定的 InstanceType 不合法（超出可选范围）。|
|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|400|指定的 InstanceType 未授权使用。|
|InvalidInternetChargeType.InstanceNotSupported|The specified instance which is in vpc is not support the parameter InternetChargeType.|400|VPC 实例不支持 InternetChargeType。|
|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid.|400|指定的 InternetChargeType 不存在。|
|InvalidParameter|The specified parameter “InternetMaxBandwidthOut” is not valid.|400|指定的 InternetMaxBandwidthOut 不合法（不是数字或超出范围）。|
|InvalidPeriod|The specified period is not valid.|400|指定的 period 参数格式不合法（不是数字或超出范围）。|
|InvalidRebootTime.Malformed|The specified RebootTime is not valid.|400|指定的 RebootTime 不合法。|
|InvalidRebootTime.ValueNotSupported|The specified RebootTime is out of the permitted range.|400|指定的 RebootTime 超出范围。|
|OperationDenied|Specified instance is in VPC.|400|指定实例在 VPC 中。|
|CategoryViolation|The specified instance does not support this operation because of its disk category.|403|磁盘类型不支持该操作。|
|ChargeTypeViolation|The operation is not permitted due to charge type of the instance.|403|付费方式不支持这个操作。|
|Diskcategory.Mismatch|The disk specified to convert to portable is not allowed due to the disk category does not support.|403|指定的磁盘类型不支持转换为可卸载磁盘。|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|该资源目前的状态不支持此操作。|
|Instance.UnPaidOrder|The specified instance has unpaid order.|403|该实例下还有未付费的订单。|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|该资源目前被安全锁定被拒绝操作。|
|InstanceTypeNotSupported|The specified zone does not offer the specified instancetype.|403|指定 zone 不支持指定的实例类型。|
|InvalidDisk.NotAllowed|The specified disk is not allowed to be converted to portable.|403|指定的磁盘不允许转换为可卸载磁盘。|
|LastTokenProcessing|The last token request is processing.|403|上一次请求还在处理中。|
|InvalidDiskId.NotFound|The specified disk does not exist.|404|指定的磁盘不存在。|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|指定的 InstanceId 不存在。|

