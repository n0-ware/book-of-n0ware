# find

The "find" command is a complex one designed for navigating a specified portion of the file system to find files based on the specific arguments

## Examples

- `find . -type f -exec cat {} +`
	- Executes `cat` on all files in all directories in and below the current directory.