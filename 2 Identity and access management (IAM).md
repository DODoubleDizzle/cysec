# 1 Controlling access to assets
## 1.1 Subject
A subject is an active entity that accesses a passive object to receive information from, or data about, an object
- Subjects can be users, programs, processes, services, computers, or anything else that can access a resource
## 1.2 Object
An object is a passive entity that provides information to active subjects 
- objects include files, databases, computers, programs, processes, services, printers, and storage media
## 1.3 Definition of access control
The goal of access control is to provide access to authorized subjects using:
- Hardware
- Software
- Administrative policy
- Administrative procedure
## 1.4 Access control types
### 1.4.1 Preventive Access Control
A preventive control attempts to stop unwanted activity from occurring.
### 1.4.2 Deterrent Access Control
Blocks the intent of doing something but it can still occur.
Policies, security-awareness training, locks, fences, security badges, guards, mantraps, and security
cameras.
### 1.4.3 Compensating Access Control
A compensation control is deployed to provide various options to other existing controls to aid in enforcement and support of security policies. They can be any controls used in addition to, or in place of, another control
### 1.4.4 Detective Access Control
A detective access control attempts to discover or detect unwanted activity. Detective controls can only detect the activity after it has occured.

### 1.4.5 Directive Access Control
Directs a subject on what to do, example in an airport if you have signs that tell you where to go this is directive, in opposision to in deterrent control you would have security cameras which would make the subject not do something.
### 1.4.6 Recovery Access Control
Recovery Acces Control is the expansion of corrective, allowing full recovery.
### 1.4.7 Corrective Access Control
A corrective control modifies the environment to return systems to normal after an unwanted or unauthorized activity has occurred. Corrective controls attempt to correct any problems that occurred because of a security incident

## 1.5 Categories
### 1.5.1 Physical controls
guards, fences, motion detectors, locked doors, sealed windows, lights, cable protection, laptop locks, badges, swipe cards, guard dogs, video cameras, mantraps, and alarms

### 1.5.2 Technical or logical controls
Hardware or software to manage access
- authentication methods (such as usernames, passwords, smartcards, and biometrics), encryption, access control lists, protocols, firewalls, routers, intrusion detection systems (IDSs)

### 1.5.3 Administrative controls
Policies and procedures defined by an organization’s security policy and other regulations or  requirements. They are sometimes referred to as management controls.
- policies, procedures, hiring practices, background checks, data classifications and labeling, security awareness and training efforts, vacation history, reports and reviews, work supervision, personnel controls, and testing
# 2 The steps of access control
## 2.1 Identification
Identities need to be unique so you can tell subjects apart.
- Username, Email, Badge
## 2.2 Authentication
Provide additional information that corresponds to the identity
- Password, Passphrase, Pin, Fingerprint
>[!warning]
>This needs to be protected

## 2.3 Password
Passwords are typically static. They are the weakest form of authentication
### 2.3.1 Cognitive Password
Mostly legacy but things you know. For example:
- "Whats the name of your first pet?"
- "Whats your favourite animal?"
Better if users can decide their own questions and answers

## 2.4 Passphrase
A passphrase is a string of characters similar to a password but that has unique meaning
to the user. For example: 1P@ssedTheCySecEx@m

## 2.5 Smartcard
Credit card sized badge with integrated circuit chip. It contains information about the user and is used for identification and authentication. Nowadays smartcards include microprocessors and one or more certificates for asymmetric cryptography for further security.

## 2.6 Token
Generates a number every x seconds which the users has to input.
### 2.6.1 Synchronous Dynamic Password Tokens
Hardware tokens that create synchronous dynamic passwords are time-based and
synchronized with an authentication server
- They generate a new password periodically, such as every 30 seconds. This does require the token and the server to have accurate time
### 2.6.2 Asynchronous Dynamic Password Tokens
An asynchronous dynamic password does not use a clock
- The hardware token generates passwords based on an algorithm and an incrementing counter when using an incrementing counter, it creates a dynamic onetime password that stays the same until used for authentication

