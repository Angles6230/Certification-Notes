
### Basic Networking Terms
What is a Network?
	A digital telecommunications network for sharing resource between nodes
	A way to share resources between nodes
Most basic type of network
	Two devices directly connected to each other with a cable
Servers
	Device that provides function for other devices
Clients
	Device that accesses a service made available by a server
Protocol
	Set of rules used for communication between devices

#### Networking Devices
Repeater
	Layer 1 device - simply amplified and repeated the electrical signal
	One to one port
Hub
	Multiport repeater
	One port to multiport - constant broadcast
	Wireless Access Points (WAPs)
	Learns MAC in software
Switch
	Layer 2 device
	Uses MAC address table to organize traffic
	Learns MAC in hardware using ASIC(Application Specific Integrated Circuits)
	Used in LAN
	Microsegmentation - each host directly connected to switch is now its own collision domain
	Same broadcast domains as a bridge
	Switch Operation
		Whenever frame is received switch will look at src mac
		Learned MAC will be added to MAC addr table which maps to ports
		Unicast frame - known MAC addr - send frame out relevant port
		Broadcast frame or unknown unicast - Flood out of all ports aside from one it received the frame from
Routers
	Layer 3 devices
	Uses IP address table to transport traffic
	Routes information between IP networks
	Used in WAN
Firewalls
	Restrict who can access the network
	Uses firewall rules
	Blocks traffic from outside to inside or vice versa according to firewall rules
Intrusion Detection System [IDS]
	Can warn you when an attack happens
	simply detects and alerts
Intrusion Prevention System [IPS]
	alerts theres a problem but also blocks the attacker
Wireless Lan Controller [WLC]
	Used to manage access point
Access Point
	Autonomous - dont need a WLC
	Lightweight - register with the WLC and be configured through the WLC
		WLC will manage the Lightweight APs
### Ethernet LAN Switching
Ethernet frame
	split into header nd trailer
	`[preamble | Start-of-frame(SOF) | destination addr | src addr | type | data field | FCS`
	Please suck dick so tanya doesnt fuck
	header
		preamble
			7 bytes long - 8 bits per 1 byte = 56 bits
			allows devices to synchroniz their reciever clocks
			10101010
		start frame delimiter - SFD
			1 byte/8bit
			10101011
			indicates end of preamble and beginning of rest of the frame
			used for synchronization
		Destination - layer 2 addr(MAC) that frame is being sent - 6 bytes
		source - layer 2 addr  - 6 bytes
			indicate the devices sending and recieving the frame
			MAC addr - 6 byte/48 bit address
		type - indicates layer 3 protoccol used in the packet - IPv4 or IPv6 - 2 bytes
			 sometimes its a length field 
				 2 bytes or 16 bit field
				 IF the value of the field is 1500 or less it indicates the length of encap packet or less
				 If value of 1536 is greater then it indicates the TYPE of packet, length is then indicated with other methods
				 0x0800 - IPv4 -2048 in dec
				 0x86DD - IPv6 - 
	Trailer
		only has FCS or frame check sequence
			4 bytes in length
			detect corrupt data by running a Cyclic redundancy check (CRC) algo over the received data
	Total size is 26 bytes
	Minimum size of a frame is 64 bytes
		64 - 18(header + trailer) = 46
		If payload is less than 46 bytes, padding bytes are added
MAC Addr
	6 octets
	Burned In address - BIA
	First 3 octets are ORganizational Unique Identifier (OUI)
		assigned to the company making the device
	LAst 3 octets are unique to device itself
	12 hexdec char
Types of frame
#### MAC address
Dynamic MAC addr
	automatically learned on the mac addr
	IF unknown unicast frame - frame gets flooded on every port aside from the one it got
	If known unicast frame - frame is forwarded according to the port in the mac addr table
Dynamic MAC addr is removed from the MAC addr tables after 5 min. 
	Called aging
Mac Address table
	Show mac address-table
	Vlan column, mac addr column, type and port
#### ARP 
Address resolution protocol
used to discover layer 2 address(MAC) of a known layer 3 address(IP)
Consists of two messages
	ARP Request
		Sent as broadcast
		Src Ip and Dst IP
		Src MAC is src
		Dst MAC is Broadcast or FF:FF:FF:FF:FF
		Host devices will ignore if it doesnt have it's dest IP
	ARP Reply
		sent as unicast - only one host
		All field are filled out and only sends it unicast
ARP Table
	Internet Address - IP addr
	Physical Addr - MAC addr
	Type static - Default entry
	Type dynamic - learned via ARP
#### Ping
Network utility that is used to test reachability
Two messages
	Both are unicast
	ICMP echo request
	ICMP echo reply
### IP addresses
Class A 
	First octet binary
	0 - 127.255.255.255
		127.X.X.X - reserved for loopback
		0.X.X.X - reserved for default network
	Private - 10.x.x.x
Class B 
	129 - 191.x.x.x
	Second octect
	172.16.x.x - 172.32.x.x
Class C 
	192-223.x.x.x
	Third octet
	192.168.x.x
Class D 
	Multicast addresses
	224 - 239.x.x.x
	224.0.0.x - Multicast address
	Fourth octet
Class E
	240-255.255.255.255
	Broadcast reserved
Local Loopback Addresses
	127.X.X.X range - IPv4 local loopback address
	10.1.1.1/32 - Router and switch loopback address
		used for troubleshooting routing protocols
	::1 - IPv6 loopback
	Used to let a system send msg to itself for testing
	verifies the TCP/Ip stack is correctly installed on the machine
APIPA
	Automatic Private IP address
	When PC is configured with DHCP but no DHCP server is available
	PC automatically chooses a IP 169.254.0.0/16 for communication in local segment
	IP assigned is non routable but communicate on local network
	Assigned to DHCP clients
Discontiguous Mask 
	Non continuous mask
	11100.1111.00011.1100
Only contiguous masks supported on cisco devices
	Subnetmask must start wtih contiguous binary 1s
### Cabling and Packet Flows
CSMA/CD
	Carrier sense Multiple Access Collision Detection
	Once collision is detected, random jam is sent and hosts wait a random time before sending 
Unicast - one to one
Broadcast - one to all
	IPv6 does not support
Multicast - one to multiple 
	Devices need to explicitly ask for the traffic
10Base2 
	10Mbps - shared
	Max distance of 183m
	Due to collisions can only use 30-40% 
		(10/4 * 30%) really be 0.75MBps not 10Mbps
	Also broadcast - makes ddos
10BaseT
	Twisted pair ethernet
	Max distance of 100M
	UTP or STP - shielded or unshielded
	MDI -> MDIX - straighthrough
	MDI:MDI or MDIX : MDIX - cross over
	MDI: PC, Routers, server
	MDIX: Hubs, Switchs, bridge
100BaseT 
	802.3u
	100Mbps
1000BaseT
	802.3ab
	1Gbps
10GBaseT
	802.3an
	10 gig
Fiber
	Cable breakdown
		Fiberglass core - center
		Cladding - reflects light
		Protective Buffer
		Outer Jacket of the cable
	Single Mode
		Core diameter is narrower
		light enters at sincle angle
		Laser based transmitter
	Multimode
		Core diameter is wider
		Allows multiple angle/modes of lightwaves to enter fiberglass core
		LED based transmitter
		Longer than UTP but shorter than  single mode
		Cheaper than single mode
Fiber Standards - S is not single
	1000Base-LX 
		802.3z
		1Gbps, 550m(MM)/5km(SM)
	10GBase-SR 
		802.3ae
		Multimode
		400m
	10GBase-LR
		802.3ae 
		single mode
		10km
	10GBase-ER
		802.3ae 
		30km
		single
Auto MDI/X 
	Automatically changes electrical signals so you dont need crossover/straighthrough
	can autodetect cable type
Direct Attachment Cable
	cable with SFP on both ends
Rollover Cable
	Connect to console port
Hubs
	Frame sent to hub,
	Hub will amplify the signal and send the frame out all ports
Bridge
	store mac addr in mac addr table
	CAM table
	Processing in software
	If MAC addr known in MAC addr table - sent to port
	If unknown then broadcast out of all port except source port
Switches
	ASIC
		Application specific Integrated Circuit
	1. MAC addr is empty
	2. unknown Frame is flooded out of all ports
	3. source port is writted into mac addr table
	4. once dest port replies to src port, the new port is added to mac addr table
		IF frame has dst mac addr is FFFFFFF -> broadcasted
		Broadcast addr is not associated with specific ports
	Switch will not slow frame down - physical movement
	Full duplex - Collision detection is turned off, only CSMA is used
Routers
	Still use MAC Addr but decision makingprocess is done using IP addr
	MAC addr is from hop to hop
	IP addr is from src to destination
	When you configure a router with an IP, it includes mask
		The router will update the routing table with the network addr
		Routers populate on network addr not individual host addr
	ARP 
		Resolves IP > MAC bc you need MAC to make next hop
	1. Src PC checks ARP in it's local ARP cache
	2. if no arp entry, sends out a ARP Request broadcast on local subnet asking for MAC addr of Dst PC
	3. ARP Reply comes back from someone who knows the MAC Addr of Dst IP, MAC addr is associated with IP addr and added to Src PC ARP cache
### Loopback 
Loopback interface exists for the purpose of testing 
Loopback is a logical interface in a router that won't go down unless you shut it down
	Can give it an IP address
If a cable went down on a physical addr, you can telnet to a loopback
Easier to use loopbacks for management
In OSPF, the router ID selected is the highest IP addr of any interface
	Loopbacks override physical interfaces
	Normally if it was a physical interface, if it went down router ID would change
	However with loopbacks router IDs stay consistent
	For OSPF
		Specify loopback int and set your own router ID
### TCP - UDP
IP is connectionless
UDP
	User Datagram protocol
	Connectionless, best effort
TCP
	Transmission Control Protocol
	3 way handshake
	connection oriented
Socket
	Combination of IP addr, port number used and transport protocol used
TCP/UDP allow for session multiplexing
	Single host with single IP addr is able to create multiple sessions
Segmentation
	Information can be broken up into smaller chunks
	MTU - Maximum Transmissible Unit depends on medium
		FastEthernet is 1500 bytes
		TCP is 65495 bytes
			When TCP is transported across fastethernet it is broken up into 1500 bytes
	Maximum segment size is the largest amt of data in bytes TCP is willing to send in one segment
	MSS should be small enough to avoid IP fragmentation
	TCP supports MSS and Path MTU discovery
		Sender and receiver can automatically determine max transmission size
	Path MTU discovery is mandatory in IPv6
Flow Control
	To avoid sending data too quickly
	If sender send data faste rthan receiver can handle receiver drop the data
	TCP has sliding window to control flow of data.
		Sender will only send certain amt of info before it recieves a send ack
	UDP will simply send the information regardless of the processing speed
Connection Oriented
	TCP is CO
	UDP is Connectionless
Reliability
	Every segment is acknowledged
UDP
	Transport layer protocol
	Access to layer 3 without overhead
	connectionless
	provides limited error delivery
	best effort
	no data recovery features
	UDP Header
	16 bit src port | 16 bit dst port
	16 bit UDP length | 16 bit UDP checksum
	Min 8 bytes
	Max 65,535 bytes 
	Checksum is optional in IPv4 but not in IPv6
TCP
	Pair of virtual circuits
	Full duplex
	Error checking due to checksum
	Data packets are sequenced and numbered
	Data acknowledge receipt - if not ack then it will retrans or terminate
	Data recovery features
	TCP flags/ control bit
		CWR - Congestion Window Reduced flag - Qos to indicate congestion
		ECE - Echo congestion Noticiation Echo field - QoS to indicate congestion
		URG - Urgent
		ACK - acknowledgement of data
		PSH- PUSH set by sender to immediately process this
		RST - reset connection
		SYN- synchronize sequence number first flag only
		FIN - finish - sequence is done
	Window Size - specify size of receive window
Port Number 
	Well known 1- 1023
	Registered 1024 - 49151
	Dynamic - 49152 - 65535
	Euphemeral ports - Short lived ports used for the client side of the connection
		only last for the duration of the session
		IANA suggests 49152 - 65535
		BSD 1024 - 4999
		Linux uses 32768 - 61000
		Win7 uses IANA
		FreeBSD uses IANA
Three way handshake
	HostA : Sends CTL = SYN SEQ = 100 or initial value
		Also specifies the num of port sender wants to connect
	HostB: Received SYN
		Send SYN, ACK
		CTL = SYN, ACK SEQ = 300 ACK = 101
	ACK flag indicates the next portion of data the host expects to recieve
	HostA: Syn received, session established
		CTL = ACK, expects 301 and SEQ = 101
		Syn flag is unset so 3 way handshake is sent successfully
