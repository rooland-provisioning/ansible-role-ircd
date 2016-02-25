IRCD
=========

[![Build Status](https://travis-ci.org/jpbarto/ansible-ircd.svg?branch=master)](https://travis-ci.org/jpbarto/ansible-ircd)

The IRCD role deploys the IRCD Hybrid server, its documentation can be found here: http://www.ircd-hybrid.org/
Currently the role supports deployment on Debian-based distributions only. Tested on Ubuntu Trusty and Precise.

Install
-------

```sh
ansible-galaxy install jpbarto.ircd
```

Requirements
------------

No requirements.

Role Variables and Defaults
---------------------------

```yaml
# text to be embedded into the servers message of the day (motd) file
ircd_motd: Confucious say, if you think you will sum up your whole life on this little bit of paper, you are crazy

# A string containing the name of the administrator, eg 'John Smith'
ircd_admin_name: Admin Smith

# A string containing the email address of the administrator
ircd_admin_email: admin@local.host

# Which port number the server should listen on
ircd_port: 6667

# A string containing the IRC network name to which the server belongs, eg 'Interlinks IRC'
ircd_network_name: Local Network

# A string containing a description of, geographically, where the server resides, eg 'San Francisco, California, USA'
ircd_geo_location: Earth
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
