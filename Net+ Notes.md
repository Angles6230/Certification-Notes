# 1.0 Networking Fundamentals
## 1.1 Understanding the OSI Model
### Open Systems Interconnection Reference model
Layer 1 - Physical
	Cables, fiber, signal analysis
	Bits
Layer 2 - Data Link
	MAC address
		Ex. NIC
	Switching layer
	Frame
	broadcast
	Link Layer Control - LLC
		Provides Connection services
		Flow contorl
		Error control - when expected data frame wasnt recieved or corrupted checksum
	How is data sync'd?
	Isochronous - Network device uses common reference clock source and create time slots
	Synchronus - Network device agree on clocking method to indicate beginning and end of frames
	Asynchronus - Network devices reference their own internal clock
Layer 3 - Network Layer
	Packets
	routing layer
		Routed Protocols
			AppleTalk
			IPX
			IP
	Internet protocol (IP) only one that remains today
	Frames will be fragmented
	Mulitcast,unicast
	How should data be forwarded or routed?
	Packet switching - routing/data is divided into packets
	Circuit switching - dedicated communication link is established between two devices
	Message switching - data is divided into messages, msgs then stored and forwarded
Layer 4 - Transport
	Post office layer
	Information is too big to be sent in a single frame
	Pieced together in other side
	TCP and UDP 
		TCP - Transmission control Protocol
		UDP - User Datagram Protocol
	Routers, Load balancers, Firewalls
Layer 5 - Session 
	Communication between management devices
		Start, stop, restart
	Control protocols/tun protocols
	H.323
		Voice
	NetBIOS
		Used by computers to share files ove rthe network
Layer 6 - Presentation
	Character encoding
	Application encryption
	Often combined with applicaiton layer
	Data formatting - HTML, Javascript, Unicode, JPG
	Encryption - TLS, SSL
	HTML, XML, Javascript, ASCII, Unicode, IMG formats, TLS, SSL
Layer 7 - Application
	Layer we see
	Application services
	Service advertisement
	Remote Access
	Webbrowsing
	Email
	DNS, FTP, POP3, SSH, DNS, etc
Follow the Conversation 
	Application - mail.google.com
	Presentation   - SSL Encryption
	Session - link the presentation to the transport
	Transport - Encap in TCP
	Network - IP encap
	Data - Ethernet cable
	Physical - Electricity
Data Communication
	PDU - Protocol Data Unit
		Tranmission units
		Ethernet operates on a frame of a data
			Doesnt care whats on the inside
		IP operates on a packet of data
	TCP Segment
	UDP Datagram
### Data Encapsulation and decap
Ethertype field - used to indicate which protocol is encap in the pyaload of the frame
Layers 5, 6, 7 - Application layers
Layer 4 - TCP header | Application layers
Layer 3 IP header | TCP header | Application layer
Layer 2 Frame header | IP header | TCP Header | Appl Layer | Frame Trailer
Layer 2 frame encaps all the infor within and contains the preceding headers
Decapsulation
	Layer 1 Bits
	Layer 2 - frames
	Layer 3 - packets
	Layer 4 - Segment - TCP or Datagram - UDP
TCP Flag
	contained within the TCP header
	Sends bits that are within the header of the packet
	Each type of bit has a sequence and contains control info
	Flags control the payload
	Syn - Synchronize sequence numbers
	PSH - push data to the applicaiton without buffering
	RST - reset the connection
	FIN - Last packet from sender - finished
	PSH - Give data priority
	URg - process immediately
MTU - Maximum Transmission Unit
	Maximum IP packet to transmit but not fragment
	Fragmentation slows things down
	Requires overhead along the path
	Different hops can use diff MTU
	Can't automatically find out if ICMP is disabled
	Maximum size of Ethernet packet is 1500 bytes
	MTU is usually only set once
		MTU might be set for tunnel protocols
		If packet has Dont Fragement - DF set - routers usually respond with ICMP msg
	Troubleshoot using ping
	Ping with DF and force a maximum size of 1472
		1500 bytes - 8 byte ICMP - 20 byte IP add = 1472 bytes to use
	Windows: ping -f{ping with dont fragment} -l{length of data} 1472{length of byte you wanna use} 8.8.8.8{IP address}
		If it works it will be a regular IP ping
		If it doesnt work it will have a reply 
		"Packet needs to be fragmented but DF set"
	Unix: ping -D -s 1472 {IP ADD}
## 1.2 Network topologies and Network Types
### Physical Layout of network items 
Star
	Hub and spoke
	hub in the middle 
	Spoke is end host devices
	Switches are in the middle
Ring
	Older Token Ring
	Metro Area Networks 
	Wide Area Networks
	Dual Rings
		If something goes wrong you can send network backwards
		I.E. going clockwise - smt goes wrong, can go counter clockwise after looping back
	Built in tolerance
Bus
	Early LAN
	Coaxial cable was the bus
	Each end host was a stop
	One break in the cable and the bus stops
	Controller Area Network
		CAN Bus
Mesh
	Multiple links to same place
	Can be partially or fully connected
	Has redudancy, fault tolerance, load blancing
	Used in WANs for fully/partially meshed
Hybrid
	Combination of one or more physical topologies
	Most networks are Hybrid
Wireless Topologies
	Infrastructure 
		All devices communicate through an access point
	Ad hoc
		Devices communicate among themselves directly
	Mesh
		IoT
		Ad hoc devices work to form a mesh cloud
		Self form and self heal
			If one goes down, it fixes itself
### Network Types and Characteristics
Peer to Peer 
	All devices are clients and servers
		Everyone talks to everyone
	Easy to deploy
	Low cost
	Difficult to administer and secure
Client Server
	Central server
	Clients talk to the server
	No Client to client communication
	Adv
		Performance
		Administration
	Disadv
		cost 
			Software, hardware
		Complexity
LAN - Local Area Network
	A bdlg or group of bldg
	High speed
	Ethernet and 802.11 wireless
MAN - Metropolitan Area Network
	Network in  a city
	Larger than LAN, Smaller than WAN
	Metro-Ethernet
WAN - Wide Area Network
	Spanning the glob
	Connects LANs across a distance
	Slower than LAN
	Point to point serial, MPLS etc
	Terrestrial/non - Satellite links
	Dedicated Lease linke
		Connects two sites, more expensive bc customer doesn't share the line
	Circuit switched connection
		Connection only turned on when you need it
	Packet switched connection
		Dedicated lease but multiple people share the bandwidth
WLAN - Wireless LAN
	802.11 tech
	Mobility - limited within a building
	Expand coverage with WAPs
PAN - Personal Area Network
	Own Private network
	Cars
	Mobile phone connections to wireless headset
	Health items
CAN - Campus/Corporate Area Network
	Middle ground btwn LAN and MAN
	Limited geographical area 
		Grp of buildings
	LAN technologies but diff bldg
	your own fiber, no third party
		No extra fees
NAS - Network Attached Storage
	Multiple drives
	Connect to shared storage across the network
	file-level access
	Have to change entire file
		I.E. Change only 1 byte in a gb file - have to change entire gb
Storage Area Network - SAN
	Looks and feels like a local storage device
		Block level access
		Feels like a local storage
	Uses jumbo frames frequently
NAS and SAN both require a lot of bandwidth - dedicated storage network
Multiprotocol Label Switching - MPLS
	Communication through WAN but uses labels 
	any type of connection through mpls
	Routing decisions are easy
	Ready to network type of WAN
	Any transport medium, any protocol
	Pushing and popping
		Labels are pushed onto packets as they enter the MPLS cloud
		Labels are popped off on the way out
mGRE - Multipoint Generic Router Encapsulation
	used exclusively for Dynamic Multipoint VPN (DMVPN)
		DMVPN created for a use, then torn down when its not needed
			Dynamic mesh
	Common on cisco
SD-WAN
	WAn built for the cloud
	Software Defined WAN
	Data center used to be in one place - cloud has changed everything
	No need to hop through a central point
	Remote site automatically connects to a resource
### Service Related Entry point
Demarcation Point
	Point where you connect with the outside world
	Where you connect to the ISP
	Central location in a building
	Connect your CPE 
		Customer Premises equipment - customer prem
	Can be used to figure out if its your stuff or the providers stuff
Smartjack
	Network Inferface Unit - NIU
	equipment owned by the network provider
	Able to provide diagnastics and run tests remotely
	Alarm Indicators
### Virtual Network Concepts
VNetwork 
	Migrate 100 physical servers into one physical server with 100 virtual servers
	Replace physical network devices with virtual versions
Network Function Virtualization - NFV
	manage from hypervisor
	Replace network devices with virtual versions
	Can easily deploy router/switch etc through hypervisor
Hypervisor
	Virtual machine manager - VMM
	HArdware management
		CPU
		Netowrking
		Security
	Single console 
		one pane of glass
vSwitch
	Virtual switch
	same as physical switch but virtual
vNIC
	Virtual NIC
	Virtual machine needs their own vnic
	config through hypervisor
### Provider Links
Satellite networking
	Communication to satellite
	Non terrestrial
	High cost
	50 mbs down 3mbs up
	Remote sites, hard to network sites
	High latency
	High frequencies - 2GHz
		Line of sight, rain fade
Copper
	Extensive installations
	easy to install/maintain
	Limited bandwidth due to physics
	WANs i.e. cable modem, DSL
	Often combined with fiber
	DSL - Digital Subscriber Link
		ADSL - Asymmetric DSL
			Speeds going into the homes are diff from the ones going out
		Uses telephone lines
		~10000 ft limitation from central office (CO)
		200MBs down 20 Mbs up
	Cable Modem/Broadband
		Transmission across multiple frequencies
		Coaxial
		Data Over Cable Service Interface Specification - DOCSIS
			Standard for cable modem
		High sped networking 
			50Mb/s + 
Fiber
	Frequencies of light
	High speed data communication
	Higher installation cost than copper
	more difficult to repair
	can send over long distances
	Large installations in WAN
	SONET Rings
	Wavelength Division Multiplexing - WDM
Metro Ethernet
	Metropolican area network
	Connect sites with ethernet
	but the provider will use fiber
