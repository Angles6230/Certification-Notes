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
