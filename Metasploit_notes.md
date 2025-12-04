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
- We can use help command on its own or for a specific command. For eg. <mark>help set</mark> command on msfconsole.
- <mark>history</mark> command can be used to see commands history.
- msfconsole have tab completion support.
- Msfconsole is managed by context. If we using a module and we set a parameter or command such as <mark>RHOSTS</mark> in it, now we switched to another module then the previous parameter will not automatically set on the new module, we have to set it again for this module.
-  <mark>use exploit/windows/smb/ms17_010_eternalblue</mark> - to use a module in msfconsole.
-  EternalBlue exploit was developed for a vulnerability affecting the SMBv1 server on Windows systems.
-  U.S. National Security Agency (N.S.A.) developed EternalBlue exploit.
- While using a module the prompt changes but it does not enter a folder as we can typically expect in an operating system command line.
- <mark>show option</mark> - to see all options related to the module/exploit we have chosen.
- A Post-exploitation module may only need us to set a SESSION ID.
- <mark>show</mark> command can be used with auxiliary,payload, exploit,etc) to list available modules. Like <mark>show payloads</mark>, <mark>show exploit</mark> for a context like eleternalblue.
- <mark>show</mark> if used direclty from mfsconsole will list all modules avaialbe. *<mark>show all</mark> sometimes.
- <mark>back</mark> - to leave the context or module.
- <mark>info</mark> - to get further info about any module.
- <mark>info exploit/windows/smb/ms17_010_eternalblue</mark> - to get info about a module directly from msfconsole prompt.
- Info will display detailed information on the module such as its author, relevant sources, etc.
- <mark>search</mark> - this command will search the Metasploit framework database for modules relevant to the given search parameter.
- Using CVE numbers, exploit names (eternalblue, heartbleed, etc), or target system one can conduct searches.
- any module returned in s search result with the command use followed by the number at the beginning of the result line, for e.g. <mark>use 0</mark> instead of use auxiliary/admin/smb/ms17_010_command.
- search using keywords such as type and platform. For eg. <mark>search type: auxiliary telnt</mark>.
  
🔴 Working with modules
- <mark>use</mark> - to use a module
- Base on the module one use, additional or different parameters are needed to be set.
- <mark>show options</mark> - command to list the required parameter of current module.
- <mark>set parameter_name value</mark> -> <mark>set RHOSTS 10.233.xx.xx</mark> - This syntax is used to set parameters.
- One may see five different prompts while using Metasploit :-
  * The regular command prompt: Here metasploit commands cannot be used.
  * The msfconsole prompt: msf6 or msf5 or msf is the msfconsole prompt. This prompt is before a context is set, so context-specific commands cannot be used here.
  * A context prompt : After one set a module the msfconsole will show context prompt. After this one can set parameters and use the module.
  * The Meterpreter prompt: Meterpreter is an important payload. If one can see this prompt it means a meterpreter agent was loaded to the target system and it connected back to you. One can use meterpreter specific commands here.
  * A shell on the target system: Once the exploit is completed, you may have access to a command shell on the target system. This is a regular command line, and all commands typed here run on the target system.
- <mark>show options</mark> - command to list all available parameters.
- Some parameters require a value to work and some are pre-populated. One have to check itself and put the required value for your target accordingly.
- <mark>set rhosts 10.10.165.39</mark> - to set RHOSTS parameter to the IP address of target system.
- After setting a parameter, <mark>show options</mark> command to check the value was set correctly.
- Parameters that often used :-
  * RHOSTS :
    + "Remote Host", the IP address of the target system.
    + A single IP address of a network range can be set.
    + This will support the CIDR (Class Inter-Domain Routing) notation (/24, /16, etc.)or a network range (10.10.10.x- 10.10.10.y).
    + One can use a file where targets are listed. One target IP per line.
    + command - <mark>set rhosts file:/home/sama/Downloads/targetfile.txt</mark>.
  * RPORT: "Remote Port", the port on the target system the vulnerable application is running on.
  * PAYLOAD: The payload one will use with the exploit.
  * LHOSTS: "Localhost", the attacking machine (your AttackBox or Kali Linux) IP address.
  * LPORT: "Local Port", the port one will use for the reverse shell to connect back to. This is a port on you attacking machine, and you can set it to any port not used by any other appplication.
  * SESSION: Each connection established to the target system using Metasploit will have ta session ID. One will use this with post-exploitation modules that will connect to the target system using an existing connection.
- One can override any set parameter using the <mar>set</mark> command again with different value.
- <mark>unset</mark> - to clear any set parameter.
- <mark>unset all</mark>- to clear all set paratmeters.
- <mark>setg</mark> - to set values that will be used for all modules. It allows to set values so it can be used by default across different modules.
- <mark>unsetg</mark> - to clear all value globally or set with setg.

- <mark>exploit</mark> or <mark>run</mark> - to launch the module once all parameters are set.
- <mark>exploit -z</mark> - to run the exploit or module and background the session as soon as it opens.
- 
               
