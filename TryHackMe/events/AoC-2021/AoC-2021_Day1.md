# AoC-2021_Day1

[AoC-2021_TOC](AoC-2021_TOC.md)  
Tags [^1]


Given an [Insecure Direct Object Reference (IDOR)](../../../concepts/Insecure%20Direct%20Object%20Reference%20(IDOR).md) vulnerable website. Navigating to the *Your Activity* page shows an `IDOR` vulnerable URL. 

![IDOR Vuln Spotted](AoC-2021_Photos/1.0%20AoC-Day-1_12-19-21-IDOR_Vuln.png)

Logical User ID for admin, superuser, or other desireable accounts is `1` or `0` and an attempt yields the activity for "Santa" is `1`.

![Santa Activity](AoC-2021_Photos/2.0%20AoC-Day-1_12-19-21-Santa-Activity.png)

Attempting several others yields User ID  `9` is for "The Grinch." There are several options for *Revert* on the page related to changed inventory SKU numbers. 

```
https://inventory-management.thm/activity?user_id=9
```

![Grinch Activity](AoC-2021_Photos/3.0%20AoC-Day-1_12-19-21-Grinch-Activity-w-Reverts.png)

Reverting all of the changes yielded the [flag](AoC-2021_Day1.md#Flag%20THM%20AOC_IDOR_2B34BHI3) for the box.  [Go to flag](#flag)

![Flag!](AoC-2021_Photos/4.0%20AoC-Day-1_12-19-21-Revert-To-Flags.png)

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

<a href="#flag">Flag</a> THM{AOC_IDOR_2B34BHI3}
[^1]: #idor #webapp 