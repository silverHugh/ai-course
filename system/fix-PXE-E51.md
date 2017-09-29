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

- [ ] Install a new virtual machine. 
