# DescribeDiskMonitorData {#DescribeDiskMonitorData .reference}

查询一块磁盘指定时间内的使用信息。可查询磁盘实用信息包括读 IOPS、写 IOPS、读带宽（Bps）、写带宽（Bps）、读延时（ms）以及写延时（ms）。若查询的信息中出现内容缺失，是因为我们无法获取该段时间的使用信息，即磁盘状态不是 **使用中**（`In_Use`）。

## 描述 {#section_esm_5t4_ydb .section}

调用该接口时，您需要注意：

-   只能查询状态为 **使用中**（`In_Use`）的磁盘使用信息。更多详情，请参阅 [普通云盘状态表](cn.zh-CN/API参考/附录/普通云盘状态表.md#)。

-   一次最多返回 400 条数据，即指定的（`EndTime`–`StartTime`）/`Peroid` 需要小于等于 400。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeDiskMonitorData|
|DiskId|String|是|磁盘 ID。|
|StartTime|String|是|数据的起始时间。按照 [ISO8601](cn.zh-CN/API参考/附录/时间格式.md#) 标准表示，格式为 `YYYY-MM-DDThh:mm:ssZ`。使用 UTC 时间标准。如果秒（`ss`）不是 00，则自动取为下一分钟开始时。|
|EndTime|String|是|数据的结束时间。按照 [ISO8601](cn.zh-CN/API参考/附录/时间格式.md#) 标准表示，格式为 `YYYY-MM-DDThh:mm:ssZ`。使用 UTC 时间标准。如果秒（`ss`）不是 00，则自动取为下一分钟开始时。|
|Period|Integer|否|数据的精度，单位为秒。取值范围:-   60
-   600
-   3600

默认值：60|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|TotalCount|Integer|磁盘使用信息的返回条目数量。|
|MonitorData|[DiskMonitorDataType](cn.zh-CN/API参考/数据类型/DiskMonitorDataType.md#)|磁盘的监控数据集合。|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeDiskMonitorData
&DiskId=d-mydisk001
&StartTime=2014-07-23T12:07:00Z
&EndTime=2014-07-23T12:09:00Z
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DescribeDiskMonitorDataResponse>
        <MonitorData>
                <DiskMonitorData>
                        <BPSRead>0</BPSRead>
                        <BPSTotal>0</BPSTotal>
                        <BPSWrite>0</BPSWrite>
                        <DiskId>d-23b3p4r8b</DiskId>
                        <IOPSRead>0</IOPSRead>
                        <IOPSTotal>0</IOPSTotal>
                        <IOPSWrite>0</IOPSWrite>
                        <TimeStamp>2014-07-23T12:07:00Z</TimeStamp>
                </DiskMonitorData>
                <DiskMonitorData>
                        <BPSRead>0</BPSRead>
                        <BPSTotal>204</BPSTotal>
                        <BPSWrite>204</BPSWrite>
                        <DiskId>d-23b3p4r8b</DiskId>
                        <IOPSRead>0</IOPSRead>
                        <IOPSTotal>0</IOPSTotal>
                        <IOPSWrite>0</IOPSWrite>
                        <TimeStamp>2014-07-23T12:08:00Z</TimeStamp>
                </DiskMonitorData>
                <DiskMonitorData>
                        <BPSRead>0</BPSRead>
                        <BPSTotal>819</BPSTotal>
                        <BPSWrite>819</BPSWrite>
                        <DiskId>d-23b3p4r8b</DiskId>
                        <IOPSRead>0</IOPSRead>
                        <IOPSTotal>0</IOPSTotal>
                        <IOPSWrite>0</IOPSWrite>
                        <TimeStamp>2014-07-23T12:09:00Z</TimeStamp>
                </DiskMonitorData>
        </MonitorData>
        <RequestId>BF666447-B171-4076-BCBA-48437C18FD76</RequestId>
        <TotalCount>3</TotalCount>
</DescribeDiskMonitorDataResponse>
```

 **JSON 格式** 

```
{
  "MonitorData": {
    "DiskMonitorData": [
      {
        "BPSRead": 0,
        "BPSTotal": 0,
        "BPSWrite": 0,
        "DiskId": "d-23b3p4r8b",
        "IOPSRead": 0,
        "IOPSTotal": 0,
        "IOPSWrite": 0,
        "TimeStamp": "2014-07-23T12:07:00Z"
      },
      {
        "BPSRead": 0,
        "BPSTotal": 204,
        "BPSWrite": 204,
        "DiskId": "d-23b3p4r8b",
        "IOPSRead": 0,
        "IOPSTotal": 0,
        "IOPSWrite": 0,
        "TimeStamp": "2014-07-23T12:08:00Z"
      },
      {
        "BPSRead": 0,
        "BPSTotal": 819,
        "BPSWrite": 819,
        "DiskId": "d-23b3p4r8b",
        "IOPSRead": 0,
        "IOPSTotal": 0,
        "IOPSWrite": 0,
        "TimeStamp": "2014-07-23T12:09:00Z"
      }
    ]
  }, 
  "RequestId": "A48A0A77-34F5-4C33-9066-9E8D2DA0D8E2",
  "TotalCount": 3
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidEndTime.Malformed|The specified parameter “EndTime” is not valid.|400|指定的 `EndTime` 不合法。|
|InvalidParameter.TooManyDataQueried|Too many data queried.|400|一次最多返回 400 条数据，即指定的（`EndTime`–`StartTime`）/`Peroid`需要小于等于 400。|
|InvalidPeriod.ValueNotSupported|The specified parameter “Period” is not valid.|400|指定的 `Period` 不合法。|
|InvalidStartTime.TooEarly|The specified parameter “StartTime” is too early.|400|指定的 `StartTime` 太早。|
|InvalidStartTime.Malformed|The specified parameter “StartTime” is not valid.|400|指定的 `StartTime` 不合法。|
|InvalidDiskId.NotFound|The DiskId provided does not exist.|404|指定的 `DiskId` 不存在。|
|Throttling|You have made too many requests within a short time; your request is denied due to request throttling.|400|系统流控期间，请稍后再试。|