## 1.3 Types of Cables and Connectors
### Copper
Fundamental to network communication
Twisted pair
	Two wires with equal transmit power
	Transmit +/- Recieve +/-
	The twist keeps interference away
	Pairs in same cable have different twist rates
	Cat 5
		100m max dist
		1000BAse-T
	Cat 5e
		Enhanced
		100m
		1000Base-T
	Cat 6
		10GBase-t
		55m unshielded
		100m shielded
	Cat 6a
		Augmented
		100m
	Cat 7
		10Gbase-T
		100M
		only shielded
	Cat 8
		40GBaset-T
		Shielded only
		30m
Coaxial/RG-6
	Two or more forms using same axis
Twinaxial
	Two seperate conductors 
	same as coax
	full duplex
	5m
	low cost
	low latency compared to TP
Structured Cabling
	ISO 11801 cabling standards
Termination standards
	TIA/EIA-568A
		WG/G/WO/B/WB/O/WBr/Br
	TIA/EIA-568B
		WO/O/WG/B/WB/G/WBr/Br
### Fiber
Transmission by light
no RF signal 
	Difficult to monitor or tap
	immune to RF interference
slow signal degrade
	Long distance
Singlemode
	Fiber core - smaller
	only allows one signal of light
	Up to 100KM 
	Expensive - stronger light source
	outside is protective ferrule
Multimode
	Short range
		up to 2KM
	multiple light signals
	fiber optic is bigger than size of light
### Connector Types
Fiber Connectors
	Local Connector(LC)
		Two different fibers inside 
		Usually send/recieve
		Push-down to lock
	straight tip (ST)
		push in and twist to lock
	subscriber connector (SC)
		Square connector
	mechanical transfer (MT) registered jack (RJ)
		Very small connector 
			Smallest amt of real estate
			Push down on top
	Angled physical contact (APC)
		ferrule end face polished at 8 degree angle
		low return loss
	Ultra-physical contact (UPC)
		Ferrule end face connected at 0 degree angle
		Facing each other directly
		high return loss
Coax
	RG6 - used for cable company to individual homes
	RG59 - between two nearby devices such as cable box to tv
	F-type connector
		Cable television
		Screw with tiny wire inside
		DOCSIS - Data Over Cable Service Interface Specification
		RG-6 cable
		Threaded
	BNC 
		Cable with twist and lock
	Twinaxial - two conductors, coaxial has one
Serial
	DB9 - 9 pins
	DB25 - 25 pins
RJ11
	Telephone/DSL
	6 position, 2 conductors(6P2C)
	6 spots only 2 spots used
		RJ14
			6P4C
RJ45
	Ethernet
	8P8C
Straight through patch cables
	Same pinout 
	connect layer 2 to different 
	DTE to DCE
Crossover cable 
	A and B on different sides
	Connect everything except switch to X
	DTE to DTE
	DCE to DCE
Data Terminating Equipment - (DTE)
	Does it think? Then its a DTE - Data Thinking Equipment
	endpoint equipment like laptops, servers, routers
Data Communications Equipment - (DCE)
	Switches, modems, hubs, bridges
media converters
	OSI Layer 1
	Changes one media type to another media type
		i.e. change copper to fiber then copper again
	Almost always powered
Transceivers
	Transmitter and receiver in same component
	Modular interface for receiver
	Duplex communication through two fibers
	Bi-directional
		Traffic in both directions with a single fiber
		uses two diff wavelengths
Transceiver type
	Gigabit Interface Converter (GBIC)
		Standard, hot-pluggable gigabit Ethernet transceiver (copper or fiber)
		Older version of SFP
	Small form-factor pluggable (SFP)
		Support up to 4.25 Gbps
		Mini-GBIC
		Compact, hot-pluggable optical module transceiver
	Enhanced form-factor pluggable (SFP+)
		Support up to 16Gbps
		Assume 10 for easy memorization
	Quad small form-factor pluggable (QSFP)
		4 channel SFP = 4 * 1 Gb/s = 4Gbps
	Enhanced quad small form-factor pluggable (QSFP+)
		4 channel SFP+ = 4 * 10Gbit/s = 40 Gbps
	QSFP/+ is bigger slot than SFP/+
###  Cable management
Demarcation point
	Entrance facility where your WAN connection enters
Patch panel/patch bay
	Allows you to move a connection with different interfaces rather than modifying cabling on the floor
	Can be punchdown on one or both sides with RJ45 on one side
Fiber distribution panel
	Permanent fiber installation
	Patch panel at both ends
	Distributes fiber
	Loops on the inside for future insurance
	loops as well as for not destroying fiber
Punchdown block
	Push/punch down the wire into the teeth and the connecters connect 
	66
		Analog voice and some digital links
		Left is patched to the right
		Wire and punchdown tool
	110
		wire to wire patch panel
		Supports Cat5-6 
		wires are punched into the block
	Krone
		Alt to 110 
		common to europe
		Analog and digitial
	Bix - Building Industry Cross Connect
		Created in 1970s by Northern Telecom
### Ethernet standards
Basebane 
	Single frequency using the entire medium
Broadband
	Single wire but many different frequencies
Copper
	10BASE-T
		two pair
			Cat3
			100m distance
		10Mbit
		Base - Baseband
		T - Twisted pair
	100BASE-TX
		Fast Ethernet
		100Mb/s
		Two pair
		Cat 5 min
	1000BASE-T
		Gigabit Ethernet over Cat 5
			Cat5 deprecated for Cat5E
		4 pairs 
	10GBASE-T
		4 pair
		Higher frequency of 500MHz
			gigabit ethernet used to use 125MHz
		Cat6
			Unshielded - 55m
			Shielded - 100m
			Cat6A - 100m shielded or unshielded
	40GBASE-T
		40Gb/s 
		4 Balanced twisted pair
		Cat8 min
		40m max dist
Fiber
	100BASE-FX
		Pair of multimode fiber
		Laser components
		400m - half-duplex
		2KM - fullduplex
	100BASE-SX
		S is noit single
		Less expensive
		LED optics
		300m Maximum dist
	1000BASE-SX
		Gb ethernet over shortwavelength laser
		Multimode fiber
		220 - 550m dependent on fiber type
	1000BASE-LX
		long wavelength laser
		multimode - 550m MAX
		singlemode - 5km max
	10GBASE-SR
		SR - short range
		multimode
		26 - 400m
	10GBASE-LR
		LR - long range
		single mode
		10km Max range
	Single Mode Fiber - (SMF)
		Longer distances, single mode of travel
	Multimode Fiber - (MMF)
		Shorter distances, multiple modes
Wavelength Division Multiplexing(WDM)
Bidirectional communication over single strand of fiber for multiple types of signals
	Coarse wavelength division multiplexing (CWDM)
		10GBaseLX4  
		Four 3.125Gb/s carriers at 4 diff wavelengths
	Dense wavelength division multiplexing (DWDM)
		Multiplex multiple OC carriers into a single fiber
		Up to 160 signals and increase thruput to 1.6Tb/s 
	Bidirectional wavelength division multiplexing (WDM)
## 1.4 IP Addressing Schemes
### Public vs. private
RFC1918
	Set aside private IP Add
		10.0.0.0-10.255.255.255/8
		172.16.0.0-172.16.255.255/12
		192.168.0.0-192.168.255.255/16 
Network address translation (NAT)
	Over 20bil devices on the internet
	IPv4 only supports 4.29bil addresses
	IP addr is changed as it goes through the network
	Public addr != private addr
Port address translation (PAT)
	Nat Overload
	Source Address Translation
	Uses private IP add and randomly assigned Port number to determine who is who
### IPv4 vs. IPv6
Automatic Private IP Addressing (APIPA)
	Automatically assigned addr when DHCP server is unavailable and IP is not assigned manually
	Link-local address
	Can only communicate to other local devices in the subnet
	No forwarding by routers
	169.254.X.X
		First and last 256 add are reserved
		functional is 169.254.1.0-169.254.254.255
	Automatically assigned
		Uses ARP to confirm the address isn't currently in use
Extended unique identifer (EUI-64)
	unique IPv6 static to a device
	Combine 64 bit IPv6 and MAC addr
		Split MAC into 2 24bit halves
		Put FFFE in the middle for 16 additional bits
		Invert 7th bit
		Turns burned in adr(BIA) into a locally administered 
		Sometimes called the universal/local bit(U/L bit)
	MAC addr
		EUI48
	64 bit IPv6 Subnet prefix:3byteMAC:FFFE:3byteMAC
		Unique IPv6 that cannot be recreated due to MAC addr
Multicast
	Only send packet to ppl who want it
	One to many of many
	Stock exchanges, Dynamic Routing updates
	Very specialized, carefully engineered
	IPv4 and IPv6 - mostly IPv6
Unicast
	One station sending info to another station
	One to one
	File transfers, web surfing
Anycast
	single destination IP add has multiple paths to 2 or more endpoints
	Communicate to only one device but can be any device -multiple options open
	Looks like unicast but cloned
	Anycast DNS
	Can be sent to closest device
Broadcast
	Send information to everyone at once
	One to all
	Limited scope - Broadcast domain
		Limited to IP subnet
	Routing updates/ arp updates
	Only IPv4 
		IPv6 uses multicast
Link local
Loopback
	address to yourself
	127.0.0.1 usually
	Can be entire 127.x.x.x range
	Used to make sure your own machine works
Subnet Mask
	Used by device to know what subnet it is on
	The IP neighborhood
IP Address
	Every device needs a unique IP address
	The IP address
Default gateway
	Address for the router on the local subnet
	Local post office address
### IPv4 subnetting
32 bit 
Subnet 
	Network Address - first IP addr of subnet
	First usable host addr
	Last usable host addr
	Network Broadcast - last IP addr of subnet
	Divided into network bits and host bits
Classless (variable-length subnet mask)
Classful
	Very specific subnetting architecture
		Not used since 1993
	A
		255.0.0.0
		1-127 
		0XXX
	 B
		 255.255.0.0
		 128-191
		 10XX
	 C
		255.255.255.0
		192-223
		110X
	- D
		- Multicast
		- 224-239
		1110
	- E
		- Reserved
		- 240-254
		- 1111
Classless Inter-Domain Routing (CIDR) notation
	How many bits are the network bits
	I.E 12 bits 11111111.11110000.00000000.00000000 = /12
