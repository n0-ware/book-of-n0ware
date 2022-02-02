# Link Layer
###### Tags[^1]
- Network collisions happen when yo are dealing with a physical-only connection, such as a bus in ring topology
	- A collision is when two packets are transmitted at the same time
- Link layer reduces collisions
- Ethernet is the primary link-layer protocol
	- Allows for logical boundaries between physically connected devices
	- Switches and bridges form the boundaries
- Devices such as switches allow us to segment networks into "Broadcast Domains" so that collisions are reduced, and switches can record the MAC addresses of devices so that data-transfer between segmented networks is possible
- MAC address allow any device to reach another device as long as it knows the devices MAC address
	- MAC addreses are discovered via broadcast, where a system will ask every other system "Who has this MAC address I want to talk to" and the message will bounce from switch to switch until it finds one that knows where that MAC address lives, and then the information can be routed
	- Address Resolution Protocol handles this
	- A MAC is made up of six sets of hexadecimal numbers or six-bytes
		- AA:BB:CC:DD:EE:FF
		- 12:34:56:78:90:12
		- The first set of six is the OUI, or *Organizationally Unique Identifier*, which helps maintain unique numbers and corresponds to the manufacturer of the devices



#networking #fundamental 