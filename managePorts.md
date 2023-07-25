# Ufw

* install ufw `apt install ufw`
* allow all outgoing traffic `ufw default allow outgoing`
* deny incoming traffic `ufw default deny incoming`
* allow ssh 22 `ufw allow ssh`
* allow 80  `ufw allow 80/tcp`
* allow 443  `ufw allow 443/tcp`
* activate ufw `ufw enable`
* rules list `ufw status`