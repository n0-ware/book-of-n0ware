# Windows Registry
*Windows* uses something called the **registry**[^2] as a database to store this configuration data for system components to store and retrieve this data. 

The data contained in the registry varies according to the version of *Windows* in question. Applications use something called the "registry API" to retrieve, modify, or delete registry data. Errors in the registry can break functions on the system, requiring you to restore the value to the state it was in prior to the errors. 

 In *Windows*, the registry contains *the most critical* system information, constantly used, referenced, and relied upon by the OS and applications during all phases of system operation. 

The registry is organized by `hives` each one containing `keys` and `values`. Changes can be made according to a hive, such as for a user via the `HKEY_CURRENT_USER` hive or on the entire system via the `HKEY_LOCAL_MACHINE` hive. 

> It is important to note that the *Windows* registry is an attractive attack vector with a wide attack surface and ripe targets. Passwords and hashes can be extracted, crucial configurations changed, and essential functions tampered with if the proper permissions are not in place. 

See [Registry Basics](../../Windows%20Fundamentals/10%20Registry%20Basics.md) for more information. Also [Hives](../../Windows%20Fundamentals/10%20Registry%20Basics.md#Hives) and [Using Keys](../../Windows%20Fundamentals/10%20Registry%20Basics.md#Using%20Keys). For interacting with the registry, see [reg](../../../Tools,%20Binaries,%20and%20Programs/Windows/Admin%20Tasks%20(not%20spellchecked)/reg.md).

[^1]: https://docs.microsoft.com/en-us/windows/win32/sysinfo/registry
[^2]: https://docs.microsoft.com/en-us/windows/win32/shell/hkey-type
[^3]: https://docs.microsoft.com/en-us/windows/win32/sysinfo/predefined-keys