### IPv6 concepts
128 bit address
	340 undecillion
	8 octets
Shorthand notation
	Groups of zeros can be abbreviated with a double colon "::"
		Only one set is allowed per addr 
			You can group 3 octets of zeroes into one double colon but you cant do it twice.
	Leading 0s can be removed
		Ex. 2600:DDDD:0001:0001 -> 2600:DDDD:1:1
IPv6 Subnet Masks
	First 48 bits/First 3 16ets are called the global routing prefix
		IANA:RIR:ISP:Locally assigned:Host ID 
		48 bits          :  16                    :      64
			regional internet registry = RIR
		16 subnet bits = 65536 total subnets
		2^64 hosts = 18 million/trillion hosts
Tunneling
	6 to 4 addressing
		Send IPv6 over existing IPv4 addr
		Creates an IPv6 addr based on the IPv4 addr
		No support for NAT
		requires dedicated/specific relay routers
	4 to 6 addressing
		IPv4 to IPv6
	Teredo
		Tunnel IPv6 through NATed IPv4
		End to end IPv6 through an IPv4 network
		No special IPv6 router needed
		Temp use until native IPv6 Networks take over
		Windows
	Miredo
		Opensource linux for teredo
Dual stack
	Run both IPv4 and IPv6 at the same time
	Interfaces will be assigned multiple addr types
	IPv4
		Config with IPv4 addr
		IPv4 routing table
		IPv4 dynamic routingprotocols
	IPv6
		config with IPv6 addr
		IPv6 routing table
		IPv6 dynamic routing protocols
No Broadcasts only multicasts and anycasts
Router advertisement
	Neighbor Soliciatation(NS)
		Sent as a multicast 
	Matching devices send back a Neighbor Advertisement(NA)
	Neighbor Discovery Protocol(NDP)
		No broadcasts
		Neighbor MAC discovery
		Replaces ARP
	Stateless address autoconfiguration (SLAAC)
		Automatically configure an IP addr without a DHCP server
		Duplicate Addres detection (DAD)
			no duplicate ip addr
		Discover routers and identify themselves
### Virtual IP (VIP)
Not Associated with a physical network adapter
Virtual machine - virtual internal router address
### Subinterfaces
## 1.5 Common Ports and Protocols, applications and encrypted alternatives
### IP protocol types
OSI Layer 4 protocol
Multiplexing -  use many different applications at the same time
Internet Control Message Protocol (ICMP)
	Text msging for your network devices
	Administrative requests
TCP - Transmission Control Protocol
	Connection Oriented Setup and close 
	Reliable delivery protocol
		Recovery from errors,recovers out of order messages
	Flow control  - can manage how much data is sent
UDP -User Datagram Protocol
	Connectionless - No formal open or close to the connection
	"unreliable" 
		No error recovery
		No reordering of data or retrans
	No Flow control - send it and pray
Generic Routing Encapsulation (GRE)
	Tunnel between two endpoints
	Encapsulate traffic inside of IP
		Endpoints appear to be directly connected
	No built in encryption
Virtual Private Network(VPN)
	Requires a concentrator 
		Encryption/decryption access device
		often integrated into the firewall
Internet Protocol Security (IPSec)
	Uses GRE as tunneling protocol 
		Generic Routing Encapsulation
	Security for OSI Layer 3
		Authentication and encryption for every packet
	Confidentiality and integrity/anti-replay
	Standardized
	Transport Mode 
		Seperate IP header from data, encapsulate data inbetween IPsec Header
		Only encrypt payload
		Client to site
	Tunnel Mode
		Give a new IP header, encap in IPsec headers and then inside is the actual original IP header and data
		site to site
		Entire packet encryption
	Authentication Header (AH)
		Hash of the packet and a shared key
		Adds a AH header to the packet header
		Uses hash on the destination end to compare and ensure integrity
		Provides authentication and integrity
	Encapsulating Security Payload (ESP)
		Encrypts the packet to hide it
		Adds header, trailer and integrity check value to ensure confidentiality 
		Provides Auth, integrity and confidentiality
### Common Ports
• File Transfer Protocol (FTP) 20/21
	20 for sending, 21 for session
• Secure Shell (SSH) Secure FTP 22
	file transfer, file access, file management over encrypted channel
• Secure File Transfer Protocol (SFTP) 22
	Secure Shell file transfer
• Telnet 23
	SSH but insecure
• Simple Mail Transfer Protocol (SMTP) 25
	Sends mail from your device
	Sends mail between mail servers
• Domain Name System (DNS) 53
• Dynamic Host Configuration Protocol (DHCP) 67/68
• Trivial File Transfer Protocol (TFTP) 69
	Provides no security features
	Very basic form of file sharing
• Hypertext Transfer Protocol (HTTP) 80
• Post Office Protocol v3 (POP3) 110
	Retrieves mail but only works on one device
• Network Time Protocol (NTP) 123
• Internet Message Access Protocol (IMAP) 143
	Retrieves mail but works on all devices
• Simple Network Management Protocol (SNMP) 161/162
	Network monitoring protocol
	Notifications from agents on Port 162
	Recieves requests on UDP 161
• Lightweight Directory Access Protocol (LDAP) 389
• Hypertext Transfer Protocol Secure (HTTPS) [Secure Sockets Layer (SSL)] 443
• HTTPS [Transport Layer Security (TLS)] 443
• Server Message Block (SMB) 445
	Provides shared access to files, directories and devices
	Used mainly by computers running windows - CIFS
• Syslog 514
• SMTPS 587
	TLS, SSL
• Lightweight Directory Access Protocol (over SSL) (LDAPS) 636
• IMAP over SSL 993
	SSL, TLS
• POP3 over SSL 995
	SSL, TLS
• Structured Query Language (SQL) Server 1433
	MSFT exclusive
• SQLnet 1521
• MySQL 3306
• Remote Desktop Protocol (RDP) 3389
	Microsoft proprietary protocol
• Session Initiation Protocol (SIP) 5060/5061
	Used for managing real time sessions - voice, video, im, etc
## 1.6 Use and Purpose of Network Services
### DHCP
Oct 1993 - Bootstrap protocol - BOOTP
	Required static database of IP and MAC to assign
DHCP - 1997
Provides clients with 
	IP
	Subnet mask
	Default gateway
	DNS server
	WINS server
	VOIP variables
4 Steps
	Discover - DHCP Discover sent from host to DHCP through broadcast
	Offer - DHC offer sent from server to broadcast as a way to get back to host
	Request - DHCP request sent from host to server through broadcast
	Acknowledgement - DHCP server sends ack to broadcast - host is configured
Scope
	IP address range used by DHCP server
	Subnet mask
	Exclusion ranges
		Excluded IP addresses
	DNS server
	Default gateway options
	VOIP servers
	DHCP Pool
		Grouping of IP addresses
	Scope is usually a single pool of IP addr
Dynamic assignment
	Large pool of addresses to give out
	Addr reclaimed after a lease period
	Automatic Assignment 
		DHCP server keeps a list of past assignments
		You can get same IP addr afterwards
Static assignment
	administratively configured
	Table of MAC addr
		Each MAC has a IP
	Also called IP/Addr reservation
Lease time
	IP address is temporary but it can seem perm
	Duration is configured by DHCP server
	Reboot - reallocates the lease
	Can also manually release the IP addr
	DHCP renewal
		T1 timer - Checkin with the lending DHCP server to renew the IP addr
			50% of lease time by default
		T2 timer - if original DHCP server is down, rebind with any DHCP server
			87.5% of lease time by default
DHCP relay
	IP helper/UDP forwarding
	Special configuration that allows a router to transfer DHCP requests to the DHCP server on another network
### DNS
Domain Name System - translate human readable names into computer readable IP addr
FQDN - Fully Qualified Domain Name
	The full URL, each part of the URL is a hierarchy
Record types
	Resource Records(RR)
		Database records of domain name services, over 30 types
	Address (A vs. AAAA)
		Defines IP address of a host
		A for IPv4
		AAAA for IPv6
	Canonical name (CNAME)
		alias, different name but same server
	 Mail exchange (MX)
		 Determines host name for the mail server
		 Only the name no IP addr
	 Start of authority (SOA)
		 In the beginning of the DNS server info
		 Describes DNS zone details
		 Structure
			 Name of the zone
			 Serial number
			 refresh, retry and expiry timeframes
			 Caching duration/TTL
	 Pointer (PTR)
		 Reverse of a A or AAAA record
		 Allows for a reverse DNS lookup
		 Resolves an IP addr to Host name
	Text (TXT)
		Human readable text info
		Useful public info
		Sender Policy Framework(SPF)
			Prevents mail spoofing
		Domain Keys Identified Mail (DKIM)
			Allows ppl to verify the public key
	 Service (SRV)
		 Find a specific service
		 Identifies the particular service's server
	 Name server (NS)
		 List name servers for a domain
		 Points to the DNS server that is authoritative for the domain
Global hierarchy
	Root DNS servers
		13 clusters
Internal vs. external
	Internal DNS
		Managed on internal servers
		Config and maintained by local team
		DNS for local devices
	External DNS
		Managed by third party
Zone transfers
	Replicate a DNS database
	Primary DNS server has a primary copy
	Sync to secondary server
	Triggered by referencing the serial number
Authoritative name servers
	Authoritative - DNS server is authority for the zone
	Non Authoritative - Does not contain zone source files, probably cached info
Time to live (TTL)
	configured on the authoritative server
	Specifies how long the cache is valid
	Long TTL can cause problems
DNS caching
	Store DNS info on your computer
	DNS resolver
	Recursive lookup
		Single request to local DNS server
		DNS server does the work then reports back
		DNS server keeps a cache to maintain performance
	iterative lookup
		Do all the queries by yourself, keep asking new servers until you find it
		DNS cache is kept on your own compuer
Reverse DNS/reverse lookup
	Provide DNS with IP addr, DNS provides FQDN
forward lookup
	Provide DNS server with FQDN, DNS server provides IP addr
### NTP
Network Time Protocol
Synchronize the clocks
	Log files, authentication info, outages
	Automatic updates
	Flexible
	Accurate