TCP Window size
	In basic form, tcp has window size of 1
	For every 1 segment, reciever sends 1 ack
	Window size - number of data segments the sender is allowed to send per ack
	Sliding window
		When a packet is dropped the host will slow down
		Congestion window - CWND 
			Intially set at very low value
			increases at exponential rate
			slows down growth using congetion avoidance
		Weighted Random Early Detection - WRED
			Improve efficiency of TCP transmission
			Avoid global syncronization issue - where mutliple senders drop the packet and slow down/speed up at the same time which causes congestion again
				Avoids this with random detection
			Randomly drops packets
				WRED drops based on QoS
		Both reciever and sender can negotiate the window size
Port Spanning/Port mirroring
	SPAN - Switch  Port ANalyzer
### VLANs
VLAN
	Single broadcast domain
	Virtual LANs = Broadcast domains
		Seperate networks regardless of physical location
	Advantages
		Segmentation
		Flexibility
		Security
PCs are oblivious to VLANs they only see ethernet
Trunks
	Special type of link between 2 switches to communicate VLAN information between them
	ISL - interswitch link
	802.1q - industry standard 
	Allow multiple VLANs to traverse a link
802.1Q frame
	Contains a Tag field
		contains of two main parts
		Tag Protocol Identifier - TPID
			0x8100 to identify it as a 802.1q frame 16 bits/2bytes length
		PRI - Priority code point
		Canonical Format Identifier - CFI
		VLAN ID - 12 bit field to specify whcih VLAN this field belongs to
			2^12  = 4096 variations
			However VLANs 0 and 4065 are reserved for system use and VLAN 1 is native VLAN
			VLANs 2 - 4094 are configurable
Native VLAN
	Untagged VLAN
	Management VLAN
		STP/DTP
	Untagged frames are automatically associated with Native VLAN
	Always use VLAN 1, tagged if native VLAN
		CDP - Cisco Discovery Protocol 
		VTP - VLAN Trunk Protocol
		PAgP - Port aggregation Protocol
		UDLD - UniDirection LinkDirection
	If Native VLANs are not the same, it will be notified Native VLAN mismatch
	Sometimes if used for cisco switch -> phone -> PC
		Tagged goes to Phone
		untagged/native goes to PC
Port Assignment
	Static VLAN
		ADmin configured ports
	Dynamic VLAN
		VLAN Management  Policy Server
			VLAN assigned to port depending on the MAC address of the device
	Voice VLAN
		IP Phones
VLAN Trunking Protocol
	Cisco propriety
	Allows for propagation of VLAN information
		Addition, deletion and renaming of VLANS
	Can only propagate across trunk links
	VTP Messages
		Summary Advertisment
			Every 5 minutes
			Or whenever there is a change
			Informs other switches of the current VTP domain and new config number
		Subset Advertisements
			Contains a list of VLAN information
			If there are several VLANS, more than one may be required
		Advertisement Requests
			Summary Request
				Switch has been reset
				VTP domain name has been changed
				Switch has recieved VTP summary adv with higher config rev number than it's own
	VTP requires same VTP domain with same VLAN information
		Switches can only be in one VTP domain at a time, default is in NULL Domain
	Any changes causes the revision to go to next
		Then any switches on a lower revision will synchronize to the highest revision
	VTP Modes
		Server
			Create, Modify, delete VLANs
			Sends and Forwards Advertisments
			Synchronizes database rev num
			Saves VLAN Config 
			This is where you make your changes
		Client
			Cannot create, modify, delete vlans
			Sends and forwards advertisments
			Synchronizes database to highest rev num

### DTP
Dynamic Auto
	Craves for access but will concede to trunk
	Doesn't initiate trunking
Dynamic Desireable
	Craves for trunk but will concede to Access-Access only
	initiates truking with the remote end
DTP packets are sent on VLAN1
When trunking is used NAtive VLAN is used to send DTP packets
### Spanning Tree
Stops Layer 2 loops in switch environment
Different types of Spanning Tree
	802.1D - Legacy, used for bridges
	CST - common spanning tree - assumes only one spanning tree instance for the entire bridged network
	PVST - Only supported ISL
	PVST+ - Supports ISL and 802.1Q
		Cisco enhancement of spanning tree that provides seperate 802.1 Spanning tree instances
		1 BPDU per VLAN, more VLAN meant more traffic
	MSTP - Multiple VLANs to same spanning tree
	802.1S - 2 spanning tree instances
	RSTP - Rapid spanning tree 802.1w
		Quicker convergence
		Only supports one instance of spanning tree
		Adds roles to ports and enhances BPDU exchanges
	Rapid PVST+ - one spannng tree per VLAN but rapid convergence
		Default on cisco routers 
Required by bc otherwise frames would flood out everything and create routing loops
Bridge Protocol Data Units 
	Sent every 2 seconds
	If a sw receives BDPUs from same switch on multiple ports the SW knows it has a loop
	Contain information about spanning tree
	Contains the SW's unique MAC addr
	Bridge ID - 8 byte value unique to switch
		2 byte priority field
			32768 priority by default
		6 byte system id
		Lower is better
	3 Types
		Configuration 
			Used by spanning tree to provide infromation to switches
		Topology change
			tel lswitches of a  change
		Acknowledgement
			used to confirm receipt of a topology change in a notification
	Disables the interface if spanning tree is detected
Root bridge
	Root of the spanning tree
	Determined with lowest Bridge ID
		which consists of priority and MAC addr
	Root port
		Sending port
		When determining the root port
			Port cost > Sender bridge ID > Sender port ID 
		Port chosen with lowest path cost
			Speed - Cost 1998 and before - Cost 2004 and after
			10 Mbps - 100 - 2,000,000
			100 Mbps - 19 - 200,000
			1Gps - 4 - 20,000
			10 Gbps - 2 -2,000
			100 Gbps - NA - 200
			1 Tbps - N/A - 20 
		Lowest neighbor bridge ID
		Lowest port priority
			128 by default
		Lowest Port ID
	Designated Port - best port to use on a per segment basis to get to the root bridge
		Recieving port
	Every other port is  in BLK state
		In RSTP or RPVST it is called Alternate port as it will be fallback if Designated port goes down
PVST+ Extended Bridge ID
	When configuring multiple VLAN and Per VLAN Spanning Tree
		Different MAC addr would have to be allocated for every VLAN
		Not scalable
	Mac Address Reduction
	Bridge ID is split into 3 parts
	Bridge Priority | Extended System ID | MAC Address
	Allows for a large amt of bridge IDs even without too many MAC addr/unique physical units
	Bridge Priority can only be in increments of 4096
	0 = 4096
	1 = 8192
	Max is 61440
	Lower is better
	Bridge Priority + VLAN number = Bridge ID Priority
Edge Port/ Port Fast 
	Standard ports take 30 seconds to converge
		PC already booted up and DHCP requested IP addr before it is converged
	Edge ports - Ports connected to edge devices
	Cisco - port fast
	Generic - Edge port 
	Enable Port Fast ONLY on access edge ports
	If you enabled port fast on trunk ports, it will loop
		Starts immediately into forwarding in Spanning Tree
		PortFast bypasses listening and learning
			Goes directly from blocking to forwarding
		Edgeports connected to end host will still be Point to point(P2p) if full duplex
PVST vs RPVST Port states
	When in learning state, traffic will be blocked,
	USer traffic will only be forwarded when in the fwd state
	States
		Blocking - Blocks data and blocks Learning MAC - stable
		Listening - Blocks data and blocks learning MAC - transistory
		Learning - Blocks Data but learns MAC addr - transitory
		Forwarding - Forwards Data and Learns MAC addr - Stable
		Disabled - Blocks data and blocks learning MAC - Stable
	Rapid Spanning Tree only has
		Discarding
		Learning
		Forwarding 
### Switch interfaces
Switch interfaces are up/up if connected to another device
down/dwon if not connectied to another device
Duplex statues
	A-full
		auto negotiate full
Speed
	a-100
		auto negotiate up to 100mbps
	auto 
		auto negotiate the highest
Type
	Type of connector
Duplex
	Half duplex
		device cannot send and receive data at the same time
	Full duplex
		device can send and recieve at the same time
Autonegotiation
	interfaces that can run at different speeds can have default settings of speed auto and duplex auot
	Interfaces advertise their capabilities to the neighboring device and negotiate the ebst speed and duplex they are both capable of
	For Speed 
		will try to sense the speed that the other device is operating at
		if it fails to sense speed it will use slowest supported speed
	For duplex
		if the speed is 10mbps or 100mbps it will be half
		if speed is 1000mbps or greater it will be full
#### Interface Errors
Runts: Frames smaller than min - <64 bytes
Giants: Frames larger than max - 1518bytes>
CRC: Frames tha failed the CRC check in FCS
Frames: Frames that have incorrect format
Input Errors : Total various counters due to above errors
Output Errors : total errors when the switch tried to send frame but failed due to an error
### IPv4 Header
Version
	4 bits, Identifies IP version used
	IPv4 = 0100
	IPv6 = 0110
Internet Header Length
	IHL
	Specifies the length of the header in 4 byte incremets
	Min value is 5 or 20 bytes (5 * 4 )
	Max value is 15 (15 * 4) 60 bytes
DSCP
	Differentiaed Services Code point
	Used for QoS
ECN
	Explicit Congestion notification
	Provides end to end notification of congestion without dropping packets
	however requires both sides to support it
Total Length
	Indicates total length of the packet
	Total lenght of packet
	Value here = bytes, no extra stuff
	Min value = 20 = IPv4 header with no data
	Max value is 65535
Identification
	Identifies which packet a fragment belongs
	All fragments of a packet will have their own IPv4 header but this value is the same
		Fragments are made if it exceeds MTU
Flags
	Used to control/identify fragments
	Bit 0 : reserved
	Bit 1 : Don't Fragment (DF) bit
	Bit 2 : More fragments (MF) bit
		Set to 1 if there are more fragments in the packet coming, 0 if its the last fragment
Fragment Offset
	used to indicate the position of the fragment within the original unfrag IP packet
Time to Live
	TTL
	Router will drop a packet with TTL of 0
	Used to prevent infinite loops
	Each hop count, TTL decreases by 1
	Default is 64
Protocol
	Indicates protocol of the encapsulated L4PDU
	6 = TCP
	17 = UDP
	1 = ICMP
	89 = OSPF
Header checksum
	When router gets a packet, 
	it calculates a checksum,
	 then it compares it to the checksum value in this field,
	 if they dont match
	router drops packet
	Used only to check for error in HEADER ONLY
Source IP addr
Destination IP addr
Options field
	Options
	0 - 40 bytes
### Routing
What is routing? 
	Process that routers use to determine the path that IP packets should take over a network to reach their destination
Routers store routes to all of their known destinations in a routing table
Routers look in the routing table to fdind the best route to forward that packet
Types of routing
	Dynamic routing
	Static routing
		Manually configures routes on the router
Codes of Routing Table
	These two are automatically added when you configure an IP addr on an interface and enable it.
	C - Connected
		Route to the network the interface is connected to
	L - Local
		Router with the actual IP addr configured on the interface
		IP Address configured on a router interface will appear as this
Connected and Local routes are created once an int is turned on
C - connection to network
	Provides connection to all hosts in that network
L - connection to the actual IP
	Router knows, if i recieve a packet with this IP addr, its to me
Routers choose the most specific matching route
	AKA the lowest subnet
Breaking Dwon the variable subnetted
ex. 192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks
	In the routing table there are 2 routes to subnets that fit within the 192.168.1.0/24 network, with two different netmasks (/24, /32)
Routers drop packets with an unknown destination
### Static Routing 
A router knows how to reach its own IP addresses and dest in connected networks but not remote networks
Default gateway
	Least specific route possible
	includes all IP addresses
	Gateway of last resort
If a router doesnt have a route to the destination it will drop the packet
Router needs two routes, route to A and route to B
This ensures two way reachability to a -> B and B - > A 
R1 has PC A 
R2 has PC B
However R1 to PC B needs to be configured
Static has code of S
	When exit interface only, it only displays "Directly connected and the exit interface"
	if given exit int and next hop IP, it will show via *ip addr* and exit int
S* means route is a candidate for default route
### Vlans
Virtual Local Area Network
Single broadcast domain
Broadcast traffic
	unnecessary traffic reduces performance
	Want to limit access
		Because this is one LAN, PCs can reach each other directly without going thru the firewall or router
VLANs are configured on a per-interface basis
Logically seperate end hosts at layer 2
Switches do not forward traffic directly between hosts in different VLANs
Accessport is a swtich port that belojngs to a single VLAN
Trunk ports is a switch port that carries multiple VLANs
Trunk Ports
	It is possible to use seperate interface for each VLAN when connecting to switch or routers
	However with a larger amt of VLAN this is not viable
	By default all VLANs are allowed on a trunk lan
		Every single VLAN the switch knows about is on trunk
	Trunking Protocols
		ISL - InterSwitch Link
			old Cisco propriety protocol
			Encapsulates frames
		802.1q or dot1q
			industry standard
			Does not encapsulate any frames
	802.1q tag is inserted between source and type/length
		4 bytes in length
		TPID
			Tag Protocol Identifier
			When the switch sees the value, it knows it's a dot1q tagged frame
			2 bytes/16 bits
			Set to value of 0x8100
		TCI
			PCP
			Priority Code Point
				Used for CoS - class of service
					prioritizes important traffic in congested networks
			DEI
				Drop Eligible Indicator
				Used to indicate frames that cna be dropped if the network is congested
			VID
				VLAN ID
				Identifies the VLAN the frame belongs to
				12 bits/1.5 bytes
				2^12 = 4096 vlans (0-4095)
					However VLAN 0 and 4095 is reserved so 1-4094
					VLAN 1 is native VLAN so 2 - 4094
