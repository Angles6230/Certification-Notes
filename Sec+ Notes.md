CIA Triad 
Confidentiality - Encryption - who knows
Integrity - nonrepudiation - what is it - hashing
Availability - can you access it - backus
# 1.1 - Social Engineering
## Phishing - Social engineering with a touch of spoofing
Typosquatting 
	URL Hijacking - same domain name but slight differences
	Prepending - adding smt to the beginning
Data URL Phishing
	Prepending
	Changes the data in the 
Pretexting  - Lying to get information 
Pharming - redirect a legit website to bogus site
	Poisoned DNS server or client vulnerabilties
	Harvest large groups of people
	Phishing - collect access credentials
	Hard for antimalware to stop 
		Everything looks normal
Vishing - Voice phishing 
	Caller ID spoofing
Smishing - SMS phishing 
	Forwards link or asks for personal info
Spear Phishing - Targeted phishing with inside info
Whaling - Spear phishing high value target
## Impersonation - 
Pretext - Actor and story 
	Atkers pretend to be someone they arent
	Uses details from reconnaissance
	Atk the victim as someone higher in rank
	Tons of technical details
	Be a buddy
Eliciting information - extracting info
	Hacking the human
Identify fraud 

## Dumpster Diving
Gathering information from trash
Secure your garbage
Shred/secure your documents


## Shoulder Surfing
Obtaining information through viewing the target computer from behind them
Shoulder Surf from afar with binoculars
Webcame monitoring
Be aware of your surroundings
Privacy filter
Keep monitor away from window
## Hoaxes
threat that doesnt exist but it seem like it COULD be real
Still consume resources
Email Hoax
Hoax in Browser
Dehoaxing
	Spam filter

## Watering Hole Attacks
Infecting a third party and hoping you get infected
Exectuing watering hole attack
	Determin which website the vict group uses
	Infect 3rd party site
	Infect all visitors
Defense in depth
	Layered defense
Firewall and IPS  - stops it before it gets bad

## Spam
Unsolicited messages
SPIM - Spam over IM
Security Concerns and resource utilization/storage costs
Spam Filtering
	Stop it at the gateway before it reaches the user
	Allowed list
	SMTP standards - block anything that doesnt follow RFC standards
	rDNS - block email where senders domain doesnt match IP add
	Tarpitting - Intentionally slow down mail server\
An open relay on mail port can lead to  Email server being flagged as a spam server
	Open relay port means somoene outside your network can send mail through your mail server using your port causing other mail servers to register your server as a spam
Antivirus
	You can prevent malicious file attachements through antivirus software
Antispam
	Reduces spam but does not scan for infected attachements
HFW
	monitor traffic coming into and leaving computer but do not scan for infected files
Mail ports
	SMTP 25
	POP3 110
	IMAP 143
	SMTPS 465
	POP3S 995
	IMAPS 993
Pretty Good Privacy
	Lightweight encryption, signin, decrypting email program
	Uses IDEA algo
GNU Privacy Guard 
	Updated version of PGP 
	Uses AES
	GPG - GNU - LINUX FREE EMAIL
## Influence Campaigns 
Sway public opinion
Nation state actors
Advertising
enabled through social media 
	Amplification - Fake accts
		Then creating content
		Post on social media
		Amplifies the message
		Real people see it then share the msg
		Mass media picks up the story
Hybrid warfare
	Military strategy
	Cyber warfare
	Influence with military spin
## Other social Engineering attacks
Tailgating - Use authorized individual to gain access to bldg by going right behind
	Mantraps defeat this
Invoice Scam
Credential Harvesting 
	Password harvesting
	Hacks stored credentials like browsers
	User opens email/docu which runs a macro/script that downloads cred harvesting software
## Social Engineering Principles
Authority - Someone in charge
Intimidation - Bad things will happen if you dont help
Consensus - Convince based on what is expected
Scarcity - Situation will not be this way for long - its running out
Urgency - Act quickly don't think - time is running out
Familiarity/Liking - Someone you know/ common friends/ making friends
Trust - Someone who is safe - pretending to be trusted
# 1.2 Malware 
## Malware
These all work Together
Drive-by download - Website popups to automatically download 
OS and Application updates
Malicious software
### Viruses
Malware that can reproduce itself
Requires user to click on or use it to start the process
May or maynot cause problems
Reproduces through file systems or network
	Categories
	Program virus - part of the applicaiton
	Boot Sector virus - exists in bootsector and it lauches with bootsector
	Script viruses - OS or browser
	Macro virus - runs inside another application
	Polymorphic
		Adv version of encrypted virus that can change itself everytime by altering the decryption module to avoid detection
	Fileless - stealth atk - operates solely inside memory/ram 
		click a link on website/email that then downloads smt to run 
		might even change registry with autostart
	Multipartite
		 Virus that combines boot and program viruses to first attach itself to the boot sector and system files before attacking other files on the computer
	A stealth virus is **a computer virus that uses various mechanisms to avoid detection by antivirus software**
	
### CryptoMalware
Newer gen of ransomware 
Locks data using cryptography until you get a key
you get a key from sending money
### Ransomware
Data is valuable - it has a cost money
Protection 
	Always have a offline backup 
	Keep OS up to date
	Keep application up to date
### Worms
Malware that self replicates
Uses network as transmission medium
Can take over many systems very quickly
Wannacry
### Trojan Horses
Software that pretends to be something else
Software will look normal
Potentially Unwanted Program(PUP)
	Potentially undesirable software
	Browser search hijacker
	Overly agressive browser toolbar
Remote Access Trojan(RAT)
	Remote Administration Tool
		Ultimate backdoor
		Might be installed by a RAT
			Keylogs, screen records, copy files etc.
### Rootkit
Modifies core system files part of the kernel
Now part of the OS it is not invisible to the AV
Secure boot with UEFI 
### Adware/spyware
Computer turns into one big advertisement
May be installed accidentally
Spyware - 
	Software that spies on you
	Keylogger 
	
### Botnet
Once your machine is infected it becomes a bot
Sits around, checks with Command and Control(CC) server
Then it executes any command by the CC server
Relays for DDoS, Spams etc.

## Malware Exploitation
Exploit technique - specific method the malware code infects a target host
Dropper - install or run other types of malware
Downloader - connects to the internet to retrieve additional tools 
Shellcode - lightweight code designed to run an exploit on the target
Code injection -  runs malicious code with ID number of legitimate process
Living off the land - uses standard system tools to perform intrusions
## Logic Bomb
Waits for predefined Event
Often left by disgruntled employee
Time bomb - occurs when date or time is reached
User Event 
Difficult to identify before it goes off
	Each is unique
## Password Attacks
Plaintext/ unencrypted passwords - no encryption
Hashing a password - 
	Turns data into message digest
	Different inputs have different hash
	Oneway trip
Spraying attack - try to login with incorrect password
	If not work with top then they go to next account
	Avoids acct or lockouts
Brute force
	Try every possible combo
	Online 
		Lockout after num of attempts
	Offline attack
		Large computation resource req
		Takes their time due to no lockout
	Dictionary attack
		Uses common words from the dictionary
		Many wordlists are available 
			Sometimes tailors to a field
		Can substitute letters i.e. password > P@ssw0rd
		Takes time - Distributed cracking and GPU cracking is common
	Rainbow Attack 
		Optimized prebuild set of hashes
		Saves time and storage space
		Doesnt need to contain every hash
		Speed increase
		Different tables for different applications
Salting -Extra random data added to password when hashing 
	Each user gets their own salt
	Rainbow tables dont work if salted
## Hijacking
Definition - Exploitation of a computer session in an attempt to gain unauthorized access to stuff
Session Theft-  Atker guesses the SESSID for the web session and enables them to take over the already auth session
TCP/IP hijacking - atker takes over a TCP session without need of cookie or other host access
Blind Hijacking - atker blindly injects data into the comm stream without being able to see if it is successful or not
Click jacking - uses multiple transparent layers to trcik a user into clicking on a button or link on a page
Man in the middle - attk that causes data to flow through atkers comp where they can intercept or manipulate data
Man in the browser -trojan infects a vulnerable web browser and modifies the web pages or transactions done within the browser
Replay attack - valid data tansmission is fraudulenty or maliciously rebroadcast, repeated or delayed 
	Just intercept and analyze it
	Session tries to manipulate it

## Physical Attack
Malicious USB Cable
	Looks like normal 
	But actually operates differently I.E. like HID
	Once connected the cable takes over
Malicious flash drive
	Plug it in and see - causes problems
	Older OS automatically ran files 
	Could still run as a HID
	Can be ethernet
	Can be boot device
Skimming
	Stealing credit card info during normal transaction
	Card Cloning 
		makes a duplicate of skimmed clone
		Gift cards get cloned.
## Adversarial Artificial Intelligence
AI is only as good as the training data
Check training data
Retrain with data
Artificial Intelligence 
	science of creating machines with the abilkity to develop problem solving and analysis without huiman direction
Machine Learning 
	Component of AI that enables a machine to develop strats for solving a task
		Requires information input
	Poisoning training data - created poisoned output
	human determins factors
Deep Learning 
	Learning that enables machine to learn on its own
	Uses simpler classes of knowledge to make more informed determinations
	Machine determines factors
## Supply Chain attacks
Attackers can infect a part along the way
People trust their suppliers
Due Diligence 
	legal principle that subject has used best practice for what theyre doing
Trusted Foundry 
	Micreoprocessor utility that is part of a validated supply chain - hardware/software does not deviate from its documented function
	Trusted Foundry Program is operated by DoD
Hardware Source Authenticity - process of ensuring that hardware is tamperfree

## Cloud vs On Premise 
Cloud - 
	Centralized and costs lest
	No physical access
		Third party might have access
	Managing large scale security
		Automated large security
	More available bc larger structure - higher uptime
	Scalable security options
		Not as customizable but easier
On Premise - 
	Security is on client
	Complete control
	On Site can manage better
		Local team is more expensive and difficult to staff
		Local time maintains uptime availability
	Security Changes can take time due to new equip/config etc

## Cryptographic attacks
Hash collision 
	2 diff plain text but same hash 
	Find collision through brute force
	Protect yourself with larger hash
MD5 hash was cracked in 1996
Downgrade attack 
	Uses an older crypto which is easier to break

# 1.3 Application Attacks
## Priviledge Escalation
Gain higher level access to system
Horizontal priviledge escalation

## Cross Site Scripting (XSS)
Manipulating the site to hit a client
Takes advantage of trust a user has for a site
	Enables attackers to inject client side scripts into webpages viewed by others
Non Persistent (reflected) XSS 
	Website allows scripts to run in user input
Persistent (Stored) XSS
	Attacker posts message to social network
	Anyone who reads it gets the script on their machine
	Everyone gets payload
XSRF/CSRF 
	Attacker forces a user to execute actions on a web server they are already auth with
## Injection Attacks
Manipulating the site to hit the server
Code injection - bad programming
Structured Query Language - SQL injection
	Modifies SQL requests by not sanitizing input
Extensible MArkup Languag - XML 
Lightweight Directary Access Protocol - LDAP
	Database used to centralize info about clients and objects on the network
		Encrypted 636
		Unencrypted 389
	Microsofts version is Active Directory
	Store info about auth
	LDAP injection to manipulate applicaiton results
	An LDAP injection attack targets ==directory services databases==
Dynamic Link Library  - DLL
	Inject DLL and have application run a program

## Buffer Overflow
Spills over to other memory areas

## Replay Attack
Useful info is transmitted over the network
Attker can capture info that makes it seem like it was coming from you 
Pass the hash
	Atk gains access to the hash
	Sends it to the server and atker pretends its the client
	From the perspective of the server it looks like the atker is the client
Cookies and session IDs can be used for replayu attacks too
Sidejacking
	Client gets session ID from server
	Atker can pose as client by using Sess ID