Stratum
	Some clocks are better than others
	Value of accuracy of time
	Stratum 0 = atomic clock
	Stratum 1 = synchronized to stratum 0, primary time servers
	Stratum 2 = sync to Stratum 1
Clients
	Requests time updates from servers and modifies itself accordingly
Servers
	Listens on UDP/123 and responds to requests from NTP clients
	Does not modify their own time
	Needs one clock source
	Usually selects lowest stratum source
## 1.7 Basic Corporate and Datacenter network Architecture
### Three-tiered
Core
	Center
	Web servers, databases, appli
	Almost everyone will need access to it
	Users don't connect to the core
Distribution/aggregation layer
	Midpoint between user and core
	Communication between access switches
	Provides redundancy and control of traffic
Access/edge
	Where users connect
	Access switch
	End station/printers
### Software-defined networking
Split functions into separate logical units
	Extend the functionality and management of a single device
	Built for the cloud
Management plane
	Used to monitor traffic conditions, status of network and allows admins to oversee the network
	Admins configure and manage the device
Application layer
	communication requests or info about network
Control layer
	Control Plane
	Manages action of the Data plane
	Routing table, session tables, Nat tables
	Controls where data will go
Infrastructure layer
	Data plane
	Where work is done
	Process the network frames and packets
	Forwarding, trunking, encryption, NAT
### Spine and leaf
Each leaf connects to each spine switch
	Mesh type but leaf doesnt connect to leaf, leaf to all spine, spine to all leaf
Software-defined network
Top-of-rack switching
	each leaf is on the top of the physical network rack
Simple cabling, redundant, fast
Additional switches may be costly
==Backbone==
### Traffic flows
North-South
	Traffic going to outside device
East-West
	Traffic between devices in the same data center
Branch Office
	Remote location
	Client devices only
On Premises data center
	Technology is located inhouse
	requires monitoring and cooling etc
Colocation 
	Multiple companies share a location
	Cages to prevent others from touching your gear
	Third party monitoring
### Storage area networks
Looks and feels like a local drive
Block level access aka efficient reading and writing 
	can only change small block rather than whole file
Requires a lot of bandwidth
	May use isolated network
Connection types
Fibre Channel over Ethernet (FCoE)
	No special networking hardware needed
	Switch tech, not routable
Fibre Channel
	Connect stores togeth in a highspeed network
		2 4 8 16 gb/s rates
	Servers and storage connect to Fibre Channel switch
		Server - initiator needs a FC interface
		Storage - target is commonly referenced by SCSI, SAS, SATA commands
Internet Small Computer Systems Interface (iSCSI)
	Send SCSI commands over an IP network
	IBM and  Cisco created , now RFC standard
	Makes remote disk look and operate like local disk
	No proprietary software needed
## 1.8 Cloud Concepts and Connectivity Options
### Deployment models
- Public
	- Available to everyone over the internet
- Private
	- Your own data center
- Hybrid
	- Mix of private and public
- Community
	- Several orgs share the same infra
### Service models
- Software as a service (SaaS)
	- On demand software
	- No local installation
	- Central management of data and applications
	- Ex. GoogleMail, O365
- Infrastructure as a service (IaaS)
	- Hardware as a service
	- Outsource your equipment
	- Still responsible for management and security
- Platform as a service (PaaS)
	- Someone handles the platform, you only ned to do the development
	- No direct control of data, ppl or infra
	- Salesforce
	- Make from available stuff
- Desktop as a service (DaaS)
	- Basic appl usage
	- Appli run on remote server
	- Virtual Desktop Infrastructure - VDI
	- Local device is just a keyboard, mouse and screen
	- Minimal operating system on the client
	- Network connectivity is a huge req
### Designing the Cloud
Infrastructure as code
	On demand computing power, click a button, stuff happens
	Describe the infra
	Modify the ifnra and create versions
	Use the description to build other infr instances
	Makes a perfect version every time
- Automation/orchestration
	- Automation is key to cloud computing
	- Entire applications can be instantly created/destroyed with the push of a button
	- Instances can follow the sun i.e. be online in a moment, offline in a moment
	- Security policies should be part of orchestration
 Connectivity options
	- Virtual private network (VPN)
		- Site to site VPN
		- Encrypt through the internet
		- Virtual Private Cloud Gateway 
			- Provides a point for users to connect into the VPC
		Virtual Private Cloud
			The private network
		VPC endpoint
			Direct connection between cloud provider networks
Multitenancy
	Multiple clients use the same cloud infra
	Looks like theyre the only one but its one of many
Elasticity
	Scale up or down as needed, save money on the fly
Scalability
	Applications also scale
	Access from everywhere
Security implications
	VM sprawl - built too many, dont know which VMs are related to which applications
		Security risk
	VM escape protection
	Private-direct connection to cloud provider
# 2.0 Network Implentations
## 2.1 Networking Devices, features and placement
### Networking devices
Switch
	Bridging done in Hardware
		Application specific integrated circuit - ASIC
		Layer 2 device
			Forwards traffic based on MAC addr
	May Provide Power over Ethernet (POE)
	- Layer 3 capable switch
		- Routing capability
		- one physical device but you still need 2 diff configs
- Router
	- Routes traffic between IP subnets
	- OSI layer 3 
	- Often connect diverse network - LAN, WAN, copper, fiber
- Hub
	- Multiport repeater
	- What goes into the hub is repeated to every other port
	- OSI layer 1
	- Half duplex
	- Less efficient as network traffic increases
- Access point
	- Simple a point to connect to the wired network from a wireless network
- Bridge
	- Makes forwarding decisions in software
	- Connects different physical networks
	- OSI layer 2
	- WAP - bridges wireless network and wired network
- Wireless LAN controller
	- Centralized management of Access points
	- Deploy new access points
	- Performance and security monitoring
	- Configure and deploy changes
	- Reports on use
- Load balancer
	- Distribute the load
	- Multiple servers but ensures that its seemless to the user
	- Large scale implementations
	- Fault tolerance
	- Configurable load
	- TCP, SSL offload
	- Caching
	- Prioritization
	- Content switching
- Proxy server
	- Sits between users and external network
	- Shields the user from the outside
	- Useful for caching, access control, URL filtering and content scanning
- Cable modem
	- Broadband
	Transmission over multiple frequencies
	Different traffic types
	Data on cable network - seperated by DOCSIS
	Uses cable
- DSL modem
	- Asymmetric Digital Subscriber line -DSL
		- Downloads are faster than upload ( asymmetric)
	Faster speeds the closer to the central office
	- Uses telephone lines
- Repeater
	- Receive signal , regenerate, resent
	- no decisions to make
	- Can be used to boost or connect one type of wire to another
- Voice gateway
	- Private Branch Exchange -PBX - Phone switch
	- Convert between VoIP protocols and traditional Public Switched Telephone Network Protocols(PSTN)
	- Often built into the VoIPPBX
- Media converter
	- Converts from one signal to another
	- i.e. fiber to copper and then back again
	- Almost always powered
- Intrusion prevention system(IPS)/intrusion detection system (IDS) device
	- Watch network traffic
	- IDS only alerts
	- IPS stops before it happens
- Firewall
	- Filter traffic by port number or application
	- Application aware - NGFW - Next Generation
	- Encrypt traffic
	- Can also be layer 3 devices
		- Provide NAT
		- Dynamic routing
- VPN headend/concentrator
	- Purpose built encryption/decryption access device for VPN en/decrypting
	- Can also be software based option
### Networked devices
- Voice over Internet Protocol (VoIP) phone
	- Replaced Plain Old Telephone Service(POTS)
	- Relatively complex embedded system
	- Each device is a computer
	- Usually powered by Ethernet(POE)
- Printer
	- Color and BW output
	- AIO - All in One, printer, scanner, fax machine
		- Connectivity varies depending on manufactuer
- Physical access control devices
	- Card reader, access with smart card
		- Needs connection to network
	- Biometric authentication
	Ethernet connected, IP addr thru DHCP or Static
- Cameras
	- CCTV
	- Motion detection, object detection, license plate detection
	- Often networked together and stored network
	- IP addressable
		- Multicast
- Heating, ventilation, and air conditioning (HVAC) sensors
	- Complex science, must be integrated into fire system
	- PC manages equipment
	- Network connectivity is crucial
- Internet of Things (IoT)
	- Require segemented network, limit security breaches
	- Refrigerator
	- Smart speakers
	- Smart thermostats
	- Smart doorbells
- Industrial control systems/supervisory control and data acquisition (SCADA)
	- Large scale, multi-site industrial control Systems (ICS)
		- PC manages equipment
		- Real time info, system control
		- Requires extensive segmentation
## 2.2 Routing Tech and bandwidth management concepts
Routed protocol 
	- protocol by which data can be routed - IP, IPX, AppleTalk
### Routing
- Dynamic routing
	-Determine best path to take, when changes occur, update the information
	-Link state 
		- Information is passed between routers related to connectivity
		- Speed of the connection - faster is better
		- Only triggered updates -link state is reported
		- Very scalable
		- Open Shortest Path First (OSPF) - interior gateway protocol
			- Cost based on link speed between routers
		- Intermediate System to Intermediate System (ISIS)
			- Like OSPF but not as popular
	-Distance vector 
		- Determined based on how many hops/routers is another network
			- Hop count as metric
		- Usually automatic
		- Good for smaller networks but don't scale well
		- Sends entire routing table during updates every 30-90s
		- Broadcasts updates
		- Enhanced Interior Gateway Routing Protocol(EIGRP)
			- Cisco only
			- uses hops and bandwidth and delay
		- Routing InternetProtocol (RIP)
			- Cost based on Hop
	-hybrid/Path vector
		- Combination of link state and distance
		- Determines best route on path, network policies or configured rule-sets
		- Border Gateway Protocol (BGP) - The only Exterior gateway protocol
			- backbone of internet
		- If a route goes down, other routes can fill in
	Interior - operate within an autonomous system
	Exterior - operate between autonomous system
	Metrics - lower the better
- Routing table
	- A list of directions for your packets
	- Happens in every place, workstations, routers, devices
	- A hop - a packet passes through a router
	- Next hop - destination gateway of next gateway
	- Don't need to know entire path, only next hop
	- Time to live - TTL
		- Counter in IPv4, everytime it hits a new router, counter goes down by one, at 0 it is discarded
		- Hop limit IPv6 
