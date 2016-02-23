IRCD
=========

The IRCD role deploys the IRCD IRC2 server, its documentation can be found here: https://launchpad.net/ubuntu/+source/ircd-irc2
Currently it supports deployment on Debian-based distributions only. Tested on Ubuntu 14.04.

Requirements
------------

No requirements.

Role Variables
--------------

ircd_motd
A string of text to be embedded into the servers message of the day (motd) file.
Default value: 'How now brown cow?'

ircd_admin_name
A string containing the name of the administrator, eg 'John Smith'
Default value: 'Admin Smith'

ircd_admin_email
A string containing the email address of the administrator
Default value: 'admin.smith@local.host'

ircd_port
Which port number the server should listen on
Default value: 6667

ircd_network_name
A string containing the IRC network name to which the server belongs, eg 'Interlinks IRC'
Default value: 'local network'

ircd_geo_location
A string containing a description of, geographically, where the server resides, eg 'San Francisco, California, USA'
Default value: 'Earth'


Dependencies
------------

No dependendencies

Example Playbook
----------------

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

License
-------

MIT

Author Information
------------------

jpbarto <jason.p.barto@gmail.com>
