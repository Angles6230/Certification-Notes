## Configurations
### CDP
Enable CDP globally
	`SW1(config)# cdp run`
Enable/Disable CDP on interfaces
	`SW1(config-if)# cdp enable`
### LLDP
Enable LLDP globally
	`SW1(config)# lldp run`
Enable transmit and receive on interface
	`SW3(config)#int g0/1
	`SW3(config-if)#lldp transmit
	`SW3(config-if)#lldp recieve`
### NTP
Configuring the time
`R1# clock set [time]`
Configuring NTP
	`R1(config)#ntp server 1.1.1.1`
Configuring NTP master
	`R1(config)#NTP master [stratum]`
NTP Authentication
	enable NTP authentication
	`R1(config)#ntp authenticate
	Create NTP key
	`R1(config)#ntp authentication-key 1 md5 cisco
	Assign NTP key as trusted
	`R1(config)#ntp trusted-key 1`
	Config R2 to use R1 as trusted NTP and use NTP key to authenticate R1
	`R2(config)#ntp authentication-key 1 md5 cisco
	`R2(config)#ntp trusted-key 1
	`R2(config)#ntp server 192.168.12.1(R1) key 1
Configure NTP to update hardware calendar
	`R2(config)#ntp update-calendar`
### Configuring STP
Display STP
	`Show spanning tree`
Configure STP
	`SW1(config)#spanning-tree vlan [#] [root (primary | secondary) | prioirty (0-61440)] 
Configure cost for interface
	`SW1(config-if)# spanning-tree vlan [#] cost [#]`
Configure priority for interface 
	`SW1(config-if)# spanning-tree vlan [#] priority [#]
Configuring Portfast/edge port
	`SW1(config-if)# spanning-tree portfast [enable|disable|trunk]
Configuring bdpuguard
	`SW1(config-if)# spanning-tree bpduguard [enable|disable]
Configuring RSTP type
	`SW1(config-if-range)#spanning-tree link-type point-to-point`
### Etherchannels
Configure Etherchannel
	`ASW1(config-if-range)#channel-group [#] mode 
		``(active | auto | desirable | on | passive)`
Configure etherchannel loadbalancing
	`ASW1(config)#port-channel load-balance [options below]
		`(dst-ip) Dst IP Addr 
		`(dst-mac) Dst Mac Addr
		`(src-dst-ip) Src XOR Dst IP Addr
		`(src-dst-mac) Src XOR Dst Mac Addr
		`(src-ip) Src IP Addr
		`(src-mac) Src Mac Addr


## Routing
Enable IP routing on layer 3 switch
	`DSW1(config)# ip routing`
Create a route
	`ip route [destination network] [subnet mask] [exit interface | next hop IP addr]`
Advertise default route
	`R1(config-router)#default-information originate`
Create default route
	`R1(config)#ip route 0.0.0.0 0.0.0.0 [next hop]`
Enable IPv6 routing
	`R1(config)#ipv6 unicast-routing`
Enable IPv6 on interfaces
	`R2(config-if)#ipv6 enable`
Adding IPv6 EUI-64(IPv6 MAC) onto route
	`R1(config-if)#ipv6 addr 2001:db8::/64 eui-64`
IPv6 Routing
	`R2(config)#ipv6 route [destination] [interface] [address] (interface-linklocal) [ad]`
### EIGRP
Enable EIGRP
	`R4(config)#router eigrp [as #]
Enable eigrp on all interfaces
	`R4(config-router)# network 0.0.0.0 255.255.255.255`
Add a network
	`R4(config-router)# network [ip address] [wildcard mask]
Disable autosum
	`R4(config-router)# no auto-summary`
Configure passive interface
	`R4(config-router)# passive-interface [interface]`

### OSPF
`R4(config-if)#router ospf [Process ID]
Add network to ospf
`R4(config-router)#network 0.0.0.0 255.255.255.255 area [area number]
Set reference bandwidth
`auto-cost reference-bandwidth [number]`
View LSB
`show ip ospf database`
View neighbors
`show ip ospf neighbors`
view interface
`show ip ospf interface`
Configure dead/hello interval
``R4(config-router)# ip ospf [hello|dead]-interval [time]`

### HSRP
Enable HSRPv2
	`R1(config-if)#standby version 2`
HSRP Configuration
	`R1(config-if)#standby [group number] `
		`ip` - configures virtual ip addr
		`ipv6` - ipv6 addr
		`preempt` - enables preemption - take back over if it goes down
		`priority` - 
		`timers` - hello/hold timers
		`track` - priority tracking

## Access List
### Standard ACLs
Named ACLs
	`R2(config)#ip access-list standard [name]
	`R2(config-std-nacl)#permit/deny 172.16.2.1`
	Apply the ACLs
	`R2(config)#int g0/0`
	`R2(config-if)#ip access-group [Name] [in/out]`
Numbered ACLs
	`R1(config)#access-list 1 [deny | permit] {Addr|any|host addr} [0.0.0.255]
	`R1(config)#access-list 1 permit any
	Apply the ACLs
	`R1(config)#int g0/1
	`R1(config-if)#ip access-group 1 out`
### Extended ACLs
Create
	`R1(config)#ip access-list extended [100-199 or word]`
Configure
	`R1(config-ext-nacl)# [permit|deny] [protocol] [source] [destination] [port]`
Permit 
	``R1(config-ext-nacl)# permit ip any any`
Apply
	`R1(config-ext-nacl)#int g0/0`
	`R1(config-if)#ip access-group 100 in`

# Show commands
`show etherchannel summary
show etherchannel load balancing
	`show etherchannel load-balance
`show spanning-tree
`show interfaces trunk
`show ip route (eigrp|ospf|connected etc)
Show running ip protocols
`show ip protocols`
`show ip [eigrp|ospf] neighbors`
`show ip interface brief`
Displays all EIGRP advertised routes
`show ip eigrp topology`
Display HSRP
`show standby`
See ACLS
`Show access-lists`
`show cdp neighbors`
See everything
`Show cdp neighbors detail`
`show cdp interface [int]`
Show NTP
`show ntp associations`