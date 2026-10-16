

## Main Implementation Techniques of Trojan Horses

### Auto-Start Technology

Apart from the first run when a user must execute it, a Trojan program generally loads its server-side program automatically every time the user starts the system.

### Hiding Technology

To prevent Trojan programs from being discovered, Trojan designers will adopt as many hiding methods as possible and will not show themselves in the system. Trojan programs are generally very small in size and do not consume too many resources when executed.

### Remote Monitoring Technology

Remote monitoring is the main function of a Trojan and also its ultimate purpose. It includes monitoring the target host's mouse, keyboard, screen display, and even network communication traffic direction; it also includes collecting information about the target computer's system; it can also control the target machine to run programs or disable functions on the attacked computer according to the attacker's will.

## Examples of Trojans

- Remote access Trojans are currently the most widespread type of Trojan horse. They can access the victim's hard drive and control it. This type of Trojan is very simple to use: as long as a user runs the server program and the attacker obtains the user's IP address, the attacker can access the user's computer. This Trojan allows a remote controller to do anything on the local machine, such as keystroke logging, upload and download functions, screen capture, and so on. Famous Trojans of this type include BO (Back Office) and the domestic Glacier (Binghe).
- Password-sending Trojans aim to find all hidden passwords and send them to a designated mailbox without the victim's knowledge. Most Trojans of this type do not restart every time Windows restarts, and most of them use port 25 to send e-mail.
- Keystroke-logging Trojans are very simple: they do only one thing—record the victim's keystrokes and keep a complete record in a log file. This type of Trojan starts with Windows and records everything while the victim is online.
- The sole function of destructive Trojans is to destroy and delete files. This makes them very simple and easy to use. They can automatically delete all .DLL, .INI, or EXE files on the user's computer.
- FTP Trojans open port 21 on the user's computer (the default port used by FTP), allowing anyone with an FTP client program to connect to the computer without a password and perform uploads and downloads with the highest privileges.

## Trojan Intrusion Process on the Server Side

| Client C | Server S |
| --- | --- |
| Implantation | Install, hide, open port for listening |
| Connection request | Respond |
| Remote control | Monitor, file operations, system manipulation |

## Other Attacks

### Spoofing Attacks

Spoofing attacks are an important means of network attacks. Common spoofing methods include DNS spoofing, e-mail spoofing, Web spoofing, IP spoofing, and so on.

### Attacks Exploiting Program Errors (Vulnerabilities)

As a complete system, no matter how much its security is strengthened, it still has security vulnerabilities of varying degrees to a greater or lesser extent, let alone the various other types of software commonly used. In a sense, errors in programs are almost inevitable. Any small oversight or mistake by software developers gives intruders an opportunity.

## Meaning of Vulnerabilities

- A vulnerability is a defect in hardware, software, or policy that allows attackers to access or control a system without authorization.
- A vulnerability is a defect that was not considered during software development; it is also called a software bug.
- A vulnerability refers to inherent defects or configuration errors in computer system hardware and software, including operating systems and applications. These defects and errors can be easily exploited by hackers to attack computer systems.

## Understanding Vulnerabilities

- Vulnerabilities generally refer to (security) flaws in software.
- Vulnerabilities exist in common software.
- Vulnerabilities are unknown in advance and discovered afterwards.
- Vulnerabilities are security risks; if exploited, the consequences are unpredictable.
- Vulnerabilities can generally be exploited remotely.
- Vulnerabilities can generally be patched.

![](img/56e4826257c2e3f407630825aa58ce2d_131_0.png)

## Causes of Vulnerabilities

- Design flaws
- Considerations of interest
- Software is becoming increasingly complex

## An Example of a Vulnerability (RPC Overflow Vulnerability)

Release date: 2003-07-14

Severity: High

Threat level: Remote administrator privileges

Hazard description: Remotely enter the system and execute arbitrary code

Error type: Design error

Exploitation method: Server mode

CVE ID: CAN-2003-0352

Affected systems: Windows series (NT, 2000, XP, 2003)

## RPC Overflow Vulnerability

By writing content beyond the length of a program's buffer, a buffer overflow is caused, thereby corrupting the program's stack and causing the program to execute other instructions, thus achieving the purpose of an attack.

Remote Procedure Call (RPC) is a remote procedure call protocol used by the Windows operating system. The RPC protocol provides an interactive interprocess communication mechanism that allows program processes on a local machine to seamlessly run code in remote systems. The predecessor of this protocol was the OSF RPC protocol, but Microsoft added some of its own extensions.