- Static routing
	- Route that is made
	- Doesnt change
- Default route
	- Default direction to go
	- Gateway of last resort
	- Go that way > rest of world
	- Destination of 0.0.0.0
	- Can simplify the routing process
- Administrative distance
	- Routing Metrics
		- Each protocol has its own way to calculate the best route
		- Metric values are assigned by each individual routing protocol
		- Use metrics to choose between redundant links
		- Lower is better
	- Used by router to determine which routing protocol has priority 
• Bandwidth management
	- Traffic shaping
		- Packet shaping
		- Control priority by bandwidth usage or data rates
		- Buffer traffic
		- Manage the Quality of Service (QoS)
	- Quality of service (QoS)
		- Different devices, some service is more important
		- Voice is real time - higher priority
		- Recorded streaming has a buffer - lower priority
		- Database application - lowest priority
## 2.3 Common Ethernet Switch features
Ethernet Frame
	Preamble - 7 bytes 56 alternating ones and zeroes - used for sync
	Start Frame Delimiter - 1 byte - designates end of preamble
	Destination MAc Addr 6 bytes 
	Source MAC addr - 6 bytes
	EtherType - 2 bytes - describes data inside the payload
	Payload - 46 - 1500 bytes - actual data
	FSC - 4 bytes - Frame check sequences - makes sure the frame is sent correctly
• Data virtual local area network (VLAN)
	Group of devices in the same broadcast domain, seperated logically instead of physically
	Trunking - IEEE 802.1Q
		Connect the same vlan on two different switches
- Voice VLAN
	- Data loves to congest network, Voice is sensitive to congestion
	- Each interface has seperate Data and Voice VLAN
	- Vlan dedicated for VoIP
- Port configurations
	- Port tagging/802.1Q
		VLANs are tagged with 4 byte identifier
			Tag Control Indetifier - TCI
			Tag Protocol Indentifier - TPI
			One VLAN is left untagged - native VLAN
	- Port aggregation
		- Link Aggregation Control Protocol (LACP) 802.3ad
		- Multiple interfaces act like one big interface
	Port config 
		Settings need to match on both sides
		Duplex - Half - send or recieve at one time/full - can send and recieve at the same time
		Speed - Speed of the link
		IP addr, VLAN int, Management Inter
		Trunking
	- Flow control
		- You never know how fast or slow traffic will flow
		- 802.3x - Pause frame
	- Port mirroring
		- Copy packets from one inter 
		- Used for packet captures
		- Copy packets from one interface to another interface for troubleshooting
		- SPAN - Switch Port ANalyzer connection
	- Port security
		- Prevent unauthorized users from connecting to a switch int
		- Based on source MAC addr
		- Configure a maximum num of source MAC addr on an interface
		- Can also configure specific MAC addr
	- Jumbo frames
		- Ethernet frames with more than 1500 bytes of payload
		- Up to 9216 bytes, commonly 9000 bytes
		- Increase transfer efficiency
		- Everything inbetween must support jumbo frame number though
	- Auto-medium-dependent interface crossover (MDI-X)
		- Automated way to electronically simulate a crossover cable connector even if using a straighthrough patch
		- If it is not supported you need to use the crossover
		- Workstation to switch - Straighthrough
		- Router to switch - Straighthrough
		- Switch to switch - Crossover
		- Router to router - crossover
		- Workstation to router - crossover
- Media access control (MAC) address tables
	- Lists MAC addr and interface for each device
	- Building the MAC addr table
		- Switch examines incoming traffic , adds MAC to table and identifies the interface
		- If MAC is unknown, info is sent to everyone on the network and wait for a response
		- Repeated when traffic comes in again
- Power over Ethernet (PoE)/ Power over Ethernet plus (PoE+)
	- Power provided on an ethernet cable
	- One wire for network and electricity
	- Power provided at built in power? Endspan, Inline power? Midspan
	- Power Modes
		- A - Power on data pairs, gigabit 
		- B - Power on spare pairs, 10 -100mb
	PoE IEEE 802.3af-2003
		15.4 watts DC/350 mA
	POE+ IEEE 802.3af-2009
		25.5 watts/600 mA
- Spanning Tree Protocol
	- Ensures a loop doesnt occur on the network
	- STP modes
		- Blocking - not forwarding to prevent loop
		- Listening - not forwarding and cleanign the MAC table
		- Learning - not forwarding and adding to the MAC table
		- Forwarding - Data passes through
		- Disabled - disabled
		- Shortest Path Bridging -(SPB)
			- Larger network environments
	Root Bridge  - Switch elected to act as a reference point for spanning tree
		Switch with the lowest bridge ID (BID)
			Made up of priority value and MAC addr
	Non Root Bridge - all other switches
	Root port - Port that is the port closest to root bridge
	Designated Port - Port that is available to forward traffic
	Blocked Port - Port that is blocked to prevent loop
	Link Cost - speed of link, lower link speed, higher the cost
	STP calculations based on Bridge ID and Path Cost
Rapid Spanning Tree Protocol - (RSTP)
	Decreased convergence from 30-50s to 6s
	Backwards compatible
- Carrier-sense multiple access with collision detection (CSMA/CD)
	- CS - Is there signal avail that we can use to send data?
	- MA - Multiple access - more than one device on the network
	- CD - Collision Detect - two stations talking at once detected
	- Listen for an opening and don't transmit if the network is already busy
		- Send data whenever you can - Request to Send - (RTS)
		- If collision occurs - jam - wait random timer
		- Wait random amt of time and retry  - If recieved RTS respond with Clear to Send (CTS)
- Carrier Sense multiple access/collision avoidance (CSMA/CA)
- WLAN uses CSMA/CA while ethernet uses CSMA/CD
• Address Resolution Protocol (ARP)
	Determine a MAC addr based on IP addr
	Maps IP addr to MAC
	arp -a
• Neighbor Discovery Protocol(NDP)
	No broadcasts 
	Multicast with IPv6
	can also be used with SLAAC - autoconfig IP addr without DHCP
	DAD - negates duplicate IPs
	Sends Neighbor Solicitation - NS
	Sends back Neighbor Advertisement - NA
## 2.4 Configure Wireless Settings and Standards
 • 802.11 standards
	- a
		- Original 802.11 standard
		- 5Ghz range
		- 54 Mbit/s
		- Smaller range than b
		- Oct 1999
	- b
		- 2.4Ghz
		- 11Mbit/s
		- Oct 1999
		- More frequency conflict
	- g
		- Upgrade to b
		- 2.4Ghz
		- 54Mbit/s
		- Backwards compatible with b
	- n (WiFi 4)
		- OCt 2009
		- Operates at 5 and 2.4 Ghz
		- 600 Mbits/s
		- 4 x MIMO
			- Multiple input, multiple output - increase power with multiple antennaes
			- 2x2:2 
			- AP antennas x Client Antennas:number of streams
	- ac (WiFi 5)
		- Jan 2014
		- Operates in 5Ghz band
		- Increased channel bonding - larger bandwidth usage
		- Denser signal modulation - faster
		- 8 x MU-MIMO
			- up to 8 MIMO streams
				- Download only
			- Nearly 7 Gbit/s
			- 3x3:2
	- ax (WiFi 6)
		- Feburary 2001
		- 5 GHz and 2.4Ghz
		- 1201 Mbit/s per channel
		- 8 Bi-directional MU-MIMO streams
			- 8X download and upload
			- 4x4:4
		- Orthogonal frequency division multiple access -OFDMA
			- Works similar to cellular communication
• Frequencies and range
	- 2.4GHz
		- Channel 1, 6, 11
		- 20 Mhz
	- 5GHz
		- A lot of frequncies
		- 20 Mhz
		- 40 Mhz
		- 80 Mhz
		- 160 Mhz
	- Spread Spectrum Wireless Transmissions
		- Direct Sequence Spread Spectrum - (DSSS)
			- Modulates data over entire range of frequencies using signals known as chips
			- Uses entire frequncy spectrum
			- Susceptible to enviornmental interference
		- Frequency Hopping Spread Spectrum - (FHSS)
			- Devices hop between preset frequencies
			- Increases security as hops occur based on a common timer
		- Orthagonal Frequency Division Multiplexing (OFDM)
			- Uses slow modulation rate with simultaneous transmission of data over 52 data streams
			- Allows for higher data rates while resisting interference between data streams
			- Channel bonding
		- Only DSS and OFDM are commonly used in WLANs
• Channels
	Groups of frequencies, numbered by IEEE
	Using non overlapping channels is optimal
	20, 40, 80, 160 MHz frequencies
	Combining channels allows for larger speeds
	- Regulatory impacts
• Channel bonding
	Grouping channels together to get better performance
High signal to noise ratio - good, good signal low noise
• Service set identifier (SSID)
	The Name of the network
	- Basic service set identifier
		- hardware address of an AP is the BSSID
		- Only one AP
		- Wireless network using a single WAP
	- Extended service set identifier (ESSID)
		- Network name shared across access points
		- Wireless network using multiple WAPs
		- Seamlessly switch from AP to AP
	- Independent basic service set (Ad-hoc) - (IBSS)
		- Two devices communicate directly to each other
		- No APs
	- Roaming
• Antenna types
	- Omni
		- Sticks - Signal is distributed evenly on all sides
	- UniDirectional
		- Focus the signal
		- Increased distance
		- Yagi antenna
		- Parabolic
			- Focus signal to a single point
• Encryption standards
	- WiFi Protected Access (WPA)
		- 2002, replaced WEP
		- TC4 with TKIP
		- Pre-Shared Key
		- WPA2
			- CCMP block cipher
			- AES and MIC 
			- Had a PSK bruteforce problem
				- Listen to 4way handshake
		- WPA3
			- GCMP
			- SAE  Simultaneous Authenatication of Equals(SAE)
				Everyone uses the diff session key even though its same PSK
				it creates a strong shared secret without needing to pre-share a key.
	- WPA/WPA2Enterprise (AES/TKIP)
		- Authenticate with auth server i.e. RADIUS
