# Zenoss Installer using Ansible

Uses Ansible to install Zenoss 5.0 core. 

Detailed Instructions under: (http://www.zenoss.com/sites/default/files/documentation/Zenoss_Core_Installation_Guide_r5.0.x_d1051.15.120.pdf)

Ansible Docs: http://docs.ansible.com/


## Minimum Recommended Server
The hosts in the default resource pool should meet the following, minimum
requirements:
■ 4 CPU cores (64-bit only; real or virtual)
■ 20GB RAM
■ 1 network interface controller (must support TCP/IP)
■ The network latency among all hosts in a resource pool should be less than 5 milliseconds
■ Local storage is recommended, and SAN storage is supported
■ Minimum Local storage 30GB RHEL, 60GB Ubuntu
■ OS RHEL/CentOS 7.1, Ubuntu 14.04LTS (I'm testing AWS RHEL 7.1)



## Installation

Clone this repo:

    $ git clone https://github.com/seizadi/ansible-zenoss.git
    $ cd ansible-zenoss

Make sure NTP running, on AWS make sure UDP port 123 is open outbound. To check:

	$ ntpstat
If your output resembles the output below, then NTP is working:

	synchronised to NTP server (12.34.56.78) at stratum 3 ....

Modify your hosts file to put your Zenoss server's IP

Run ansible with following:

    ansible -

