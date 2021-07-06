Vagrant

Npt working anymore... prompted for pwd on Reload, Halt, Up etc.

Sources:

https://gist.github.com/berkayunal/ad5a4357a12833495195c5be2c622dde
https://gist.github.com/elvetemedve/c3574e5cadbcddef0b85

https://webcache.googleusercontent.com/search?q=cache:F3ky-A_7Vb0J:https://www.rubydoc.info/gems/vagrant-hostsupdater+&cd=1&hl=en&ct=clnk&gl=us
https://www.jeffgeerling.com/blogs/jeff-geerling/better-vagrant-development-workflow

https://github.com/agiledivider/vagrant-hostsupdater
https://gist.github.com/beddari/1472018

VAGRANT_HOSTS_ADD = /bin/sh -c 'echo "*" >> /etc/hosts'


    sudo visudo

```
Cmnd_Alias VAGRANT_EXPORTS_ADD = /usr/bin/tee -a /etc/exports
Cmnd_Alias VAGRANT_NFSD = /sbin/nfsd restart
Cmnd_Alias VAGRANT_EXPORTS_REMOVE = /usr/bin/sed -E -e /*/ d -ibak /etc/exports
# Allow Vagant to manage hosts file.
Cmnd_Alias VAGRANT_HOSTS_ADD = /bin/sh -c echo "*" >> /etc/hosts
Cmnd_Alias VAGRANT_HOSTS_REMOVE = /usr/bin/sed -i -e /*/ d /etc/hosts
%admin ALL=(root) NOPASSWD: VAGRANT_EXPORTS_ADD, VAGRANT_NFSD, VAGRANT_EXPORTS_REMOVE, VAGRANT_HOSTS_ADD, VAGRANT_HOSTS_REMOVE
```

```
Cmnd_Alias VAGRANT_EXPORTS_ADD = /usr/bin/tee -a /etc/exports
Cmnd_Alias VAGRANT_NFSD = /sbin/nfsd restart
Cmnd_Alias VAGRANT_EXPORTS_REMOVE = /usr/bin/sed -E -e /*/ d -ibak /etc/exports
# Allow Vagant to manage hosts file.
Cmnd_Alias VAGRANT_HOSTS_ADD = /bin/sh -c 'echo "*" >> /etc/hosts'
Cmnd_Alias VAGRANT_HOSTS_REMOVE = /usr/bin/sed -i -e /*/ d /etc/hosts
%admin ALL=(root) NOPASSWD: VAGRANT_EXPORTS_ADD, VAGRANT_NFSD, VAGRANT_EXPORTS_REMOVE, VAGRANT_HOSTS_ADD, VAGRANT_HOSTS_REMOVE
```
