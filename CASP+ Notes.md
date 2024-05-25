# Domain 4
## Data considerations

All data has a lifecycle associated with it

Data ownership and data sovereignty - cloud based servers and third party vendors or global

Risk - result of failure to provide for CIA

Confidentiality
 - how secure is the information and how secure does that info need to be?
 - Confidentiality failes if someone can obtain and view the data we are attempting to protect
 - If someone gains the file but it is encrypted, it is still confidential
 - Encryption
 
Integrity
- How correct is the info 
- Has it been modified in transit or in storage
- Hashing
- Checksums
- Failed if its modified

Availability
 - Data is available when and where it is needed
 - Uptime and accessible by end users
 - redundancy 
 - Disaster recovery plan
 - Fails if user is unable to use the data when needed 

Categorize potential risk 
	Low 	 - Limited 
	Moderate  -  More serious
	High - Severe and potentially catastrophic

Categorization is required by IS owned or used by USG FIPS

### Data Classification
Based on it's value to the org and sensitivity of the info if it were to be disclosed

Over classification leads to higher costs that are unnecessary

Two common classification schemes

Commercial business
 - Public  - No impact to company
 - Sensitive - Minimal impact 
 - Private - Info such as personnel record, salary etc
 - Confidential - Trade secrets, IP , source code etc

Military and Govt
- Unclassified - Released to public under FOIA
- CUI - Unclass but should be protected - medical records
- Confidential - trade secrets - seriously affect the govt
- Secret - deployment plans - seriously damage
- Top Secret - blueprints - gravely damage 

Protecting data takes resources 

Data should not be stored forever

Policies should be enacted for when data is retained or destroyed

### Data Types
Data type is a tag or label to identify data under subcategory under classification

Health data 
- Protected under HIPAA
- Labeled as PHI - Protected Helath Info

Financial Data
- Data used by internal management to analyze business performance
- sensitive bc access to data could provide investors unfair advantage
- Proprietary Corporate Information

Intellectual Property
- Proprietary Corporate Information

Personally identifiable information 
- Any info used to de-anonymize someone
- Bday, name, SSN
Cannot just categorize as unclass or top secret, consider its data type and subcategory as well

Format of this data
 - Organization of this info
 - Two common types
	 - Structured data
		 - Lists
	 - Unstructured data
		 - PPT or email, chat log etc
		 - Have to use specialized systems to parse that data

Data state
- Location of data within a processing system
- At rest
- In motion
- In use
### Data Retention
Set of policies 

How long you should keep a set of data

Legal requirements?

Maintains and controls certain data to comply with business policies and applicable laws and regulations

Listen to your lawyers
-  They know the exact requirements
Retaining the data
 - Preservation of data
 - Information thats kept for a specific purpose outside of an organizations data retention policy
 - Seperate Data preservation policiy
	 - Based on storage, processing capabilities etc
Backup method for data retention
 - Can put into tape drive
Data retention types
- Short term
	- How often yopungest media sets will be overwritten
- Long term
	- Data thats moved to an archive storage to prevent it from being overwritten
Think about if data is retained under short term or longterm methods

Make sure theres no lapse between the two 

How mcuh to backup?
- Wont have enough time, space, money to keep everythihng forever
- 1. Everything legally required to
- 2. Everything based on policies or based on policies
- 3. You decide what you need-  discretionary

Figure out how much to backup based off of Business Continuity plan or BCP
 - Define RPO - recovery point objective
 - I.e. if you can afford to lose a days worth of data - rpo is 24 hours
 - Budget fund based around RPO
RPO helps drive recovery window and redundancy

### Data Destruction
Data removal
- Ready for disposal at the end of its retention period
- Data is said to be expired
- Generic term that refers to any process that deletes or makes inaccessible any form of data
- Qucik ,easy may leave data remnants behind
- Only used with least sensitive data types

Destruction
- Makes an effort to destroy the underlying data
- i.e. overwrite the area of disk 

Sanitation
- Step further than data destruction 
- Performs verification function to ensure the data has been wiped and no longer accessibile