Vlan Ranges
	Normal 
		1 -1005
	Extended
		1006 - 4094
	Default VLANs that always exist
		1, 1002, 1003, 1004, 1005
Native VLAN
	Feature of 802.1q
	Native VLAN is VLAN 1 by default on all trunk ports
		Can be changed but needs to be manually configured
	Switch does not add a dot1q tag to frames in the native VLAN
	If the switch sees an untagged frame, it assumes it is in the native VLAN
Show vlan brief
	shows ports assigned to each vlan
Show interfaces trunk
	confirms trunk ports
### Multilayer switches
Layer 3 switches
Capable of both switching and router
Can assign IP addresses to it's interfaces like a router
Can create virtual int for each VLAN as well
Can configure routes on it as well
Switch Virtual Interfaces
	Virtual interfaces you can assign IP addresses to in a multilayer switch
To enable routing use the command
	ip routing
Then interface to an interface
	no switchport
		turns it from a switchport into a routed port
To create an SVI
	interface vlan *vlan id*
	ip address *ip address* *netmask*
	no shut
SVIs are shutdown by default so no shut it.
For SVI to be up/up
	1.VLAN must exist on switch
	2. SW must have at least one acceport in VLAN that is up/up or one trunk that allows the vlan that is in up/up
	3. VLAN must not be shut down
	4. SVI must not be shutdown
### DTP
Dynamic Trunking Protocol
	Cisco proprietary protocol that allows switches to dynamically determine interface status without manual config
	Enabled by default
	Should be disabled for security purposes
DTP Modes
	DTP will not form a trunk with a router, PC etc.
	Dynamic Auto
		Does not actively try to form a trunk but will differ if a trunk port is encountered
		auto access
		auto auto
		All other scenarios will form a trunk
	Dynamic Desirable
		Actively try to form a trunk with other cisco switches
		Desirable trunk
		desirable desirable
		desirable auto
	However if it is up against an access port, it will differ to the access port
		static access - access port that belongs to VLAN that doesnt change
		dynamic access- server automatically assigns VLAN depending on the MAC addr
	Old Switches are default desirable, new switches are default auto
Switches can negotiate 802.1q and ISL trunk encapsulation modes with
	switchport trunk encap negotiate
	ISL is favored over 802.1q
DTP frames are sent in VLAN1 in ISL or Native VLAN in 802.1q
### VTP
VLAN Trunking Protocol
VTP allows you to control VLANs on a central VTP server
Other switches synchronize their VLAN Database to the server
Cisco switches operate in server mode by default
VTP domain name is case sensitive
Versions
	1	& 2
		Do not support extended VLAN range
	3
		Supports extended VLAN range
		Offers cryptography for VTP domain password
Modes
	Server
		Can add/modify/delete VLANs
		Store the VLAN database in non-volatile RAM(NVRAM)
			Database is saved even if sw is turned off
		Will increase revision number every time a VLAN is added/modified/deleted
		Will advertise the latest ver of VLAN Database on trunk interfaces
			VTP info is shared on trunk ports only!!!
		Also serve as VTP clients
			Will synchronize to another VTP server with a higher revision number
	Client
		Cannot add/modify/delete VLANs
		Do not store VLAN database in NVRAM until VTP v3
		Will synchronize their VLAN database ot the server with the highest revision number in their VTP domain
		Will advertise their VLAN database and forward VTP advertisements to other clients over their trunk ports
	Transparent
		Does not participate in VTP domain
		Maintains it's own VLAN DB in NVRAM but wont be advertised to other switches
		Will not sync but will forward VTP advertisements
		Only forwards VTP advertisements on trunk ports
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
Change VTP mode
	vtp mode *transparent/client/server*
If a switch with no VTP domain name receives a VTP advertisement with a VTP domain name, it will automatically join that VTP domain
If SW receives a VTP advertisement in the same VTP domain with a higher rev number it will update it's VLAN database
VTP Danger
	If you connect an old SW with a higher rev num to your network and VTP domain name matches, all SW in the domain will sync their VLAN DB to the old SW
Changing the VTP domain to an unused domain will reset the rev  to 0
Changing VTP mode to transparent will also reset rev to 0
Change VTP version
	vtp version *1/2/3*
	Changing version will change rev num as well
### Spanning Tree Protocol
Reasons to use STP
	Network Redundancy - essential
	Servers typcally have more than one NIC so they can be plugged into more than one switch for redundancy
	Each time a frame arrives on a SW port, it uses the src mac addr to update the MAC table
		When frames arrive with same src mac addr but different port, SW will constantly update its MAC addr table
		Known as **MAC address Flapping**
Classic Spanning Tree - 802.1D
Prevents loops by placing redundant ports in blocking state
	turns the ports into backups and forwards if the active port fails
Interfaces in forwarding state behave normally
Interfaces in blocking state only send and receive BDPU(Bridge Data Protocol Units)
STP SW send/receive Hello BPDU out of all interfaces.
	Default Hello BPDU
		Every 2 seconds
If a Sw receives a Hello BPDU on an int it knows the interface is conncted to another SW
Switches use Bridge ID field to elect root bridge
	Lowest Bridge ID is root bridge
	Bridge ID is Bridge Priority > MAC Addr
		Bridge priority is usually the same so lowest MAC addr wins
Bridge Priority is actually 2 parts
	Bridge priority + VLAN ID
Why use this? 
	Cisco switches use a version of STP called PVST Per Vlan Spanning Tree
	Runs seperate STP instance per different VLAN
	By adding VLAN ID in bridge priority, the Sw will have different bridge ID in every VLAN\
Bridge priority must be in values of 4096
All root bridges are in forwarding state
	all other switches must have a path to reach root bridge
When a Sw powers on, it assumes it's the root bridge
	will only give up position to superior BPDU
	Once topology is converged, only root bridge sends 
STP Steps
	1.Switch with lowest bridge ID is the root bridge
		On root bridge, all of it's ports are designated ports
	1. Each remaining switch will select one of it's interfaces to be the root port
		Ports accross the root port are always designated ports
		root port selection
			1. Lowest root cost
			2. Lowest neighbor bridge ID
			3. Lowest neighbor switch's Port ID
	3.  The remaining ports must have 1 designated port, the other ports will be designated
STP Root costs
	10 Mbit - 100
	100 Mbit(fastethernet) - 19
	1 gb - 4
STP Designations
	Root
		Recieves BPDUs
	Designated
		Forwarding BPDUs
	NonDesignated
		Blocking
STP Port States
	Listening
		Transitional
		Leads to Learning state 
		Done by  designated and root port only
		15 seconds long by default
			Forward delay timer
		Does not sent/recieve reg traffic
		Only forwards/receives STP BPDUs
		Does NOT learn MAC addresses
	Learning 
		Transitional
		15 seconds long by default
			Forward delay timer
		Only forwards/receives STP BPDUs
		Does not sent/recieve reg traffic
		Does learn MAC addresses
	Blocking
		Stable, non-designated
		Disabled to prevent loops
		Do recieve only STP BPDUs
		Do not forward STP BPDUs
		Do not learn MAC addresses
	Forwarding
		stable, designated and root
		Operates as normal
		Sends/recieves BPDUs
		Send/recieves normal traffic
		Learns MAC addr
	Disabled
		disabled
STP Timers
	Hello
		How often root bridge sends hello BPDUs
		2 sec
	Forward Delay
		How long the switch will stay in listening and learning states
		15 sec
		30 total for listening and learning
	Max age
		How long interface will wait after ceasing to receive hello BPDUs to change STP topology
		20 sec
		10 x hello timer
Portfast
	Allows a port to move immediately to the forwarding state
	bypassing listening and learning
	Only enable on ports connected to end hosts
	Only create on access mode
BPDU guard
	If an interface with BPDU guard recieves a BPDU from another switch
	INT will be admin shutdown to prevent loop
	To enable int again, use no shut on it.
	However if problem is not solved, it will be shutdown again due to BPDU
### Rapid Spanning Tree
IEEE versions
	Spanning Tree Protocol  - 802.1D
		All VLANs share one STP instance
	Rapid Spanning Tree Protocol - 802.1w
		Faster Convergence
	Multiple Spanning Tree Protocol - 802.1s
		Uses modified RSTP mechanics
		Can group multiple VLANs into different instances
		Better for large networks
Cisco Versions
	Per Vlan Spanning Tree Plus (PVST+)
		Each VLAN has their own STP instance
		Can loadbalance by blocking different ports in each VLAN
	Rapid PVST+
		Seperate STP instance per VLAN
		Better for smaller-med networks
RSTP
	Not a timer based spanning tree algorithm
	Bridge to bridge handshake mechanism
		Allows ports to move directly to forwarding
	Same purpose as STP - Blocking layer 2 loops
	Also elects root bridge,root port and designated port with same rules as STP
	RSTP costs expanded
		10 mbps - 2,000,000
		100 mbps = 200,000
		1 gbps - 20,000
		10 gbps 2000
		1000 gbps - 200
		1 tbps - 20
		10 tbps - 2 
	Simplified port states
		Discarding - stable
			Only receives BPDUs
			Does not learn MAC addr 
			Does not forward traffic
		Learning - transitional
			Send/recieve BPDU
			Learn MAC addr
			Doesn't forward traffic
		Forwarding
			Works as normal
	Port Roles
		Root port 
			Port closest to root bridge
			Root Bridge doesnt have a root port
		Designated Port
			Only one per segment/collision domain
		NonDesignated Port seperated
			Alternate Port Role
				Discarding port that recieves a superior BPDU
				Back up to root port, automatically turns into root port without transitional state 
			Backup port role
				Discarding port that recieves superior BPDU from another interface on the same switch
				Only happens when you have a HUB
				Same BPDU on two ports
				Back up to designated port
				Lowest port ID is selected as DP, other is BUP
	In STP only root bridge sends BPDU
	In RSTP all Sw send their  own BPDUs
		SW is neighbor lost in 3 BPDUs(6s)
			It will then flush all MAC addrs on int
	RSTP link types
		Edge - port connected to end host, moves directly to forwarding
		Point-to-point - direct connection between two switches
			auto-detected
		Shared - connection to hub, half duplex
### Ether Channel
Allows you to group multiple interfaces into a single interface
When the bandwidth of interfaces on endhost is greater than distribution switches it is called **oversubscription**
EtherChannel groups multiple interfaces together into a single interface
Port Channel
Link Aggregation Group(LAG)
	Bundles multiple ports into one etherchannel(LAG) interface
EtherChannel load balances based on flows
	Flow - communication between two nodes in the network
	Frames in the same flow will be forwarded using the same physical interface
		If in different physical interfaces, some frames can arrive out of order
	If a seperate communication happens it will use different physical interface
	TL:DR 1 communication uses the same physical interface
	Purpose
		Bind physical interfaces into a logical interface
		Assign protocol Negotiation mode to a physical interface(trunk)
Layer 2 Etherchannel
Can change inputs used in the interface selection calculation/Configurable to load balance using the below
	Src MAC - default
	Dst MAC
	Src and Dst MAC
	Src IP
	Dst IP
	Src and Dst IP
Layer 3 Etherchannel
	Port Numbers
Three methods of EtherChannel
	Port Aggregation Protocol (PAgP)
		Cisco proprietary
		dynamically negotiates creation/main of etherchannel
	Link Aggregation control Protocol (LACP)
		Industry Standard
		Can be used to form Etherchannels with other companies
	Static EtherChannel
		Protocol isnt used to determine if etherchannel should be formed
		Interfaces is statically configured to form
		Not recommended bc you want the switch to adjust if something goes wrong
Up to 8 Interfaces to be formed into a single EtherChannel
	16 in LACP but 8standby/8active
Etherchannel Modes
	PAgP
		Auto 
			Auto + Auto = no ether
		Desirable
			Desire + auto = ether
			desire +desire = ether
	LACP
		Active - enable unconditionally
		Passive - enable only if a LACP device detected
	on - Enable etherchannel only
		Static Etherchannel
Channel group number has to match for interfaces on same switch, but doesnt need to match on different switches
Trunk config applied to Etherchannel is applied to the member interfaces
Must have matching configs
	Same duplex
	Same speed
	Same switchport mode
	Same VLAN
If an int does not match it will be excluded
Layer 2 Etherchannel can loadbalance based on
	src-dst mac
	src-dst IP
Layer 3 EtherChannel can load balance based on a variety of options.
	• src-dst-mac
	• src-dst-ip
	• src-dst-port
