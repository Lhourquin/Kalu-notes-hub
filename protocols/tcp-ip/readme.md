# TCP-IP for programmers

This is the protocols, the language alows systems to talk to each other.

## Logical vs. Physical

* Logical devices are the specific service - Firewall, Modem, Router, Access Point
  * These were, and can still be dedicated devices, but are generally built into a single device such as SOHO Router that has a Router, Switch, Access Point, Firewall and even VPN built-in.
* Physical Devices are the actual objects you plug into the network.
* Design/ Whiteboard based on Logic
* Build based on Physical

## BEWARE of CACHEING

* Systems "cache" data and store it locally so that they can respond to clients more quickly
* When you make a change the system you are connecting to may still respond with cached data
* Either wait for caches to clear, or force a cache to be "flushed"
* "Replication" times are how long it takes for changes to be copied to all relevant systems

## What is a Protocol

* Language for computer to talk with each other
* Network Protocols, Storage Protocols, Communication Protocols
* TCP/IP
* FTP
* SIP
* RTMP
* iSCSI

## TCP/IP v6 ???

* Tomorrow... Is always a day away...
* We'll run out of v4 addresses the day after tomorrow...
* "legacy" systems have a nasty habit of not dying properly...

## Ethernet Standard

* Star typology (better than rings and bus typology)
* RJ45 connectors
* MAC addresses (unique identifier of a device)
* CSMA/CD  Collision Domains (carrier sense multiple access, colision detection: principe-> ***Listen before talking***)

## MAC address ?

* Universally Unique identifier
* First Part is the Vendor ID, Second Part is the Serial number
* Connection has a MAC addresses
* REST API to find info based on MAC addresses  
  * <https://www.macvendorlookup.com/api>

## Layer 2 Data Link Layer

* Cross over cables (connect two computer together)
* Hubs (to connect multiple computer but it can cause a Broadcast storm, hubs boradcast incoming traffic on all ports)
* Bridges (allows to divide segment to avoid Collision (old ways))
* Switches (they manage the traffic by the MAC address, switch they know particular MAC address is at this particular ports, MAC address table)
  * MAC Address table (all of different MAC address here)
  * Back plane (is the communication for all of these port together)
  * Speed per port (capacity of a switch)
* Broadcast Storms

## Layer 3 Networking

* Connecting Multiple Networks together
* LAN, WAN, CAN, MAN, Internet
* Routers
* Routable Protocols - TCP/IP v4, TCP/IP v6, IPX/SPX

## TCP/IP v4 - Routable Protocol Suite

* Protocol Suite (multiple protocol inside tcip/ip protocols (ip protocol, tcp protocol, icmp etc), so tcp/ip is not a single protocol)
* TCP - Transmission Protocol (how the two devices actually communicate with each other )
* IP - Addressing Protocol
* ICMP - Ping (never turned off)

## TCP/IP Address and Subnet Mask

* 192.168.1.1, every device connected to a network has an IP address like this that identifies it.
* Subnet Mask like 2555.2555.2555.0 helps define which portion of the IP is the network and which part is the host (the specific device)
* Network part: That identifies the overall Network
* Host part: This identifies a specific device in that network.
* Example: for 192.168.1.15 with a subnet mask 255.255.255.0:
  * The 192.168.1 is the network part
  * The .15 is the host part (the specific device on that network)
* The subnet mask makes sure devices know if they're on the same network and how to route data to the right place.

* Another case and example: 192.168.1.1/24
  * 192.168.1.1 is the IP address like discussed above
  * /24 is called **CIDR** (Classless Inter-Domain Routing) notation. It shows how many bits in the subnet mask are dedicated to the network part of the IP address.
    * In **/24**, the number "24" means that the first 24 bits of the IP address are used for network, and the rest ( 32 - 24 - 8 bits) are used for identifying hosts (devices) in that network.
    * Now to relate it to a subnet mask:
      * /24 is equivalent to the subnet mask 255.255.255.0. this is because the first 24 bits are set to "1" (which makes 255 in decimal), and the last 8 bits are "0" (which makes 0 in decimal).
      * In this case, 192.168.1 is the network part (because of the /24, or 255.255.255.0)
      * The last part (the .1) is the host part, representing a specific device on the network
      * So 192.168.1.1/24 means: Network -> 192.168.1.0, host -> .1 (one of the 254 possible hosts, since 8 bits give us 2^8 = 256 addresse, but two are reserved)
* An IP Address contains the address for the Network part and the Host part
* Subnet Mask divides IP Address into Network and Host addresses
* A, B and C Subnets
* Scribble stuff on whiteboard about octets (bytes?) to impress students...
* Octets Value - 2 for number of hosts
  * Lower number is Subnet, Higher is Broadcast

## Private IP Address Blocks (Non internet routable)

* Private IPv4 addresses
  * The Internet Engineering Task Force (IETF) has directed the Internet Assigned Numbers Authority (IANA) to reserve the following IPv4 address ranges for private networks.

  | RFC 1918 name | IP address range | Number of addresses | Largest CIDR block (subnet mask) | Host ID size | Mask bits | Classful description |
  |---------------|------------------|---------------------|----------------------------------|--------------|-----------|----------------------|
  |24-bit block | 10.0.0.0 0 - 10.255.255.255 | 16 777 216 | 10.0.0.0/8 (255.0.0.0)| 24 bits | 8 bits | single class A network |
  |20-bit block | 172.16.0.0 - 172.31.255.255 | 1 048 576 | 172.16.0.0/12 (255.240.0.0)| 20 bits | 12 bits | 16 contiguous class B networks |
  |16-bit block | 192.168.0.0 - 192.168.255.255 | 65 536 | 192.168.0.0/16 (255.255.0.0)| 16 bits | 16 bits | 256 contiguous class C networks |

