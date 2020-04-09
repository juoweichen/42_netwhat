# 42_netwhat
This is the 42 net gateway project, which lead you to learn some basis knowledge about internet. Before jump straight into the questiones, here's some nice articles to read: <br>
A guideline: [How Do IP Addresses Work?](https://www.howtogeek.com/341307/how-do-ip-addresses-work/)<br>
From Cisco, more technical: [IP Addressing and Subnetting for New Users](https://www.cisco.com/c/en/us/support/docs/ip/routing-information-protocol-rip/13788-3.html#anc7)<br>
Recommand courses: [Sunny classroom](https://youtu.be/vcArZIAmnYQ)<br>

Becasue there's tons of articles or tutorials explained how internet work, so on the following question I will try to cut straight to the answer, not gonna waste too much writing on explain basis.<br>

**1. What is an IP address:**<br>
	IP(Internet Protocal) address is a sets of number which has been assign to the device when it connect to internet, it identify the location of the device just like the physical address in your home.<br>

**2. What is a Netmask:**<br>
	An IPv4 address consist with two part, Network ID and Host ID. <br>
	**Network ID:** Specific network location<br>
	**Host ID:** Specific device<br>
	Again, we bring physical address as example. The network ID is like street name and host ID is like house number. ie 1234 Ardenwood street.
	```	
	192.168.1		 .255
	Network ID		Host ID
	```
	Netmask is a 32 bit number used to divide ip to network ID and host ID. (Mask in CS usually means a bitwise number works like a "filter" to filter out the number you assign)
	```
	IP address: 	192.168.1.255
	Netmask:		255.255.255.0 -> 11111111.11111111.11111111.00000000
	```
	Meaning the last 8 bits in IP address are "Host ID", and the first 24 bits are "Network ID". It can been expressed as Classless Inter-Domain Routing (CIDR) notation:
	```
	192.168.1.255/24
	```

**3. What is the subnet of an IP with Netmask**<br>
	Subnetting allow you to connect multiple devices under same network ID. The number of host in each subnet mask shown as below chart(Origin: [subnetting is simple](https://youtu.be/ecCuyq-Wprc)): <br>
	<img src="https://github.com/pootitan/42_netwhat/blob/master/subnetting_table.png" height="75%" width="75%"><br>
	For instance, if we want to divide 4 subnets under current network id, each subnet would allow 64 - 2 = 62 host at the same time, minus 2 for 1) sub-network ID. 2) broadcast ID<br>
	<img src="https://github.com/pootitan/42_netwhat/blob/master/subnet_4.png" height="75%" width="75%"><br>

4. What is the broadcast address of a subnet
	A broadcast address is an IP address that is used to target all systems on a specific subnet network instead of single hosts. From the previous question we know how to calculate the broadcast ID for each subnet.

5. What are the different ways to represent an ip address with the Netmask
	Regular:
	```
	IP address: 	192.168.1.255
	Netmask:		255.255.255.0
	```
	CIDR notation:
	```
	192.168.1.255/24
	```
	
6. What are the differences between public and private IPs<br>
	public IP: A globally unique IP which assigned to a device(mostly router) to connect the outer net. In the home network senario, it most likely been provide by Internet service provider(ISP)<br>
	private IP: An address allocate and subnetting from the public ip device. Like the computer, tablet and smartphone are most likely connect to private ip.<br>

7. What is a class of IP addresses<br>

◦ What is TCP
◦ What is UDP
◦ What are the network layers
◦ What is the OSI model
◦ What is a DHCP server and the DHCP protocol
◦ What is a DNS server and the DNS protocol
◦ What are the rules to make 2 devices communicate using IP addresses
◦ How does routing work with IP
◦ What is a default gateway for routing
◦ What is a port from an IP point of view and what is it used for when connecting to another device