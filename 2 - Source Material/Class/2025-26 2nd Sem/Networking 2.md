
2026-08-10  19:53

Tags: [[School]] [[Coding]]

---
# Networking 2  |  2025-26


## Rules and Regulations

- Write happy day (e.g happy wednesday) in online chats after joining
- AI Policy
	- Should not be more than 20%
	- If you are caught using AI to answer tests, OSA
	- Declare in reference section what AI was used and to what extent
	- Double check that the reference links are real
	- Include an "AI Use Statement" in the file or as a separate file in the submission
	- Copyleaks, Turnitin - official tool for detection
- Type "recitation" in chat every time you recite
- Consultation: Wednesday 


Net2 possible group members
- Kirk
- Gab
- Vincent
- Richbert
- Von
- Henson

---

# 1st Semester

## Prelim


**Assignment**
- Short presentation of final project from networking 1 on monday

**Learnings**
- Cannot distribute 127 because it is reserved for loopback; used to check if your computer is working or not


**Lab Activity 1 - Class C**

Scenario: 
Given an IP Address 206.207.208.0. Your client (QMRV Company) has Four (4) Offices (subnet) located in Four (4) different cities (Makati City, Manila  City, Quezon City, Pasay City) with 25 computers or host/subnet. Please check if the figures are possible for subnetting?

![[Pasted image 20260810085316.png]]

There are 4 subnets in the scenario, so the borrowed bits should be greater than 4

1+2=3 ; 3<4 not enough
1+2+4=7 ; 7>4 enough
so 3 bits will be borrowed

since 3 bits are borrowed, we subtract the borrowed bits from the total bits:
255-7 = 248

so the subnet mask is **255.255.255.248** or **/29**

/29 is derived from subtracting 32 (total bits in one IP address) to the borrowed bits (3 in this scenario), which is equal to 29 (32-3)

Now the usable subnets and usable hosts are solvable

Usable subnets: 2^3 - 2  =  8-2  =  **6 subnets**
The 3 is from the borrowed bits

Usable hosts: 2^5 - 2  =  32-2  =  **30 hosts per subnet**
The 5 is from the remaining bits

**Requirements:**
Subnets: 4
Hosts: 25

The calculation is more than enough for the requirement, so it fits.

| Subnet No. | Network Address | Hosts | Broadcast Address | Usable |
| ---------- | --------------- | ----- | ----------------- | ------ |
| 0          | 206.207.208.0   |       |                   |        |


### 8/24/26

Commands:
`ping 127.0.0.1`
- loopback/localhost
- tests if your computer's internal network software and TCP/IP stack work right
`hostname`
`ipconfig` or `ifconfig`
`ipconfig /all` or `ifconfig -a`

TLDs (top level domains)
- .com .edu .mil .org

IANA
ISO
IEEE

RA 10173 
- Data Privacy Act of 2012
- protects the fundamental human right to privacy and communication while ensuring that organizations handle personal data properly
RA 10175 
- Cybercrime Prevention Act of 2012
- defines and penalizes cybercrimes such as hacking, data interference, identity theft, cybersex, child pornography, and cyberlibel to secure the country's digital environment


#### Assignment

- Notebook
- CAT 5e or CAT6
- RJ45 (passthrough/normal) as many as you want
- Check all networking/cybersec related RA
- add ipconfig results to notebook




---

## Midterm


### Date - Topic

#### Subtopic



---

## Finals


### Date - Topic

#### Subtopic