For high secret - might physically destroy hard drives

### Data ownership

Get input from stakeholders who own the assets

Stakeholders provide proper data classification

Process of identifiying the person responsible for CIA of the info asset

Data owner
- Senior exec 
- Maintaining the CIA of the Info asset
- They create the rules

Data steward
- Quality of data
- Making sure data is appropriately labeled and classified
- Make sure rules are being followed
- Should know about the data and its details

Data Custodian
- Handling management of the system assets are stored
- Enforcing Access control , encryption ,backup and recovery set yb the owner 

Privacy Officer
- Oversight on privacy related data such as PHI, PII, SPI
- On the hook for data breach
- Ensure compliant with legal and regulatory framework
- Properly doing data minimization
	- sovereignty
	- retention
	- data destruction

Should not be CIO or IT for everything owner, Data owner should be business side

IT can be data custodian
### Data Sovereignty
Principle that countries and states may impose on individual requirements on data collected or being stored within their jurisdiction

Protection only applies when you're within the walls of the country

GDPR - EU

If you have a website in US and use USD, an EU citizen buys from you, there is no GDPR protections for privacy as EU citizen left the EU to come to the store, You didnt target the EU citizen directly

## Risk Management
### Risk Strategies
Risk management is your primary job 

Finding ways to minimize the likelihood of certain outcome from occurring and achieving the outcomes we want

Faucets of Risk Management
- Risk Assessment
- Risk Measurement
- Handling
- Tracking
- Lifecycle
- Consideration

What and where is risk

Risk - Probability that a threat will be realized and a cotninual balancing act of a vulnerability against a threat 

Vulnerability - weakness in system configuration

Cannot fully control threats - can only minimize

Threat - anything that could cause harm loss dmg or compromise to IS

What can we do to minimize risk

### Risk Management Lifecycle

Identify
- Brainstorming the threats
- Considers all types of risks or uncertainties that may impact us to achieving a set of objectives
- Managing Information Security Risk - guide for risk management - NIST SP 800-39
- Frame - True goal in risk management - Establish a strategic risk management framework supported by key stakeholders at the top tier of organization

Assess
- Identify and prioritize diff business processes and workflows in the org
- Which assets are there and which assets support the workflows

Respond/Control
 - Mitigations in place to lower the risk we assessed
 - Categories of control
 - People
	 - Controls and mitigations 
	 - Reducing risk, increasing security through culture
 - Process
	 - Rules, regulations and oversight
 - Technology
	 - Right systems in place and automate them to make it smarter and effective
 - Protect
	 - Providing appropriate safeguard
 - Detect
	 - Defining appropriate activities to identify occurrence of an event
 - Respond
	 - Activities to take action against incident
 - Restore/Recover
	 - plans for resilience or restore capabilities

Review/Monitor

Evaluate the effectiveness of the risk response measures and identifies changes that could affect how risk can be managed

Risk Determination - conducted through performance of a formal risk analysis
 - Quantitative
	 - hard numbers
	 - Assign values to the asset, threat frequency, impact of threat realization
 - Qualitative
	 - Non numerical values, feeling or opinion
	 - Propoised impact severity
	 - Loss potential
	 - Likelihood of occurrence
	 - Con: Dollar values are not provided, hinders Cost benefit analysis

### Risk Types

Inherent - Risk is identifies but no mitigation is applied 
- Level of risk in place prior to taking any mitigating actions
- Always some inherent risk

Residual risk - Calculate the risk after mitigation and controls are applied

Risk Exception - risk created due to exemption being granted or failure to comply with corporate policy
- Should not be a way of life in your org, should be issued for a short period of time or while waiting for overall policy change

### Risk Handling
Only 4 things you can do with risk

Avoid - Strategy that involves stopping the risky activity or choosing an alternative\
 - eliminating hazards that could negatively affect us

Mitigate - Strategy that seeks to minimize the risk to an acceptable level an organization is willing to accept

Transfer - Transfer risk to third party, i.e. insurance company

