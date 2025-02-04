# Lecture - Day 5

## Questions
- Why, if NFS points to **finish this quesiton**

## Lecture - Fingerprinter
#evolve/fingerprinter
- Understand what is happening in your scans
- Don't just `-A` every time. 
- Know the difference between `sudo nmap` and `nmap` in how ot defaults to `sS` vs `sT`. 
- Commands change, never know. 

**Great convo about version detection about minute 11**

### Scripting
#nmap/scripting #enumeration/nmap #activeinfogathering 

- #NSE scripts expalnd your enumeration capability
- WIthout script scanning you are limibted to -sV, manually interaction, poking and prodding for low fruit
- *Nmap* says let me help you with this. 
- All located
- Scripts generally organized by the protocol they interact with. 
	- ssl, ssh, etc. 
- Written in LUA, somewhat easy to understand
- Must be stingy and precise with your scripts in a client environemnt. Time is key! Some scripts have srguments, and will require lists, and these must also be made with care. Nothing thoughtless. 
- Try his customized script `nmap -sV --script="(default or safe) and not http" scanme.nmap.org -vvv`

### Scanning
- Always start with a -p- on single targets, no reason not too, not a huge performance loss. 

Headed to #cliente [Cliente](Evolve%20Labs/Cliente.md).

Did not finish, only got to exploit user. Several students got Cliente finished. 