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
- Active Directory Domain Services
  - Domain
  - Domain Trees
  - Forests
  - Forest Design/Models
    - Single Forest
    - Multiple Forest
    - Organizational Forest Model
    - Resource Forest Model
    - Restricted Forest Model
    - Single Domain Model
    - Regional Domain Model
   - Security Identifiers (SID) and Globally Unique Identifiers (GUID)
   - Trusts
     - Forest Trusts
   - Domain Controller (DC)
     - Global Catalog (GC)
     - Read Only Domain Controller (RODC)
     - Replication and Failover Clustering
     - Knowledge Consistency Checker (KCC)
   - Organizatinal Units (OU)
   - Active Directory Objects
     - Container
     - Leaf
   - Flexible Single Master Operation (FSMO)
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

# Windows Server
A brief explanation of some of the systems that were used in the making of this repository along with other features.

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

# Active Directory Domain Services 
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

## Forests Design
One of the most important aspects in a system is designing it in an efficient way, this applies to Active Directory as well. A good forest design could only be achieved after identifying the needs for the organization. </br>

### Single Forest
A single Active Directory forest consists of only one forest, therefore it could be considered as a more simpler solution, it is the default mode. Most business models if not all could fit into this model, it’s significantly cheaper to maintain only one forest. </br>
Most documentation states that restricting yourself to one forest is the key to success.

### Multiple Forest
The multi-forest model consists of at least 2 forests and is a must in some organizations, this adds to the already complexed and thought topology. Managing multiple forests require more administrators (I.T) as well as more physical hardware. There are several reasons as to why you should use the multi-forest model: </br>
- Organization acquisitions usually require some security boundaries </br>
- Isolation needed due to constant forest schema changes or due to vast organizations with multiple forests that share only common resources whilst keeping the other resources isolated in a different forest. </br>
- Many organizations are under strict regulations that require isolation between some departments. </br>

### Organizational Forest Model
An organizational forest model focuses on having control over the forest autonomy and isolation. To access resources in other forests, trust relationships between the forests must be established first.

### Resource Forest Model
The resource forest model is used to separate the users from the sources. The resource forests contain only administrative user accounts for maintenance besides the resources. The trust relationships are one way, so that users can get resources from the resource forests.

### Restricted Access Forest Model
The restricted access forest model consists of an organizational forest, and a restricted access forest with classified data. There are no trusts between the forests, and so if users want to access the classified data, they must have a user in that forest. This helps in reducing the risk of compromising important data.
Organizations use that structure when working on classified government projects, new hardware, etc.

### Single Domain Model
A single domain model consists of a single domain in a single forest, it’s the easiest to administer implementation of Active Directory and it contains all the objects in the forest. All data is replicated between all domain controllers, this means that all the domain controllers can be global catalog. Users can authenticate through every domain controller, irrelevant of their geographical location. Implementing this model also results in more administrative overhead.

### Regional Domain Model
The regional domain model consists of a forest root domain and multiple domains, this model is more complex compared to the single domain model and is used when not all domain controllers could be connected to the rest of the domain through fast WAN links. </br>
Data inside the domain is only replicated within the domain controllers in that domain, this allows a reduced traffic over the WAN links, the model is mainly applicable to large numbers of users that are in different geographical locations. </br>
This model does not provide isolation, to achieve isolation you must create separate forests.

## Security Identifiers (SID) and Globally Unique Identifiers (GUID)
Every time we create and object in Active Directory it is assigned with a security identifier (SID) and a globally unique identifier (GUID).

### Security Identifiers (SID)
A security identifier is a value given to an object which is a unique value within its enterprise and is stored in the ObjectSID property. A security identifier is given to a user account or a group account by an authority. The security identifier authority never issues the same SID, nor use SIDs from deleted objects within the enterprise. There are commonly used security identifiers that are used across all Active Directory systems, these are generic users/groups. </br>
If a user has migrated to another domain, it will receive a new security identifier generated by the new domain, the former security identifier is saved in the SIDHistory, this property holds any other values the object has been formerly assigned. If a user tries to access a resource, any one of the values saved in the SIDHistory could allow or deny access. This can be a double edged sword, this feature helps in that there is no need to make access control changes, it could also be in conflict of the organization’s interests. </br>
*Example: a group is deleted by the administrator, the security identifiers attached to the group gets deleted as well and would not be used again by the system.* </br>
The operating system refers to objects in the security context by using their security identifiers, every time a user signs in, the system creates a token for the user, that token includes the security identifier for that user and allows or prevents him from actions based on the policies attached to the user.

### Globally Unique Identifiers (GUID)
The globally unique identifier is a 128-bit number that is used by Active Directory to identify objects (user accounts, group accounts), it’s given when a new object is created. The globally unique identifier value never changes, and therefore is considered for the most reliable way to find objects. </br>
A misconception about the globally unique identifier is that it is a unique number, when in reality a globally unique identifier is a value that has 2^128 different options. Calling it unique is based on the unlikeliness of it to appear anywhere else. </br>
Some documentation gives the term universally unique identifier (UUID) to this number, for its unlikeliness of reappearing again.

