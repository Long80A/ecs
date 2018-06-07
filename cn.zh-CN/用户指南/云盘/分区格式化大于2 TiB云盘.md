# 分区格式化大于2 TiB云盘 {#concept_i15_qpc_ydb .concept}

如果您要分区格式化一块大于2 TiB的作数据盘用的云盘（本文统一称为 **大容量数据盘**，小于2 TiB的数据盘统称为 **小容量数据盘**），您必须采用GPT分区形式。本文档描述了如何在不同的操作系统里分区格式化一块大容量数据盘。

**说明：** 如果您要分区格式化一块小于2 TiB的数据盘，请参见 [Linux 格式化和挂载数据盘](../cn.zh-CN/个人版快速入门/步骤 4：格式化数据盘/Linux 格式化和挂载数据盘.md#) 和 [Windows 格式化数据盘](../cn.zh-CN/个人版快速入门/步骤 4：格式化数据盘/Windows 格式化数据盘.md#)。

## 注意事项 {#section_xmm_psc_ydb .section}

分区格式化大容量数据盘时，需要注意以下事项：

-   大容量数据盘支持的分区工具和文件系统如下表所示。

    |操作系统|分区工具|文件系统|
    |:---|:---|:---|
    |Linux|`parted`|ext4或xfs|
    |Windows|**磁盘管理**|NTFS|

-   **不建议使用小容量数据盘的快照创建大容量数据盘**

    理论上，您可以使用一块小容量数据盘的快照创建一个大容量数据盘，但是我们不建议您这么做，而是创建空的大容量数据盘，或者使用大容量数据盘的快照创建大容量数据盘。原因如下：

    -   使用小容量数据盘的快照创建大容量数据盘时，系统只完成块设备级的磁盘扩容，并没有实现分区格式和文件系统的自动转换。
    -   如果小容量数据盘快照中使用的是MBR分区格式，以上提到的分区工具（Linux上的 `parted` 和Windows上的 **磁盘管理**）都不能在保留数据的前提下将分区形式从MBR转换为GPT。所以，即使您使用小容量数据盘的快照创建了大容量数据盘，在分区格式化时，您都需要删除原有数据，再按照GPT格式分区。如果您已经用小容量数据盘的快照创建了大容量数据盘，请参见 [Windows里分区格式化由小容量数据盘的快照创建的大容量数据盘](#Windows2012Snapshot) 。

        **说明：** 如果小容量数据盘快照本身就是GPT分区格式，或者您另有强大的分区工具，则不在此列。您可以根据自身情况来选择。

-   **数据盘快照的影响**

    大容量数据盘的数据量很大，但是创建快照的速度和小容量数据盘是一样的，所以每天创建快照的时间会与数据量成比例增长。创建快照的速度和数据的增量成正比，脏数据越多，创建快照耗时越久。


## Windows里分区格式化空的大容量数据盘 {#section_enm_psc_ydb .section}

这部分以Windows Server 2008 R2 64位系统为例，说明如何在Windows实例中分区格式化一块大容量数据盘。假设需要处理的数据盘是一个4 TiB的空盘。

**前提条件**

数据盘已经挂载到实例上。具体操作，请参见 [挂载云盘](cn.zh-CN/用户指南/云盘/挂载云盘.md#)。

**操作步骤**

按以下步骤分区格式化一块大容量数据盘：

1.  [远程连接Windows实例](cn.zh-CN/用户指南/连接实例/连接实例概述.md#)。
2.  在任务栏里，单击 ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4424_zh-CN.png) 图标。
3.  在 **服务器管理器** 的左侧导航栏里，选择 **存储** \> **磁盘管理**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4425_zh-CN.png)

4.  找到需要分区格式化的磁盘（本示例中为 **磁盘 4**）。磁盘状态显示为 **脱机**。
5.  右击磁盘 4周边空白处，单击 **联机**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/34377/cn_zh/1514438661986/Win2008_%E8%81%94%E6%9C%BA.png)

    联机后，磁盘 4的状态显示为 **没有初始化**。

6.  右键单击磁盘 4周边的空白区，在弹出菜单中，选择 **初始化磁盘**。
7.  在 初始化磁盘 对话框里，选择 **磁盘 4**，并选择磁盘分区形式为 **GPT**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4427_zh-CN.png)

