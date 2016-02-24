IRCD
=========

[![Build Status](https://travis-ci.org/jpbarto/ansible-ircd.svg?branch=master)](https://travis-ci.org/jpbarto/ansible-ircd)

The IRCD role deploys the IRCD IRC2 server, its documentation can be found here: https://launchpad.net/ubuntu/+source/ircd-irc2
Currently it supports deployment on Debian-based distributions only. Tested on Ubuntu 14.04.

Requirements
------------

No requirements.

Role Variables
--------------

```yaml
# text to be embedded into the servers message of the day (motd) file
ircd_motd: how now brown cow

# A string containing the name of the administrator, eg 'John Smith'
ircd_admin_name: Admin Smith

# A string containing the email address of the administrator
ircd_admin_email: admin.smith@local.host

# Which port number the server should listen on
ircd_port: 6667

# A string containing the IRC network name to which the server belongs, eg 'Interlinks IRC'
ircd_network_name: local network

# A string containing a description of, geographically, where the server resides, eg 'San Francisco, California, USA'
ircd_geo_location: 'Earth'
```

Dependencies
------------

No dependendencies

Example Playbook
----------------

```yaml
    - hosts: ircd_servers

      become: true
      become_user: root
      become_method: sudo

      vars:
        ircd_motd: Confucius say, if you think you will sum up your whole life on this little bit of paper, you are crazy.
        ircd_network_name: Local Network
        ircd_port: 6667
        ircd_admin_name: Admin Smith
        ircd_admin_email: admin@local.host
        ircd_geo_location: Earth

      pre_tasks:
        - name: update apt cache
          apt: update_cache=yes

      roles:
         - { role: jpbarto.ircd }
```

License
-------

[MIT](LICENSE)

Author Information
------------------

Jason Barto - jason.p.barto@gmail.com