### Dynamic Routing
Network Route
	Route to a network/subnet
Host route
	Route to specific host/single address
	specified with /32 mask
Directly Connected routes
	Have an AD of 0, metric of 0
Floating Static
	A static route that is configured with higher Admin Dist
	Made less preferred than routes learned by dynamic routing protocol to the same dst
	This route will be inactive unless dynamic  routing protocol route is removed
Routers use dynamic routing protocols to advertise information about connected routes and routes they know
Use adjacencies/ neighbor relationships/ neighborships to exchange information
Uses metric to determine which route is superior
	Lower = better
Types
	Interior Gateway Protocol
		Used to share routes within a single Autonomous system i.e. single company
		Distance Vector
			RIP
				Routing Information Protocol
				Hop count metric
				Links of all routes are equal
			EIGRP
				Enhanced Interior Gateway Rotuing Protocol
				Bandwidth and delay
		Link State
			OSPF
				Open shortest Path First
				Cost based on bandwidth
			IS-IS
				Intermediate System to Intermediate system
				Cost is not automatically calculated
					100 by default
	Exterior Gateway Protocol
		Used ot share routes between different autonomous systems
		Path Vector - BGP
Distance vector
	Routing by rumor
	Hop to hop information
	Only send known destination networks and their metric to reach destination networks
	Routers only learn distance(metric) and vector (direction/next hop router)
Link State
	Each router creates a connectivity map of the network
	To allow this, each router advertises information about it's interfaces to it's neighbors
	Uses more CPU
	Faster in reacting in changes in the network
If a router learns two or more routes via same routing protocol to the same dest with same metric, both will be added
	Traffic will be loadbalanced over both routes
	ECMP - Equal Cost Multipath
Metric - used for the same routing protocol 
	Changes 
Administrative distance - used for different routing protocols
	Does not change
	Lower is better
	C - Directly Connected - 0 
	S - Static - 1
	eBGP - 20
	D - EIGRP - 90
	IGRP - 100
	O - OSPF - 110
	ISIS - 115
	R - RIP - 120
	EIGRP(external) - 170
	iBGP - 200
	Unusable - 255
In a routing table it is "[AD/Metric]"
When multiple routes are added to the router vis different routing protocols, only the lowest AD is added to the routing table
### RIP
Distance Vector IGP
Uses Hop count as metric
Max Hop count is 15
Almost never used in real networks
RIPv1 and RIPv2 is used for IPv4
RIPv1
	Only uses classful addresses
	Msgs are broadcast
RIPv2
	Supports VLSM/CIDR
	Includes subnet mask info
	msgs are to multicast to 224.0.0.9
RIPng - IPv6
Uses two msg types
	Request
		Ask RIP neighbors to send routing table
	Response
		To send local router's routing table to neighbors
Both sent every 30s
network command tells router to
	look for interfaces with an ip addr within the range
	active RIP on int that fall within range
	form adj with connected RIP neighbors
	advertise the network prefix of the INTERFACE
	Doesnt tell the router whcih networks to advertise, tells the router whcih int to activate rip on
Passive-interface command
	tells the router to not send advertisements on this interface
### EIGRP
Uses bandwidth and delay to calculate metric
Feasible Distance - route's metric value to destination(src to dest) 
	Best metric along a path
Advertised/Reported Distance - neighbors metric value to destination(hop 1 to dest)
	In the routing table it looks like this:
	``via 10.10.1.1 (Feasible distance/Reported Distance), interface
Successor - best route/ lowest metric
Feasible successor - alternate route whose reported distance is lower than successor's feasible distance 
	variance value - multiplier for max feasible successor RD loadbalancing
	Will only perform over feasible successor routes. 
Sends multicast using 224.0.0.10
Can perform unequal-cost load-balancing
	Can be configured to loadbalance unequally
Autonomous System nuber must match between routers
Router ID
	Manual config
	Highest IP addr on loopback addr
	Highest IP addr on physical int
### OSPF
Uses Shortest Path First (Open Shortest Path First)
	Dijkstra's algorithm
Three versions
	OSPFv1 - not used
	OSPFv2 - IPv4
	OSPFv3 - IPv6+4
Characteristics
	• link-state routing protocol
	• classless routing protocol
	• hop count is unlimited
	• metric = interface cost (bandwidth)
	• global view database topology table
	• shortest (best) route calculated from topology table
	• event-triggered routing updates only
	• auto-summary disabled (default)
	• scalable to large enterprise domains
	• fast convergence when there is link failure
	• load balancing across four equal paths only
Routers store information in LSA - Link State Advertisements
	Organized in a structure called LSDB - Link State Database
Routers flood LSAs until all routers in the OSPF area develop the same map of the network aka LSDB
LSA has an aging time of 30 min
	Flooded again after the timer expires
OSPF Router ID
	OSPF is highest(Open - high), STP is lowest(Stop low)
	Used to identify the OSPF router to neighbors within the same area
	Determination priority
		Manually configured RID
		Higher IP addr among loopback addr
		Highest IP addr among physical interfaces
OSPF Steps
	Become neighbors
	Flood/Exchange LSAs with neighbors
	Calculate the best routes and insert into routing table
OSPF uses areas to divide up the network
	Single area is good for small networks
	single area is too much cpu usage for large networks
MutliArea OSPF must connect back to Area 0/Backbone
Area - A set of routers that share the same LSDB
Backbone/Area 0 - An area all other areas must connect to
Internal Routers - router with all int in the same area
Area Boarder Routers(ABR) - routers with interfaces in multiple areas
	ABRs maintain a seperate LSDB for each area they are connected to
Backbone Router - Routers connected to Area 0
Intra-Area Route - Routes to dst inside the same Area
Interarea route - routes to dst outside to diff areas
OSPF Process IDs are only locally significant
	Only Areas need to be the same
Autonomous System Boundary Router - ASBR 
	OSPF router that connects the OSPF network to an external network
OSPF Metric - Cost
	Calculated by dividing reference bandwidth value by interface bandwidth
	Reference band/int band
	Default is 100mbps
	Does not go lower than 1 cost
	Total Metric is All costs added together
OSPF Neighbors
	Main point of OSPF 
	Once OSPF is actived on an interface, the router starts sending OSPF hello messages
		Default hello timer is 10s on Ethernet/ Dead timer is 40s
		Hello Msgs are multicast to 224.0.0.5
			OSPF hello packets are used for neighbor adjacency and DR/BDR election
	Neighbor States
		(Damn Its 2, Send Emails Later Fucker)
		OSPF is activated on interface
		Sends hello msg to 224.0.0.5
			Contains router ID and neighbor router ID, Neighbor RID is going to be 0.0.0.0
		R1 doesnt know about any neighbors so its state is down
		Neighbor State - Down
		Once R2 receieves the hello packet it will add entry for R1 to OSPF neighbor table
		Neighbor State - Init
			Hello packet received but own router ID is not in the Hello packet
		R2 will send hello packet containing RID of both routers
		R1 will send a hello msg back, containing R2's RId as well
		Neighbor State - 2-way
			Once it hits 2-way state it means they are ready to share LSAs to build a common LSDB
			NonDR/BDR routers stay in 2 way - 2 ways of communication
	Now they decide which one is Master and Slave router
		only needed for intial LDB exchange
	ExStart state
		To decide Master/slave they exchange DBD - Database Description Packets
		Higher Router RID will become the Master and initiate the exchange
		Router with Lower RID will become the slave
	ExChange state
		Routers exchange DBDs which contain a list of the LSAs in their LSDB
		Routers then compare DBD list to their own LSDB
	Loading State
		Routers send Link State Request (LSR) to request that their neighbors send them any LSAs they don't have
		LSAs are sent in Link State update (LSU)
		Routers send LSAck msgs to ack the LSAs
		Both routers have same LSDB
	Full state
		Routers have full OSPF adjacency
		Continue to send and listen for Hello packets every 10s
		Everytime hello is received, Dead Time(40s) is reset
		If Dead time expires, neighbor is removed.
OSPF Message Types
	1 - Hello - Neighbor discovery and maint, neighbor adjacency and sync neighbor LSDB
	2 - DataBase Description(DBD) - Summary of LSDB of each router
	3 - Link State Request (LSR) - Request Specific LSA from neighbor
	4 - Link State Update (LSU) - Send specific LSA to neighbor
	5 - Link State Acknowledgement(LSAck) - Used to Ack the router received a msg
	After network convergence has occured - Keepalive packets are sent a regular intervals between routers
OSPF network types
	Broadcast
		Enabled by default on Ethernet and FDDI
		Assigned to network interfaces of directly connected OSPF neighbors aka ethernet
		B is near E(thernet) and F(DDI)
		10 hello, 40 dead
	Point to Point
		Enabled by default on Point to Point Protocol(PPP) and High Level Data Link Control (HDLC)
		Point to point is on Point to Point 
		Serial interfaces
		10 hello, 40 dead 
	Point to multipoint
		30 hello, 120 dead
	Non-broadcast
		Enabled by default on frame relay and x.25 interfaces
		Rel(ay)aX(.25)
		No hello or dead
Broadcast Network Type
	Enabled on Ethernet and FDDI
	Routers dynamically discover neighbors by sending/listening for OSPF hello using multicast 224.0.0.5
	Designated Router(DR) and BDR(Backup designated router) interface must be elected on each subnet - only DR if no OSPF neighbors
	Routers that are not DR or BDR become the DROther
	Dr/BDr Election order of priority
		1.Highest OSPF Int priority
		2. Highest OSPF Router ID
		The default OSPF interface priority is 1 on all interfaces so router ID is used by default.
DR/BDR election is non-preemptive, once selected they will keep their roles until OSPF is reset. 
	When the DR goes down, BDR becomes DR
	A new election is done for the new BDR
	DROthers only move to fullstate with DR and BDR, they are only in 2way with other DROthers
Routers only exchange LSAs with Dr and BDr, DR Others will not exchange LSAs with each other
	Reduced LSAs flooding the network but same LSDB.
Point-to-point OSPF
		Enabled on serial interfaces using PPP or HDLC encapsulations by default
		Dynamically discover neighbors using multicast 224.0.0.5
		BDR/Dr is not elected
		Only used in point to point connections
		Full adjacency without B/DR
	Serial Connection
		One side - Data Communications Equipment - DCE
			DCE needs to specify clock rate/speed of connection
		One side Data Terminal Equipment - DTE
			DTE recieves the clock rate/speed of the connection
		Default encap on serial is HDLC
Non broadcast timer - hello 30, dead 120
LSA Types
	Type 1 - Router LSA
		Every router generates this LSA
		IDentified using router ID
		List networks attached to the router's OSPF int
	Type 2 - Network LSA
		Generated by DR of each multi-access network
		List routers attached to multi-access network
	Type 5 - AS external LSA
		Generated byASBR to describe routes outside of the AS domain
### First Hop Redudancy Protocol
- Computer networking protocol which is designed to protect the default gateway by allowing two or more routers to provide backup for that address in the event of the failure
- Both routers share a VIP(Virtual IP)
	- End hosts use the VIP as their default gateway
- Each router has the same virtual MAC address
	- Active router replies to ARP req using the virtual MACaddr, so traffic destined for other networks will be sent to it
- Clients are configured to use the VIP instead of the actual IP as the default gateway
- Routers negotiate roles by using multicast Hellos to each other
Router roles
	Standby
	Active
Uses ARP to update the MAC address for the new router, IP is still the same
	Only tricks the switches
When the Active router fails the standby becomes the new active router.
	The old standby/new active will send gratuitous arp messages so switches will update their MAC addr tables
FHRP is non preemptive by default, if the old Active comes back it will become standby not the active
	This can be configured to change
Types of FHRP
	Hot Standby Router Protocol (HSRP)
		Cisco Proprietary
			Cisco is H(SRP)ot G(LBP)arbage
		Active and Standby router
		Version 1 and 2, Version 2 adds IPv6 
			V1 and V2 are not compatible
			V1 multicast 224.0.0.2
			V2 multicast 224.0.0.102
		Virtual MAC Address
			V1 0000.0c07.acXX (XX = group number)
			V2 0000.0c9f.fxxx (XXX = group number)
	Virtual Router Redundancy Protocol (VRRP)
		Open standard
		Master/Backup
		Multicase = 224.0.0.18
		Mac = 0000.5e00.01XX 
		VRRP allows for assigning physical int IPs as the virtual IP addr
		Preemption is enabled by default
			Preemption allows the higher priority to take over even if current router is down
			**Scenario A**
				No preempt on both routers.
				Router A fails and router B takes over active role. But when router A is up, Router B remains active because there is no preempt for both.
			**Scenario B**
				Preempt on Router A only.
				Router A fails and router B takes over active role. When router A goes up, Router A will take over active role because it has preempt.
	Gateway Load Balancing Protocol (GLBP)
		Cisco Proprietary
			Cisco is H(SRP)ot G(LBP)arbage
		Load balances among multiple routers within a single subnet
			Active Virtual Gateway is selected
			Up to 4 Active Virtal Forwarders are assigned by the AVG
			Each AVG is the default gateway for the portion of hosts in the subnet
		Multicast - 224.0.0.102
		MAC addr - 0007.b400.XXYY (XX = GLBP group number, YY = AVF number)