Accept - simply accept the pain

Risk appetite - How much risk you're willing to accept before action is deemed necessary to reduce that risk
- Risk attitude or risk tolerance
As you add more security, usability decreases

### Risk Tracking

Systematically trakcing and evaluating the performance of risk mitigation actions against established metrics throughout the lifecycle of an identified risk

Risk Register - tool used to ideitify all potential risks  in a system or org

Should include
- Risk identified
- Description
- Level
- Likelihood
- Owner
- Mitigation measures applied
- Residual level

Scalability
- Agility of the system to handle the increase in demand

Reliability
- Measurement of probability that the system will meet certain performance standards

Availability 
- Percentage of time that the infra will be operational under normal circumstances

KPI - Key performance indicators

KRI - Key risk indicators - used to measure risk instead of performance
	 KRIs are supported by the underlying KPI
### Risk Assessment

Tool used to identify vulnerabilities and threats, assess impact and determine what controls to utilize

1. Identify assets and value
2. Vulnerabilities and threats
3. Probability and impact
4. Balance impacts costs with countermeasures
Assessments should be conducted prior to deploying any new system or technology

Can only be successful if supported by senior management

Likelihood of a threat - measure of the probability that a particular risk will be realized and impact your org
- Categorized by 
- Motivation
	- Acquisition or theft
	- Business adv
	- Damage
	- Embarrassment
	- Technical adv
- Source
	- Intneral
	- External
- Annualized rate of occurrence
	- Magnitude of impace - Estimation of the amt of dmg that a negative risk cna achieve or the amt of opportunity cost if a risk is realized
		- Single loss expectancy - Cost with each idividual threat that occurred
		- Annual loss expectancy - total cost over a year for the threat
	- Return on investment - how long it will take to make up fopr the expense by preventing risk from occurring
		- Determines the expected fiscal gains for improvements and balances cost of implementing changes
	- 6 types of loss
		- Productivity
			- Down time or repair time
		- Revenue
			- Outage and cannot make money
		- Data loss
			- Data is loss, takes time to perform recovery
			- Downtime leads to productivity loss
			- Data loss can require creation
		- Data compromise
			- disclosure or modification of data
		- Cost of repairs
			- Actual costs of software, hardware, labor to replace or repair
		- Loss of repuation
	- Calculating ROI
		- Payback - compared ALE against cost of implementation
		- Net present value - NPV 
			- Time value of money - money spent today is not the same as money spent tomorrow
			- Discount rate - makes tmmrw money equal todays money
			- Account for yearly savings by assumed discount rate 
			- Due to inflation, opportunity cost and other financial factors
		- Total cost of ownership - TCO
			- labor costs
			- Software costs
			- Can include admin costs, insurance premiums
		1. Industry benchmarks arent always representative for your org
		2. Minor risk should be covered by org not insurance
		3. Risk management softrware shjould be utilized due to complexity of risk
		4. Consider value of risk management - not onyl about the money
		5. TCO analysis doesnt instantly save you money, it is realized over time
		6. Org cannot solve all possible problems
	- MTTR- Mean time to repair/recovery 
	- Average time a device will take to recover from failure
	- MTBF - Mean time between failures
- Trend Analysis
	- Gap analysis - Performance we're experiencing and expected performance
		- Find out what caused this decreased performance 
		- Eliminate risks
		- Reduce downtime
	- Trend Analysis
		- Provide methods and processes to take historical data to provide future projection of risk
		- Provide good baseline

## Policies and Framework

### Policies
- Sep of duties
	- Preventative administrative control
	- Distribute approval and auditing across multiple duties
	- High risk functions should use proper seperation of duties
	- Dual control - two keys
	- Split knowledge - Two diff ppl have half of the required knowledge
- Job rotation
	- Different users are perform tasks of same position
	- Helps prevent and identify fraud
	- Also helps to crosstrain and backup primary
- Mando vacay
	- Require employees take vaca at one point 
	- Forces someone else to come in and do their job functions for them
