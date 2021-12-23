# TryHackMe - Advent of Cyber 2021 - Day 1
## Save the Gifts
> Edward Hartmann
> December 19, 2021

***<u>Refs/Links:</u>***
- [Advent of Cyber 2021 TOC](_AoC-2021_TOC.md)  
-  Tags[^1] 
-  Flag[^2]

[^1]: #idor #webapp 
[^2]: THM{AOC_IDOR_2B34BHI3}

## Walkthrough
We are given an [IDOR](../../../knowledge-base/vulnerabilities/insecure_direct_object_reference-IDOR.md) vulnerable website. Navigating to the *Your Activity* page shows a vulnerable URL. 

![IDOR Vuln Spotted](AoC-2021_Photos/1.0%20AoC-Day-1_12-19-21-IDOR_Vuln.png)

Logical User ID for admin, superuser, or other desireable accounts is `1` or `0` and an attempt yields the activity for "Santa" is `1`.

![Santa Activity](AoC-2021_Photos/2.0%20AoC-Day-1_12-19-21-Santa-Activity.png)

Attempting several others yields User ID  `3` is for "McStocker and `9` is for "The Grinch." There are several options for *Revert* on the page related to changed inventory SKU numbers. 

![McStocker](AoC-2021_Photos/2.5%20AoC-Day-1_12-19-21-McStocker.png)

```
https://inventory-management.thm/activity?user_id=9
```

![Grinch Activity](AoC-2021_Photos/3.0%20AoC-Day-1_12-19-21-Grinch-Activity-w-Reverts.png)

Reverting all of the changes yielded the [flag](AoC-2021_Day1.0.md#Flag%20THM%20AOC_IDOR_2B34BHI3) for the box.  Scroll down for flag

![Flag!](AoC-2021_Photos/4.0%20AoC-Day-1_12-19-21-Revert-To-Flags.png)

Congratulations on completing the box!
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


