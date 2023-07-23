# Adding user [Linux]

* Create user `sudo adduser username`
* Give superuser privileges `sudo usermod -aG sudo username`
* Open ssh config `sudo nano /etc/ssh/sshd_config` and enable PubkeyAuthentication, PasswordAuthentication. Disable - PermitRootLogin.
* Restart ssh service `sudo service ssh restart`
* Check status `sudo service ssh status`


# Add ssh access for new user

* create .ssh `mkdir -p /home/username/.ssh`
* `chmod 700 /home/username/.ssh`
* create auth file `touch /home/username/.ssh/authorized_keys`
* `chmod 600 /home/username/.ssh/authorized_keys`
* add ssh pub key `echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQC5Uk6FglNkYw7dDdnQGl2ZSAGrSxEvvUGw2kU0i8BfmaVE7X0pBocfdAHSDgsks3+zYCYgb6ZdiTCPD49Hv63cI5Ue8SjhjhYjyNRfmsXjKx8J87b9NA2IR/R/bf2FPHeF0XSEAU7rzZciLz8WjkYMNPzDYP6j4yB8BIYgYj7nbcaAv0bv6GyJaCl1OCY7iMCVVPDgN6FsSyoTYi7pJxmJ2qtqr8QORVaZUFJvj5J4mZ8PdFYMjxdYh/9xWKqoScWXBY9zAMWqpBjQBU2a91Yyq7N86cfpaHANGMxELrdHWLJElT2pubUdgm8AfqaXpvq7T82SD5/NG6gAhJsu86nTA2kni+Rym0f8ce6I62pz2kw2cn3NwQPWn2VExhsnEHg8KJnl3nGCZK7jV9MoSNe4slNhNIaMZn22ykdLUwA0tVTmdehmHU3KpKLY+rbQErRD7zQtxn/v+FFfMBS4h4bGIQA2iIBt6TA8PcMMbvokivFQ2Igs9EM9tKBGkxz1d1WUnDoG/HUhVEhX2aVA+6cwNJwoIq/3FV83gUsVOTd6Rw/b1f71qjje0cOUmRd8xWS3L3oYzmdEM5QW/KWDSroLv6CC9mGqf3wC0XQszSp2dc545+zJGZm5H/13jOtSJE/Ej51Kbv2BB2Feu0tkk48jizJsNplvLyZgJWsXBB2BQQ== mak@maks-Air.localdomain
" >> authorized_keys`


# Create ssh
`ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f /path/to/your_keyfile`
`ssh-keygen -t rsa -b 4096 -f /path/to/your_keyfile`