- Least privilege
	- Providing users or services with the lowest level of access required to do their job functions
	- Identify job functions and restrict to the identified level of access
	- Need to know 
		- Not every user needs access to every single file
	- Easiest to create groups based off of their role then assign work groups
- Employment and termination procedures
	- Admin control that is focused on what to do when hiring and firing an employee
	- How they will be screened
	- How are they hired, onboarded, terminated and offboarded
	- Sign appropriate documents, privacy, use agreement, NDAs, cybersecurity training      
	- Employees may be cooperative during hiring, may not be cooperative during offboarding
		- During uncooperative termination, should be revoked immediately
- User training
	- Security awareness
		- Reinforce users with the importance of help 
		- What to do in an incident
		- Current threats
		- Should be developed based on intended audience
	- Security Training
		- Teach personnel the skills needed to do their job in a more secure manner.
	- Security Education
		- General in nature
		- Gain more expertise
- Auditing requirements and frequency
	- What are we auditing
	- How is it going to be reported
	- How often are we doing audits
	- May be based on contractual requirements
	- Know what you will audit, what the scope will be and to what level
### Frameworks
- States the role of security in an organization and establishes desired endstate of the security program
- Broad and provide basic foundation upon the standards baselines and guidelines 
- Organizational sec pol
	- Provides general direction
	- Framework to meet business goals
	- Define roles, responsibilities and terms
- System specific pol
	- Security needs of the specific technology
	- More technical
- Issue specific policies
	- Address specific issue such as email privacy or termination
- Categories
	- Regulatory
		- Mandatory Standards
		- Laws
	- Advisory
		- Acceptable activites such as AUP
	- Informative
		- Focus on certain topic, educational in nature
- Standards - used to implement a policy inside an org
- Baseline - Reference points that are documented for use as a method of comparison
- Guideline - Not require actions but recommended
- Procedures - Step by step instructions based off of the standard, policies and guidelines
- Enterprise security architecture frameworks
	- SABSA - Sherwood Applied Business Security Architecture
		- Who what where when why how of a problem
		- Six layers of SABSA
			- Operational
			- Component
			- Physical
			- Logical
			- Conceptual
			- Contextual
	- COBIT - Control Objectives for Information and Related Technology
		- Security control development framework 
		- Divides IT into 4 domains
			- Plan and Organize
			- Acquire and implement
			- Deliver and support
			- Monitor and evaluate
	- ITIL - IT service management framework
	- NIST SP 800-53
		- Security controls framework 
		- Developed by US DEpt of Commerece
		- Technical, operational or management control
### Regulations
- HIPAA - Health data
	- Affects healthcare providers and related facilities
- Sarbanes-Oxley -SOX
	- Publicly traded US Corporations
	- Must follow certain accounting methods and financial reporting
- Gramm Leach Bliley Act - GLBA
	- Affects banks, mortgag companies, loan officies, insurance companies, investment and credit card providers
	- Financial institutions
	- Security of PII
	- Prohibits financial informaiton sharing with thrid parties
- Federal Information Security Management Act - FISMA
	- Federal agencies
- Federal Privacy Act of 1974 
	- Affects any USG computer system that collects, stores, uses or disseminates PII
	- Only places requirements upon Federal agencies 
- Family Education Rights and Privacy Act - FERPA
	- Protects privacy of student education records
	- Applies to all schools 
- Computer Fraud and Abuse act - 1986
	- Defines hacking of protected computers
	- Computers that include financial records or govt info
- Economic espionage act of 1996
	- Affects orgs with trade secrets and for anyone who tries to use encryption for criminal activities
- Childresn Online Privacy Protection Act - COPPA
	- Imposes requirements on websites and online services that are directed to children under 13 yo
- Personal Information Protection and Electronic Documents Act - PIPEDA
	- Canadian
	- Requires orgs to obtain consent when they collect, use or disclose PII 
	- Have clear and readily available policies for their customers
