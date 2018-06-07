# 创建ga1实例 {#concept_zq2_z3v_xdb .concept}

## 镜像说明 {#section_rmr_2jv_xdb .section}

GPU 可视化计算 ga1 规格族实例，使用了 AMD 的 S7150 系列 GPU。阿里云和 AMD 合作优化了 GPU 的驱动程序，您需要使用 **镜像市场** 里的预装驱动的镜像，分别是：

-   CentOS 7.3 版预装 AMD GPU 驱动
-   Ubuntu16.04 版预装 AMD GPU 驱动
-   Windows 2008 R2 中文版预装 AMD GPU 驱动
-   Windows 2008 R2 英文版预装 AMD GPU 驱动

## 创建实例 {#section_tmr_2jv_xdb .section}

您可以按照 [创建ECS实例](../cn.zh-CN/个人版快速入门/步骤 2：创建ECS实例.md#) 的描述创建 ga1 规格族实例。在选择配置时，您需要注意以下几点：

-   **网络**：选择 **专有网络**。因为目前 GPU 渲染型 ga1 规格族实例只支持专有网络（VPC）。
-   **实例**：选择 **系列 III** 的 **GPU 可视化计算 ga1**。
-   **镜像**：选择 **镜像市场**，并单击 **从镜像市场选择（含操作系统）**。在镜像市场的弹出框中输入 GPU 或 AMD 搜索镜像。

    **说明：** 建议购买或订阅这几款镜像，以后创建实例时可以从**已购买的镜像**或**已经订阅的镜像**中查找。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9628/5119_zh-CN.png)


## 注意事项 {#section_rk5_kjv_xdb .section}

-   GPU 可视化计算 ga1 实例使用的驱动是阿里云和 AMD 合作提供的优化版本驱动，目前只通过阿里云提供的镜像对外输出，不提供驱动的下载链接，暂不支持客户自行安装驱动。
-   卸载或删除 GPU 驱动相关组件造成驱动不能正常工作的情况，需要通过 [更换系统盘](cn.zh-CN/用户指南/云盘/更换系统盘（公共镜像）.md#) 的方式恢复 GPU 的相关功能。

    **警告：** 此操作会造成数据丢失。

-   创建 GPU 可视化计算 ga1 实例时，选择其它的镜像会造成实例的驱动不能正常工作，用户需要通过 [更换系统盘](cn.zh-CN/用户指南/云盘/更换系统盘（公共镜像）.md#) 的方式重新选择预安装 AMD GPU 驱动的镜像。
-   对于 Windows 系统，GPU 驱动安装生效后，阿里云控制台的 **远程连接** 功能不可用，管理终端 始终显示黑屏或停留在启动界面。请通过其它协议进入系统，如 Windows 自带的远程桌面连接（RDP）。
-   Windows 自带的远程连接（RDP）协议不支持 DirectX、OpenGL 等相关应用，您需要自行安装 VNC 服务和客户端，或其它支持的协议，例如 PCOIP、XenDeskop HDX 3D 等。

