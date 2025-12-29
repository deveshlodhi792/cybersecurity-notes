🔴 Introduction to Meterpreter
- Meterpreter is a Metasploit payload that supports the penetration testing process with many valuable components.
- Meterpreter runs on the target system and it act as an agent within a command and control architecture.
- Using Meterpreter one can interact with the target operating system and files and run specialized Meterpreter's commands.
- Meterpreter runs on the target system without installing itself.
- It runs in the memory (RAM) and does not write itself to the disk on the target.
- This feature helps to avoid get detected by antivirus scans.
- Meterpreter is seen as a process when it runs on the target.
- Meterpreter also avoid being detected by network-based IPS (Intrusion Prevention System) and IDS (Intrusion Detection System) solutions.
- It uses encrypted communication with the server where Metasploit runs (our attacking machine) to avoid being detected.
- Meterpreter is recognized by major antivirus software, this feature provides some degree of stealth.
- <mark>meterpreter > getpid</mark>, <mark>getpid</mark> command to get the process ID with which Meterpreter is running on the target.
- Process ID number is used to interact with the process when the need arises (e.g. if it needs to be stopped).
- <mark>meterpreter > ps</mark>, <mark>ps</mark> command to list processes running on the target system, we can see meterpreter's PID is named spoolsv.exe and not by its name.
- Even if we were to go a step further and look at DLLs (Dynamic-Link Libraries) used by the Meterpreter process, we still would not find anything jumping at us (e.g. no meterpreter.dll).
- <mark>C:\Windows\system32>tasklist /m /fi "pid eq 1304"</mark> to see DLL in the meterpreter session on the target system after using shell command.
- Metepreter establish encrypted (TLS) communication channel with the attacker's system.



🔴 Meterpreter Flavors
- Metasploit payloads are divided into two categories; inline (also called single) and staged.
- Staged payloads are sent to the target into two steps.
- An intial part of the payload is sent to target called as stager and then it request the rest of the payload.
- This allows for a smaller initial payload size.
- Meterpreter payloads has a wide range of different versions you can choose from based on your target system.
- <mark>msfvenom --list payloads | grep meterpreter</mark> this command will list the payloads and shows payloads that have associated 'meterpreter'.
- List of Meterpreter versions available:-
  * Android
  * Apple iOS
  * Java
  * Linux
  * OSX
  * PHP
  * Python
  * Windows
 
 -  One's decision on which version of Meterpreter to use will be mostly based on three factors:
  * The target operating system.
  * Components available on the target system.
  * Network connection types you can have with the target system. TCP/HTTPS?



🔴 Meterpreter Commands
- <mark>meterpreter > help</mark>, "help" command on any meterpreter session will list all available commands.
- Every version of Meterpreter will have different command options, so running the <mark>help</mark> command is always a good idea.
- Commands of meterpreter will run on the target without loading any additional script or executable files.
- Meterpreter provides three primary categories of tools;
  * Built-in commands
  * Meterpreter tools
  * Meterpreter scripting
- If we run <mark>help</mark> command, we can see Meterpreter commands are listed under different categories (these categories of commands is of Meterpreter (windows/x64/meterpreter/reverse_tcp) version:
  * Core commands
  * File system commands
  * Networking commands
  * System commands
  * User interface commands
  * Webcam commands
  * Audio output commands
  * Elevate commands
  * Password database commands
  * Timestomp commands
Note: Different Meterpreter versions have different commands categories.

- Below are some of the core commands that most commonly used while using Meterpreter.
  * Core commands
    + background : Backgrounds the current session
    + exit : Terminate the Meterpreter session
    + guid : Get the session GUID (Globally Unique Identifier)
    + help : Displays the help menu
    + info : Displays information about a Post module
    + irb : Opens an interactive Ruby shell on the current session
    + load : Loads one or more Meterpreter extensions
    + migrate : Allows you to migrate Meterpreter to another process
    + run : Executes a Meterpreter script or Post module
    + session : Quicly switch to another session

  * File system commands
    + cd : Will change directory
    + ls : Will list files in the current directory (dir will also work)
    + pwd : Prints the current working directory
    + edit : will allow you to edit a file
    + cat : will show the contents of a file to the screen
    + rm : will delete the specified file
    + search : will searc for files
    + upload : will upload a file or directory
    + download : will download a file or directory
  
  * Networking commands
    + arp : Displays the host ARP (Address Resolution Protocol) cache
    + ifconfig : Displays network interfaces available on the target system
    + netstat : Displays the network connections
    + portfwd : Forwards a local port to a remote service
    + route : Allows you to view and modify the routing table

  * System commands
    + clearev : Clears the event logs
    + execute : Executes a command
    + getpid : Shows the current process identifier
    + getuid : shows the user that Meterpreter is running as
    + kill : Terminates a process
    + pkil : terminates processes by name
    + ps : Lists running processes
    + reboot : reboots the remote computer
    + shell : Drops into a system command shell
    + shutdown : Shuts down the remote computer
    + sysinfo : Gets information about the remote system, such as OS

  * Others Commands
    + idletime : returns the number of seconds the remote user has been idle
    + keyscan_dump : Dumps the keystorke buffer
    + keyscan_start : starts capturing keystrokes
    + keyscan_stop : Stops capturing keystrokes
    + screenshare : Allows you to watch remote user's desktop in real time
    + screenshot : Grabs a screenshot of the interactive desktop
    + record_mic : records audio from the default microphone for X seconds
    + webcam_chat : starts a video chat
    + webcam_list : Lists webcam
    + webcam_snap : Takes snapshot from the specified webcam
    + getsystem : Attempts to elevate your privilege to that of local system
    + hashdump : Dumps the contents of the SAM database

