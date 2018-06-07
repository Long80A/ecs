# 创建GPU计算型实例 {#concept_g5s_g2z_xdb .concept}

## 创建实例 {#section_v1b_nxz_xdb .section}

您可以按照 [创建ECS实例](../cn.zh-CN/个人版快速入门/步骤 2：创建ECS实例.md#) 的描述创建gn4、gn5或gn5i实例，创建时需要注意以下配置。

-   **地域**：不同的实例规格族供应的地域信息不同。如下所示：

    -   gn4：华北2（可用区A）、华东2（可用区B）、华南1（可用区C）
    -   gn5：华北2（可用区C、E）、华北5（可用区A）、华东1（可用区G、F）、华东2（可用区D、B、E）、华南1（可用区D）、香港（可用区C、B）、亚太东南1（可用区B、A）、亚太东南2（可用区A）、亚太东南3（可用区A）、亚太东南5（可用区A）、美国西部1（可用区B、A）、美国东部1（可用区B、A）、欧洲中部1（可用区A）

        **说明：** 如果您要在gn5实例上部署NGC（NVIDIA GPU CLOUD）环境，选择地域时请参见 [在gn5实例上部署NGC环境](https://help.aliyun.com/document_detail/69102.html)。

    -   gn5i：华北2（可用区C、E、A）、华东1（可用区B）、华东2（可用区D、B）、华南1（可用区A）
    如果ECS创建页面显示的地域和可用区信息与上述描述不符，以ECS创建页面上显示的信息为准。

-   **镜像**：
    -   如果您需要安装GPU驱动和CUDA库，可以选择以下任一种方式：
        -   选择 **公共镜像** 中的CentOS 64位（目前提供的所有版本都支持）、Ubuntu16.04 64位或SUSE Linux Enterprise Server 12 SP2 64位镜像，并选择 **自动安装GPU驱动**。再选择需要的CUDA库和GPU驱动的版本。

            **说明：** 

            -   您可以根据您的业务需要选择合适的GPU驱动版本。如果是新业务系统，建议您在下拉菜单中选择最新的GPU驱动版本。
            -   如果选择 **自动安装GPU驱动**，**系统配置** 的 **高级选项** 中会自动生成 **实例自定义数据**，即自动安装CUDA库和GPU驱动的shell脚本。实例第一次启动后，cloud-init会自动执行脚本，自动安装GPU驱动。更多信息，参见 [自动安装GPU驱动脚本注意事项](#GpuDriveScript)。
        -   选择 **镜像市场**，并搜索 NVIDIA，在搜索结果中选择需要的镜像。目前只支持CentOS 7.3和Ubuntu 16.04。
    -   如果gn4、gn5或gn5i实例要用于深度学习，可以选择预装深度学习框架的镜像：选择 **镜像市场**，并搜索 深度学习，在搜索结果中选择需要的镜像。目前只支持Ubuntu 16.04和CentOS 7.3。
    -   除上述以外的其他镜像，实例创建完成后，自行 [下载并安装GPU驱动](#installDrive)。
-   **实例**：选择 **异构计算GPU/FPGA** \> **GPU计算型**，按需求选择合适的实例规格。
-   **网络**：选择 **专有网络**。
-   **公网带宽**：根据您的实际需要选择带宽。

    **说明：** 如果使用Windows 2008 R2镜像，GPU驱动安装生效后，您不能使用控制台的 [**远程连接**](cn.zh-CN/用户指南/连接实例/使用管理终端连接 ECS 实例.md#) 功能连接gn4、gn5或gn5i实例，所以，您必须选择 **分配公网IP地址**，或者创建实例后 [绑定EIP](../../cn.zh-CN/用户指南/绑定EIP.md#)。

-   **登录凭证**：根据实际需求设置登录凭证。

    **说明：** 建议您不要选择 **创建后设置**。实例创建成功后，GPU驱动安装成功之前，如果您需要登录实例，必须重置密码或者绑定SSH密钥对，需要重启实例使修改生效，而重启操作会导致GPU驱动安装失败。

-   **实例自定义数据**：如果选择了 **自动安装GPU驱动**，这里会显示自动安装CUDA库和GPU驱动的shell脚本。请您仔细阅读脚本内容和注意事项。

## 查看自动安装GPU驱动进程 {#section_gbb_nxz_xdb .section}

如果您选择了 **自动安装GPU驱动**，实例创建完成后，您可以 [远程连接实例](cn.zh-CN/用户指南/连接实例/连接实例概述.md#)，通过安装日志 `/root/nvidia_install.log`查看GPU驱动的安装进程。

**说明：** GPU驱动安装完成前，您不能操作GPU，也不能安装其他GPU相关软件，以免自动安装失败。

## 下载并安装GPU驱动 {#installDrive .section}

如果使用没有预装GPU驱动的镜像，您必须为实例安装GPU驱动。操作步骤如下：

1.  获取GPU驱动安装包：
    1.  进入 [NVIDIA 官网](http://www.nvidia.com/Download/index.aspx?lang=cn)。
    2.  手动查找适用于实例的驱动程序，并单击 **搜索**。筛选信息说明如下表所示。

        | |gn4|gn5|gn5i|
        |:-|:--|:--|:---|
        |产品类型|Tesla|Tesla|Tesla|
        |产品系列|M-Class|P-Series|P-Series|
        |产品家族|M40|Tesla P100|Tesla P4|
        |操作系统|根据实例的镜像选择对应的版本。如果下拉列表中没有显示服务器操作系统，请单击下拉列表底部的 **选择所有操作系统**。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9632/5114_zh-CN.png)

|

    3.  确认无误后，单击 **下载** 按钮。
2.  安装GPU驱动：
    -   Windows实例：直接双击安装GPU驱动。
    -   Linux实例：按以下步骤安装驱动
        1.  下载并安装kernel对应版本的kernel-devel和kernel-header包。
        2.  运行以下命令，确认已经完成下载并安装kernel-devel和kernel-header包：

            ```
            sudo rpm -qa | grep $(uname -r)
            ```

            以CentOS 7.3为例，如果出现以下类似信息，表示已经完成安装。

            ```
            
            kernel-3.10.0-514.26.2.el7.x86_64
            kernel-headers-3.10.0-514.26.2.el7.x86_64
            kernel-tools-libs-3.10.0-514.26.2.el7.x86_64
            python-perf-3.10.0-514.26.2.el7.x86_64
            kernel-tools-3.10.0-514.26.2.el7.x86_64
            ```

        3.  按NVIDIA官网GPU驱动下载页的 **其他信息** 描述安装GPU驱动。

            以Linux 64-bit Ubuntu 14.04为例：

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9632/5117_zh-CN.png)


## 安装GRID驱动 {#section_ubb_nxz_xdb .section}

如果gn5或gn5i实例需要支持OpenGL图形显示，必须安装GRID驱动，具体操作，请参见 [在gn5或gn5i实例中安装GRID驱动](https://help.aliyun.com/document_detail/66441.html)。

## 注意事项 {#section_urs_qd1_ydb .section}

**远程连接功能**

对于Windows 2008 R2及以下版本，GPU驱动安装生效后，控制台的 [**远程连接**](cn.zh-CN/用户指南/连接实例/使用管理终端连接 ECS 实例.md#) 功能不可用，管理终端 会始终显示黑屏或停留在启动界面。请您通过其他协议进入系统，如Windows自带的远程连接（RDP）。

Windows自带的远程连接（RDP）协议不支持DirectX、OpenGL等相关应用，您需自行安装VNC服务和客户端，或其他支持的协议，例如PCOIP、XenDeskop HDX 3D等。

**自动安装GPU驱动脚本**

关于自动安装GPU驱动的shell脚本，注意事项如下：

-   该脚本会自动下载并安装NVIDIA GPU的驱动和CUDA库。
-   因实例规格的内网带宽和vCPU核数不同，实际自动安装时间为4.5分钟 ~ 10分钟不等。安装GPU驱动时，您不能操作GPU，也不能安装其他GPU相关软件，以免自动安装失败。
-   自动安装结束后，实例自动重启，使驱动生效。
-   脚本会自动开启GPU驱动的 **Persistence Mode**，并将该设置添加到系统自启动脚本中，确保实例重启后还能默认开启该模式。该模式下GPU驱动工作更稳定。
-   [更换操作系统](cn.zh-CN/用户指南/实例/更换操作系统.md#) 时，您需要注意以下信息：
    -   如果原来的镜像是Ubuntu16.04 64位或SUSE Linux Enterprise Server 12 SP2 64位，换成其他镜像后，无法自动安装GPU驱动。
    -   如果原来的镜像是CentOS的某个版本，换成其他版本的CentOS镜像后，GPU驱动能正常安装。
    -   如果换成其他不支持自动安装GPU驱动脚本的镜像，无法自动安装GPU驱动。
-   安装过程中会生成相应的安装日志，日志存放路径为 /root/nvidia\_install.log。您可以通过日志查看驱动安装是否成功。如果失败，您可以通过日志查看失败原因。

