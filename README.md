# PENETRATION_REPORT

PENETRATION TESTING REPORT

FOOTPRINTING & NETWORK SCANNING PHASES
###Reconnaissance/Footprinting is  the information-gathering phase of cybersecurity reconnaissance. It involves collecting details about a target before attempting further security testing.

### Network scanning is the process of examining a network to identify active hosts, open ports, running services, and potential weaknesses


# Modules completed
W2-PM1 (Multiple Kali Tools)

W2-PM2 (GHBD)

W2-PM4 (Theharvester)

W2-PM5 (Zenmap Scanning)

##Client/Target
1. Networkwalks (secured written permission already)
2. My own local LAN Network


##Phases covered

Phase 1: Reconnaissance & Footprinting

Phase 2: Scanning & Network Discovery

Phase 3-5: In Progress


## Introduction
This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1), the harvester (W2-PM4) and scanning my own local network with Zenmap (W2-PM5). One module covers the footprinting phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network. It is the Week 2 part of my ongoing internship program at Networkwalks.

All commands were run in Kali Linux and the harvester (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.


## Tools Used
The tools used in this report and its purpose.
Tool: Kali Linux & Windows
Purpose Operating systems used for reconnaissance activities
TOOl: WHOIS
Purpose: Find domain registration details (owner, dates, name servers).
Tool: whatweb
Purpose: Fingerprint web technologies (server, CMS, plugins, IP).
Tool: nslookup
Purpose: Resolve the domain name to its IP address using DNS.
Tool: curl -I
Purpose: Read the HTTP response headers of the website.
Tool: wafw00f
Purpose:Detect whether a Web Application Firewall protects the site.
Tool: dnsrecon
Purpose:Enumerate all DNS records (NS, MX, SPF, TXT, SRV).
Tool: Zenmap (Nmap GUI)
Purpose:Scan the local subnet to find live hosts, IPs and MAC addresses.
Tool: Windows CMD
Purpose:Local IP and MAC address identification


## Activities Performed

#Footprinting & Reconnaissance

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


## theHARVESTER
theHARVESTER is a footprinting tool which is used for gathering information of emails, sub-domains,hosts, employee names, open ports and banners from different public sources like search engines,
PGP key servers and SHODAN computer database.
I used theHARVESTER to gather the list of email IDs related to a target organization.

<img width="557" height="460" alt="task1" src="https://github.com/user-attachments/assets/472098d3-aa98-4428-bb41-ac34976f3667" />

<img width="1263" height="640" alt="task2 theharvester" src="https://github.com/user-attachments/assets/eefef7ff-cd6c-4966-a3e5-63d64a3b5194" />


## Network Scanning with Zenmap
For the second activity, I used Zenmap to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.
I first used the Windows ipconfig command to identify my local IP address and LAN subnet.I then entered the subnet into Zenmap and selected Ping Scan to identify active hosts.

<img width="625" height="532" alt="zenmap" src="https://github.com/user-attachments/assets/cb5b1b45-4964-4547-8749-aaed7407a9d4" />


The example results provided in the practical identified two live hosts:

The example results also included One MAC addresses.
After completing the scan, I opened the Topology section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.
Note: The actual subnet, number of hosts and addresses should be replaced with the results from my own network when submitting the report.

<img width="503" height="441" alt="png" src="https://github.com/user-attachments/assets/e88e1b6d-d705-4228-a4fb-0ac4a66621f2" />



## I learned how to:

 - Use WHOIS to obtain domain registration information.

- Use NSLookup and DNSRecon to investigate DNS records and domain infrastructure.

- Use WhatWeb to identify technologies used by a website.

- Use cURL to examine HTTP response headers.

- Use Wafw00f to identify the presence of a Web Application Firewall.

- Use theHarvester to collect publicly available reconnaissance information.

- Use Zenmap/Nmap to identify live hosts and network information.

- Use Windows CMD to identify local IP and MAC addresses.

- Understand the difference between passive and active reconnaissance.

- Document reconnaissance findings in a structured manner for cybersecurity assessment.

Overall, the project improved my understanding of information gathering, network enumeration, and the importance of identifying exposed information and services as part of a security assessment.
# 🧰Report 
The report included as a file.

# 🔐 Security and Ethical Use
This project is basicly for educational Purposes only

# 👤 Author
- Nwafor Faith Oluchukwu
- Cybersecurity Intern B084
- LinkedIn:www.linkedin.com/in/nwaforfaith

# 📌 Project Information
Program Name: Cybersecurity at Networkwalks | Week: 02 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub






