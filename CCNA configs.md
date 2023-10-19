Port  Spanning
	`Conf t
	`monitor session *number* source interface *interface*
	`monitor session *number* destination interface *interface*
Show session
	`sho monitor session *number*
Change name
	`hostname *name*
Save
	`copy running-config startup-config
Shows spanning tree
	show spanning-tree
Change spanning tree mode
	spanning-tree mode
view arp table
	arp -a - windows/linux/macos
	show arp - cisco ios
mac addr table
	show mac address-table 
clear mac addr table
	clear mac address-table dynamic address MAC address*
	clear mac address-table dynamic interface *interface*
Show ip interfaces
	show ip interface brief
show interfaces
	show interfaces *interface*
show interface status
	Show interface status
change speed of int
	int f0/1
	speed *number*
	duplex *full/half/auto*
Configure VLANs allowed on trunk
	Switchport trunk allowed vlan *VLAN ID*
Show vlans
	Show vlan brief
specify native vlan
	switchport trunk native vlan 10
Router on a stick
	Switch - configure access ports
		int *interface*
		switchport mode access
		switchport access vlan *VLAN ID*
	Switch Configure trunk port
		int *interface*
		switch mode trunk
		switchport trunk encapsulation dot1q
	Router - Configure for each vlan
		int *interface*.*vlan id*
		encapsulation dot1q *VLAN ID*
		ip add *ip address* *submask*
Configuring Native VLAN on router
	encapsulation dot1q *VLAN ID* native
		Assumes untagged frames belong to the native vlan and frames sent in the native vlan will not be tagged
	Configure the ip address of the native vlan in the router's physical interface
To enable routing in layer 3 switch use the command
	ip routing
Then interface to an IP interface
	no switchport
		turns it from a switchport into a routed port
Set interface to default
	default interface *interface*
To create an SVI
	interface vlan *vlan id*
	ip address *ip address* *netmask*
	no shut
Display switchport status
	show interface *interface* switchport
Enable DTP
	switchport mode dynamic *auto/desirable*
Disable DTP
	switchport nonegotiate
Show VTP status
	VTP version capablities
	VTP version running
	VTP domain name : default is null
	VTP Operating mode
	VTP maximum VLANs supported
	Number of existing VLANs
	Config Rev #
Change VTP domain name
	vtp domain *name*
Change VTP version
	vtp version *1/2/3*
Change VTP mode
	vtp mode *transparent/client/server*
Show VTP Status
	show vtp status
enable portfast
	int *interface*
	spanning-tree portfast
Enable portfast on all access ports
	spanning-tree portfast default
Enable BPDU guard
	int *interface*
	spanning-tree bpduguard enable
enable BPDU guard on all portfast interfaces
	spanning-tree portfast bpduguard default
Set switch as primary switch in STP
	spanning-tree vlan *VLAN ID* root primary
	*sets STP priority to 24576, if another switch has 24576, it will set it to 4096 less and so on*
Set switch as secondary switch in STP
	spanning-tree vlan *VLAN ID* root secondary
Change interface cost in STP
	int *interface*
	spanning-tree vlan *VLAN ID* cost *cost*
Change interface port priority in STP
	int *interface*
	spanning-tree vlan *#* port-priority *value*
Change spanning tree mode
	spanning-tree mode *mst/pvst/rapid-pvst*
Show spanning tree
	show spanning-tree
Configure spanning tree link type
	spanning-tree link-type *point-to-point/shared*
Show etherchannel
	Show etherchannel load-balance
Change etherchannel load balance
	port-channel load-balance *method*
Configure etherchannel on int
	int range *interface*
	channel-group *number* mode *mode*
change channel protocol
	channel-protocol *LACP/PAgP*
etherchannel show
	show etherchannel summary
	show etherchannel port-channel
Show ip protocols status
	show ip protocols
rip config
	router rip
	version 2
	no auto-summary
	network *ip address*
passive-interface
	passive-interface *interface*
Propegate default route
	default-information originate
eigrp config
	router eigrp *ASN*
	no auto-summary
	passive-interface *int*
	network *network* *wildcard mask*
