# DescribeLaunchTemplateVersions {#DescribeLaunchTemplateVersions .reference}

查询实例启动模板版本。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeLaunchTemplateVersions|
|RegionId|String|是|实例启动模板所属的地域 ID。您可以调用 [DescribeRegions](cn.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|LaunchTemplateId|String|否|实例启动模板 ID。您必须指定 `LaunchTemplateId` 或 `LaunchTemplateName` 以确定模板。|
|LaunchTemplateName|String|否|实例启动模板名称。|
|LaunchTemplateVersion.N|Long|否|一个或多个实例启动模板版本。|
|MinVersion|Long|否|通过范围指定版本时的最小版本号。|
|MaxVersion|Long|否|通过范围指定版本时的最大版本号。|
|DefaultVersion|Boolean|否|是否查询默认版本。|
|PageNumber|Integer|否|实例启动模板列表的页码。起始值：1默认值：1

|
|PageSize|Integer|否|分页查询时设置的每页行数。最大值：50 默认值：10

|

 **返回参数** 

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|TotalCount|Integer|实例启动模板总数|
|PageNumber|Integer|当前页码|
|PageSize|Integer|分页查询时设置的每页行数|
|LaunchTemplateVersionSet|[LaunchTemplateVersionSet](#LaunchTemplateVersionSet)|关于模板版本的信息|

**数据类型 LaunchTemplateVersionSet** 

|名称|类型|描述|
|:-|:-|:-|
|CreateTime|String|模板创建时间|
|ModifiedTime|String|模板修改时间|
|LaunchTemplateId|String|模板 ID|
|LaunchTemplateName|String|模板名称|
|DefaultVersion|Boolean|模板默认版本|
|VersionNumber|Long|模板版本号|
|VersionDescription|Long|模板版本描述|
|createdBy|String|模板的创建者|
|LaunchTemplateData|[LaunchTemplateData](#LaunchTemplateData)|模板具体配置|

**数据类型 LaunchTemplateData** 

|名称|类型|描述|
|:-|:-|:-|
|ImageId|String|镜像 ID|
|InstanceType|String|实例规格|
|SecurityGroupId|String|安全组 ID|
|VSwitchId|String|虚拟交换机 ID|
|InstanceName|String|实例名称|
|Description|String|实例描述|
|InternetMaxBandwidthIn|String|公网入带宽最大值|
|InternetMaxBandwidthOut|String|公网出带宽最大值|
|HostName|String|实例主机名|
|ZoneId|String|实例所属的可用区 ID|
|SystemDisk.Category|String|系统盘种类|
|SystemDisk.Size|Integer|系统盘大小，单位为 GB|
|SystemDisk.DiskName|String|系统盘名称|
|SystemDisk.Description|String|系统盘描述|
|DataDisk.n.Size|Integer|数据盘大小|
|DataDisk.n.SnapshotId|String|数据盘使用的快照 ID|
|DataDisk.n.Category|String|数据盘的磁盘种类|
|DataDisk.n.Encrypted|Boolean|数据盘是否加密|
|DataDisk.n.DiskName|String|系统盘名称|
|DataDisk.n.Description|String|系统盘描述|
|DataDisk.n.DeleteWithInstance|String|数据盘是否随实例释放而释放|
|IoOptimized|String|是否为 I/O 优化实例|
|NetworkInterface.n.PrimaryIpAddress|String|弹性网卡的主私有 IP 地址|
|NetworkInterface.n.VSwitchId|String|弹性网卡所属的虚拟交换机 ID|
|NetworkInterface.n.SecurityGroupId|String|所属的安全组 ID 必须是同一个 VPC 下的安全组|
|NetworkInterface.n.NetworkInterfaceName|String|弹性网卡名称|
|NetworkInterface.n.Description|String|弹性网卡描述信息|
|Period|Integer|购买资源的时长|
|InternetChargeType|String|公网带宽计费方式|
|NetworkType|String|网络类型|
|UserData|String|实例自定义数据，需要以 Base64 方式编码|
|KeyPairName|String|密钥对名称|
|RamRoleName|String|实例 RAM 角色名称|
|AutoReleaseTime|String|自动释放时间|
|SpotStrategy|String|后付费实例的竞价策略|
|SpotPriceLimit|Float|设置实例的每小时最高价格|
|SecurityEnhancementStrategy|String|是否开启安全加固|
|Tag.n.Key|String|实例的标签键|
|Tag.n.Value|Float|实例的标签值|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeLaunchTemplateVersions
&RegionId=cn-hangzhou
&LaunchTemplateName=lt-name1
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DescribeLaunchTemplateVersionsResponse>
	<RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
	<TotalCount>1</TotalCount>
	<PageNumber>1</PageNumber>
	<PageSize>10</PageSize>
	<LaunchTemplateVersionSets>
		<LaunchTemplateVersionSet>
			<CreateTime>2018-05-14T14:18:00Z</CreateTime>
			<ModifiedTime>2018-05-14T14:18:00Z</ModifiedTime>
			<LaunchTemplateId>lt-m5e3ofjr1zn1aw7xxxx</LaunchTemplateId>
			<LaunchTemplateName>wd-1526307480xxx</LaunchTemplateName>
			<DefaultVersion>true</DefaultVersion>
			<VersionNumber>1</VersionNumber>
			<CreatedBy>1942111349714xxx</CreatedBy>
			<VersionDescription>wwww</VersionDescription>
			<launchtemplatedata>
					 <imageowneralias>ImageOwnerAlias1</imageowneralias>
					 <description>Description1</description>
					 <resourcegroupid>ResourceGroupId1</resourcegroupid>
					 <datadisks>
						 <datadisk>
							 <snapshotid>SnapshotId1</snapshotid>
							 <description>Description1</description>
							 <category>cloud_efficiency</category>
							 <encrypted>false</encrypted>
							 <size>44</size>
							 <deletewithinstance>true</deletewithinstance>
							 <diskname>DataDiskName1</diskname>
						 </datadisk>
					 </datadisks>
					 <userdata>UserData1</userdata>
					 <systemdisk.diskname>SystemDiskDiskName1</systemdisk.diskname>
					 <systemdisk.size>44</systemdisk.size>
					 <ramrolename>RamRoleName1</ramrolename>
					 <networktype>NetworkType1</networktype>
					 <networkinterfaces>
						 <networkinterface>
							 <description>Description1</description>
							 <securitygroupid>SecurityGroupId1</securitygroupid>
							 <vswitchid>VSwitchId1</vswitchid>
							 <networkinterfacename>NetworkInterfaceName1</networkinterfacename>
							 <primaryipaddress>PrimaryIpAddress1</primaryipaddress>
						 </networkinterface>
					 </networkinterfaces>
					 <imageid>windows2008.vhd</imageid>
					 <spotpricelimit>1</spotpricelimit>
					 <systemdisk.category>cloud_efficiency</systemdisk.category>
					 <instancetype>ecs.xn4.small</instancetype>
					 <spotstrategy>SpotWithPriceLimit</spotstrategy>
					 <hostname>HostName1</hostname>
					 <tags>
						 <instancetag>
							 <value>bb</value>
							 <key>ss</key>
						 </instancetag>
					 </tags>
					 <keypairname>KeyPairName1</keypairname>
					 <systemdisk.iops>22</systemdisk.iops>
					 <iooptimized>true</iooptimized>
					 <zoneid>ZoneId1</zoneid>
					 <systemdisk.description>SystemDiskDescription1</systemdisk.description>
					 <securitygroupid>sg-tiantt1234</securitygroupid>
					 <vswitchid>vsw-xxxxxx</vswitchid>
					 <period>1</period>
					 <internetchargetype>PayByBandwidth</internetchargetype>
					 <instancename>InstanceName1</instancename>
					 <internetmaxbandwidthout>20</internetmaxbandwidthout>
					 <internetmaxbandwidthin>1</internetmaxbandwidthin>
					 <securityenhancementstrategy>Active</securityenhancementstrategy>
					 <autoreleasetime>2019-10-21T00:00:00Z</autoreleasetime>
				 </launchtemplatedata>
		</LaunchTemplateVersionSet>
	</LaunchTemplateVersionSets>
</DescribeLaunchTemplateVersionsResponse>
```

 **JSON 格式** 

```
{
	"RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
	"TotalCount":1,
	"PageNumber":1,
	"PageSize":10,
	"LaunchTemplateVersionSets":{
		"LaunchTemplateVersionSet":[{
			{
					"LaunchTemplateData":{
						"Description":"Description1",
						"ResourceGroupId":"ResourceGroupId1",
						"DataDisks":{
							"DataDisk":[
								{
									"SnapshotId":"SnapshotId1",
									"Description":"Description1",
									"Category":"cloud_efficiency",
									"Encrypted":false,
									"Size":44,
									"DeleteWithInstance":true,
									"DiskName":"DataDiskName1"
								}
							]
						},
						"UserData":"UserData1",
						"SystemDisk.DiskName":"SystemDiskDiskName1",
						"SystemDisk.Size":44,
						"RamRoleName":"RamRoleName1",
						"NetworkType":"NetworkType1",
						"NetworkInterfaces":{
							"NetworkInterface":[
								{
									"Description":"Description1",
									"SecurityGroupId":"SecurityGroupId1",
									"VSwitchId":"VSwitchId1",
									"NetworkInterfaceName":"NetworkInterfaceName1",
									"PrimaryIpAddress":"PrimaryIpAddress1"
								}
							]
						},
						"ImageId":"windows2008.vhd",
						"SpotPriceLimit":1,
						"SystemDisk.Category":"cloud_efficiency",
						"InstanceType":"ecs.xn4.small",
						"SpotStrategy":"SpotWithPriceLimit",
						"HostName":"HostName1",
						"Tags":{
							"InstanceTag":[
								{
									"Value":"bb",
									"Key":"ss"
								}
							]
						},
						"KeyPairName":"KeyPairName1",
						"SystemDisk.Iops":22,
						"IoOptimized":"true",
						"ZoneId":"ZoneId1",
						"SystemDisk.Description":"SystemDiskDescription1",
						"SecurityGroupId":"sg-tiantt1234",
						"VSwitchId":"vsw-xxxxxx",
						"Period":1,
						"InternetChargeType":"PayByBandwidth",
						"InstanceName":"InstanceName1",
						"InternetMaxBandwidthOut":20,
						"InternetMaxBandwidthIn":1,
						"SecurityEnhancementStrategy":"Active",
						"AutoReleaseTime":"2019-10-21T00:00:00Z"
					},
					"LaunchTemplateName":"wd-1526308145065",
					"CreatedBy":"1942111349714263",
					"VersionDescription":"wwwdesc",
					"ModifiedTime":"2018-05-14T14:29:05Z",
					"CreateTime":"2018-05-14T14:29:05Z",
					"DefaultVersion":true,
					"LaunchTemplateId":"lt-m5efs0xpur7pey3y9yt7",
					"VersionNumber":1
				}
		}]
	}
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidLaunchTemplate.NotFound|The specified LaunchTemplateId “\{0\}” LaunchTemplateName “\{1\}” is not found.|400|指定的 `LaunchTemplateId` 和 `LaunchTemplateName`不存在。|
|MissingParameter|The input parameter “\{0\}” that is mandatory for processing this request is not supplied.|400|缺失必需参数。|
|InvalidParameter|the parameter\(s\) “\{0\}” provided is\(are\) invalid.|400|指定的参数不合法。|
|InnerServiceFailed|call inner service failed|403|服务器内部错误。|