8.  在 磁盘管理 窗口，右键单击磁盘 4的 **未分配** 区域，选择 **新建简单卷**，创建一个4 TiB的NTFS格式的卷。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4428_zh-CN.png)

9.  在 新建简单卷向导 中，完成以下操作：
    1.  单击 **下一步**。
    2.  指定卷大小：指定简单卷大小。如果您只要创建一个主区，使用默认值。单击 **下一步**。您也可以把 **磁盘 4** 分成多个分区来使用。

        **说明：** NTFS卷上的最大尺寸，理论上，NTFS的最大卷包含264-1个簇。实际上，WinXP Pro中，NTFS卷的最大限制是232-1个簇。举例来说，如果是64 KiB的簇，那NTFS卷的最大尺寸就是约256 TiB 。如果选择4 KiB的簇，那NTFS卷的最大尺寸就是约16 TiB。NTFS会根据磁盘的容量来自动选择簇的大小。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4429_zh-CN.png)

    3.  分配驱动器号和路径：选择一个驱动器号（即盘符），如本示例中选择G。单击 **下一步**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4430_zh-CN.png)

    4.  格式化分区：选择格式化设置，包括文件系统、分配单元大小和卷标，确认是否 **执行快速格式化** 和 **启用文件和文件夹压缩**。这里仅选择 **执行快速格式化**。单击 **下一步**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4431_zh-CN.png)

    5.  开始创建新简单卷。当向导对话框里显示已经完成新简单卷的创建时，单击 **完成**，关闭 新建简单卷向导。

格式化分区完成后，**磁盘管理** 中 **磁盘 4** 的状态如下截图所示。

![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/34377/cn_zh/1514438976977/Win2008_%E6%96%B0%E5%BB%BA%E7%AE%80%E5%8D%95%E5%8D%B7_%E5%AE%8C%E6%88%90.png)

## Windows里分区格式化由小容量数据盘的快照创建的大容量数据盘 {#Windows2012Snapshot .section}

如果您使用一个小容量数据盘的快照创建了一块大容量数据盘，您需要先将数据盘的分区形式从MBR转为GPT，再格式化数据盘，原来快照的数据将无法保存，所以我们不建议您使用小容量数据盘的快照创建大容量数据盘。

如果您确实创建了这样的大容量数据盘，按以下步骤分区格式化这块数据盘。本示例中的操作系统是Windows Server 2012 R2 64位，假设需要处理的数据盘容量为3 TiB。

**前提条件**

数据盘已经 [挂载](https://help.aliyun.com/document_detail/25446.html) 到实例上。

**操作步骤**

按以下步骤分区格式化一块大容量数据盘：

1.  [远程连接Windows实例](cn.zh-CN/用户指南/连接实例/连接实例概述.md#)。
2.  在Windows Server桌面，右键单击 **开始** 图标，选择 **磁盘管理**。

    未格式化分区的数据盘（如本示例中的磁盘 2）处于 **脱机** 状态。

3.  右键单击磁盘 2周边的空白区，在弹出菜单中，选择 **脱机**。
4.  右键单击一个简单卷，在弹出菜单中，选择 **删除卷**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4433_zh-CN.png)

5.  右键单击磁盘 2周边的空白区，在弹出菜单中，选择 **转换成GPT磁盘**。
6.  在 磁盘管理 窗口，右键单击磁盘 2的 **未分配** 区域，选择 **新建简单卷**,创建一个3 TiB的NTFS格式的卷。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4434_zh-CN.png)

