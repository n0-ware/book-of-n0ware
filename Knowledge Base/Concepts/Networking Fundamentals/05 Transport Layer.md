# Transport Layer
###### Tags[^1]
- TCP and UDP
- Routes messages across systems using IP addressing
- Responsible for arrival in the right order and on time
- Compare and contrast TCP/UDP
## TCP
- Most common protocol at this layer
- Stateful, connection-oriented
- Two-way communication using a [Session](../Web/Sessions.md) established using a 3-way handshake
	- SYN, SYN-ACK, ACK
	- Session and reliability established
- TCP requires a port as well between 0 and 65535
	- Note well-known and ephemeral

## UDP
- Stateless, connectionless
- Send and forget style. Assumes data will reach target
- Only good for when guarantee of delivery is not paramount
- TCP = Phone call, UDP = Snail Mail


#networking #fundamental 