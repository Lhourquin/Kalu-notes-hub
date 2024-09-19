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
