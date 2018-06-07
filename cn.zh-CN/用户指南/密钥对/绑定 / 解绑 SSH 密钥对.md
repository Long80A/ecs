# 绑定 / 解绑 SSH 密钥对 {#concept_zzt_nl1_ydb .concept}

## 使用限制 {#section_f2n_pl1_ydb .section}

-   一台 ECS 实例只能绑定一个 SSH 密钥对。
-   除系列 I 的非 I/O 优化实例外，所有 [实例规格族](../cn.zh-CN/产品简介/实例规格族.md#) 的 Linux 实例均支持 SSH 密钥对登录。
-   如果 ECS 实例处于运行中（Running），绑定或者解绑 SSH 密钥对后，您需要 [重启实例](cn.zh-CN/用户指南/实例/重启实例.md#) 使操作生效。
-   如果 ECS 实例已经绑定了 SSH 密钥对，绑定新密钥对后，新密钥自动替换原有的密钥。
-   如果 ECS 实例使用密码认证，绑定密钥对后，密码验证方式自动失效。
-   解绑密钥对后，需要 [重置实例密码](cn.zh-CN/用户指南/实例/重置实例密码.md#) 才能使用密码认证方式正常登录 ECS 实例。

## 绑定密钥对 {#section_d4l_ql1_ydb .section}

按以下步骤绑定密钥对。

1.  登录 [ECS 控制台](https://ecs.console.aliyun.com/#/home)。
2.  选择一个地域。
3.  在左侧导航栏中，选择 **网络与安全** \> **密钥对**。
4.  找到需要操作的密钥对，在 **操作** 列中，单击 **绑定密钥对**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9730/4671_zh-CN.png)

5.  在 绑定密钥对 对话框里，在 **选择 ECS 实例** 栏中，选中需要绑定该密钥对的 ECS 实例名称，单击 **\>**，移入 **已选择** 栏中。

    **说明：** **选择 ECS 实例** 栏中的 ECS 实例名称如果显示为灰色，表示该实例为 Windows 实例或系列 I 的非 I/O 优化实例，这类实例不支持 SSH 密钥对。

6.  单击 **确定** 绑定密钥对。

## 解绑密钥对 {#section_lqq_yp1_ydb .section}

按以下步骤解绑密钥对。

1.  登录 [ECS 控制台](https://ecs.console.aliyun.com/#/home)。
2.  选择一个地域。
3.  在左侧导航栏中，选择 **网络与安全** \> **密钥对**。
4.  找到需要操作的密钥对，在 **操作** 列中，单击 **解绑密钥对**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9730/4672_zh-CN.png)

5.  在 解绑密钥对 对话框里，在 **选择 ECS 实例** 栏中，选中需要解绑的 ECS 实例名称，单击 **\>**，移入 **已选择** 栏中。
6.  单击 **确定** 解绑密钥对。