### IPv6
2^128 addresses available
Shortening
	Only Leading 0s can be removed
	Consecutie quartets of all 0s can be replaced with double colon (::)
		This can only be done once in an address
8 Quartets in total
IPv6 global unicast
	Enterprise typically recieve /48 block
	Subnets typically use /64 block
	First 3 quartets are global routing prefix assigned by ISP
	4th quartet is used as VLAN identifier
	GGGG:GGGG:GGGG:VVVV:XXXX:XXXX:XXXX:XXXX/64
	To identify the prefix length, count the bits
	1 digit is 4 bits so count to the prefix length
EUI-64
	Extended Unique Identifier
	Method of converting a MAC addr into a 64 bit interface identifier
	The interface identifier can become the host portion of the /64 IPv6 addr
	How to do it
		1. Divide MAC addr in half
			1234 56 | 78 90AB
		2. Insert FFFE in middle
			1234 56*FF FE*78 90AB
		3. Invert 7th bit
			*Each hexa digit is 4 bits*
			*So second digit is the modified digit*
MAC address types
	UAA - Universally Administered Address
		Manufaturer made
	LAA - Localled Administered Address
		Admin programms
	Identified by the 7th bit or U/L bit
		0 = UAA
		1 = LAA
IPv6 Types
	Global unicast 
		Public addresses - expected to register them
	Unique Local 
		Private addresses that cannot be used over the internet
		Can be used freely within internal networks
		Cannot be routed over the internet/ will be dropped
	Link Local 
		Automatically generated on IPv6 interfaces
		FE80::/10
			Only FE8 
		Only used for communication within a single subnet
		USed for routing protocol peerings
		Next hop addresses for static routes
		Neighbor Discovery Protocol
	Multicast 
		One to many
		FFXX - multicast
		FF00::/8 for multicast
		All nodes - FF02::1 - 224.0.0.1
		All routers - FF02::2 - 224.0.0.2
		All OSPF  - FF02::5 - 224.0.0.5
		All OSPF DR/BDR  - FF02::6 - 224.0.0.6
		All RIP - FF02::9 - 224.0.0.9
		All EIGRP  - FF02::A - 224.0.0.10
		Scopes - indicate how far the packet should be forwarded in multicast
			Interface local - FF01 
				packet doesnt leave the local device, can be used to send traffic to service within the device
			Link local - FF02 
				Stays within local subnet
			Site local - FF05
				Forwarded by routers, limited to single WAN
			ORganization local - FF08
				wider in scope than site local/ entire org
			Global - FF0E
				No boundaries
	Anycast 
		One of one of many
		Multiple possible destinations, only sent to one
		Simply select a unicast and make it an anycast
		Any will show up in show int
::  = unspecified IPv6 addre
IPv6 default route is ::/0
::1 = loopback addr
Neighbor Discovery Protocol
	Replaces ARP
	2 types of msgs
		Neighbor Solicitation(NS)
		Neighbor Advertisement (NA)
	IPv6 has neighbor table instead of ARP table
		Link local is automatically created
		Age indicates how long ago the int recieved traffic in minutes
	Automatically discover routers
		Sends msg Router Solicitation(RS)
			Sent to multicast all routers FF02::2(All routers)
			Ask all routers on the local link to identify themselves
			All hosts do this
		Router Advertisement (RA)
			Sent to multicast all nodes(broadcast)
			Router announces its presence
			Router sends pegriodically
			Only routers do this
SLAAC 
	Stateless Address Auto-Configuration
	Auto learns IP addr from default gateway
Duplicate Address Dection - DAD
	Checks to see if other devices on the local link is using the same IPv6 Addr
	Host sends a NS to it's own IPv6 addr
		If it doesnt get a reply it knows the addr is unique
		If it does, then duplicate address msg shown
IPv6 Route types
	Directly attached static route
		Only exit interface is specified
		Cannot use if the interface is an ethernet interface
	Recursive static route
		Only next hop is specified
	Fully specified static route
		Both exit int and next hop are specified
	Network route
		Might use /64
	Host route
		uses /128
	Default route
		::/0
	Floating Static route
		When a static route's AD is set to higher than main route
		Used as a backup
### ACLs
![[2021-12-30_14-37-00-6237f02d1287cc812d1d0a4957ac7410.png]]
ACLs are configured in the global config mode
ACLs MUST be applied to the interface to be in effect
	One ACL per interface per direction
		Inbound one ACL
		Outbound one ACL
ACLs are made up of ACE - Access Control Entries
	ACEs apply in order from Top to bottom
	Once the packet matches one of the ACEs, it takes action and the rest of the ACL is ignored
ACLs have implicit deny in the end of it, implicit allow must be configured
Types
	Standard - Match based on source IP add only
		1-99, 1300-1999
	Extended - Match on Src/dst IP, Src/Dst port etc
		100-199, 2000-2699
Advantages of named vs numbered
	You can delete ACEs with the "no *number*" 
	With numbered you need to type "no whole entry"	
	When configuring/editing numbered ACLs, you can only delete the entire ACL
Extended ACL should be applied as close to source as possible
Extended ACL format
	source, mask,srcport, destination, mask,dstport
	src ip, mask, srcport, dst ip, dst mask are all that is required for ext acl
Standard ACL should be applied to as far as possible
Standard ACL format
	source address, wildcard mask
### Cisco Layer 2 Discovery protocols
Share info and discover info about neighboring devices
	Host name
	IP addr
	Device type
CDP is proprietaary
	Cisco Discovery Protocol
LLDP is industry standard
	Link Layer Device Protocol
Considered a security risk 
Cisco Discovery Protocol
	Enabled on cisco devices by default 
	CDP msgs are periodically sent to multicast MAC addr 0100.0CCC.CCCC - C is cisco
	When a device receives a CDP msg, it processes and discards the msg, it does NOT forward it to other devices
	Can convey VTP information
	CDP sent every 60 seconds by default
	CDP holdtime is 180 seconds by default - C is 3, 3x 60 is 180
		If not recieve msg for over 180s it is removed from CDP neighbor table
	CDPv2 Msgs are sent by default
	R- Router
	S - Switch
LinkLayer Discovery Protocol
	LLDP msgs periodically sent to multicase MAC 0180.C200.000E
	LLDP msgs are sent every 30s
	LLDP holdtime is 120s - 4 letters, 4x30 = 120
	LLDP has a reinitialization delay
		WHen LLDP is enabled it will be delayed by this timer
		2s by default
	R - Router
	B - Switch
### NTP
All devices have an internal clock
can see with show clock command
	show clock detail  - can see time source
		If it has * -  means time soure is not considered authoritative
Manually configured time is not scalable
	Manually configured time will drift
NTP clients request from NTP servers
	Distance from reference clock is called stratum
	Stratum 0 = atomic clock
	Stratum 1 - directly connected to strat 0 - primary servers
	Stratum 2+ - secondary servers
	Stratum 15 = Maximum value
Can also peer with devices at the same stratum to provide a more accurate time
	Symmetric active mode
DNS
	Msgs greater than 512 bytes are sent in TCP
### DHCP 
Can dynamically assign
	DHCP
	DNS
	Default gateway
DHCP Types - DORA
	Release
	Discover
		Broadcast msg asking for DHCP server
	Offer - how about this IP
		unicast frame to client MAC addr
	Request
		Broadcast- Client tells a server which IP it is using
		All DHCP servers send a offer so the client needs to choose one
	Ack  - Server confirms that client can use the address
DHCP Relay
	Large enterprises choose to use a centralized DHCP server
	Wont be able to hear broadcast msgs
	Can configure router as a DHCP relay agent
		Router will forward DHCP broadcast msgs to DHCP server
### SNMP
Two types of devices
	Managed Devices
		Devices being managed in SNMP
	Network Management Station (NMS)
		Devices that do the managing in SNMP
		SNMP (Server)
Three main operations in SNMP
	Managed devices can notify NMS of events
	NMS can ask the managed devices for information on current status
	NMS can tell the managed devices to change aspects of their configuration
SNMP Components
	NMS
		SNMP Application
			Provides an itnerface for the network admin to interact with
		SNMP Manager
			Software on NMS that interacts wth managed devices, 
				requests for informaiton
				Send configs etc
	Managed Device
		SNMP Agent
			Software running on the managed devices that interact with the SNMP Manager
		Management Information Base
			Structure that contains variables that are managed by the SNMP
			Information on the specified machine
				Each variable is identified by the Object ID (OID)
					Ex. Variables CPU, RAM etc.
	SNMP Messages transfer information from agent and manager
OID
	SNMP OID is organized into a heirarchical structure
SNMP Versions
	SNMPv1 
		Original
	SNMPv2c
		Allows NMS to retrieve large amts of info with a single request
		community strings - passwords
		Inform messages - notify network devices when Traps are recieved
		64 bit counters
	SNMPv3
		Secure version of SNMP that supports strong encryption and authentication
SNMP Message class
	Read
		Sent by NMS to read informaiton from the managed devices
		Get
			Request sent from the manager to agent to retrieve value of OID
		GetNext'
			Get the next available variables in MIB
		GetBulk
			more efficient GetNext
	Write
		Sent by NMS to change information on the managed device
		Set
			Change the value of one or more variables
		Notification
			Sent by managed devices to alert the NMS of particular event
				Trap
					Notif sent from agent to manager
					UDP, unreliable
				Inform
					Notification message that is acknowledged with a resp msg
		Response
			Msgs sent in response to a previous msg/req
				Response
### Syslog
Industry Standard for message logging
seq : time stamp : %facility-severity-MNEMONIC:description
Severity levels - Emergency ACE WIND
	0 Emergency
	1 Alert
	2 Critical
	3 Error
	4 Warning
	5 Notice
	6 Inform
	7 Debug
Logging Locations
	Console line - syslog msgs will be displayed in CLI by default.
		sent by default
	VTY lines - Displayed in CLI when connected via Telnet/SSH
	Buffer - Syslog msgs will be saved to ram
		Sent by default
	External sever - config syslog to send msgs to external server
		UDP 514
By default Syslog msgs will not be displayed with connected via Telnet/SSH
	Need a command to be used
	R1#terminal monitor
	Must be used everytime you connect via SSH
**Cisco Default Logging Configuration**
	• Logging service is enabled
	• Syslog server is disabled
	• Syslog default transport is UDP 514
	• Logging facility is local7
	• Informational (Level 6) messages and lower enabled
	• System messages are enabled on console
	• System messages are disabled on VTY lines (terminal monitor)
	• System messages are stored in local buffer memory
### Secure Shell
SSH
Only a single console line so the nuber is always 0
iOS images that support SSH will have K9 in their name
	Can also confirm with show ip ssh
	version 1.99 = supports v1 and v2
	Key length of at least 768 bits is require for SSHv2 
SSH config requirements
	1. Configure Hostname
		hostname *name*
	2. Configure DNS domain name
		ip domain name *domain*
	3. Generate RSA key pair
		crypto key generate rsa
	4. configure enable PW and username/pw
		enable secret *password*
		username *user* secret *pass*
	5. Enable sshv2
		ip ssh version 2
	6. Configure VTY lines
### FTP/TFTP
Most common use of FTP/TFTP is used to upgrade OS of a device
TFTP
	Only allows client to copy a file to or from a server
	No authentication
	No Encryption
	Best used in controlled environment to transfer small files quickly
	UDP Port 69
	TFTP Reliability
		Every data msg is ack'd at the destination
		Timers are used and if an expected msg isnt reeceived in time. the waiting device will resend its previous msg
Three phases
	Connection
		Sends a request to the server and server responds back
	Data Transfer
		server and client exchange TFTP msgs
		One sends data and the other sends ack
	Connection Termination
		After the last data msg has been sent a final ack is sent to terminate connection
FTP
	Uses port 20 and 21
	Username and pw used for authenticaiton, no encryption
	FTPS - FTP over SSL/TLS  can be used (upgrade to FTP)
	SSH File Transfer Protocol - SFTP can also be used(new protocol)
FTP has 2 types of connections
	FTP Control connection - is established and used to send FTP cmd and repliex
	FTP Data connection - When files are needed to be transferred, a seperate FTP data connection is made to transfer the file
FTP active mode data connection - Server initiates the data connection
FTP Passive mode data connection - client initiates the data connection
	Needed when client is behind a firewall
### NAT
Eases management of internet connectivity - only one IP to troubleshoot rather than multiple outside links
Conceals Private IP addr assignments from the internet
	From the outside, it looks like theyre all sent from one IP
RFC 1918
Source NAT
	Translates the src IP addr to src IP addr of the public interface
