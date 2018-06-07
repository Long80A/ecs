# DescribeSpotPriceHistory {#DescribeSpotPriceHistory .reference}

查询竞价实例近 30 天内的历史价格。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeSpotPriceHistory|
|RegionId|String|是|实例所属的地域 ID。您可以调用 [DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|ZoneId|String|是|可用区 ID。|
|NetworkType|String|是|竞价实例网络类型。取值范围：-   classic：表示竞价实例的网络类型为经典网络
-   vpc：表示竞价实例的网络类型为专有网络

|
|InstanceType|String|是|实例规格。|
|IoOptimized|String|否|是否为 I/O 优化实例。取值范围：-   optimized：表示竞价实例为 I/O 优化实例
-   none：表示竞价实例为非 I/O 优化实例

系列 I 实例默认值：none

系列 II 实例默认值：optimized系列 III 实例默认值：optimized

|
|StartTime|String|否|查询竞价实例历史价格的起始时间。按照 [ISO8601](cn.zh-CN/API参考/附录/时间格式.md#) 标准表示，需要使用 UTC 时间，格式为 YYYY-MM-DDTHH:MM:SSZ 。默认为空，空代表结束时间前 3 天，最大值不得超过指定的结束时间 30 天。|
|EndTime|String|否|查询竞价实例历史价格的结束时间。按照 ISO8601 标准表示，需要使用 UTC 时间，格式为 YYYY-MM-DDTHH:MM:SSZ 。默认为空，空表示当前时间。

|
|Offset|Integer|否|查询开始行。默认值：0

|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|NextOffset|Integer|下一页开始行，查询下一页的数据，参数 Offset 的指定值为该值|
|SpotPrices|[SpotPriceType](cn.zh-CN/API参考/数据类型/SpotPriceType.md#)|竞价价格详情|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeSpotHistory
&RegionId=cn-hangzhou
&ZoneId=cn-hanghzhou-c
&NetworkType=vpc
&InstanceType=ecs.t1.xsmall
&IoOptimized=none
&UtcStartTime=2017-08-22T08:45:08Z...
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DescribeSpotPriceHistoryResponse>
    <RequestId>xxxxxxxxxxxxxx</RequestId>
    <NextOffset>1000</NextOffset>
    <SpotPrices>
        <SpotPriceType>
            <IoOptimized>none</IoOptimized>
            <OriginPrice>0.028</OriginPrice>
            <NetworkType>classic</NetworkType>
            <Timestamp>2017-09-18T11:00:00Z</Timestamp>
            <ZoneId>cn-hangzhou-c</ZoneId>
            <SpotPrice>0.006</SpotPrice>
            <InstanceType>ecs.t1.xsmall</InstanceType>
        </SpotPriceType>
        <SpotPriceType>
            <IoOptimized>none</IoOptimized>
            <OriginPrice>0.028</OriginPrice>
            <NetworkType>classic</NetworkType>
            <Timestamp>2017-09-18T12:00:00Z</Timestamp>
            <ZoneId>cn-hangzhou-c</ZoneId>
            <SpotPrice>0.006</SpotPrice>
            <InstanceType>ecs.t1.xsmall</InstanceType>
    </SpotPriceType>
</SpotPrices>
</DescribeSpotPriceHistoryResponse>
```

 **JSON 格式** 

```
{
    "RequestId":"xxxxxxxxxxxxxx",
    "NextOffset":1000,
    "SpotPrices":
    {
        "SpotPriceType":[
        {
            "IoOptimized":"none",
            "OriginPrice":0.028,
            "NetworkType":"classic",
            "Timestamp":"2017-09-18T11:00:00Z",
            "ZoneId":"cn-hangzhou-c","SpotPrice":0.006,
            "InstanceType":"ecs.t1.xsmall"
            }
        ]
    }
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidParams.EndTime|The format of the specified parameter EndTime is invalid.|400|参数 `EndTime` 格式应遵循 ISO8601 标准表示。|
|InvalidParams.InstanceType|The specified parameter InstanceType is required.|400|参数 `InstanceType` 不得为空。|
|InvalidParams.IoOptimized|The value of specified parameter IoOptimized is invalid.|400|参数 `IoOptimized` 的取值有误。|
|InvalidParams.NetworkType|The value of specified parameter NetworkType is invalid.|400|参数 `NetworkType` 的取值有误。|
|InvalidParams.RegionId|The specified parameter RegionId is required.|400|参数 `RegionId` 不得为空。|
|InvalidParams.StartTime|The format of the specified parameter StartTime is invalid.|400|参数 `StartTime` 格式应遵循 ISO8601 标准表示。|
|InvalidParams.ZoneId|The specified parameter ZoneId is required.|400|参数 `ZoneId` 不得为空。|

