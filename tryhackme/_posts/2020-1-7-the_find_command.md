---
layout: post
title: The find command
description: >
  This tutorial will help you understand how to use the `find` command effectively in a CTF context. It is written in a way that you won’t have to refer to the man page to complete it, although I recommend the man page for further reading..
---

# The find command


## Task 2

### Find all files whose name ends with ".xml"

```bash

find / -type f -name "*.xml"

```

### Find all files in the /home directory (recursive) whose name is "user.txt" (case insensitive)

```bash

find /home -type f -name user.txt

```

### Find all directories whose name contains the word "exploits"

```bash

find / -type d -name "*exploits"

```

## Task 3


### Find all files owned by the user "kittycat"

```bash

find / -type f -user kittycat

```



### Find all files that are exactly 150 bytes in size

```bash

find / -type f -size 150

```


###  Find all files in the /home directory (recursive) with size less than 2 KiB’s and extension ".txt"

```bash

find /home -type f -size -2k -name "*.txt"

```


### Find all files that are exactly readable and writeable by the owner, and readable by everyone else (use octal format)

```bash

find / -type f 644

```

### Find all files that are only readable by anyone (use octal format)


```bash

find / -type f -prem /444

```

### Find all files with write permission for the group "others", regardless of any other permissions, with extension ".sh" (use symbolic format)

```bash

find / -type f -perm -o=w -name "*.sh"

```

### Find all files in the /usr/bin directory (recursive) that are owned by root and have at least the SUID permission (use symbolic format)


```bash

find /usr/bin -type f -user root -perm -u=s

```

### Find all files that were not accessed in the last 10 days with extension ".png"


```bash

find / -type f -time +10 -name "*.png"

```


###  Find all files in the /usr/bin directory (recursive) that have been modified within the last 2 hours


```bash

find /usr/bin -type f -mmin -120

```