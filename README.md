# Branch Organization

## Git Flow suggests a standard branch organization in a repository:

* main: The main branch contains stable, production-ready code. All merges into main should be thoroughly tested and
  verified.
* develop: The develop branch is the general development branch. It contains the latest changes and new features that
  are
  not yet ready for production.
* feature: For each new feature or task, a separate branch is created branching off from develop. After completing the
  work, the feature branch is merged into develop.
* release: Release branches are used for preparing new releases of the project. They are created before publishing a new
  version and can be fixed or enhanced before final merging into main and develop.
* hotfix: Hotfix branches are used for quickly fixing issues in the production environment. They branch off from main,
  fix
  the problem, and then merge back into both main and develop.



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
* add ssh pub key `echo "PUB_KEY" >> /home/username/.ssh/authorized_keys`


# Create ssh
`ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f /path/to/your_keyfile`
`ssh-keygen -t rsa -b 4096 -f /path/to/your_keyfile`


# Install Proxmox Debian 12
`https://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_12_Bookworm`