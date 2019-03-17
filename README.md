
Example virtual machine setup ansible playbook
==============================================

This playbook contains some repeated tasks I do with ansible against freshly
installed linux virtualmachines.

Currently implemented for centos 7 VMs and GCP debbian instances.

All rules in ansible.inventory directory apply only to the demo environment
obviously.

Examples
--------

Examples for host inventory items are in examples directory.

Usage for CentOS VM
-------------------

Make sure host is reachable in the first place (networking is up).

If the VM does not have SSH server enabled after initial reboot, login as root
from VM console and start sshd service:

    systemctl start sshd

When first run, you should run the playbook with root SSH login with password
setup during centos install:

    ansible-playbook virtualmachines.yml -u root --ask-pass

The playbook will configure a normal user and disable root logins, so after
first run you would run it with normal user, for example:

    ansible-playbook virtualmachines.yml -u hile --become

Usage for GCP debian instances
------------------------------

To access GCP debian instances with SSH and ansible, you need to configure
suitable google cloud OS Login accounts first.

For detailed instructions see:

https://cloud.google.com/compute/docs/instances/managing-instance-access

