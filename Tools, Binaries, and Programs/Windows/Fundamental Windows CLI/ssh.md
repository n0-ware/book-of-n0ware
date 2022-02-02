# Secure Shell (ssh)
###### Tags[^1]

 [^1]: #windows #fundamental #linux

The `ssh` command is used to securely remote into another computer via the command line on both *Windows* and *Linux*. The most secure form of `ssh` requires the use of public/private key authentication, requiring that the user attempting to `ssh` has the private key half of a public key stored on the server. 

 ## Syntax

 ```
 ssh [options] username@xxx.xxx.xxx.xxx
 ```

 Arguments
 - `-i` &mdash; Reference a "key file" for public/private key authentication