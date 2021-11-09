# Active-Directory-Attacks
##### A simple guide to show different attacks on Microsoft Active Directory.
##### The Active Directory was installed on a Microsoft Windows Server 2019 (GUI).


## Introduction
- Windows Server
   - Dynamic Host Configuration Protocol (DHCP)
   - Domain Name System (DNS)
   - Preboot Execution Environment (PXE)
   - Remote Access
   - Internet Information Services (IIS)
- Lightweight Directory Access Protocol (LDAP)
- Kerberos
- Active Directory
   - Fundamentals
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
      - Failover Clustering
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

## Windows Server Fundamentals
???

## Active Directory
#### The Windows implementation of a general-purpose directory service, which uses LDAP as its primary access protocol. Active Directory stores information about a variety of objects in the network such as user accounts, computer accounts, groups, and all related credential information used by Kerberos. Active Directory is either deployed as Active Directory Domain Services (AD DS) or Active Directory Lightweight Directory Services (AD LDS).

The most significant difference between between AD LDS and AD DS is that AD LDS does not host domain naming contexts. A server can host multiple AD LDS DCs. Each DC is an independent AD LDS instance, with it's own independent state. AD LDS can be run as an operating system DS or as a directory service provided by a standalone application (ADAM).

Directory services allows an easy and quick storage, search and managment of resources within a network. The Active Directory works in a hierarchical way and allows the arrangement of resources based on DCs (Domain Controllers - databases), it is also a secutiry solution to vast networks.
Unlike Peer to Peer Network which is used in small networks, Active Directory is a centralised network managment, which uses databases that attain each user/device configuration.

Active Directory helps both IT/administrators and end users.
Users only need to login once and their files are stored in a repository which is accessible to other users from different domains/trees/forests.
Administrators/IT are enjoying the benefits of implementing group policies, having to make changes one time and push it for every computer in the domain, the same could be applied to security configurations. Storing vital information about the users in databases. The ability to make changes and apply them to domains are what makes Active Directory so keen.

Active Directory Web Services (ADWS) Provides a web service interface to Active Directory Domain Services (AD DS) and Active Directory Lightweight Directory Services (AD LDS) instances.
### Active Directory Lightweight Directory Services (AD LDS)

Active Directory Lightweight Directory Services (AD LDS) is an independent mode of Active Directory, minus infrastructure features, that provides directory services for applications. AD LDS consists of a directory service that is accessible via the Lightweight Directory Access Protocol (LDAP). AD LDS is primarily intended for use by application software as a storage mechanism. </br>
AD LDS provides dedicated directory services for applications. It provides a data store and services for accessing the data store. It uses standard application programming interfaces (APIs) for accessing the application data. The APIs include those of Active Directory, Active Directory Service Interfaces, Lightweight Data Access Protocol, and System.DirectoryServices. AD LDS operates independently of Active Directory and independently of Active Directory domains or forests. It operates either as a standalone data store, or it operates with replication. Its independence enables local control and autonomy of directory services for specific applications. It also facilitates independent, flexible schemas, and naming contexts

