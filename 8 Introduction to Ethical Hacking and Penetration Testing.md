# 1 Attack concepts
## 1.1 Hacking
- Exploiting vulnerabilities in systems and/or software to gain unauthorized access 
- Security control compromise
- Produce behaviours outside of system/software's original intent
## 1.2 Ethical hacking 
- Using tools and techniques to validate, audit and report on system/software vulnerabilities 
- Vulnerability existence reporting
# 2 Hacker types
## 2.1 Black Hat 
- Malicious, destructive hacker that usually remains anonymous 
## 2.2 Grey Hat 
- Those possessing Black hat skills who focus on both offense and defence
## 2.3 White Hat 
- Those possessing black hat skills who primarily focus on defence
## 2.4 Script Kiddie 
- Individuals that use tools without understanding what they are doing 
## 2.5 Cyber Terrorist 
- Skilled attacker whose purpose it to further an ideology 
## 2.6 State Sponsored 
- Hackers employed by the government for both offensive and defensive activities
## 2.7 Hacktivist (Woke Cyber Terrorist)
- A computer hacker whose activity is aimed at promoting a social or political cause

# 3 Penetration testing
## 3.1 The Legal Aspects of Penetration Testing
### 3.1.1 Statement of work
- Activities to be performed 
- Pen testing timeline 
- Scope 
- Location of the work 
- Can be a standalone document or part of a Master service agreement (MSA)
### 3.1.2 Non Disclosure agreement
#### 3.1.2.1 Uni-lateral NDAs 
Are  used when an external security firm is hired to test the security of a company's IT systems and agrees not to disclose any found vulnerabilities or sensitive data. This type of NDA protects the client company's confidential information while allowing testers to perform their work without legal concerns about information disclosure.
#### 3.1.2.2 Bi-lateral NDAs 
Are used when both the hiring organization and the security service provider exchange sensitive information, such as security practices or proprietary technologies, which both parties agree to keep confidential.
#### 3.1.2.3 Multi-lateral NDAs
Are used when multiple organizations are involved in a single testing instance.


## 3.2 Penetration testing vs vulnerability scanning

| **Penetration Testing**                                                                                              | **Vulnerability Scanning** |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| Manual process                                                                                                       | Automated process          |
| A professional tries to uncover weaknesses<br>-> find a way to break in your system<br>-> gives an in-depth analysis | Periodic scans             |

>[!info]
>First step of vulnerability scanning must be performed by penetration testers to determine the overall state of your systems


## 3.3 Methods
### 3.3.1 Black-box Testing
The tester has no prior knowledge of the network or system infrastructure. The approach simulates an external hacking or cyber attack scenario to discover vulnerabilities that can be exploited from outside the organization.
### 3.3.2 White-box Testing
Also known as clear-box testing, this method involves full knowledge of the system or network, including source code, infrastructure details, and documentation. Insiders perspective.
### 3.3.3 Gray-box Testing
This method is a blend of black-box and white-box testing. The tester has partial knowledge of the system's internal structures.

# 4 Zero-Day attacks
- Get their name because they have been known publicly for zero days.
- A Zero-Day attack exploits security flaws discovered by hackers that have not been thoroughly addressed by the security community (Zero-Day vulnerabilities)
- The **window of vulnerability** is the delay between the discovery of a new type of malicious code and the issuance of patches and antivirus updates.

# 5 Malicious code
## 5.1 What is malicious code
Malicious code exploits vulnerabilities to deliver harmful payloads. Viruses and Trojans spread through user errors, while worms self-propagate across vulnerable systems.

## 5.2 Sources of malicious code
### 5.2.1 Script-Kiddie
They use ready-to-use software tools to attack systems. Often based in countries with minimal law enforcement, these attackers use malware to steal money and identities globally.

### 5.2.2 Drive-by download
A drive-by download refers to the unintentional download of malicious code to your computer
or mobile device that leaves you open to a cyberattack.
- Unlike many other types of cyberattack, a drive-by doesn't rely on the user to do anything to actively enable the attack 
- Drive-by downloads may happen when visiting a website or clicking a link, or clicking on a pop-up window

