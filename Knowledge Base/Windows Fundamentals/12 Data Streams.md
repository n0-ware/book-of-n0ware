# Data Streams
###### Tags[^1] 
Within [Network File System (NFS)](../Concepts/Network%20File%20System%20(NFS).md), there are multiple types of "streams" that NTFS can use to store content. Typically, when data is created, it is stored on the default data stream. We can, however, use al *alternate data stream* to store our data, known as *ADS*. We can create our own *ADS* and choose to save the data there. Let's use an example by first printing data from a file stored on the default data stream using [type](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/type.md).

```
C:\Users>echo "I am part of the default stream" > defeault_stream.txt

C:\Users>type defeault_stream.txt
"I am part of the default stream"
```

This functions as expected. We piped some data using [echo](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/echo.md) into the file `default_stream.txt` and printed it with [type](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/type.md). But how do we create an *ADS*, save some data to that stream, and then access it? This is done using [echo](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/echo.md) and appending `:[Stream]` to the end of the file. View this below. 

```
C:\Users>echo "I am saved to an alternate stream named ADS" > alternate_stream.txt:ADS

C:\Users>type alternate_stream.txt
```

Notice how when we used `type` on `alternate_stream.txt` we did not get any output. This is because the syntax we used will only print data from the default stream. We can print data from alternate streams by using [dir](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/dir.md#Listing%20Data%20Streams) with the `/R` flag to show alternate data streams. 

```
C:\Users>dir /R
 Volume in drive C is Black SSD
 Volume Serial Number is DE8E-ADB8

 Directory of C:\Users

01/31/2022  09:07 AM    <DIR>          .
01/31/2022  09:07 AM    <DIR>          ..
01/31/2022  09:07 AM                 0 alternate_stream.txt
                                    48 alternate_stream.txt:ADS:$DATA
01/31/2022  09:04 AM                36 defeault_stream.txt

               2 File(s)             36 bytes
               5 Dir(s)  164,176,179,200 bytes free
```

It is worth nothing that the 36 bytes that made up `alternate_stream.txt` are not counted in the total bytes, even with the `/R` flag. You would have to use a command such as [du](../../Tools,%20Binaries,%20and%20Programs/Windows/Admin%20Tasks%20(not%20spellchecked)/du.md) from [sysinternals](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/sysinternals.md) to truly list the total space on disk. 

In order to print this data, we cannot use `type`. We have to redirect the contents of `alternate_stream.txt:ADS` into a command like `more`. 

```
C:\Users>more < alternate_stream.txt:ADS
"I am saved to an alternate stream named ADS"
```


Another built in [sysinternals](../../Tools,%20Binaries,%20and%20Programs/Windows/Fundamental%20Windows%20CLI/sysinternals.md) command [streams](../../Tools,%20Binaries,%20and%20Programs/Windows/Admin%20Tasks%20(not%20spellchecked)/streams.md) can be used to display the hidden streams not immediately visible. 

```
C:\Users>streams alternate_stream.txt

streams v1.60 - Reveal NTFS alternate streams.
Copyright (C) 2005-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

C:\Users\alternate_stream.txt:
             :ADS:$DATA 48
```

The reason this is worth noting is due to the potential security ramifications this represents. While *Windows* uses these alternate data streams as a way to manipulate data for operating system specific reasons, malicious files can use this to hide data in plain sight. Remembering to use `dir /R` and `dir /AH` when performing investigations is crucial from a blue team perspective to ensure you are finding potential threats to your system. 

An overview of Data Streams from Malwarebytes can be found [here]. 

[1^]: #windows #fundamental 