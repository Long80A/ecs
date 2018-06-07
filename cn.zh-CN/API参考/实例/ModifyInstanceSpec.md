# ModifyInstanceSpec {#ModifyInstanceSpec .reference}

调整一台实例的实例规格和公网带宽大小。

## 描述 {#section_bmh_rh5_xdb .section}

调用该接口时，您需要注意：

-   实例必须处于无欠费状态。

-   实例状态必须为 **运行中**（`Running`）或者 **已停止**（`Stopped`）时才能调节公网带宽大小。

-   升级或者降低实例规格前，您可以通过 [DescribeResourcesModification](cn.zh-CN/API参考/其他接口/DescribeResourcesModification.md#) 查询当前实例支持变配的实例规格。

    更多详情，请参阅 *云栖社区* [查询 ECS 变配的可用资源实践](https://yq.aliyun.com/articles/500164)。

-   实例状态必须为 **已停止**（`Stopped`）时才能变更实例规格。

-   单次只能升级单项配置，即单次只能修改实例规格，或者只能调整公网带宽大小。

-   单个实例每成功操作一次，5 分钟内不能继续操作。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：ModifyInstanceSpec|
|InstanceId|String|是|指定的实例 ID。|
|InstanceType|String|否|实例规格。更多详情，请参阅 [实例规格族](../cn.zh-CN/产品简介/实例规格族.md#)，也可以调用 [DescribeInstanceTypes](cn.zh-CN/API参考/实例/DescribeInstanceTypes.md#)接口获得最新的规格表。|
|InternetMaxBandwidthOut|Integer|否|公网出带宽最大值，单位为 Mbps \(Megabit per second\)。取值范围：-   按固定带宽计费：\[0, 100\]
-   按使用流量计费：\[0, 100\]

|
|InternetMaxBandwidthIn|Integer|否|公网入带宽最大值，单位为 Mbps \(Megabit per second\)。取值范围：-   按固定带宽计费：\[1, 200\]
-   按使用流量计费：\[1, 200\]

|
|ClientToken|String|否|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一。只支持 ASCII 字符，且不能超过 64 个字符。更多详情，请参阅 [如何保证幂等性](cn.zh-CN/API参考/附录/如何保证幂等性.md#)。|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求 ID|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceSpec
&InstanceId=i-xxxxx1
&InstanceType=ecs.s1.large
&InternetMaxBandwidthOut=10
&InternetMaxBandwidthIn=100
&ClientToken=xxxxxxxxx
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<ModifyInstanceSpecResponse>
   <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyInstanceSpecResponse>
```

 **JSON 格式** 

```
{
   "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|Account.Arrearage|Your account has an outstanding payment.|400|账号已经欠费。|
|DependencyViolation.InstanceType|The current InstanceType cannot be changed to the specified InstanceType.|400|当前实例规格不允许变更到指定的实例规格。|
|IdempotenceParamNotMatch|Request uses a client token in a previous request but is not identical to that request.|400|与相同 `ClientToken` 的请求参数不符合。|
|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|400|`ClientToken` 参数值不合法，不能包含 ASCII 以外的字符。|
|InvalidInstance.UnpaidOrder|The specified instance has unpaid order.|400|当前实例有未支付的订单。|
|InvalidInstanceType.ValueNotSupported|The specified InstanceType is not supported.|400|指定的 `InstanceType` 不合法（超出可选范围）。|
|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|400|指定的 `InstanceType` 未授权使用。|
|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid.|400|指定的 `InternetChargeType`不存在。|
|InvalidParameter|The specified parameter InternetMaxBandwidthOut is not valid.|400|指定的 `InternetMaxBandwidthOut`不合法（不是数字或超出取值范围）。|
|InvalidParameter.Bandwidth|The specified parameter Bandwidth is not valid.|400|指定的公网带宽值不合法。|
|InvalidParameter.Conflict|The specified image does not support the specified instance type.|400|指定实例的 `InstanceType` 不允许使用该镜像。|
|InvalidParameter.Mismatch|Too many parameters in one request.|400|请求参数过多。|
|InvalidStatus.ValueNotSupported|The current status of the resource does not support this operation.|400|当前的实例状态不支持此操作。|
|InvalidStatus.ValueNotSupported|The instance cannot be modified in the specified status.|400|当前的实例状态不支持此操作。|
|OperationDenied|The specified instance is in VPC.|400|该实例的网络类型为专有网络。|
|Price.PricePlanResultNotFound|The internetMaxBandwidthIn or internetMaxBandwidthOut provided is invalid.|400|请求参数 `InternetMaxBandwidthIn` 或 `InternetMaxBandwidthOut` 不合法。|
|Throttling|You have made too many requests within a short time; your request is denied due to request throttling.|400|操作过于频繁。|
|InvalidInstanceStatus.NotStopped|The specified Instance status is not stopped.|400|实例未处于停止状态。|
|CategoryViolation|The specified instance does not support this operation because of its disk category.|403|当前实例的磁盘类型不支持此操作。|
|ChargeTypeViolation|The operation is not permitted due to charge type of the instance.|403|当前实例的付费类型不支持此操作。|
|ImageNotSupportInstanceType|The specified image does not support the specified InstanceType.|403|指定镜像不支持该实例类型。|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|该实例目前被安全锁定，拒绝操作。|
|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|403|账户余额不足。|
|LastTokenProcessing|The last token request is processing.|403|上一次请求还在处理中。|
|OperationDenied|The instance is out of usage.|403|该实例库存不足，请选择其他实例。|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|指定的 `InstanceId` 不存在。|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|
|InvalidAction|The specified action is not valid.|500|当前操作无效。|