- General Data Protection Regulation - GDPR
	- EU
	- Personal data cannot be collected, processed or retained without the individuals' informed consent
	- Can only be used for stated purpose
	- Purpose must be clearly described to the user in plain language, not in legalese
	- User has right to withdraw their consent at any time
	- Ability to inspect, ament or erase any data that is held about them
		- Right to be forgotten
### Standards
Created for specific industries to be followed as best practice
- PCI DSS - Payment Card Industry Data Security Standard.
	- Agreement that any org that collects, stores or processes CC info has to abide by
	- Contractual agreement and standard
	- Org must recieve external audit once a year
- ISO
	- Group of standards created as a series of best practices
	- ISO 27000 - Information System Security Measurement
	- ISO 27001 - How to manage Info sec
	- ISO 27002 - different info sec controls you can use
- CMMI - Capability Maturity Model Integration
	- PRocessed and behaviors that are used during development of software, products and services
	- Categoriezes orgs from 1-5 
	- 1 = Least mature
	- 5 = Most mature
- NIST - National Institute of Standards and Technology
	- NIST 800 series
	- NIST SP 800-53 - Security and privacy controls
	- NIST CSF - Cybersecurity framework
- Common Criteria - CC
	- Set of standards in which comp sys users can specify their security, function, and assurance requirements in a given system
	- Like the PG or R rating for movie
	- Evaluation Assurance Levels - EAL
		- Go from EAL1 to ELA7
		- Higher ELA means more cost
- Cloud Security Alliance's Security Trust Assurance and Risk or CSA STAR.
	- Publicly accessible registry that documents security and privacy controls
	- Standard that cloud providers are going to be compared against
	- Allows orgs to better understand their security and compliance postures
	- Two levels
		- 1 - Self assessment, Orgs submit to a security and privacy self-assessment against the Cloud Controls MAtrix and GDPR Code of conduct
		- 2 - Same as 1 but third party does the audit
### Contracts and Agreements
- SLA - Service Level Agreement
	- ability to support and respond to problems within a given timeframe providing the agreed upon level of service
- OLA - Operational level agreement
	- Internal agreement between different departments
- MSA - Master Service Agreement
	- Agreement for future agreements
- NDA - Defines what data is considered confidential and cannot be shared outside of the relationship
	- Administrative control not technical
- MOU - Memorandoum of understanding
	- Non binding
	- Letter of intent
	- Gentlemens agreement
- Interoperability agreements 
	- Binding agreements used during normal operations
- Interconnection security agreement - ISA
	- Agreement for the owners and operators of an IT system to document what technical controls each org has to meet for interconnection to happen
- BPA - Business Partnership Agreement
	- Between 2 business partners and establishes the conditions of that relationship
	- Outlines responsibilities
- Privacy Level Agreement 
	- Addresses which PII can be shared, with whom and how it is transmitted and exchanged securely and confidentially
	- If a piece of data can be used by itself or in combination with other pieces of dat to uniquely identify a person it is considered PII
	- Outlines in contractual terms how any third parties you deal with are going to ensure the information it hosts for you is not seen by the wrong set of eyes
### Legal Considerations
- Due diligence
	- Investigated all reasonable measures to address a given risk
	- Research aspect
- Due care
	- Having taken all reasonable actions to prevent security issues
	- Action aspect
- Export controls
	- Federal laws that prohibit the unlicensed export of certain commodities or information for reasons of national security or protections of trade
	- Military applications or economic protection issues
	- Concerns over destination country, organization or individual
	- Concerns about suspected or declared end use or end user
- Legal hold
	- Process that an org uses to preserve all forms of potentially relevant info when litigation or lawsuits are pending or reasonably anticipated
	- Org will suspend normal disposition or processing of records i.e. tape recycling, media archiving etc
	- E-Discovery
		- Discovery in legal proceedings such as lawsuits, investigations or FOIA requests
		- Electronic information has an intangible form, volume transience, persistence
		- Elec info is usually accompanied by metadata
- Third party attestation of compliance
	- Third-party came, audited and Stating that you met the requirements and you're compliant
