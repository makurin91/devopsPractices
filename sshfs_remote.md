
* Create ssh key `ssh-keygen` or `ssh-keygen -f ~/.ssh/new`
* Copy key to the remote host `ssh-copy-id -p 2222 <username>@<remote_host>`  or `ssh-copy-id -i ~/.ssh/*.pub -p 2222 <username>@<remote_host>`
* login without password `ssh -p 2222 username@remote_host`
* Go to -> `sudo nano /etc/ssh/sshd_config` and change to `PasswordAuthentication no`
* !!!! for MAC -> `https://osxfuse.github.io/` install macFUSE
* !!!! for MAC -> `brew install --cask macfuse`
* use sshfs `sshfs -o ssh_command='ssh -i path/to/keyfile/id_rsa.2' <username>@<remote_host>:/home/myuser /Users/mak/Desktop/testfolder`
* unmounted `umount /path/to/mount/point`
