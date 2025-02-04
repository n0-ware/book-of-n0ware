
# Day 3 Lecture 2/26
#activeinfogathering #dns/zonetransfer 

## Questions
- Zone Transfers - Demo shows that **megacorpone.com** has its own nameservers. Checking others, usually they are not named after their own domain. Do companies create their own nameservers often? Big companies? Are they internal or external?
**These days, it is unlikely that companies will be using external DNS servers that are subject to zone transfers


## The Harvester
#theharvester 

Searching for people that work at **Evolve Security** on LinkedIn

```Bash
(n0_ware㉿hartbox)-[~]$ theHarvester -d evolvesecurity.com -b linkedin

*******************************************************************
*  _   _                                            _             *
* | |_| |__   ___    /\  /\__ _ _ ____   _____  ___| |_ ___ _ __  *
* | __|  _ \ / _ \  / /_/ / _` | '__\ \ / / _ \/ __| __/ _ \ '__| *
* | |_| | | |  __/ / __  / (_| | |   \ V /  __/\__ \ ||  __/ |    *
*  \__|_| |_|\___| \/ /_/ \__,_|_|    \_/ \___||___/\__\___|_|    *
*                                                                 *
* theHarvester 4.0.3                                              *
* Coded by Christian Martorella                                   *
* Edge-Security Research                                          *
* cmartorella@edge-security.com                                   *
*                                                                 *
******************************************************************* 


[*] Target: evolvesecurity.com 
 
        Searching 100 results.
        Searching 200 results.
        Searching 300 results.
        Searching 400 results.
        Searching 500 results.
[*] Searching Linkedin. 

[*] LinkedIn Users found: 301
---------------------
Abdul Aleem Tayob 
Abner Anglero - Evolve Security Academy 
Adabara Dalez - Evolve Security Academy 
Adam Minjares - Security Analyst 
Alec A. - Jr. SOC Analyst 
Alex Brown - Evolve Security Products Limited 
Alex Cohen - Independent Contractor 
Alex Goldman - Evolve Security Academy 
...
```

The output continues for tons of pages. 

To do all sources, switch to `all` with `-b`. 

## Tools in Class
- `site:uga.edu AND filetype:docx AND "security policy"`
- https://www.sans.org/posters/google-hacking-and-defense-cheat-sheet/ #dorking #osint 
- `site:*evolvesecurity.com AND inurl:*login*`
- `site:github.com *evolvesec
- https://docs.google.com/document/d/1A2v1eK52j-6VDCKnc1H2-Qdv9uMSBO1b6hVi7GB0n_A/edit
- https://github.com/ElevenPaths/FOCA - FOCA #foca #osint

Really cool passive info gathering tools:  

-   [https://github.com/arch4ngel/eavesarp](https://github.com/arch4ngel/eavesarp)
-   [https://github.com/lgandx/PCredz](https://github.com/lgandx/PCredz)
## On Client Suggestions
- Command prompt > powershell > powershell ise > old powershell
- Task manager > wireshark > portable wireshark