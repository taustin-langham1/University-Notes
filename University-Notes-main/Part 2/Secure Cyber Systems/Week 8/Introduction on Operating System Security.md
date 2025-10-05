
- overview
- Access control
- File system sec
- Process and memory protection
- patch management
- auditing and logging


- describe how identifiers work
- describe the concept of file system security
- understand and describe buffer overflow and error messages
- understand patch management 
- describe the concept of auditing and logging

# Operating system security


## OS security is relevant to...

**Access control**

- authentication: verifying the identity of users
- authorisation: granting or restricting access to resources based on user roles and permissions

**User management**

- Creating and managing user accounts with appropriate privileges
- implementing the principle of least privilege.

**File system security**

- protecting files and directories through permissions
- encrypting sensitive data to prevent unauthorised access

**Process and memory protection**

- isolating processes to prevent interference or exploitation
- preventing buffer overflows and other memory related attacks 

**Physical security**

- protecting hardware and physical access to systems

**Patch management**

- regularly updating the OS to fix vulnerabilities and bugs
- applying security patches to address known exploits

**Auditing and Logging**

- Tracking system activities and user actions for accountability
- analysing logs to detect and respond to suspicious behaviour 

**Malware protection**

- using antivirus and anti-malware tools to detect and remove malicious software
- preventing the execution of unauthorised or harmful programs


# Access Control (User Identifiers)


- an active entity, called 'subject' request access to a passive entity, called 'object'

- subject: user or process (active)
- object - file or resource (passive)
- access operators: the operations

****

**discretionary**

- the owner of a resource decides who is allowed access
- access control is at the owners discretion

**mandatory**

- a system wide policy decrees who is allowed access

## user identifiers 

**UIDs** are unique numerical values assigned to users in an operating system to identify and manage their access to system resources


- a user cannot actually open a file

we can use "Process"

- a program in excecution
- a process has process ID (PID)
- A process open the file on our behalf


## Types of User Identifiers

##### UID values differ from system to system


- UID (User ID)
	- A unique number assigned to each user in the system
	- the root user (superuser) typically has a UID of 0
	- Regular users are assigned UIDs starting from a specific range (e.g., 1000 and above in many Linux systems)
	
- GID (Group ID)
	- A unique number assigned to a group of users
	- Users can belong to one or more groups, and GIDs help manage group-based permissions

- Effective UID (EUID):
	- Used to determine access rights for privileges of another user 

- Real UID (RUID):
	- The UID of the user who started the process

- Saved UID (SUID):
	- Allows a process to switc)h back to a privileged UID after temporarily dropping privileges


## How do UIDs work?

- when a user logs in, the system assigns their UID and GID to the session.
- files and processes created by the user inherit their UID and GID 
- permissions for files and directories are checked against the UID and GID of the user or process attempting access

**Example:**

- Linux/Unix Systems:
	- UID 0 is reserved for the root user (*Superuser*)
	- regular users have UIDs starting from 1000 (configurable in /etc/login.defs)
	- group information is stored in /ect/group, and user information in /ect/passwd.


## Special UIDs 

- **Root (UID 0):** Has unrestricted access to the system

- **System Users (UID 1-999):** Reserved for system services and daemons (e.g., www-data for web servers)
	- www-data is a special user account commonly used in linux-based operating systems, particularly in web server environments. it is primarily with web servers like Apache and Nginx
- **Nobody (UID 65534):** A restricted user with minimal privileges, often used for running untrusted processes



## Potential Threats 

**Privilege Escalation:**

- attackers may exploit misconfigured UID (e.g., setuid programs) to gain elevated privileges

**UID Reuse:**

- reassigning a UID to a new user can lead to unintended access to files owned by the previous user


**Least Privilege:**

- assigning appropriate UIDs and GIDs ensures users and processes operate with minimal privileges, reducing the attack surface



# File System Security 


- refers to the mechanisms and practices used to protect the data stored in a file system from unauthorised access, corruption, or loss
- it ensures the confidentiality, integrity, and availability of files and directories 

- file system security is a critical aspect of operating system security and involves a combination of technical controls, permissions, and policies


## File permissions

**Ownership:**
- each file and directory is owned by a specific user and group
- the owner has control over the file's permissions 


**Permission Types:**
- read (r): allows viewing or reading the file/directory
- write(w): allows modifying or deleting the file/directory
- execute(x): allows running the file as a program or accessing the directory

**Permission Levels:**

- User (Owner): permissions for the file owner
- Group: permissions for members of the file's group 
- others: permissions for all other users


## Linux File permissions


- permission bits are grouped in three triples - define read, write, and execute access for owner, group, and other
- A '-' indicates that a right is not granted

- **Example:**
	- A permission string like rwxr-xr-- means:

(broken up like - - -, - - -, - - - )

- the owner has read,write, and execute permissions (rwx).
- the group has read and execute permissions (r-x)
- others have only read permissions (r--)


## File integrity checking 

- we can use tools lie tripwire or AIDE to monitor files for unauthorised changed by comparing current file states with a known baseline 

• Tripwire (https://www.tripwire.com/)
• Advanced Intrusion Detection Environment (AIDE)
(https://aide.github.io/)


## Example of file system security in Different OSs


Linux/unix: 

- uses permissions (e.g., chmod, chown) and ACLs for access control
- Tools like SELinux or AppArmor provide additional security policies

Windows:

- uses NTFS permissios and ACLs
- Features like BitLocker provide encryption for file systems

macOS:

- uses APFS (Apple File System) with built-in encryption and permissions


# Process and Memory Protection


- Refers to the mechanisms implemented by an operating system to *ensure that processes operate in isolation and do not interfere with each other* or access memory they are not authorised to use


**Process isolation**

- each process runs in its own virtual address space, isolated from other processes.

- prevents one process from accessing or corrupting the memory of another process

**Memory protection**


- ensures that a process can only access memory regions it is authorised to use
- prevents unathorised access to OS kernel's memory or other processes' memory

#### Potential Threats

**Privilege Levels** 

- modern CPUs support multiple privilege levels (e.g., user mode and kernel mode)
- user processes run in user mode with limited privileges, while the OS kernel runs in kernel mode with full access to hardware and memory

**Buffer overflows**

- attackers exploit poorly written code to overwrite memory and execute malicious ocde
- mitigated by systems like ASLR, NX bit, and stack canaries

**Privilege escalation**

- attackers attempt to gain higher privileges to take control
- mitigated by strict separation between user and kernel mode

**Denial of Service (DoS)**

- malicious processes may consume excessive resources, causing the system to crash or become unresponsive
- mitigated by resource limits and process scheduling 


## What is a buffer overflow?

is a type of software vulnerability that occurs when a program writes more data (a fixed size block of memory) to a buffer than it can hold

this excess data can overwrite adjacent memory locations, leading to unpredictable behavior, crashes, or even security exploits 

buffer overflows are a common target for attackers because they can be exploited to execute malicious code, escalate privileges, or crash a system

with buffer overflow, attacks can possibly do:


- force the program to spawn a command shell to execute commands

- add account 
- remotely control the GUI
- alter system configuration