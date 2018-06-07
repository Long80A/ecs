# DescribeLaunchTemplates {#DescribeLaunchTemplates .reference}

查询可用的实例启动模板。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeLaunchTemplates|
|RegionId|String|是|实例启动模板所属的地域 ID。您可以调用 [DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|LaunchTemplateId|String|否|实例启动模板 ID。您必须指定 `LaunchTemplateId` 或 `LaunchTemplateName` 以确定模板。|
|LaunchTemplateName|String|否|实例启动模板名称。|
|PageNumber|Integer|否|实例启动模板列表的页码。起始值：1默认值：1

|
|PageSize|Integer|否|分页查询时设置的每页行数。最大值：50 默认值：10

|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|TotalCount|Integer|实例启动模板总个数|
|PageNumber|Integer|当前页码|
|PageSize|Integer|分页查询时设置的每页行数|
|LaunchTemplateSet|[LaunchTemplateSet](#LaunchTemplateSet)|实例启动模板的信息集合|

**数据类型 LaunchTemplateSet** 

|名称|类型|描述|
|:-|:-|:-|
|CreateTime|String|实例启动模板创建时间|
|ModifiedTime|String|修改时间|
|LaunchTemplateId|String|模板 ID|
|LaunchTemplateName|String|模板名称|
|DefaultVersionNumber|Long|模板默认版本号|
|LatestVersionNumber|Long|模板最新版本号|
|CreatedBy|String|模板的创建者|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeLaunchTemplates
&RegionId=cn-hangzhou
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DescribeLaunchTemplatesResponse>
	<RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
	<TotalCount>1</TotalCount>
	<PageNumber>1</PageNumber>
	<PageSize>10</PageSize>
	<LaunchTemplateSets>
		<LaunchTemplateSet>
			<CreateTime>2018-05-14T14:18:00Z</CreateTime>
			<ModifiedTime>2018-05-14T14:18:00Z</ModifiedTime>
			<LaunchTemplateid>lt-m5e3ofjr1zn1aw7xxxx</LaunchTemplateid>
			<LaunchTemplateName>wd-1526307480xxx</LaunchTemplateName>
			<DefaultVersionNumber>1</DefaultVersionNumber>
			<LatestVersionNumber>1</LatestVersionNumber>
			<CreatedBy>1942111349714xxx</CreatedBy>
		</LaunchTemplateSet>
	</LaunchTemplateSets>
</DescribeLaunchTemplatesResponse>
```

 **JSON 格式** 

```
{
	"RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
	"TotalCount":1,
	"PageNumber":1,
	"PageSize":10,
	"LaunchTemplateSets":{
		"LaunchTemplateSet":[{
			"LaunchTemplateName":"wd-1526307480xxx",
			"CreatedBy":"1942111349714xxx",
			"ModifiedTime":"2018-05-14T14:18:00Z",
			"LatestVersionNumber":1,
			"CreateTime":"2018-05-14T14:18:00Z",
			"LaunchTemplateId":"lt-m5e3ofjr1zn1aw7qdxxx",
			"DefaultVersionNumber":1
		}]
	}
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|MissingParameter|The input parameter “\{0\}” that is mandatory for processing this request is not supplied.|400|缺失必需参数。|
|InvalidParameter|the parameter\(s\) “\{0\}” provided is\(are\) invalid.|400|指定的参数不合法。|
|InnerServiceFailed|call inner service failed|403|服务器内部错误。|

