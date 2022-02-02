æ# Global Glossary

### Access Control
Access control is a security concept related to controlling the level of access or permission that a user, group, or other identity is entitled to. There are a variety of different methods of managing access control. 

#### Access Control Lists
<a id="acl"></a>
ACL's are a table or dictionary, usually on a computer, that inform the operating system or security software which access rights each entity (user, group, etc.) is entitled to on a particular system or to a particular object, such as directories or files. The individual entries on this list are called "trustees" and correspond to a user or group and detail the permissions they have been given. On an ACL are ACE's, or access control entities. 

#### Access Control Entries
<a id="ace"></a>
Access control Entries (ACE) are listed on an ACL and consist of the name of a user or group of users and the rights they have on an associated system. On an ACL, each entry is an Access Control Entry (ACE). *Windows*has six types of ACEs, each with a SID, a collection of access rights, and various flags that indicate differing attributes. These are the elements of an ACE
-   A [Security Identifier (SID)](Windows%20Fundamentals/99%20Glossary%20(Windows).md#Security%20Identifiers%20SID) that identifies the [trustee](https://docs.microsoft.com/en-us/windows/win32/secauthz/trustees) to which the ACE applies.
-   An [_access mask_](https://docs.microsoft.com/en-us/windows/desktop/SecGloss/a-gly) that specifies the [access rights](https://docs.microsoft.com/en-us/windows/win32/secauthz/access-rights-and-access-masks) controlled by the ACE.
-   A flag that indicates the type of ACE.
-   A set of bit flags that determine whether child containers or objects can inherit the ACE from the primary object to which the ACL is attached.

#### Discretionary Access Control (DAC)
DAC is a type of access control that relates to the granting/restricting of access based on the identity of the subject and/or the groups they belong to. For example, on *Linux*, there are **r** - read, **w** - write, and **x** - execute permissions, assigned to either the owner, group, or everyone type of user group. 

#### Principle of Least Privilege
#### Least Privilege
The concept of "least privilege," or the "principle of least privilege," refers to granting all users, applications, or processes that require privileges on a system the minimum level required to perform their job tasks. In short, if you don't need access to something, you don't have it, whether it be access to a folder, file, or program. This is a design principle across all security architectures. Like in the movies, if you don't have the clearance level..."That's classified.""

#### Inheritance
Inheritance is the concept that a "child" will acquire attributes of the "parent." This is broad, and can relate to [Permissions](Windows%20Fundamentals/99%20Glossary%20(Windows).md#Permissions) for files and folders, or [processes](Windows%20Fundamentals/09%20Windows%20Processes.md#Processes%20Explained) that are the parent or child of another process.

#### Libraries
The concept of "libraries" is universal to most programming languages. Essentially, a *library* is a set of code that accomplishes a specific task, enables a particular function, or otherwise "does something" that a programmer may want to incorporate into their code without having to write it themselves.

Libraries allow code to be written without "reinventing the wheel," allowing existing functionality to be imported into another program. 

#### Protocol Data Unit
A PDU[^1] refers to the single unit of information transmitted to related entities across a network. A PDU is protocol specific and contains user data. In most data architectures, such as the TCP/IP or OSI model, each layer implements protocols specific to the type or mode of the exchange.

[^1]: https://en.wikipedia.org/wiki/Protocol_data_unit