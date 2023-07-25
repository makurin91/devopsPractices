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


# Install Cloud-init
* Update `apt-get update`
* Install cloud init `apt-get install cloud-init`