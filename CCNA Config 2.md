## Configurations

### Basic configs
`Switch(config)#hostname []
`SW2(config)#enable secret [password]
`SW2(config)#username [username] secret [password]
`SW2(config)#line console 0
Require login to access line
`SW2(config-line)#login local
`SW2(config-line)#exec-timeout 5
#### SSH
Continued from above
Create Domain name
`SW2(config)#ip domain-name cisco.com
Generate keys for ssh auth
`SW2(config)#crypto key generate rsa
`SW2(config)#line vty 0 15
`SW2(config-line)#login local
Require SSH connections
`SW2(config-line)#transport input ssh

### FTP
Need to configure user and passwd
`R2(config)#ip ftp username [username]
`R2(config)#ip ftp password [password]
Get file
`R2# copy ftp flash`
### TFTP
`copy tftp [location]
### Booting
Boot system from tftp or flash 
`R1(config)#boot system [flash|tftp] [filename]`
Saving config
`R1# copy run start`
`R1# write`
Restart
`R1#reload`
Delete something from flash
`R1#delete flash:[filename]`

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
Specify delay timer for LLDP
	`SW3(config)#lldp reinit [sec]`
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
### DHCP
Reserve a DHCP range
	`R2(config)#ip dhcp excluded-address [Lowest IP] [Highest IP]`
Configuring the pool
	`R2(config)#ip dhcp pool [Name]`
	Add a network to distribute
	`R2(dhcp-config)#network 192.168.1.0 255.255.255.0
	DNS server to config
	`R2(dhcp-config)#dns-server 8.8.8.8
	Domain name to config
	`R2(dhcp-config)#domain-name cisco.com
	Default gateway to config
	`R2(dhcp-config)#default-router 192.168.1.1
Configure router interface as DHCP client
	`R1(config)#int g0/0
	`R1(config-if)#ip address dhcp`
Configure router as a dhcp relay agent
	Configure on the interface closest to the DHCP server
	``R1(config)# int g0/1
	`R1(config-if)#ip helper-address [DHCP server address]`
### DHCP Snooping
Enable DHCP snooping globally
`SW1(config)#ip dhcp snooping 
Enable it on a vlan
`SW1(config)#ip dhcp snooping vlan 1
Apply on interface
`SW1(config)#int g0/2
`SW1(config-if)#ip dhcp snooping trust
Disable DHCP relay 
`SW1(config)#no ip dhcp snooping information option
Allow for auto-recovery
`SW1(config-if)#errdisable recovery cause dhcp-rate-limit`

### DAI
`SW1(config)#ip arp inspection vlan 1
`SW1(config)#interface g0/0
`SW1(config-if)#ip arp inspection trust
Sets the arp rate to 25 packets per 2 seconds, burst interval is optional, default is 1s
`SW1(config-if)#ip arp inspection limit rate [25] burst interval [2]
Reenabling interfaces
`shut/no shut`
`SW1(config)#errdisable recovery cause arp-inspection`
Checks the arp mesg fields, can utilize one, two or three in one cmd
`SW1(config)#ip arp inspection validate [dst-mac | ip |src-mac]
### SNMP
Create SNMP communities
	`R1(config)#snmp-server community [name] [ro(read only)|rw (read-write)]`
### Syslog Commands
Include timestamps
	`R1(config)#service timestamps log datetime msec`
Enable logging for VTY lines
	`R1#terminal monitor
Enable logging to buffer
	``R1(config)#logging buffered [size]`
### NAT
Configure interfaces as inside/outside
`R1(config)#int g0/1
`R1(config-if)#ip nat inside
`R1(config-if)#int g0/0
`R1(config-if)#ip nat outside
Mapping static NAT
`R1(config)#ip nat inside source static [local ip] [global ip]`
Clearing dynamic NAT translations
`R1#clear ip nat translation *`
Dynamic NAT
	Configure interfaces
	`R1(config)#int g0/0
	`R1(config-if)#ip nat outs
	`R1(config-if)#int g0/1
	`R1(config-if)#ip nat inside
	`R1(config-if)#exit
	Create access-list so router knows what to perimit
	`R1(config)#access-list 1 permit 172.16.0.0 0.0.0.255
	Create the Nat Pool and define the address range
	`R1(config)#ip nat pool Pool1 100.0.0.1 100.0.0.2 netmask 255.255.255.0
	Configure router to use the pool range as the source addr
	`R1(config)#ip nat inside source list 1 pool Pool1
PAT
	Uses PAT and uses interface address for inside global
	`R1(config)#ip nat inside source list 1 interface g0/0 overload
### Voice VLANs
Creating Vlans and assigning Voice VLAN
	`SW1(config)#int ra g1/0/2-3
	`SW1(config-if-range)#swi
	`SW1(config-if-range)#switchport mode access
	`SW1(config-if-range)#switchport access vlan 10
	``% Access VLAN does not exist. Creating vlan 10
	`SW1(config-if-range)#switchport voice vlan 20
	``% Voice VLAN does not exist. Creating vlan 20
Configure ROAS
	`SW1(config-if)#switchport trunk encapsulation dot1q`
	`SW1(config-if)#switchport mode trunk`
	Allow only data and voice vlan
	`SW1(config-if)#switchport trunk allowed vlan 10,20`
	Sub interface configuration
	`R1(config-if)#int f0/0.10
	`R1(config-subif)#ip add 192.168.10.1 255.255.255.0`
	`R1(config-subif)#encapsulation dot1q 10
### QoS
Identify what type of traffic you want to apply QoS
`R1(config)#class-map [Class map name]`
`R1(config-cmap)#match protocol [https]
Specify what kind of treatment you want to give to each type of traffic
`R1(config)#policy-map [policyname]
Apply the previously created classmapto the policy
`R1(config-pmap)#class [class map]
Tell it what to do with the traffic
This will mark any HTTPS paccket with a dscp value of 31
`R1(config-pmap-c)#set ip dscp [AF31]
Specify how much of bandwidth to reserve for it
`R1(config-pmap-c)#priority percent 10
If it is not a priority queue
`R1(config-pmap-c)#bandwidth percent 10
Apply to the interface
`R1(config)#int g0/0/0
`R1(config-if)#service-policy output [policy name]


### Port Security
`SW1(config)#int ra f0/1-3
Set how long the MAC addresses stay on
`SW1(config-if-range)#switchport port-security aging time 60
Portsecurity can only be enabled on access or trunk port
`SW1(config-if-range)#switchport mode access
Enable port security
`SW1(config-if-range)#switchport port-security
Set the violation mode
`SW1(config-if-range)#switchport port-security violation [shutdown|restrict|protect]
Set maximum mac addresses valid for this port
`SW1(config-if-range)#switchport port-security maximum [#]
Set so port security dynamically learns mac addr
`SW1(config-if-range)#switchport port-security mac-address sticky

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
### DNS
Configure DNS server on router
	`R1(config)#ip name-server [dnssvr IP]
Associate names with host IP
	`R1(config)#ip host [name] [host ip]`
### NAT

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
Enable logging to syslog server
	``R1(config)#logging [ip addr]`
Set severity of syslog msgs sent to server
	``R1(config)#logging trap [severity]`
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
Show DNS
	`show hosts`
Show logging
	`show debugging`
`show flash`
Shows NAT translations aka src-dest
`R1#show ip nat translations
`R1#show ip nat statistics`
`SW1#show ip arp inspection interfaces`
``SW1#show ip arp inspection`