## Request Forgeries
Cross site requests - requesting from another site thats not from the actual site
	Most of these are unauthenticated requests
Takes advantage of the trust 
## Driver Manipulation
Shimming - Filling the gap between two objects
	Can be abused by malware 
	Library that responds to inputs that the original device driver isnt designed to handle and would require a seperate file
	I.E. using win compatability mode to force system to use downgraded protocols
Refactoring 
	Driver that has code changed
	unique, sig based detection cannot detect it
	Metamorphic malware - different program each time it's downloaded
	Adds different code that changes the signature

## SSL Stripping/ HTTP downgrade
Combines On path attack with downgrade attack
	Strips S from HTTPS
SSL - Secure Socket Layer - deprecated in 2011
SSL 3.0 deprecated in June 2015
Transport layer security - can downgrade to SSL 3.0
TLS 1.1 deprecated in Jan 2020
TLS 1.2/1.3 most common
## Race Conditions
Time of Check to Time of Use attack (TOCTOU)
	Check sys
	When do you use the results of last check
	something can happen between check and use
## Memory Vulnerabilities
Memory leak 
	unused mem never returned to the system
	good DDoS
Null pointer Reference
	Makes an application points to a place where nothing exists
Integer overflow
	Large num goes into smaller space
Directory Traversal
	Read files from webserver that is outside the website file folders
	non-secure directory structures on the host
SQL injection
	targets relational databases behind the web appli
LDAP injection
	Targets the directory DATABASE
	attacks active directory
API attacks
	Application Programming Interface
Resource exhaustion
	Zip bomb
	DHCP Starvation

# 1.4 Network Attacks
## Rouge Access Point and Evil Twins
Unauthorized Wireless Access Point
	Not necesarry malicious
	Enable wireless sharing
Schedule periodic reviews
802.1x Network Access Control
	NAC - Security technique which devices are scanned to determine its current state prior to being allowed access into the given network
	if it fails inspection it is put into quarantine
Evil Twins
	looks the same as real WAP 
	Malicious
	Can overpower existing AP
	WiFi/Hotspot users are easy to fool
## Bluejacking Bluesnarfing
Sending of unsolicited messages to another device via BT
Typically within 10m
BlueSnarfing - 
	Atker is able to access information from BT 
	Modern devices not affected
BlueJacking - sending unsolicited messages - sends info
Bluesnarfing 
	unauthorized access of information  - takes info
	Gaining un auth access through bt
## Wireless Disassociation Attacks
Wireless Deauth attack
	A deauthentication attack involves sending specially crafted traffic to a wireless client and an access point, in the hopes of causing them to deauthenticate with each other and disconnect.
	DDoS for wireless
802.11 includes management frames 
	Originally sent in the clear
	Atker can send false mgmt frames
	patched - 802.11w July 2014
		More important things are encrypted
		some are not
		802.11ac+ 
## Wireless Jamming
RF jamming
Transmit interfering wireless signals
Decrease signal to noise ratio at the receiving device
	Sometimes not intentional
Reactive Jamming - only sending when someone tries to communicate
Needs to be somewhere close
## RFID
Radio Frequency Identification
Uses Radar technology, 
	RF powers the tag, 
	ID is transmitted back
Some are active/pwered
Some are bidirectional
Attacks 
	Data capture
	Replay attack
	Spoof reader
	DoS
	Many Decrypt keys are on google
NFC - near field communication
	2 way
	Payment systems
	ID card
	Same concerns as RFID
## Randomizing Cryptography
Crypographic nonce
	Arbitrary number
		used once
	random or pseudo rano number
	used during login progress
	Pswd hash diff in every time

## On path Network attack
Redirects your traffic without you knowing

## MAC Flooding and Cloning
Atker sends traffic with diff src mac add to the switch
Forces the switch to go to broadcast 
turns switch into a hub
	Atker can capture all network traffic
MAC Cloning 
	Spoofs
	circumvents filters
	Disrupt communication to legitimate MAC

## DNS Attacks
DNS Poisoning
	Modify client host file
		Host file takes precedence over DNS queries
	Send fake resp to valid DNS request
	Can be prevented if you only allow authenticated zone transfers
Domain Hijacking
	Gain access to domain registar  they can change IP
URL Hijacking
	Creates domain name that is similar
	Phishing site?
	Infect by driveby
	Types
		Typosquatting/brand jacking
		Mispelling
		Typing error
		Diff phrase
		different top lvl domain
Unauth Zone transfer - Attacker requests replication of DNS info to their sytems for use 
Altered hosts file
Pharming - atker redirects one website traffic to another website
Domain name kiting - keeps domain name isn limbo
## Denial of Service
Force a service to fail
Competitive advantage
Smokescreen for exploit
can be friendly unintentional
Flood Attack
	Specialized type of DoS whcih attempts to send more packets to a single server or host than they can handle
Ping flood
	atker atempts to flood the server by sending too many ICMP pings
Smurf attack
	Attacker sends a ping to subnet braodcast addr and devices reply to spoofed IP(victim)
Fraggle Attack
	Attacker sends UDP echo packets to port 7 and port 19 to flood with UDP attacks
Syn Flood
	Atker initiates multiple TCP session s but never completes 3 way handshake
XMAS attack
	network scan sets FIN PSH and URG flags set and cause device to crash or reboot
Ping of Death
	sends a oversized and malformed packet to another comp or server
Teardrop atk
	atk breaks apart packets into IP frags and modifies them with overlapping and oversized pauloads
Perm DoS
	BReaking a netwoking device
Fork bomb
	Atk that creates a large num of processes to use up the available processing power of the comp

Distributed DoS
	Botnets
	Asymmetric threat 
	Amplification
		turn a small atk into a big one
		Reflects protocl from one service to another machine
			DNS amplification
		Application DoS
## Malicious Scripts
PowerShell 
	.ps1 file ext
	Uses cmdlets
	PS scripts and exes
	Perfect for attacking windows
Python
	.py
	Popular in many technologies
Shell script
	Bash, Bourne, Korn, C
	Starts with #! or .sh ext
	Linux/Unix
		Linux is done at cmdline so it is perfect
Macros
	Automates functions within the application
	Can be used to perform malicious attacks
Visual Basic for Applications(VBA)
	Automates process within MicroOffice
## Threat Actors 
- Anyone or anything with motive/resource to attack another's IT infra
	Hackers
	Hacktivists - Promoting 
	Script kiddie - no hacking skills , grabbing known scripts
	Insiders - ppl inside the org
	Shadow IT - unauthorized ppl who implement IT solutions
	Criminal Syndicates - criminals - primarily DDOS
	State Actors - Govts
	Advanced PErsistent Threat ( APT) - long term hacking to get a lot of info overtime
	Competitors

# 1.5 Attack Vectors
## Attack Vectors
Direct Access
	A lot of vectors available
Wireless Attack vectors
	Login
	Rouge APs
	Evil Twin
Email 
	Phishing
	most successful
	Social engineering
	Malware attachments
Supply chain
	Tamper with manufacterurs
Social Media
	OSINT to gain access to account
Removable media
	USB
	HID devices
Cloud 
	Publicly facing application and svcs
	Security misconfigurations
## Threat Intelligence
Research the threat
Data is everywhere
Types of monitoring
	Behavioral - uses baseline of normal behavior, helsp prevent 0 day attacks
	Signature - uses signatures, can be out of date and cannot detect threats previously encountered
	Rule based - dependent on admin created rules that search for specific behaviors
	Active based - take active steps to prevent network intrusion
OSINT - Open Source INTel
	Publicly available
	Govt Data
	Comm Data
Closed proprietary data
	someone else used
	Threat Intell Services
	Constant threat monitoring
	Costs money
	Might be automated
Vulnerability Databases
	ppl find database and gets published
	CVE common vulnerabilities and Exposures
	US National vulnerabiliy Database (NVD)
Public threat intel
	Often classified info
Private Threat intel
	Priv companies ahve resources
Neeed to share critical detials
	Real time high quality
Cyber Threat Alliance(CTA)
	Members upload information and score each submission a la reddit
Automated Indicator Sharing(AIS)
	Automates information transfer
	Standardized in Structured Threat Information eXpression(STIX)
		Transported in Trusted Automated eXchange of Indicator Information(TAXII)
Dark Web Intel
	Overlay networks that use intel
	Hacking groups and svcs
	Monitor forums for activity
Indicators of Compromise
	Event that indicates intrustion
Predicitive analysis
	Analyze large amts of data quickly
	Identify behavioral patterns
	You can forcast
Threat maps
	identify threats and types of attacks/where etc
## Threat Research
Know your enemy
Vendor and manufacturers
Vulnerability feeds
Conferences
Academic Journals
Industry Groups
Social Media
TTP - Tactics, techniques and procedures
# 1.6 Vulnerabilities
## Vulnerability Types
Zero Day atks - vuln not found yet
Open permissions - leave the door open
Unsecured root accts 
Errors - can give too much info
Weak Encryption
Default settings
Weak protocols
Legacy platforms
## Third party risks
Prepare for the worst

## Vulnerability Impacts
Data Loss
Identity Theft
Fin Loss
Reputation Impact
Availability Loss

# 1.7 Threat hunting
## Threat hunting
Intell Fusion - overwhelming


## Vulnerability Scanning
Minimally invasive 
	Unlike pen test
Test from outside and inside
Gather info
==Scan Types==
	Non Intrusive Scans - Gather info dont try to exploit vuln
	Intrusive - try to exploit and see if it works
	Non Credentialed scans - Scanner cant login to remote dev
	Credentialed scans - emulates insider atk
Appli scans
Web scans
Net scans
False positives/negatives

## Security Information and Event Management Device (SIEM)
Logging of security events and information
Log aggregation and long term storage
Data Correlation
Forensic analysis
IoC - Indicator of Compromise
Syslog - system logging
	Central log collector
User and Entity Behavior Analytics(UEBA)
	Detect insider threats
Sentiment Analysis
Event deduplication - SIEM can record events in a central store and remove redundant events to produce a more accurate analysis
## SOAR 
Security 
Orchestration
	Connect diff tools together 
Automation
	Handle security tasks automatically
Response
	Make changes immediately
	Playbook - series of steps but playbook is conditional

# 1.8 Pen Testing
## Penetration Test
Simulate an attack
Actually try to exploit vulnerabilities
Compliance mandate
Rules of Engagement
	Defines purpose and scope
Blind Test - Unknown enviroment
Known Enviroment - full disclosure
Partial
Process
	Intital Exploitation
	Lateral movement
	Persistence
	Pivot
	Cleanup

## Reconnaissance
Passive Footprint - understand from open sources
	Social media
	Corporate website
	Subreddit
	Dumpster diving
OSINT
Wardriving/Warflying
	Combing wifi monitoring and GPS
Active Footprinting
	Trying the doors
	Visible on logs
	Ping scans, Port scans
	DNS scans
	NMAP

## Security Teams
Red Team
	Offensive
	Ethical hacking
Blue Team
	Defensive
	Protect the data
Purple Team
	Red and Blue together
White Team
	Referee in a security exercise
Black Hat - Enemy
White Hat - Hired by the company
Grey hat - not hired but not malicious

# 2.1 Sysadmin basics
## Config Management
Identify and document
Network Diagrams
Physical Data Center layout
Baseline Config
Standard Naming conventions
IP Schema
	IP plan for location, sections etc

## Remote Desktop services
Remote desktop protocol - RDP 
	Microsoft's proprietary protocol
	Does not provide auth inately
	Port 3389
Virtual Network Computing - VNC
	Port 5900
	Requires client, server and protocol to be configured
Remote Access Services
	Password Auth Protocol- PAP
		Provide auth but transmits login creds in the clear
	Challenge Handshake Auth Protocol - CHAP
		Used to provide auth by using user's pass to encrypt a challenge string
		Compares answers
## Protecting Data
Data Sovereignty
	Data in a country falkls under that country
