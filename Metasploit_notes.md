🔴 Introduction
- Metasploit Framework is an open-source version of metasploit that works from the command line.
- Metasploit Framework is a set of tools that allow information gathering, scanning, exploitation, exploit development, post-exploitation, and more.
- Primary usage of the Metasploit Framework is penetration testing but it is also useful for vulnerability research and exploit development.
- Main components of the Metasploit Framework
  *  msfconsole : The main command-line interface.
  *  Modules :  Supporting modules such as exploits, scanners, payloads, etc.
  *  Tools : Stand-alone tools that will help vulnerability research, vulnerability assessment, or penetration testing. Some of these tools are msfvenom, pattern_create and pattern_offset.

🔴 Main Components of Metasploit
- msfconsole - command to open metasploit and interact with the metasploit console.
- Modules - small components within the Metasploit Framework. Built to perform a specific task, such as exploiting a vulnerability, scanning a target, or performing a brute-force attack.
- Exploit - A piece of code that uses a vulnerability present on the target system.
- Vulnerability - a desgin, coding or logic flaw that can affect the target system. vulnerability exploitation can result in disclosing of confidential information or allowing the attacker to execute the code on target system.
- Payload - codes that will run on the target system to acheive the results we want like reading of confidential information on the target system.
- exploits find and use vulnerability to execute payloads on the target system to take the information from the system.

- Auxiliary : **root@ip-10-10-135-188:/opt/metasploit-framework/embedded/framework/modules# tree -L 1 auxiliary/
auxiliary/** - to find any kind of supporting module, such as scanners, crawlers and fuzzers.

- Encoders : **root@ip-10-10-135-188:/opt/metasploit-framework/embedded/framework/modules# tree -L 1 encoders/
encoders/**
  * Encoders will help to encode the exploit an payload. It might bypass the signature-based antivirus solution but there is no surety for every try.
  * Signature-based antiviurs and security solutions detect threats by comparing suspicious files to their database of known threats and raise an alert if there is a match.
  * antivirus and security solutions can perform additional checks thats why encoders have limited success rate.

- Evasion : **root@ip-10-10-135-188:/opt/metasploit-framework/embedded/framework/modules# tree -L 2 evasion/
evasion/**
  * Evasion modules are used to evade the antivirus software with more or less sucess.

- Exploits: **root@ip-10-10-135-188:/opt/metasploit-framework/embedded/framework/modules# tree -L 1 exploits/
exploits/
 **

- NOPs : **root@ip-10-10-135-188:/opt/metasploit-framework/embedded/framework/modules# tree -L 1 nops/
nops/**
  * NOPs (No OPeration) are used as a buffer to achieve consistent payload size.
  * As after running NOPs CPU do nothing for one cycle.

- Payloads : **root@ip-10-10-135-188:/opt/metasploit-framework/embedded/framework/modules# tree -L 1 payloads/
payloads/**
  * Exploits will leverage a vulnerability on the target system and payloads help to acheive the desired results and info from the target.
  * Starting the calculator on the target system remotely by launching the calc.exe application is a benign way to show that we can run commands on the target system.
  * Launching calc.exe is a proof of concept to add to the penetration test report.
  * Metasploit have ability to send different payloads that can open shells on the target system to get an interactive connection.
  * Pyaloads have four different directories: adapters, singles, stagers and stages.
  * Adapters - an adapter wraps signle payloads to convert them into different formats. For example, a normal single payload can be wrapped inside a powershell adapter.
  * singles - these are self-contained payloads which do not need to download an additional component to run. for example, add user, launch notepad.exe.
  * Stagers - It helps to set up a connection channel between Metasploit and the target system. First the Stagers are uploaded by "staged payloads" on the target system then they downloa the rest payload (stage).
  * Stages: Stages are the remaining size of payloads downloaded by the stagers.
 
- Single payload - generic/shell_reverse_tcp - have "_" between "shell" and "reverse".
- Staged Payloads - windows/x64/shell/reverse_tcp - have "/" between "shell" and "reverse".

- Post - Post modules will be useful on the final stage of the penetration testing process listed above, post-exploitation.

🔴 Msfconsole
- <mark>msfconsole</mark> - to launch metasploit framework.
- <mark>ls</mark> - to lists the contents of the folder from which Metasploit was launched.
- <mark>ping -c 1 8.8.8.8</mark> - to check connectivity with google's DNS.
- <mark>clear</mark> - to clear terminal screen.
- Metasploit not allow to use regular command line features (eg. does not support output redirection).
- 
- 
