# nano
## Description

The basic *Linux* text editor is `nano`. It can be used to create a new file that does not exist, or edit a file that already exists. 

## Syntax

```
nano [filename]
```

When using `nano`, there are a few commands to know

- <kbd>ctrl</kbd>+<kbd>O</kbd> &mdash; Saves the file
- <kbd>ctrl</kbd>+<kbd>X</kbd> &mdash; Closes the file. If you do this before saving, it will ask if you want to "Save the modified buffer". Press <kbd>>Y</kbd> to save with the same name or provide a new one. You may press <kbd>>N</kbd> if this was in error. 
- <kbd>ctrl</kbd>+<kbd>W</kbd> &mdash; Search within the file for a text string. Press <kbd>Enter</kbd> to search. 
	- Using <kbd>alt</kbd>+<kbd>W</kbd> to move to the next match. 
- <kbd>ctrl</kbd>+<kbd>K</kbd> &mdash; Cuts the current line
- <kbd>ctrl</kbd>+<kbd>U</kbd> &mdash; Pastes what was previously cut. Can do this many times. 

There are several arguments to use with `nano`:
- `-B` &mdash; Creates a backup. Appends `~` to the end of the file using the same nam,e 
- `-F` &mdash; Read the file into a new buffer by default (creates a new file)
- `-l` &mdash; Include line numbers
- `-m` &mdash; Enables mouse support