OSPF config
	router ospf *proccess id*
	network *ip addr* *wildnet mask* area *number*
Change reference bandwidth OSPF
	auto-cost reference-bandwidth *bandwidth in mbps*
Show ospf neighbor *used to ddisplay the collection of OSPF neighbor link-states*
	Show ip ospf neighbor
Show ospf status on an interface
	show ip ospf interface *int*
Configure all OSPF interfaces to be passive
	router ospf *number*
	passive-interface default
Change ospf priority
	int *int*
	ip ospf priority *0-255*
configure PtP
	encapsulation *ppp*
	*Figure out which side is DCE and which is DTE*
		show controllers *interface*
	clock rate *bits-per-sec*
	ip ospf network *network type*
show ospf info
	show ip ospf database
Change HSRP version
	int *interface*
	standby version *1/2*
HSRP  virtual IP
	standby *group number* ip *ip addr*
HSRP Priority 
	standby *group number* priority *priority number*
HSRP Preemption - Causes router to take role of active router even if another router already has the role
	standby *group number* preempt
	*only have to configure this on the router you want as active*
Show HSRP
	show standby
Configuring IPv6
	ipv6 unicast-routing - *allows router to perform ipv6 routing*
		int *interface*
		ipv6 address *2001:db8:0:0::1/64*
		not shut
Show Ipv6
	show ipv6 interface brief
		*link local addresses are automatically configured on an interface when IPv6 is assigned*
Config as anycast
	ipv6 addr *2001:db8:1:1::99/128* anycast
Display ipv6 neighbor table
	show ipv6 neighbor
Config IPv6 route
	ipv6 route *dst/prefix* {*next hop* | *exit interface* (*next hop*)} (*ad*)
Config numbered access list
	access-list *number* permit | deny *ip addr* *wildcard mask*
Config named access list
	ip access-list standard | extended *acl-name*
		*entry-number* {deny | permit} *ip addr* *wildcard mask*
		remark *remarks/decr*
Apply ACL to interface
	int *inter*
	ip access-group *ACL* in | out
Resequence ACL
	ip access-list resequence *acl-id* *starting-seq-num* *increment*
	starting-seq-num - Change the seq num of first entry to X
	increment - add X for every entry after that
Configuring ext ACL from global config
	access-list *number* (permit | deny) *protocol* *src-ip* *dst-ip*
Configuring ext ACL from subconfig mode
	ip access-list extended (name | number)
		*seq-num* (permit | deny) *protocol* *src-ip* *dst-ip*
Matching port numbers
	(deny | permit) (tcp | udp) *src-ip* (eq | gt | lt | neq | range) *src-port-num* *dst-ip*  (eq | gt | lt | neq | range) *dst-port-num*
	eq = equal to
	gt = greater than
	lt = less than
	neq = not equal to
	range = range *port1* *port2*
	host = used if its a /32
	example : deny tcp any host 1.1.1.1 eq 80
CDP Configs
	CDP troubleshooting
		show cdp
		show cdp interface
			gives basic info on each interface
		show cdp traffic
			shows cdp counters
		show cdp neighbors detail
			shows detail info on cdp neighbors
		show cdp entry *name*
			only specified neighbor
	To enable/disable CDP
		(no) cdp run
	to enable disable cdp on interface
		int *interface*
			(no) cdp enable
	Configure CDP timer
		cdp timer *sec*
		cdp holdtime *sec*
	CDP v2
		(no) cdp advertise-v2
LLDP configs
	Enable/disable
		(no) lldp run
	Enable on specific interfaces
		Transmit LLDP on interface only
			lldp transmit 
		Recieve LLDP on interface only
			lldp receive
	Configure lldp timer
		lldp timer *sec*
	Configure LLDP holdtime
		lldp holdtime *sec*
	Config LLDP reinit timer
		lldp reinit *sec*'
LLDP verification
	show lldp traffic
	show lldp interface
		shows lldp applied interfaces
	show lldp neighbors
		Shows lldp table
	show lldp neighbors detail
		detailed interface information
	show lldp entry *interface*
		detailed interface information for specific interface
