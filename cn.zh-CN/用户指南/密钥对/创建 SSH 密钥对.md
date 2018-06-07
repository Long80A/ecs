# 创建 SSH 密钥对 {#concept_wy4_th1_ydb .concept}

## 使用限制 {#section_odb_g31_ydb .section}

-   [SSH 密钥对](../cn.zh-CN/产品简介/网络和安全性/SSH 密钥对.md#)，简称密钥对，仅支持 Linux 实例。
-   目前，阿里云只支持创建 2048 位的 RSA 密钥对。
    -   阿里云会保存密钥对的公钥部分。
    -   密钥对创建成功后，您需要下载并妥善保管私钥。
    -   私钥使用未加密的 PEM（Privacy-enhanced Electronic Mail） 编码的 `PKCS#8` 格式。
-   一个云账号在一个地域最多可以拥有 500 个密钥对。

## 创建密钥对 {#section_f5c_h31_ydb .section}

1.  登录 [ECS 控制台](https://ecs.console.aliyun.com/#/home)。
2.  选择地域。
3.  在左侧导航栏中，单击 **密钥对**。
4.  在 密钥对 页面上，单击 **创建密钥对**。
5.  在 创建密钥对 页面，设置密钥对名称，并选择 **自动新建密钥对**。

    **说明：** 指定的密钥对名称不应该与已有的密钥对名称重复，也不应该与删除前仍绑定实例的密钥对名称重复。否则，控制台会报错“密钥对已存在”。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9728/4669_zh-CN.png)

6.  单击 **确定** 创建密钥对。

    **说明：** 创建密钥对后，您需要下载并妥善保管私钥。当该密钥对绑定某个 ECS 实例时，如果没有私钥，您将再也不能登录该 ECS 实例。


密钥对创建成功后，您可以在密钥对列表里看到新创建的密钥对信息，包括 **密钥对名称**、**密钥对指纹** 等。

## 后续操作 {#section_nn4_5j1_ydb .section}

创建密钥对后，您可以为 ECS 实例 [绑定 / 解绑 SSH 密钥对](cn.zh-CN/用户指南/密钥对/绑定 / 解绑 SSH 密钥对.md#)。