## Causes of the RPC Vulnerability

- The DCOM interface of RPC is responsible for handling DCOM object activation requests, but it cannot correctly handle malformed messages.
- Its essence is the failure to effectively check its parameters.

## Common Ways to Apply Patches

- Version upgrade.
- Directly run the patch program.
- Modify settings.
- Disable unnecessary services (ports).

## Time Relationship Among Vulnerabilities, Attack Programs, Patches, and Viruses

Virus name: Blaster

Vulnerability exploited: Windows RPC vulnerability

Microsoft advisory: MS03-026 (2003.7.14)

Patch release date: 2003.7.16

Attack code discovery date: 2003.7.24

Virus appearance date: 2003.8.13

Remediation time: 8 days / 27 days

## Classification of Security Vulnerabilities

- Network protocols: TCP/IP, NetBIOS
- Operating systems: Windows, Linux, Unix
- Application services: FTP, POP3, HTTP
- Application software: Databases
- Configuration settings: Password settings, anonymous settings, registry
- Network devices: Routers, firewalls

![](img/56e4826257c2e3f407630825aa58ce2d_140_0.png)

## Classification Rules for Vulnerability Risk Levels

High:
- Attackers can remotely execute arbitrary commands or code.
- Attackers can remotely obtain administrative privileges of application systems.
- Remote denial-of-service attacks.

Medium:
- Attackers can remotely create, modify, or delete files.
- Attackers can obtain sensitive system information, such as usernames and password information.
- Attackers can read arbitrary files and directories.
- Attackers can read specific files and directory contents.
- Issues that may potentially lead to medium-risk vulnerabilities.

Low:
- Attackers can obtain information about certain systems or services, such as operating system type, physical paths, and service version information.
- No known security issues, but may be unnecessary services.

Note: The threat level of a vulnerability can be measured by the prevalence of the affected program. The wider its applicability, the higher the threat.

## Vulnerability Scanners

- A vulnerability scanner is software that performs risk analysis and assessment of the security of networks and hosts. It is a program package that can automatically detect security weaknesses and hidden dangers in remote or local host systems.
- Vulnerability scanning is the inspection of important computer information systems to discover vulnerabilities that can be exploited by hackers. The result of vulnerability scanning is essentially an assessment of system security performance; it indicates which attacks are possible and therefore becomes an important part of a security solution.
- Vulnerability scanning is an important technology in network security defense.

## Vulnerability Scanner Schematic Diagram

![](img/56e4826257c2e3f407630825aa58ce2d_145_0.png)

Scanner server

Console

Agent

Agent

Agent

Agent

Agent

Note: Vulnerability scanners are divided into network-based and host-based types; network-based vulnerability scanners do not include agents.

## Principles, Targets, and Results

Principle: Use simulated attacks to check one by one for known security vulnerabilities that may exist in the target.

Targets: Workstations, servers, switches, database applications, and other objects.

Results: Provide system administrators with thorough and reliable security analysis reports, serving as an important basis for improving the overall level of network security.

## Advantages of Vulnerability Scanners

In the construction of a network security system, security scanning is a tool that is low-cost, effective, fast to take effect, relatively independent of network operation, and simple to install and run. It can greatly reduce the manual labor of security administrators and help maintain the consistency and stability of security policies across the entire network.

## Classification of Vulnerability Scanners

- Network-based vulnerability scanning
- Host-based vulnerability scanning

Note: Their implementation principles are basically the same, but their architectures differ greatly.

## Components of Network Vulnerability Scanning

- Vulnerability database module
- User configuration console module
- Scan engine module
- Result storage and report generation tools

## Basic Principles

Generally speaking, network-based vulnerability scanning tools can be regarded as vulnerability information collection tools. Based on the characteristics of different vulnerabilities, they construct network packets and send them to one or more target machines on the network to determine whether a specific vulnerability exists.

## Implementation Process

1. Determine the scan targets and which vulnerabilities to check according to the settings of the **console**.
2. Send the packets assembled by the **scan engine** to the target machine, receive the returned results, and compare them with the characteristic values in the **vulnerability database**.
3. Generate a scan report using the scan results returned by the **scan engine**.

![](img/56e4826257c2e3f407630825aa58ce2d_152_0.png)