### Basics
- Active Directory Application Mode (ADAM) - A Lightweight Directory Access Protocol (LDAP) - compliant directory service used for building directory-enabled applications. </br>
- Azure - Microsoft's cloud, which can also run AD (was not used in the demonstrations in this repository) </br>
- Distinguished Name (DN) - A string that uniquely identifies an object in Active Directory. </br>
- Directory Information Tree (DIT) - </br> 
- Direectory System Agent (DSA) - A collection of services and processes that run on each domain controller and provide access to the data store. The data store is the physical store of directory data located on a hard disk. </br>
- Data Source Name (DSN) - A symbolic name that applications use to request a connection to an ODBC Data Source, it represents the ODBC connection. DSN stores the connection details when making connection to the ODBC.
- Line of Business (LOB) - a general term which refers to a product or a set of related products that serve a particular customer transaction or business need. One of the set of critical computer applications perceived as vital to running an enterprise. 
- The Local Security Authority (Domain Policy) Remote Protocol (LSAD) - Used to manage various machine and domain security policies. All versions of Windows NT operating system–based products, in all configurations, implement and listen on the server side of this protocol. However, not all operations are meaningful in all configurations. </br>
- Namespace (NS) - Unique naming based on hierarchy and logic. </br>
- Naming Context (NC) - A set of objects organized as a tree, referenced by a DSName. A contiguous Active Directory subtree that is replicated on one or more domain controllers in a forest (Directory Partition).
- Naming Context Replica - A variable containing a tree of objects whose root object is identified by some naming context (NC).
- NetBIOS - A particular network transport that is part of the LAN Manager protocol suite. NetBIOS uses a broadcast communication style that was applicable to early segmented local area networks. A protocol family including name resolution, datagram, and connection services. </br>
- Microsoft's Open Database Connectivity (ODBC) - The interface that makes it possible for applications to access data from a variety of database managment systems (DBMS). ODBC is a low-level, high-performance interface that is designed specifically for relational data stores.
- Remote Procedure Call (RPC) - A communication protocol used primarily between client and server. The term has three definitions that are often used interchangeably:
  1. A runtime environment providing for communication facilities between computers (the RPC runtime)
  2. A set of request-and-response message exchanges between computers (the RPC exchange)
  3. And the single message from an RPC exchange (the RPC message).
- Security Account Manager (SAM) - Windows stores and manages the local user and group accounts in a database file called Security Account Manager (SAM). It authenticates local user logons. This allows a domain-joined computer to make local logon.
- Security Identifires (SID) - An identifier for security principals that is used to identify an account or a group. Conceptually, the SID is composed of an account authority portion (typically a domain) and a smaller integer representing an identity relative to the account authority, termed the relative identifier (RID).</br>
- SYSVOL - A folder which resides on each and every domain controller within the domain. It contains the domains public files that need to be accessed by clients and kept synchronised between domain controllers. Also keeps inside all files related to group policies and any startup scripts, logon scripts that were created and added to group policies. </br>

#### Domain, Tree, Forest
- An AD (Active Directory) domain is a group of users, devices that are part of the network (PC, printers, etc..), applications and other AD objects. They are all part of the domain, and are controlled by the DC (Domain Controller). An AD tree is a group of domains with a trust between them a parent-child relation and they share the same domain namespace.
Each domain is given a DNS name that identifies the domain.
  
- A domain tree is made up of several domains that share a common schema and configuration, forming a contiguous namespace. Domains in a tree are also linked together by trust relationships. Active Directory is a set of one or more trees. Trees have a unique namespace which they share with their domains.</br> _For instance, a tree name could be drive.google.com and one of his children (domains under him) would be named project.drive.google.com there could be no other tree with the same name (drive) in that forest._
- Forests are a set of one or more trees that do not form a contiguous namespace, all trees in a forest share a common schema, configuration and global catalog. Trees in a forest share the same attributes, and have a trust relationship. There can be more than one forest in an organization and they can be linked via trust authorization by both forest adminstrators. Multiple forests can be helpful in vast companies that are spread.