Static NAT
	Statically configuring one to one mapping of private IP addr to public IP addr
	inside local ip add is mapped to inside global ip addr
	inside local - IP addr from the perspective of the local network - private IP of src
	inside global - IP addr of the inside host from perspective of the outside - public IP of src
	outside local - IP addr of outside host from perspective of the local network 
	outside global - ip addr of outside host from perspective of outside network
		These two are usually the same
	If you try to map more than one Private IP to public IP, it will be rejected
	Allows for remote host to initiate a session from the internet
Dynamic NAT
	Router dynamically routes inside local to inside global as needed
	DHCP for NAT
	How it works in Cisco IOS
		ACL is used to identify whcih traffic should be translated
			If srcip is permitted by ACL, src IP will be trans
			If SRC IP is not perm, SRC IP will not be translated but DOES NOT DROP IT
	NAT Pool is used to definie the available inside global addr
	Dynamically assigned, but it is still 1:1
Port Address Translation
	NAT Overload
	Translates IP addr and Port number
	Uses unique port num for each communication flow
	16 bits = 65000 port numbers available
	Uses different port number but same inside global IP
	No one to one mapping, many to one
### QoS
IP phones have a internal 3 port switch
	1 port is uplink to external sw
	1 port is downlink to pc
	1 port connects internally to the phone itself
Allows PC and IP phone to share a single switchport
Seperate voice traffic and data traffic by using a voice VLAN
	PC1 will sent traffic untagged
	SW1 will use CDP to tell PH1 to tag PH1's traffic with VLAN11
POE(Power over Ethernet)
	Allows power sourcing equipment(PSE) to provide power to Powered Devices(PD) over an ethernet cable
	PSE is usually a SW and PDs are stuff like IP phones
	When a device is connected to POE-enabled port, the PSE sends low power signals and monitors the response and determines how much power the PD needs
	Power policing can be configured to prevent a PD from taking too much power.
	By default Switchport will assign maximum power to connected device
Made as Cisco Inline Power (ILP)
QoS is used to manage the following characteristics
	Bandwidth 
		Allows you to reserve certain amt of links bandwidth for specific kinds of traffic
	Delay
		Amt of time it takes traffic to go src -> dst = one-way delay
		amt of time to takes traffic to go src->dst->src = two-way delay
	Jitter
		Variation in one-way delay between packets sent by the same application
		Ip Phones have jitter buffer to proivde a fixed delay to audio packets
	Loss
		The % of packets sent that do not reach their destination
Acceptable standards for phonecall
	OWD - 150ms or less
	Jitter - 30ms or less
	Loss - 1% or less
If network device recieves msgs faster than it can forward them, it is placed in a queue
	Msgs are sent in FIFO
	If queue is full, new packets will be dropped
		Tail drop
Tail drop is harmful due to TCP global synchronization
	All TCP hosts simuetanously slow down the rate and ramp up the rate at the same time, leading to more congestion.
To prevent TCP global synchronization
	USe Random Early Detection(RED)
		When traffic in queue reaches a certain threshold, the device will start randomly dropping packets from select TCP flows
	Weighted RED
		Allows you to control whcih packets are dropped depending on the traffic class
Classification - organizes network traffic(PAckets) into traffic classes(categories)
	Ways to classify traffic
		ACL
		Network Based Application Recognition(NBAR)
			Performs a deep packet inspection
			Looks beyond layer 3 and 4
		PCP - Prioirty Code Point
			Only used when there is VLAN tag
			8 Possible values
			0 - Best effort
			1 - background
			2 - excellent effort
			3 - critical applications - call signaling traffic marked
			4 - Video
			5 - Voice - Actual call traffic mark
			6 - Internetwork control
			7 - Network control
		Differentiated Services Code Point (DSCP)
		Provides per hop behaviors
			Default Forwarding (DF) - best effort traffic
			Expedited Forwarding (EF) - low loss/jitter/latency - voice
			Assured Forwarding(AF) - set of 12 std values
			Class Selector (CS) - set of 8 std values
Trust Boundaries
	Defines where devices trust/don;t trust the QoS markings of received msgs
	If markings are trusted
		Devices will forward the msg without changing the markings
	If marks untrusted
		Device will change the markings according to the configured policy
Queue/Scheduler
	Device is only able to froward one frame out of an interface at once
	Scheduler is used to decide whcih queue traffic is forwarded from the next
	Prioritization allows the schedule to give certain queues more priority than others
	Class Based Weighted Fair Queuing -CBWFQ
		Weighted round robin while guaranteeing each queue a certain percentage of the int bandwidth
	Low Latency Queuing - LLQ
		Designates one or more queue as strict prioirty queues
		If traffic is in the queue, they scheduler will always take the next packet
		Might starve other queues
Traffic Shaping - buffers traffic in a queue if traffic rate goes over the configured rate
Traffic policing - drops traffic if the traffic rate goes over the configured rate
	Burst traffic can be configured to allow traffic over a short period of time
		instead of a stream it is sent in bursts
		
### Port Security
Allows you to control whcih SRC MAC addr are allowed to enter the SWport
When you enable port security with default settings,
	only one mac addr allowed
	allows first src mac addr that enters int
Can change max num of MAC addr allowed
Can by dynamically learned or manually configured
Port-security can only be enabled on swi mod acc or swi mod trunk
	Cannot be using DTP
Secure-up = port security is up and admin up
If a port is shutdown you need to shutdown then noshut it aka reset it
Err-disable recovery
	 Causes err-disable ports to reset after set amt of time
Violation modes
	Shutdown
		Generates syslog/SNMP msgs
		Violation counter is set to 1 when the interface is disabled
		Interface is disabled
		All traffic is discarded
	Restrict
		Switch discards traffic from unauthorized MAC addresses
		Syslog/SNMP msg for each unauth MAC
		Int is NOT disabled
		Violation is incremented by 1 for each unauth frame
	Protect
		Switch just discards traffic from unauth MAC addr
		Int is not disabled
		Does not generate msgs
		Does not increment violation counter
By default Secure MAC addr will not age out
	Default is Absolute
		Absolute - Secure MAC addr is learned, aging timer starts and MAC is removed after the timer expires
		Inactivity - Secure MAC addr is learned, aging timer starts but is reset everytime a frame is recieved
Sticky MAC addr
	Dynamically learned MAC addr that is added to running config
	It will be converted to static
### DHCP Snooping
Filter DHCP msgs on untrusted ports
Best practice - uplink ports are trusted, downlink is untrusted
If DHCP received on trusted port, forward as normal
If DHCP received on untrusted
	IF DHCP Server, discard
	IF DHCP Client
		Discover/Request - Check if src MAC and DHCP CHADDR fields match
			If match forward, else discard
		Release/Decline - Check if packet SRC IP nad receiving int match the entry in the DHCP snooping binding table 
			if match forward, else discard
DHCP Snooping Binding Table - when a client successfully leases an IP Addr from a server, create a new entry in the DHCP snooping binding table. 
Rate limitng - Can limit the rate at whcih DHCP msgs are allowe to enter an interface
	Over the limit will lead to errdisabled
DHCP Option 82
	Provides additional information about whcih DHCP relay agent received the client's msgs on which interface
	By default, cisco sw will add opt 82 to dhcp msgs they receive from clients even if its not a dhcp relay agent
		This can cause switches to drop dhcp msgs with opt 82 
### Dynamic ARP Inspection
Feature of SW used to filter ARP msgs recieved on untrusted ports
Best practice -  Ports connected to other network devices should be trusted, end hosts untrusted
DAI inspects the sender MAC and sender IP field of ARP msgs recieved on untrusted ports and checks that there is a matching entry in the DHCP snooping binding table.
DAI does not inspect on trusted ports
ARP ACLs can be configured to map IP addr/MAC addr for DAI to check
	useful for hosts that don't use DHCP
DAI default rate limiting is enabled on untrusted ports up to 15 packets per second
DAI burst interval - allows you to configure rate limiting like "x packets per y seconds"
Gratuitous ARP = ARP reply sent without receiving an arp request
	Sent to broadcast MAC addresses
Rate limiting limits the rate ARP msgs are received on an interface, not sent
DAI checks sender IP and MAC against DHCP snooping binding table and ARP ACLs


### LAN Architectures
Campus LAN Design
Two tier
	Access
		end hosts connect to
		Lots of ports
		QoS marking is done here
		Security services are performed here like DHCP Snooping and DAI
		Connection between Access are layer 2 aka Spanning tree is used to prevent looping
	Distribution
		Aggregate connections from access layer switches
		Typically boarder between layer 2 and layer 3
		Connections between distribution are layer 3
	Also called collapsed core as it omits the core layer
Distribution SW are connected to each other in full mesh
Access SW are connected in partial mesh
Three Tier Campus LAN Design
	Access
	Distribution
	Core Layer
		Focus is speed( Fast transport)
		CPU intensive operations such as security, QoS should be avoided at this layer
		Core SW connect to the routers
		Layer 3 only
Data Directions
	North-south
		Access to distribution to core to internet
	East west
		traffic between servers in the same layer, traffic doesnt go out to the internet
Spine leaf architecture
	Designed for Data centers
	Due to the precedence of virtual servers, applications are often deployed in a distributed manner which increases the amt of East-West traffic in the data center
		Designed for east-west traffic, you can get to SW 1 to SW2 easily due to the increased paths
	3 tier arch led to bottlenecks due to bandwidth and different paths the traffic took
	Full Mesh topology
		Spine switches
			Each spine switch is connected to each leaf switch but not to each other
		Leaf switch
			Each leaf switch is connected to each spine switch but not to each other
			Can connect to APIC and EPG
		Each server is connected through the same amt of hops.
		Loadbalanced/traffic is randomly taken
SOHO Network
	Office of a small company or a small home office with few devices
### WAN Architectures
WAN over dedicated connection (LEASED line)
	Each office(spoke) is connected by a leased line, direct line unshared to a center(hub)
WAN connection via Ethernet/Fiber
WAN connection over shared infrastructure (Internet VPN)
Leased line 
	Dedicated physical link
	Serial connections such as PPP or HDLC encap 
MPLS
	Multi Protocol Label Switching
	Shared infra
	Multiple VPNs created over the shared infrastructure using Labels
		Terms
			CE - Cusomter Edge Router
			PE - Provider Edge Router
			P Router - Provider Core Router
	MPLS/PE/P routers use Labels instead of IP to route traffic
	When PE routers receive frames from CE routers, they add a label to the frame
		label is located between layer 2 eth header and layer 3 ip header
		Sometimes called Layer 2.5 protocol
		Labels are used to forward packet
	CE routers does not use MPLS
	When Using MPLS Layer 3 VPN CE and PE routers peer 
	With Dynamic routing
		Office A CE connects with local PE and Office B connects with local PE, through OSPF all 4 routers share information
		Office A's CE will learn about Office B's routes through OSPF peering
	Or in a static routing - the PE connection will just be the next home and Service provider takes it from there.
	In a Layer 2 MPLS VPN, CE and PE routers do not form peerings
		in this topology, the logical tolopogy is the PE routers do not exist, it looks like a switch
		The CE routers peer with each other
		CE WAN interfaces will be in the same subnet
DSL
	Digital Subscriber line
	Provides internet connectivity over phone lines and can share the same phone line. 
	Modem required to de/modulate phone singal for internet access
Cable internet
	Internet access thru CAT(Cable Television) lines
	Cable modem required to convert data
		Can be sep device or home router
Redundant Internet connections
	1 connection to 1 isp = single home
	2 connection to 1 isp = dual homed
	1 connection to diff isp = multihomed
	2 connection to each diff isp = dual multihomed
Private WANs provides security
Site to Site VPN
	Used to connect two sites together over the internet
		VPN tunnel is created by encap the original IP packet with VPN header and new IP header
			With IPsec, original packet is encrypted
				Needs its own header as whole packet is encrypted
				Limitations of IPsec
					Doesnt support broadcast and multicast traffic, only unicast
					Configuring full mesh of tunnels is a labor intensive task, 
						Solved with DMVPN
	GRE
		Creates tunnels but does not encrypt
		Able to encapsulate wide variety of Layer 3 protocols
	GRE over IPsec
		GRE does not encrypt the original packet so no security
			Advantage of being able to encap a wide variety of msgs like broadcast and multicast
		Original packet has GRE header and new IP header, then encrypted and attached a IPsec and IP header
		`[ip packet] GRE header] IP header]`
		``[Encrypted]IPSec VPN header] IP header]
		Flexibility of GRE with security of IPSec
	DMVPN
		Cisco Developed
		Dynamic Multipoint VPN
		Allows routers to dynamically create a full mesh of IPsec tunnels without having to manually configure every single tunnel
		1. Config IPsec tunnels to a hub site
		2. Hub router gives each router info on how to form IPsec tunnel with other routers
Remote Access VPN
	Used to allow end devices to access the companys internal resources securely over the internet
	VPN software is installed on end devices
	end devices then form secure tunnel to one of the companys router/firewall 
	TLS
	One end device to site
