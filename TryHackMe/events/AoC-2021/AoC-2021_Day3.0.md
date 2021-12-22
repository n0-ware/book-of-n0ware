# TryHackMe - Advent of Cyber 2021 - Day 3
## Christmas Blackout
> Edward Hartmann
> December 22, 2021

Refs/Links:
- [Advent of Cyber 2021 TOC](_AoC-2021_TOC.md)  
-  Tags[^1]
-  Flag[^2]

## Walkthrough
We are given a website vulnerable to enumeration to attempt directory busting and authentication brute forcing. 

![Landing Page](AoC-2021_Photos/13.0%20AoC-Day-3_12-22-21-Landing-Page.png)

The first thing we are going to do is attempt to enumerate hidden directories to [discover hidden content](../../../knowledge-base/concepts/web/content_discovery.md). Using [dirbuster](../../../tools/dirbuster.md) and [Seclists](../../../tools/sec_lists.md) is our attack path. 

```
dirb http://10.10.150.97 /usr/share/wordlists/seclists
```
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>

[^1]: #authentication #brokenaccesscontrol #insecuredesign #contentdiscovery #webapp 
[^2]: 