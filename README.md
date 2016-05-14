# ansible-role-ircd

[![Build Status](https://travis-ci.org/rooland-provisioning/ansible-ircd.svg?branch=master)](https://travis-ci.org/rooland-provisioning/ansible-ircd)

The IRCD role deploys the IRCD Hybrid server, its documentation can be found here: http://www.ircd-hybrid.org/

Currently the role supports deployment on Debian-based distributions only. Tested on Ubuntu Trusty and Precise.

## Install

```sh
ansible-galaxy install rooland-provisioning.ircd
```

##Requirements

No requirements.

## Role Variables and Defaults

- **ircd.motd**         (_required_): Text to be embedded into the servers message of the day (motd) file
- **ircd.admin_name**   (_required_): A string containing the name of the administrator, eg 'John Smith'
- **ircd.admin_email**  (_required_): A string containing the email address of the administrator
- **ircd.port**         (_required_): Which port number the server should listen on
- **ircd.network_name** (_required_): A string containing the IRC network name to which the server belongs, eg 'Interlinks IRC'
- **ircd.geo_location** (_required_): A string containing a description of, geographically, where the server resides, eg 'San Francisco, California, USA'
- **ircd.fqdn**         (_required_): Domain name on which IRC server will be reachable

## Dependencies

No dependendencies

## Example Playbook

```yaml
    - hosts: ircd_servers
      roles:
         - rooland-provisioning.ircd

      vars:
        ircd:
          motd: Confucius say, if you think you will sum up your whole life on this little bit of paper, you are crazy.
          port: 6667
          network_name: Local Network
          admin_name:   Admin Smith
          admin_email:  admin@local.host
          geo_location: Earth
```

## License

[MIT](LICENSE)

## Author Information

Jason Barto - jason.p.barto@gmail.com (original author)

### Mailo Svetel

- Usually idling on Freenode as lipoqil
- http://him.rlnd.cz
