

* перевірити скільки і яких шелів встановлено в системі `cat /etc/shells`
* Перевірити який поточний шел `ps -p $$`
* Перевірити вміст змінної SHELL `echo $SHELL`
* Перевірити поточний шел командою readlink `readlink -f /proc/$$/exe`
* Перевірити поточну версію шелла `echo $BASH_VERSION`
* Встановити bash поточним дефолтним шелом `chsh -s /bin/bash`
* Перевірити поточний шел перевіркою поточних змінних оточення `echo $0`
* compare `printenv | grep SSH_CONNECTION && printenv | grep SSH_TTY`
* Перевірити змінні оточення командою env `env`