### 5.2.3 Advanced persistent threat (APT)
One of the key differences between APT attackers and other malware authors is that these malware developers often have access to zero-day exploits that are not known to software vendors.
- Malware built by APTs is highly targeted, designed to impact only a small number of adversary systems and difficult to defeat.

## 5.3 Viruses
As with biological viruses, computer viruses have two main functions, propagation and destruction
### 5.3.1 Propagation
The propagation function defines how the virus will spread from system to system 
- Viruses use new and innovative methods to escape detection and bypass increasingly sophisticated antivirus technology 
#### 5.3.1.1 Techniques
##### 5.3.1.1.1 master boot record (MBR) infection
- Extremely small (512 Bytes)
- MBR viruses store the majority of their code (the rest) on another portion of the storage media 
	- The system reads the infected MBR 
	- The virus instructs it to read and execute the code stored in this alternate location 
	- The system loads the entire virus into memory
##### 5.3.1.1.2 file infection
- Extend executable files
- Escape detection by using a filename similar to a legitimate operating system file (companion virus)
- Standard file infector viruses are often easily detected 
	- by comparing file characteristics such as size and modification date before and after infection 
	- by comparing hash values
##### 5.3.1.1.3 macro infection
operates by injecting its code into macros attached to the type of popular data files associated with office work, like Microsoft Word, Excel, or PowerPoint files.
- A drastic reduction in the prevalence of macro viruses was achieved by restricting the ability of untrusted macros to run without explicit user permission
>[!info]
>ILOVEYOU virus used this
##### 5.3.1.1.4 service injection
- The Service Injection viruses inject themselves into trusted runtime processes of the operating system, such as **svchost.exe**, **winlogin.exe**, and **explorer.exe** that is also how they avoid detection of antivirus

### 5.3.2 Destructive power
The destructive power is delivered by the virus’s payload by implementing whatever malicious activity the virus writer had in mind 
- This could be anything that negatively impacts the CIA triad of systems or data


### 5.3.3 Platforms Vulnerable to Viruses
- Windows favourite target
- Nothing is safe anymore

### 5.3.4 Virus Types

#### 5.3.4.1 Multipartite Viruses
Multipartite viruses use more than one propagation technique in an attempt to penetrate systems that defend against only one method or the other. 

>[!info] The Marzia virus
>- infects the command.com system file qualifying it as a file infector virus
>- 2 hours after the first infection, it writes malicious code to the system’s master boot record qualifying it as a boot sector virus

#### 5.3.4.2 Stealth Viruses
- Stealth viruses hide themselves and tool antivirus packages into thinking that everything is functioning normally.
	- A stealth boot sector virus might overwrite the system’s MBR with malicious code and modify the operating system’s file access functionality. 
	- When the antivirus package requests a copy of the MBR, the modified operating system code provides it with a clean version of the MBR free of any virus signatures. When the system boots, it reads the infected MBR and loads the virus into memory
#### 5.3.4.3 Polymorphic Viruses
- Polymorphic viruses modify their own code as they travel from system to system.
- This constantly changing signature will render signature-based antivirus packages useless 
	- Antivirus vendors have “cracked the code” of many polymorphism techniques and are able to detect known polymorphic viruses
##### 5.3.4.3.1 Encrypted Viruses
- A type of polymorphic virus that uses cryptographic techniques to avoid detection
- Each infection utilizes a different cryptographic key, causing the main code to appear completely different on each system


#### 5.3.4.4 Logic Bombs
- Logic bombs are malicious code objects that infect a system and lie dormant until they are triggered by the occurrence of one or more conditions such as time, program launch, website logon

>[!info] Michelangelo Virus
>- Infects a system’s MBR 
>- Hides until March 6 (Michelangelo Birthday) 
>- Reformats the hard drives of infected systems and destroying all the data they contained


## 5.4 Trojan Horse
- A Trojan horse is a software program that appears "kind" but carries a malicious payload, just like the horse of troy

>[!info] Rogue antivirus software
>- This software tricks the user into installing it by claiming to be an antivirus package (using a pop-up ad that mimics the look  of a security warning) 
>- Once the user installs the software, it either steals personal information or prompts the user for payment to “update” the rogue antivirus 
>- The “update” simply enables the Trojan!

Difference to Virus:

