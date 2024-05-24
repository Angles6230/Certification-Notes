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
- Employment and termination procedures
### Frameworks
### Regulations
### Standards
### Contracts and Agreements
### Legal Considerations
### Integrating Industries