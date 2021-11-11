# Active-Directory
##### The Active Directory was installed on a Microsoft Windows Server 2019 (GUI).


# Introduction
- Windows Server Features (some)
   - Dynamic Host Configuration Protocol (DHCP)
   - Domain Name System (DNS)
   - Preboot Execution Environment (PXE)
   - Remote Access
   - Internet Information Services (IIS)
- Lightweight Directory Access Protocol (LDAP)
- Kerberos
- Directory Services
- Active Directory Features
  - Single Sign-On (SSO)
  - Replication
  - Auditing
  - Security
- Active Directory Fundamentals
  - Domain
  - Domain Trees
  - Forests
    - Forest Design
    - Single Forest
    - Multiple Forest
   - Trusts
   - Forest Trusts
   - Domain Controller
     - Global Catalog (GC)
     - Read Only Domain Controller (RODC)
     - Replication and Failover Clustering
     - Knowledge Consistency Checker (KCC)
   - Organizatinal Units
   - Containers
   - FSMO
     - Forest Level
       - Schema Operations Master
       - Domain Naming Master
     - Domain Level
       - Primary Domain Controller (PDC)
       - Relative Identifier (RID)
       - Infrastructure Master
     - Failover		
- Domain Name System (DNS)
- Group Policy
- Active Directory Planning
- Managing Active Directory Objects
  - Managing Users
  - Managing Computers
- Active Directory Lightweight Directory Services (AD LDS)
- Active Directory Federation Services (AD FS)
- Active Directory Rights Management Services (AD RMS)
- Active Directory Certificate Services (AD CS)
 
- Bibliography

# Windows Server Features

### Dynamic Host Configuration Protocol (DHCP)

### Domain Name System (DNS)

### Preboot Execution Environment (PXE)

### Remote Access

### Internet Information Services (IIS)


# Lightweight Directory Access Protocol (LDAP)

# Kerberos

# Directory Services


# Active Directory
Active Directory is the leading directory service solution made by Microsoft. It was first introduced in Windows 2000 Server edition as an implementation of X.500 directory.
Active Directory uses LDAP as its primary access protocol. Active Directory stores information about a variety of objects in the network such as user accounts, computer accounts, groups, and all related credential information used by Kerberos. </br>
Active Directory can be deployed in one of five forms: Active Directory Domain Services (AD DS), Active Directory Lightweight Directory Services (AD LDS), Active Directory Federation Services (AD FS), Active Directory Rights Management Services (AD RMS), Active Directory Certificate Services (AD CS). </br>
This repository will focus on AD DS as it’s the most common product of Active Directory.

# Active Directory Features
## Single Sign-On (SSO)
There are many applications that require authentications from the user, sometimes different authentication methods. This can be both time consuming for user and I.T and a security problem, a common security problem is having users writing down their passwords on notes around the office due to one too many passwords to remember for each application. </br>
Single Sign-On as implied, requires the user to log in with a single user-ID and password for the whole session, Active Directory will provide the credentials needed for any further logins. Hence, the user won’t need to keep typing his credentials to get access.

## Replication
Active Directory could be implemented in small/centered organizations as well as vast organizations with many sites. The more complex organizations require multiple Domain Controllers, therefore it’s important for the Domain Controllers to maintain updated data throughout the sites. Active Directory maps the IP addresses of each site, this is done using the Subnet Mask. </br>
The replication is managed by the Knowledge Consistency Checker (KCC), a process that runs on the Domain Controllers and generates replication topology for the Active Directory forest. </br>
Identifying the organization’s needs and making an effective topology is crucial for the network’s performance.

## Auditing
Auditing helps to maintain regulatory compliance and the organization’s security. Auditing in Active Directory uses policies to store events, as with many Active Directory aspects this too can be a two-edges sword as the administrators would have to prioritize some events over others, policies cannot be too broad or too narrow. </br>
Auditing could be used in forensic analysis and in detecting anomalous behavior.

## Security
Active Directory stores in its databases vast amounts of information about the organization’s employees, this calls for protection. </br>
Active Directory supports various authentication methods, group policies and practices to use against threats, these solutions should be implemented by administrators, but must be followed by the employees. Administrators need to recruit the users for the task, while maintaining the group policies as well as updating the system.