### Virtual Machines
Hypervisor - used to manage and allowcate hardware resources to each VM
	Type 1 aka Native or Bare Metal - run directly on top of hardware 
		Also called VMM Virtual machine monitor
		ESXi
	Type 2 aka Hosted - Run on top of a Host OS(i.e. Windows)
		VirtualBox
Bins/Libs are software libraries needed by the Apps running in each VM
Traditional IT deployments
	On Prem
	Co-location
Cloud IT deployments
5 Essential Characterstics
	On Demand self service
		Consumer can provision capabilities without needing human interaction from each service provider
	Broad network access
		Capabilities are available over the network and accessed through thin or thick clients
	Resource Pooling
		Provider's resources are pooled to server multiple consumers, physical and virtual resources dynamically assigned according to demand
	Rapid elasticity
		Capabilities can be elastically provisioned and released
	Measured Service 
		Cloud systems automatically control and optimize resource use by measuring capability
		Cust and Provider can see their metrics
Three Service models
	IaaS
		Consumer is provided with the resources to do whatever they want
		Amazon EC2
	PaaS
		Consumer does not control the underlying infra but manages deployed applications 
		Customers can use to develop their own applications
	SaaS
		Software, Consumer does not manage or control the underlying cloud infra
		M365
		GSuite
Containers
	Software packages that contain an App and all dependencies for the contained app to run
	Runs on top of a container engine i.e. Docker Engine
	Lightweight, include only the dependencies required to run the specific App
	VMs need to run an OS on each VM, Containers can run only the app and dependencies
Container Orchestrator 
	Software platform for automating the deployment, management, scaling of containers
	i.e. Kubernetes, Docker Swarm
	VMs take more time to boot up due to OS
		Containers can boot in millisec
	VMs take more space
		Containers take little space
	VMs use more resources
		Containers use less resources due to shared OS
	VM and Containers are portable but Containers are smaller, faster.
	VM is more isolated, each VM runs it's own OS
		Containers are less isolated as they run on the same OS
### VRF
Virtual Routing and Forwarding
Used to divide a single router into multiple virtual routers
Commonly used to facilitate 
L3 int are configured to be in a specific VRF instance
Layer 3 concept
Allows this by having the router build multiple separate routing tables
Traffic in one VRF cannot be forwarded out of an interface in another VRF
	VRF leaking can be configured to allow traffic between VRFs
VRF - Commonly used by service providers to allow one device to carry traffic from multiple customers
	Each customers traffic is isolated from the others
	IPs can overlap without any issue
		Ex. Customer 1 on VRF 1 can use 10.0.0.0/24
		Cust 2 on VRF 2 can also use 10.0.0.0/24
With VRF you don't get Interface IP overlaps
	Without VRF two interfaces on the same router cannot be in the same subnet
	With VRF 2 interfaces on the same router can be in the same subnet
IPs addr needs to be reconfigured when you assign an interface to a VRF
Show ip route shows all routes
show ip route vrf customer
	Shows VRF's routing table
When pinging you need to specify the vrf
	`ping vrf customer1 192.168.1.1
### Wireless Fundamentals
Wireless Networks
	All devices within range recieve all frames
	Privacy within the LAN is a greater concern
	Carrier Sense Multiple Acces with Collision Avoidance CSMA/CA
		Used to facilitate half duplex commuinications
	Wireless communication is regulated
	Wireless signal coverage must be considered
		Absorbtion
		Reflection
		Refraction
		Diffraction
			Blind spots behind obstacle
		Scattering
Radio Frequency
	Amplitude - Max str of the electric and magnetic fields
	Frequency - number of up/down cycles per a given unit of time
		Hertz - cycles per sec
	Wifi bands
	2.4 Ghz
		1-14
		Best Channels are 1, 6, 11
	5 Ghz
Service Sets
	All devices in a service set share the same SSID
	Independent
		ad-hoc
		Two or more devices without an AP
		airdrop
	Infrastructure
		Basic
			One AP
			Clients connect to each other via AP but not directly to each other
			Other APs can use the same SSId but not the same BSSID(Basic Service Set ID)
			BSSID is basically MAC Addr
			Wireless devices associate with the BSS
			Area around the AP where the signal is available is the Basic Service Area(BSA)
		Extended
			Multiple APs
			Each BSS uses the same SSID but different BSSID
			SSID provides the network name
			BSSID identifies the actual access point
			Clients seemlessly pass between APs without having to reconnect
				Called Roaming
			10-15% Overlap between BSAs
	Mesh
		Mesh Basic Service Set
		Use 2 radios
			One to provide BSS to wireless clients
			One to form backhaul network to bridge from AP to AP
		One AP connected to wired network - Root AP -RAP
		Other APs are called Mesh AP -MAPs
All Devices in the same service set share the same SSID(Service Set ID)
	Does not need to be unique
Upstream wired network is called DS(Distribution System)
Each BSS/ESS is mapped to a VLAN on the wired network
Possible for an AP to provide multiple WLANs, each with unique SSID
WLAN is mapped to seperate VLAN and connected to wired network thru a trunk
Repeater
	AP in repeater mode can be used to extend the range of the BSS
	AP retransmits any signal it gets
		Single radio repeater must operate on the same channel as the ap but lower thruput
		two radio repeater cna recieve on one channel and transmit on another
Workgroup bridge - WGB
	Wireless client of another AP and can be used to connect a wired device to a wireless network
	uWGB - 802.11 std 
	WGB- cisco proprietary version
Outdoor Bridge
	use specialized antennas taht focus most ofthe signal power in one direction
### Wireless Architecture
802.11 Frame 
`[frame control|duration/id|Address1|addr2|addr3|SeqCtrl|addr4|QoS|HT control|Data|FCS]`
	Frame control - Provides information such as msg type and subtype
	Duration ID - Indicate time in microsec that the channel will be dedicated for transmission of the frame or identifier for the association
	Addresses - Up to 4 addresses can be rpesent
		Destination Addr - Final recipient of frame
		Source Address - Original Sender
		Receiver Address - Immediate recipient
		Transmitter Address - Immediate Sender
	Sequence Control - Used to reassemble fragments and eliminate duplicate frames
	QoS Control - Used in QoS to prioritize traffic
	High Throughput control - used to enable high thruput
		802.11n - High Thruput Wifi
		802.11ac - Very High Thruput Wifi
	Data 
	Frame Check Sequence - check for errors in frame
802.11
	Client initiates and make roaming decisions for themselves
	802.11 Association Process
		Three states
			Not auth, not associ
			Auth, not associated
			Auth and Associated
		Must be Auth and Asso to send traffic thru it
			Two ways to scan for a BSS 
				Acitve - station sends probe requests and listens for probe resp
				Passive- station listens for beacon msgs which are sent periodically by the AP
		Client ------------- AP
		probe request -->
		<-- Prob response
		Not Authenticated, Not Associated
		Auth request -->
		<--Auth response
		Authenticated, Not associated
		Asso request -->
		<--Asso Resp
		Authenticated and Associated
	802.11 Msg types
		Management Frames - Manage the BSS
			BAAP 
			Beacon
			Probe req/resp
			Auth
			Association
		Control 
			Used to control access to the medium - CSMA/CA
				Request to send
				Clear to send
				Ack msg
		Data 
			Actual data packets
Wireless AP Deployment methods
	Autonomous
		Self contained systems that don't rely on WLC
		Configured individually, no central management
		Autonomous APs connect to the wired network with a trunk link
		Data traffic in autonomous AP data goes directly to target
	Lightweight 
		Handle realtime operations like transmitting/receiving traffic, encrypt/decrypt traffic
		Management functions is handled by the WLC
			RF Management, security/QoS management, Client auth,
		Called Split-MAC architecture
		WLC used to centrally configure the lightweight APs
			WLC and Lightweight auth each other using digital certs
		WLC and LW AP use a protocol called Control And Provisioning of wireless access points (CAPWAP) to communicate
			Two tunnels created between each AP and the WLC
				Control tunnel UDP 5246
					used to config the AP and control/manage operations
					All traffic is encrypted by default
				Data tunnel UDP 5247
					Traffic from wireless client is sent through this tunnel to the WLC
					It does not go directly to wired network
					Tunnel traffic is not encrypted by default
						Encrypted with Datagram Transport Layer Security
						DTLS uses UDP
		Due to being tunneled to WLC, APs connect to access ports
		Trunk is needed to connect WLC to wired network
	Benefits to Split MAC Architecture
		Scalability - WLC simpler to build/support a network 
		Dynamic Channel assignment - WLC can automatically select the channel for each AP
		Trasmit power optimization -Automatically set the approrpiate transmit power
		Self-healing wirelss coverage - WLC can increase transmit power to avoid coverage holes
		Seamless roaming
		Client load balancing
		Security/QoS management
Lightweight AP Modes
	Local - Default mode where AP offers a BSS for clients to associate with
	FlexConnect- Offers one or more BSS for clients to associate with
		Allows AP to locally switch traffic between wired and wireless networks if tunnels to WLC go down
	Sniffer - Dedicated to capturing 802.11 frames and sending to a device running wireshark
	Monitor - Receiving 802.11 frames to detect rogue devices, can de-auth rouge devices
		Rouge Detector - Does not use radio, listens to traffic on wired network, receives a list of suspected rogue clients, correlates ARP msgs on wired net and info from WLC to detect rogue devices
	Se-Connect - Dedicated to RF spectrum analysis
	Bridge/Mesh Mode - Dedicated bridge between site and can be made a mesh
	Flex plus bridge - Flex connect and bridge together
Cloud based AP
	Autonomous AP centrally managed in the cloud
	Automatically configure when connected to  network
	Cisco Meraki
		Dashbaord can be used to configure APs, monitor the network, generate performance reports
		Like WLC
		Meraki tells each ap what to do
		However Data traffic is not sent to the cloud, only control/management info is sent to cloud 
		Data traffic is sent directly to wired connection
WLC Deployment models
	Unified - WLC is hardware in the central locaiton of the network
		Support up to 6000 APs
		Suitable for large enterprise campus
	Cloud-Based - WLC is a VM running on a server
		Support up to 3000 APs
	Embedded - WLC is integrated in switch
		Support up to 200 APs
	Mobility Express-  Integrated in an AP
		Ap containing WLC builds a CAPWAP inside of it
		100 APs
### Wireless Network Security
Authentication
	Only trusted user/devices should be given access to network
	Authentication Methods
		Open Authentication
			Client sends request, AP accepts it
			Auth/Asso with AP but its possible to require other securities
				i.e. Starbucks
		Wired Equivalent Privacy(WEP)
			Encryption RC4
			Shared key protocol
			40 bits in length or 104bits in length
			Not secure
			Only server sends challenge phrase
		Extensible Authentication Protocol(EAP)
			Authentication Framework
			Defines a set of auth functions that are used by EAP methods
			802.1x - port based NAC
				Supplicant - client
				Authenticator - AP
				Authentication Server - Device that receives client creds and permits/denies access
				In This model, Supplicant open auths to Authenticator, but to get access to network EAP auth is used
		Lightweight EAP (LEAP)
			Username and password to authenticate
			Mutual Auth by challenge phrase from client and server
			Dynamic WEP keys used, change frequently
			Considered vulnerable
			Used to replace WEP
			Cisco developed
		EAP-FAST(EAP Flex Authentication via Secure Tunneling)
			Cisco developed
			1.Protected Access Credential(PAC) is generated and passed from the server to client
			2. Secure TLS tunnel is established between client and auth server
			3. Client and AS communicate inside the tunnel to auth
		PEAP (Protected EAP)
			Like EAP-FASt, uses a TLS tunnel
			Uses a digital certificate instead of PAC
			Only AS needs Certificate
		EAP-TLS
			PEAP only requires the AS to have certificate
			EAP-TLS requires a cert on the AS and every client
			Digicert is exchanged between AS and Client, both mutally authenticate each other
				Don't need to authenticate inside the tunnel
Encryption
	Traffic sent between client and APs should be encrypted
	Devices on the WLAN use the same protocol
		Each client use a unique encryption/decryption key
	Group key used by the AP to send traffic to all its clients
	Integrity Check Methods
		Temporal Key Integrity Protocol - (TKIP)
			MIC is used to protect integrity of messages
				MIC includes the  sender MAC addr to identify frame sender
				Timestamp is added to prevent replay attack
			Key mixing algorithm is used to create a unique WEP key for every frame
			Initialization vector is doubled to 48 bits
			TKIP sequence number is used to keep track of frames
		Counter/CBC-MAC Protocol -CCMP
			Provides Encryption and Integrity
			Requires hardware
			AES countermode encryption
			Uses CBC_MAC as MIC
		Galois/Counter Mode Protocol - GCMP
			Allows higher data throughput than CCMP
			AES countermode encryption
			GMAC as MIC
Integrity
	Ensures msg is not modified
	Message Integrity Check (MIC)
Wifi Protected Access
	WEP
		RC4
	WPA
		TKIP provides encryption/MIC
		802.1X auth(enterprise) or PSK(Personal)
	WPA2
		CCMP
		802.1x(enterprise) or PSK (Personal)
	WPA3
		GCMP provides encryption/MIC
		8021.x or PSK(personal)
		Protected Management Frames - PMF, protects 802.11 management frames from eavesdropping.
		SAE - Protects 4 way handshake 
		Forward secrecy - prevents data from being decrypted after it has been transmitted
Support two auth modes,
	Personal mode - PSK is used for authentication
		4 way handshake is used for authentication, PSK is used to generate encryption keys
	Enterprise Mode - 802.1X used with authentication server
### Wireless Configurations
WLCs only support Static LAG, no PAgP or LACP
WLC GUI cannot be connected through SSH or Telnet, Must use HTTP or HTTPS
SVI for each vlan - default gateway for the subnets
Option 43 IP XXXX - Used to tell APs the address of their WLC
If the Regulatory domain of the country specified in the WLC config doesnt match the regulatory domain of the AP, the AP will not be able to join to the WLC
Auto RF - allows WLC to automatically select which channels to use and how much power to use
	Allows for RF cell optimization
WLAN Characteristics
	• WLAN ID, Profile Name and SSID
	• Wireless Security: Open, WPA2-PSK, WPA2, Guest
	• DHCP Source: Controller / Server / Router
	• Radio settings: 802.11n, 802.11a, 802.11g
	• Quality of Service: Platinum, Gold, Silver, Bronze
WLC GUI
	Controller Tab 
		Interfaces - logical interfaces on WLC
		Port- physical port
WLC Ports are physical ports that cables connect to
	Service port 
		Dedicated management port
		Only supports one VLAN
		Must connect to switch access port
	distribution system port
		network ports that connect to the distribution system(wired network)
		Used for data traffic
		Usually connected to trunk ports
	console port 
	Redundancy port - used to connect to another WLC to form a HA pair
WLC interfaces are logical interfaces within the WLC
	Static Interfaces
		Management interface
			Management traffic such as telnet, ssh, http, radius auth
			CAPWAP is formed to/from here
			Communicates with other WLCs
		Redundancy management interface
			Standby WLC management
		Virtual Interface
			Used when communicating with wireless clients to relay DHCP requests, perform client web auth etc
		Service Port interface
			Interface is bound to it
			for out of band management
			Physical interface
			Only interface available while booting
	Dynamic Interface
		Used to map WLAN to VLAN
			Traffic from internal WLAN will be sent to wired network from WLC's internal dynamic VLAN interface
		Used for client data
		User defined
Lightweight Access Point(LAP)
	When there isnt a centralized Wireless LAN Controller(WLC), you can manage each individual AP as it is booted up into LAP mode
	Default of cisco WAPs

### Cisco WLCs
Controller Tab
	Create new interface
	interface name
	Vlan id
WLAN tab
	Creating a new WLAN
		click new, 
		Select type of WLAN
		Profile Name
		SSID 
		WLAN ID
	General Tab
		Change interface 
		SSID change
	Security Tab
		Layer 2 security features
			None - Open auth
			WPA+WPA2 - 
			802.1x - EAP with dynamic WEP
			Static WEP - static shared WEP
			Static WEP+ 802.1x - Shared WEP OR EAP
			CKIP - Enables Layer 2 security using CKIP
			None+ EAP Passthrough - Uses open auth combined with remote EAP Auth
			PSK can be ASCII or Hex
		Layer 3 Security
			None - Disables regardless of Layer 2 selection
			IPSec  - 
			VPN Pass-through - Allows client to establish connection with specific VPN server
			Web authentication - Username and passwd through network
			Web passthrough - Direct access for guest lans without user/pass, warning or statement
			Conditional/Splash web redirect- require 802.1x layer 2 auth
	QoS 
		Platinum - Voice
		Gold - Video
		Silver  - Best effort/Default
		Bronze - Background
Clients Tab
	Shows IP addr
	AP associated with
	SSID using
Wireless Tabs
	List of APs joined on the WLC
CPU ACLs
	Used to limit access to the cPU of the WLC
	Limits whcih devices can connect via HTTP/S, Telnet/SSH, retrieve information thru SNMP
	Only affects things that target the WLC
### Network Automation
![[2021-12-30_15-22-15-7653a9fa6d976deffa3a0ff8e3649b9e 1.png]]
![[2021-12-30_15-24-10-328a119ac8271f69bf1a8418049dead2 2.png]]
Advantages
	Test and deploy
	Centralized management
	Scalable
	Dynamic
	Faster 
	Scripting
	logical
	Orchestrated - multiple tasks can be done at once 
SDN
	Software defined networking
	Functions divided into three planes
Data Plane/Forwarding plane
	Forwarding user data/traffic from one int to another 
Control plane
	Forwarding Decisions
	MAC addr, Routing table, ARP Table, etc
	Controls what the data plane does
	Performs Overhead work
		OSPF info, ARP msgs, STP info
Management Plane
	Protocols used to manage/configure devices
	SSH/Telnet
	Syslog 
	SNMP
	NTP
Operations by the management and control plane are usualyl managed by the CPU
Not desirable, usually specialized hardware ASIC(Applicaiton-Specific)
Tables are stored in a memory called TCAM
Data directions
	Southbound interface (SBI)
		Communications between controller and network devices it controls
		Consists of communication protocol and API
	Northbound interface (NBI)
		Allows us to interact with the controller, access the data  it gathers about the network, program it etc.
		REST API (Representational State Transfer) API - type of API
			USed on controller as an interface for  apps to interact with it
### JSON, XML, YAML
Data Serialization
	Process of converting data into a standardized format/structure that can be stored
Serialization - allow us to represent variables with text.
JSON
	Less secure, less bandwidth than xml
	Returns data in form of object that contains key value pairs
	Open file format
	Open Data interchange format
	Whitespace is insignificant
	Start and stop are `[]`
	Four primitive data types
		String
			Text value - surrounded by double quotes " "
		Number
			Numeric value - not surrounded by quotes
		Boolean
			Only two possible values, true or false not surrounded by quotes
		Null
			intentional abscence of object value
			null - no quotes
	Two structured data type
		Object
			unordered list of key-value pairs
			Object surrounded by curly bracket ``{ }
			key is a string
			value is any valid JSON data type
			key and value sepeated by colon ``: 
				``{key : value}
			Each key:value pair is seperated by comma
			You don't need a comma after the last key:value pair
				``{ key : value , key:value }
			You can use an object as the value of a key:value pair
				Objects in object is called nested object
		Array 
			Series of values separated by commas
			Values don't need to be same data type
			Surrounded by bracket  `[ ]
			Seperated by comma ,
				``{ key : [ array, array, array ] }
