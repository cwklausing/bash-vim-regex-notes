# Intro
## kernel:
*cpu scheduling
*i/o comp hardware
*memory

## shell
* comp program to launch other programs using text interface
* bash - 1987

## utilities
* ecosystem of programs

## Unix philosophy
* each program should do one thing well
* output of a program can become input of another--aka modular

## Test your shell!
  echo $SHELL

# Beginning

## simple commands
ls can take a bunch of arguments--for ex, a path:
* ls /

cd, pwd, ls

## Special directories
* .
* ..
* ~

## cat
can concatenate two files
probably DON'T want to cat a jpeg file

## cp
copies files:
ex: cp beep.txt boop.txt
--copies beep into boop

## cp -r
*recursively copy directories into new directories

## mv
*rename and overwrite files

## mkdir
* mkdir -p
* can make a bunch of directories in a row

## testing
can put 'echo' in front of a command

## brace expansion
braces expand whatever is before that
ex: cat b{ee,oo}p.txt
note: brace expansion option doesn't have to exist
another ex:
echo {look,sneeze,laugh}{at,with,around}{me,you,him}
another another ex:
mkdir -p images/img{0..100}

## rm
*removes a single file
*rmdir removes empty directory

## wc
word count
lines, words, bytes in a file
can read from files and standard input

## head
display first line of a file

## tail
same as head, but the end

## paths
relative v absolute

## saving outputs
echo hello there > hello.txt
the greater than symbol redirects to standard output in a file

## interesting tidbit
appending things is a lot easier than prepending things

## PIPES! Yeah | Yeah | Yeah
pipes allow you to fed the output of one program to the input of the next
for ex:
ls -1 *.txt | wc -l
^ this lists the number of text files, counts them

can use pipes to 

## CURL

## sed
sed -E 's/\s+/\n/g'
^ will give each word a new line

## cal
shows current month's calendar. Can also pass month/year

## date
date + '%H' shows hours
date + '%H:%M:%S' shows hour minute date
date + '%F' shows year month date

## backticks
run a command, and saves stoutput into whatever you're doing
either
echo `date`
or
echo $(date)
another ex:
echo something data > blah-$(date).log

## environment variables
* vars defined by the shell and shell scripts
like $HOME
using all caps is the convention

# Scripts!
simple script:
while true; do date; sleep 1; done

at top of script file, need to have #!/bin/bash

piping into a while loop:
ls -1 | while read LINE; do echo -n "$LINE "; wc -l $LINE; done

# Permissions
UGO[+|i]WRX
can be written in octal

# exit codes
echo $?

## if test -f cool.txt; then echo ok; else echo not good;
if you put parenthases around something, it will evaluate it (or something like that?)

## jobs
can type 'jobs' to see what jobs are running
ctrl+z puts current program into background
fg puts it back into foreground
with multiple, need fg %number

### pgrep searches a program by its name

# REGEX
Main commands:
* grep
* sed
* perl
* vim
* less

## common regex format
`/PATTERN/` - match
`s/PATTERN/REPLACEMENT/` - replace
^t = line starts with a t

## flags
i - case insensitive
g - match all occurences

## metacharacters
`.` matches any character

## character class sequences
'\w' - word character: `[A-Za-z0-9_]`
'\W' - non-word character

## anchors
`^` - anchor at the beginning
`$` - anchor to the end

ex:
'cool beans'.replace(/^beans/, 'Beans')
'cool beans'
'beans cool'.replace(/^beans/, 'Beans')
'Beans cool'
'beans cool'.replace(/^beans/, 'Beans')
ex2:
'beep boop'.replace(/b(ee|oo)p/g, 'braaap')
'braaap braaap'

## capture groups
take whatever the regex finds, and add stuff before/after it, or replace things around it
echo 'hey <cool> whatever' | sed -r 's/<([^>]+)>/(\1)/g'

