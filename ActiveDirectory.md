# Active-Directory
##### A simple guide to show different attacks on Microsoft Active Directory.
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
    - Forest Structure
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
Domains differ from one to another by the domain identifiers (name, IP, physical hardware).

## Domain Trees

## Forests

### Forest Structure

### Single Forest

### Multiple Forest


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

