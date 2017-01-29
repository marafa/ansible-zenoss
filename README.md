# Zenoss Installer using Ansible

Uses Ansible to install Zenoss 5.1 core. 

# Documentation
 * Installation Guide: https://www.zenoss.com/sites/default/files/documentation/Zenoss_Resource_Manager_Installation_Guide_r5.1.1_d1052.16.060.pdf
 * Configuration Guide: https://www.zenoss.com/sites/default/files/documentation/Zenoss_Resource_Manager_Configuration_Guide_r5.1.1_d1042.16.061.1.pdf
 * Ansible Docs: http://docs.ansible.com/


## Minimum Recommended Server
The hosts in the default resource pool should meet the following, minimum
requirements:
 * OS RHEL/CentOS 7.1
 * 4 CPU cores (64-bit only; real or virtual)
 * 20GB RAM
 * 1 network interface controller (must support TCP/IP)
 * The network latency among all hosts in a resource pool should be less than 5 milliseconds
 * Local storage is recommended, and SAN storage is supported
 * Minimum Local storage 30GB x 2 disks

## Installation

Clone this repo:

    $ git clone https://github.com/marafa/ansible-zenoss.git
    $ cd ansible-zenoss

Make sure NTP is running, this includes checking local and site firewalls. To check:

	$ ntpstat
If your output resembles the output below, then NTP is working:

	synchronised to NTP server (12.34.56.78) at stratum 3 ....

Modify your hosts inventory/file to put your Zenoss server's IP

Verify you can ssh to your Zenoss host using ssh keys AND that user can sudo without a password

## Notes
 * The speed of the installation is dependent on your internet connection. It can take an hour or more.

## To use

Modify the variables group_vars/all.yml to suit your environment

Run ansible with following:

    ansible-playbook -i hosts playbook.yml 

To test a role
(This is useful when you want to verify your server meets Zenoss specs)

    ansible-play -i hosts -l localhost test_role.yml -e "ROLE=installation_checks"
