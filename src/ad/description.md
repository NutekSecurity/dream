# Active Directory

Summary: Struggling to understand the difference between Active Directory and LDAP? Don't worry, we’ll make it simple. These are just two among many methods that can provide secure user authentication and authorization. The information in this article will help you decide if LDAP or Active Directory is right for your organization. Robust security and a seamless user experience are attainable, and you can have both!

What Is LDAP and Active Directory?

Lightweight Directory Access Protocol (LDAP) and Active Directory (AD) are core to Identity and Access Management (IAM). Both are legacy methods that have been in use since the mid-1990s. And both continue to be popular today. While AD and LDAP mean two distinctly different things, some people use these terms interchangeably.

Lightweight Directory Access Protocol (LDAP)

So, what is LDAP? Lightweight Directory Access Protocol is an open, platform-independent protocol used to access and maintain directory services over a TCP/IP network. It’s considered lightweight because LDAP is a pared-down version of an older X.500 network directory services standard called Directory Access Protocol (DAP).

LDAP provides a framework for organizing data within a directory. It also standardizes how users, devices, and clients communicate with a directory server. Because LDAP is optimized for speed, it excels at searching through massive volumes of data quickly. LDAP’s scalability makes it an ideal solution for large enterprises that need to authenticate users on platforms with thousands—or even millions—of users.

Active Directory (AD)

Active Directory (AD) is Microsoft’s proprietary directory service for Windows domain networks. It comprises a database (called a directory) and various services, all of which work together to authenticate and authorize users. The directory contains data that identifies users—for example, their names, phone numbers, and login credentials. It also contains information about devices and other network assets.

AD simplifies IAM by storing information about users, devices, and other resources in a central location. Organizations can enable single sign-on (SSO) to allow users to access multiple resources within a domain using one set of login credentials. AD checks to ensure that users are who they claim to be (authentication) and grants access to resources based on each individual user’s permissions (authorization).

LDAP vs. Active Directory: What's the Difference?

The difference between LDAP and Active Directory is that LDAP is a standard application protocol, while AD is a proprietary product. LDAP is an interface for communicating with directory services, such as AD. In contrast, AD provides a database and services for identity and access management (IAM).
LDAP communicates with directories using a LDAP server. Some organizations use LDAP servers to store identity data for authenticating users to an application. Because AD is also used to store identity data, people sometimes confuse the two methods or conflate them as “LDAP Active Directory” or “Active Directory LDAP.” The fact that AD and LDAP work together adds to the confusion that leads people to think of Active Directory as LDAP.

Similarities Between LDAP and Active Directory

Active Directory is a Microsoft application that stores information about users and devices in a centralized, hierarchical database. AD provides a powerful identity and access management solution. Enterprises use AD to authenticate users to access on-prem resources with a single set of login credentials.

Applications typically use the LDAP protocol to query and communicate with directory services. However, when it’s used in combination with Active Directory, LDAP can also perform authentication. It does this by binding to the database. During binding, the LDAP server authenticates a user and grants access to resources based on that user’s privileges.

While Microsoft uses the more advanced Kerberos protocol as its default authentication method, AD offers organizations the option to implement LDAP instead. LDAP provides a fast and easy method of authentication. It simply verifies the user’s login credentials against the information stored in the AD database. If they match, LDAP grants the user access.

LDAP and Active Directory Advantages and Disadvantages

LDAP and Active Directory have their respective strengths and weaknesses. Evaluating the pros and cons of LDAP vs. Active Directory can help organizations gain a clearer understanding of LDAP vs. AD.

Advantages

These are the main benefits of using LDAP:

It is widely supported across many industries.
It is a standardized, ratified protocol.
It is available as open-source software and has a very flexible architecture.
It is lightweight, fast, and highly scalable.
Active Directory also offers many benefits, including

It is highly customizable, making it easy to use, manage, and control access.
It leverages trust tiers and extensive group policies to provide stronger security than other directory services.
It includes compliance management features, such as data encryption and auditing.
Different versions exist for different needs, including federation services and cloud security.
Disadvantages

As a legacy technology, LDAP has a few downsides. Organizations can find these challenges difficult to overcome:

Its age: LDAP was developed during the early days of the internet.
It is not well-suited for cloud and web-based applications.
Setup and maintenance can be very challenging and usually require an expert.
Active Directory has several drawbacks, too. Here are some disadvantages to consider:

It only runs in Windows environments.
Because AD manages the network, the entire network will go down if AD fails.
Setup and maintenance costs can be high.
Legacy AD is limiting because it requires on-prem infrastructure.
LDAP and Active Directory Use Cases

So, is there a difference between AD and LDAP when it comes to use cases? Yes, indeed.

LDAP was originally developed for Linux and UNIX environments, but today it works with a wide range of applications and operating systems. Examples of popular applications that support LDAP authentication include OpenVPN, Docker, Jenkins, and Kubernetes. One of the most common use cases for LDAP is as a tool for querying, maintaining, and authenticating access to Active Directory.

In contrast, Active Directory is less flexible than LDAP because it only operates in Microsoft environments. AD excels at managing Windows clients and servers and works well with other Microsoft products, such as SharePoint and Exchange. Because AD and domain-joined Windows devices are tightly integrated, Active Directory is more secure than LDAP.

LDAP or Active Directory–Which One Should You Choose?

LDAP’s speed and scalability make it the better option for large applications that need to authenticate vast numbers of users. Examples of organizations that might benefit from LDAP include companies in the airline industry or wireless telecommunications providers that handle millions of subscriber queries.

