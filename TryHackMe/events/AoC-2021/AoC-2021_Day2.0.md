# AoC-2021_Day2
> Edward Hartmann
> December 20, 2021

Refs/Links:
- [Advent of Cyber 2021 TOC](_AoC-2021_TOC.md)  
-  Tags[^1]
-  Flag[^2]
## Walkthrough
We are given a website and told it is vulnerable to [cookie manipulation](../../../knowledge-base/vulnerabilities/cookie_manipulation.md). 

![Vulnerable Landing Page](AoC-2021_Photos/5.0%20AoC-Day-2_12-19-21-Lading-Page.png)

With no access we are going to create an account, but will view the [cookies](../../../knowledge-base/concepts/web/cookies.md) first to see what changes. No cookies are present prior to creating an account or logging in. 

![No Cookies](AoC-2021_Photos/6.0%20AoC-Day-2_12-20-21-No-Cookies.png)

When attempting to create an account, we are told we do not have permissions to do so. 

![Cannot Create Account](AoC-2021_Photos/7.0%20AoC-Day-2_12-20-21-Cannot-Create-Account.png)

While we could not create an account, we were given a cookie named `user-auth` with a value `7b636f6d70616e793a2022546865204265737420466573746976616c20436f6d70616e79222c206973726567697374657265643a2254727565222c20757365726e616d653a226e305f77617265227d`.

![User-Auth Cookie](AoC-2021_Photos/8.0%20AoC-Day-2_12-20-21-User-Auth-Cookie.png)

To identify this cookies encoding we will use [CyberChef](https://gchq.github.io/CyberChef/) on GitHub. Paste the cookie into the `Input` box and drag `Magic` from the left menu into the `Recipe` pane. The output field informs us this encoded with `hexadecimal`. This can be verified by removing `Magic` and replacing it with `From Hex` to achieve the same result. 

![CyberChef Magic Decoding](AoC-2021_Photos/9.0%20AoC-Day-2_12-20-21-Magic-Decoding.png)

Verified with `From Hex`

![From Hex Decoding](AoC-2021_Photos/10.0%20AoC-Day-2_12-20-21-Hexdump-Decoding.png)

At a glance, it is also easy to note that this is `hexadecimal` due to the type of values in the string. It is entirely alphanumeric, and there are no characters except `a-f`. 

Our decoded value is in `JSON` format, and easily editable type of object we can modify to our needs. The cookie also contains little identifiable information to prevent us from using another username to attempt to login. Let's give it a try with the username `admin`. Using CyberChef, simply replace `From Hex` with `To Hex` and put the modified `JSON` in the `Input` field. 


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

[^1]: #cookies #authentication #webapp
[^2]: 