# Fixing error: PXE-E51

## Error Description

PXE-E51: No DHCP or proxyDHCP offers were received.

Screenshots:

1.
<a href="https://ibb.co/eOUNoa"><img src="https://thumb.ibb.co/eOUNoa/IMG_20170913_151319.jpg" alt="IMG 20170913 151319" border="0" /></a>

2.
<a href="https://ibb.co/dH8tuF"><img src="https://thumb.ibb.co/dH8tuF/IMG_20170913_151416.jpg" alt="IMG 20170913 151416" border="0" /></a>

3.
<a href="https://ibb.co/ng9cMv"><img src="https://thumb.ibb.co/ng9cMv/IMG_20170913_151419.jpg" alt="IMG 20170913 151419" border="0" /></a>

## Google materials

1. [PXE-E51 "No DHCP or DHCP Proxy Offers received" error](https://community.saas.hpe.com/t5/ProLiant-Deployment-and/PXE-E51-quot-No-DHCP-or-DHCP-Proxy-Offers-received-quot-error/td-p/835177)
1. [PXE E51 No DHCP or proxy DHCP offers were received](https://support.symantec.com/en_US/article.TECH12323.html)
1. [What is PXE - Preboot Execution Environment (PXE)](http://searchnetworking.techtarget.com/definition/Preboot-Execution-Environment)

## Actions

### 2017-09-20

Change Embedded Gb NIC1 setting from `Enable with PXE` to `Enable`. Doesn't work.

Find there is some problem with Port A:

Normal:<br>
<a href="https://ibb.co/eQqCDk"><img src="https://thumb.ibb.co/eQqCDk/IMG_20170920_163438.jpg" alt="IMG 20170920 163438" border="0" /></a>

Down server:<br>
<a href="https://ibb.co/g4b8m5"><img src="https://thumb.ibb.co/g4b8m5/IMG_20170920_162951.jpg" alt="IMG 20170920 162951" border="0" /></a>

- [x] Try to replug hardware.

### 2017-09-29

Problem: One hadrware broken.<br>
Replace the broken one with a new 500G hardware.

Problem: No system
Install XenServer 6.1 and configure static network.<br>
In local command line, configure DNS server.<br>
Manage this server with XenCenter.

- [x] Install a new virtual machine. 

### 2017-10-10

Problem: can't remove vm-disk after removing vm

Attemption: 
- xe vdi-destory
- ...
- xe vm-disk-remove
- xe vm-destory
- xe vm-shutdown uuid=... `You attempted an operation which involves a host which could not be contacted.`

Solution: In XenCenter, remove it from Pool and then add it back.

### 2017-10-23

Finished:
- [x] NTP time sync, ntpd in Cloudera-Manager
- [x] Modify hostname of Cloudera-Host-5
- [x] Modify `/etc/hosts`
- [x] Install xs-tools
- [x] Configure static IP of Cloudera-Host-5

- Problem: 主机问题 - `代理状态`
  - Detail: `该主机与Cloudera Manager 断开联系的时间过长。不能确定主机的 Cloudera Manager 代理软件版本`
  - Solution: Network problem. Shutdown the firewall of Cloudera-Manager by command `service iptables stop`.
  - (Firewall was started when configure ntp server.)

TODO:
- [x] Install CDH4 in Cloudera-Host-5
  - Current Role
    - RegionServer
    - DataNode
    - SecondaryNameNode
    - TaskTracker
    
### 2017-10-27

Install CDH4 in Cloudera-Host-5.

Using local yum repo to install CDH, `自定义存储库`.
Key commands:
- `service iptables stop`
- `service httpd start` in Cloudera Manager

TODO:
- [ ] Give roles to Cloudera-Host-5
- [ ] fix error: `HDFS service not configured for High Availability must have a SecondaryNameNode`

### 2017-10-30

Problem: `Host Monitor 未运行`

Solution: Seems fixed by restart `Cloudera Management Service` and stop iptables in service provider host.

- [X] Apply access from outer network.
