# ECS 使用须知 {#concept_q1h_cyw_wdb .concept}

为了保证您云服务器 ECS 实例的正常运行，在使用之前，务必认真阅读以下注意事项。

## **操作须知** {#section_mqk_ddx_wdb .section}

**禁忌**

-   禁止用户使用 ECS 实例做流量穿透服务。违规者最高处以关停并锁定实例的处罚，并清退处理。
-   禁止使用 ECS 针对淘宝等电商网站从事刷单、刷销量、刷广告、进行虚假网站交易的网络行为。
-   不要开启 SELinux。
-   不要卸载相关硬件的驱动程序。
-   不要随意修改网卡 MAC 地址。

**建议**

-   对于 4 GiB 以上内存的云服务器，请选择 64 位操作系统，因为 32 位操作系统存在 4 GiB 的内存寻址限制。目前支持的 64 位操作系统包括（版本请以购买实例页面上的显示为准）：
    -   Aliyun Linux 64 位
    -   CoreOS 64 位
    -   CentOS 64 位
    -   Debian 64 位
    -   FreeBSD 64 位
    -   OpenSUSE 64 位
    -   SUSE Linux 64 位
    -   Ubuntu 64 位
    -   Windows 64 位
-   Windows 32 位操作系统支持最高 CPU 核数为 4 核。
-   将 Windows 实例用于建站、部署 Web 环境，需要至少 2 GiB 内存。1 核 1 GiB 实例规格无法启动 MySQL。
-   为保证服务的连续性，避免因宕机迁移而导致的服务不可用，建议将相关软件都设置成开机启动。如果有应用服务连接的数据库，需要在程序中设置成自动重连机制。
-   I/O 优化实例不要关闭 aliyun-service 服务。
-   不建议升级云服务器的内核和操作系统版本。如果需要升级内核，请参考 [如何避免升级Linux实例内核后无法启动](https://help.aliyun.com/document_detail/59360.html)。

## Windows 操作系统须知 {#section_ajc_kdx_wdb .section}

-   不要关闭 Windows 系统自带的 shutdownmon.exe 进程。关闭后可能会使服务器重启时间变长。
-   不要重命名、删除或禁用 Windows 下的 Administrator 账号，以免影响服务器使用。
-   如果您使用普通云盘，不建议使用虚拟内存。如果是高效云盘或 SSD 云盘，可以根据实际情况使用虚拟内存。

## Linux 操作系统须知 {#section_opn_ldx_wdb .section}

-   不要修改 Linux 实例默认的 /etc/issue 文件内容。否则，根据实例创建的自定义镜像的系统发行版本无法被正确识别，使用该镜像创建的实例无法正常启动。
-   不要随意更改根目录所在分区下各个目录的权限，尤其是 `/etc`、`/sbin`、`/bin`、`/boot`、`/dev`、`/usr`和 `/lib` 等目录的权限。如果权限更改不当会导致系统出现异常。
-   不要重命名、删除或禁用 Linux下的 root 账号。
-   不要编译 Linux 系统的内核，或对内核进行任何其他操作。
-   如果您使用普通云盘，不建议使用 swap 分区。如果是高效云盘或 SSD 云盘，可以根据实际情况使用 swap 分区。
-   不要开启 NetWorkManager 服务。该服务会跟系统内部网络服务出现冲突，导致网络异常。

关于云服务器 ECS 的使用限制，请参考 [使用限制](cn.zh-CN/用户指南/使用限制.md#)。

