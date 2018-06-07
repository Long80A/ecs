# DescribeClassicLinkInstances {#DescribeClassicLinkInstances .reference}

查询一台或多台与专有网络 VPC 建立了连接的经典网络类型实例。

## 描述 {#section_b3w_mmn_ydb .section}

调用该接口时，您需要注意：

-   该接口仅支持经典网络类型实例。

-   单次最多只能查询 100 台经典网络类型实例。

-   参数 `VpcId` 和 `InstanceId` 不能同时为空。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeClassicLinkInstances|
|RegionId|String|是|实例所属的地域 ID。您可以调用 [DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|InstanceId|String|否|实例 ID。最多指定 100 台实例 ID，并使用半角逗号（`,`）隔开。示例格式为 `InstanceId=i-XXX, i-XXX, i-XXX, i-XXX, ...`。|
|VpcId|String|否|VPC ID。目标 VPC 必须已 [开启 ClassicLink 功能](../../cn.zh-CN/用户指南/ClassicLink/建立ClassicLink连接.md#) 功能。|
|PageNumber|Integer|否|当前页码。起始值：1默认值：1

|
|PageSize|Integer|否|分页查询时设置的每页行数。取值范围：\[1, 100\]默认值：10

|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|TotalCount|Integer|连接总数|
|PageNumber|Integer|连接列表的页码|
|PageSize|Integer|输入时设置的每页行数|
|Links|[Link](cn.zh-CN/API参考/数据类型/Link.md#)|返回经典网络类型实例和 VPC 连接信息|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeClassicLinkInstances
&RegionId=cn-hangzhou
&VpcId=vpc-test
&InstanceId=i-test, i-test1
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DescribeClassicLinkInstancesResponse>
    <RequestId>B154D309-F3E1-4AB7-BA94-FEFCA8B89001</RequestId>
    <TotalCount>2</TotalCount>
    <PageNumber>1</PageNumber>
    <PageSize>10</PageSize>
    <Links>
        <Link>
            <InstanceId>i-test</InstanceId>
            <VpcId>vpc-test</VpcId>
        </Link>
        <Link>
            <InstanceId>i-test1</InstanceId>
            <VpcId>vpc-test</VpcId>
        </Link>
    </Links>
</DescribeClassicLinkInstancesResponse>
```

 **JSON 格式** 

```
{
    "PageNumber":1,
    "Links":{
        "Link":[{
            "InstanceId":"i-test",
            "VpcId":"vpc-test"
            },
           {
           "InstanceId": "i-test1",
           "VpcId": "vpc-test"
           }]
    },
    "TotalCount":2,
    "PageSize":10,
    "RequestId":"B154D309-F3E1-4AB7-BA94-FEFCA8B89001"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidRegionId.Malformed|The specified RegionId is invalid.|400|指定的 `RegionId`不存在或者未授权。|
|InvalidInstanceId.NotBelong|The user does not own the specified instance.|403|指定的实例不属于您。|
|InvalidParameter.InvalidInstanceIdAndVpcId|Either InstanceId or VpcId must be specified.|403|必须指定 `InstanceId` 或 `VpcId`。|
|InvalidParameter.ToManyInstanceIds|The maximum number of specified InstanceIds is exceeded.|403|指定的 `InstanceId` 超过 100 台实例 ID。|
|InvalidVpc.NotBelong|The user do not own the specified VPC.|403|指定的 VPC 不属于您。|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|指定的 `InstanceId` 不存在。|