Data Masking Obfuscation
	Hides some of the data and sensitive data
	Used to protect data in use
Data Encryption 
	Encode info into unreadable data
	Two way street as long as you have code
	Confusion - encrypted data should be vastly diff from PT
Data At rest
	Data on storage device
	Encrypt the data
	Encrypting files and folders ensures that data is protected whether the server is on or off—even if the hard disk is removed from the server.
	Encrypting the entire hard disk protects the data when the server is powered off; however, once the server is powered on and the disk is decrypted, the data is no longer protected by encryption.
Data in transit/motion
	Data transmitted over the network
	Not much protection 
Data in use
	Data actively being processed
	Almost always decrypted
	Can easily picked up from RAM
Tokenization
	Replace sensitive data with non sensitive placeholder
	Data at rest protection
Windows uses NTFS or FAT32 storage
	New Technology File System - newer better than FAT32
Linux use ext
OSX use APFS
RAID
	0 - striping - availability only
	1 -mirroring - backup only
	5 - block level striping with distributed parity 4 drives
	6 - striping and double parity data across disk drives 5 drives 
	10 - combines two seperate raid 1s together into a raid 0 system
	Fault resistant raid - protects against the loss of the data if one disk fails - 1 or 5
	Fault tolerant - protects against the loss if single component fails 1, 5, 6
	diaster tolerant - provides 2 independent zones raid 10
Tape rotation
	10 tape
		Each tape is used once per day for 2 weeks then set is reused
	Grand father son
		Three sets of backup tapes, son - daily, father- weekly, grandf - monthly
	Towers of hanoi
		3 sets of backup tapes
		rotated more complex
	Snapshot backup 
		Captures the entire OS data
Hard Drive Sanitation
	Cryptographic erase
		erases the media encryption key and reimages the drive
	Secure erase
		sanitation of flash based devices when cryptographic erase is not available
	zero fill
		set all bits to value 0 and takes longer
	physical destruction
Data wiping/clearing 
	Using a software tool to overwrite the data by just overwriting it 
		more times is more secure
	Degaussing 
		demagnetizing a HD
		unusable
	Purging
		Removing sensitive data from hard drve - general term
	SHredding - shredding
## Data loss prevention
On computer
On Network
On Server
DLP on workstation deny/allow certain tasks
Cloud based DLP
Blocks certain actions
Strategies
	Exact Data match 
		Pattern matching technique that uses a structure databse of string values
			Match fingerprints based on format or sequence
			ex. for ssn match xxx-xxx-xxxx
	Document matching
		Attempts to match partial or whole document
		document type matching
	Statistical matching
		Machine learning to analyze various sources using AI
	Classification techniques
		Uses classification tags i.e. military might use secret
## Site Resiliency
Processes to revert to primary location
Hot site - exact replica
	Just buy 2 of everythign
	Automation replication
Cold site - no hardware
	No hardware
	Need to bring your data with you
	Bus in your team
Warm Site - Just enough to get going within relatively short time

## Honeypot
Attracts badguys
Makes it interesting for recon when the atker attacks the honeypot
honeynet 
	Multiple honeypots 
honeyflies
	Attractive baits
	ex passwords.txt fake file
DNS sinkhole
	hands out incorrect IP add
	Blackhole DNS

# 2.2 Cloud Computing
## Cloud Models
Infra as a Service - IAAS
	only the baremetal stuff
Hardware as a service- HAAS
Software as a service - SAAS
	on demand software
	Google mail, everything is there
Platform as a service - PAAS
	salesforce
	building blocks but make your own like squarespace
MSP - Managed service provider
	manages tech stuff for clients
	MSSP - Managed Security Service Provider
Cloud Models
	Public - available to everyone on internet
	Community - several orgs share resources
	Private - own localized data center

## Cloud Computing
on demand
Fast implementation
Issues
	Limited bandwidth
	Latency
	cloud resp with sec not you
Edge Computing
	Applications are being run by local system
	Computed at the edge node rather than going all the way back to the cloud
	Cache/buffering
Fog Computing
	Distributed cloud architecture
	Immediate data stays local
	Local decisions made with local data
	Private data never leaves
	Long term data can go into the cloud
## Designing the Cloud
on demand
elasticity easily
Applications scale
	Availability from anywhere
thin client
	applications run on remote server
	Virtual Desktop Infra ( VDI)
	Desktop AAS
	Local device is only keyboard/mouse/monitor
	Network connectivity req
Virtualization
	Diff OS on same hardware
	Save space
	Each appl inst has its own OS
	Relatively Expensive
Application Containerization
	Single infra/host OS 
	A docker to allow different apps run in self contained sandbox
		Appl also cannot interact with other containers
		Standard format container
	Lightweight 
	Secure seperation
Virtualized vs Containerized
Virtual - Seperate OS 
Containerized - Single OS sperate app
Microservices
	Monolithic applications - one app does it all
	Large code base - complexity when upgrade/Troubleshoot issues
	Breaking up the app into seperate functions
When you call an Application Programming Interface/ API just call one function
Breaks up monolithic apps into seperate parts 
API is the glue for the microservices
Scalable - just increase the microservices
Resiliant - if one part fails, not everything fails
Containment is built in
Function AAS
	Appl is seperated into individual autonomous funct
	Stateless compute container - appli will send api req - reesults are sent back to client
	Serverless Architecture
		Container/instances created and torn down as needed just for a function
		i.e. lots of inventory - create multiple inventories and then delete it after its done
	May be event triggered and ephemeral
		Don't have to keep unused server maintained
		Can scale easily
		Managed by third party
Transit Gateway
	Cloud router - centralizes VPC resources to allow ppl to connect to these VPC resources
	Virtual Private Cloud
		pool of resources created in a public cloud
		pool of appli instances contained in VPC container
		effectively seperate clouds
	Transit gateway - cloud router for different cloud VPCs
Service Integration and Management(SIAM)
	consolidates different applications to one management framework
## Infrastructure as code
Describes servers/networks/appli as code
	Everytime we need something we then call the pre-made code
Software Defined Networking - SDN
	Use code to do networking, once it works it works
		Already secure can just do it again and again
	Seperates networking devices into 2 planes
		Control plane - actual control of the router
		Data plane - actual routing functions
	Changes can be made dynamically
	Centrally Managed - called single pane of glass
	Programmatically configured - no human intervention
VXLAN - virtual extensible LAN 
SDV - software defined visibility 
## Virtualization Security
Too easy to build instances
VM sprawl 
	too many VMs = too many atk vectors
VM - self contained..or is it
VM escape - break out of VM - once you escape you have great control
# 2.3 Secure Coding
## Secure Deployment
Software Development Lifecycle
Planning
	Identifying security requirements for the software
	create a plan for meeting requirements
Design
	software designed with security in mind
	secure algo, protocols
	secure data storate, comms etc
Implementation
	Programmers begin to code
		Basic debugging to ensure it works\
	Software is developed according to the design
Testing
	Formalized testing
	made to ensure it is secure and functions as intended
Integration
	Integrate application into larger enviroment
Deployment
	End users can actually use it
Maintenance
	Software bugs fixes, updates, patches
	Retirement
