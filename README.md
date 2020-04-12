# 42_netwhat
This is the 42 net gateway project, which leads you to learn some basic knowledge about the internet.  <br>
Because there are tons of courses and tutorials explained how the internet works, so on the following question I will try to cut straight to the answer, saving my words on explain basis.<br>
Recommend courses: [Sunny classroom](https://youtu.be/vcArZIAmnYQ)<br>
 
1. What is an IP address:<br>
   IP(Internet Protocol) address is a set of number which has been assign to the device when it connects to the internet, it identifies the location of the device just like the physical address in your home. <br>
   There's two standard format for IP address:<br>
   1. IPv4: support 32 bits long address, looks like `` 212.78.1.25``.<br>
 
   2. IPv6: 128 bits long address, like ``3ffe:1893:3452:4:345:f345:f345:42fc``<br>
 
   [How Do IP Addresses Work?](https://www.howtogeek.com/341307/how-do-ip-addresses-work/)<br>
   [IP Addressing and Subnetting for New Users](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html#anc7) (From Cisco, more technical detail)<br>
 
2. What is a Netmask:<br>
   An IPv4 address consists of two parts, Network ID and Host ID. <br>
   **Network ID:** Specific network location<br>
   **Host ID:** Specific device<br>
   Again, we bring the physical address as an example. The network ID is like street name and host ID is like house number. ie 1234 Ardenwood street.
   ```
   192.168.1        .255
   Network ID      Host ID
   ```
   Netmask is a 32-bit number used to divide IP to the network ID and host ID. (Mask in CS usually means a bitwise number works like a "filter" to filter out the number you assign)
   ```
   IP address:     192.168.1.255
   Netmask:        255.255.255.0 -> 11111111.11111111.11111111.00000000
   ```
   Meaning the last 8 bits in IP address is "Host ID", and the first 24 bits are "Network ID". It can be expressed as Classless Inter-Domain Routing (CIDR) notation:
   ```
   192.168.1.255/24
   ```
 
3. What is the subnet of an IP with Netmask<br>
   Subnetting allow you to connect multiple devices under same network ID. The number of host in each subnet mask shown as below chart(Origin: [subnetting is simple](https://youtu.be/ecCuyq-Wprc)): <br>
   <img src="https://github.com/pootitan/42_netwhat/blob/master/subnetting_table.png" height="75%" width="75%"><br>
   For instance, if we want to divide 4 subnets under current network id, each subnet would allow 64 - 2 = 62 host at the same time, minus 2 for 1) sub-network ID. 2) broadcast ID<br>
   <img src="https://github.com/pootitan/42_netwhat/blob/master/subnet_4.png" height="75%" width="75%"><br>
 
4. What is the broadcast address of a subnet:<br>
   A broadcast address is an IP address that is used to target all systems on a specific subnet network instead of single hosts. From the previous question, we know how to calculate the broadcast ID for each subnet.
 
5. What are the different ways to represent an IP address with the Netmask
   Regular:<br>
   ```
   IP address:     192.168.1.255
   Netmask:        255.255.255.0
   ```
   CIDR notation:
   ```
   192.168.1.255/24
   ```
  
6. What are the differences between public and private IPs<br>
   **public IP:** A globally unique IP which assigned to a device(mostly router) to connect the outer net. In the home network scenario, it has most likely been provided by the Internet Service Provider(ISP)<br>
   **private IP:** An address allocate and subnetting from the public IP device. Like the computer, tablet and smartphone are most likely connect to private IP.<br>
 
7. What is a class of IP addresses<br>
   There's 5 types of classes of IP address, from A to E. A to C are used for host address, D and E is for other purpose.<br>
   The difference between class A to C is the protion of mask<br>
   ```
   Class A: 255.0.0.0
   Class B: 255.255.0.0
   Class C: 255.255.255.0
   ```
   <img src="https://www.cisco.com/c/dam/en/us/support/docs/ip/routing-information-protocol-rip/13788-3-00.gif" height="75%" width="75%"><br>
 
   The system of IP address classes was developed for the purpose of Internet IP addresses assignment. The classes created were based on the network size. For example, for the small number of networks with a very large number of hosts, Class A was created. Class C was created for numerous networks with a small number of hosts. <br>
 
8. What is TCP<br>
   TCP stands for Transmission control protocol, which is a standard that defines how to establish and maintain a network conversation. TCP makes sure the data can deliver correctly between application through IP network by the [Three-way handshake.](https://youtu.be/xMtP5ZB3wSk) TCP also in charge packet reassemble and error checking by the "header" in each packet.
 
9. What is UDP<br>
   User Datagram Protocol (UDP) is another common internet protocol. Unlike TCP, UCP doesn't guarantee for delivering, it's unreliable yet lighter to transmit. UDP is suitable for purposes where error checking and correction are critical, the time-sensitive applications may prefer UDP than TCP, ie. real-time stream. [TCP vs. UDP](https://youtu.be/SLY4Ud53UGs)<br>
 
10. What are the network layers<br>
   In computer science, the concept of network layers is a framework that helps to understand complex network interactions. There are two models that are widely referenced today: OSI and TCP/IP. <br>
 
11. What is the OSI model<br>
   The OSI (Open Systems Interconnection) model was developed by the International Organization for Standardization. There are 7 layers:
   ```
   Physical (e.g. cable, RJ45)
   Data Link (e.g. MAC, switches)
   Network (e.g. IP, routers)
   Transport (e.g. TCP, UDP, port numbers)
   Session (e.g. Syn/Ack)
   Presentation (e.g. encryption, ASCII, PNG, MIDI)
   Application (e.g. SNMP, HTTP, FTP)
   ```
   The TCP/IP model is a more concise framework, with only 4 layers:
   ```
   Network Access (or Link)
   Internet
   Transport (or Host-to-Host)
   Application (or Process)
   ```
   [The Network Layers Explained](https://www.plixer.com/blog/network-layers-explained/)<br>
 
12. What are a DHCP server and the DHCP protocol<br>
   A DHCP (Dynamic Host Configuration Protocol) Server is a network server that automatically provides and assigns IP addresses, default gateways and other network parameters to client devices. When a device tries to connect to the internet, first it needs to ask for a public IP address. Generally, it takes 4 steps to ask an IP address from DHCP server:<br>
   	1. DHCPDiscover: Client sends a broadcast message by UDP to any DHCP servers nearby.<br>
   	2. DHCPOffer: If a DHCP server heard the broadcast, it would respond an offer to client to said that it has available IP addresses.<br>
   	3. DHCPRequest: Client takes the offer and responds a lease request to DHCP server for an IP address.<br>
   	4. DHCPAck: DHCP server sends an IP address to the client, the IP address has set an expire date, client need to send renew request before expire.<br>
 
13. What are a DNS server and the DNS protocol<br>
   Devices connect to each other by IP address, but it's difficult for human to remember numbers like it, so DNS (Domain Name System) server help resolve a domain name address to an IP address for device to read.<br>
   Because the browser could not understand human languages, when we type the domain name onto the browser, the client device will try to find the IP address for the domain name through several DNS servers. <br>
   <img src="https://d1.awsstatic.com/Route53/how-route-53-routes-traffic.8d313c7da075c3c7303aaef32e89b5d0b7885e7c.png" height="75%" width="75%"><br>
   [What is DNS](https://aws.amazon.com/tw/route53/what-is-dns/)<br>
 
14. What are the rules to make 2 devices communicate using IP addresses<br>
   Transmission Control Protocol (TCP)<br>
   Internet Protocol (IP)<br>
   User Datagram Protocol (UDP)<br>
   Post office Protocol (POP)<br>
   Simple mail transport Protocol (SMTP)<br>
   File Transfer Protocol (FTP)<br>
   Hyper Text Transfer Protocol (HTTP)<br>
   Hyper Text Transfer Protocol Secure (HTTPS)<br>
   Telnet<br>
   Gopher<br>
   [Types of network protocol and their uses](https://www.w3schools.in/types-of-network-protocols-and-their-uses/)
 
15. How does routing work with IP<br>
   It is a network that routes packets from a source computer to a destination computer. The Internet is made up of a massive network of specialized computers called routers. Each router’s job is to know how to move packets along from their source to their destination. A packet will have moved through multiple routers during its journey.<br>
   When a packet moves from one router to the next, it’s called a hop. You can use the command line-tool ``traceroute`` to see the list of hops packets take between you and a host. <br>
   [How Does The Internet Work?](https://medium.com/@User3141592/how-does-the-internet-work-edc2e22e7eb8)
16. What is a default gateway for routing<br>
   A default gateway is an entire router connects a local network between the public network. The default gateway in a home network, for example, understands specific routes that must be taken to move internet requests from a computer out of the network and onto the next piece of equipment that can understand what needs to be done. For more detail, check out
   [NAT (Network Address Protocol) - SNAT, DNAT, PAT & Port Forwarding](https://www.youtube.com/watch?v=wg8Hosr20yw)<br>
17. What is a port from an IP point of view and what is it used for when connecting to another device<br>
   On a TCP/IP network, every device must have an IP address. The IP address identifies the device e.g. computer.<br>
   However, an IP address alone is not sufficient for running network applications, as a computer can run multiple applications and/or services. Just as the IP address identifies the computer, The network port identifies the application or service running on the computer.<br>
   [TCP/IP Ports and Sockets Explained](http://www.steves-internet-guide.com/tcpip-ports-sockets/)
 

