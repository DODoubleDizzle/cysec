
> [!abstract] Tldr
> 

# 1 Intellectual Property
## 1.1 Copyright ©
Protects Intellectual Property against unauthorized duplication

8 broad categories:
1. Literary
2. musical
3. dramatic
4. choreographic
5. graphical/sculptural works
6. audiovisual works
7. sound recordings
8. architectural works

### 1.1.1 Software Copyright
Software is defined under literal works. **The ideas behind the code are not protected however.**

### 1.1.2 Establishing Copyright
- The creator of a work has automatic copyright upon creation (exception is "Work for Hire")

### 1.1.3 Formal Copyright
- is protected until 70 years after last author death
- marked with copyright symbol

## 1.2 Trademark
Protects words, slogans and logos which identify a company and its products

### 1.2.1 Establishing Trademarks ™
Trademarks do not need to be registered. ™ indicates that one intends to protect words or slogans as trademarks.

### 1.2.2 Official Trademark ®
Needs to be officially registered with the "Eidgenössische Institut für Geistiges Eigentum (IGE)"
Institute of Intellectual Property

## 1.3 Patents
Patents grant 20 years of exclusive rights to use of an invention.
There are three requirements to file a patent, the innovation must be: 
- new 
- useful 
- not obvious

> [!Warning]
> Patents do not provide adequate protection for software.

## 1.4 Trade Secrets
Since all of the above methods require to disclose details of your work. Therefore, one can choose to keep these details to themselves as a Trade Secret. Trade Secret protection is currently one of the best ways to protect Software.


# 2 The CIA Triad
The primary goals and objectives of security are confidentiality, integrity, and availability.
## 2.1 Confidentiality
Ensures that sensitive information is accessed only by an authorized person and is protected from unauthorized access. Techniques like encryption and access controls are used to protect confidentiality.
Violations of confidentiality include capturing network traffic, stealing password files, social engineering, port scanning, shoulder surfing, eavesdropping, and sniffing.
## 2.2 Integrity
Focuses on maintaining the accuracy and reliability of data. It ensures that information is not altered by unauthorized individuals. Measures such as hash verifications and intrusion detection systems are employed to safeguard integrity.
## 2.3 Availability
Guarantees that information is readily available to authorized users when needed. This involves ensuring a high level of system performance, implementing redundancy and scalability, and maintaining reliable backups to prevent data loss or destruction.


# 3 Threat
## 3.1 STRIDE threat model
### 3.1.1 Spoofing (Authenticity):
- An attack aimed at gaining access to a system using a falsified identity. This involves an attacker pretending to be someone else to gain unauthorized access.
### 3.1.2 Tampering (Integrity):
- Involves unauthorized changes or manipulation of data, either in transit or in storage. Tampering can be used to falsify communications or alter static information, undermining the integrity of the data.
### 3.1.3 Repudiation (Non-repudiation):
- Occurs when a user or attacker denies having performed an action or activity. Repudiation attacks can lead to security violations being blamed on innocent third parties.
### 3.1.4 Information Disclosure (Confidentiality):
- The unauthorized revelation or distribution of private, confidential, or controlled information to external or unauthorized entities, compromising the confidentiality of the data.
### 3.1.5 Denial of Service (DoS) (Availability):
- An attack that attempts to prevent authorized use of a resource. It does not necessarily result in a full interruption but could reduce throughput or introduce latency, hampering the productive use of a resource.
### 3.1.6 Elevation of Privilege (Authorization):
- Occurs when a limited user account is transformed into one with greater privileges, powers, and access, thereby violating authorization policies.

# 4 Destroying Data
- **Erasing**: Remove the pointer to Data, data still exists until the space is needed and it is rewritten
- **Clearing**: Overwriting it with meaningless or unclassified Data
- **Purging**: Combining multiple clearing instances as well as other methods such as degaussing (which means demagnetizing a hard drive).
- **Destruction**: Physical destruction of the hard drive with means such as burning, crushing, shredding or dissolving.

# 5 Data categorization
## 5.1 Types of Data:
### 5.1.1 Personally Identifiable Information (PII):
Information that can identify an individual, such as name, AHV-number (social security), or biometric records.
### 5.1.2 Protected Health Information (PHI):
 Health-related information that can be linked to a specific person, protected under laws like HIPAA (in the United States).
### 5.1.3 Proprietary Data:
Data that gives an organization a competitive edge, including software code, technical plans, internal processes, intellectual property, and trade secrets.
## 5.2 Classification Schemes:
### 5.2.1 Government/Military Classification:
Classified into the following levels based on the potential damage to national security in order of  descending severity:
- top-secret
- secret
- confidential
- sensitive
- unclassified
### 5.2.2 Commercial/Business/Private Sector Classification:
Includes the following levels for the sensitivity and intended circulation of the data in order of  descending severity:
- confidential
- private
- sensitive
- public


# 6 Risk management
## 6.1 Quantitative Risk analysis
- **Exposure Factor (EF)**: percentage of loss
- **Single loss expectancy (SLE)**: the cost associated with a single realized risk
	- Asset Value * exposure factor = **AV** * **EF** = **SLE**
- **Annualized rate of occurrence (ARO)**: expected frequency with which a specific threat or risk will occur within a year
- **Annualized loss expectancy (ALE)**: is the possible yearly cost of all instances of a  threat against an asset -> **SLE** * **ARO**
- **Annualized expectancy with a safeguard**: Reduce **ARO**, goal is to 0, **EF** usually remains the same
- **ALE** before safeguard - **ALE** after implementing the safeguard - annual cost of safeguard (**ACS**) = value of the safeguard to the company

## 6.2 Risk Mitigation
Reducing risk is the implementation of safeguards and countermeasures to eliminate vulnerabilities or block threats

## 6.3 Assigning risk
Is the placement of the cost of loss a risk represents on to another entity or organization

## 6.4 Accepting risk
If the countermeasure cost outweighs the possible cost of a loss due to the risk you would accept the risk

## 6.5 Risk deterrence
Security cameras, auditing, guards, banners, motion detectors, authentication, make known that you will prosecute

## 6.6 Risk avoidance
Use things that will avoid risk in the first place, for example close ports, don't use FTP, use more secure stuff

## 6.7 Residual Risk
Even after all countermeasures are implemented and we are sure there is no risk left there will always be some residual risk that was not yet thought of.

# 7 Privacy
## 7.1 European union general data protection regulation (GDPR)
- Companies need to inform authorities of serious data breaches within 24h
- Individuals will have access to their own data
- People are allowed to require companies to delete their information if it is no longer needed
### 7.1.1 Anonymization
Removes all relevant data so that it is impossible to identify the original subject or person
### 7.1.2 Pseudonymization
As the name implies pseudonymization is the process of replacing some words, phrases or more generically data with a pseudonym so the data cannot be linked back to its original without access to the additional information required to re-identify the data.


