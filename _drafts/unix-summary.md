# Posix Unix Operations Summary

## Shell Programming Related
- command
	built-in shell function to run with normal unix command
	without any shell function or alias
- echo
- expr
- false
- getopts
- logger
- printf
- read
- sh
- sleep
- tee
- test
- true
- xargs

## Text Processing Related
- awk
- comm
- csplit
- cut
- diff
- ed
- expand
- fold
- head
- iconv
- join
- lp
- paste
- patch
- pr
- sed
- sort
- tail
- tr
- tsort
- unexpand
- uniq
- wc

## Filesystem Related
- basename
- cat
- cd
- chgrp
- chmod
- chown
- cksum
- cmp
- cp
- dd
- df
- dirname
- du
- file
- find
- ln
- ls
- mkdir
- mkfifo
- mv
- patchchk
- pwd
- rm
- mdir
- touch

## Process Management Related
- at
- batch
- kill
- nice
- nohup
- ps
- renice
- time
- wait

## Network Related
- uuencode
- uudecode

## Misc
- alias
- ar
- bc
- crontab
- date
- env
- gencat
- getconf
- grep
- hash
- id
- locale
- localedef
- logname
- m4
- mailx
- man
- mesg
- newgrep
- od
- pax
- split
- strings
- stty
- tabs
- tput
- tty
- umask
- unalias
- uname
- write





Move file in batch

```shell
mkdir folder
mv * folder
```

Remove suffix in batch

```shell
for file in suffix_*; do 
	mv $file ${file$suffix_} 
done
```

<br>


