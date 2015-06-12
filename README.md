# ansible-plugin-profile
Ansible plugin for timing tasks. Patches welcome.

## Usage

Make a directory called `callback_plugins` next to your playbook and put `profile_tasks.py` inside of it.

```shell
    mkdir callback_plugins
    cd callback_plugins
    wget https://raw.githubusercontent.com/aioue/ansible-plugin-profile/master/callback_plugins/profile_tasks.py
```

Now, run your playbook as normal.

## Features

### Tasks

Ongoing timing of each task as it happens.

Format:
`<start timestamp> (<time of previous task>) <current elapsed execution time>`

```shell
TASK: [ensure messaging security group exists] ********************************
Thursday 11 June 2016  22:50:53 +0100 (0:00:00.721)       0:00:05.322 *********
ok: [localhost]

TASK: [ensure db security group exists] ***************************************
Thursday 11 June 2016  22:50:54 +0100 (0:00:00.558)       0:00:05.880 *********
changed: [localhost]
```

### Play Recap

Recap includes ending timestamp, total time and sorted list of longest running tasks.  
No more wondering how old the results in a terminal windows are.

```shell
   ansible <args here>
   <normal output here>
   PLAY RECAP ******************************************************************** 
   Thursday 11 June 2016  22:51:00 +0100 (0:00:01.011)       0:00:43.247 *********
   ===============================================================================
   really slow task  | Download project packages----------------------------11.61s
   security | Really slow security policies----------------------------------7.03s
   common-base | Install core system dependencies----------------------------3.62s
   common | Install pip------------------------------------------------------3.60s
   common | Install boto-----------------------------------------------------3.57s
   nginx | Install nginx-----------------------------------------------------3.41s
   serf | Install system dependencies----------------------------------------3.38s
   duo_security | Install Duo Unix SSH Integration---------------------------3.37s
   loggly | Install TLS version----------------------------------------------3.36s
```