NTP
	show clock
	show clock detail
	Manual configure time
		clock set *hh:mm:ss* *day month year*
	Manuall configure hardware clock
		calender set *hh:mm:ss* *day month year*
	sync calender to clock
		clock update-calender
	sync clock to calender
		clock read-calender
	change time zone
		clock timezone *timezone* *hours-offset minutes-offset*
	set clocktime daylight saving
		clock summer-time (date | recurring) *week# day month hh:mm* *week#-to-end day month hh:mm*
	set NTP server
		ntp server *ip add* *prefer*
	set symmetric mode
		ntp peer *ip add*
	show ntp table
		show ntp associations
	show ntp status
		show ntp status
	Configure NTP auth
		ntp authenticate
		ntp autheitcation-key *key#* md5 *key*
		ntp trusted-key *key#*
		ntp server *ipaddr* key *key#*
DNS configs
	Configure Router to act as DNS server
		ip dns server
	configure a list of hostname/ip addr mappings
		ip host *PC1* *192.168.0.101*
	Configure outside DNS server Router will query
		ip name-server *8.8.8.8*
	Enable router to perform DNS queries
		ip domain lookup
	Configure default domain name
		ip domain name *nelsonchiu.com*
	show host file
		show hosts
DHCP server config
	ip dhcp excluded-address *192.168.strt ip 192.168.end ip*
	ip dhcp pool *pool name*
		network *192.168.1.0* */24*
		dns-server *dns ip*
		domain-name *set domain name*
		default-router *default gateway ip*
		lease *days hours minutes* or *infinite*
Show dhcp cmds
	show ip dhcp binding
configure router to use DHCP to learn it's ip address
	int *g0/1*
	ip address dhcp
Configure DHCP relay agent
	int *g0/1*
	ip helper-address *192.168.0.1*
SNMP Configs
	*Optional Information*
	snmp-server contact *email addr*
	snmp-server location *location*
	snmp-server community *community* ro | rw
		ro  = read only
		rw = read/write
	snmp-server host *NMS ip addr* version *1 | 2c | 3* *Community*
	snmp-server enable traps *trap set*
Syslog
	!#logging to console lines
		logging console *level | keyword*
	!#logging to vty lines
		logging monitor 
	!#logging to buffer
		*level indicates max level*
		logging buffered (*size in bytes*) *level*
	Logging to external server
		logging *server-ip*
		logging host *server-ip*
	logging trap
		*sets logging level for external server*
		logging trap *level*
	By default Syslog msgs will not be displayed with connected via Telnet/SSH
		Need a command to be used
		R1#terminal monitor
		Must be used everytime you connect via SSH
	Prevent syslog interrupts
		line *con* *0*
			logging sychronous
	Service timestamps log datetime | uptime
		Datetime - Timestamp will display the date/time when event occurred
		uptime - timestamp will display the device uptime when event occurred
	service sequence-numbers
		display sequence numbers
console port security
	line con 0
	*configure password*
	password *ccna*
	*Tell the device to require a user to enter configured password to access the CLI*
	login 
create usernames
	username *name* secret *password*
Apply username to line
	line con 0
		*Tells device to require user to login using one of the configured usernames*
		*overwrites password cmd*
		login local
	User timeout
		exec-timeout *minutes* *seconds*
Configure telnet
	enable secret *password*
	username *user* secret *pass*
	*Up to 16 lines can connect at once (Virtual TeleType)*
	line vty 0 15
	login local
	exec-timeout 5 0
	*Configure what connections to vty lines are allowed*
	transport input *( telnet  | ssh | telnet ssh | all | none)*
Enable SSH
	*FQDN of device is used to name the RSA keys*
	ip domain name *domain name*
	*Generate RSA keys*
	crypto key generate rsa modulus *Length*
Configure SSH
	enable secret *password*
	username *user* secret *pass*
	*Restrict SSH to version 2 only*
	ip ssh version 2
	*Up to 16 lines can connect at once (Virtual TeleType)*
	line vty 0 15
	*Cannot use login for SSH only login local*
	login local
	*Apply ACL to line*
	access-class *num* *{in | out}*
	exec-timeout 5 0
	*Configure what connections to vty lines are allowed*
	transport input *(telnet | ssh | telnet ssh | all | none)*
