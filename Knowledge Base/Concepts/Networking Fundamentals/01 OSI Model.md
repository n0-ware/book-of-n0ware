# OSI Model
###### Tags[^1]
## Layers
- 7 layers, each referring loosely to the responsibilities, types of data, and actions preformed on the information at each layer
- Each layer relates to either the layer above or layer below, preforming actions on the information required for the next layer to use it. 
	- e.g., the presentation layer either encrypts data for the session layer, or decrypts it for the application layer. 
- A general architecture for the transmission of PDU's, or [Protocol Data Unit](../../Glossary%20(Global).md#Protocol%20Data%20Unit)[^2]. 
- Data is referred to by a specific name at each layer, sometimes repeating
	- Data
	- Segment/Datagram
	- "Encapsulation" is the term used to describe how each layer relies on the format of the information below it, or how it encapsulates the information itself for the layers below it. 
	- As information travels up the model, the various layers of encapsulation are stripped off until just the data we want arrives at the top layer, properly formatted, and ready for the application. 
	- On the way down, data is encapsulated in a way that it can be properly transmitted over the wire to become usable by the target system. 
### Layer 7 - Application - Data
- Human/Software interaction with a network
- Not application in terms of programs themselves
	- Refers to the protocol's by which software receives data
	- E.g., browser gets application layer data and interprets for the user
### Layer 6 - Presentation Layer - Data
- Rearranges data from the lower layer so the application layer can use it
- Encryption, compression, and other transformation happen here
### Layer 5 - Session Layer - Data
- Initiation, maintenance, and termination of the many connections that exist between computers.
- Typically referred to as [Sessions](../Web/Sessions.md)
- The lowest data layer
### Layer 4 - Transport Layer - Segment/Datagram
- Responsible for most of the process by which data gets from point A to B
- Orders (and re-orders) data as needed, handling errors, and informing the related parties that data is either received properly or must be reset
- Handles throttling and windowing
	- Both refer to the rate at which data is transferred, layer 4 informs this speed
- In connection-oriented protocols (stateful), called them *segments*.
- In connection-less protocols (stateless), called them *datagrams*
### Layer 3 - Network Layer - Packets
- Deals with information traveling between two networks
- Routing network tasks such as broadcasts
- Information is called *packets*
### Layer 2 - Data Link Layer - Frame
- Transfer of information from physically connected hosts
- Initiates, monitors, and terminates physically connected machines
- Checks for and corrects errors on layer 1
- Two sub layers
	- Media Access Control (MAC) decides how and when different devices can communicate to avoid cross talk and collisions
	- Logical Link Control (LLC) deals with flow control and error handling
- Information is called a *frame*
### Layer 1 - Physical Layer - Bits
- Raw data transfer "on the wire."
- Deals with the actual physics of the data transfer, such as the transference of digital bits into physical bits in the form of electricity, radio waves, fiber optic transfer via photons, etc. 
- Information called *bits*



[^1]: #networking #fundamental 
[^2]: https://en.wikipedia.org/wiki/Protocol_data_unit