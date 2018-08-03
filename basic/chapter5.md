- rx has to be given to directory for peolpe to enter it. w is a serious operation because haiving it, one can add new file ,rm or mv exisiting files under the directory (but cannot modify or read files if do not have permission).
- think about directory as a drawer. r means light, x means key. You can must use key(x) open it to get something. But you do not have to have light(r) find it as long as you know exactly where the thing is (know filename).
- chgrp -R groupname dirname/filename
- chown -R username:groupname dirname/filename
- chmod
  u,g,o,a +-= rwx
  chmod u=rwx,go=rx .bashrc

- having w can modify but cannot delete file
- su - and exit
- kernel version check
  uname -rm
- chmod 754 filename or chmod u=rwx,g=rx,o=r filename
- chown chgrp