# Active Directory Fundamentals 
## Domain
Domain refers to a collection of logical objects (users/computers/printers), each object has a unique identity, and a set of privileges that are administrated to follow the rules posed by the administrator. The domain can be viewed as a security boundary for the objects inside it, using different policies to maintain the organization’s security.
Domains differ from one to another by the domain identifiers (name, IP, physical hardware). </br>
Microsoft is well known for its backward compatibility, *for instance, Windows 10 still doesn’t allow for users to make a folder named “CON”.*  Active Directory supports backward compatibility as well, it’s called functional levels and allows for administrators to add domains with the same functional level as the forest, but a newer Windows Server edition. </br>
*Example: a forest functional level is 2016, the administrators have not yet upgraded to the newest functional level. In order for the administrators to add a domain, it must be at the same functional level as the forest, hence they could install a Windows Server 2022 and the Active Directory would support the functional level of Active Directory 2016.* </br>
This is an important aspect to different organization that don’t have the resources or the need for new features. With that being said, Microsoft ends their support for legacy servers/Active Directory as years pass.

## Domain Trees
A domain tree is a collection of domains, this can be viewed as a parent-child relationship whereas the domain tree is the parent, and the domain is the child. Just like a family, domains inside the domain tree share a contiguous namespace, but there can be only one parent domain in a domain tree. </br>
*Example: CongoRainforest.com is the forest domain name, the domain tree name is Mahogany.ActiveDirectory.com and the fully qualified domain name is Fruit.Mahogany.ActiveDirectory.com* 

## Forests
Active Directory forest represents the complete Active Directory instance, it has at least one domain and the collection of the domain trees, much like other directory services it is built in a hierarchical structure. All the domains/domain trees inside the forest are connected in a two-way transitive trust, hence data flows in both directions. </br>
Forests can contain non-contiguous domain names unless the domain names are in a domain tree.

### Forests Design
One of the most important aspects in a system is designing it in an efficient way, this applies to Active Directory as well. A good forest design could only be achieved after identifying the needs for the organization. </br>
Some documentations divide the Active Directory forest into 3 kinds of models: organizational forest model, resource forest model, restricted access forest model. </br>
I will divide the structure into two types of forest implementations, a single or a multiple forest structure. 

### Single Forest
A single Active Directory forest could be considered as a more simpler solution, it is the default mode. Most business models if not all could fit into this model, it’s significantly cheaper to maintain only one forest. </br>
Most documentation states that restricting yourself to one forest is the key to success.

### Multiple Forest
The multi-forest model is a must in some organizations, this adds to the already complexed and thought topology. Managing multiple forests require more administrators (I.T) as well as more physical hardware. There are several reasons as to why you should use the multi-forest model: </br>
- Organization acquisitions usually require some security boundaries </br>
- Isolation needed due to constant forest schema changes or due to vast organizations with multiple forests that share only common resources whilst keeping the other resources isolated in a different forest. </br>
- Many organizations are under strict regulations that require isolation between some departments. </br>

## Trusts

## Forest Trusts


## Domain Controller

### Global Catalog (GC)

### Read Only Domain Controller (RODC)

### Replication and Failover Clustering

### Knowledge Consistency Checker (KCC)


## Organizatinal Units

## Containers


## Flexible Single Master Operation (FSMO)

## Forest Level Roles
These roles are unique to each forest, hence only one of each in the forest

### Schema Operations Master

### Domain Naming Master

## Domain Level Roles
These roles exist in every domain, every Domain Controller maintains these FSMO roles.

### Primary Domain Controller (PDC)

### Relative Identifier (RID)

### Infrastructure Master

### Failover		


## Domain Name System (DNS)


## Group Policy


## Active Directory Planning


## Managing Active Directory Objects

## Managing Users

## Managing Computers


## Active Directory Lightweight Directory Services (AD LDS)


## Active Directory Federation Services (AD FS)


## Active Directory Rights Management Services (AD RMS)


## Active Directory Certificate Services (AD CS)


## Azure Active Directory
 
# Bibliography

