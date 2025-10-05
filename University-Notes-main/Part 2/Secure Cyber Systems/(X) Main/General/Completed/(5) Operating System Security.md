1. **What is operating system security?**

mechanisms in place to protect the OS from threats, vulnerabilities, and unauthorized access. 

measures to prevent a person from illegally using resources in a computersystem

2. **What is user identifier, and how it works?**

unique numerical values assigned to users in an OS to identify and manage their acess to system resources

root has UID of 0

GID = group ID, manage group-based permissions

when a user logs in, the system assigns their UID and GID to the sesson

3. **What is file system security, and permission types?**

• refers to the mechanisms and practices used to protect the data stored in a file
system from unauthorized access, corruption, or loss.
• It ensures the confidentiality, integrity, and availability of files and directories.

• Permission bits are grouped in three triples – define read, write, and execute access for
owner, group, and other.
• A ‘-’ indicates that a right is not granted

A permission string like rwxr-xr-- means:
• The owner has read, write, and execute permissions (rwx).
• The group has read and execute permissions (r-x).
• Others have only read permissions (r--)

4. **What is process and memory protection?**

ensure that processes (running programs) operate in
isolation and do not interfere with each other 

Ensures that a process can only access memory regions it is authorized to use.

5. **What is buffer overflow and what is a buffer?**

Attackers exploit poorly written code to overwrite memory and execute malicious code

a buffer is a fixed-size block of memory
A buffer is a location where data is stored

6. **Can you give some error messages related to buffer overflow?**

-Bus Error
• Memory doesn’t exist
-Segmentation fault
• Memory protection deny access
-General Protection fault
• Memory protection deny access

7. **What is patch management and types of patches?**

identifying,
acquiring, testing, and deploying
updates (called "patches")

to
software, operating systems, and
applications to fix vulnerabilities,
bugs, or improve functionality

. Inventory and Assessment
• Maintain an inventory of all hardware and software assets.
• Identify which systems and applications require patches.
2. Vulnerability Monitoring
• Monitor for new vulnerabilities and patches released by vendors.
• Use tools like vulnerability scanners or subscribe to security bulletins.
3. Patch Acquisition
• Download patches from trusted sources (e.g., vendor websites).
• Verify the integrity of patches using checksums or digital signatures.

4. Testing
• Test patches in a controlled environment (e.g., staging or sandbox) to ensure they do not cause
issues.
• Check for compatibility with existing systems and applications.
5. Deployment
• Deploy patches to production systems after testing.
6. Verification and Documentation
• Verify that patches were successfully applied and systems are functioning correctly.
• Monitor for any unexpected issues post-deployment.
• Maintain records of patching activities, including which patches were applied and when. 

7. **What are the main purposes of auditing and logging?**

Logging is the process of recording events, activities, and transactions that occur within a
system, application, or network

Auditing is the process of reviewing and analyzing logs and records to ensure compliance,
detect anomalies, and investigate security incidents


8. **Can you list some types of logs?**


System Logs:
Record operating system events (e.g.,
startup, shutdown, hardware errors).
Application Logs:
Track events within specific applications (e.g.,
login attempts, errors).
Security Logs:
Capture security-related events (e.g.,
authentication, access control, intrusion
attempts). 39
Network Logs:
Monitor network traffic and connections
(e.g., firewall logs, DNS queries).
Audit Logs:
Specifically track user activities and changes
for compliance and accountability



DESCRIBE HOW USER IDENTIFIERS WORK

**User Identifiers (UIDs)** are unique numeric or alphanumeric values assigned to each user on a computer system or network.

DESCRIBE THE CONCEPT OF FILE SYSTEM SECURTIY

**File System Security** involves protecting data stored on a computer’s file system from unauthorized access, alteration, or deletion.

permissions: RWX - every file is owned by a user and a group
ACLs access control lists


DESCRIBE BUFFER OVERFLOW AND ERROR MESSAGE

**Buffer Overflow** is a vulnerability that occurs when more data is written to a memory buffer than it can hold.

This can overwrite adjacent memory, potentially allowing attackers to inject malicious code.


DESCRIBE THE CONCEPT OF PATCH MANAGEMENT

Regularly updating the OS to fix vulnerabilities and bugs.
• Applying security patches to address known exploits

**Patch Management** is the process of acquiring, testing, and applying updates to software to fix known vulnerabilities, improve performance, or add new features.

DESCRIBE THE CONCEPT OF AUDITING AND LOGING

**Auditing and Logging** are critical for tracking system activity, detecting unauthorized access, and supporting forensic investigations.
**Logs** record events such as login attempts, file access, software installations, and network activity.

e.g., syslog