• Cellular technologies
	2G Networks
	- Code-division multiple access (CDMA)
		- Each call uses a different code, is then split up and transmitted into one channel
		- Verizon, Sprint
	- Global System for Mobile(GSM)
		- Mobile Networking Standard - 90% of the market
		- Allowed you to move from phone to phone using SIM
		- Multiplexing
		- Tmobile, AT&T
Communications (GSM)
	- Long-Term Evolution (LTE)
		- 4G technology
		- Converged standard based on GSM and EDGE - Enhanced Data RAtes for GSM evolution
		- LTE-A(Advanced)
	- 3G
		- GPS, Mobile TV, etc.
	5G 
		Eventually 10Gbit/s
		Slower speds of 100-900Mbits
		Significant IoT impact
# 3.0 Network Operations
## 3.1 Network Availability
• Performance metrics/sensors
	- Device/chassis
		- Temperature
			- Internal sensors
			- Early warning of excessive utilization or hardware issues
		- Central processing unit (CPU) usage
			- Measures perforance of the processor
			- Overall perf is based on the value
		- Memory
			- Operational resource
			- Running out of memory is bad
	- Network metrics
		- Bandwidth
			- Fundamental network statistic
			- Identify issues
		- Latency
			- Delay between request and response
			- Some is expected - laws of physics
		- Jitter
			- Real=time media is sensitive to delay
			- Time between frames
			- Too mcuh is a choppy voice call
			- Uneven arrival of packets
	Monitoring 
		Ensure issues are not real or solve them early
• SNMP - Simple Network Management Protocol -UDP/161
	Database of Data - MIB
	V1 - Original
	V2 - improved no encryption
	V3- Encryption
	- Traps - UDP/162
		- Most SNMP Operations expect a poll
		- Traps can be configured, when error occurs, alert automatically happens
	- Object identifiers (OIDs)
		- Number that references a value in the MIB
		- every variable has a corresponding OID
		- Common across devices, some manually define their own OIDs
	- Management information bases (MIBs)
		- Most metrics in MIB-II commands
		- Proprietary MIB may be available
• Network device logs
	- Log reviews
		- Traffic logs
			- View traffic information from routers, switches, firewalls etc
			- Very detailed
			- Important historical information
		- Audit logs
			- What did they do and when did they do it
		- Syslog
			- Standard for system message logging
			- Usually central logging reciever
			- Each log entry is labeled
	- Logging levels/severity levels
		- Not all alerts have same priority
		- 0 - emergency
		- 1 -alert condition
			- Correct immediately
		- 2 - critical condition
			- failure in the system
		- 3- error condition
			- Something is happening
		- 4 - warning condition
			- Error if action not taken soon
		- 5 - notice condition 
			- unusual but not error
		- 6 - information
			- normal operational msg
		- 7 - debugging
		- Low level
		- High level
		- Can be used as a filter
• Interface statistics/status
	- Link state (up/down)
	- Speed/duplex
	- Send/receive trafc
	- Cyclic redundancy checks (CRCs)
	- Protocol packet and byte counts
• Interface errors or alerts
	- CRC errors
		- Failed frame check sequence
		- May indicate bad cable or inter
	- Giants
		- Frames larger than 1518 bytes
	- Runts
		- Frames that are smaller than 64 bytes
		- Collision maybe
	- Encapsulation errors
		- Inconsistent configurations between switches
		- ISL or 802.1Q misconfig
• Environmental factors and sensors
	- Temperature
		- Devices need to be cold to work well
	- Humidity
		- High humidity - condensation
		- Low humidity - static
	- Electrical
		- Device and circuit load
	- Flooding
		- Water = bad
• Baselines
	Normal operation statistic 
	Used to compare and contrast to ensure something isnt out of the ordinary
• NetFlow data
	Gather traffic statistic from all traffic flows
	Shared communication between devices
	Probe and collector
		Probe - watches network
		Collector - Summaries are sent to collector
• Uptime/downtime
	Is it up or down
	How long?
## 3.2 Organizational Documents and Policies
 Plans and procedures
	- Change management
		- How to make a change
		- Documentation
		- Have clear policies
	- Incident response plan
		- Something happens how do you respond
		- Emergencies make ppl panic
		- Need documentation
			- Prep
			- Detect and analysis
			- Contain, eradicate, recover
			- Post incident activity
	- Disaster recovery plan
		- If disaster happens, something should be ready
		- How do you deal with it
		- Comprehensive plan
		- Recovery location, Data recovery method, application restoration, IT and employee availability
	- Business continuity plan
		- Continuity of Operations planning (COOP)
		- Alternative if something goes wrong
		- Must be documented and tested befroe smt actually happens
	- System life cycle
		- Asset disposal
		- Is information legally required to keep?
		- Don't want critical info in the trash or leaked
	- Standard operating procedures
		- Operational procedures
		- Know what to do when smt happens
		- Documentation is key
• Hardening and security policies
	- Password policy
		- Make your password strong
		- Increase password entropy
	- Acceptable use policy
		- What can you do on company time/company computers
		- Used by company to limit legal liability
	- Bring your own device (BYOD) policy
		- Employee brings own device
		- Is data protected?
	- Remote access policy
		- How do we control when theyre working from home?
		- Specific technical requirements
			- Encryption
			- Confidential credentials
			- Use of network
	- Onboarding and offboarding policy
		- Bringing someone in or sending someone off
		- Should be preplanned so it is detailed and nothing goes wrong
	- Security policy
		- Documentation of organization's IT security policies
	- Data loss prevention
		- Prevent data from being stolen
		- Detailed how data is transferred
		- DLP solutions can watch and alert for policy violations
• Common documentation
	- Physical network diagram
		- Follows physical wire and device 
		- How they are physically connected
	- Floor plan
		- Overlayed wired and wireless network
		- Documents where wires go
		- Used for planning
	- Rack diagram
		- Diagram of a rack describing which item is whcih
	- Intermediate distribution frame (IDF)
		-Passive cable termination
		Punchdown and patch panels
		Mounted on wall or flat surface
		Central location for all transport media 
		Extension of MDF, closer to the users
	- main distribution frame (MDF) 
		- Central point of the network
		- Usually in data center
		- Termination point for WAN links
		- Good test point
	- Logical network diagram
		- How things are connected in cyberspace
		- Use specialized software - visio, omnigraffle, gliffy.com
		- Useful for planning
		- High level views - WAN
	- Wiring diagram
		- ANSI/TIA/EIA 606 - standard for managing cables
		- which cables go to whcih ports
		- Cable labeling
		- Port labeling
	- Site survey report
		- Determine existring wireless landscape
		- Make the best possible connection
		- Work around existing frequencies
		- Heat maps
	- Audit and assessment report
		- Validate existing security policies
		- Internal audits
		- External audits
	- Baseline configurations
		- Point of reference over time
• Common agreements
	- Non-disclosure agreement (NDA)
		- Confidentiality between parties
		- Protects Confidential information
		- Can be unilateral or multilateral
		- Formal Contract
	- Service-level agreement (SLA)
		- Minimum terms for services provided
		- Used between customers and service providers
	- Memorandum of understanding (MOU)
		- Both sides agree on contents of memorandum
		- Informal letter of intent
## 3.3 High Availability and Disaster Recovery
Fault tolerance
	Maintain uptime in case of failure
	Adds complexity
	Single device fault tolerance
• Load balancing
	Some servers are active, some are on standby
	Share the load
	Take over incase of a failure
• Multipathing
	Multiple connections incase one goes down
	Port Aggregation
		Combine two ports together and increase bandwidth
		Still provides failover
• Network interface card (NIC) teaming
	Load Balancing/Fail Over (LBFO)
		Aggregate bandwidth
		but if one fails you have a failover
		Multiple NICs but look like one big one
• Redundant hardware/clusters
	- Switches
	- Routers
	- Firewalls
• Facilities and infrastructure support
	- Uninterruptible power supply (UPS)
		- Short term power
		- Enough time to just save 
		- Offline/Standby - small delay maybe
		- Line-interactive 
		- OnLine/Double-Conversion - always getting power from UPS so no switching process
		- Auto-shutdown, phoneline suppression
	- Power distribution units (PDUs)
		- Essentially a powerstrip for a rack
		- Monitoring and control
	- Generator
		- Long term backup power
	- HVAC
		- AC, Heat, Venting 
	- Fire suppression
• Redundancy and high availability (HA) concepts
	- Cold site
		- Barebones, need to move everything
		- No data
	- Warm site
		- Midway between hot and cold, some stuff
	- Hot site
		- Everything is there, ready to go very fast
	- Cloud site
		- Using a cloud provider for backup
	- Active-active 
		- Two devices, but use both
	- active-passive
		- Two devices installed and config
		- If one fails, passive takes over
	- Multiple Internet service providers (ISPs)/diverse paths
		- Multiple paths or isps for redundancy
		- May require more config
		- Failover process?
	- Virtual Router Redundancy Protocol (VRRP)
		- Virtual IP addr associated with the router
		- If physical router fails the virtual IP switches to another router
		- Gateway Loadbalancing protocol - (GLBP)
			- cisco proprietary
		- Common Address Redundancy protocol (CARP)
	- First Hop Redundancy Protocol (FHRP)
		- If default gateway fails, allows another router to take over as the next hop
	- Mean time to repair (MTTR)
		- How long it takes to get back up
	- Mean time between failure (MTBF)
		- Predict time between outages
	- Recovery time objective (RTO)
		- Amt of time it takes to get back to business
	- Recovery point objective (RPO)
		- Amt of data you need back up to start business
• Network device backup/restore
	- State
		- Revert it to previous state and use backup so you can still operate
	- Configuration
		- Every device has a config, back it up so you can restore if it fails
# 4.0 Network Security
## 4.1 Security Concepts
Confidentiality
	Encryption
	Who can see it
integrity,
	Hashing
	Has it been seen
availability
	redundancy
• Threats
	- Internal
		- Employees
	- External
		- Companies
		- Bad actors
• Vulnerabilities
	- Common vulnerabilities and exposures (CVE)
		- List of documented exploits and vulnerabilities
	- Zero-day
		- Undocumented exploit
• Exploits
	A weakness in the config/system
• Least privilege
	Only give what is necessary to do the job, no more
• Role-based access
	Only allow people who need it to do their job, not everyone
	You assign rights to roles, ppl get assign roles
