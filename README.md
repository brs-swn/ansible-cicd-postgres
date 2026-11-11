PostreSQL Services for CICD Implementation
=========

This configures the PostgreSQL service on Fedora or Red Hat. The primary purpose is to configure postgres and initalize databases for CICD toos such as GitLab, OpenProject and Artifact Keeper.

The services that are configured with this role are:
* postgres

The baseline configuration was adapated from:
https://oneuptime.com/blog/post/2026-02-21-ansible-configure-postgresql/view
Author: Nawaz Dhandala
@nawazdhandala

Requirements
------------

This Role is customized for Fedora Linux 45 or higher. Other distributions
can be used, but updates to packaging and paths would have to be changed.
This assumes that a basic OS is installed with the proper partitions to 
accommodate the minimum storage. Hosts file, user accounts and NTP are also 
assumed to be configured.

Role Variables
--------------

See the default variable list for variables that can be overriden in the inventory group vars.

Also, host names, IP and MAC addresses are defined in the inventory hosts. See the example hosts file.

Dependencies
------------

 - An ansible user with SSH keys must already be configured on the target host.
 - It is advisable to to configure NTP.
 - No other Galaxy roles should be necessary to use this role.

Example Playbook
----------------
The play book should be defined as follows:

    - hosts: cicd_db
      become: yes
      become_user: root
      roles:
        - ansible-cicd-postgres

To execute the playbook use the following syntax:

    export ANSIBLE_CONFIG=ansible.cfg

    ansible-playbook \
     --private-key ~/.ssh/ansible-id_rsa \
     -u ansible --ask-vault-pass \
     -i ../inventory/hosts \
     server-configure-db.yml

License
-------

GPL-2.0-or-later

Author Information
------------------

Brent R. Scott <brs.scottworks@gmail.com>
