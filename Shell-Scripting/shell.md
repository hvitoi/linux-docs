# Shell scripting

- `Hardware` -> `Kernel` -> `Shell` -> `Application` -> `User`
- `CPU` -> `Program` -> `Bash` -> `Browser` -> `You`

Shell + Kernel = `OS`
Shell + Application = `Software`

- Shell is an interface between the users and the Kernel/OS
- `CLI` is a Shell
- `GUI` is a Shell

## Find your shell

```sh
echo $0 # Current shell
cat /etc/shells # Available shells
echo $? # Print the exit code
```

## Types of Shell

- `Gnome`: Graphical shell
- `KDE`
- `sh`: Command line shell. Original linux shell. Born shell. Developed by Stephan Born, therefore the name
- `bash`: Born Again SHell (New version of sh)
- `csh` and `tcsh`: C oriented shells.
- `ksh`: Korn SHell (Most used in Solaris)

## Change the default shell

- Change default shell
- The shell binary must be authorized in `/etc/shells`

```sh
# Change the default shell for the current user
chsh -s `shell`

# Example for zsh
chsh -s $(which zsh) # Log out to apply!

# Check the user shell
cat /etc/passwd | grep `username`
echo $SHELL
```

## Shell Scripting

- Shell: `#!/bin/bash`
- Comments: `# comments`
- Commands: `echo, cp, grep etc`
- Statements: `if, while, for etc`

--> Shell scripts MUST have executable permissions!
--> Shell scripts MUST be called from the absolute or relative path ./script.bash

## Variables

```bash
#!/bin/bash
name=Herique
surname=Vitoi
msg='How are you?' # Muti-word strings must be in quotes!
echo # Print blank line
echo "Good day, $name $surname. $msg"
```

## Input / Output

```bash
#!/bin/bash
echo What is your name?
read varname # Wait for input
echo Hello $varname
myhostname=`hostname` # The ticks are necessary is the result of a command needs to be assigned to a variable
echo My host is $a
```

## If - Then

```bash
#!/bin/bash

count=100
if [ $count -eq 100 ]
then
  echo Count is 100
else
  echo Count is not 100
fi

if [ -e /home/hvitoi/Documents/error.txt ] # -e checks if a file exists
then
  echo "File exists"
else
echo "File does not exist"
fi
```

## For loops

```bash
#!/bin/bash
for i in 1 2 3 4 5
do
  echo "Welcome $i times"
done

for i in eat run jump play
do
  echo $i
done

for i in {1..5} # same as 1 2 3 4 5
do
  touch $i
done
```

## While

```bash
#!/bin/bash
count=0
num=10

while [ $count -lt 10 ] # less than
do
  echo $num seconds left to stop this process
  sleep 1
  num=`expr $num - 1`  # mathematical expression
  count=`expr $count + 1`
done

echo $1 process is stopped # $1 is the process id
```

## Case statements

```bash
#!/bin/bash
echo Choose an option
echo 'a = Display date and time'
echo 'b = List file and directories'
echo 'c = List users logged in'
echo 'd = Check system uptime'
read choice

case $choice in
  a) date;; # 'a' run the command date;
  b) ls;;
  c) who;;
  d) uptime;;
  *) echo Invalid choice. # default option
esac
```

## Check server connectivity

```bash
#!/bin/bash
host="192.168.1.1"

ping -c1 $host # c1 is count. Ping once
if [ $? -eq 0 ] # $? exit status of the previous above
then
  echo $host is OK
else
  echo $host is NOT OK
fi

ping -c1 $host &> /dev/null # /dev/null is a blackhole and the message is not shown
if [ $? -eq 0 ] # $? is the reutrn of the command above
then
  echo $host is OK
else
  echo $host is NOT OK
fi

# Read the hosts from a file
hosts=`cat /home/hvitoi/Documents/my-hosts`
for ip in $hosts # or $(cat /home/hvitoi/Documents/my-hosts)
do
  ping -c1 $ip &> /dev/null # /dev/null is a blackhole and the message is not shown
  if [ $? -eq 0 ] # $? is the reutrn of the command above
  then
    echo $ip is OK
  else
    echo $ip is NOT OK
  fi
done
```

## Aliases

```bash
# Create alias
alias ll = "ls -laF"
alias pl = "pws; ls"
alias tell = "whoami; hostname; pwd"
alias dir = "ls -l | grep ^d" # List only directories
alias d = "df -h | awk '{print \$6}' | cut -c1-4" # \$6 the \ is necessary! Otherwise the shell interprets as an environment variable

# List all aliases
alias

# Remove alias
unalias `alias_name`
```

- User alias `~/.bashrc`
- Global alias `/etc/bashrc`

## Shell History

```bash
# Show the last executed commands
history # 1000 by default

# The result of history feeds the less command
history | less

# Execute the nth command
!`command_number`
!455 # executes command number 455
```

- File the stores the history: `~/.bash_history`