* These 3 ranges of addresses are not available in public,
not routable on the internet, menaning that any device using these
IPs can't communicate directly with the internet without
some form of translation (like NAT)

* Reserved, so they will never be assigned by an Internet Service Provider (ISP)
to a public-facing device or server.

Example:

* A web server on the internet will never have an IP like 192.168.1.100
because that's in the private IP range.
It would have a public IP like 203.0.113.5 instead.

## Switch and ARP (Address Resolution Protocol)

* Switches are layer 2 networking
* Switches contain MAC Address Tables
* ARP - Address Resolution Protocol - Resolves MAC address to IP Address
* Example - Run: arp -a (this command that give us the IP addresses and all
the MAC addresses for any communication that this computer has seen,
that's not necessarily all the computers that are on the network,
but all the computers, that this computer has seen.)

## TCP ports

* Port is like a door, an entry point to access to a specific type of service running on the same IP address, standard port exist for specific protocol who run service.
* Each services listen on a specific port number, so that incoming data can be directed to the correct application
* IP address to locate the device, port number to access a specific service on that device
* Ports ensure that multiple services can run on the same IP address without confusion
* By assiging specific ports to different services, the system can direct network traffic correctly.
* 192.168.1.1:8080
* Every Protocol uses a TCP Port.
* These are generally preconfigured, but can be manually set.
* SMTP - 25
* HTTP - 80
* HTTPS - 443
* FTP - 20
* SSH - 22

> [!WARNING]
> Open ports can also be potential entry points for attackers, so it's important to close unnecessary ports or use a firewall to manage access.

## Routers and Default Gateways

* Routers Connect Network Together: router is a device that connect different networks together,
typically your local network (LAN) to the internet (WAN)
* Within local network, devices can communicate directly with each other (using switches and IP addresses),
but when a device needs to send data to different network (like accessing a website on the internet),it needs
the router to handle that communication.

* The Defaults Gateway is the Router a Host communicates with is a computer
cannot be found on the LAN.
* The default gateway essentially the IP address of the router on your local network (LAN) that serves as
the access point to other network, like the internet
* When a computer (or host) on your network tries to communicate with a device or service that isn't on the local network,
it sends the traffic to the **default gateway** (the router), which forwards it to the correct destination.
* Example : In a home network, your computer has an IP address like 192.168.1.10, your router (default gateway) has an IP address like 192.168.1.1.
When your computer tries to access a website (say 8.8.8.8) it doesn't know
how to reach it directly, so it sends the request to the **default gateway** (192.168.1.1),
which forwards the request to the internet.
* The default gateway acts as the **doorway out of your local network** to the broader internet (or other network)
* If the router ( default gateway) is misconfigured or unavailable,
devices on your local network won't be able to communicate with anything
outside the network.

## Modems (short for **modulator-demodulator** )

* Device that converts or translate basically different types of data communication system,
different types of signals used,
into a format that can be understood by our local network,
typically **Ethernet (tcp/ip)** (i.e 5g to ethernet tcp/ip, fiber optic to ethernet tcp/ip etc.).
* **Modulation** Converts digital data from your computer or network into analog signals (or another format)
for transmission over the internet infrastructure (e.g, telephone lines,
fiber optics, cable lines, 5G)
* **Demodulation** Converts incoming analog or other types of signals from the internet into digital data
that your devices can understand.
* Modems Change Network Types
* Cable Modem -> Ethernet
* Fiber Optic Modem -> Ethernet

## NAT (Network Address Translation) and Port Forwarding

* NAT is a technique that allows multiple devices on a private network (with private ip address) to share a single IP address to communicate with the internet
* With NAT, a router translate between private IP addresses (like 192.168.x.x) inside
a local network and the single public IP address assigned to that network by the internet service Provider
(ISP), This allows to an entire home or business network to use just one public IPv4 address to access the internet.
* NAT killed IPv6... Not really, but NAT reducing the need for each device to have its own unique public IP address.
This "stretched" the lifespan of IPv4, postponing the exhaustion problem.
* Numerous Connected Devices can share the same External IP Address.
The NAT Enabled Router will automatically route traffic to appropriate Hosts.
* Port Forwarding forwards inbound TCP Port Traffic to Specific Hosts, like a web servers you want to expose in public, you have to specify your public IP address at specific port refers to your web server at your private ip address at specific port
* BEWARE - Carrier NAT..
* Carrier NAT, CGNAT (Carrier-Grade Network Address Translation) is a techno used by ISP to share a single public address amoung multiple customers.
* Due to the shortage of IPv4 addresses, ISPs use Carrier NAT to assign private IP addresses to customers and translate their traffic to a shared public IP when they access the internet. This is similar to regular NAT but happens at the ISP level, not just within your home network.
  * Your router has a private IP assignerd by the ISP
  * The ISP uses Carrier NAT to translate your private IP (and many other customers private IP)
    to a shared public IP when sending the traffic to the internet
    * Downsides : shared ip issues, Since many users share thje same public IP, things like port forwarding and peer-to-peer application can be problematic
    * traceability : It make  identifying individual users harder because they share one public IP (generally is the case with low cost isp)

## DMZ (Demilitarized zone)

* Section of your network that's exposed to the public internet
* Isolated from your private internal network
* typically used for **public facing servers** (like web, email, FTP servers) to add extra layer of security
* Allows external users to access a sevice (like website) without giving them direct
access to your internal network (where sensitive data are located)
* Partially exposed to the internet
* Internal network protected from external access

## Internet Facing Static IP addresses

* Server is "directly" connected to the internet
* No need for Port Forwarding
* may cost extra money
* May be limited or not available from vendor
  * Many ISP's will sell no, or limited static IP Addresses to customers