7.  在 新建简单卷向导 中，完成以下操作：
    1.  单击 **下一步**。
    2.  指定卷大小：指定简单卷大小。如果您只要创建一个主区，使用默认值。单击 **下一步**。您也可以把 **磁盘 2** 分成多个分区来使用。

        **说明：** NTFS卷上的最大尺寸，理论上，NTFS的最大卷包含264-1个簇。实际上，WinXP Pro中，NTFS卷的最大限制是232-1个簇。举例来说，如果是64 KiB的簇，那NTFS卷的最大尺寸就是约256 TiB。如果选择4 KiB的簇，那NTFS卷的最大尺寸就是约16 TiB。NTFS会根据磁盘的容量来自动选择簇的大小。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4435_zh-CN.png)

    3.  分配驱动器号和路径：选择一个驱动器号（即盘符），如本示例中选择E。单击 **下一步**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4436_zh-CN.png)

    4.  格式化分区：选择格式化设置，包括文件系统、分配单元大小和卷标，确认是否 **执行快速格式化** 和 **启用文件和文件夹压缩**。这里仅选择 **执行快速格式化**。单击 **下一步**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4437_zh-CN.png)

    5.  开始创建新简单卷。当向导对话框里显示已经完成新简单卷的创建时，单击 **完成**，关闭 新建简单卷向导。

格式化分区完成后，**磁盘管理** 中 **磁盘 4** 的状态如下截图所示。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/6088_zh-CN.png)

## Linux里分区格式化大容量数据盘 {#section_a4m_psc_ydb .section}

对于Linux实例上挂载的大容量数据盘，采用GPT分区形式。Linux系统里，大容量数据盘一般采用xfs或者ext4文件系统。

这部分以CentOS 7.4 64位系统为例，说明如何在Linux实例上使用 **parted** 和 **e2fsprogs** 工具分区并格式化一个大容量数据盘。假设需要处理的数据盘是一个新建的3 TiB的空盘，设备名为 /dev/vdd。

**前提条件**

您的Linux实例上已经安装了 **parted**。如果未安装，运行命令 `yum install -y parted`。

您的Linux实例上已经安装了 **e2fsprogs**。如果未安装，运行命令 `yum install -y e2fsprogs`。

