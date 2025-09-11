Host Discovery using nmap network scanner
Nmap uses multiple ways to specify its targets:
- Using '-' in IP (Internet Protocol) range: To scan all the IP addresses from 192.168.0.1 to 192.168.0.10, we can use command **nmap 192.168.0.1-10**
- Using '/': To scan a subnet just put **nmap 192.168.0.1/24** it would be equivalent to **nmap 192.168.0.0-255** (It will show mac address of the host(device) along with ip address)
- Hostname: We can also scan our target by specifying its hostname (Note: do not scan any random host/website you don't own or have no permission to scan using this command otherwise you can get in legal trouble).
  
