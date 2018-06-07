# ModifyInstanceChargeType {#ModifyInstanceChargeType .reference}

更换一台或者多台按量付费实例为预付费（包年包月）实例。同时可以将实例挂载的所有按量付费云盘转换为预付费（包年包月）云盘。

## 描述 {#section_gjr_1h5_xdb .section}

调用该接口时，您需要注意：

-   实例必须处于 **运行中**（`Running`）或者 **已停止**（`Stopped`）状态。

-   实例欠费时，无法修改计费方式。

-   实例设置了自动释放时间时，无法修改计费方式。

-   实例每成功操作一次，五分钟内不能继续操作。

-   更换计费方式后，默认自动扣费。您需要确保账户余额充足，否则会生成异常订单，此时只能作废订单。

    如果您的账户余额不足，可以将参数 `AutoPay` 置为 `false`，此时会生成正常的未支付订单，您可以登录 [ECS 控制台](https://ecs.console.aliyun.com/) 支付。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：ModifyInstanceChargeType|
|RegionId|String|是|实例所属的地域 ID。您可以调用 [DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|InstanceIds|String|是|实例 ID。取值可以由多个实例 ID 组成一个 JSON 数组，格式为 \["s-xxxxxxxxx", "s-yyyyyyyyy", … "s-zzzzzzzzz"\]，最多支持 20 个 ID，ID 之间用半角逗号（`,`）隔开。|
|Period|Integer|是|购买实例的时长。|
|PeriodUnit|String|是|时长周期单位。取值范围：-   Year
-   Month
-   Week
-   Day

目前只支持 `Year`、`Week` 和 `Month`。|
|IncludeDataDisks|Boolean|否|是否将实例挂载的所有按量付费云盘转换为预付费（包年包月）云盘。取值范围：-   true
-   false

默认值：true|
|AutoPay|Boolean|否|是否自动支付。取值范围：-   true：自动支付。您需要确保账户余额充足，如果账户余额不足会生成异常订单，只能作废订单。
-   false：只生成订单不扣费。如果您的账户余额不足，会生成正常的未支付订单，此订单可登录 [ECS 控制台](https://ecs.console.aliyun.com/) 支付。

默认值：true|
|DryRun|Boolean|否|是否只预检。当 `DryRun` 值为 `true` 时，只预检测，不实际的修改付费类型操作。取值范围：-   true
-   false

默认值： false|
|ClientToken|String|否|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一。只支持 ASCII 字符，且不能超过 64 个字符。更多详情，请参阅 [如何保证幂等性](cn.zh-CN/API参考/附录/如何保证幂等性.md#)。|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|OrderId|Long|生成的订单 ID|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceChargeType
&RegionId=cn-hangzhou
&InstanceIds=["i-xxxxx1","i-xxxxx2"]
&Period=1
&PeriodUnit=Month
&AutoPay=false
&IncludeAllDisks=true
&ClientToken=xxxxxxxxxxxxxx
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<ModifyInstanceConfigurationResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
    <OrderId>10111111111xxxxx</OrderId>
</ModifyInstanceConfigurationResponse>
```

 **JSON 格式** 

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
    "OrderId": 1011111111111111,
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|ExpiredInstance|Expired instances exist in your request list.|400|实例列表中存在欠费实例。|
|InstancesIdQuotaExceed|The maximum number of Instances is exceeded.|400|单次最多能指定 20 台实例。|
|InvalidInstance.UnpaidOrder|The specified instance has unpaid order.|400|实例有未支付的订单。|
|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|400|参数 `ClientToken`参数值不合法，不能包含 ASCII 以外的字符。|
|InvalidParameter.InstanceIds|The specified InstanceIds are invalid.|400|指定的 `InstanceIds` 不合法。|
|InvalidStatus.ValueNotSupported|The instance cannot be modified in the specified status.|400|实例必须处于 **运行中**（`Running`）或者 **已停止**（`Stopped`）状态。|
|ReleaseTimeHaveBeenSet|The specified instance has been set released time.|400|您的请求中存在已设置了释放时间的实例。|
|Throttling|You have made too many requests within a short time; your request is denied due to request throttling.|400|您的操作过于频繁，请稍后再试。|
|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|403|您的账户余额不足。|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|指定的实例不存在。|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误。|

