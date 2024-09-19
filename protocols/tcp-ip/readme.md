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

* Star typology
* RJ45 connectors
* MAC addresses
* CSMA/CD  Collision Domains