## 5.5 Keystroke logging
- Logs they keystrokes as the name implies.
- Usually a software but can also be presented as hardware, for example in public places a keyboard.


## 5.6 Ransomware
- Ransomware infects a target machine and then uses encryption technology to encrypt files stored on the system with a key known only to the malware creator.

>[!info] Examples
>Cryptolocker, WannaCry, Petya, Nyetya, BABUK (2021)

## 5.7 Worms
- Self propagation

>[!info] Code Red Worm
>- Seeks many new targets by randomly selected hundreds of IP addresses and then probed those addresses to see whether they were used by hosts running a vulnerable version of IIS 
>- It defaced HTML pages on the local web server, replacing normal content with the following text:
>	- Welcome to http://www.worm.com!HackedByChinese! 
>- It planted a logic bomb that would initiate a denial-of-service attack against the IP address 198.137.240.91, which at that time belonged to the web server hosting the White House’s home page


## 5.8 Spyware
- Spyware monitors your actions and transmits important details to a remote system that spies on your activity

## 5.9 Adware
- Adware uses a variety of techniques to display advertisements on infected computers 
- pop-up ads  
- More advanced versions may monitor your shopping behavior and redirect you to competitor websites 
- Adware often take advantage of third-party plug-ins to web browsers, to spread their malicious content 
- The original plug-in code is supplemented with malicious code that spreads malware, steals information, or performs other unwanted activity


# 6 Antivirus
An Antivirus software is a computer program used to prevent, detect, and remove malware

## 6.1 Detection methods
### 6.1.1 Signature-based
- Most used
- Database containing characteristics of all known viruses
	- Crucial to update
	- Cannot detect newly created viruses
- Scans the storage media periodically
**For example: Windows Defender, McAfee**

### 6.1.2 Heuristic-based
- The antivirus analyse the behaviour of software, looking for the signs of virus activity
	- attempts to elevate privilege level
	- coverage of electronic tracks
	- alteration unrelated or operating system files
- If the software behaves suspiciously in that environment, it is added to blacklists throughout the organization, rapidly updating antivirus signatures
**For example: Malwarebytes**

### 6.1.3 Data integrity
- Data integrity antivirus functionality is designed to alert administrators to unauthorized file modifications
	- Unless a new software, application of an operating system patch has been installed, sudden changes in executable files may be a sign of malware infection
- These systems work by maintaining a database of hash values for all files stored on the system

**For example: Tripwire File Integrity Monitoring (FIM)**


# 7 Application Attacks
## 7.1 Buffer Overflows
Buffer overflow vulnerabilities occur when user input isn't properly validated for size.  
• Input that's too large can overflow a data structure, impacting other data in the computer's memory.  
### 7.1.1 Execute commands on server
• A web form has a field connected to a backend variable that allows 8 characters, but the form processor doesn't verify the input length.  
• The operating system may write data beyond the reserved memory space, corrupting other data. 
• This can be exploited to overwrite system commands, allowing an attacker to execute arbitrary commands on the server.
### 7.1.2 Read data you should not read
Like described in the [[6 TLS#4.1 Heartbleed|Heartbleed]] bug, read additional memory from server buffer.

## 7.2 Time of Check to Time of Use
- The time of check to time of use (TOCTTOU or TOC/TOU) issue is a timing vulnerability that occurs when a program checks access permissions too far in advance of a resource request
- If an operating system builds a comprehensive list of access permissions for a user upon logon and then consults that list throughout the logon session
- If the system administrator revokes a particular permission, that restriction would not be applied to the user until the next time they log on 
- If the user is logged on when the access revocation takes place, they will have access to the resource indefinitely 
- The user simply needs to leave the session open for days, and the new restrictions will never be applied


## 7.3 Backdoors
- undocumented command sequences that allow individuals with knowledge of the back door to bypass normal access restrictions
- Trojan Horses sometimes create backdoors
- Are used by developers for development and debugging to speed up workflow and avoid continuous authentication. Sometimes accidentally left in the production code.

>[!info] Stuxnet had a backdoor


## 7.4 Escalation of Privilege
- Attacker increases his access to admin.
- A rootkit (kit to access to root) increases the access level to root as the name implies.


# 8 Web Applications Attacks
## 8.1 Cross-Site Scripting


# 9 OWASP TOP 10
