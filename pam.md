# Pluggable Authentication Modules


`/etc/apt/source.list`
`deb http://deb.debian.org/debian bullseye-proposed-updates main contrib non-free`

!!! IMPORTANT install `sudo apt -y install libpam-pwquality libpwquality-tools`


* edit `sudo nano /etc/pam.d/common-password`
* add `password requisite pam_pwquality.so retry=3 minlen=8 lcredit=-1 ucredit=-2 dcredit=-2 ocredit=-1`
* add for remember 4 times pass `password     requisite    pam_unix.so remember=4`


* edit `sudo nano /etc/pam.d/common-account`
* add to common-account `account    required pam_faillock.so`
* block user after 5 failed auth -> edit`sudo nano /etc/pam.d/common-auth`
* add `auth required pam_faillock.so preauth deny=5 unlock_time=120`
* commented `auth   requisite                       pam_deny.so`
* add `auth [default=die] pam_faillock.so authfail`
* go to `nano /etc/security/faillock.conf`
* change deny to 5
* check locked user `faillock --user some`
* reset locked user `faillock --user some --reset`

* password life 90 days 



* sshd restart `sudo systemctl restart sshd`
* pam restart `sudo systemctl restart systemd-logind`