![forest pic](https://user-images.githubusercontent.com/90955504/133885246-7cfb043e-f0bd-49f7-831f-93cb99b803e5.png)

#### Trusts
Active Directory domains rarely exist in isolation. Many Active Directory deployments in customer sites consist of two or more domains that represent boundaries between different geographical, managerial, organizational, or administrative layouts. For example, when company "A" acquires company "B", it quickly becomes necessary for preexisting domains to start trusting each other. Alternatively, in some deployments, servers that have a specific role (such as a mail server) can be members of a "resource domain", easing the management burden by combining like roles under one administrative domain. Communication between disparate domains, especially secure communication that involves authentication and authorization, requires that some stateful knowledge is shared between the peer domains in order for them to trust one another. Some of this knowledge is sensitive, forming the cryptographic basis of trust mechanisms used in protocols such as Kerberos and Netlogon RPC. Other state is public knowledge, such as the NetBIOS name of a peer domain, or which security identifiers are owned by the peer domain. Information like this plays a crucial role when performing name lookups, which are essential for authorization, locating user accounts, or simply displaying information in some type of user interface.

Trusted Domain Object (TDO): A collection of properties that define a trust relationship with another domain, such as direction (outbound, inbound, or both), trust attributes, name, and security identifier of the other domain.
#### A trust relationship is a logical relationship between two domains/forests which allows authentication. By default, a secure channel is used to check security information, including security identifiers (SIDs) of users and groups.

This secure channel can be extended to other Active Directory domains by creating trust relationships between multiple domains or multiple forests. There are different trust relationships:
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

When a change is made to an object in a directory partition, the value of the changed attribute or attributes is updated on all domain controllers that store a replica of the same directory partition. Domain controllers communicate data updates automatically through Active Directory replication. Their communication about updates is always specific to a single directory partition at a time. It's importatnt to know that when a change occurs on a source domain controller, it notifies its destination replication partner, prompting the destination domain controller to request the changes from the source domain controller. The source domain controller either responds to the change request with a replication operation or places the request in a queue if requests are already pending. Each domain controller has a queue of pending replication operations that are processed one at a time.
If the DC is down there will be no way for the users to authenticate themselves and access any of the domain's resources. Everything that require AD authentication will be inaccessible.

#### Read-Only Domain Controller (RODC)
##### Inadequate physical security is the most common reason to consider deploying an RODC. An RODC provides a way to deploy a domain controller more securely in locations that require fast and reliable authentication services but cannot ensure physical security for a writable domain controller.
 Read-Only Domain Controlelr is the same as DC except that it contains a read only copy of the AD configuration of the domain in which it's located, it's mainly used to improve security (since the copy is a read-only and cannot be modified), to speed up session openings and to improve access to network resources. Could be used in a LOB application, it provides a more secure mechanism for deploying a domain controller in this scenario. It's possible to grant a non-administrative domain user the right to log on to an RODC while minimizing the security risk to the Active Directory forest.
It is mostly common in branches with: relatively few users/ poor physical security/ relatively poor network bandwidth to a hub site/ little knowledge of IT.
#### Global Catalog (GC)
##### A domain controller (DC) that contains a naming context (NC) replica (one full, the rest partial) for each domain naming context in the forest.
A Global Catalog server contains basic (but incomplete) set of attributes for each forest object in each domain
GCs are useful for reducing access times to an AD infrastructure. This is only necessary in a few cases such as: 
- An application requires the presence of global catalog. This is particularly the case for Microsoft Exchange and Microsoft Message Queuing (MSMQ).
- There are more than 100 users, used to reduce the use of WAN bandwidth.
- The logon is slow on the client workstations.


## Bibliography
https://us.informatiweb-pro.net/ </br>
https://docs.microsoft.com/en-us/ </br>
https://social.technet.microsoft.com/wiki/ </br>
https://en.wikipedia.org/wiki/Active_Directory </br>
https://ldapwiki.com/wiki/Partial%20Attribute%20Set </br>
https://www.techopedia.com/ </br>




Many network-related operations depend on domains in order to complete various tasks. This document describes some of these tasks, including:
 Joining a domain by creating an account via LDAP.

Knowledge Consistency Checker (KCC)
A domain controller that runs Active Directory is part of a distributed system that performs replication. The KCC is a component that reduces the administrative burden of maintaining a functioning replication topology. The KCC ensures that a replication path exists between the same NCs that are present in different DCs. The KCC is explained in [MS-ADTS] sections 3.1.1.1.13 and 6.2. The KCC helps administrators build a replication topology that incurs minimal cost. This cost is defined by the administrator as explained in [MS-ADTS] section 3.1.1.1.13.

ADCAP: The Active Directory Web Services Custom Action Protocol [MS-ADCAP].

directory service (DS): A service that stores and organizes information about a computer network's users and network shares, and that allows network administrators to manage users' access to the shares. See also Active Directory.

AD DS DC

domain functional level: A specification of functionality available in a domain. Must be less than or equal to the DC functional level of every domain controller (DC) that hosts a replica of the domain's naming context (NC). For information on defined levels, corresponding features, information on how the domain functional level is determined, and supported domain controllers, see [MS-ADTS] sections 6.1.4.2 and 6.1.4.3. When Active Directory is operating as Active Directory Lightweight Directory Services (AD LDS), domain functional level does not exist.

Domain Name System (DNS): A hierarchical, distributed database that contains mappings of domain names to various types of data, such as IP addresses. DNS enables the location of computers and services by user-friendly names, and it also enables the discovery of other information stored in the database.

flexible single master operation (FSMO): A read or update operation on a naming context (NC), such that the operation must be performed on the single designated master replica of that NC. The master replica designation is "flexible" because it can be changed without losing the consistency gained from having a single master. This term, pronounced "fizmo", is never used alone; see also FSMO role, FSMO role owner, and FSMO object.

The definition of global catalog is specified in [MS-ADTS] section 3.1.1.1.8.

Kerberos: An authentication system that enables two parties to exchange private information across an otherwise open network by assigning a unique key (called a ticket) to each user that logs on to the network and then embedding these tickets into messages sent by the users. For more information, see [MS-KILE].

Lightweight Directory Access Protocol (LDAP): The primary access protocol for Active Directory. Lightweight Directory Access Protocol (LDAP) is an industry-standard protocol, established by the Internet Engineering Task Force (IETF), which allows users to query and update information in a directory service (DS), as described in [MS-ADTS]. The Lightweight Directory Access Protocol can be either version 2 [RFC1777] or version 3 [RFC3377].

NT Directory Service (NTDS): A previous name for Active Directory.

primary domain controller (PDC): A domain controller (DC) designated to track changes made to the accounts of all computers on a domain. It is the only computer to receive these changes directly, and is specialized so as to ensure consistency and to eliminate the potential for conflicting entries in the Active Directory database. A domain has only one PDC.

read-only domain controller (RODC): A domain controller (DC) that does not accept originating updates. Additionally, an RODC does not perform outbound replication. An RODC cannot be the primary domain controller (PDC) for its domain.

relative identifier (RID): The last item in the series of SubAuthority values in a security identifier (SID) [SIDD]. It distinguishes one account or group from all other accounts and groups in the domain. No two accounts or groups in any domain share the same RID.

replica domain controller / replica directory server: A server that contains a replicated copy of the directory and is able to answer client requests over any protocol that the directory service supports.

role: The domain role quantifies the relationship between a computer and a domain. Domain roles include the following: Joined: Linked to a domain for purposes of policy and security. Standalone: Not associated with any domain. Domain controller: Linked to a domain, and hosting that domain.

security descriptor: A data structure containing the security information associated with a securable object. A security descriptor identifies an object's owner by its security identifier (SID). If access control is configured for the object, its security descriptor contains a discretionary access control list (DACL) with SIDs for the security principals who are allowed or denied access. Applications use this structure to set and query an object's security status. The security descriptor is used to guard access to an object as well as to control which type of auditing takes place when the object is accessed. The security descriptor format is specified in [MS-DTYP] section 2.4.6; a string representation of security descriptors, called SDDL, is specified in [MS-DTYP] section 2.5.1.

server: A domain controller. Used as a synonym for domain controller.

Windows NT 4.0-style domain: A domain that is created from Windows NT 4.0 operating system servers with an account database that includes all the information in the domain. Windows NT 4.0-style domains do not implement Active Directory, LDAP directories, or Kerberos authentication.

writable naming context (NC) replica: A naming context (NC) replica that accepts originating updates. A writable NC replica is always full, but a full NC replica is not always writable. Partial replicas are not writable. See also read-only full NC replica.
