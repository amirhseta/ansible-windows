## [![Nabla](https://debops.org/images/debops-small.png)](https://github.com/AlbanAndrieu) alban_andrieu_windows

<!-- This file was generated by Ansigenome. Do not edit this file directly but
     instead have a look at the files in the ./meta/ directory. -->

[![License](http://img.shields.io/:license-apache-blue.svg?style=flat-square)](http://www.apache.org/licenses/LICENSE-2.0.html)
[![Branch](http://img.shields.io/github/tag/AlbanAndrieu/ansible-windows.svg?style=flat-square)](https://github.com/AlbanAndrieu/ansible-windows/tree/master)
[![Donate](https://img.shields.io/gratipay/AlbanAndrieu.svg?style=flat)](https://www.gratipay.com/~AlbanAndrieu)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-alban.andrieu.windows-660198.svg?style=flat)](https://galaxy.ansible.com/alban.andrieu/windows)
[![Platforms](http://img.shields.io/badge/platforms-windows-lightgrey.svg?style=flat)](#)
[![Flattr this git repo](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=AlbanAndrieu&url=https://github.com/AlbanAndrieu/ansible-windows&title=ansible-windows&language=en_GB&tags=github&category=software)

Goal of this project is to launch ansible script using [pywinrm](https://pypi.python.org/pypi/pywinrm).
A VagrantFile is downloading a windows 2012 server VM that will be hosted on VirtualBox.
Then we are launching Ansible script in order to set up this VM.

VM was taken from
------------------

https://vagrantcloud.com/opentable/boxes/win-2012r2-standard-amd64-nocm/versions/1.0.0/providers/virtualbox.box

### Requirements

On Ubuntu, where VirtualBox and Vagrant are installed, do not forge to do the following
```
sudo pip install https://github.com/diyan/pywinrm/archive/df049454a9309280866e0156805ccda12d71c93a.zip --upgrade
```

It is working with the following version :

# Os is an Ubuntu 12

python -V
```
#Python 2.7.3
```
pip -V
```
#pip 1.4.1 from /usr/local/lib/python2.7/dist-packages (python 2.7)
```

VBoxManage --version
```
#4.3.28r100309
```

vagrant --version
```
#Vagrant 2.3.0.0
```

vagrant plugin list
```
#winrm (1.1.3)
#vagrant-login (1.0.1, system)
#vagrant-share (1.1.0, system)
```

ansible --version
```
#ansible 1.7.2
```

On the windows VM :

Try :

[Configure remoting](https://github.com/AlbanAndrieu/ansible-windows/blob/master/files/ConfigureRemotingForAnsible.ps1)

```
powershell -File ConfigureRemotingForAnsible.ps1 
\\powershell -File ConfigureRemotingForAnsible.ps1 -ForceNewSSLCert
```

[Configure user for remoting](https://github.com/AlbanAndrieu/ansible-windows/blob/master/files/ConfigureRemotingUserForAnsible.ps1)

```
powershell -File ConfigureRemotingUserForAnsible.ps1 
```

[Upgrade PowerShell](https://github.com/AlbanAndrieu/ansible-windows/blob/master/files/upgrade_to_ps3-1.ps1)


```
powershell -File upgrade_to_ps3-1.ps1
```

[Install PowerShell]()

```
@powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%systemdrive%\chocolatey\bin
cinst powershell
```

```
choco install powershell
choco upgrade powershell
```

[Disable password](http://www.tenniswood.co.uk/technology/windows/how-to-disable-password-expiration-for-windows-server-2012/)


### Installation

This role requires at least Ansible `v2.3.0.0`. To install it, run:

Using `ansible-galaxy`:
```shell
$ ansible-galaxy install alban.andrieu.windows
```

Using `arm` ([Ansible Role Manager](https://github.com/mirskytech/ansible-role-manager/)):
```shell
$ arm install alban.andrieu.windows
```

Using `git`:
```shell
$ git clone https://github.com/AlbanAndrieu/ansible-windows.git
```

### Documentation

<!---
More information about `alban.andrieu.windows` can be found in the
[official alban.andrieu.windows documentation](https://docs.debops.org/en/latest/ansible/roles/ansible-windows/docs/).
-->


### Role variables

List of default variables available in the inventory:

```YAML
windows_enabled: yes                       # Enable module

#ansible_ssh_user: vagrant
#ansible_ssh_pass: vagrant
#target port
#ansible_ssh_port: 5986
#local port
#ansible_ssh_port: 55985
ansible_connection: winrm
```


### Detailed usage guide

Run the following command :

`ansible-playbook -i hosts -c local -v windows.yml -vvvv --ask-sudo-pass | tee setup.log`


### Authors and license

`alban_andrieu_windows` role was written by:

- [Alban Andrieu](nabla.mobi) | [e-mail](mailto:alban.andrieu@free.fr) | [Twitter](https://twitter.com/AlbanAndrieu)

- License: [GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)

Copyright (c) 2017 [Alban Andrieu](https://alban.andrieu.com/)

### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/AlbanAndrieu/ansible-windows/issues)!

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

***

This role is part of the [Nabla](https://github.com/AlbanAndrieu) project.
README generated by [Ansigenome](https://github.com/nickjj/ansigenome/).