## 2.7 OneTime Password Generators
Used by most authenticators for 2-factor authentication. They are either Time based or HMAC based.

## 2.8 Authentication factors
In ascending order of how secure they are
### 2.8.1 Something you know
Like Cognitive passwords touched on before
### 2.8.2 Something you have
Like a smartcard
### 2.8.3 Something you are/you do
Biometrics, Voice, Fingerprint, Signature dynamics

### 2.8.4 Multi-Factor: 2
- Card and pin
- Password and authenticator OneTimePassword
### 2.8.5 Multi-Factor: 3
- Badge, finger and then password
- Smartcard, eye, palm
### 2.8.6 Geolocation
Depending on where you are you have access
#### 2.8.6.1 Somewhere you are
The somewhere-you-are factor identifies a subject’s location based on a specific computer, a geographic location identified by an Internet Protocol (IP) address, or a phone number identified by caller ID
#### 2.8.6.2 Somewhere you aren't
Many IAM systems use geolocation technologies to identify suspicious activity • For example, imagine that a user typically logs on with an IP address in Switzerland. If a user is trying to log on from a location in India, it can block the access even if the user has the correct username and password

## 2.9 Authorization
### 2.9.1 From users perspective
Verification of the digital identity for authenticity
### 2.9.2 From system perspective
If the authentication worked you still need to be authorized to perform functions or access specific resources within the controlled environment.

### 2.9.3 Access control models
#### 2.9.3.1 Discretionary Access Control (DAC)
Every object has an owner, and the owner can grant or deny access to any other subjects. Used in NFTS etc.
#### 2.9.3.2 Role Based Access Control
Users are assigned to roles, and roles are assigned privileges. Users in a role will have all privileges assigned to their role(s).
#### 2.9.3.3 Rule Based Access Control
Global rules for all users. Rules in this models are sometimes called filters or restrictions.
#### 2.9.3.4 Attribute Based Access Control
Access to Objects are controlled by rules which can include multiple attributes. Subjects have attributes such as ID, job roles, group memberships, memberships, management level, security clearance etc. Access to an object is only granted if all attributes are acceptable.

#### 2.9.3.5 Mandatory Access Control
Each Object has a security level in an hierarchical structure (e.g. Top Secret, Confidential). Each Subject possesses a certain level in this structure as well. Subjects can only access Objects which are at or below their level in the hierarchy

### 2.9.4 Authorization Mechanisms
A authorization mechanism it the principle with which access to an object is granted or denied to a subject.
#### 2.9.4.1 Implicit Deny
Access to an object is denied unless access is explicitly granted to a subject. Most widespread mechanism currently in use.
#### 2.9.4.2 Constrained Surface
Using interfaces to control what subjects can see or do. Users with full privileges have access to all parts of the application.
#### 2.9.4.3 Access Control Matrix
An access control matrix is a table that includes subjects, objects, and assigned privileges.

||file1.txt|file2.sql|Socket s|
|---|---|---|---|
|Alice|read, write|write|-|
|Bob|-|read|append|
|Process 294|-|-|open, read, write, close|



|     | file1.txt   | file2.sql | Socket s                 |
| --- | ----------- | --------- | ------------------------ |
|     | read, write | write     | -                        |
|     | -           | read      | append                   |
|     | -           | -         | open, read, write, close |


#### 2.9.4.4 Capability Table
Same as Access Control Matrix, but focused on one service. Essentially the same as one collumn on the ACM.
#### 2.9.4.5 Content-Dependent Control
Content-Dependent Control grants subjects access based on the information an Object contains. This is normally done dynamically.
#### 2.9.4.6 Context-Dependent Control
Context-Dependent Control only grants Subject access to an Object after a certain context in the system has been reached with previous actions/events.


## 2.10 Auditing
Audit tables - every action of a user gets tracked.

## 2.11 Accounting
To be held accountable for actions that are mentioned in the auditing.


# 3 Common Access Control Attacks
