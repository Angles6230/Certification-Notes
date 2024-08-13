AD Forest
Single isntance of AD
Every org has at least one forest
Highest level of org
 - includes domains
- configs 
- one AD Schema
  - Schema - Defines what is allowed to be stored within AD and how
domains within a forest share implicit trust with other domains
- Two way transitive trusts
-Also share common AD Schema
- Share Global catalog
   - Little data base that contains a refrence for all domains in forest but only with partial attributes
-Non contiguous namespace
Setting up DC on server core
Get-command *feature* 
get-windowsfeature *ad-domain*
install-windowsfeature ad-domain-services - installs binaries for AD
Configure AD
Install-addsdomaincontroller -domainname name -credential (get-credential)
Get-addomaincontroller - Get list of domain controllers
Get-Aduser -filter name- list AD users
Install from media - install from CD
 Advantages - adoiv replicating entire Ad over WAN, only changed items since IFM was created are replicated
 Install more than one AD DC
Ntdsutil
-Command line tool
Provides management facilities
Database maint tasks
Diag tools
metadata cleanup
Need to run from elevated cmd prompt

Generate IFM data file
ntdsutil
activate instance ntds
ifm
create sysvol full [Path]

Make IFM source available to a new server
-Share IFM folder 
- Copy over IFM folder to server
Server manager
-Promote server to a DC
-Add a DC to existing domain
Install from media - select IFM folder

