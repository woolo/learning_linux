- `cd -`
- pwd -P
- mkdir -m 711 test
- ls -d
- rmdir
  for rm empty directory
- PATH="${PATH}:/root"
- cp -a
  Usually when we cp other people's file, we want the copied file to be ours. However, when doing the backup, we want the try to preserve all the priviledge as before. Therefore, we use cp -a. Why we say, "try to preserve"? Becuase sometime, the operator do not have the priviledge to change the owner and group of the files. e.g, you cannot make the file still owned by root when copying it from root.

- cp -u
  Only copy when copied one is newer. Useful for backup.

- cp -l V.S cp -s
hard link V.S. symbolic link

- cat -n
- cat -A
- less is more than viewing file
  /string search string below
  ?string search string above
  n search next matched string
  N search previous matched string
  g go to first line
  G go to the end

- man is using less
- tail -f file
  very useful: keep monitoring the changes to the file (log file for example), until [ctrl]-c

- head -n 20 /etc/man_db.conf | tail -n 10
  very interesting


- never search ascii table again
echo -n a | od -t d
echo -n a | od -t dCc

- use ; to execute mulitple commands and join the output together for better comparision sometimes.
- use \ to write input in one line

- umask affects the intial permission bits of newly created files in the current shell execution evironment. umask value indicates the permission that will be removed from the default permission. The default permission for a file is 666 while for a directory is 777. Therefore, when umask is set to 022, it will remove the write permission of others, no matter others have the permission or not. Specifically, the permission of others is rwx, when w is removed, it become r-w. Please do not simply sum the decimal number representation. Why? See this example: 666-003=663, -rw-rw--wx. But actually should be: (-rw-rw-rw-) - (--------wx) = -rw-rw-r--

# Under Ext2/Ext3/Ext4/xfs
- chattr +a file
  can only append data to the file. The file cannot be rm or modify. This may especially useful for log file to detect system intrusion?

- chattr +i file
  cannot rm, rename, cp -s or write or append data to the file.

- lsattr -adR filename or directory

#
- SUID can let the executor (people who have the w permission) temporarily become the owner of the binary file in order to execute this binary. e.g. /etc/shadow is owned by root. However, all the users can change their own password which will use /etc/passwd. This is also why onion-share need a binary file compiled from c to become amnesia in Tails.
- SBIT is for directory only, making the file in the directory can only be rm by owner and root, even if the directory has w permission to everyone. eg. /tmp
- SUID -4 SGID -2 SBIT -1 , chmod 7551
- SUID u+s SGID g+s SBIT o+t
- which will search the command available in $PATH, therefore, command brought by bash will not be found. eg. which history
- find is the most complete and powerful find. one can specify file time, size, permission and so on.