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
* Check init logs output `cat /var/log/cloud-init-output.log`
* Check init logs `cat /var/log/cloud-init.log`

# Create ubuntu template
* Create VM with this settings: kvm64, Delete volume, minimum RAM
* ubuntu releases `https://cloud-images.ubuntu.com/minimal/releases/jammy/release/`
* debian releases `https://cloud.debian.org/images/cloud/bullseye/latest/`
* centos releases `https://cloud.centos.org/centos/7/images/`
* redhat releases `https://access.redhat.com/downloads/`
* download cloud ubuntu img `wget https://cloud-images.ubuntu.com/minimal/releases/jammy/release/ubuntu-22.04-minimal-cloudimg-amd64.img`
* download cloud debian img `wget https://cloud.debian.org/images/cloud/bullseye-backports/latest/debian-11-backports-genericcloud-amd64.qcow2`
* `qm set 900 --serial0 socket --vga serial0`
* `mv ubuntu-22.04-minimal-cloudimg-amd64.img ubuntu-22.04.qcow2`
* `qemu-img resize ubuntu-22.04.qcow2 32G`
* `qm importdisk 900 ubuntu-22.04.qcow2 local`
* Go to VM -> Hardware and add unuses disk, click Discard and Advanced -> SSD emul
* Go to Options and change Boot options: Enable disk and dragondrop to 2nd posititon
* Add Cloud init -> Hardware add
* Then add all info to the Cloud init