数据盘已经挂载到实例上。详细信息，请参见 [挂载云盘](cn.zh-CN/用户指南/云盘/挂载云盘.md#)。

**操作步骤**

按以下步骤分区格式化大容量数据盘，并挂载文件系统：

1.  运行命令 `fdisk -l` 查看数据盘是否存在。返回结果应包括如下所示的信息。如果没有，表示您未挂载数据盘。

    ```
    
    Disk /dev/vdd: 3221.2 GB, 3221225472000 bytes, 6291456000 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    ```

2.  运行命令 `parted /dev/vdd` 开始分区：
    1.  运行命令 `mklabel gpt`，将MBR分区形式转为GPT分区形式。
    2.  运行命令 `mkpart primary ext4 <StartSector> <EndSector>`，划分一个采用ext4文件系统的主分区，并设置分区的开始位置和结束位置。如果一个数据盘只分一个分区，则运行命令 `mkpart primary ext4 0 -1`。

        **说明：** 您也可以使用xfs文件系统。

    3.  运行命令 `print`，查看分区表。

        ```
        
        (parted) mkpart primary ext4 0 -1
        Warning: The resulting partition is not properly aligned for best performance.
        Ignore/Cancel? ignore
        (parted) print
        Model: Virtio Block Device (virtblk)
        Disk /dev/vdd: 3221GB
        Sector size (logical/physical): 512B/512B
        Partition Table: gpt
        Disk Flags:
        Number Start End Size File system Name Flags
        1 17.4kB 3221GB 3221GB primary
        ```

    4.  运行命令 `quit`，退出 **parted** 操作。
3.  运行命令 `partprobe`，使系统重读分区表。
4.  运行以下命令，创建一个ext4文件系统，并使 /dev/vdd1 分区使用ext4。

    ```
    mke2fs -O 64bit,has_journal,extents,huge_file,flex_bg,uninit_bg,dir_nlink,extra_isize /dev/vdd1
    ```

    **说明：** 

    -   如果您要关闭ext4文件系统的lazy init功能，避免该功能对数据盘I/O性能的影响，可以参考 [附录2：关闭lazy init功能](#LazyInit)。
    -   如果数据盘的容量为16 TiB，需要使用指定版本的e2fsprogs工具包格式化，请参考 [附录1：升级e2fsprogs工具包](#e2fsprogs)。
    -   如果您要创建一个xfs文件系统，运行命令 `mkfs -t xfs /dev/vdd1`。
5.  运行命令 `mkdir /test`，创建一个名为 /test 的挂载点。
6.  运行命令 `mount /dev/vdd1 /test`，将分区 /dev/vdd1 挂载到 /test。
7.  运行命令 `df -h`，查看目前磁盘空间和使用情况。

    如果返回结果里出现新建文件系统的信息，说明挂载成功，可以使用新的文件系统了。挂载完成后，不需要重启实例即可开始使用新的文件系统。

    ```
    
    [root@izXXXXz ~]# df -h
    Filesystem Size Used Avail Use% Mounted on
    /dev/vda1 40G 6.4G 31G 18% /
    devtmpfs 487M 0 487M 0% /dev
    tmpfs 497M 0 497M 0% /dev/shm
    tmpfs 497M 364K 496M 1% /run
    tmpfs 497M 0 497M 0% /sys/fs/cgroup
    tmpfs 100M 0 100M 0% /run/user/0
    /dev/vdd1 2.9T 89M 2.8T 1% /test
    ```

8.  （可选）向 /etc/fstab 写入新分区信息，启动开机自动挂载分区。
    1.  （可选）运行命令 `cp /etc/fstab /etc/fstab.bak`，备份 etc/fstab。
    2.  运行命令 `echo /dev/vdd1 /test ext4 defaults 0 0 >> /etc/fstab`，向 /etc/fstab 里写入新分区信息。
    3.  运行命令 `cat /etc/fstab`，查看 /etc/fstab 的信息。

        如果返回结果里出现了写入的新分区信息，说明写入成功。


至此，您已经成功分区并格式化了一个3 TiB数据盘。

**附录1：升级e2fsprogs工具包**

如果数据盘容量为16 TiB，您需要使用1.42及以上版本的e2fsprogs工具包完成ext4文件系统格式化。如果e2fsprogs版本太低（比如：e2fsprogs 1.41.11等），会出现如下错误信息：

```

mkfs.ext4: Size of device /dev/vdd too big to be expressed in 32 bits using a blocksize of 4096.

```

您需要按以下方式安装高版本的e2fsprogs，如本示例中使用的1.42.8：

1.  运行命令 `rpm -qa | grep e2fsprogs` 检查e2fsprogs当前的版本。![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/4439_zh-CN.png)

    如果当前版本低于1.42，按以下步骤安装软件。

2.  运行以下命令下载 1.42.8 版本的e2fsprogs。您可以在 [e2fsprogs](https://www.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/v1.42.8/?spm=a2c4g.11186623.2.14.Pb5baW) 找到最新的软件包。

    ```
    
    wget https://www.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/v1.42.8/e2fsprogs-1.42.8.tar.gz
    
    ```

3.  依次运行以下命令，编译高版本的工具。

    ```
    
    tar xvzf e2fsprogs-1.42.8.tar.gz
    cd e2fsprogs-1.42.8
    ./configure
    make
    make install
    ```

4.  运行命令 `rpm -qa | grep e2fsprogs` 检查是否成功安装高版本软件。

**附录2：关闭lazy init功能**

ext4文件系统的lazy init功能，默认开启。该功能开启时，系统后台会发起一个线程持续地初始化ext4文件系统的metadata，从而延迟metadata初始化。所以在刚格式化数据盘的一段时间内IOPS会受到影响，比如，数据盘的IOPS性能测试的数据会明显偏低。

如果要在格式化以后马上测试数据盘性能，您需要运行以下命令在格式化文件系统时关闭lazy\_init功能。

```
mke2fs -O 64bit,has_journal,extents,huge_file,flex_bg,uninit_bg,dir_nlink,extra_isize -E lazy_itable_init=0,lazy_journal_init=0   /dev/vdd1
```

关闭lazy init功能后，格式化的时间会大幅度地延长，格式化32 TiB的数据盘可能需要10-30分钟。

请您根据自身的需要选择是否使用lazy init功能。