## Trusts
Active Directory domains rarely exist in isolation. Many Active Directory deployments in customer sites consist of two or more domains that represent boundaries between different geographical, managerial, organizational, or administrative layouts. *For example, when company "A" acquires company "B", it quickly becomes necessary for preexisting domains to start trusting each other.* Communication between disparate domains, especially secure communication that involves authentication and authorization, requires that some stateful knowledge is shared between the peer domains for them to trust one another. Some of this knowledge is sensitive, forming the cryptographic basis of trust mechanisms used in protocols such as Kerberos and Netlogon RPC. Other state is public knowledge, such as the NetBIOS name of a peer domain, or which security identifiers are owned by the peer domain. Information like this plays a crucial role when performing name lookups, which are essential for authorization, locating user accounts, or simply displaying information in some type of user interface.

Trusted Domain Object (TDO): A collection of properties that define a trust relationship with another domain, such as direction (outbound, inbound, or both), trust attributes, name, and security identifier of the other domain.
**A trust relationship is a logical relationship between two domains/forests which allows authentication.** By default, a secure channel is used to check security information, including security identifiers of users and groups.

This secure channel can be extended to other Active Directory domains by creating trust relationships between multiple domains or multiple forests. There are different trust relationships:
- One-way trusts relationships are valid in one direction.
- Two-way trusts relationships are valid in both directions.
- Explicit trust is a trust that's created manually by the system administrator.
- External trust is a trust between domains that belong to different forests.

These relationships can be either transitive or non-transitive:
- Transitive trusts, if there is trust between the domains a user can access these trust paths. </br>
*Example: if domain A trusts domain B, and domain B trusts domain C, when transitivity is enabled, users of domain A can access both domain B and C.*
- Non-transitive trusts, even if there is trust between all the domains, but they are non-transitive, then they could only access their nearest trust points. </br> 
*Example: if domain A trusts domain B, and domain B trusts domain C. User from domain A could only access domain B.*

### Forest Trusts
An Active Directory Forest is the security and administrative boundary for objects and entities. Due to some business need, if we want to establish a bridge between two AD Forests, we need to configure Forest Trust between those forests. Forest Trusts are created between Forest Root Domains and are valid for all Domains within the entire Forest.

Forests can be linked in either one-way trust or two-way trust, but they are bound to be non-transitive. </br> 
*Example: if forest A and forest B are connected, and forest B is connected to forest C, forest A could not access forest C. The only way for forest A to access forest C and overcome the non-transitive trust is to make a trust between them.*


## Domain Controller (DC)
Unlike the components mentioned before, Domain Controller is a physical component. It’s a computer that runs Windows Server operating system and has Active Directory Domain Services installed, a Domain Controller could be viewed as a database and it can hold nearly 2 billion objects. </br>
A Domain Controller is authoritative for the domain to which the server is joined. It contains the Active Directory database for the domain namespace, the configuration, and the Flexible Single Master Operation roles (at least the domain level ones). There can be any number of Domain Controllers in a domain for different reasons (organization size, replication).
Domain Controllers authenticate all users and computers in a domain, which is a primary security function in a network infrastructure. It's critical to ensure the optimal number and placements of Domain Controllers in any Active Directory structure. 
When a change is made to an object in a directory partition, the value of the changed attribute or attributes is updated on all Domain Controllers that store a replica of the same directory partition. Domain Controllers communicate data updates automatically through Active Directory replication. Their communication about updates is always specific to a single directory partition at a time. It's important to understand that when changes occur on a source Domain Controller, it notifies its destination replication partner, prompting the destination Domain Controller to request the changes from the source Domain Controller. The source Domain Controller either responds to the change request with a replication operation or places the request in a queue if requests are already pending. Each Domain Controller has a queue of pending replication operations that are processed one at a time.
If the domain’s Domain Controller is offline, it will be impossible for the users to authenticate themselves and access any of the domain's resources. Everything that require Active Directory authentication will be inaccessible.

### Global Catalog (GC)
Global catalog is a type of a domain controller, it contains a partial replication of all the directory objects for the entire forest and a full writable copy of objects within its domain. The topology for the global catalog is generated by the system, while administrators can change the configurations. </br>
Users may not always know the distinguished name of an object they have interest in finding, this is where the global catalog helps, as it holds the most frequently used searches. Global catalog allows a quickly search without knowing where the object is placed. </br>
Every domain must have at least one global catalog, therefore when installing the first domain controller within a domain, it automatically promotes the domain controller to a global catalog. The same is applied in a single-domain-single-forest structure.
In a more complex structure, the placement of a global catalog is a crucial part in the design as it increases the amount of data replicated, as well as the bandwidth.
### Read Only Domain Controller (RODC)

### Replication and Failover Clustering

### Knowledge Consistency Checker (KCC)


## Organizatinal Units

## Active Directory Objects

### Container

### Leaf


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

