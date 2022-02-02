# Internet Layer
###### Tags[^1]
## Ethernet
- How devices connect across networks
- Made mostly of IP 
	- an Internet Protocol Address has four octects of 8 bits that compose a 32-bit number
	- Octects are groups of 8
	- That means the total unique values are close to 4.3 billion, 2^32. 
	- Each octet has 256 values, which is 2^8
	- Can also be seen as 2^8^4 = 4.3 billion-ish
	- NAT and PAT come to play in stretching these addresses to the required amount of devices in the world
- Subnet Mask is how devices know which network they belong to
- Opposite an IP address in design, they start with 255 (usually) and define, through binary mathemetaics (binary "and") if two networks belong on the same network
- If a network has a subnet mask of 255.255.0.0, all IP addresses that share the same first two octets can talk to eachother without requiring additional routing, e.g., 192.168.1.2 and 192.168.2.1. If the mask were 255.255.255.0, then we have two different resources. 
- IP addresses can be written in binary, as can subnet masks

```
192.168.1.1   = 11000000.10101000.00000001.00000001
192.168.1.2   = 11000000.10101000.00000001.00000010
255.255.255.0 = 11111111.11111111.11111111.00000000
```

-  To see if two devices are on the same network, first we note the zeros on the subnet mask. Zeros do not effect the devices network. This tells us that the all of the 1's define that particular networks address range, meaning the first three sets of 1's define 192.168.1 as the primary address range, and anything from 192.168.1 to 192.168.255 are all on the same network
	- Where there are 1's on the subnet mask, so also must there be 1's on the IP address. The above example matches
- If we had two IP addresses where 1's don't all match with the subnet mask, then the devices are on two separate networks, as below. 
```
192.168.1.1   = 11000000.10101000.00000001.00000001
192.168.20.1  = 11000000.10101000.00010100.00000001
255.255.255.0 = 11111111.11111111.11111111.00000000
```
The zeros 1's in the third octect do not all match with the 1's in eachother and the 1's in the subnet mask meaning they are on different networks. 

**Better explanation of subnetting required**

#networking #fundamental 