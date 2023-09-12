
* Create folder in the shared directory `sudo mkdir /srv/shared_folder`
* Add folder for all users `sudo bash -c 'for user in /home/*; do ln -s /srv/shared_folder "$user/shared_folder"; done'`



* Remove folder for all users `sudo bash -c 'for user in /home/*; do rm "$user/shared_folder"; done'`
* Remove main folder `sudo rm -r /srv/shared_folder`