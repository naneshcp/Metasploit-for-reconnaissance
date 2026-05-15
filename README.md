# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
<img width="527" height="418" alt="image" src="https://github.com/user-attachments/assets/8857fa4f-aaa4-4182-8914-eb21d84048ae" />

Invoke msfconsole:
## OUTPUT:
<img width="805" height="697" alt="image" src="https://github.com/user-attachments/assets/a5f752f6-40ff-4292-bb8d-25fb54b8d5f2" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="802" height="837" alt="image" src="https://github.com/user-attachments/assets/712139c9-695c-4200-897b-468653d243f8" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="808" height="863" alt="image" src="https://github.com/user-attachments/assets/d0749a90-4d9e-41db-b4cf-1dc6d084c986" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="561" height="294" alt="image" src="https://github.com/user-attachments/assets/72c72954-1577-4686-9d70-8f13ecf925f4" />

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="1920" height="1043" alt="VirtualBox_kali_14_05_2026_21_23_13" src="https://github.com/user-attachments/assets/0b254b21-d4ee-4c00-8e66-51979c2e1990" />

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="831" height="835" alt="image" src="https://github.com/user-attachments/assets/dfb6e0b0-c97f-4ec4-bbad-f073e5761197" />

The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:
<img width="1016" height="713" alt="image" src="https://github.com/user-attachments/assets/4dbf1701-423e-4147-8330-5ff626b9ac8a" />

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="1000" height="421" alt="image" src="https://github.com/user-attachments/assets/5587fe8f-0079-4056-9f19-270de2859249" />
Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:
<img width="1000" height="421" alt="image" src="https://github.com/user-attachments/assets/5587fe8f-0079-4056-9f19-270de2859249" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="830" height="242" alt="image" src="https://github.com/user-attachments/assets/78085038-16fa-46a0-a8af-41c84588f58d" />
Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="869" height="169" alt="image" src="https://github.com/user-attachments/assets/bb4b22c9-e720-4423-9aee-f368f82e9d50" />

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="960" height="337" alt="image" src="https://github.com/user-attachments/assets/0d895d4d-0445-40f3-9f1f-307a54739520" />

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="960" height="337" alt="image" src="https://github.com/user-attachments/assets/b05049af-5f55-45d2-9e7d-8c5c2ed7cc04" />


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
