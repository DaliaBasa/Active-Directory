# Active-Directory-Attacks
##### A simple guide to show different attacks on Microsoft Active Directory.
##### The Active Directory was installed on a Microsoft Windows Server 2019 (CLI).


## Introduction
1. Windows Server Fundamentals
2. Active Directory Fundamentals
- Active Directory Lightweight Directory Services (AD LDS)
- Basics
  - Domain, Tree, Forest
    - Trusts
    - Forest Trusts
  - Domain Controller
    - Read Only Domain Controller (RODC)
    - Global Catalog (GC)
  - FSMO Explanation
			
- DNS
- Group policy
- LDAP
  - Directory Service
- Kerberos
 
10. Bibliography

## Windows Server Fundamentals
???

## Active Directory
#### The Active Directory system can operate in two distinct modes: as Active Directory Lightweight Directory Services (AD LDS) and as Active Directory Domain Services (AD DS).
The most significant difference between between AD LDS and AD DS is that AD LDS does not host domain naming contexts. A server can host multiple AD LDS DCs. Each DC is an independent AD LDS instance, with it's own independent state. AD LDS can be run as an operating system DS or as a directory service provided by a standalone application (ADAM).

Active Directory is a directory service made by Microsoft to give a solution to the IT infrastructure complexity within the growing numbers of users/devices in networks. 

Directory services allows an easy and quick storage, search and managment of resources within a network. The Active Directory works in a hierarchical way and allows the arrangement of resources based on DCs (Domain Controllers - databases), it is also a secutiry solution to vast networks.
Unlike Peer to Peer Network which is used in small networks, Active Directory is a centralised network managment, which uses databases that attain each user/device configuration.

Active Directory helps both IT/administrators and end users.

Users only need to login once and their files are stored in a repository which is accessible to other users from different domains/trees/forests.

Administrators/IT are enjoying the benefits of implementing group policies, having to make changes one time and push it for every computer in the domain, the same could be applied to security configurations. Storing vital information about the users in databases. The ability to make changes and apply them to domains are what makes Active Directory so keen.

### Active Directory Lightweight Directory Services (AD LDS)

Active Directory Lightweight Directory Services (AD LDS) is an independent mode of Active Directory, minus infrastructure features, that provides directory services for applications. AD LDS consists of a directory service that is accessible via the Lightweight Directory Access Protocol (LDAP). AD LDS is primarily intended for use by application software as a storage mechanism.

### Active Directory Domain Services (AD DS)

### Basics
- Azure - Microsoft's cloud, which can also run AD (was not used in the demonstrations in this repository) </br>
- DN - Distinguished Name. A string that uniquely identifies an object in Active Directory. </br>
- DIT - Directory Information Tree. </br> 
- Line of Business (LOB) - a general term which refers to a product or a set of related products that serve a particular customer transaction or business need. One of the set of critical computer applications perceived as vital to running an enterprise. 
- Namespace (NS) - Unique naming based on hierarchy and logic. </br>
- SID - Security Identifires. An identifier for security principals that is used to identify an account or a group. Conceptually, the SID is composed of an account authority portion (typically a domain) and a smaller integer representing an identity relative to the account authority, termed the relative identifier (RID).</br>
- SYSVOL - A folder which resides on each and every domain controller within the domain. It contains the domains public files that need to be accessed by clients and kept synchronised between domain controllers. Also keeps inside all files related to group policies and any startup scripts, logon scripts that were created and added to group policies. </br>
#### Domain, Tree, Forest
- An AD (Active Directory) domain is a group of users, devices that are part of the network (PC, printers, etc..), applications and other AD objects. They are all part of the domain, and are controlled by the DC (Domain Controller). An AD tree is a group of domains with a trust between them a parent-child relation and they share the same domain namespace.
Each domain is given a DNS name that identifies the domain.
  
- A domain tree is made up of several domains that share a common schema and configuration, forming a contiguous namespace. Domains in a tree are also linked together by trust relationships. Active Directory is a set of one or more trees. Trees have a unique namespace which they share with their domains.</br> _For instance, a tree name could be drive.google.com and one of his children (domains under him) would be named project.drive.google.com there could be no other tree with the same name (drive) in that forest._
- Forests are a set of one or more trees that do not form a contiguous namespace, all trees in a forest share a common schema, configuration and global catalog. Trees in a forest share the same attributes, and have a trust relationship. There can be more than one forest in an organization and they can be linked via trust authorization by both forest adminstrators. Multiple forests can be helpful in vast companies that are spread.

