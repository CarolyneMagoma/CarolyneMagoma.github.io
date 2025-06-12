---
title: "Simple Office Network"
date: 2025-02-27 00:00:00 +0800
tags: [Networking]
category: [Packet tracer projects]
---

<b>Guide question<b>

Design a network in CISCO packet tracer to connect two departments through the following:
- each department should contain atleast two pcs
- appropriate number of switches and routers should be used in the network.
- using the given network address 192.168.40.0, all interfaces should be configured with appropriate ip addresses, subnet mask and gateways.
- All devices in the network should be connected using appropriate cable.
- Test the connectivity between the two departments -pcs in one department should be able to ping the pcs in other departments.


# Network topology
The network topology consists of two departments, each equipped with two PCs, a switch, and connected through a router. Department A and Department B are organized to ensure efficient communication while maintaining distinct subnets. In Department A, the PCs are connected to a switch, which in turn connects to the router, allowing access to Department B. The router serves as the central point for inter-departmental communication, using two interfaces configured with appropriate IP addresses for each subnet. This design enables seamless connectivity and efficient data transfer between the departments, ensuring that devices can easily communicate with one another while being properly segmented within the network.

![networktopology](assets/images/2025-06-10_12_39_24-cisco_packet_tracer.png)


# Subnetting.
Step 1: Determine the Number of Subnets Needed  

You need 2 subnets.

Step 2: Calculate the New Subnet Mask

The original subnet mask is /24, which means 255.255.255.0.     

To create 2 subnets, we need to borrow bits from the host part of the address. The formula to calculate the number of subnets is 
2 pow 𝑛
 , where 
𝑛
is the number of bits borrowed.
For 2 subnets:

2 pow 1 =2
We need to borrow 1 bit from the host portion.
New Subnet Mask Calculation
Original subnet mask: /24 (or 255.255.255.0)
New subnet mask: /25 (or 255.255.255.128)     

Step 3: Determine the Subnets
With a /25 subnet mask, we can calculate the two subnets:

Subnet 1:
Network Address: 192.168.40.0
Usable IP Range: 192.168.40.1 to 192.168.40.126
Broadcast Address: 192.168.40.127

Subnet 2:
Network Address: 192.168.40.128
Usable IP Range: 192.168.40.129 to 192.168.40.254
Broadcast Address: 192.168.40.255


# Configure the Switches
For both switches, no specific IP configuration is needed unless you require remote management. Just ensure they are connected to the router and PCs. 

# Router configuration
To configure the router for the newly created subnets, first access the router's command-line interface (CLI) and enter privileged EXEC mode. Next, enter global configuration mode. Configure the router's interfaces corresponding to each subnet.

The g0/0 interface is configured with the IP address 192.168.40.1 and a subnet mask of 255.255.255.128. This interface serves as the gateway for devices in Subnet 1 (192.168.40.0/25). By assigning this IP address, the router facilitates communication between devices within this subnet and allows them to access other networks. The subnet mask indicates that the first 25 bits of the address are used for the network portion, leaving sufficient host addresses for devices within this subnet.

![networktopology](assets/images/2025-06-10_12_48_27-Router0.png)

The g0/1 interface is configured with the IP address 192.168.40.129 and the same subnet mask of 255.255.255.128. This interface functions as the gateway for devices in Subnet 2 (192.168.40.128/25). Similar to g0/0, this configuration enables devices in this subnet to communicate with each other and with devices in other networks. The subnet mask here also designates the first 25 bits for the network, providing a structured method for IP addressing and efficient routing between the two subnets.

![networktopology](assets/images/2025-06-10_12_49_58-interface2.png)


# configuring pcs

To configure IP addresses on PCs in Cisco Packet Tracer, First, click on the PC you want to configure and open the Desktop tab. Then, select IP Configuration. In the IP Configuration window, enter the assigned IP address (e.g., 192.168.40.2 for PC1) and the appropriate subnet mask (e.g., 255.255.255.128). Next, input the default gateway (e.g., 192.168.40.1 for PC1). Repeat this process for each PC, using the specified IP addresses and gateways for each department. Once configured, the PCs will be able to communicate within their subnets and with other devices on the network.

![description](assets/images/2025-06-10_20_01_39-pc-a1.png)


![description](assets/images/2025-06-10_20_03_14-pc-a1-2.png)

# Pinging devices
The ping command is used to test the connectivity between devices on a network by sending Internet Control Message Protocol (ICMP) Echo Request packets to the specified IP address—in this case, 192.168.40.130. The output indicates that four packets were sent, with three replies received, resulting in a 25% packet loss, which suggests potential issues in the network path or with the target device. The round trip times for the received packets varied from a minimum of 0 milliseconds to a maximum of 17 milliseconds, with an average of 6 milliseconds, indicating that the device is reachable and responding, but the packet loss may signify intermittent connectivity problems or network congestion. Overall, the ping test provides valuable information about the health and performance of the network connection between the two devices.

![description](assets/images/2025-06-10_12_53_55-PC-A2-PC-B1.png) 

all the ping requests from department A to department B were successful as shown below.


![description](assets/images/2025-06-10_12_58_31-successful_pings.png)







# Conclusion.

This lab demonstrates how to use subnetting, routing, and basic configuration in Cisco Packet Tracer to connect two separate departments effectively. The successful ping tests confirm that the network was set up properly and allows communication between devices across subnets.

This type of setup is foundational for anyone learning about network design, IP addressing, and router configuration.

Happy Networking.