Software development lifecycle methodology (SDLM) - provides a structure for planning, design development, testing and deployment of software applications
	Sandboxing -
		isolated testing enviroment 
		Use during development process
	Development 
		Secure enviroment
		Write code
	Test
		All of the pieces are put to gether
		Does it work?
	Quality Assurance(QA)
		Verifies its working as expected
		Validates new functionality
		Verifies old errors are fixed
	Staging
		Works and feels like real enviroment
		copies produciton data to see how it works/performs
	Production
		Applicaiton is live
		Impacts users
		New servers needed for new stress?
	Patch Management
		Planning
		Testing
		Implemnenting
		Auditing
		Disable the wuauserv service to prevent Windows Update from running automatically`
Continuous integration - 
	software development method in which code updates are tested and committed to a development or build server/code repository rapidly.
	Can test and commit updates multiple times  per day
	detects and resolves development conflicts early and often
	continuous coding and detecting issues early 
Continuous delivery 
	app and platform requirements are frequently tested
	Ready to be installed but not actually installed
	Have to do continuous integration
Continuous Deployment 
	app and platform updates are committed to prod rapidly
	continuously installed 
Continuous monitoring - technique of constantly evaluating an environment for changes so that new risks may be more quickly detected.
Infrastructure as Code
	Deploy virtualization through using standardized scripts to speed up deployment process
## Secure Coding Techniques
SQL Databases
	common query requests are stored on server and it is just grabbed
	Client can only call the procedure and not call
	Limits interaction
Obfuscation/camouflage
	Turn readable code into nonsense
Code reuse
	Copy paste
	if old code has issues - security vulnerabilities?
	Dead code- does the variable get used or is it useless?
Input validation
	Document all input methods
	Check and correct all input -normalization
	Removing redundant entries from a database - normalization
	Dont give them an opening
	Server side - checks on server side
	client side - may provide addi speed
	Escaping 
		 secure coding technique that ensures that any system commands are not processed and executed as actual commands; instead, they are only recognized as text.
Memory management
	Never trust data input
	buffer overflows are a huge security risk
third party libs and SDKs
	security riskts in the lib?
Data exposure
	how is the data being handled by the data
	input/output data exposure check
Static Analysis - Source code is checked while its not running
Dynamic Analysis - Source code is checked while it is running
## automation and scripting
Auotmated courses of action
Continous monitoring
Configuration validation
	Automatically perform checks before deployment
Continuous integreation(CI)
	Code is constaly written
		Too many changes for manual checks
		Automated checks
		Continuous delivery
			Automate testing and release
			Click a button and it goes
		Continuous deployment
			Automate everything
Artificial Intelligence - 
Machine Learning - 
# 2.4 Authentication
## Authentication methods
Something you have
Directory Services
	Keeps usernames and passwords in a single database
	Large distributed database
	Constantly replicated
All auth requests reference this data base
Access via Kerberos or LDAP - Lightweight Directory Auth Protocol
Kerberos
	Authentication protocl used by windows to provide mutual auth using tickets
	Port 88
Federation
	Authentication with a third party
	Auth and authorize between two orgs
Attestation
	Prove hardware is really yours
	System you trust
	Remote attestation
		device provides operational report to verification server 
SMS - MFA
	Can be intercepted
Push notification
	More secure than sms
Auth apps
	Pseudo random token generations
	Time based One Time Password algo - TOTP
		Secret key and time of day
		Secret key is config ahread of time
	HMAC based One Time Password algo
		synchronized between client and server
		keyed hash message auth code (HMAC)
		One time passwords - used once
Can also use phone call
Static codes
	ATM pins
Smart card
	CAC
## Biometric
Something you are
False acceptance rate(FAR)
	Type II error
False rejection rate (FRR)
	Type I error
Crossover error rate (CER)
	The rate where both accept and reject error rates are equal.
	FAR and FRR are equal
## Multifactor Auth
Identification - who you claim to be
Authentication - Prove who you are
Authorization - what can you do
Accounting - What did you do
Factors
	Smt you know
		Password
		PIN
		Pattern
	Smt you have
		Smart card
		USB token
		Your phone i.e. SMS
	Smt you are
		Biometrics
		difficult to change
Attributes
	somewhere you are
		Based on your location
		Mobile device loc services
	something you can do
		Signature
	smt you can exhibit
		Way you walk
		Typing analysis
	someone you know
		Social factor
		Web of trust
Single Sign on- SSO
	Default user profile is created and linked to all resources needed
Federated Identity Management -FIdM
	Single identity is created for a user and shared wiht all the orgs in a federation
	Cross certificaiton
		Web of sturst to certify
	Trusted 3rd party
		Orgs place their trust in a 3rd party
	Security Assertion Markup Language(SAML)
		attestation model built upon XML to share FIdM
	OpenID 
		Open standard and decentralized protocol to auth users in a federated identity management system
OpenID is easier to implement than SAML, SAML is more efficent than OpenID
# 2.5 Redundancy
## Disk Redundancy
Duplicate parts of the system
Maintain uptime
Hardware/software failure
Geographic dispersal
	Natural disasters can happen
Multipath I/O
	Allows other routes if something along the path fails
	RAID - Redundant array of independent disks
		RAID 0 - Striping without parity - high performance no fault tolerance
		RAID 1 - Mirroring - Duplicates data for fault tolerance but req 2x disk space
		RAID 5 - Striping with parity - fault tolerant - requires one add drive for redundancy
## Network Redundancy
Load Balancing
	Some servers are are active some are on standby
	If active server fails the passive on takes it place
	Load Balancer types
		Round Robin
		Active/active =
			 both work but when one is down the other pikcs up the slack, both at 50% each
		active/passive =
			 when one goes down the other picks up 
NIC Teaming
	Load Balancing Fail Over (LBFO)
		Aggregate bandwidth 
			increased thruput and redudnant paths
		multiple nics 
			look like a single adapter 
## Power Redundancy
UPS - Uninterruptible Power Supply
	Short term back up power so you can save before it shuts down
	Types
		Offline/Standby
			not enabled unless power is lost
		Line-interactive
			As voltage slowly goes down, UPS voltage fills in the gaps
		On-line/Double conversion 
			Always online, always providing power
				The moment power goes it no interuption it is always on
Power conditioners - provide steady stream of electricity to units
Generators
	Long term backup
Dual power supplies
	Redundancy
	Essentially 2 PSUs
	Each should be able to run 100% of the load but would normally run 50% each
	Hot swappable
Power distribution unit(PDUs)
	Provide power outlet
## Replication
SAN Replication
	Share data between different devices
	Duplicate data from one data center to another 
		constantly replicate to allow transfer
	SAN - Storage area network
		Specialized high performance network of storage devices
	SAN Snapshot
		Create a state of data based on a point in time
		Copy that state to another SAN
VM Replication
	VM redundancy
	Maintain consistency and only have to update/maintain 1 VM
	also acts as a backup bc you can just load the premade software
	Only have to copy changes not duplicate the entire VM
On premises vs cloud
	Speed - local is faster
	Money - storage is expensive , cloud is scalable 
	Security - local is private, cloud is reliant on the provider
## Backup types
File backups
	Archive attribute
		Set when the file is modified
	Full backup
		everything 
		You want to make this one first
	Incremental
		Only files that changed since last incremental backup
		When you load the backup you need every single icremental backup
	Differential 
		Only files that changed since last FULL backup
		When you load you only need differental and full
		However everyday each diff backup gets bigger
		Archive attribute is NOT cleared
Backup media
	Magnetic tape
		Sequential storage
		100gb - multiple tb
		easy to store and ship
	Disk
		Faster
		Deduplicate and compression of data - more efficient
	Copy
		Exact duplicate
Network Attached Storage(NAS)
	Connect to shared storage device across the network
	File level access - if you need to change a portion of a file you need to rewrite the entire file
SAN
	Looks and feels like local storage device
	Block lvl access - only change the portion on the disk
Bakcup locations
	Offline location
		Fast and secure
		protected and maintained
	Online backup
		Remote network connected third party
		available anywhere
## Resiliency
Non persistence - cloud is always in motion
Snapshots - captures current config of the asset
	Can just load the snapshot
	Can take multiple and have different versions
	can roll back to known config but dont modify the data
High availability
	always on always available
	always have a higher cost
Order of restoration
	application specific
		Certain components might need to be restored first
	bakcup specific
Diversity
	Tech 
		0 day can affect a bunch of devices but if you have different security devices it can be avoided
	Vendors
		A single vendor can become a disadvantage
	Cryptographic
		All crypto is temporary
		Diverse CA can provide diff protection
	Controls
		Different controls allow multiple layers where you can fail 
Fail safe - unlocked when power is removed - defaults to being unlocked
	Operation > security
fail secure - locked whe power is removed - defaults to blocking
	Security > operation
# 2.6 embedded system
hardware and software designed for specific function
	built from only this task in mind - considered static environments
Arduino - Single board microcontroller
Raspberry Pi - highly successful, low-cost, single-board compute
System on a chip (SOC)
	Small form factor
	Integrates the platform functionality of multiple logical controllers onto a single chip
	An integrated circuit combining components normally found in a standard computer system
Field programmable gate array (FPGA)
	Integrated circuit taht can be configured after manufacturing
	Can just reprogram the fpga
SCADA - Supervisory Control and DAta Acquisition System Network
	sensors and control systems over a large area
	Industrial/energy/logistics
	Controls HVAC stuff
	Also called ISC - Industrial Control Systems
		the actual system that is used to control the thing
Building Automation System(BAS)
	Controls HVAC doors, lighting fire control etc but for "smart buildings"
distributed control systems
	Real Time Operating System(RTOS)
		Type of Os that prioritizes execution of operations to ensure consisten response time
	real time control
	requires extensive segmentation
Programmable Logic Controller- PLC 
	Computer designed for dpeloyment in an industrial or outdoor setting
Embedded hosts - systems that have OS burned into chips cannot change
Smart devices/IoT
	Sensors
	smart devices
	wearables
	facility automation
	weak default configs - easily hackable if not secured
Specialized
	Medical devices
	often using older OS
	Vehicles
		Intern entwork is often accessible from mobile
	Aircraft 
VoIP
	Each device is a seperate computer
HVAC
Drones
Printers/scanners/fax
	MFD - multi function devices - AiO
	some images are stored locally on the device, can be retrieved externally
	Logs can be stored as well
ISC/SCADA vulnerabilities
	Operational Technology 
		network designed to implment industrial control rather than networking
			Availabilitiy and integrity over confidentiality
	Human Machine Interface - I/O controls on a PLC to allow a user to configure/monitor the system
## Embedded System Communication
5G - 5th gen cellular networking
	10 gb/s
	slower from 100-900 mb/s
Subscriber Identity module - SIM
Narrowband
	Longer distances
	Conserve bandwidth
Baseband
	0 or 100%
	Bidirectional but not same time
Zigbee
	802.15.4 PAN 
	Alt to wifi and bt
	allows things to mesh
	Used in IoT
## Embedded System constraints
Mitigating Vulnerabilities
	Establish administrative control
	Disable unecessary links
	Devlop and testa  patch 
	Perform regular audits
Limited amt of features
not fully capable
Power is and issue
computational power
networking issues
difficult to change/modify crypto
difficult to patch
Auth is often an afterthought
	should be seperated
# 2.7 Physical Security
## Physical Security Controls
Physical Access Control system (PACS)
	Components and protocosl that facilitate the centralized config and security stuff
Bollards/Barricades
	Prevent access
	channel ppl
Access control vestibules
	All doors normally unlocked
		opening one door causes others to lock
	All doors normally locked
		unlocking one door prevents others from unlocking
	one door open, one door locked
		when one is open the other has to be locked
Alarm
Signs
	Clear and specific instructions
		keep ppl away from restricted areas
		Personal safety
	Informational
video surveillance
	CCTV
Industrial camouflage
	Conceal important facility in plain sight
Guards and access lists
	human interaction
	cost
	Access list 
	ID badge
	two person integrity/control
		no one person has access to asset
Biometric
Door access
	Lock and key
	Deadbolt
	Keyless/piun
	Token based - RFID badge/keyfob
Cable locks
	Temp security
	works almost anywhere
USB Data blocker
	Allow voltage reject data
Proper lighting - more light more security
Fencing - 
fire suppression
	Sprinklers - 
		wet pipe - filled with water all the way to the head and waiting for the bulb to be melted or broken
		dry pipe - filled with pressurized air and only push water into the pipes when needed
		pre action - activate when heat or smoke is detected
	Clean agent system 0 fire suppression system that relies on gas to extinguish fire
		Used to be HALON
			Now it's FM-200
Drones
Faraday cage - blocks EM fields
Screened subnet- DMZ
## Secure Areas
Air gap
Vaults/safes
Hot and cold areas 
	optimize temp
Old server rooms used Halon
We now use F200
HVAC - connected to ICS and SCADA networks


## Secure Data destruction
Disposal can be a legal issue
Dont want crit info in trash
	Shred/pulverizer
	Degaussing - renders drive unusable
Reuse storage media
Certificate of destruction

# 2.8 Cryptography
## Crypto concepts
Confidentiality
Auth/Access control
Non repudiation 
Integrity
Homomorphic encryption
	usualy decrypt, perform function , encrypt
	This can perform calcs while its encrypted 
Diffie-Hellman Exchange (DHE) is a key negotiation and agreement protocol used in public key cryptography.
RSA is the de facto standard used to generate public and private key pairs in a PKI.
The Online Certificate Status Protocol (OCSP) is used to obtain the revocation status of digital certificates. It is used as an alternative to certificate revocation lists and enables clients to request and receive the electronic status of digital certificates automatically and in real-time

## Symmetric/Assymetric crypto
Symmetric
	Single shared key
		encrypt/decrypt is the same key
	Shared secret
	doesnt scale very well
	fast to use
Assymetric
	public key cryptography
	2 keys
		Public key - everyone has
			Public key can  be in possession of anyone and is used to verify the private key was used
		Private key
			Private key is used to encrypt that anyone can decrypt but only the private key can prove who it is
		Encrypt with public, can only decrypt with private
## Hashing and Digital sigs
Birthday attack - collision
hashes
	Represent data as short string of text
	Message digest
	One way trip - cannot recreate data
	Integrity
	Can be digital signature
Collisions
	When different input has same hash
Salt 
	Random data added to hash
Digital Sig
	Prevent collisions
		Use DSA< RSA< ECDSA or SHA
	Prove message was not changed
		Integrity
	POrove source
		Auth
	Make sure sig is not fake
		Non repudiation
	Sign with private key
	Verify with public key
Message Digest 5 - MD5
	128 bit hash
Secure Hash Algo 1 /SHA-1
	160 bit hash
SHA 2
	SHA 224, 256, 348, 512
	256 bit fixed output
SHA3
	224-512 bits
RACE Integrity Primitve Evaluation Message Digest - RIPMEMD
	160 bit fixed output
	160, 256, 320 bit hash
NTLM - 128 bit output
HMAC - hash algo to creat lvl of aussrance
Hash security
	Key stretching - increase the time needed to crack it
		Regen until its secure enough
		Change weak key into strong key but feeding it into an algo to get a stronger one
	Key exchange 
		generating and exchanging a asymmetric key for session
		or exchanging public keys to use for PKI
	Key Streaming
		Sending individual characters through algo and using XOR function to change output
Key stretching algorithms
	bcrypt
		Hashes from passwords
		Multiple rounds of blowfish
	Password Based Key Derivation Function 2
		RSA based
## Cryptographic keys
Stream cipher - uses a keystream generator to encrypt data bit by bit using XOR funct
Block cipher - breaks data into fixed length blocks
	ECB - weakest
	GCM - data integrity and confidentiality
Symmetric algos 
	DES - 56 bits old standard
	3DES - 3 seperate keys(3 DES)
	IDEA - 64 bit blocks
	AES - 128, 192 or 256  bit blocks, standard for  US govt
	Blowfish - 64 bit blocks and variable legnth encryption key
	Twofish - 128 bit blocks and 128, 192, 256 bit encryption key
	RC 4, 5, 6 - RC4 used in WEP
Asymmetric keys
	Diffie Hellman
		Used to conduct key exchanged
		used in IPSec
	RSA
		 widely used
		 Rijndael
	ECC
	
## Blockchain Technology
Distributed ledger
	Everyone maintains ledger
Payment processing
Digital ID
Supply chain monitoring
Digital voting
1) Transaction
2) transaction is sent to every node to be verified
3) verified trans is added to new block of data
4) hash is calculated from previous blocks
## Cryptography Use cases
Low power devices
	Use Elliptic curve cryptography(ECC) for asymmetric encryption
Low latency 
	Symmetric encryption
High resiliency
	Larger key sizes
	Hashing provides data integrity
Confidentiality
	Secrecy/privacy
Integrity
	Prevent modification
Obfuscation
	encrypted data hides the code
Authentication
	Password hashing
	Protect original password
	add salt
Non repudiation
	Confirm auth of data
	digital sig confirms integrity and non-repud
## Cryptography limitations
Speed
	Adds overhead
Size
	AES is 128bits/16 bytes
	Encrypting 8 bytes would require 8 more bytes
Weak keys
	WEP used weak Initialization Vector in RC4
	
Time
	Encryption and hashing takes time
	Larger files take longer
Longevity
	specific crypto tech can become less secure over time
Predictability and entropy
	RNG is critical 
	Hardware random number gen can be predictable
Key reuse
	Reusing the same key reduces complexity
	if key is compromised everything is at risk
Resource vs security
	Real time applications cannot have a delay
## Secure Protocols
Real Time Transport Protocol(RTP)- Secure RTP
	Adds security feat to RTP
	Uses AES to encrypt voice//data
	Uses HMAC-SHA1 for auth and integrity
Time Synchronization
	NTP has no sec features
		Used in amplified DDoS 
	NTPsec - secure NTP
Secure/Multipurpose Internet Mail Extensions
	Public private key encryption mechanism
	Allows digital signature
	However requires a PKI or similar to spread Public keys
Secure POP3 - STARTTLS extension to encrypt
Secure IMAP - IMAP with SSL
If mail is browser based always encrypt with SSL
WEB
	Secure sockets layer/Transport layer security - only use TLS now
	HTTPS - HTTP over TLS
		Uses public key encryption
		Private key on server
		Symmetric session key is transferred using asymmetric encryption
	Transport Layer Security - TLS
		Uses one or more PKI certs to secure comms
		
IPsec 
	Allows you to send information over public internet but encrypt data so info is confidential
	Confidentiality/integrity/anti-replay
	Standardized
	2 core IPsec protocols
		Authentication Header(AH)
		Encapsulation Security Payload(ESP)
File Transfer
FTPS - File transfer protocol secure - FTP-SSL or TLS
SFTP - SSH file transfer protocol only SSH
Lightweight Directory Access  Protocol - LDAP
	Protocol for reading and writing directories over an IP network
	X.500 specification written by International Telecommunications Union(ITU)
	Originally called DAP 
	LDAP is protocol used to query
	LDAPS - LDAP over SSL
Simple Authentication and Security Layer
	Provides authentication using different methods
	Can be used by LDAP for security as well
SSH - Secure SHell Port 22
	Encrypted termianl communication
	Replaced Telnet and FTL
	Provides secure terminal communication and file transfer features
DNS Port 53
	Originally had no security
	DNSSEC - DNS Security Extentions
		Validate DNS responses
		Done using Public key cryptography
Simple Network Management Protocol v3 - SMNPv3
	Confidentiality
	Integrity
	Authentication
DHCP - no secure version or built in security
	In Active Directory - DHCP servers must be authorizied 
	Switches can be configured to only allow DHCP from trusted interfaces.
	DHCP client DoS - Starvation attack
		Switches can be configured to limit number of mac add per interface
			Disable interface when multiple MAC add are seen
# Endpoint Protection
## Endpoint
User access
	Stop the attackers 
	inbound and outbopund attacks
	a lot of platforms
Antivirus/anti malware
	Typically uses signatures - set pattern in file
End point detection and response (EDR)
	Monitors endpoints
	Uses different ways to detect a threat
	Signatures arent the only tool
	Behavioral analysis - machine learning
	Lightweight agent on endpoint
	Can investigate the threat
	Can respond the threat
	Can be used to view status on endpoints
	Can be used to analyze endpoint status
Data Loss Prevention(DLP)
	Stop data before attacker gets it
		Data leakage
	So many srcs so many dst
		many diff systems
Next Generation Firewall(NGFW)
	OSI Applicaiton layer scanner
		All data in every packet
	Application layer gateway
	Deep packet inspection
	Stateful multilayer inspection
	Broad security controls
	URL filtering capability
Host based firewall
	Software based
	Personal
	Allow/disallow incoming outgoing 
	able to see in the clear traffic
Host based IDS - HIDS
	Detect intrustion
Host based IPS - HIPS
	Prevent intrusion
	Signature, heuristics, behavioral\
User and Entity Behavior Analytics(UEBA)
	System that can provide an autopmated identification of sus activity by user
	Heavily dependent on AI and ML
## Boot Integrity
Boot is perfect infection point
Has same rights as the OS
Secure Boot
	UEFI Bios Secure Boot
	BIOS includes the manufacturer's public key
	Digital sig is checked during bios bpdate
	Secure boot verifies the boot loader
		Checks the bootloader's digital sig
		Must be signed with trusted cert or manutally verified
Trusted Boot
	Boot loader verifies digital sig of OS kernel
	Kernel verifies all the other start up components
	Just before loading drivers it starts Early Launch Anti-Malware - ELAM
		Checks every driver, if it fails then it will not be loaded
Measured Boot
	Checks nothing on this computer has changed
	UEFI stores a hash of firmware, boot drives and everything else loaded during Trusted Boot and Secure boot
	Remote Attestation - Device provides a central management server with a verification report of all info thats been gathered
	Encrypted and signed with TPM
	Attestation server receives boot report and changes are reported and monitored
Chain of trust
	Security is based on trust
	Trust has to start somewhere
Hardware root of trust
	Difficult to change
	Hardware Security Module - Card that is added to the system and contains a crypto processor
Trusted Platform Module(TPM)
	Specification for crypto functions
	hardware to help with encryption
	Might have persistent memory for burned in unique keys
	Might have RNG 
	Password protected, built with anti brute force tech
## Database security
Tokenization - replace sensistive data with placeholder 
	Isnt encryption or hashing - no overhead straight up replaced value
Hashing a password
	Hash represents fixed length - message digest
	Hopefully will not have collision
	One way trip Cannot go back
## Application Security
Input validation
	applications verify that info received from user matches specific format or range of values
Dynamic analysis - run while code is running
Static - run while code is not running
	Fuzzing is used to test input validation
		Random input to application to try and find system failures
Secure Cookies 
	Sensitive info should not be in cookies
HTTP secure Headers
Code signing
	Trusted CA signs the dev's public key
	Developer signs the code with private key
Allow/deny list
Static Application Security Testing(SAST) 
	Helps idenitfy security flaws
## Application Hardening
Minimize attack surfaces
Remove all potential known vulns
Some hardening might be external mandates
Close open ports
Control access with firewall
SCCM - Mirosofts System Center Configuration Management
Registry - windows, thousands of settings
	Disable SMBv1
Disk Encryption
	Encryption protectsd ata confidentiality
	Advanced Encryption standard - symmetric key encryption that supports 128 and 256 bit 
	Prevent access to application data
	Full Disk Encryption(FDE)
		Provide confidentiality for an entire data storage device
	Self Encrypting drive (SED)
		Hardware based
		Opal Storage specification
File integrity
	Done by hashing
Operating system hardening
	Categories of updates
		Security update - security related vulnerability
		Critical update - specific prob addressing a critical non sec bug
		service pack - tested cumulative grouping of patches,hotfix and sec patches
		Windows Update - recommended update to fix non critical problem
		Drive updare - updated driver to fix sec issue or add feature
# 3.3 Loadbalancing
## Loadbalancer
Distribute the load
Large scale implementations
Fault tolerance
Load Balancer - manages load across multiple servers
	TCP offload
	SSL offload
	Caching 
	Prioritization
		QoS
	Content Switching
Configs
	Round Robin - each server is selected in turn
		Weighted - prioritize server use
		Dynamic - Loadbalancer sends to lowest use
	Affinity 
		User communicating through that loadbalancer is always communicating with hte same server - Session IDs
	Active/Passive
		If active server fails, passive automatically takes it place
	Active/active 
## Network Segmentation
Physical Logical or virtual
Reasons
	Performance
	Security
	Compliance
Physical Segmentation - air gapped
	Multiple assets taht are seperately maintained and upgraded powered while not fully utilizing the switches
Logical Segmentation with VLANs
	Virtual LANS
		Logical only
		Segment the network
		Reduce collisions
		Organize the network
		Increase security
Extranet - private network for partners
	Only allows access to auth users
Intranet - internal private network
East-west traffic
	Traffic between devices in the same data center
	Relatively fast response times
North south traffic
	Ingress /egress from outside device
Zero Trust
	Most networks are relatively open on the inside
	0 trust is trust nothing on your network 
		Everything must be verified
Bastion Hosts
	Internet facing servers that have to be used to internet
	Left in DMZ and hardened bc its web facing
	Web/email servers
Jumpbox
	hardened server that provides access to hosts in the DMZ
	should only have minimum required software
	only thing that has permissions to go through the firewall and touch the dmz
## Virtual Private Networks
Encrypted private data traversing a public network
VPN Concentrator
	Allows for hundreds of simultaneous VPN connections
		Split tunnelling - machine diverts internal traffic over VPN but external traffic over their own connection
	Encrypton/decryption access device
	Often integrated into a firewall
	Used with client software
Remote Access VPN
	Always on option
SSL VPN - uses 443 port
	Almost no firewall issues
	No big VPN clients
	Just remote access communicaiton
	Authenticate users
		No reqs for digital certs or shared passwords
	Can be run from a browser
HTML5 VPN
	Supports Application programming interface
	Create VPN tunnel without seperate VPN application
	HAve to use a HTML5 browser (almost all)
FULL tunnel
	Everything transmitted by the user to the VPN concentrator
		VPN concentrator decrypts it then decides where it is going
		Even if the dest is not in the corporate network it still goes to VPN concentrator to go back to the user.
Split tunnel
	Admin of VPN can configure some info going into tunnel, and some going out
Site to Site VPN
	L2TP - Layer 2 Tunnelling Protocol
		Usually used L2TP with IPsec
IPsec
	Security for OSI layer 3
	Transport mode/tunnel mode
		Original packet - IP HEADER | DATA
		Transport mode - IP Header | IPsec Headers | Data |IP sec Trailers  - encrypted data but CT header
		Tunnel Mode - New IP Header| IPsec Headers | IP Header | Data | IPsec trailers - encrypted IP header and data
Authentication header - AH
	Hash of packet and a shared key
		Usually SHA-2
	Only provides data integrity and authentication
	Does not provide encryption
Encapsulation Security Payload
	Encrypts and auths tunnelled data
		SHA-2 for hash
		AES for encryption
		Adds header, trailer and Integrity Check Value
		Often Combines AH and ESP
## Port Security
Broadcast
	Send info to everyone at once
	Every single device has to look at that packet
	Can cause DoS
	Used by Routing Updates and ARP Reqs
Loop protection
	2 switches can send traffic back and forth forever
	802.1D to prevent loops
Spanning Tree Protocol
	Root port 
	Designated Port
	Blocked Port - Blocked ports so loops dont occur
BPDU Guard- Bridge Protocol Data Unit 
	If application
DHCP snooping
	Switch can be configured with trusted and untrusted DHCP sources
	Switch watches for dhcp conversations
		then filters the dhcp convo
MAC filtering
	limit access through physical hardware address
	keeps neighbors out
	MAC add can be spoofed
	Security through obscurity
## Secure Networking
DNSSEC
	Validates DNS resp
	Origin auth
	Data integrity
	Uses Public Key cryptography
Can use DNS for security - stop user from visiting dangerous sites
	DNS resolves to sinkhole add
Out of band management
	If network isnt available network management has seperate management interface
		Connect a modem to dial into the device
	Might have centralized console router/comm server
	Wireless routers behave as hubs do, clients exist in a single collision domain
QoS - prioritize traffic
IPv6 security
	More difficult to ip/port scan
	Tools already support ipv6
Taps and port mirrors
	Physical taps 0 disconnect the link and put a tap in the imddle
	port mirror - software tap
	Port mirroring 
		 One or more switch ports configured to forward all packets to another port on the switch
FIM - File integrity monitoring
	Some files never change
	If it changes then alarms go off
	Ex. SFC
## Firewall
Stateless firewalls
	Does not keep traffic of traffic flows
	Each packet is individually examined
	Can allow malicious packets through bc it blindly follows rules
Stateful firewalls
	Remember the state of the session
	everythign within valid flow is allowed
UTM - Unified Theat Management
	Web security gateway
	URL filter
	Malware inspect
	Spam filter
	Router/switching
	Firewall
	IPS/IDs
	VPN endpoint
NGFW
Web Applicaition Firewall - WAF
	Applies rules to HTTP/S communications
	Part of PCI CSS
Firewalls
	ACLs
		Groupings called tuples
		Logical path - top to bottom
## Network Access Control
Access control
	Control where you are
	Control based on rules
	Access can be revoked or changed
Posture Assessment
	BYOD - Bring your own device
	Malware infections
	Unauth appli
Persistent agents
	Perm installed
	PEriodic updates
Dissolvable agents
	No agents req
	runs during posture assess
	terminates after
## Proxy Server
Sits between users and networks
Useful for caching, access control, URL filtering and content scanning
Transparent - invidisble
Forward Proxy
	Internal proxy
	Commonly used to control user access to internet
Reverse Proxy
	Inbound traffic from internet to your internal service
Open Proxy
	Third party uncontrolled proxy
## Intrusion Prevention
NIDS and NIPS - Network IPS/IDS
Watches Network traffic
 Detection - Alarm or alert
Passive minitoring
	Examine a copy of the traffic - Port Mirror or Network Tap
	No way to block/prevent traffic
	Out of band responses
		When malicious traffic is identified IPS can send TCP RST(reset) frames
			After the fact
			Limited UDP response avail
Inline monitoring
	IPS sits physically in line
	In band resp
		Malicious traffic is immediately dropped and identified
Identification techs
	Signature based
	Anomaly based
	Behavior based
## Other Stuff
Jump Server
	Access to secure network zones
	Highly secure network zones
	Hardened point to jump to a server then jump to the servers
	Significant security concern
Hardware Security Module(HSM)
	Is a card that is added to the system
	Manages large amt of keys etc in your enviroment
	usually have tons of redundancy
	Key backup storage
	Cryptographic accelerators
Sensors and collectors
	Aggregate information from network devices
# Wireless
## Wireless Cryptography
Securing a wireless network
	Authenticate the users before granting access
	Ensure all communication is confidential
	Verify integrity of all comms
		Message Integrity Check(MIC)
Encrypt the data
	WEP - Wired Equivalent Privacy - look for answer with IV
		24 bit IV, original wireless security
		Weak due to 24bit IV
	WPA - Wifi Protected Access - look for TKIP and RC4
		Used TKIP, Message Integrity Check and RC4 encryption
		Temporal Key Integrity Protocol - 48 bit
	WPA2
		Wifi Protected Access 2 - Look for CCMP and AES
		Confidentiality with AES 128 bit
		AES with CCP
		CCMP - Cipher Block Chaining Message Authentication Code Protocol
			MIC is CBC MAC
	WPA3
		GCMP - Galois/Counter Mode Protocol
		AES with GCMP
		Same AES confidentiality
		MIC is GMAC
	WPA2 has a presharekey brute force problem
		Once you have PSK it's over
	WPA3 chages the PSK process
		Removal of the PSK
		Includes mutual auth
		Creates shared session key without sending that key across the network
		Perfect forward secrecy - new key everytime a new session is made
		Uses SAE
Simultaneous Authenatication of Equals(SAE)
	Everyone uses the diff session key even though its same PSK
	it creates a strong shared secret without needing to pre-share a key.
Perfect Forward Secrecy/Forward Secrecy  -PFS
	SAE provides assurance that session keys will not be compromised even if long term secrets are compromised
	Strengthen session keys
## Wireless Authentication Methods
Credentials
	Pre-shared key - PSK
	Centralized auth - 802.1x
		802.1x - standardized framework for port based auth on wired/less networks
Configs
	WPA2- personal is PSK
	WPA2 - enterprise is 802.1x
	Open System - no passwd
	WPA3 - Personal - PSK
		AES 256 encrption with SHA 384 hashing
	WPA3- Implemented RADIUS auth
		CCMP 128 as encryption
Captive portal
	Authentication to a network
	Access table recognizes lack of authentication
		redirects the web access to captive portal page
		Asks for authenticaiton factor
		Once approved web session continues
Wifi Protected Setup - WPS
	Allows easy setup of the mobile device
	Different way to connect
		PIN, Push button, NFC
## Wireless Authentication Protocols
Extensible Authentical Protocol
	Authentication Protocol
	EAP integrates with 802.1x
PAP - sends stuff in clear text 
802.1x - Port based Network Access Control
	Used in conjunction with access database
	supplicant - client
	Authenticator - device that provides access
	Authentication server - validates the client credentials
EAP Flexible Authentication via Secure Tunneling
	EAPFAST
	Auth Server and supplicant share a protected access credential(shared secret)
	Supplicant recieves PAC 
	Supp and AS mutually authenticate and negotiate a TLS tunnel
	User Auth happens over TLS tunn
	Requires a RADIUS SERVER
LEAP - Cisco Proprietary EAP
Protected EAP
	PEAP
	AS digital cert instead of a PAC
	Client doesnt need digital cert only server
	MS Challenge Handshake Authentication Protocol v 2
	Generic Token Card - GTC
EAP-TLS
	Strong security wide adoption
	Requires digital cert on all devices
	performs mutual auth on the network 
	then TLS tunnel is formed
	Requires PKI to manage deploy and revoke certs
	Some older certs dont support digital certs
	Requres both server and client to possess PKI cert
EAP Tunnel TLS
	EAPTTLS
	Only needs a single digital  cert on the AS
	Builds a TLS tunnel on this cert
RADIUS Federation
	Federation - link a user's auth over to network of another org
	RADIUS on backend
	EAP to auth
## Installing wireless networks
Site surveys
	Existing wireless landscape
	existing APs
	Heat maps
Wireless survey tools
	Signal coverage
	Interfeerence
	Builtin tools
	Spectrum analyzer
Wireless packet analysis
	Everyone hears everything
Channel selection and overlaps
	Overlapping channels
		Frequency conflicts
AP placement
	minimal overlap
	Maximize coverage
	Avoid interference
		Microwaves etc
	Signal control
		Avoid excessive signal distance
Wireless infra sec
	Wireless controller
		Central management of WAPs
## Wireless attacks
War driving - act of searching for wireless networks by driving around until you find them
War Chalking - act of physically drawing symbols in public places to denote open/closed/ protected networks in range
IV attack - Atker observes the operation of a cipher being used with several diff keys and finds mathematical relationship
WiFi Disassociation attack - forces a client offline then captures the handshake when it reconnects
Brute Force attack 
	continually guessing a password against one user
	multiple passwords, 1 user
Password spraying 
	brute force attack where large number of user is up against one password
	multiple users, 1 password
Spoofing - goal is to assume the identity
MiTM
Credential stuffing 
	brute force atk, same creds are tried against multiple websites
Broken Auth - auth mechanism lets atker gain entry
## Mobile Networks
Point to point
Point to multipoint
	802.11 wireless
		Wired Equibalent Privacy - claims to be as secure as a wired network
	Does not imply full connectivity between nodes
		Might have interferrence and issues
Cellular networks
	Mobile phones
		GSM - Unlocked uses a sim card
		CDMA - doesn't use a sim card, locked to a carrier
	Seperate land into cells
	Antenna covers a cell with certain freq
	Security concerns
		Traffic monitoring
		Locaiton tracking
		World wide access
Wifi
	Local network acess
	Data capture 
	On path attack
		modify attack
		deny data
Bluetooth
	High speed comms over short distance
		PAN
RFID - Radio Frequency Identification
	one way communication
NFC - Near field communication
	Two way wireless
	bootstrap for BT pairing
	Security concerns
		Remote capture
		10m for active devices
		DoS
		MitM attack
		Loss of device control
IR- Infrared
	Entertainment centers
USB - Universal Serial Bus
	Physical connectivity
	Physical access is always required
GPS 
	Requires at least 4 satellites to use GPS 
	Determins longitude, latitude, altitude
## Mobile Device Management - MDM
BYOD- Bring Your Own Device
Applicaiton management
	Manage versions and types 
	Not all appli are secure
	Manage by allow lists
Mobile Content Management(MCM
	Secure access to data
	Protect data from outsiders
	File sharing and viewing
Remote wipe
	Remove all data from your mobile device
Geolocation
	Precise tracking details
Geofencing
	Restrict or allow features when device is in a particular area
Screenlock
	Locking data
Push notif services
	Can show information
Containerization
	Seperate enterprise mobile apps and data
	Create a virtual container for company data
Full device encryption -FDE
## Mobile Device security
MicroSD - HSM
	Hardware Security Module in Microsd form
Unified Endpoint Management
	USM 
	Manage mobile and non mobile devices
Mobile appli management - MAM
SEAndroid
	Security enhancements for android
	SELinux
## Mobile Device Enforcement
Third party app stores
	Apple app store
	Google play
	Not all appli are secure
Jailbreaking - rooting
	allows to circumvent uncontrolled access
Carrier unlocking
	Most phones are locked to a carrier
	Security revolves around connectivity
	Moving carrier can unlock MDM
Firmware OTA
	OTA - over the air
	Automatically pushed to your device when ready
Camera use
	Not always a good thing
	Corporate espionage
	Camera can be controlled by MDM
SMS/MMS 
	Short message service/Multi Media Service
	Control of data can be concern
External Media
	Sd flash memory or USB lightning drives
USB OTG
	USB on the go
	connect mobile devices directly together
	USB 2.0 standard
Audio recordings
Geo tagging/GPS tagging
	Phone knows where you are in the metadata
Wifi Direct/Adhoc
	Connect wireless devices directly without access point
	WiFi direct 
Wifi hotpost/tethering
	Turning phone into wifi/hotspot
	Can be a vulnerability
Payment methods
	NFC or etc
## Mobile Deployment Modes
BYOD - Bring Your Own Device
	Employee owns device
	Difficult to secure
COPE - Corporate owned, Personally enabled
	Company buys a device
	Used as both corpoate and personal
	Org has full control over device
CYOD- Choose Your Own Device
	User gets to choose what device they want
COBO - corporate owned, business only
	Company owns the device
	Device is not for personal use
VDI/VMI
	Virtual Desktop/Mobile Infrastructure
	Data is securely stored and containerized
		in the cloud
	All devices connecting in connect to the same image 
	Centralized appl development
	write for one platform
	Update single application and can update all 
## Cloud Security Controls
HA across Zones
	Availability Zones - AZ
		Effectively self contained zone
	Build applications to be highly available(HA)
		can config appli to recognize what zones they are in
	Load balancer to provide seamless HA
Resource Policies
	Identity and Access Management(IAM)
		Determines who gets access
		What tehy get access to
	Map job funct to roles
	Set granular policies
	can centralize user accts
Secrets Management
	cloud computing has tons of secrets
		API keys, certs, passwords
	Can be overwhelming
	Authorize access to the secrets
	Manage an access control policy
	Provide audit trail
Integration/Auditiing
	Integrate auditing on diff platforms
	Cloud based SIEM
	Auditing
## Securing Cloud Storage
Cloud storage
	Data is on public cloud
		but not public data
		access must be limited and protected
		might be required in diff geographical locations
		back up required
		availability
Permissions
	Different options
		Bucket policies
		Globally blocking public access
		Don't put data in the cloud unless it really needs to be there
Encryption
	Server side encryption
		Encrypt the data in the cloud
		Data is encrypted when stored on disk
Replication
	Copy data from one place to another
	Data recovery
		Hot site for disaster recovery
	Data analysis
	Back ups
## Securing Cloud Networks
Cloud Networks
	Connect cloud components
	Users communicate
		public internet?
		VPn?
	Cloud devices communicate between each other
Virtual Networks
	Virtual servers, switches, routers etc
	same configs as physical device
	On demand 
	Rapid elasticity
Public and private subnet
	Private cloud
		All internal IP add
		Only connect through VPN
		No access from internet
	Public cloud
		External IP add
		Connect to cloud from anywhere
		Several independent tenants
		like a rental
	Hybrid
		Combines both
		Some resources are developed like private, some are like public
		Strict rules should be developed for this type
		One single tenant
		like a house
	Community
		Resources and cots are shared among several diff orgs who have common needs
		multiple cooperating tenants
		like a coop/hostel sharing stuff
	Multi cloud
		cloud consumer uses multiple public clouds
		different public clouds
		different rooms from different places
Segementation
	Cloud seperates VPCs, containers and microservices
	Data is separate from the applications
	Web Application Firewall(WAF)
	Next Generation Firewall(NGFW)
## Securing Compute Clouds
Security groups
	Firewall for comput instances
	controle inbound and outbound flows
	Layer 4 Port num
	Layer 3 address
Dynamic resource allocation
	Provision resources when they are needed
	scale up and down
Instance awareness
	Granular security controls
	Define and set policies
Virtual private cloud endpoints
	VPC gateway endpoints
		Allow private cloud subnets to communicate to other cloud services
Container security
	same security concerns
	Use container specific OS
	Group container types on the same host
## Cloud security Solutions
Cloud Access security broker(CASB)
	Visibility
		What apps are in use
		Are they auth ot use the apps
	Compliance
		Are they complying with regulations
	Threat prevention
		allow access by auth users, prevent atks
	Data security
		Ensure all data transfers are encrypted
		Protect transfer of PII with DLP
Applicaiton security
	Secure cloud based appli
	Common concern - appli misconfigs
Next Gen Secure Web Gateway (SWG)
	Protect users and devices
	Go beyond URLs and GET requests
	Examine appli API
	Examin JSON strings
Firewalls in the cloud
	Virtual firewall/host based
	Segementation between microservices/VMs or VPCs
	OSI layers Layer 4 - Layer 7
Security controls
	Cloud native security controls\
## Identity Controls
Identity provider (IdP)
	Authentication as a Service
	List of entities - users and devices
	Commonly used by SSO appli
Attributes
	Identifier or property of entity
	Personal - name, email , empl ID, phone num
	Dept name, etc
	One or more attrib for ID
Certificates
	Digital certs
		Assigned to person or device
		allows you to confirm someone you can trust
		Binds the identity of cert owner to public and priv key
			Requires PKI and a CA
	Token and cards
		Smart card, USB token
	SSH keys
		USe a key instead of user/pass
		Public/priv keys 
		critical for automation
		Key management is critical
## Account Types
User account
	Acct associated with a specific person
	Storage and files can be priv to that user
	Account you normally use
Shared accoount
	Used by more than one person
	guest login/ anon login
	very difficult to create an audit trail
	Password management becomes difficult
Guest account
	No access to change 
	no password
Service account
	Used exclusively by services 
	prevent services from being able to login - they shouldnt be able to log in in the first place
	access can be defined for a specific service
	commonly used usernames and password
		Need best policy for password updates
		Passwords do not frequently change 
Privileged accounts
	Access to one or more systesm
	full access to system
	Root/ADministrator
	Should not be used for normal administration
	Highly secured, 2FA, password changes
## Account policies
Control access to account
Permissions after login
Perform reoutine audits
Auditing
	Permission auditing
	Usage auditing
Password complexity and length
	Password entropy
		no obvious passwords
	Stronger passwords are at least 8 characters
	Prevent password reuse
	Password age minimum - requires users wait a certain amt of time to change password - prevents frequent password change
	Password age maximum - requires users to change passwd after a certain amt of time - prevents same passwd forever
Account lockout and siablement
	Too many incorrect passwords will cause a lockout
disabling accounts
	Keeps files and decryption
Location based policies
	Network location
	GPS
	GeoTagging
	Location based
## Authentication Management
Password keys
Password vaults
	manager
Trusted Platform Module 
	On motherboard
	TPM
	Cryptographic processor
	Specification for crypto function
	Used to store keys for encrypting hard disks
	persistent memory - keys are burned in unique
Hardware Security Module
	high end crypto device
	For servers
	Key backup
	crypto accelerators
	used in large enviroements
Knowledge based auth (KBA)
	Personal knowledge as auth factor
## PAP and CHAP
Password Authentication Protocol - PAP
	basic
	Sends info in the clear
Challenge Handshake Authentication Protocol - CHAP
	Not used for wireless auth
	Three way handshake
		after linke is established server sends challenge msg
		client responds with password hash calculated from challenge and passwd
		Server compares stored passwd hash with recieved passwd hash and compares the two\
	Used DES - weak
MS-CHAP
	PPTP - point to point tunneling protocol
	Used DES - weak
## Identity and Access Services
RADIUS - Remote Authentication Dialin User Service
	Centralize Auth for users
	Operates at applicaiton layer
	TACACS+ cicso proprietary
	Networking protocol that provices Authen, Author, accounting management 
	Doesn't support some protocols
	Encrypts only the password in acc-req packet
	Combins Authentication and Authorization
TACACS - Terminal Access Controller Access Control System
	XTACACS - 
		Completely encrypted so it is safe
TACACS+ - cisco proprietary RADIUS - Port 49
	Primarily used for device administration
	Seperates authentication and authorization
Kerberos - Network auth - port 88 -windows
	Open standard -
	Single sign on
	validity period
		Relies on NTP - Network Time Protocol
	Mutual authentication between client and server
	You get a ticket the first time, then just show the ticket
		Wristband in concert, your password is your money
IEEE 802.1x - 
	Port based Network Access Control
	Auth for wired and wireless
	Auth against a central auth database
OAuth - Authentication
OpenID - Authorization
## Federated Identities
Security Assertion Markup Language (SAML)
	Not designed for mobile apps
	Used to enable SSO across multiple web applications by secrely sharing user credentials in the form of SAML Assertions
OAuth
	Authorization framework
OpenID Connect
## Access Control
Mandatory Access Control 
	Most secure form of access control
	Computer system determines Access control
	Configure seperate levels
	Every object gets a label
	Labeling of objects uses predefined rules
Discretionary Access control
	The owner has control on who can access
	Can modify at any time
	Every  object must have an owner
Role based Access control
	Admins provide access based on the role of the user
	I,E, windows groups - if you're in hte group you get all the permissions
	non discretionary - users cannot modify the ACL of the object only what groups/roles they have
Attribute based access control
	USers has complex relationships
	Next generation auth model
	Uses context to grant access
Rule based access control
	Sysadmin sets the rules
	System checks ACL for access
Lattice based Access contorl 
	Uses math to create sets of objects and define how they interact
Privileged Access Management(PAM)
	Managing superuser access
	store privileged acct in a digital vault
		Privileges are given temporarily 
## Public Key infrastructure
Key management lifecycle
	Key generation - Make key
	Certificate Generation - Make cert
	Distribution - give it to users
	Storage - store keys somewhere
	Revocation - take away keys
	Expiration - delete keys
A digital sign adds a trust
Commercial certificate authorities
	Purchase your website cert
	Create a key, paid, send the public key to the CA to be signed
		Certificate signing request - CSR
		CSR should be submitted to CA in order to request a new digital cert
		Once a cert expires you have to ask for a new one! you cannot reuse the old one.
Private certificate auth
	you are your own CA
	Needed for med to large orgs
PKI Trust
	HEirachial
		Single CA issues certs to intermediate CAs
		Distributes cert management load
		Easier to deal with revocation of interm Ca than root
Registration authority(RA)
	Entity requesting the cert needs to be verified
Wildcard certs
	Allow you to save money by buying only 1 cert rather than multiple
	For subdomains only
	easiler to manage
	ex. \*.marines.gov covers \www.marines.gov mail.marines.gov etc etc
X.509 
	Standard used PKI for digital certs and contains owner/users info and CA's info
Subject Alternative NAme -SAN
	Certificate owner to specify additional domains and IP addr to be supported
Key Revocation
	Certificate Revocation List(CRL)
		used to identify invalid certs
		Large file that is revoked certs
OCSP - Online Cert Status Protocol
	Protocol that provides the validity of the certs such as good,revoked or unknonw
## Certificates file formats
X.690 uses 
	Basic Encoding Rules - BER
		Original ruleset governing the encoding of data structures for certificates 
		Multiple encoding allowed
	Canonical Encoding Rules - CER
		Restricted version of BER - only allows one type of encoding
	Distinguished ENcoding Rules -DER
		ONly allows one encoding type
		Most restrictive
Privacy Enahcned Electronic Mail - PEM
	.pem
	.cer
	.crt
	.key
Public Key Cryptographic System # 12 - PKCS#12
	.p12
Persoanl Information Exchange
	.pfx
PUblic Key Cryptographic Systems #7
	.p7b
## Cert Concepts
Online and offline CAs
	Distribute the load
	Then take the root CA offline
OCSP stapling
	provides scalability for OCSP checks
	OCSP status is stapled onto the SSL/TLS handshake
HTTPs Pinning
	Pins the expected cert or pk to applicaiton
	Compiled in the app on first run
	resist impersonation attacks by presenting a set of trusted public keys to user's browser as part of http header
PKI Trust Relationships
Single CA
Hierarchical
Mesh
Web of trust
	Sign certs of ppl you know
Mutual Auth
	Server auths with client
	Client auths with server
Key Escrow
	Someone else holds your decryption keys
Key Recovery Agend
	Specialized type of software that allows the restoration of a lost or corrupted key to be performed
Cert Chaining
	Chain of trust
		List of all certs between server and root CA
## Reconnaissance Tools
Traceroute/tracrt
netstat- network statistics
	-a all active commands
curl - client URL
	grab raw data
IPscanners
	ARP
	ICMP
	TCP ACK
	ICMP time
hping
	TCP/IP packet assembler analyzer
theHarvester
	OSINT
sn1per
	combines many recon tools
scanless
	proxy port scan
dnsneum
	enum dns information
	find host names
Cuckoo - sandbox for malware
Nessus - vulnerability scanner
logger - add entries to system log - syslog
## Shell and script enviro
SSH Secure shell
	TCP/22 
Powershell
	.ps1
python
	.py
## Packet Tools 
Also called protocol analyzer
	Promiscuous Mode
		Network Adapter is able to capture all packets on the network regardless of the MAC add of the frames
	Non-Promiscuous Mode
		Network adapter can only capture packets directly addressed to itself
Wireshark
tcpdump - innate to all OS
tcpreplay
## Forensic tools
dd  - copy drive
memdump - copy info in sys mem to stdout
WinHex - universal hexdec editor
FTK imager
Autopsy - digital forensics
Data sanitization
	Remove data
	one way trip
## incident Response process
IRT - specialized group trained and tested
	CSIRT - Computer security IRT
	Incident response manager - team lead
	security analyst
	triage analyst
	forensic analyst
	threat researcher
	cross functional support
		management
		exec
		hr
		legal
Reponse lifecycle
	Preparation
		Preparing for the incident
		training
		communication methods
	Detection and analysis/Identification - team identifies the incident and notifies the team
	Containment, eradication and recovery
		Reconstitution
	Post incident activity
		Lessons learned
Exercise
	Documenation Review
	Tabletop exercises
		Get key players together and talk through a simulated disaster
	Walkthrough 
		Get all players and step through
		Walk through each step
		involve each group
	Full scale 
Disaster Recovery plan
IR planning
	Establihs a IRT
Continuity of operations planning (COOP)
	not everything goes according to plan
## Attack Frameworks
Cyber kill chain
	Built by lockheed martin
		Recon
			attacker determins what methods to use
		Weaponization
			atker couples payload code
		Delivery
			Atk identified a vector to transmit the weaponized code
		Exploit
			Weaponized code is executed
		Install
			Allows actor to run remote access tool
		C2
			command and control
		Actions on objectives
			do things they wanted to do
MITRE ATT& CK
	knowledge base for cyber attacks and common atk procedures
Diamond Model of Intrusion Analysis
			Adversary
	Infrastructure                Capability
			Victim
		Model to describe cyber attacks
## Logs
Network logs
	netflow - summarization of the data
		Doesnt capture every packet only enough to give you an idea
		cisco network protocol that collects active IP net traffic that flows in/out of an interface
			point of origin
			destination
			volume
			paths on network
	sflow - sampled flow
		Open source netflow
	IPfix - Internet Protocol Flow information Export
		universal stnd for export of ip information
		Standard format to count data for companies i.e. tracking how much data you used on a cellphone plan
Metadata - data that describes other data by providing definition and descriptions
System log files
Application log
Syslog - standard for message logging - only for linux
	syslog - first one
	rsyslog - second
	syslog-np - newest more capabilities
Journalctl - commany line utility used for displaying logs from linux logging system
nxlog - multiplatform log management tool, opern soruce similar to rsyslog, syslog-ng
	Cross platform
## SOAR
Security Orchestration Automation Response
Runbooks
	Linear Checklist of steps to perform
	Step by step apporach to automation
	Largely automated
Playbooks
	Conditional steps to follow  - broad process
	Requires human interaction - which is where conditional steps come in
## Forensic Procedures 
IDentification
	Ensure scene is safe, secure and ID the scope of evidence to be collected
	Make sure the scene is safe
Collection
	Authorization to collect evidence is obtained
		warrant
	Document and prove integrity of evidence as it is collected
		make sure its an exact match of the data for analysis
		Prove integrity so no data is changed
Analysis
	create copy of evidence and use repeateable tools for analysis
Reporting
	Create a report of the methods and tools used in the investigation
Order of Volatility
	CPU registers, CPU cache
	Router table, ARP cache, kernel statistics, memory, temp swap files
	temp file systems
	persistent hard storage
		HDD/SDD/flash drive
	remote logging and monitoring data
	physical config/network topology
	archival media
RAM 
	Memory dump 
		grab everything in active ram
Sawp/pagefile
	place to store RAM when mem is depleted
	puts stuff onto storage
Snapshots
	Way to image VM
	Incremental between snapshots
Cache
	Store data for use later
FTK and Encase are forensic tools
Autopsy tool
## Security tools
tracert/tracerout - route of packet
nslookup/dig - dns
ipconfig/ifconfig 
	 displays all network configs and can be used to modify DHCP and DNS settings
nmap 
	open source network scanner by sending packets and analyzing their responses
ping/pathping 
	 determine if something is reachable
hping 
	open source packet generator and analyzer for TCP/IP
	used for security auditing
	craft packet however we want
netstat
	utility that displays network connections for TCP
	routing tables
	network int and protocol statistics
arp - look at ARP cache
route - view and manipulate IP routing
curl 
	transfer data too or from a server using protocols
theharvester
	py script to gather information from the network OSINT
sn1per 
	automated scanner that can be used during pentest to scan for vulns
scanless
	create a webserver to do a scan on a target
dnsenum
	look at all DNS server and DNS entries  for a organization
Nessus
	vuln scanne rthat can remotely scan a comp or network for vuln
Cuckoo
	Open source software for automating analysis of sus files
tcpdump 
	CLU that lets you look and capture network system - inherent to all OS
tcpreplay
	suite of utilities for editing and replaying network traffic
Forensics
	dd-
		copy disk images using a bit by bit copying process
	FTK imager 
		GUI tool
		data preview and imagine tool
		quickly look at electronic evidence
	memdump 
		CLU to dump sys mem to stdout 
	WinHex 
		disk editor and universal hex editor
	Autopsy
		Digital forensics platform and GUI interface
		Make hard to use cmd line tools easier with GUI
PenTest
	Metasploit-MSF
		comp sec tool that offers info about software vulns, IDS signature development and improves pentesting
	Browser Exploitation Framework - BeEF
		hook one or  more browsers and use them to launch commands and more attacks from within the browser
	Cain and Abel
		password recovery tool
			sniff the network and crack passwds using diction, brute force, cryptanlaysis,
			record VoIP convo
			decode scrambled passwords
			reveal password boxes
			analyze routing protocols
	Jack the ripper
		Open Source password cracker
## Legal
Legal Hold 
	Process designed to preserve all info in preparation for lawsuit
Chain of custody
	control evidence
	Maintain integrity
	Use hashes
Exculpatory evidence 
	proves innocence.
Inculpatory evidence 
	proves guilt
Demonstrative evidence, 
	evidence that attempts to recostruct the event
	presenting a physical object that displays the results of an event that occurred
Documentary evidence 
	directly supports or proves a definitive assertion.
	printed form of evidence 
## Security Controls
Managerial controls
	Controls that address sec design
	policies
Operations Controls
	Security guards, awareness programs
Technical controls
	Done by the system
Control Type
	Preventive
		Doesnt know about
		Doors, security guards
	Detective
		Intrusion detection
	Corrective
		used to correct a condition when there is either no control at all, or the existing control is ineffective
		a corrective control is temporary until a more permanent solution is put into place.
	Deterrent
		Knows about
		Discourages
	Compensating
		compensating control assists and mitigates the risk an existing control is unable to mitigate.
	Physical
		Door lock etc
## Security
Security Regulations
	GDPR - EU 
		Protects Sensitive Personal Information (SPI)
			information about race or ethnic origin, opinions, beliefs, nature
	PCI DSS - credit card
	Sarbanes Oxley - SOX
		deals with publicly traded corporations
		SOX - SPY SOXL etc
	HIPPA - Health
		PHI
	Gramm Leach Bliley Act - GLBA
		Deals with banks etc
		GL Bank Act
	FISMA - requ every agency to develop their own cybersec program
 Security Frameworks
	 CEnter for Internet Security Critical Security Controls(CIS CSC)
	 NIST Risk Management Framework(NIST RMF)
	 NIST CSF - CyberSec Frame
	 TTP - Tactics Techniques Procedures
	 NVD - National Vulnerability Database
		AIS - Automated Indicator Sharing
			 Govt Initiative for sharing real time cyber threat indicators
	ISO 
		27001 - Information Security Management System
		27002 - code of practice for ISMS
		27701 - Privacy 
		31000 - risk management 
	SSAE SOC2 Type 1/2
		SOC2 - Trust Services Criteria
			Firewalls, IDS, MFA
			Type 1-  tests controls in place at particular point in time
			Type 2 - test controls over time at least 6 months
	Cloud Security Alliance(CSA)
Security Configurations
	Web server hardening
		Access a server with your browser
		Updates
		Install PKI certificate and enable TLS/SSL
		Do not use administrative accounts
			use a user account with limited priv incase the server is compromised
		Network access and security - limited
Personnel Security
	Acceptable Use policies
		What is okay to use what is not
	Business policies
		job rotation
			No one maintains control for long periods of time
		Mandatory vacations
			Rotate ppl through jobs
			longer the vacation, the better chance for identify fraud
		Seperation of duties
			split knowledge
				no one has all of the details
		Dual control - 2 ppl must be present
		Clean desk policy
			When you leave nothing is on your desk
	Least privilege 
		rights and permissions set to bare minimum to do job
	NDA - non disclosure agreement
	User trainig
		Gamification
		CTF
		phishing simulation
		computer based training -cbt
	Role based security awareness training
## Third party risk management
Service Level Agreement - SLA
	Minimuim terms for services provided
Memorandum of Understanding -MOU
	Both sides agree on the contents of the memorandum
Measurement System Analysis
	Assess the measurement process
	Calculate measurement uncertainty
Business PArtnership agreement - BGA
	Owner stake
	financial contract
Non Disclosure Agreement - NDA
End of Life - EOL
	Manufacturer stops selling/supporting product
End of Service Life 
	No more support
	Premium support an option
## Managing Data
Data steward
	Responsible for data accuracy privacy and security
	Associates sensitivty labels to the data
Data classification
	Data types
	Data compliance
Data retention
	Keep files that change frequently for version control
	can help recover from virus infection
## Organizational Policies
Change management
	How to make a change
	Commonly referred to as config management
		Configuration control - contorlling changes that have now been baselined
Change control
	formal process
	avoid downtime, confusion etc
Asset management
## Risk management types
Acceptance
	We'll take the risk
Risk avoidance 
	stop participating
transference
	insurance
mitigation
	decrease risk level
Risk register
	Every project has a plan but also has risk
Inherent risk
	impact + likelihood
Residual Risk
	inherent risk + control effectiveness
risk appetite - how much risk you're willing to take
Qualitative - A opinionated risk assessment
Quantitative - hard nunbers
	Likelihood - Annualized Rate of Occurence - ARO
	Single Loss Expectancy - how much money is loss
	Annualized Loss Expectancy - ARO x SLE
Disaster types
	Environmental
	Person made
	Internal and external
## Business Impact Analysis
Recovery Time Objective - How long to get back up and running to particular point
	Work Recovery Time - WRT
		Time it takes to reintergrate and testing/upgrade
Recovery Point Objective (RPO) - Minimum requirements to get system running
	How much unavailable is aceptable
	Maximum amt of data(in time) org can afford to lose
Mean Time to Repair (MTTR)- Time required to fix the issue
Mean Time between failures (MTBF)- time between failures
Maximum tolderable Downttime - MTD 
	Longest period of time a business can be inoperable without causin catostrophic failure
Disaster Recovery plan - DRP
	Detailed plan for resuming operations after a disaster
Risk assessment - Probability something will happen and its impace - defined values
## Privacy and Data breaches
Information Life Cycle
	Creation and receipt
		Create data or recieve it
	Distribution
		Sorted and stored
	USe
		Make decisions and create product/services
	Maintenance
		ongoing data retrieval and data transfers
	Disposition
		Dispose or archive it
Data Breach ocnsequences
	Reputation damage
	Identity theft
	Fines
	IP Theft
Privacy Impact Assessment - PIA
	Privacy risk needs to be identified
## Data classifications
Proprietary 
	Property of organizaiton
	Trade secrets
PII - Personally Identifiable information
	Data can be used to identify an individual
PHI - Protected Health Information
Public/Unclass
	No restrictions
Private/Classified/Restricted/ Internal Use only
	Restricted
Sensitive
Confidential
	Very sensitive
Critical
	extremely sensitive
Data minimization
	Minimal data collection
Data masking
	Data obfuscation
Anonymization
	Makes it impossible to identify individual data from a data set
Pseudo anonymization
	Can be reversible
	replace personal info with pseudonyms
Data Responsibilities
	Data owner
		Accountable for specific data
	Data controller
		Manages the purposes and means
	Data processor
		Processes data on behalf of the controller
	Data steward/custodian
		resp for accuracy of data, privacy and security
	Data Protection officer
		Responsible for orgs data privacy policy
Business Continuity Plan
	Checklist review 0 BCP is distributed to each rep of each dept to ensure no major components have been left out
	Structured walkthrough - requires BCP to get together to review the BCP as a group
	Steps
		initiate Project initiation
		assess Business impact assessment
		Develop the plan
		test the plan
		maintain the plan
OVAL - Open Vulnerability and Assessment Language 
	Standard designed to regulate the transfer of secure public info across networks
	Language - XML schema used to define and describe the info being created
	Interpreter - reference developed tyo ensure the info passed  complies with scheams and defs