Microsoft Active Directory is the most widely used directory service for enterprises. It is a good solution for highly structured organizations, such as large commercial banks and government agencies, which prioritize security and compliance. The typical AD customer relies primarily on Windows-based architecture instead of using cloud-, web-, or Linux-based applications.

Because AD was designed for a traditional, on-prem environment with a clearly defined perimeter, there’s no simple way to move it to the cloud. Likewise, because of its age and on-prem limitations, legacy LDAP isn’t a good option for cloud or hybrid environments, either.

[AD vs LDAP: Which is Right for Your Organization?](https://www.jumpcloud.com/blog/active-directory-vs-ldap)

[AD vs LDAP](https://www.strongdm.com/blog/ldap-vs-active-directory)

Active Directory is a Microsoft product used to organize IT assets like users, computers, and printers. It integrates with most Microsoft Office and Server products.

Lightweight directory access protocol (LDAP) is a protocol, not a service. LDAP is used to talk to and query several different types of directories (including Active Directory).

What Is Active Directory?
Microsoft creates a lot of IT software, from Windows desktops to Windows Server, Exchange, Sharepoint, and more.

In the IT environment, users don’t want to use a separate password for each application they access. And IT admins want to be able to group people together and manage access to computers and printers.

Active Directory was created to ease the management of users and computers by storing information about them in a single directory.

Imagine working at a company without a directory:

You would have to keep providing a username and password for each application.
IT admins would have to manually assign you to every single application you need to access.
If you update your password or change your last name, you would have to do that in every application in which you have an account.
The directory brings together, in a central service, information about all the people, computers, and other assets in the organization. It also stores credentials (like your username and password) so it can authenticate you to all the applications you use.

In Active Directory, assets are sorted into one of three tiers.

Domains: Users (such as employees) and devices (such as computers) that share the same Active Directory database are part of a domain. A domain is usually associated with either a company or an organization in a company, like the “Engineering Domain.”
 
Trees: Trees define the trust between domains, deciding who can access what in different parts of an organization, and letting IT admins manage their own community of users and devices.
 
Forests: For large organizations or intercompany relationships, domains are grouped into forests. Inter-forest trust is usually developed after a company acquires another company. Employees in both organizations need to access each other's resources.
Each one of these levels has access rights and communication privileges unique to it.
Active Directory Tiers Diagram
Active Directory also includes security features, including:

Authentication. Users must provide the relevant credentials before they can access resources on the network.
 
Security groups. IT admins organize users into groups. The groups are then assigned to apps to minimize administration.
 
Group policy. There are a large number of policies in Active Directory that define who can access computers remotely or configure browser security settings.
Active Directory supports a variety of ways to authenticate users. Over the range of its life, Active Directory has supported LAN Manager, NTLM, and Kerberos. Each time, the authentication protocol evolved to be more usable and secure.

Active Directory’s main purpose was to bring together all the Microsoft technologies to allow users to easily access resources and to allow administrators to securely define their access.

What Is LDAP?
LDAP is a protocol that was designed for applications to query user information very quickly and at scale. It was ideal for something like the telecommunications or airline industry.

Active Directory was designed for enterprises with maybe a few thousand employees and computers. LDAP was a protocol designed for applications powering the telephone wireless carriers that needed to handle millions of requests to authenticate subscribers to the phone networks.

LDAP is a product-agnostic protocol. Active Directory actually implemented with LDAP support to allow LDAP-based applications to work against an existing Active Directory environment.

As a protocol, LDAP is primarily concerned with:

Directory structure. Each entry in the directory has attributes and can be accessed via a unique distinguished name (DN) that is used when querying the directory.
 
Adding, updating, and reading data. LDAP is optimized for fast searching and reading of data.
 
Authentication. In LDAP, you “bind” to the service. This authentication can be a simple username and password, a client certificate, or a Kerberos token.
 
Search. One area where LDAP excels is search. Again, LDAP-based servers are typically designed for mass queries, and those are usually searches for sets of data.
How Do LDAP & Active Directory Compare?
LDAP is a protocol, but vendors built directories where LDAP was the primary means of communicating with the directory. They were often known as LDAP servers.

The servers were mainly used as an information store about users for an application. As a result, they are sometimes compared with Active Directory. This led to some confusion, with people asking which is better: an LDAP server or Active Directory?

There isn’t really a good answer to this question, as it’s not a fair comparison. People might really be asking a different kind of question. For example, is Active Directory a better choice for an application directory than using Ping Identity Directory or Oracle Internet Directory?

Typically, LDAP servers are appropriate for very large-scale applications, such as the millions of subscriber queries made in a wireless telecommunications platform.

LDAP is also good in situations where you have a large number of user authentications taking place. At one point, Twitter had a very large LDAP service powering its user authentication.

Due to its design, Active Directory is not ideal for very large-scale implementations with a single community of users. It does scale very well when the organization is distributed into multiple forests and domains.

There are Active Directory implementations with hundreds of thousands of users, but they are all managed in localized domains and forests.

Where Active Directory Excels
Active Directory is excellent at its core job, which is managing access to on-premises Microsoft-based technology, such as Windows clients, servers, and SharePoint/Exchange.

Group policy in Active Directory can be very effective at securing Windows computers due to the tight integration between domain-joined Windows computers and Active Directory. LDAP servers have no equivalent here.

What Is Active Directory? Working, Importance, and Alternatives
Active Directory is a central database that systematically organizes a company’s network and users.

 Vijay Kanade  Vijay Kanade AI Researcher
May 25, 2023

Image showing Microsoft Active Directory on a laptop
Active Directory (AD) is defined as a directory service that connects users with the network resources they need to accomplish their tasks.
AD is Microsoft’s proprietary entity that runs on Windows Server and allows administrators to manage access permissions across networks.
This article explains the fundamentals and importance of Active Directory and lists eight of its top alternatives.
Table of Contents
What Is Active Directory?
Importance of Active Directory
Top Alternatives To Active Directory
What Is Active Directory?
Active Directory (AD) is a directory service that connects users with the network resources they need to accomplish their tasks. It is Microsoft’s proprietary entity that runs on Windows Server and allows administrators to manage access permissions across networks. AD first emerged in the Windows 2000 system, intending to provide directory services to complex IT environments.

The directory stores information about objects, wherein an object may refer to network elements such as a user, group, device, or application. AD is responsible for categorizing these objects based on name and attributes. For instance, the object user may include a user name, designation, access permissions, system password, etc.

The main service offered by Active Directory is Domain Service, also termed as ‘AD DS.’ It is a service that stores directory information and manages user interaction with the domain. When a user signs into a system or attempts to connect to a server on a network, AD DS performs the task of verifying user access. Technically, user access to any network resource is controlled by AD DS. Microsoft products such as Exchange Server and SharePoint Server rely on AD DS to provide access to network resources. The server hosting the AD DS is called a domain controller (DC).

Services offered by AD are used by organizations to control the activities going on within their IT framework. Hence, it is vital for companies to understand the basic structure of AD.

Active Directory structure
Active Directory stores data in a hierarchical structure that consists of domains, trees, and forests.

Domain: A domain refers to a set of objects (users, peripherals, devices) that share a common AD database. It is recognized by a DNS name (xyz_company.com).
Tree: One or more domains combine to form a tree. The tree has a common DNS root name. For instance, ecommerce.marketing.com, sales.marketing.com, and business.marketing.com.
Forest: One or more trees sharing a common schema, directory configuration, or a global catalog are regarded as a forest. However, this does not have a continuous namespace like a tree. Forests act as a security boundary for organizational networks.
Organizational Units (OU): Objects within a domain fall under OUs. These simplify administration and policy management as administrators can create functional, geographic, or business structures and then apply group policies to all these OUs. Moreover, OUs play a crucial role when it comes to the delegation of control over network resources to different administrators.
Other Active Directory services
With time, ADs have evolved, and Microsoft has incorporated an additional suite of services under the Active Directory umbrella.

1. Active Directory Lightweight Directory Services (AD LDS)
The lightweight version of Domain Services eliminates complex and advanced functionalities from directory services by cutting down on the use of domain controllers, forests, or domains. Such services are typically employed in small office setups.

For instance, let’s say a company stores all its router information in one directory. In this case, Lightweight Directory Access Protocol (LDAP) can be employed to search for a specific router, localize it on the network, and then connect to it securely. Here, LDAP represents an instance of AD LDS.

2. Active Directory Certificate Services (AD CS)
AD CS refers to services used to issue and manage digital certificates often seen in software security setups. Such security systems rely on public key technologies. The digital certificates provided by AD CS can be used to encrypt and sign digital documents. These certificates can further be used to authenticate computers, users, or devices on a network.

3. Active Directory Federation Services (AD FS)
AD FS allows individuals to use the single sign-on (SSO) feature to access applications and systems outside the corporate environment. It is much like a web-based feature that contractors can use to log on to a personal network and, at the same time, get authorized to access a client’s private network.

4. Active Directory Rights Management Services (AD RMS)
AD RMS is used as a security strategy by organizations to safeguard and protect documents using information rights management (IRM) policies. AD RMS enables individuals and administrators to define permissions to access documents, workbooks, and presentations.

See More: What Is a Bare Metal Server? Definition, Working, and Importance

Importance of Active Directory
Active Directory makes the life of an administrator easy since it provides them with a centralized user and rights management platform. Organizations gain better control over computer and user configurations by implementing AD. Moreover, companies can keep their network and resources secure and organized without the need to deploy excessive IT resources.

Thanks to the benefits AD offers to organizations of all sizes, several companies today are implementing it as a necessity. According to a recent report by 6sense, in 2023, 18,132 companies from across the globe started using Microsoft Azure AD services. If we look at this from a geographical viewpoint, the U.S. is the top contributor with 51.96% of customers, followed by the U.K. with 9.52%, and Canada with 5.59% of customers.

As AD is being deployed at a large scale, it is important to consider why its implementation is inevitable for IT environments.

Active Directory Importance
Active Directory Importance

1. Provides a master data repository
AD is a master repository that stores the identity information of users, applications, and network resources. The AD database can store the information of up to 2 billion objects. Moreover, AD gives flexibility to corporate users who intend to use the organization’s network from any remote location. This means remote users can access network resources from anywhere in the network, irrespective of their physical presence.

AD is key to administrators since the authentication and authorization of users and applications can be done from one master repository. Also, without directory services, identity information could be replicated in various systems, which can eventually complicate the task of administrators.

2. Facilitates minimal data replication
In complex businesses, multiple domain controllers are essential to run business operations. When identities are managed by a central database system, subdomain controllers are aware of the updates happening in the AD database. Thus, AD can delegate responsibilities to centralized domain controllers through organization tools to add, delete, or modify active or inactive identities/objects. Such synchronization facilities ensure that data is consistent across all domain controllers. As a result, organizations can make changes in their operations within a few clicks.

3. Enables periodic audits
Auditing is essential for organizations to stay up to date on new and emerging security threats. AD allows periodic audits of events occurring in identity infrastructure, such as object authentication or user access violation. With a central database in place, such threat data can easily be collected and used for troubleshooting purposes.

4. Provides network security
AD acts as a security tool that safeguards an organization’s network from external threats. Higher-level management authorities and key stakeholders can also use AD to set permissions for network resources and applications for other administrators or users. Additionally, since AD is structured hierarchically, objects within the AD tree or forest can inherit permissions from parent objects. Such features assist in identifying corporate or remote users uniquely and securely.

Administrators can also duly update access permissions within one database, which reduces the chances of incorrect or outdated configuration in the directory.

5. Allows single sign-on functionality
An enterprise typically uses multiple applications within its framework. However, each of these applications employs its own authentication mechanisms. Since AD supports SSO features, users can sign in with one set of credentials and get access to other independent software systems used by the enterprise. In simple words, users need not sign in every time to gain access to a newer application. Once a user gets authenticated on a computer system, the credentials of that session are used to authenticate other AD-integrated applications.

See More: Why the Future of Database Management Lies In Open Source

Top Alternatives To Active Directory
It would be an understatement to say that privacy is a major concern for all organizations. Microsoft has already provided a solution to this through Active Directory. However, several other players are operating in the market who are helping enterprises secure their networks.

According to 2023 data from 6sense, the Identity and Access Management (IAM) market is dominated by Microsoft Active Directory with 33.48% market share, followed by Azure Active Directory (13.46%), Microsoft Azure Active Directory (10.37%), and AWS Identity and Access Management (5.54%).

These are the top alternatives to AD that are commercially available in the market:

1. Apache Directory
Apache Directory is open-source software designed by Apache Software Foundation. The solution is a Java-based directory server and is LDAP V3-certified. The directory was approved by Open Group and Eclipse-based databases in 2006. It can support additional codes owing to its integration with the Kerberos server.

Advanced features include a schema browser, Directory Services Markup Language (DSML) editor, LDAP editor/browser, and LDAP Data Interchange Format (LDIF) editor for the Eclipse-based directory server. Here, LDIF represents the LDA directory content, which shows one record for each object or entry. Additionally, new features can be incorporated into Apache Directory by upgrading Eclipse-based plugins.

2. Open LDAP
Open LDAP is an open-source tool designed under the OpenLDAP project. It’s an administration tool used for LDAP database control. It is typically regarded as a Windows LDAP client that allows you to browse, look up, create, change, and delete elements residing on the LDAP server.

Other features include scheme browsing, password management, export and import LDIF, and more.

3. FreeIPA
FreeIPA is an open-source identity and authentication tool developed by Red Hat. It offers a suite of services such as identity management, audit services, and policies tailored for Linux and Unix computer networks. The current version of the project RHEL 6.2 (Red Hat Enterprise Linux 6) aims to incorporate several features AD offers.

Some of its key features include:

Security information management solution that blends Linux (Fedora), 389 Directory Server, MIT Kerberos, and others
Automated installation and configuration
Expandable management interfaces, including CLI, WEB UI, and Python SDK
4. Samba
Samba is an open-source tool that runs on Unix platforms and coexists with Windows. While it operates in the Unix environment, the tool seamlessly talks to Windows clients. The directory allows you to shift from a Unix to a Windows network easily. As a result, you can access Windows files and print services without worrying about the underlying Unix system.

The Samba project relies on a CIFS implementation (Common Internet File System) to accomplish the above switching tasks. The project has already been shifted to several non-Unix host systems, such as NetWare, AmigaOS, and VMS.

5. Univention Corporate Server (UCS)
Univention Corporate Server is a server software that controls server applications, thereby managing IT operations. It has an integrated system to control multi-platform servers, clients, users, and services, including machines operated in UCS. Hence, the software is adopted by Debian GNU/Linux, a Linux-based operating system found in laptops, desktops, and servers.

UCS underwent an upgrade to Version 3.0, following which the software has started supporting AD’s features to administer machines that run on Microsoft Windows.

6. JumpCloud
JumpCloud is a cloud directory that offers a centralized platform for system administration. The platform allows users to access files residing on Linux, Mac, and Windows systems. JumpCloud keeps the server software up to date, ensures server availability, and manages server operations. The directory has a trial version for users. However, the full-fledged version needs to be purchased via a premium subscription.

7. Lepide Auditor for Active Directory
Lepide Auditor for Active Directory has been designed to monitor, audit, and report changes as and when they are made. The tool can look for modifications made in the directory and uncover the ones that are not required. It allows you to check who made the changes, what they were, and when and where they were done. Moreover, the tool is equipped with a facility to notify whenever any change is made to the directory.

Some other features include customizable control panel views, building audit logs at one location, generating views to look for directory modifications and a panel for audited systems. The auditor can also detect risks, keep a check on common attack paths, and mitigate attacks in real-time.

8. JXplorer
Jxplorer is a cross-platform tool that can be run on Windows, Linux, and many other operating systems. It provides LDAP and DSML interfaces that enable you to monitor and manage an LDAP directory without using the traditional command line. It is a Java-based tool that is quite adaptable and easy to configure. It is available in free and paid versions for businesses.

The core of any Windows Domain is the Active Directory Domain Service (AD DS). This service acts as a catalogue that holds the information of all of the "objects" that exist on your network. Amongst the many objects supported by AD, we have users, groups, machines, printers, shares and many others. Let's look at some of them:

Users

Users are one of the most common object types in Active Directory. Users are one of the objects known as security principals, meaning that they can be authenticated by the domain and can be assigned privileges over resources like files or printers. You could say that a security principal is an object that can act upon resources in the network.

Users can be used to represent two types of entities:

People: users will generally represent persons in your organisation that need to access the network, like employees.
Services: you can also define users to be used by services like IIS or MSSQL. Every single service requires a user to run, but service users are different from regular users as they will only have the privileges needed to run their specific service.
Machines

Machines are another type of object within Active Directory; for every computer that joins the Active Directory domain, a machine object will be created. Machines are also considered "security principals" and are assigned an account just as any regular user. This account has somewhat limited rights within the domain itself.

The machine accounts themselves are local administrators on the assigned computer, they are generally not supposed to be accessed by anyone except the computer itself, but as with any other account, if you have the password, you can use it to log in.

Note: Machine Account passwords are automatically rotated out and are generally comprised of 120 random characters.

Identifying machine accounts is relatively easy. They follow a specific naming scheme. The machine account name is the computer's name followed by a dollar sign. For example, a machine named DC01 will have a machine account called DC01$.

Security Groups

If you are familiar with Windows, you probably know that you can define user groups to assign access rights to files or other resources to entire groups instead of single users. This allows for better manageability as you can add users to an existing group, and they will automatically inherit all of the group's privileges. Security groups are also considered security principals and, therefore, can have privileges over resources on the network.

Groups can have both users and machines as members. If needed, groups can include other groups as well.

Several groups are created by default in a domain that can be used to grant specific privileges to users. As an example, here are some of the most important groups in a domain:

| Security Group     | Description |
|--------------------|-------------|
| Domain Admins      | Users of this group have administrative privileges over the entire domain. By default, they can administer any computer on the domain, including the DCs. |
| Server Operators   | Users in this group can administer Domain Controllers. They cannot change any administrative group memberships. |
| Backup Operators   | Users in this group are allowed to access any file, ignoring their permissions. They are used to perform backups of data on computers. |
| Account Operators  | Users in this group can create or modify other accounts in the domain. |
| Domain Users       | Includes all existing user accounts in the domain. |
| Domain Computers   | Includes all existing computers in the domain. |
| Domain Controllers | Includes all existing DCs on the domain. |

You can obtain the complete list of default security groups from the Microsoft documentation.

Active Directory Users and Computers

To configure users, groups or machines in Active Directory, we need to log in to the Domain Controller and run "Active Directory Users and Computers" from the start menu:

Start menu AD Users and Computers

This will open up a window where you can see the hierarchy of users, computers and groups that exist in the domain. These objects are organised in Organizational Units (OUs) which are container objects that allow you to classify users and machines. OUs are mainly used to define sets of users with similar policing requirements. The people in the Sales department of your organisation are likely to have a different set of policies applied than the people in IT, for example. Keep in mind that a user can only be a part of a single OU at a time.

Checking our machine, we can see that there is already an OU called THM with four child OUs for the IT, Management, Marketing and Sales departments. It is very typical to see the OUs mimic the business' structure, as it allows for efficiently deploying baseline policies that apply to entire departments. Remember that while this would be the expected model most of the time, you can define OUs arbitrarily. Feel free to right-click the THM OU and create a new OU under it called Students just for the fun of it.

AD Users and Computers

If you open any OUs, you can see the users they contain and perform simple tasks like creating, deleting or modifying them as needed. You can also reset passwords if needed (pretty useful for the helpdesk):

IT department OU

You probably noticed already that there are other default containers apart from the THM OU. These containers are created by Windows automatically and contain the following:

Builtin: Contains default groups available to any Windows host.
Computers: Any machine joining the network will be put here by default. You can move them if needed.
Domain Controllers: Default OU that contains the DCs in your network.
Users: Default users and groups that apply to a domain-wide context.
Managed Service Accounts: Holds accounts used by services in your Windows domain.
Security Groups vs OUs

You are probably wondering why we have both groups and OUs. While both are used to classify users and computers, their purposes are entirely different:

OUs are handy for applying policies to users and computers, which include specific configurations that pertain to sets of users depending on their particular role in the enterprise. Remember, a user can only be a member of a single OU at a time, as it wouldn't make sense to try to apply two different sets of policies to a single user.
Security Groups, on the other hand, are used to grant permissions over resources. For example, you will use groups if you want to allow some users to access a shared folder or network printer. A user can be a part of many groups, which is needed to grant access to multiple resources.

Your first task as the new domain administrator is to check the existing AD OUs and users, as some recent changes have happened to the business. You have been given the following organisational chart and are expected to make changes to the AD to match it:

THM Organisational Chart

Deleting extra OUs and users

The first thing you should notice is that there is an additional department OU in your current AD configuration that doesn't appear in the chart. We've been told it was closed due to budget cuts and should be removed from the domain. If you try to right-click and delete the OU, you will get the following error:

OU delete error

By default, OUs are protected against accidental deletion. To delete the OU, we need to enable the Advanced Features in the View menu:

Enabling advanced features

This will show you some additional containers and enable you to disable the accidental deletion protection. To do so, right-click the OU and go to Properties. You will find a checkbox in the Object tab to disable the protection:

Disable OU delete protection

Be sure to uncheck the box and try deleting the OU again. You will be prompted to confirm that you want to delete the OU, and as a result, any users, groups or OUs under it will also be deleted.

After deleting the extra OU, you should notice that for some of the departments, the users in the AD don't match the ones in our organisational chart. Create and delete users as needed to match them.

Delegation

One of the nice things you can do in AD is to give specific users some control over some OUs. This process is known as delegation and allows you to grant users specific privileges to perform advanced tasks on OUs without needing a Domain Administrator to step in.

One of the most common use cases for this is granting IT support the privileges to reset other low-privilege users' passwords. According to our organisational chart, Phillip is in charge of IT support, so we'd probably want to delegate the control of resetting passwords over the Sales, Marketing and Management OUs to him.

For this example, we will delegate control over the Sales OU to Phillip. To delegate control over an OU, you can right-click it and select Delegate Control:

Delegating OU control

This should open a new window where you will first be asked for the users to whom you want to delegate control:

Note: To avoid mistyping the user's name, write "phillip" and click the Check Names button. Windows will autocomplete the user for you.

Delegating Sales OU to Phillip

Click OK, and on the next step, select the following option:

Delegating password resets

Click next a couple of times, and now Phillip should be able to reset passwords for any user in the sales department. While you'd probably want to repeat these steps to delegate the password resets of the Marketing and Management departments, we'll leave it here for this task. You are free to continue to configure the rest of the OUs if you so desire.

Now let's use Phillip's account to try and reset Sophie's password. Here are Phillip's credentials for you to log in via RDP:

THM key
Username	phillip
Password	Claire2008
Note: When connecting via RDP, use THM\phillip as the username to specify you want to log in using the user phillip on the THM domain.

While you may be tempted to go to Active Directory Users and Computers to try and test Phillip's new powers, he doesn't really have the privileges to open it, so you'll have to use other methods to do password resets. In this case, we will be using Powershell to do so:

```powershell
Windows PowerShell (As Phillip)
PS C:\Users\phillip> Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose

New Password: *********

VERBOSE: Performing the operation "Set-ADAccountPassword" on target "CN=Sophie,OU=Sales,OU=THM,DC=thm,DC=local".
```

Since we wouldn't want Sophie to keep on using a password we know, we can also force a password reset at the next logon with the following command:

```powershell
Windows PowerShell (as Phillip)
PS C:\Users\phillip> Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose

VERBOSE: Performing the operation "Set" on target "CN=Sophie,OU=Sales,OU=THM,DC=thm,DC=local".
```

THM flag
Log into Sophie's account with your new password and retrieve a flag from Sophie's desktop.
Note: When connecting via RDP, use THM\sophie as the username to specify you want to log in using the user sophie on the THM domain.

By default, all the machines that join a domain (except for the DCs) will be put in the container called "Computers". If we check our DC, we will see that some devices are already there:

Computers OU

We can see some servers, some laptops and some PCs corresponding to the users in our network. Having all of our devices there is not the best idea since it's very likely that you want different policies for your servers and the machines that regular users use on a daily basis.

While there is no golden rule on how to organise your machines, an excellent starting point is segregating devices according to their use. In general, you'd expect to see devices divided into at least the three following categories:

1. Workstations

Workstations are one of the most common devices within an Active Directory domain. Each user in the domain will likely be logging into a workstation. This is the device they will use to do their work or normal browsing activities. These devices should never have a privileged user signed into them.

2. Servers

Servers are the second most common device within an Active Directory domain. Servers are generally used to provide services to users or other servers.

3. Domain Controllers

Domain Controllers are the third most common device within an Active Directory domain. Domain Controllers allow you to manage the Active Directory Domain. These devices are often deemed the most sensitive devices within the network as they contain hashed passwords for all user accounts within the environment.

Since we are tidying up our AD, let's create two separate OUs for Workstations and Servers (Domain Controllers are already in an OU created by Windows). We will be creating them directly under the thm.local domain container. In the end, you should have the following OU structure:

final OU structure

Now, move the personal computers and laptops to the Workstations OU and the servers to the Servers OU from the Computers container. Doing so will allow us to configure policies for each OU later.

So far, we have organised users and computers in OUs just for the sake of it, but the main idea behind this is to be able to deploy different policies for each OU individually. That way, we can push different configurations and security baselines to users depending on their department.

Windows manages such policies through Group Policy Objects (GPO). GPOs are simply a collection of settings that can be applied to OUs. GPOs can contain policies aimed at either users or computers, allowing you to set a baseline on specific machines and identities.

To configure GPOs, you can use the Group Policy Management tool, available from the start menu:

Start menu GPM

The first thing you will see when opening it is your complete OU hierarchy, as defined before. To configure Group Policies, you first create a GPO under Group Policy Objects and then link it to the OU where you want the policies to apply. As an example, you can see there are some already existing GPOs in your machine:

Existing OUs in your machine

We can see in the image above that 3 GPOs have been created. From those, the Default Domain Policy and RDP Policy are linked to the thm.local domain as a whole, and the Default Domain Controllers Policy is linked to the Domain Controllers OU only. Something important to have in mind is that any GPO will apply to the linked OU and any sub-OUs under it. For example, the Sales OU will still be affected by the Default Domain Policy.

Let's examine the Default Domain Policy to see what's inside a GPO. The first tab you'll see when selecting a GPO shows its scope, which is where the GPO is linked in the AD. For the current policy, we can see that it has only been linked to the thm.local domain:

OU scope

As you can see, you can also apply Security Filtering to GPOs so that they are only applied to specific users/computers under an OU. By default, they will apply to the Authenticated Users group, which includes all users/PCs.

The Settings tab includes the actual contents of the GPO and lets us know what specific configurations it applies. As stated before, each GPO has configurations that apply to computers only and configurations that apply to users only. In this case, the Default Domain Policy only contains Computer Configurations:

OU Settings

Feel free to explore the GPO and expand on the available items using the "show" links on the right side of each configuration. In this case, the Default Domain Policy indicates really basic configurations that should apply to most domains, including password and account lockout policies:

OU detailed settings

Since this GPO applies to the whole domain, any change to it would affect all computers. Let's change the minimum password length policy to require users to have at least 10 characters in their passwords. To do this, right-click the GPO and select Edit:

Editing a GPO settings

This will open a new window where we can navigate and edit all the available configurations. To change the minimum password length, go to Computer Configurations -> Policies -> Windows Setting -> Security Settings -> Account Policies -> Password Policy and change the required policy value:

Password policy GPO

As you can see, plenty of policies can be established in a GPO. While explaining every single of them would be impossible in a single room, do feel free to explore a bit, as some of the policies are straightforward. If more information on any of the policies is needed, you can double-click them and read the Explain tab on each of them:

OU settings explain tab

GPO distribution

GPOs are distributed to the network via a network share called SYSVOL, which is stored in the DC. All users in a domain should typically have access to this share over the network to sync their GPOs periodically. The SYSVOL share points by default to the C:\Windows\SYSVOL\sysvol\ directory on each of the DCs in our network.

Once a change has been made to any GPOs, it might take up to 2 hours for computers to catch up. If you want to force any particular computer to sync its GPOs immediately, you can always run the following command on the desired computer:

Windows PowerShell
PS C:\> gpupdate /force
Creating some GPOs for THM Inc.

As part of our new job, we have been tasked with implementing some GPOs to allow us to:

Block non-IT users from accessing the Control Panel.
Make workstations and servers lock their screen automatically after 5 minutes of user inactivity to avoid people leaving their sessions exposed.
Let's focus on each of those and define what policies we should enable in each GPO and where they should be linked.

Restrict Access to Control Panel

We want to restrict access to the Control Panel across all machines to only the users that are part of the IT department. Users of other departments shouldn't be able to change the system's preferences.

Let's create a new GPO called Restrict Control Panel Access and open it for editing. Since we want this GPO to apply to specific users, we will look under User Configuration for the following policy:

Restricting access to control panel

Notice we have enabled the Prohibit Access to Control Panel and PC settings policy.

Once the GPO is configured, we will need to link it to all of the OUs corresponding to users who shouldn't have access to the Control Panel of their PCs. In this case, we will link the Marketing, Management and Sales OUs by dragging the GPO to each of them:

Linking Restrict Control Panel GPO

Auto Lock Screen GPO

For the first GPO, regarding screen locking for workstations and servers, we could directly apply it over the Workstations, Servers and Domain Controllers OUs we created previously.

While this solution should work, an alternative consists of simply applying the GPO to the root domain, as we want the GPO to affect all of our computers. Since the Workstations, Servers and Domain Controllers OUs are all child OUs of the root domain, they will inherit its policies.

Note: You might notice that if our GPO is applied to the root domain, it will also be inherited by other OUs like Sales or Marketing. Since these OUs contain users only, any Computer Configuration in our GPO will be ignored by them.

Let's create a new GPO, call it Auto Lock Screen, and edit it. The policy to achieve what we want is located in the following route:

Configuring machine inactivity limit

We will set the inactivity limit to 5 minutes so that computers get locked automatically if any user leaves their session open. After closing the GPO editor, we will link the GPO to the root domain by dragging the GPO to it:

Linking Auto Lock Screen GPO

Once the GPOs have been applied to the correct OUs, we can log in as any users in either Marketing, Sales or Management for verification. For this task, let's connect via RDP using Mark's credentials:

THM key
Username	Mark
Password	M4rk3t1ng.21
Note: When connecting via RDP, use THM\Mark as the username to specify you want to log in using the user Mark on the THM domain.

If we try opening the Control Panel, we should get a message indicating this operation is denied by the administrator. You can also wait 5 minutes to check if the screen is automatically locked if you want.

Since we didn't apply the control panel GPO on IT, you should still be able to log into the machine as any of those users and access the control panel. 

Note: If you created and linked the GPOs, but for some reason, they still don't work, remember you can run gpupdate /force to force GPOs to be updated.

So far, we have discussed how to manage a single domain, the role of a Domain Controller and how it joins computers, servers and users.

Single Domain

As companies grow, so do their networks. Having a single domain for a company is good enough to start, but in time some additional needs might push you into having more than one.

Trees

Imagine, for example, that suddenly your company expands to a new country. The new country has different laws and regulations that require you to update your GPOs to comply. In addition, you now have IT people in both countries, and each IT team needs to manage the resources that correspond to each country without interfering with the other team. While you could create a complex OU structure and use delegations to achieve this, having a huge AD structure might be hard to manage and prone to human errors.

Luckily for us, Active Directory supports integrating multiple domains so that you can partition your network into units that can be managed independently. If you have two domains that share the same namespace (thm.local in our example), those domains can be joined into a Tree.

If our thm.local domain was split into two subdomains for UK and US branches, you could build a tree with a root domain of thm.local and two subdomains called uk.thm.local and us.thm.local, each with its AD, computers and users:

Tree

This partitioned structure gives us better control over who can access what in the domain. The IT people from the UK will have their own DC that manages the UK resources only. For example, a UK user would not be able to manage US users. In that way, the Domain Administrators of each branch will have complete control over their respective DCs, but not other branches' DCs. Policies can also be configured independently for each domain in the tree.

A new security group needs to be introduced when talking about trees and forests. The Enterprise Admins group will grant a user administrative privileges over all of an enterprise's domains. Each domain would still have its Domain Admins with administrator privileges over their single domains and the Enterprise Admins who can control everything in the enterprise.

Forests

The domains you manage can also be configured in different namespaces. Suppose your company continues growing and eventually acquires another company called MHT Inc. When both companies merge, you will probably have different domain trees for each company, each managed by its own IT department. The union of several trees with different namespaces into the same network is known as a forest.

Forest

Trust Relationships

Having multiple domains organised in trees and forest allows you to have a nice compartmentalised network in terms of management and resources. But at a certain point, a user at THM UK might need to access a shared file in one of MHT ASIA servers. For this to happen, domains arranged in trees and forests are joined together by trust relationships.

In simple terms, having a trust relationship between domains allows you to authorise a user from domain THM UK to access resources from domain MHT EU.

The simplest trust relationship that can be established is a one-way trust relationship. In a one-way trust, if Domain AAA trusts Domain BBB, this means that a user on BBB can be authorised to access resources on AAA:

Trusts

The direction of the one-way trust relationship is contrary to that of the access direction.

Two-way trust relationships can also be made to allow both domains to mutually authorise users from the other. By default, joining several domains under a tree or a forest will form a two-way trust relationship.

It is important to note that having a trust relationship between domains doesn't automatically grant access to all resources on other domains. Once a trust relationship is established, you have the chance to authorise users across different domains, but it's up to you what is actually authorised or not.

When using Windows domains, all credentials are stored in the Domain Controllers. Whenever a user tries to authenticate to a service using domain credentials, the service will need to ask the Domain Controller to verify if they are correct. Two protocols can be used for network authentication in windows domains:

Kerberos: Used by any recent version of Windows. This is the default protocol in any recent domain.
NetNTLM: Legacy authentication protocol kept for compatibility purposes.
While NetNTLM should be considered obsolete, most networks will have both protocols enabled. Let's take a deeper look at how each of these protocols works.

Kerberos Authentication

Kerberos authentication is the default authentication protocol for any recent version of Windows. Users who log into a service using Kerberos will be assigned tickets. Think of tickets as proof of a previous authentication. Users with tickets can present them to a service to demonstrate they have already authenticated into the network before and are therefore enabled to use it.

When Kerberos is used for authentication, the following process happens:

The user sends their username and a timestamp encrypted using a key derived from their password to the Key Distribution Center (KDC), a service usually installed on the Domain Controller in charge of creating Kerberos tickets on the network.

The KDC will create and send back a Ticket Granting Ticket (TGT), which will allow the user to request additional tickets to access specific services. The need for a ticket to get more tickets may sound a bit weird, but it allows users to request service tickets without passing their credentials every time they want to connect to a service. Along with the TGT, a Session Key is given to the user, which they will need to generate the following requests.

Notice the TGT is encrypted using the krbtgt account's password hash, and therefore the user can't access its contents. It is essential to know that the encrypted TGT includes a copy of the Session Key as part of its contents, and the KDC has no need to store the Session Key as it can recover a copy by decrypting the TGT if needed.

Kerberos step 1

When a user wants to connect to a service on the network like a share, website or database, they will use their TGT to ask the KDC for a Ticket Granting Service (TGS). TGS are tickets that allow connection only to the specific service they were created for. To request a TGS, the user will send their username and a timestamp encrypted using the Session Key, along with the TGT and a Service Principal Name (SPN), which indicates the service and server name we intend to access.

As a result, the KDC will send us a TGS along with a Service Session Key, which we will need to authenticate to the service we want to access. The TGS is encrypted using a key derived from the Service Owner Hash. The Service Owner is the user or machine account that the service runs under. The TGS contains a copy of the Service Session Key on its encrypted contents so that the Service Owner can access it by decrypting the TGS.

Kerberos step 2

The TGS can then be sent to the desired service to authenticate and establish a connection. The service will use its configured account's password hash to decrypt the TGS and validate the Service Session Key.
Kerberos step 3

NetNTLM Authentication

NetNTLM works using a challenge-response mechanism. The entire process is as follows:

NetNTLM authentication

The client sends an authentication request to the server they want to access.
The server generates a random number and sends it as a challenge to the client.
The client combines their NTLM password hash with the challenge (and other known data) to generate a response to the challenge and sends it back to the server for verification.
The server forwards the challenge and the response to the Domain Controller for verification.
The domain controller uses the challenge to recalculate the response and compares it to the original response sent by the client. If they both match, the client is authenticated; otherwise, access is denied. The authentication result is sent back to the server.
The server forwards the authentication result to the client.
Note that the user's password (or hash) is never transmitted through the network for security.

Note: The described process applies when using a domain account. If a local account is used, the server can verify the response to the challenge itself without requiring interaction with the domain controller since it has the password hash stored locally on its SAM.