• Zero Trust
	Don't trust anyone, every time you connect you need to reverify
	Most networks are open on the inside
• Defense in depth
	- Network segmentation enforcement
		- Make sure networks dont connect to another without a barrier i.e. IDS/IPS/Firewall
	- Perimeter network 
		- A barrier network/DMZ
		- Public access to public resources
		- Contains ways to prevent or slow down intrusion or malicious actors
	- Separation of duties
		- Ensure no one person can destroy everything
		- Split knowledge - half of safe combination
		- Dual control - two people must be present
	- Network access control
		- 802.1x Port based
		- Uses EAP and RADIUS
		- Disable unused ports
		- Disable spoofed/duplicate MACs
	- Honeypot
		- False target for malicious threats to target
		- Allows you to alert/understand threats method
• Authentication methods
	- Multifactor
		- More than one credential necessary to log on
	- Terminal Access Controller Access- Control System Plus (TACACS+)
		- Remote authentication protocol
	- Single sign-on (SSO)
		- Sign onto multiple services with one logon
	- Remote Authentication Dial-in User Service (RADIUS)
		- Centralize authentication for users
	- LDAP
		- Protocol for reading directories over IP network
	- Kerberos
		- Network Authentication Protocol
		- Given a ticket, authenticate once, just show the ticket
		- Mutual authentication client and server
	- Local authentication
		- Authentication stored on local device
		- Manual process
	- 802.1X
		- NAC
		- Prevents connection to network until EAP succeeds
	- Extensible Authentication Protocol (EAP)
		- Auth framework
• Risk Management
	- Security risk assessments
	- Threat assessment
		- Assess the situation
		- What can hurt you
	- Vulnerability assessment
		- Minimally invasive
		- Just poke around see whats up
		- What can be hurt
	- Penetration testing
		- Actually trying to break in and see what happens
		- How secure are you really
	- Posture assessment
		- Check if the device is up to standard
		- Can you allow it on the network?
	- Business risk assessments
		- Business assets that could be at risk
	- Process assessment
		- Is the way you do things dangerous?
	- Vendor assessment
		- How secure are the people you buy your stuff from? Can someone attack you that way?
• Security information and event management (SIEM)
	Congregate all your logs into one place and store them.
	Allows you to correlate data and find cause or patterns
## 4.2 Common Network Attacks
• Technology-based
	- Denial-of-service (DoS)/ distributed denial-of-service (DDoS)
		- Force a service to fail
	- Botnet/command and control
		- Large amts of computers being controlled to do bidding, 
	- On-path attack (previously known as man-in-the-middle attack)
		- Attack intercepting the information, acting as an inbetween
		- Redirects your traffic
		- DNS poisoning
			- Poisoning the DNS table so you think you're going to a legit website but you're not
			- Send fake response to valid DNS request
		- ARP spoofing
			- Atker pretends they are someone through spoofing ARP
	- VLAN hopping
		- You only have access to your VLAN, jump/hop to another vlan
		- Switch spoofing
			- Pretend to be a switch, send trunk authentication
			- Now you have a trunk link
			- Disable trunk negotiation
		- Double tagging
			- Craft a packet that has 2 VLAN tags,
			- Switch removes "native" VLAN tag, fake tag is now visible
			- One way trip only
			- Don't put devices on native VLAN
	- Rogue DHCP
		- IP assigned to client is invalid or duplicate
		- Enable DHCP snooping
	- Rogue access point (AP)
		- AP that is unauthorized
		- Potential weakness
	- Evil twin
		- Looks the same as the real thing but its malicious
	- Ransomware
		- Data is locked until you pay
	- Password attacks
		- Brute-force
			- Run through every combination until you get it
		- Dictionary
			- Run through a wordlist - common words until you get it
	- MAC spoofing
		- fake a MAC addr
	- IP spoofing
		- Fake an IP addr
		- Arp poisoning
	- Deauthentication
		- Manipulates 802.11 management frames
		- Atker sends a disconnect frame - you get DC'd
	- Malware
		- Malicious programs, virus, trojans etc
• Human and environmental
	- Social engineering
		- Using human nature to find out stuff
		- Say wrong thing until someone corrects you etc
	- Phishing
		- Pretending to be something you are not to gain info
	- Tailgating
		  - Gaining access to somewhere you're not supposed to by using someone else's access
		  - Atker does not have consent - sneaking
	- Piggybacking
		- Gaining access to somewhere you're not supposed to by using someone else's access
		- Atker has consent - "oh my hands are full"
	- Shoulder surfing
		- Looking at someone over their shoulder
		- Peeking
## 4.3 Network Hardening
• Best practices
	- Secure SNMP
		- SNMPv3
		- V1 and V2 were unencrypted
		- Use authPriv
	- Router Advertisement (RA) Guard
		- IPv6 includes periodic router announcments
		- Switches can validate the RA 
	- Port security
		- Prevent unauth users from connecting to port
		- Based on source MAC addr
		- Configure src mac or maximum num of MAC addr
	- Dynamic ARP inspection - (DAI)
		- Create a map of all devices on your network and IP addr using DHCP snooping
		- Intercept ARP request and resp
			- invalid IP to MAC req or resp are dropped
	- Control plane policing - (CPP)
		- Control plane manages the device
		- Configure QoS
		- Protect against DoS
		- Manage traffic - prioritize management traffic
	- Private VLANs
		- Port isolation - restrict access between int even when its the same VLAN
		- i.e. Hotel Rooms
	- Disable unneeded switchports
		- administratively disable
		- NAC - authenticated before you can connect
	- Disable unneeded network services
		- every open port is an atk vector
		- Close unnecessary ports
	- Change default passwords
		- Default passwords are public - change it
	- Password complexity/length
		- Easy passwords are easy to guess/bruteforce
	- Enable DHCP snooping
		- Turns switch into DHCP firewall
		- Routers, switches DHCP servers are trusted
		- everything else is untrusted for DHCP
		- Filters invalid IP and DHCP information
	- Change default VLAN
		- Default vlan has all ports with no security
		- Don't put users on management VLAN
		- Assign unused interfaces to non-routable VLAN - dead end or impasse vlan
	- Patch and firmware management
		- Upgrade firmwares to prevent 0-days
		- plan for rollback or backup
			- Service packs - all at once
			- Monthly updates - incremental
			- Emergency out of band update - 0days
	- Access control list
		- Allow or disallow access to system based on tuples - rules
	- Role-based access
		- Not everyone connecting to switch or rtr needs the same lvl of access
		- Create roles and assign permissions
	- Firewall rules
		- Manage access from the firewall
	- Explicit deny
		- deny only if stated
	- Implicit deny
		- allow only if stated
		- Implicit deny doesnt log usually
• Wireless security
	- MAC filtering
		- Limit access through physical hardware addr
		- MAC addr can be spoofed
	- Antenna placement
		- limit access from outside the building
		- adjust power levels
	- Wireless client isolation
		- Wireless devices should not be able to communicate to each other
		- Hotel internet
	- Guest network isolation
		- Guest network should not be able to connect to main network
	- Preshared keys (PSKs)
		- Personal network config
		- WPA2 or WPA3
		- Same password for wifi login
	- EAP
		- Enterprise uses authentication protocol
		- A framework for authenticating wireless
	- Geofencing
		- Devices stop working in/out of a certain zone, using GPS
		- Disable certain features when connected to wifi etc
	- Captive portal
		- authentication to network
		- Access table recongnized a lack of authenticaiton
		- username/password
• IoT access considerations
	IoT security is not the primary focus
	Ensure IOT is segmented from private network
	IoT on guest network at home
Unified Threat Management
	Combines Firewall, IDS, IPS all into one
## 4.4 Remote Access
• Site-to-site VPN
	Always on
	Office to office
	Firewalls act as VPN concentrator
• Client-to-site VPN
	On demand access from a remote device
	Some software can be configured as always-on
	- Clientless VPN
		- Browser VPN - create VPN tunnel without application
		- Just use a HTML5 browser
	- Split tunnel 
		- Only relevant information is passed through VPN
		- OTher stuff is used as normal traffic
	- full tunnel
		- all information is passed through the VPN 
- Layer 2 Tunneling Protocol - (L2TP)
	- support VPNs or part of delivery of services by ISPs
• Remote desktop connection
	Share a desktop from a remote location
	RDP -  Windows
	Virtual Network Computing - VNC - 5900
		Linux and MacOS
		designed for VDI 
		Remote Frame Buffer Protocol - RFB
• Remote desktop gateway
	VPN with Remote desktop connection
	Client connects to remote desktop gateway then connects remote desktop server
	TCP/3389
• SSH
	Encrypted console communication - TCP/22
• Virtual desktop
	Virtual Desktop Infrastructure - VDI
	User connects to desktop online, local machine is only thin client
	Vocareum
• Authentication and authorization considerations
• In-band vs. out-of-band management
	OUt of band - network isnt available - how do oyu connect to rmeote systems now?
		devices have a physical management interface
		Console router/ comm server
			OUt of band access for multiple devices
## 4.5 PHysical Security 
 Detection methods
	- Camera
		- Watch ppl - replace security guard
	- Motion detection
		- Record when something moves
	- Asset tags
		- Record of every asset
		- Useful for financial records, audits and depreciation
		- Tag the asset with RFID, Org number, barcode, tracking number etc
	- Tamper detection
		- Things to check if something got temptered with
		- Case sensors - indentify case removal
		- Alarm sent from BIOS
		- Foil asset tags - void stickers
• Prevention methods
	- Employee training
		- Personal training
		- Posters
		- Login messages
	- Access control hardware
	- Badge readers
		- Keyless/pin
		- No keys to lose - no locks to rekey
		- Centrally controlled
	- Biometrics
		- Difficult to change
		- Not foolproof
	- Locking racks
	- Locking cabinets
	- Access control vestibule
		- Prevent unauthorized people from entering the building
	- Smart lockers
		- Automated and safe delivery and pickup
		- Prevent theft
		- Need a code to open the locker
• Asset disposal
	- Factory reset/wipe configuration
		- Delete data and return the config to the default, next user gets fresh config
	- Sanitize devices for disposal
		- Wipe - unrecoverable removal of data on storage device
