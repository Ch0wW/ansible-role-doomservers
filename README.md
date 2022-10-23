ansible-role-doomservers
========================

This role sets up an environment for Doom's multiplayer ports, such as [Zdaemon](https://zdaemon.org), [Zandronum](https://zandronum.com), and [Odamex](https://odamex.net) in a Linux environment.

It also creates a server template so that you can suit it to your needs.

**By default, all port installations are set to false! You'll have to manually set the variables. See the examples below.**

Requirements
------------

This role requires to create a dedicated Linux user for safety reasons. This role uses `doomuser` by default, but you can adapt it to your likings. See `Role variables` below for more information.

If you intend to include Odamex, you'll require `CMake` version 3.13 or later. You will also need the `community.general.github_release` collection to retrieve automatically the latest release version for compilation, as Odamex is the only port whose pre-built binaries are not available on Linux.

You can install the collection using this command:

```bash
ansible-galaxy collection install community.general
```

Role Variables
--------------

All the variables used in this role are found in `defaults/main.yml`.

```yml
doom_user: "doomuser"
```

This is the user that will receive all the data for the Doom environment.

```yml
doom_main_directory: /home/{{ doom_user }}/doom
```

This is the main folder that will be set-up for the Doom environment.

```yml
doom_waddir_create: true
doom_waddir: "{{ doom_main_directory }}/wads"
```

This is the directory that will be created & used for searching all the WADs for the ports. Set `doom_waddir_create` to `false` if you do not want this feature.

```yml
doom_zdaemon_install: false
doom_zdaemon_install_directory: "{{ doom_main_directory }}/zdaemon"
```

Set it to `true` if you want to install ZDaemon. The second variable is where the executable will be installed.

```yml
zdaemon_latest_version: "zserv11022_linux26.tgz"
zdaemon_extractdir: "zserv110_bin"
```

**These variables are for advanced-users only**! In case this role wasn't updated for a long time, you can still set these to manually update your ZDaemon executables, along with the directory name it uses after extracting. You can see the latest releases [here](https://downloads.zdaemon.org/).

```yml
doom_install_zandronum: false
doom_install_zandronum_directory: "{{ doom_main_directory }}/zandronum"
```

Set it to `true` if you want to install Zandronum. The second variable is where the executable will be installed.

```yml
doom_zandronum_release: "3.1"
```

**This variable is for advanced-users only**! In case this role wasn't updated for a long time, you can still set these to manually get the latest Zandronum executables. You can see the latest releases [here](https://zandronum.com/downloads/) for reference.

```yml
doom_install_odamex: false
doom_install_odamex_directory: "{{ doom_main_directory }}/odamex"
```

Set it to `true` if you want to install Zandronum. The second variable is where the executable will be installed.

Dependencies
------------

None...Example Playbook
----------------

This example will install *__the wads directory and zdaemon__* for user `doomuser`. Zandronum and Odamex will not be installed.

```yml
    - hosts: servers
      roles:
         - ch0ww.doomservers

      vars:
        - doom_user: "doomuser"
        - doom_waddir_create: true
        - doom_zdaemon_install: true
        - doom_zandronum_install: false
        - doom_odamex_install: false
```
License
-------

BSD

Author Information
------------------

This role is created by [Ch0wW](https://ch0ww.fr).
