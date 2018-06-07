# DeleteDisk {#DeleteDisk .reference}

释放一块按量付费数据盘。磁盘类型包括普通云盘、高效云盘和SSD云盘。

## 描述 {#section_qfk_mm5_xdb .section}

调用该接口时，您需要注意：

-   您的磁盘手动快照会被保留。

-   您可以通过 [ModifyDiskAttribute](cn.zh-CN/API参考/磁盘/ModifyDiskAttribute.md#) 设置是否保留或者同时释放自动快照。建议您及时删除不必要的快照，以保持足够的快照额度完成周期性的自动快照策略。

-   释放磁盘时，云盘的状态必须为 **待挂载**（`Available`）。

-   如果指定 ID 的磁盘不存在，请求将被忽略。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DeleteDisk|
|DiskId|String|是|需要释放的云盘设备 ID。|

## 返回参数 {#section_f54_lk5_xdb .section}

全是公共返回参数。参阅 [公共参数](cn.zh-CN/API参考/调用方式/公共参数.md#commonResponseParameters)

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DeleteDisk
&DiskId=d-23jbf2v5m
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DeleteDiskResponse>
    <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteDiskResponse>
```

 **JSON 格式** 

```
{
    "RequestId": "CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|DiskCreatingSnapshot|The operation is denied due to a snapshot of the specified disk is not completed yet.|403|指定的磁盘正在创建快照，请稍后再试。|
|DiskNotPortable|The specified disk is not a portable disk.|403|磁盘不是可卸载的磁盘|
|DiskTypeViolation|The specified disk is a system disk and cannot support the operation.|403|您不能释放实例的系统盘。|
|IncorrectDiskStatus|The current disk status does not support this operation.|403|磁盘的状态必须为 **待挂载**（`Available`）。|