![forest pic](https://user-images.githubusercontent.com/90955504/133885246-7cfb043e-f0bd-49f7-831f-93cb99b803e5.png)

#### Trusts
A trust relationship is a logical relationship between two domains/forests which allows authentication. By default, a secure channel is used to check security information, including security identifiers (SIDs) of users and groups.
This secure channel can be extended to other Active Directory domains by creating trust relationships between multiple domains or multiple forests. There are 2 different trust relationships:
- One-way trusts relationships are valid in one direction.
- Two-way trusts relationships are valid in both directions.
- Explicit trust is a trust that's created manually by the system administrator.
- External trust is a trust between domains that belong to different forests.

This relationships can be either transitive or non-transitive.
- Transitive trusts, as long as there is trust between the domains a user can access these trust paths.</br>  _Example: if domain A trusts domain B, and domain B trusts domain C, when transitivity is enabled, users of domain A can access both domain B and C._
- Non-transitive trusts, even if there is trust between all of the domains, but they are non-transitive, then they could only access their nearest trust points.</br> _Example: if domain A trusts domain B, and domain B trusts domain C. User from domain A could only access domain B._

##### Forest Trusts
An Active Directory (AD) Forest is the security and administrative boundary for objects and entities. Due to some business need, if we want to establish a bridge between two AD Forests, we need to configure Forest Trust between those forests. Forest Trusts are created between Forest Root Domains, and it is valid for all Domains  within the entire Forest.

Forests can be linked in either one way trust or two way trust, but they are bound to be non-transitive.</br> _Example: if forest A and forest B are connected, and forest B is connected to forest C, forest A could not access forest C. The only way for forest A to access forest C and overcome the non-transitive trust is to make a trust between them._


### Domain Controller (DC)
##### A server with Active Directory installed. A domain controller (DC) is authoritative for the domain to which the server is joined. It contains the Active Directory database for the domain namespace, plus the Configuration and Schema namespaces for the forest.
Domain controllers authenticate all users and computers in a domain, which is a primary security function in a network infrastructure. The DC is a server that contains a complete copy of the AD configuration of the domain in which it's located, as well as the SYSVOL system folder.
It's critical to ensure the optimal number and placement of domain controllers in any AD DS environment, especially in larger, distributed environments.

If the DC there will be no way for the users to authenticate themselves and access any of the domain's resources. Everything that require AD authentication will be inaccessible.

#### Read-Only Domain Controller (RODC)
##### Inadequate physical security is the most common reason to consider deploying an RODC. An RODC provides a way to deploy a domain controller more securely in locations that require fast and reliable authentication services but cannot ensure physical security for a writable domain controller.
 Read-Only Domain Controlelr is the same as DC except that it contains a read only copy of the AD configuration of the domain in which it's located, it's mainly used to improve security (since the copy is a read-only and cannot be modified), to speed up session openings and to improve access to network resources. Could be used in a LOB application, it provides a more secure mechanism for deploying a domain controller in this scenario. It's possible to grant a non-administrative domain user the right to log on to an RODC while minimizing the security risk to the Active Directory forest.
It is mostly common in branches with: relatively few users/ poor physical security/ relatively poor network bandwidth to a hub site/ little knowledge of IT.
#### Global Catalog (GC)
##### If the domain controller is configured as a global catalog, this domain controller contains a partial read-only copy of the attributes of all objects in the forest. What is also called PAS for Partial Attribute Set.
Global catalos are useful for reducing access times to an AD infrastructure. This is only necessary in a few cases such as: 
- An application requires the presence of global catalog. This is particularly the case for Microsoft Exchange and Microsoft Message Queuing (MSMQ).
- There are more than 100 users, used to reduce the use of WAN bandwidth.
- The logon is slow on the client workstations.


## Bibliography
https://us.informatiweb-pro.net/ </br>
https://docs.microsoft.com/en-us/ </br>
https://social.technet.microsoft.com/wiki/ </br>
https://en.wikipedia.org/wiki/Active_Directory </br>
https://ldapwiki.com/wiki/Partial%20Attribute%20Set </br>
