Role Name
=========

This role sets up an environment for Doom's multiplayer ports, such as [Zdaemon](https://zdaemon.org), [Zandronum](https://zandronum.com), and [Odamex](https://odamex.net). 

By default, this role will:
* Create all required subfolders
* Install Zdaemon
* Install Zandronum
* ~~Install Odamex~~ (TODO)
* ~~Install a default bash template~~ (TODO)

Requirements
------------

This role requires to create a dedicated Linux user for safety reasons. This role uses `doomuser` by default so you should do the same, but you can adapt it to your likings. See Role variables below for more information.

Role Variables
--------------

All the variables used in this role are found in `defaults/main.yml`.

```
doom_user: "doomuser"
```

This is the user that will receive all the data for the Doom environment.

```
doom_main_directory: /home/{{ doom_install_user }}/doom
```

This is the main folder that will be set-up for the Doom environment.

```
doom_waddir_create: true
doom_waddir: "{{ doom_main_directory }}/wads"
```

This is the directory that will be used for searching all the WADs for the ports. Set `doom_waddir_create` to false if you do not want this feature.

```
doom_zdaemon_install: true
doom_zdaemon_install_directory: "{{ doom_main_directory }}/zdaemon"
```

Set it to false if you do not want to install ZDaemon. The second variable is where the executable will be installed.

```
zdaemon_latest_version: "zserv11022_linux26.tgz"
zdaemon_extractdir: "zserv110_bin"
```

**These variables are for advanced-users only**! In case this role wasn't updated for a long time, you can still set these to manually update your ZDaemon executables, along with the directory name it uses after extracting. You can see the latest releases [here](https://downloads.zdaemon.org/).

```
doom_install_zandronum: true
doom_install_zandronum_directory: "{{ doom_main_directory }}/zandronum"
```

Set it to false if you do not want to install Zandronum. The second variable is where the executable will be installed.

```
doom_zandronum_release: "3.1"
```
**This variable is for advanced-users only**! In case this role wasn't updated for a long time, you can still set these to manually get the latest Zandronum executables. You can see the latest releases [here](https://zandronum.com/downloads/) for reference.


Dependencies
------------

None...

Example Playbook
----------------

**THIS IS NOT DONE YET...** So expect the default data created...

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }
```

License
-------

BSD

Author Information
------------------

This role is created by [Ch0wW](https://ch0ww.fr). 
