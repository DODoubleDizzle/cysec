
## 0.1 Erkennbare Verhalten
Standardisiert und kategorisiert
https://attack.mitre.org/


# 1 Detection
## 1.1 Anomalieerkennung
- Sensoren/messwerte (logs)
- Referenzwerte 
	- Ein benutzer braucht nicht 100 versuche zum sich einzuloggen
### 1.1.1 Big data
Das problem der anomalieerkennung ist die datenmenge, darum versucht man das zu automaitiseren.
- EDR, NDR, XDR
- Statistische Methoden (KI)
- Automatische Reaktion

### 1.1.2 Management
Applikation die einen Bericht macht und folgendes:
- Datenaggregation
- Analyse
- Alarmierung
- Dashboard (Für uns Menschen)
	- Single pane of glass - bedeutet dass man auf einem Terminal aus alles sehen kann

## 1.2 Schwellenwerte für alarm
- False positive vs false negative


# 2 Response
Wir haben einen Plan, also bleiben wir ruhig und wenden ihn an.
## 2.1 Phases of the intrusion kill chain
### 2.1.1 Reconnaissance
Research, identification and selection of targets
### 2.1.2 Weaponization
Pairing remote access malware with exploit into a deliverable payload
### 2.1.3 Delivery
Transmission of weapon to target (email attachments, websites, usb drives)
### 2.1.4 Exploitation
Once delivered, the weapons code is triggered, exploiting vulnerable applications or systems
### 2.1.5 Installation
The weapon installs a backdoor on a targets system allowing persistent access
### 2.1.6 Command & Control
outside server communicates with the weapons providing hands on keyboard access inside the targets network
### 2.1.7 Actions on objective
The attacker works to achieve the objective of the intrusion, which can include exfiltration or destruction of data, or intrusion of another target.


Ziel: Kill chain unterbrechen, ausschalten
Taktiken: Stören, eingrenzen, täuschen


