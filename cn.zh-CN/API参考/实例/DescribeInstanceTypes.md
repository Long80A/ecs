# DescribeInstanceTypes {#DescribeInstanceTypes .reference}

查询云服务器 ECS 提供的实例规格资源。更多详情，请参阅 [实例规格族](../cn.zh-CN/产品简介/实例规格族.md#)。

## 描述 {#section_c31_xmt_xdb .section}

根据 DescribeInstanceTypes 查询的实例规格列表与创建实例时按量付费实例列表一致。更多详情，请参阅 [按量付费](../cn.zh-CN/产品定价/按量付费.md#) 和 [使用限制](../cn.zh-CN/用户指南/使用限制.md#)。

如果您需要使用更多实例规格资源，可以 [提交工单](https://selfservice.console.aliyun.com/ticket/createIndex.htm) 联系我们。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeInstanceTypes|
|InstanceTypeFamily|String|否|实例规格所属的规格族。更多详情，请参阅 [实例规格族](../cn.zh-CN/产品简介/实例规格族.md#)。|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|InstanceTypes|[InstanceTypeItemType](cn.zh-CN/API参考/数据类型/InstanceTypeItemType.md#)|由实例规格项 `InstanceTypeItemType` 组成的集合|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceTypes
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DescribeInstanceTypesResponse>
    <RequestId>1651FBB6-4FBF-49FF-A9F5-DF5D696C7EC6</RequestId>
    <InstanceTypes>
        <InstanceType>
            <InstanceTypeId>ecs.t1.xsmall</InstanceTypeId>
            <CpuCoreCount>1</CpuCoreCount>
            <MemorySize>0.5</MemorySize>
        </InstanceType>
        <InstanceType>
            <InstanceTypeId>ecs.t1.small</InstanceTypeId>
            <CpuCoreCount>1</CpuCoreCount>
            <MemorySize>1</MemorySize>
        </InstanceType>
    </InstanceTypes>
</DescribeInstanceTypesResponse>
```

 **JSON 格式** 

```
{
    "RequestId": "1651FBB6-4FBF-49FF-A9F5-DF5D696C7EC6",
    "InstanceTypes": {
        "InstanceType": [{
            "InstanceTypeId": "ecs.t1.xsmall",
            "CpuCoreCount": 1,
            "MemorySize": 0.5
        },
        {
            "InstanceTypeId": "ecs.t1.small",
            "CpuCoreCount": 1,
            "MemorySize": 1
        }]
    }
}
```

## 错误码 {#ErrorCode .section}

全是公共错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

