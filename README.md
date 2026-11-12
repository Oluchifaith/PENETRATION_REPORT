# PENETRATION_REPORT
Reconnaissance,Scanning and Report
PENETRATION TESTING REPORT
FOOTPRINTING & NETWORK SCANNING PHASES
W2-PM-FINAL | CYBERSECURITY |  NETWORKWALKS

Pentester Name
(Cybersecurity Professional)
Nwafor Faith Oluchukwu
Program/Batch
B084-Networkwalks
Date
17 August 2026
Modules completed
W2-PM1 (Multiple Kali Tools)

W2-PM2 (GHBD)

W2-PM4 (Theharvester)

W2-PM5 (Zenmap Scanning)

Client/Target
1. Networkwalks (secured written permission already)
2. My own local LAN Network
Permission secured from client?
Yes
Phases covered

Phase 1: Reconnaissance & Footprinting

Phase 2: Scanning & Network Discovery

Phase 3-5: In Progress


1. Liability Disclaimer
I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

2. Introduction
This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1), the harvester (W2-PM4) and scanning my own local network with Zenmap (W2-PM5). One module covers the footprinting phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network. It is the Week 2 part of my ongoing internship program at Networkwalks.

All commands were run in Kali Linux and the harvester (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.


4. Tools Used
The table below lists each tool used in this report and its purpose.
Tool
Purpose
Kali Linux & Windows
Operating systems used for reconnaissance activities
WHOIS
Find domain registration details (owner, dates, name servers).
whatweb
Fingerprint web technologies (server, CMS, plugins, IP).
nslookup
Resolve the domain name to its IP address using DNS.
curl -I
Read the HTTP response headers of the website.
wafw00f
Detect whether a Web Application Firewall protects the site.
dnsrecon
Enumerate all DNS records (NS, MX, SPF, TXT, SRV).
Zenmap (Nmap GUI)
Scan the local subnet to find live hosts, IPs and MAC addresses.
Windows CMD
Local IP and MAC address identification


5. Activities Performed
4.1 Footprinting & Reconnaissance

I performed reconnaissance against the networkwalks.com domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. Each tool was used to collect a different type of information about the target.
First, I used WHOIS to obtain publicly available domain registration information and identify the domain’s name servers. The results provided information about the domain registration and hosting infrastructure.

<img width="538" height="397" alt="whois" src="https://github.com/user-attachments/assets/498ebfec-f279-4378-a9f6-4395337601de" />


I then used WhatWeb to identify technologies used by the website. The results identified WordPress 7.0.4 and WP Download Manager 3.3.58, along with other information exposed by the website.

<img width="1248" height="253" alt="whatweb" src="https://github.com/user-attachments/assets/cb23d493-9814-44b4-ba8f-3a24b7b0882c" />


Using Nslookup, I resolved the domain name to its IP address. The provided result identified 192.232.216.135.


<img width="238" height="147" alt="nslookup" src="https://github.com/user-attachments/assets/81150e5d-5a9b-49ce-9f67-86e3c930b95a" />


I used Curl with the -I option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint /wp-json/.

<img width="1249" height="251" alt="curl" src="https://github.com/user-attachments/assets/19d1251c-2564-483b-9b7a-4b6d7e0438b8" />


Next, I used Wafw00f to determine whether a Web Application Firewall was protecting the website. The result identified ModSecurity (SpiderLabs).

<img width="623" height="329" alt="wat" src="https://github.com/user-attachments/assets/96308b99-77ef-4707-a53a-5b24b9c6179c" />


Finally, I used DNSRecon to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF/TXT records, service records and DNS software information.
<img width="1085" height="430" alt="dns" src="https://github.com/user-attachments/assets/ca2bd74c-e307-4531-9d8a-b3ed77066257" />


4.1.1 theHARVESTER
theHarvester is a footprinting tool which is used for gathering information of emails, sub-domains,hosts, employee names, open ports and banners from different public sources like search engines,
PGP key servers and SHODAN computer database.
I used theHARVESTER to gather the list of email IDs related to a target organization.

<img width="557" height="460" alt="task1" src="https://github.com/user-attachments/assets/472098d3-aa98-4428-bb41-ac34976f3667" />

<img width="1263" height="640" alt="task2 theharvester" src="https://github.com/user-attachments/assets/eefef7ff-cd6c-4966-a3e5-63d64a3b5194" />


4.2 Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.
I first used the Windows ipconfig command to identify my local IP address and LAN subnet.I then entered the subnet into Zenmap and selected Ping Scan to identify active hosts.

<img width="625" height="532" alt="zenmap" src="https://github.com/user-attachments/assets/cb5b1b45-4964-4547-8749-aaed7407a9d4" />


The example results provided in the practical identified two live hosts:

The example results also included four MAC addresses.
After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.
Note: The actual subnet, number of hosts and addresses should be replaced with the results from my own network when submitting the report.

<img width="503" height="441" alt="png" src="https://github.com/user-attachments/assets/e88e1b6d-d705-4228-a4fb-0ac4a66621f2" />


5. Risk Analysis / Impact
Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.
#
Risk / Finding
Evidence / Observation
Potential Impact
Risk Level
1
Web technology information exposed
WhatWeb identified WordPress and WP Download Manager
Attackers may use exposed technology/version information to identify software requiring further security review /
● Medium
2
Server IP address identifiable
Nslookup resolved the domain to 192.232.216.135
Provides information about the network location of the web service
● Low
3
HTTP technical information exposed
Curl returned HTTP response headers and exposed /wp-json/
May assist technology fingerprinting and further enumeration
● Low
4
WAF technology identifiable
Wafw00f identified ModSecurity (SpiderLabs)
Reveals information about the web application’s security architecture
● Low
5
DNS infrastructure information exposed
DNSRecon identified DNS, mail and service-related records
DNS information can help build a broader infrastructure profile
● Medium
6
Multiple live hosts visible on local network
Zenmap identified four live hosts in the example network
Unknown or unauthorized devices may potentially be present on a network
● Medium


Risk level key:  ● Critical  ● Medium  ● Low
The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.
The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules.
Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.

6. Recommendations
Based on the observations from these activities, I recommend the following security improvements:
Review publicly exposed technology information
Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible.
Keep software updated
CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories.
Review HTTP headers
HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.
Review DNS records regularly
DNS records should be checked periodically to ensure that only required information and services are publicly exposed.
Properly configure and monitor the WAF
Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.
Perform regular internal network discovery
Organizations should periodically scan their own networks to identify active devices.
Investigate unknown devices
Any unexpected device discovered during network scanning should be investigated and verified.
Maintain network documentation
Network topology and device information should be documented and updated regularly.
Perform security testing with authorization
Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

7. Conclusion
During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance and network scanning.
In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain information, WhatWeb can identify web technologies, Nslookup can resolve domain names, Curl can inspect HTTP headers, Wafw00f can identify a WAF, and DNSRecon can provide additional DNS information.
In the network scanning activity, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.
The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.
I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.
Finally, I learned that reconnaissance and scanning must always be performed within an aut






