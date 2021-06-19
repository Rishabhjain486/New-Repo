# Ubuntu Settings

## MY BASH ALIASES:

ceate a file ".bash_aliases" and copy paste the following (inside {}):
```{
# To check RAM status
alias ram='free -m'

#To check HDD status
alias hdd='df -h'

# To check CPU status
alias cpu='cat /proc/cpuinfo'

# To check Memory info
alias memory='cat /proc/meminfo'

# To Clear the terminal
alias x='clear'
}```


## CHANGING THE TERMINAL FORMAT TO SHOW GIT BRANCH:

Open the file ".bashrc" and copy paste the following inside (inside [[ ]] ) at the end:
```[[
# Display active GIT branch name in the terminal (refer below link if modifications desired)
# https://thucnc.medium.com/how-to-show-current-git-branch-with-colors-in-bash-prompt-380d05a24745
parse_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
#export PS1="\u@\h \[\e[32m\]\w \[\e[91m\]\$(parse_git_branch)\[\e[00m\]$
export PS1="\[\e[91m\]\W \[\e[36m\[\e[1m\]\$(parse_git_branch)\[\e[00m\]: "
]]```


## CODE TO CHECK THE TEMP OF RASPBERRY PI ON UBUNTU:

Create a .c file with the following code (inside [[ ]]):
```[[
#include <stdio.h>

int main (int argc, char *argv[])
{
FILE *fp;
int temp = 0;
fp = fopen("/sys/class/thermal/thermal_zone0/temp", "r");
fscanf(fp, "%d", &temp);
printf(">>CPU Temp: %.2f C\n", temp / 1000.0);
}
]]```

Compile the code with:
`gcc temp.c -o temp`

Copy to directory in your path:
`sudo mv ./temp /usr/local/bin/`

Now run the command `temp` from anywhere 
