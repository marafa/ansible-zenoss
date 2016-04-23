# Zenoss Installer using Ansible

Uses Ansible to install Zenoss 5.1 core. 

# Documentation
 * Installation Guide: https://www.zenoss.com/sites/default/files/documentation/Zenoss_Resource_Manager_Installation_Guide_r5.1.1_d1052.16.060.pdf
 * Configuration Guide: https://www.zenoss.com/sites/default/files/documentation/Zenoss_Resource_Manager_Configuration_Guide_r5.1.1_d1042.16.061.1.pdf
 * Ansible Docs: http://docs.ansible.com/


## Minimum Recommended Server
The hosts in the default resource pool should meet the following, minimum
requirements:
 * 4 CPU cores (64-bit only; real or virtual)
 * 20GB RAM
 * 1 network interface controller (must support TCP/IP)
 * The network latency among all hosts in a resource pool should be less than 5 milliseconds
 * Local storage is recommended, and SAN storage is supported
 * Minimum Local storage 30GB RHEL, 60GB Ubuntu
 * OS RHEL/CentOS 7.1



## Installation

Clone this repo:

    $ git clone https://github.com/marafa/ansible-zenoss.git
    $ cd ansible-zenoss

Make sure NTP is running, on AWS make sure UDP port 123 is open outbound. To check:

	$ ntpstat
If your output resembles the output below, then NTP is working:

	synchronised to NTP server (12.34.56.78) at stratum 3 ....

Modify your hosts file to put your Zenoss server's IP

Verify you can ssh to your Zenoss host using ssh keys AND that user can sudo without a password

## To use

Modify the variables section in playbook.yml to suit your environment

Run ansible with following:

    ansible-playbook -i hosts playbook.yml 

To test a role

    ansible-play -i hosts -l localhost test_role.yml -e "ROLE=installation_checks"