# 5.0 Network Troubleshooting
## 5.1 Troubleshooting Methodology
• Identify the problem
	- Gather information
		- Try to duplicate the issue
	- Question users
		- Try to get details
	- Identify symptoms
		- May be more than one symptom
	- Determine if anything has changed
		- Overnight changes?
	- Duplicate the problem, if possible
	- Approach multiple problems individually
		- Break problems down to smaller issues
• Establish a theory of probable cause
	- Question the obvious
		- Occam's razor
	- Consider multiple approaches
		- Consider even not so obvious
	- Top-to-bottom/ bottom-to-top OSI model
		- Start with physical or start with the application
	- Divide and conquer
		-Break problem down and see what is useful what isnt 
• Test the theory to determine the cause
	- If the theory is confirmed, determine the next steps to resolve the problem
- If the theory is not confirmed, reestablish a new theory or escalate
	- Call an expert
• Establish a plan of action to resolve the problem and identify potential effects
	Build the plan to correct the issue with minimum impact
	Identify the potential effects
	Have a plan if it goes bad or it doesnt work
• Implement the solution or escalate as necessary
	Try the fix, call customer support?
• Verify full system functionality and, if applicable, implement preventive measures
	Have customer confirm the fix
• Document findings, actions, outcomes, and lessons learned
	Make sure this doesnt happen again
	If it does someone else knows how to fix it
## 5.2 Cable issues
• Specifications and limitations
	- Throughput
		- Amt of data transferred in a timeframe
		- how much water is going through the pipe
		-Actual amt of datain real world situation
	- Speed/bandwidth
		- Theoretical maximum data rate
		- bits per second
		- size of the pipe
	- Distance
		- How far the info can travel before being degreaded
• Cable considerations
	- Shielded and unshielded
		- U - unshielded
		- S braided shielding
		- F foil shielding
		- Shielding reduces signal interferance
		- (Overall cable)/(individual pairs) TP
	- Plenum and riser-rated
		- Plenum - building air circulation 
			- Smoke and toxic fumes if run in plenum area
			- Normally polyvinyl chloride - PVC
			- Can be used in air enclosed areas
			- Plenum rated means if it burns its okay
				- Flourinated Ethylene polymer - FEP
				- Low smoke polyvinyl chlorid - PVC
				- May not be as flexible
• Cable application
	- Rollover cable
		- Yost Cable
		- RJ45 to serial communications
		- cisco console cables
	- console cable
		- Serial cable
		- DB-9 and DB-25 connections
		- RS-232
	- Crossover cable
		- Like to like connection
	- Power over Ethernet
• Common issues
	- Attenuation
		- Gradual
		- Signal strength degrades over distance
	- Interference
		- EMI interference
		- Cable handling
		- Dont use staples
		- Power cords, flourescent lights, electrical systems, microwaves etc
	- Decibel (dB) loss
		- dB - signal str measurement
		- Logarithmic scale
		- 3dB = 2x
		- 10dB = 10x signal 
		- 20dB = 100x 
		- 30dB= 1000x
		- intermittent connectivity
		- No connectivity
		- Poor performance
	- Incorrect pinout
		- Is the cable pinned out right?
		- Poor pinouts might have connectiveityy issues or performance issues
	- Bad ports
		- interface errors
		-  verify configs
		- verify two way config
	- Open/short
		- Short - two connections touching each other
		- Open - disconnect
	- Light-emitting diode 	(LED) status indicators
		- Green blinky blinky good
	- Incorrect transceivers
		- transceivers have to match the fiber
		- single mode fiber - single mode transceiver
		- Wave length needs to match
		- Both sides need to match
	- Duplexing issues
		- incorrect speed auto configed
		- Might autonegotiate
		- Significant slowdowns and increase in late collisions
		- double check configs
	- Transmit and receive (TX/RX) reversed
		- Wiring mistake, crossed pairs
		- some networks will correct automatically
		- No connectivity - try Auto-MDIX
		- Locate reversal location
	- Dirty optical cables
		- blocking light on fiber = bad
• Common tools
	- Cable crimper
		- Crimp connector into the wire
	- Punchdown tool
		- Punches the wire and fastens it into the punchdown block
		- changes depending on block
	- Tone generator
		- Follow the wire - tone increases when you get close 
		- Easy wire tracing
	- Loopbackadapter
		- Testing physical ports
		- Cable that sends signal right back into the connector
	- Optical time-domain reflectometer (OTDR)
		- TDR - sends electrical pulse and pings
		- OTDR - same with light
		- Estimate cable length
		- Identify splice locations
		- Cable impedance information
		- signal loss
		- certify cable installations
		- Tests fiber
	- Multimeter
		- Check wall voltage
		- Check continuity
	- Cable tester
		- Make sure the cable pins are connected to each other
	- Wire map
	- Tap
		- Intercept network traffic
		- Physical - disconnect link and put tap in middle
		- Active - needs power
		- Passive - no power needed
	- Fusion splicers
		- Join two ends of fiber together
	- Spectrum analyzers
		- analyze wireless spectrum to see what signals are available
	- Snips/cutters - cut stuff
	- Cable stripper
		- remove cable shielding
	- Fiber light meter
		- Tests fiber and sees how much light is getting through
## 5.3 Network Software and commands
• Software tools
	- WiFi analyzer
		- Wireless networks are easy to monitor
		- Everyone hears everything
		- Just need to be quiet to hear everything
	- Protocol analyzer/packet capture
		- gather frames on the network
		- View traffic patterns and identify unknown traffic
	- Bandwidth speed tester
		- Test the speed
	- Port scanner
		- See if a port is open or avail
	- iperf
		- Performance monitoring and speed testing
		- NEed two computers, server and client
	- NetFlow analyzers
		- Gather traffic statistics from all traffic flows 
		- Standard collection method
	- Trivial File Transfer Protocol (TFTP) server
		- bare minimum file transfer
		- perfect for firmware or config upgrades
	- Terminal emulator
		- SSH or similar
	- IP scanner
		- Scan IPs that are on the network
• Command line tool
	- ping 
		- test reachability 
		- round trip time
		- ICMP
	- ipconfig/ifconfig/ip
		- Find the IP address of your system
	- nslookup/dig
		- Find the name of a IP
	- traceroute/tracert
		- What hops what route to go
	- arp
		- determine MAC addr based on the IP addr
		- arp - a : look at arp table
	- netstat
		- network statistics
		- netstat -a : active connections
		- netstat -b : binaries (windows)
		- netstat -n : Ip addr only
	- hostname
		- Find the FQDN of the host machine
		- Find IP addr of the device
	- route
		- view routing table
		- Win: route print
		- Linux/MacOS : netstat -r
	- telnet
		- Login to devices remote;y
	- tcpdump
		- capture packets from command line
	- nmap
		- Network mapper
• Basic network platform commands
	- show interface
	- show config/show run
	- show route
## 5.4 Common Wireless connectivity issues
• Specifications and limitations
	- Throughput
	- Speed
	- Distance
	- Received signal strength	indication (RSSI) signal strength
		- Closer to 0 is better, -50 dBm is excellent
		- -80 dBm and lower is bad
	- Effective isotropic radiated power (EIRP)/power settings
		- transmit str + antenna gain - cable loss
		- How much power going thru antennae
• Considerations
	- Antennas
	- Placement
	- Type
		- Parabolic
		- Yagi
		- Omnidirectional
	- Polarization
		- Orientation of antenna relative to surface of eath
		- Transmit and receiving should be the same polariziation
	- Channel utilization
		- limited amt of frequency 
		- When you hit 100% air time youve used up all of your available wireless space
			- disable legacy low speed support
			- split the network
	- AP association time
		- How long your device is connected to the AP
		- if its low, might be low power
	- Site survey
• Common issues
	- Interference
	- Channel overlap
	- Antenna cable attenuation/signal loss
	- RF attenuation/signal loss
		- Signals get weaker the farther you are from the source
	- Wrong SSID
	- Incorrect passphrase
	- Encryption protocol mismatch
	- Insufficient wireless coverage
	- Captive portal issues
	- Client disassociation issues
		- DoS attack
		- Use wireshark to diagnose
		- Remoive device performing attack to resolve or upgrade
## 5.5 General Networking Issues
• Considerations
	- Device configuration review
	- Routing tables
	- Interface status
	- VLAN assignment
	- Network performance baselines
• Common issues
	- Collisions
		- Half duplex maybe
	- Broadcast storm
		- Use a packet capture to identify
	- Duplicate MAC address
	- Duplicate IP address
	- Multicast flooding
		- Internet Group Management Protocol - IGMP
			- IGMP snooping
		- Switch intelligently forwards multicast to specific devices
	- Asymmetrical routing
		- Router goes out one way and comes back another way
	- Switching loops
		- Prevent with spanning tree protocol
		- switch autoforwards -> loop
	- Routing loops
		- A thinks next hop is B
		- B thinks next hop is A
		- Use traceroute to diagnose
		- Prevented with TTL and Maximum hop count
		- Prevented with:
			- Split horizon
				- Prevents a route learned on one int from being advertised back out of the same interface
			- Poison reverse
				- Causes a route recieved on one int to be advertised back tout of the same int with a metric considered inf
	- Rogue DHCP server
	- DHCP scope exhaustion
		- Device is now locked to local subnet
		- IP address management -IPAM device can help
		- Lower lease time
	- IP setting issues
		- Check settings
		- Monitor traffic
	- Incorrect gateway
	- Incorrect subnet mask
	- Incorrect IP address
	- Incorrect DNS
	- Missing route
		- ICMP host unreachable might be seen
	- Low optical link budget
		- Is the wire clean
	- Certificate issues
		- Certificate may not be signed
		- Time and date mgiht not be right
	- Hardware failure
	- Host-based/network-	based firewall settings
	- Blocked services, ports, or addresses
	- Incorrect VLAN
		- Check VLAN assignment
	- DNS issues
		- If ping works but browse doesnt then it might be DNS
		- Try nslookup or DIG
	- NTP issues
		- Time is used by everything
		- If its too far out of sync then we need to adjust
	- BYOD challenges
	- Licensed feature issues
		- Features are often individually licensed
		- Some features may not be available
	- Network performance issues