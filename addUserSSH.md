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
* add ssh pub key `echo "Pub_key" >> authorized_keys`


# Create ssh
`ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f /path/to/your_keyfile`
`ssh-keygen -t rsa -b 4096 -f /path/to/your_keyfile`

# Add known_hosts
`touch ~/.ssh/known_hosts`
`ssh-keyscan hostname >> ~/.ssh/known_hosts`