

* Filesystem list `df -h`
* This will give you a list of all the storage devices on your system `lsblk -a`
* Используйте команду "growpart", чтобы расширить раздел. `sudo growpart /dev/<disk> <partition>`
* После расширения раздела вам нужно изменить размер файловой системы `sudo resize2fs /dev/<disk><partition>`
