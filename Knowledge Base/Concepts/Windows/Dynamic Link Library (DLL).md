# Dynmic Link Libraries (DLLs)

The concept of "libraries" is universal to most programming languages. Essentially, a *library* is a set of code that accomplishes a specific task, enables a particular function, or otherwise "does something" that a programmer may want to incorporate into their code without having to write it themselves. It can be simple, or wildly complex, but in the end, programmers are able to pull in *libraries* to quickly and efficiently write code that builds on existing code to accomplish something else. 

In *Windows*, the libraries are known as [Dynamic Link Libraries (DLL)](../Concepts/Windows/Dynamic%20Link%20Library%20(DLL).md). They function together as a library of pre-written code that can be called upon by any number of applications at the same time to perform a task specific to the use case of the application calling on them. 

*Windows* uses an **enormous** amount of libraries at all times, and developers even use them to write code for *Windows*. 

*DLLs* are stored in specific files related to the [Directory Structure](04%20Directory%20Structure%20-%20Windows.md) of the particular architecture. In 64-bit versions, they live in **System32** and **SysWOW64**, containing 64 and 32-bit libraries, respectively. In 32-bit versions of *Windows*, all libraries are kept in **System32**. 

A common list of *DLLs* can be found [here](https://en.wikipedia.org/wiki/Microsoft_Windows_library_files) for further reading.

These are a common point of attack for malicious actors in a variety of ways. For example, in the event a DLL was deleted or otherwise not present, attackers can replace it with one of their own if they can put it where the application expects the missing one to be. The result can include privilege escalation, information disclosure, etc. 

The [listdlls](../../../Tools,%20Binaries,%20and%20Programs/Windows/Process%20Management%20(not%20spellchecked)/listdlls.md) command is used to list the running *DLLs* on the system. 
See a list of common *DLLs* [here](https://en.wikipedia.org/wiki/Microsoft_Windows_library_files). 

#windows #dll