### Integrating Industries
 - Rules are directive and specific in nature
 - Policies are easier to standardize because they are more generic in nature and don't usually provide specific solutions or methods
 - Confidentiality and encryption
	 - Some technologies are not allowed to be exported to certain areas of the world due to encryption strength due to export control
	 - May standardize to meet highest level requirements or segregate organization

## Business Continuity
### Business Continuity Plan
- Ensures an org is able to recovery from disruptive event or disaster
- Refers to the plans and processes used as a response during a disruptive event
- Disaster Recovery Plan - DRP
	- Specifically refers to plans and processes that are used during a disaster
- BCP is a plan for any disruptive event or in response to any type of threat
- BCP you plan for your primary, secondary and tertiary fallbacks
- BCP may include a DRP
- Resposibility of sernior managers for development of BCP
- Business Recovery Comittee 
	- Should include everyone from every dept
	- Identify and priority all systems that we need to support for the continuity of the business
- Define the scope of the plan otherwise subject to scope creep
	- Sr management must determine the level of risk they are willing to accept
- NIST SP 800-34 - 7 steps to perform in BCP
	- Develop a policy for contingency planning
	- Conduct business impact analysis
	- Identify preventative controls
	- Create recovery strategies
	- Develop the business continuity plan
	- Train, test, exercise the BCP
	- Maintain the BCP
- Hot sites
	- Up and running continously
	- No downtime
	- Expensive
	- What about physical things, not only data
		- Chairs, desks, chairs, network things, phones etc
		- Employees can walk in and start
	- Not used by most companies, only for mission critical items
- Warm Site
	- Get up and ready in a few days
	- Ex. has phones, power but not installed yet but can be ready in a couple days
	- Bit cheaper but reduce response time
- Cold Site
	- Even fewer facilities than a warm site 
	- Longer lead time
- Mobile Site
	- Uses independent and portable units to provide the recovery
	- DJC2
### Business Impact Analysis
- Functional analysis that is conducted as part of the development of the business continuity and disaster recovery plans
- Management level analysis that identifies the impact of losing organizational resources
- Mission essential functions - MES
	- Limited set of functions that must be continued throughout or resumed rapidly after a disruption of normal operations
- Four steps
	- Identify the crucial processes and resources in an org
		- Responsible parties will be assigned to gather info concerning them
	- Identify the impacts of an outage and estimate the downtime for crucial processes
		- each process will be assigned a criticality level
			- Critical - Should be back up within minutes or most 1hr
			- Urgent - stay down up to 24 hours
			- Important - 3 days
			- Normal - 7 days
			- Nonessential - up to 30 days
			- - Maximum Tolerable Downtime - MTD
		- Most amt of time a business can tolerate that asset or component being down
		- Maximum period of time disruption or MPTD
		- Maximum tolerable outage - MTO
		- Add RTO and WRT together
		- RTO - acceptable downtime
		- Work Recovery Time - Difference between MTD and RTO
			- Amt of time it takes to get the critical business functions back up and running once your hardware, software and config has been restored
		- Why MTD =/= RTO? 
			- Systems need to be sync'd, tested, data put back into system
			- This additional time is called WRT
		- Mean Time to Repair - MTTR 
			- Average amt of time it takes to repair an asset or component when a disaster or disruption occurs
		- Recovery Service Level - RSL
			- Percentage of how much computing power you need during a disaster
			- IF half the facility is destroyed by fire, you only need 60% of your computing resources up before you can say you are up
	- Identify your resource requirements
	- Identify the recovery priorities
		- Generally classified as high, medium, low
