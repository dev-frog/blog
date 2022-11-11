---
layout: post
title: How to Delete Lines in Vim / Vi
description: >
  Vim comes preinstalled on most of linux distributions. Sometimes it's hard to remember vim shortcut/commands

---

# How to Delete Lines in Vim / Vi


1. Pressing `dd` multiple times will delete multiple lines.
2. Type `5dd` and hit enter to delete the next five lines.
3. The syntax for deleting a range of lines is as follows:
```console
:[start],[end]d
```
You can also use the following characters to specify the range:
- `.` (dot) the current line.
- `$` The last line.
- `%` All lines.

## Example

- `:.,$d` - from the current line to the end of the file.
- `:.,1d` - from the current line to the beginning of the file.
- `10,$d` - from the 10th line to the end of the file.
- `%d` - delete all the lines of the file.
- `:g/[pattern]/d` - Deleting multiple lines based on pattern.
- `:g/^$/d` - Deleting all Blank lines.
- `:g/^#/d` - Removing all `#` from every line of the file.
- 