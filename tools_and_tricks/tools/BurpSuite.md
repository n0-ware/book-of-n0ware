# BurpSuite
## TOC
- [Description](#Description)
- [Configuration](#Configuration)
	- [Importing Certificate to Chrome](#Importing%20Certificate%20to%20Chrome)
	- [Importing Certificate to FireFox](#Importing%20Certificate%20to%20FireFox)
- [Modules](#Modules)
	- [Intruder](#Intruder)
		- [Sniper](#Sniper)
		- [Cluster Bomb](#Cluster%20Bomb)
		- [Pitchfork](#Pitchfork)
		- [Battering Ram](#Battering%20Ram)
	- [Repeater](#Repeater)
	- [Sequencer](#Sequencer)
	- [Decoder](#Decoder)
	- [Comparer](#Comparer)
	- [Logger](#Logger)
	- [Extender](#Extender)
## Description

## Configuration
A proxy is required for BurpSuite to intercept traffic, and my favorite is the *FoxyProxy* extension on [Chrome](https://chrome.google.com/webstore/detail/foxyproxy-standard/gcknhkkoolaabfmlnjonogaaifnjlfnp?hl=en) or [FireFox](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/). Simply install the extension and configure a proxy on `127.0.0.1` port `8080`. 

_Configuration on Chrome_
![FoxyProxy Configuration on Chrome](tools/tools_photos/BurpSuite-FoxyProxy-Chrome.png)

_Configuration on Firefox_ 
![FoxyProxy Configuration on FireFox](tools/tools_photos/BurpSuite-FoxyProxy-Firefox.png)
Once you've launched BurpSuite, it automatically enables the proxy by default, and if you have not turned on your proxy extension, no traffic will be able to pass through BurpSuite after it intercepts. Simply click the *FoxyProxy* extension and choose your new proxy. 

![FoxyProxy Enabled](tools/tools_photos/BurpSuite-Foxy-Proxy-Enabled.png)

You can also toggle the `Incerept is X` button to *off* to stop intercepting traffic. 

![BurpSuite Intercept](tools/tools_photos/BurpSuite-Intercept-On_Off.png)

BurpSuite requires a self-installed certificate for `SSL` traffic to work on `HTTPS` websites. Head to `Proxy` >`Options` in the BurpSuite menu and click `Import/export CA certificate`, save the certificate in `DER` format, pick a location to save the file, and give it a name with the extension `.der`. 

![Export Certificate](tools/tools_photos/BurpSuite-Export-Certificate.png)

Alternatively, you can go to `127.0.0.1:8080` in your browser and click `CA Certificate` to download. 

![Download Certificate on Localhost](tools/tools_photos/BurpSuite-Certificate-On-Localhost.png)

Take note of where you save the certificate for the next step. 


### Importing Certificate to Chrome
In *Chrome*, head to `Settings` and search for `Security`. 

![Search for Security](tools/tools_photos/BurpSuite-Chrome-Cert-Import-1.png)

Find the `Manage Certificates` option

![Locate Manage certificates](tools/tools_photos/BurpSuite-Chrome-Cert-Import-2.png)

Click the `Authorities` tab and `Import` your certificate. Choose only the first checkbox when prompted to *Trust this certificate for identifying websites*.
![Import the BurpSuite CA on Authorities](tools/tools_photos/BurpSuite-Chrome-Cert-Import-3.png)

![Trust the Certificate for Websites](tools/tools_photos/BurpSuite-Chrome-Cert-Import-4.png)

You are now configured for BurpSuite on Chrome!

### Importing Certificate to FireFox

In *FireFox* head to `Settings` , search for `Certificates` in the search bar, then click `View Certificates`. 

![View FireFox Certificates](tools/tools_photos/BurpSuite-FireFox-Cert-Import-1.png)

On the `Authorities` tab select `Import...` and load the BurpSuite certificate. 

![](tools/tools_photos/BurpSuite-FireFox-Cert-Import-2.png)

Select the checkbox to *"Trust this CA to identify websites"* and click `Ok`

You are now prepared to use BurpSuite with Firefox

## Modules
### Intruder
#### Sniper 
#### Cluster Bomb
***A note on Cluster Bomb and Exponential Combinations***   </br>

When it comes to using this utility, think of it as if we had four items in our list:

```
1
2
3
4
```

With cluster bomb, our possible combinations are 42

```
11 12 13 14 
21 22 23 24
31 32 33 34
41 42 43 44
```

We have 16 total combinations with only 4 items on the wordlist. With the wordlist `rockyou` , containing about 14 million passwords, that is over 205 **trillion** possible combinations. A bit unwieldy. Even a small wordlist with 100 items still results in 10,000 possible combinations, making cluster bomb a use-case specific tool that must be used with a carefully curated wordlist if you hope to achieve a positive result in any reasonable amount of time. If you are using BurpSuite free, the rate it tests combinations is throttled, further increasing the time to test the list.

When attacking software applications, fuzzing for unexpected behavior, wordlists can be expected to be enormous as you are attempting to test for an enormous amount of possible data combinations and intending to produce error. When password brute forcing, however, we are fighting against account lockouts and time. Keep this in mind as you use cluster bomb. More often, it is best to attempt to enumerate a username and use the _Sniper_ utility to target the username or usernames you enumerated.

#### Pitchfork
#### Battering Ram
### Repeater
### Sequencer
### Decoder
### Comparer
### Logger
### Extender

#burp #webapp #hacking #burp 