### Privacy Impact Assessment
 - Process of identifying and managing the privacy risks arising from new projects, intiatives, systems and other events 
 - Org will analyze its processes how they might affect or compromise the privacy of people whose data is collected, held or processed by the org
 - Conformance with legal, regulatory and policy requirements for privacy
 - Idetnify and evaluate the risks of privacy breaches
 - Identify appropirate privacy controls to mitigate unacceptable risks
 - Should be conducted whenever the orgn posssess sensitive information
 - Benefits
	 - Provides a warning system to detect problems and build safeguards
	 - Provides evidence of privacy risk prevention  attempts
	 - Helps imporve informed decision making by senior leaders
	 - Helps the org gain public trust and confidence
	 - Demonstrates that the org takes privacy seriously
 - Steps
	 - Intiate the project
	 - Conduct data flow analysis
	 - Conduct privacy analysis
	 - Publish the Privacy impact assessment report
 - Six steps to every good incipent respponse
	 - Detection 
		 - Need to detect the incident
		 - Logging, auditing
	 - Response
		 - Appropriate response to the incident
		 - How long each response should take
	 - Report
		 - How quickly should be reported and to what level
		 - Provide an acceptable baseline for employees to recover
	 - Recovery
		 - How do we recover
		 - Getting services back up
	 - Remediate
		 - Eliminiate any traces of the incident
		 - Getting services back to known good configuration
	- Review 
		- What caused it
		- How can we prevent in future
		- After Action Report - AAR
		- Lessons Learned Report - LLR
			- What worked what didnt how can we prevent etc
- Event - Change in state of security or operation, negative or positive
- Incident - negative event that impacts an org's security or operations
- CSIRT - Cybersecurity Incident Response Team
	- Incident Response Manager-  team lead
		- Oversees and prioritizes actions during detection, analysis and containment of an incident
		- Requires lots of soft skills
	- Security Analyst
		- Plays detective on the affected network to determine what happened
		- Triage Analyst
			- Assigned to work on the network and filter out false positives
		- Forensic analyst
			- More focused on detective work
			- Piece together what happened
			- Recover key artifacts and evidence
	- Threat researched
		- Provide threat intelligence and overall context during incident response
		- Keep up to date on previous incidents
### Testing Plans
- Checklists
	- List of items that are qreuied or things taht need to get done
- Walkthroughs
	- Basic training event
	- Having everyone gather around and describe the steps of the plan
	- At least quarterly
- Tabletop exercises
	- Discussion based session where team members discuss their roles and what they would do in response to a given scenario
	- Twice a year
- Full interruption test
	- Shut down in primary and shift to secondary
	- Actually test to see if our plans work
	- Annually or rotate with parallel or sim test one year, full interr another year
- Parallel test
	- Uses recovery systems that are built and tested to see if tehy can perform actual business to support
- Simulation test
	- Simulated disaster or incident response to discover if the response plans are good enough to work through those issues
## Risk Strategies
### Asset Value
- Assets can be tangible and intangible
- How to determine value of asset?
	- Value the asset has to the owner
	- Work required to develop or obtain the asset
	- Cost to maintain
	- Damage that  would result if lost
	- Cost competitor would pay for asset
	- Penalties that may arise if asset were lost
- Identify threats and vulnerabilities to that asset
	- Human
		- Insiders, outsiders, terrorists etc
	- Natural
		- Hurricanes, floods etc
	- Technical
		- failure of hardware or software, viruses etc
	- Physical
		- Failure of physical security measures
			- CCTV, Gate etc
	- Environmental
		- power, cooling, heating 
	- Operational
		- Process or procedure taht may affect one of our three tenets of IS - CIA
- Determine likelihood of threat or vulnerability being realized
### Control Categories
- Compensative
	- Used in place of a primary control to mitigate a risk
- Corrective
	- Reduce the effect of an undesirable effect
- Detective
	- detect and attack while its occurring 
	- notify proper personnel
- Deterrent
	- Discourage attackers
	- Signs
- Directive
	- Force compliance with security policy and practices within the organization
- Preventive
	- Prevent or stop attack from occurring in the first place
- Recovery
	- Recovery after an attack has happened
- Three types of controls
	- Administrative/Management 
		- Manage operational personnel through policies, standards, guidelines
	- Logical/Technical
		- Access lists, firewalls,
		- Auditing - one time evaluation
		- Monitoring - Ongoing process
	- Physical
		- Security badges, fences, locks
### Aggregate Risk
- 