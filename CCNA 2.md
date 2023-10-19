### NGFW/NGIPS
Inline protection
one single appliance or product
Same basic stateful packet inspection
contributes to awareness in cisco talus
Combined into Cisco Firepower management Center
### Cisco DNA Center

### QoS

### OSPF

### SDN
Software Defined Networking
Traditional : Controller Based
Silo : global
Distributed : centralized
physical : logical
Static : programmable
single-task : orchestration
local : unified
device : network
trial and error : assurance
point-in-time : real-time

Traditional : Automation
CLI : Scripting
manual : dynamic
slower : faster
error-prone : assurance
deploy : test and deploy
not scalable : scalable
physical server : physical + virtual machine

Previously, traditional networking was based on a silo view where each network device was statically managed separately. There is much more accomplished, in less time and at a lower cost while minimizing network outages. Having a centralized, real-time network view is fundamental to automation. 

Create unified policies for device configuration, security, wireless and systems management

Cisco switches support either manually configured or automatic poe nego and either CDP or LLDP can configure

routes select the longest match aka higher subnet number

DNS nameserver keywords

Network overlay
The switching fabric is a physical underlay designed for high-speed transport of east-west traffic within a data center.
There is a fabric overlay that is built on top of (or over) an underlay. An overlay is comprised of multiple virtual interconnects between endpoints.
Network overlays are simply virtual interconnects aka encapsulation protocols
CAPWAP
IPsec
VXLAN

Cisco devices can be configured and managed from a web browser for easier management. The following global commands enable an encrypted session to a device with local authentication. There is an option to authenticate users with AAA server as well.

**ip http secure-server**

**ip http authentication local**

default QoS port state is untrusted
![[2021-12-30_15-02-09-937ce4d913819135252614e55ffcd74e.png]]

Show operational status
	Sho ip int brief
Shows subnet mast and operational status
	sho protocols
	show int

![[2021-12-30_15-22-15-7653a9fa6d976deffa3a0ff8e3649b9e.png]]

![[2021-12-30_15-24-10-328a119ac8271f69bf1a8418049dead2.png]]