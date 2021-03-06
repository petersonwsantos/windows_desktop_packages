[![Build Status](https://travis-ci.org/petersonwsantos/windows_desktop_packages.svg?branch=master)](https://travis-ci.org/petersonwsantos/windows_desktop_packages)
[![GitHub release](https://img.shields.io/github/release/petersonwsantos/windows_desktop_packages.svg)](https://github.com/petersonwsantos/windows_desktop_packages/releases)
[![GitHub issues](https://img.shields.io/github/issues/petersonwsantos/windows_desktop_packages.svg)](https://github.com/petersonwsantos/windows_desktop_packages/issues)


Role Windows Desktop Packages
==============================

This Ansible Role install programs on the network's desktops using the chocolatey package manager.

<img src="https://www.pivotaltracker.com/images/v7/logos/logo_main.png" width="120">

- **Project - Ansible Roles:** https://www.pivotaltracker.com/n/projects/2102371

- **Story:** https://www.pivotaltracker.com/story/show/150707627


Requirements
------------
Test your Ansible configuration with winrm.  

**[root@ansible ]#** ansible windows -m win_ping
```
192.168.0.116 | SUCCESS => {
 "changed": false,
 "ping": "pong"
}
```
    
Role Variables
--------------

The Variables for this role must be defined in 'default/main.yml' 'vars/main.yml' or '/etc/ansible/groupvars/'.

**windows_desktop_packages_version** : For instalation packages on specific version.
Ex: 
```
windows_desktop_packages_version:
  - notepadplusplus:
    name: notepadplusplus
    state: present
    version: 7.4.2
    force: True
  - googlechrome:
    name: googlechrome
    state: present
    version: 60.0.3112.113
    force: false
```

**windows_desktop_packages_latest**: For instalation packages on latest version
Ex:
```
windows_desktop_packages_latest:
  - chocolatey
  - firefox
  - jre8
  - conemu
  - 7zip.install
  - openoffice
  - cdburnerxp
  - adobereader
  - ccleaner
  - dotnet4.0
  - flashplayerplugin
  - vlc
  - pdfcreator
  - wget
```

Chocolatey
--------------------

https://chocolatey.org/packages

<a href="https://feeds.feedburner.com/chocolatey" title="Subscribe to package updates" rel="alternate" type="application/rss+xml"><img src="https://www.feedburner.com/fb/images/pub/feed-icon32x32.png" alt="RSS" style="border:0" />&nbsp;<span> Subscribe Chocolatey to updates</span></a>


Dependencies
------------

Windows 7 or higher

Example Playbook
----------------

**[root@ansible ]#** vi site.yml
```
    - name: apply common configuration to windows nodes
      hosts: windows

      roles:
        - windows_desktop_packages
```

**[root@ansible ]#** ansible-galaxy install petersonwsantos.windows_desktop_packages

**[root@ansible ]#** tree /etc/ansible
```
    /etc/ansible
        ├── group_vars
        │   ├── all.yml
        │   └── windows.yml
        ├── hosts
        ├── roles
        │   ├── petersonwsantos.windows_desktop_packages
        │   │   ├── defaults
        │   │   │   └── main.yml
        │   │   ├── handlers
        │   │   │   └── main.yml
        │   │   ├── meta
        │   │   │   └── main.yml
        │   │   ├── README.md
        │   │   ├── tasks
        │   │   │   └── main.yml
        │   │   ├── tests
        │   │   │   ├── inventory
        │   │   │   └── test.yml
        │   │   ├── Vagrantfile
        │   │   └── vars
        │   │       └── main.yml
        └── site.yml
```


 
**[root@ansible ]#** ansible-playbook  site.yml 

License
-------

BSD

Author Information
------------------

Peterson W santos
