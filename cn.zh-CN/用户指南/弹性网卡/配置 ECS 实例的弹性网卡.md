# 配置 ECS 实例的弹性网卡 {#concept_lyl_2kk_zdb .concept}

如果您的实例使用以下几种镜像，您不需要手工配置弹性网卡（ENI）：

-   CentOS 7.3 64 位
-   CentOS 6.8 64 位
-   Windows Server 2016 数据中心版 64 位
-   Windows Server 2012 R2 数据中心版 64 位

如果您的实例使用的不是这几种镜像，但是又希望在实例上附加弹性网卡，您需要手工配置弹性网卡。本文以 CentOS 7.2 64 位系统为例介绍了如何配置附加在 Linux 实例上的弹性网卡，使其能被您的系统识别。

## 前提条件 {#section_oyn_hkk_zdb .section}

您已经将弹性网卡附加到 ECS 实例上。

## 操作步骤 {#section_pyn_hkk_zdb .section}

您应该按以下步骤配置弹性网卡：

1.  使用[DescribeNetworkInterfaces](../DNA0011860945/ZH-CN_TP_9954.dita)接口或者在 ECS 控制台上获取每个网卡的主私有 IP 地址、掩码地址、默认路由和 MAC 地址。以下为 ECS 控制台上的操作步骤：
    1.  登录 [ECS管理控制台](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home)。
    2.  找到每个网卡的主私有 IP 地址、掩码地址、默认路由和 MAC 地址。示例如下：

        ```
        
        eth1 10.0.0.20/24 10.0.0.253 00:16:3e:12:e7:27
        eth2 10.0.0.21/24 10.0.0.253 00:16:3e:12:16:ec
        ```

2.  [远程登录 ECS 实例](../cn.zh-CN/个人版快速入门/步骤 3：远程连接ECS实例.md)。
3.  生成网卡配置文件：运行 `cat /etc/sysconfig/network-scripts/ifcfg-[网卡名]`。

    **说明：** 

    -   需要注意网卡名和 MAC 地址的对应关系。
    -   默认路由需要配置为 `DEFROUTE=no`。其它的发行版与此类似，注意避免配置网卡后导致 `ifup` 改变系统当前活动的默认路由。
    -   示例如下：

        ```
        
        # cat /etc/sysconfig/network-scripts/ifcfg-eth1 
        DEVICE=eth1
        BOOTPROTO=dhcp
        ONBOOT=yes
        TYPE=Ethernet
        USERCTL=yes
        PEERDNS=no
        IPV6INIT=no
        PERSISTENT_DHCLIENT=yes
        HWADDR=00:16:3e:12:e7:27
        DEFROUTE=no
        ```

4.  启动弹性网卡：
    1.  运行命令 `ifup [网卡名]` 启动 dhclient 进程，并发起 DHCP 请求。示例如下：

        ```
        
        # ifup eth1
        # ifup eth2
        ```

    2.  请求返回后，运行命令 `ip a` 检查网卡 IP 分配情况，并注意是否与控制台上提供的网卡信息匹配。示例如下：

        ```
        
        # ip a
        1: lo:  mtu 65536 qdisc noqueue state UNKNOWN qlen 1
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
        2: eth0:  mtu 1500 qdisc pfifo_fast state UP qlen 1000
        link/ether 00:16:3e:0e:16:21 brd ff:ff:ff:ff:ff:ff
        inet 10.0.0.19/24 brd 10.0.0.255 scope global dynamic eth0
        valid_lft 31506157sec preferred_lft 31506157sec
        3: eth1:  mtu 1500 qdisc pfifo_fast state UP qlen 1000
        link/ether 00:16:3e:12:e7:27 brd ff:ff:ff:ff:ff:ff
        inet 10.0.0.20/24 brd 10.0.0.255 scope global dynamic eth1
        valid_lft 31525994sec preferred_lft 31525994sec
        4: eth2:  mtu 1500 qdisc pfifo_fast state UP qlen 1000
        link/ether 00:16:3e:12:16:ec brd ff:ff:ff:ff:ff:ff
        inet 10.0.0.21/24 brd 10.0.0.255 scope global dynamic eth2
        valid_lft 31526009sec preferred_lft 31526009sec
        ```

5.  按需要规划路由表里每块网卡默认路由 metric 值。在本示例中，假设要将 eth1 和 eth2 的 metric 值配置如下。

    ```
    
    eth1: gw: 10.0.0.253 metric: 1001
    eth2: gw: 10.0.0.253 metric: 1002
    ```

    1.  运行如下命令规划 metric 值。

        ```
        
        # ip -4 route add default via 10.0.0.253 dev eth1 metric 1001
        # ip -4 route add default via 10.0.0.253 dev eth2 metric 1002
        ```

    2.  运行命令 `route -n`检查配置是否成功。

        ```
        
        # route -n
        Kernel IP routing table
        Destination Gateway Genmask Flags Metric Ref Use Iface
        0.0.0.0 10.0.0.253 0.0.0.0 UG 0 0 0 eth0
        0.0.0.0 10.0.0.253 0.0.0.0 UG 1001 0 0 eth1
        0.0.0.0 10.0.0.253 0.0.0.0 UG 1002 0 0 eth2
        10.0.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
        10.0.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
        10.0.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth2
        169.254.0.0 0.0.0.0 255.255.0.0 U 1002 0 0 eth0
        169.254.0.0 0.0.0.0 255.255.0.0 U 1003 0 0 eth1
        169.254.0.0 0.0.0.0 255.255.0.0 U 1004 0 0 eth2
        ```

6.  创建路由表：

    **说明：** 建议您将路由表名称和规划的 metric 值保持一致。

    1.  运行以下命令创建路由表。

        ```
        
        # ip -4 route add default via 10.0.0.253 dev eth1 table 1001
        # ip -4 route add default via 10.0.0.253 dev eth2 table 1002
        ```

    2.  运行以下命令检查路由表是否创建成功。

        ```
        
        # ip route list table 1001
        default via 10.0.0.253 dev eth1
        # ip route list table 1002
        default via 10.0.0.253 dev eth2
        ```

7.  配置策略路由。
    1.  运行以下命令创建策略路由。

        ```
        
        # ip -4 rule add from 10.0.0.20 lookup 1001
        # ip -4 rule add from 10.0.0.21 lookup 1002
        ```

    2.  运行命令 `ip rule list` 查看路由规则。

        ```
        
        # ip rule list
        0: from all lookup local
        32764: from 10.0.0.21 lookup 1002
        32765: from 10.0.0.20 lookup 1001
        32766: from all lookup main
        32767: from all lookup default
        ```


至此，您已经完成了弹性网卡配置。

