# TCP/IP Model
###### Tags[^1]
## Layers
- The [01 OSI Model](01%20OSI%20Model.md) is a bit outdated, and TCP/IP replaces it to be more relevant ot the internet as we know it.
- Established by DARPA and related to ARPANET and ended with the decomissioning of ARPANET when TCP/IP became widespread
- Resulted from the need to connect network to network
- Rather than strict encapsulation favored in OSI, main goal is to bucket communication into four levels that do not need to reference the layer below. 
	- Allows each layer to have its own defined rules
	- Varying implementations do not effect the layers above or below
- The essential layers replace to applications, machines, inter-network, and within a network 

### Layer 4 - Application Layer
- Combines 5, 6, and 7 in OSI (Session, Presentation, Application)
- Handles the rules that govern how software interacts. 
- HTTP, DHCP, FTP are all protocols that exist at this layer
### Layer 3 - Transport Layer
- Handles how machines communicate together regardless of if they are on the same or different networks. 
- Defines ports (which also has to do with protocols)
- TCP and UDP dominate layer 3
### Layer 2 - Internet Layer
- Handles the communication between networks, and relates to the network layer of the OSI model
- Manages IP Addresses, IP Sec (VPN tunneling), and ICMP, among others
### Layer 1 - Link Layer
- Defines physical communication
- Also relates to the network layer in terms of how data is passed up or received from above
- ARP is a common Layer 1 protocol
- Combines Layers 1 and 2 from OSI



#networking #fundamental 