
Ansible Scripts to generate and deploy Aruba OS CX Configurations.

Play uses Roles and Variable files to build large configuration, with BGP, IPv4 and IPv6.

currently 2 main plays

CoreSwitchBuild.yml - uses the CoreSwitch roles to build based on a Jinja2 template
DeployConfig.yml - uses the CoreSwitch roles to build config, the uses the Aruba CX modules to run a tftp command on the switch to upload, followed by an error log output.

To use each, enter the variables for the switches within the vars file,


In development

1) Updating the time and date on the switch
 - clock datetime {{ ansible_date_time.date }} {{ ansible_date_time.time }}
2) Enable checkpoint before configurtion upload, check for connectivity following upload and confirm checkpoint


The following base configurtion on

user admin group administrators password plaintext Aruba123
ssh server vrf mgmt
interface mgmt
    no shutdown
    ip static <IP Address>
https-server rest access-mode read-write
https-server vrf mgmt


Cited Resource
    # https://github.com/aruba/aoscx-ansible-role
    # http://www.nettinkerer.org/using-ansible-to-create-config-files/
    # https://github.com/dmahler/ansible-template
    # https://www.bo-yang.net/2015/08/31/centos7-install-tftp-server
