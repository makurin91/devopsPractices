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

  


# Install Proxmox Debian 12
`https://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_12_Bookworm`


# Install ISO for proxmox
* connect as a root user to the proxmox machine
* `cd /var/lib/vz/template/iso/`
* `wget {link for downloading ISO}`

# Get Turnkey Jenkins template container

`pveam update`
`pveam available`
`pveam available | grep jenkins`
`pveam download local {link}`

# Ufw

* install ufw `apt install ufw`
* allow all outgoing traffic `ufw default allow outgoing`
* deny incoming traffic `ufw default deny incoming`
* allow ssh 22 `ufw allow ssh`
* allow 80  `ufw allow 80/tcp`
* allow 443  `ufw allow 443/tcp`
* activate ufw `ufw enable`
* rules list `ufw status`