XML
	Whitespace is insignificant
	Used by REST APIs
	``<key> value </key>
	uses `[]`
YAML
	Data serialization language
	Used by Ansible
	Whitespace is SIGNIFICANT
	YAML Files start with three hypens `---`
	one hyphen used to start a list `-`
	keys and values represented as key:value
### REST APIs
CRUD
	Create
		Make new variables and set their initial values
	Read
		Retrive value of a variable
	Update
		Change value of a varible
	Delete
		Delete Variable
HTTP
	POST
		Make new variable
	GET
		Retrieve variable
	PUT/PATCH
		Change value of variable
	DELETE
		Delete variable
HTTP Response
	First digit indicates the class
	1xx - informational 
		Request received, continuing
	2xx - successful
		successfully received, understood and accepted
	3xx - redirection
		Further action needs to be taken in order to complete the request
	4xx - client error
		request contains bad syntax and cannot be fulfilled
	5xx - server error
		request was valid but server unable to fulfill it
REST
	RESTful architecture states
		Uniform interface
		Client-server
			Client uses API clals/HTTP requests to access resources on the server
			Seperation between client and server means they can both change and evolve independently of each other
				When client/server interface changes, connection must not change
		Stateless
			Each API exchange is a separate event, independent of all past exchanges
			Each new request is a new session
		Cacheable or non-cacheable
			Caching - storing data for future use
				Cacheable resources must be declared as such
		Layered System
		Code on demand
### Software Defined Networking
![[2021-12-30_15-02-09-937ce4d913819135252614e55ffcd74e 1.png]]
![[2021-12-30_15-15-54-29aef91d882ac0abca617da3b5993070.png]]
Moves control plane from physical individual devices to an abstract software layer(Control layer)
Decouples control plane and data plane
SDN controller is centralized control plane with policy engine
Network infrastructure provides data plane forwarding
The control plane decides how data is managed, routed, and processed, while the data plane is responsible for the actual moving of data. This used to be one device(the switch/router) but has been separated. Control plane decides how the packets should be routed, data plane actually does the routing
Three characteristics of Network overlays
	Virtual Topology
	Encapsulation
	IP address isolation
SBI - used for comms between controller and network devices it controls
NBI - allows us to interact with the controller
Layers
	Application layer
		Contains scripts/applications that tell the SDN controller what network behaviors are desired
		You control this
	Control Layer
		Contains the SND controller that receives and processes instructions from the applicaiton layer
		Centralized management and network intelligences
		Only processes the commands given and decides how to implement i.e. sending actual CLI commands
	Infrastructure layer
		Contains network devices that are responsible for forwarding messages across the network
		Network appears as single switch
		This is the actual layer with physical devices
Cisco SD-Access is Cisco's SDN for automating campus LANs
	Application Centric Infrastructure - ACI - SDN for data center
		Network policies are defined here - management layer
	SD-WAN - SDN for automating WANs
Cisco Digital Network Architecture Center (DNA) Center is controller
Fabric
	Underlay - physical network of the devices and connections 
		Purpose is to support VXLAN tunnels of the overlay
			The switching fabric is a physical underlay designed for high-speed transport of east-west traffic within a data center.
		Three different roles for switches
			Edge nodes  - connect to end hosts
			Boarder nodes - connect to devices outside of the SD_Access domain
			Control nodes - use Locator ID Separation Protocol (LISP) to perform control plane functions
	Overlay - Virtual network built on top of the physical underlay
		SD-Access uses VXLAN
		There is a fabric overlay that is built on top of (or over) an underlay. An overlay is comprised of multiple virtual interconnects between endpoints.
		Network overlays are simply virtual interconnects aka encapsulation protocols
		Examples of Network Overlay
			VXLAN
			CAPWAP
			IPsec
	Fabric is used to refer to underlay and overlay
Brownfield - Add SD Access on top of existing network
	Only if Hardware/software supports it
	DNA center won't config underlay
Greenfield - New deployment
	Switches are all Layer 3 and use ISIS as routing protocol
	Links between switches are routed, don't need STP
	Edge nodes act as default gateway of endhosts
Cisco Trust Sec (CTS)
	Provides Policy control i.e. QoS, security policy
Cisco DNA Center has two main roles
	SDN controller in SD_Access
	Network manager in traditional network
	DNA Center is an application installed on server hardware
	Uses REST API with JSON
	Enabled Intent Based Networking(IBN)
		Allow engineer to communicate intent for network behavior and DNA center will take care of the rest
	Uses SNMP for information
### Ansible, Puppet and Chef
Configuration Drift
	individual changes made over the time causes a device config to deviate from the standard
	As engineers make changes, config can drift away
		Records are often not kept
Configuration Provisioning
	How config changes are applied to devices
	One by one config is not practical
	Ansible, puppet and chef is very good for mass config
Two essential components
	Templates
		Creates a template, values arent given
		ex. 
		` hostname {{hostname}}
		``!
		`interface gigabit 0/0
		``ip address {{Address}} {{ Mask}}
	Variables
		``hostname: R1
		`address : 192.168.1.1`
		`mask: 255.255.255.0
	Combine them both to get the correct config
Ansible
	Redhat 
	Written in python
	Agentless
		Doesnt require any special software
	Uses SSH to make changes
	Push model
		Uses SSH to connect to managed devices and pushes config changes to them
	Required text files
		Playbooks 
			Blueprint of automation tasks,
			YAML
		Inventory 
			 list of devices and their characteristics managed by ansible -written in INI, YAML, etc
		Templates
			Represents device config file but specific variable is not provided
			Written in Jinja2
		Variables
			List variables and values
			YAML
Puppet
	HTTPS 8140
	Written in Ruby DSL
	Typically agent based
		Can be run agentless where proxy agent runs in external host and proxy agent uses SSH to connect to managed devices and communicate
	Puppet server is called puppet master
	Pull model
		Clients pull config from puppet master
		TCP 8140
	Proprietary Language
	Requried Text Files
		Manifest 
			Defines desired config state of network device
		Template
			Used to generate manifest
Chef
	Ruby
	HTTPS 443 
	Agent based
	Pull mode
		TCP 10002
	Files use DSL (Domain Specific Language)
		Resources 
			Define config objects managed by chef
		Recipes
			Outline the logic and actions of tasks
		Cookbooks
			Sets of related recipes goruped together
		Runlist
			Ordered list of recipes that are run to bring a device to the desired configuration state
Salt
	Master: minion
	TCP 4505 4506
	Salt SSH
	YAML or Python
hello world