View file systems
	Show file systems
Transfer files
	copy *source* *destination*
Choose boot file
	boot system *filepath*
	copy run start
	*save the config*
	reload
show flash direfctory
	show flash
Configure FTP user/password
	ip ftp username *user*
	ip ftp password *passwd*
Static NAT config
	int *g0/1*
		*define the inside interface*
		ip nat inside
	int *g0/0*
		*define outside interface*
		ip nat outside
	*configure one to one ip addr mappings*
	ip nat inside source static *local-ip* *global-ip*
Check IP NAT translations
	show ip nat translations
Clear nat translation
	clear ip nat translation *
Dynamic NAT config
	int *g0/1*
		ip nat inside
	int *g0/0*
		ip nat outside
	*Define the traffic that should be translated*
	access-list 1 permit *192.168.0.0 0.0.0.255*
	*Define pool of inside global IP addr*
	ip nat pool *POOL1* *starting-ip-addr* *ending-ip-addr* (prefix-length *24* |  netmask *255.255.255.0*
	*Configure dynamic NAT by mapping ACL to pool*
	ip nat inside source list *1* pool *POOL1*
PAT config
	int *g0/1*
		ip nat inside
	int *g0/0*
		ip nat outside
	*Define the traffic that should be translated*
	access-list 1 permit *192.168.0.0 0.0.0.255*
	*Define pool of inside global IP addr*
	ip nat pool *POOL1* *starting-ip-addr* *ending-ip-addr* (prefix-length *24* |  netmask *255.255.255.0*
	*Configure dynamic NAT by mapping ACL to pool*
	ip nat inside source list *1* pool *POOL1* overload
PAT config (interface)
	*Mapping ACL to interface and enabling overload*
	ip nat inside source list 1 interface *outside-interface* overload
Configure Voice VLAN
	int *g0/1*
	*Port into access mode*
	switchport mode access
	*Adds vlan10 for pc*
	switchport access vlan *10*
	*Adds vlan 11 for voice*
	switchport voice vlan *11*
Power policing - err-disable
	int g0/1
		power inline police
		*disables the port and send a syslog msg if PD draws too much power*
Power policing log only
	int g0/1
		power inline police action *log*
		*Logs only, does not shutdown*
Port Security
	int g0/1
		swi mod acc
		switchport *port-security*
Configure violation mode
	switchport port-security violation { shutdown | restrict | protect }
Show port security
	show port-security {interface *interface*}
err-disable recovery
	errdisable recovery cause *psecure-violation | dhcp-rate-limit*
	errdisable recovery interval *seconds*
Config mac aging
	switchport port-security aging *(static | type {absolute | inactivity} | time {sec} )*
Dynamic mac addresses to be added to runnign config
	switchport port-security mac-address sticky 
Add mac addr to portsecurity 
	switchport port-security mac-address *mac-address*
DHCP Snooping
	*enables dhcp snooping globally*
	ip dhcp snooping
	*enable it on every vlan*
	ip dhcp snooping vlan 1
	mo ip dhcp snooping information option
	int *g0/0*
		ip dhcp snooping trust
Show snooping table
	show ip dhcp snooping binding
DHCP snooping rate limiting
	int g0/1
		ip dhcp snooping limit rate *messages-per-second*
DArp Inspection setup
	ip arp inspection vlan 1
	int *g0/1*
		ip arp inspection trust
Apply ARP inspection vlan 
	ip arp inspection vlan *vlan-number*
create arp access list
	arp access-list *name*
		permit ip host *ip-addr* mac host *mac-addr*
	ip arp inspection filter *arp-acl-name* vlan *vlan-id*
inspect arp inspect
	show ip arp inspection
	show ip arp inspection interfaces
VRF configuration
	ip vrf *vrf-name*
Apply VRF onto interface
	int *g0/0*
		ip vrf forwarding *vrf-name*
Configuring