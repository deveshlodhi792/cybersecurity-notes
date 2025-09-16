🔴 Host Discovery using nmap network scanner
Nmap uses multiple ways to specify its targets:
- Using '-' in IP (Internet Protocol) range: To scan all the IP addresses from 192.168.0.1 to 192.168.0.10, we can use command **nmap 192.168.0.1-10**
- Using '/': To scan a subnet just put **nmap 192.168.0.1/24** it would be equivalent to **nmap 192.168.0.0-255** (It will show mac address of the host(device) along with ip address)
- Hostname: We can also scan our target by specifying its hostname (Note: do not scan any random host/website you don't own or have no permission to scan using this command otherwise you can get in legal trouble).

🔴 While learning to use nmap always prefer to run nmap as root or using sudo as it would not limited to fundamental types of scans such as ICMP echo and TCP connect scans and it will not restrict the nmap's abilities with  our account privileges.

🔴 To discover the online hosts on a network use '-sn' option **"nmap -sn 10.201.xx.xx/24"** its like ping scan but it is not limited to only ping.

🔴 Scanning a "Local" Network
- Here the term 'local' refer to the network which we are directly connected to, such as ethernet or wifi network.
- Here we scan a wifi network to which we are directly connected, Our Ip address is 192.168.66.89, and we are scanning 192.168.66.0/24 network.
- We used **"nmap -sn 192.168.66.0/24"** command and its output are shown in the image <img width="1740" height="576" alt="nmap1" src="https://github.com/user-attachments/assets/0173a206-f903-4269-b804-e38f11907b3f" />
- As we are scanning the local network we can also see the MAC addresses of the devices. 
- Along with MAC addresses we have network card vendors information which also beneficial to guess the target device.
- Because the scan was on directly connected network, the nmap sent ARP requests to the devices, and when the devices responded the Nmap lables it with "Host is up".

🔴 Scanning a "Remote" Network
- Here "remote" means that atleast one router is there which separates our system from this network.
- While scanning a remote network we cannot send ARP request to the target devices.
- Here our system has the IP address 192.168.66.89 and it belongs to the 192.168.66.0/24 network.
- We will scan our target network 192.168.11.0/24 where there would be two or more routers (hops) separate our local system from the target hosts (devices).<img width="1788" height="576" alt="nmap2" src="https://github.com/user-attachments/assets/0bfbe559-c808-4ad7-ba56-57cd2dc36099" />
- The Nmap output shows that five hosts are up.

🔴 Nmap offers a list scan with the option "-sL". This scan helps to list out the targets to scan without actually scanning them. For example, **"nmap -SL 192.168.0.1/24"** will list the 256 targets that will be scanned. This option helps confirm the target before running the actual scan.
🔴 "-sn" option only discover the live hosts not the services running on the target host, which usually discover by scanning the ports of the host. The **-sn** option helps to scan the network without causing much noise.

🔴 Port Scanning
- Scanning of ports helps to discover network services listening on the live hosts. Network services means to any process that is listening for incoming connections on a TCP or UDP port.
- Common network services include web servers, which usually listen on TCP ports 80 and 443, and DNS servers, which typically listen on UDP (and TCP) port 53.
- TCP and UDP each have 65,535 ports.
🔴 Connect Scan
- The connect scan can be triggered using "-sT" option. It tries to complete the TCP - three-way handshake with every target TCP port.
- If the TCP port turns out to be open and Nmap connects successfully, Nmap will close the established connection.
- In the screenshot below, our scanning machine has the IP address 192.168.124.148 and the target system has TCP port 22 open and port 23 closed. In the part marked with 1, you can see how the TCP three-way handshake was completed and later torn down with a TCP RST-ACK packet by Nmap. The part marked with 2 shows a connection attempt to a closed port, and the target system responded with a TCP RST-ACK packet. <img width="951" height="567" alt="nmap3" src="https://github.com/user-attachments/assets/e512f384-8c0b-4aa4-87b5-b7f53ae84120" />

🔴 SYN Scan (Stealth)
- **-sS**: flag is used to do SYN Scan.
- The SYN scan does not complete a the TCP three-way handshake like connect scan, the SYN Scan only executes the first step: it sends only TcP SYN packet.
- Due to fewer logs entry it is considered a relatively stealthy scan.
  
🔴 Scanning UDP Ports
- **-sU**: option is used to scan for UDP services.
- UDP does not require establishing a connection and closing of connection afterwards.
- UDP is suitable for real-time communication, such as live broadcasts, video call, voice call, gaming, streaming, etc.
- UDP traffic is different from TCP as it is simpler than TCP.

🔴 Limiting the Target Ports
- Nmap scans the most common 1000 ports by default.
- -F is for Fast mode, it scans 100 most common ports. For example "nmap -F 198.160.xx.xx"
- -p[range] : to scan ports by specifying the range of ports. For example, "nmap -p10-1024 198.168.xx.xx".
- "nmap -p-25 198.168.xx.xx" : scan all ports between 1-25.
- "nmap -p- 198.168.xx.xx" : scan all the ports and it is equivalent to p1-65535.  

🔴 More Options
- "-O" : Guess the Operating System of the target host. For e.g. "nmap -sS -O 192.168.124.211"
- "-sV": Scans the open ports and detect the version of service running i.e. the version of SSH. The command would be "nmap -sS -sV 192.168.124.211".
- "-A" : To detect OS, version scanning, traceroute and other things. Very much noisy scan.
- "-Pn" : To Force Scan the Ports of Hosts showing down.

🔴 Scan Speed and Timing
- To control scan speed Nmap gives six timing templates - paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), and insance (5).
- Timing template can be used by its name or number. For example, "nmap -sS -T0 (or -T 0) or -T paranoid 192.168.121.xx" to opt for the slowest timing.
- To control parallel probes on TCP and UDP Ports"--min-parallelism *numprobes*" and "--max-parallelism *numprobes*".
- To control the rate of packets send per second then use "--min-rate *number*" and "--max-rate *number*".
- to limit the maximum time you are willing to wait then use "--host-timeout *time*" option.

🔴 Controlling the output
- "-v" (verbosity) to get more output and updates about what's happening while scanning is in progress. It displays the real-time information about the scan progress.
- To increase verbosity level : -vv, -vvv, or -vvvv. Another way is by specify the level like -v2, -v3, -v4, -vn. One can also increase the verbosity level by presssing "v" after the scan alreaday started.
- "-d" for debugging-level output, it is higher verbosity level. To increase the level we can specify the level no. like -d2, -d3, and so on, the higher it can go to "-d9" but the output would be of thousands of lines.

To Save Scan Report
- "-oN *filename*" - Normal output
- "-oX *filename*" - XML output
- "-oG *filename*" - grep-able output (useful for grep and awk)
- "-oA *filename*" - Output in all major formats
