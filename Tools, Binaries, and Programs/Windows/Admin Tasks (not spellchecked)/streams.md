# Streams
###### Tags[^1]

## Syntax
```
C:\Users>streams

streams v1.60 - Reveal NTFS alternate streams.
Copyright (C) 2005-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

usage: streams [-s] [-d] <file or directory>
-s     Recurse subdirectories
-d     Delete streams
-nobanner
       Do not display the startup banner and copyright message.
```

Use with `*` to list the streams for all files in the directory., 
## Examples
***Listing the data streams in a file***
```
C:\Users>streams alternate_stream.txt

streams v1.60 - Reveal NTFS alternate streams.
Copyright (C) 2005-2016 Mark Russinovich
Sysinternals - www.sysinternals.com

C:\Users\alternate_stream.txt:
             :ADS:$DATA 48

C:\Users>more < alternate_stream.txt

C:\Users>more < alternate_stream.txt:ADS
"I am saved to an alternate stream named ADS"
```

For reference, a file with no non-default data streams
```
C:\Users>streams defeault_stream.txt

streams v1.60 - Reveal NTFS alternate streams.
Copyright (C) 2005-2016 Mark Russinovich
Sysinternals - www.sysinternals.com
```
 **Common Arguments**
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 
 - ` ` &mdash; 



 [^1]: #windows #fundamental #administrative #security 
