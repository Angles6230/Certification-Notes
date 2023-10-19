list files -ls -l
find ip 
	-ifconfig
	ip addr
# Manage files from command line
File systems
	linux -ext3 ext4 xfs
	windows -NTFS FAT
	etc - config files
	home -user dir located
	opt - programs are running
	sbin -cmds and scripts are located
	var - logs
Directory listing attributes
	d next to rwx is directory
	l is a link
	Type | # of links | owner | group | size | month | day | time |name
	ls -ltr - t `[time ordered]` -r `[reverse ordered]`
Creating files and directories
	touch
	cp - copy file and create new file at dest
	vi 
	mkdir
File maint
	cp 
	rm
	mv
	mkdir
	rmdir or rm -r
	chgrp -change group owner
	chown
Soft links and hard links
	i node - inode is the number that points to the file on a harddisk
	To find iNODE- `ls -i`
	soft link - linke will be removed if file is removed or renamed
		`ln -s [file you want to link to]`
		soft link has a different inode from hardlink
	hard link -link to the inode
		`ln`
		When you remove source file, the information in the dest, it does not disappear.
		Basically creates a new name for the same file
Standard input and output
	stdin - 0
	`<` - redirects the contents of a file into  a cmd
	stdout - 1
		`>` - to redirect
		`>>` - to append
	stderr - 2
	`2>` - redirect stderr to X
	`&>2` - redirect stdout and stderr to X 
Pipes
	used by the shell to connect the output of one cmd directy to input of another cmd
	`|` 
Help commands
	`whatis`
	command `--help`
	`man` command
# Linux file editors
vi - visual editor
	`i` - insert
	`Esc` - esc out of mode
	`r` - replace one character
	`x` - delete one char
	`dd` - delete entire line
	`u` -undo delete
	`:w` -write
	`:q` - quit
	`shift+ZZ` - save file
	`a` - inserts a space
	`/` - search
		`n` - next going down
		`shift+n` - next going up
vim - adv vi
ex - extended line editor
emacs - full screen editor
ed - std line editor
# User account managment
`useradd -g groupname -s /provide/shell -c "comment" -m[make directory] -d [define/userhome/directory] [username]`
	Create passwd - `passwd [username]
`userdel`
`groupadd`
`groupdel`
`usermod`
Files
	/etc/passwd
		`name|password|UID|GID|comment|homedir|shell`
	/etc/group
		`group|group passwd| GID | Users part of group`
	/etc/shadow
		`username|hashed passwd| last password change | min days req between passwd changes | max days passwd is valid | num of days before passwd exp that user is warned | num of days after passwd exp that acct is disabled | date of acct expiration`
`chage [-m mindays] [-M maxdays] [-d lastday] [-I inactive] [-E expiredate] [-W warndays] user`
	default set in /etc/login.def
`chmod [ugo] [+/-] [s/o/w] [rwx] file` - mod file permissions user/group/owner's ability to read/write/execute  s - add/remove the SUID/SGID for X and W is for world/others bit
`chown [owner] [:group] file`
Switch users
	`su -username`
	`sudo` -switch to root
	`visudo` -add or remove rights to certain commands by modifying /etc/sudoers
# Monitoring and managing processes.
Application = service
