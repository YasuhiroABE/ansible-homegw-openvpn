YasuhiroABE.homegw-openvpn
==========================

This role sets up openvpn for the home router.
You need to prepare certificate files using easy-rsa out of this role.

Requirements
------------

This role is tested on the following platforms.

### Ansible
- Version 2.4

### Distributions
- Ubuntu 16.04
- Debian 9

Role Variables
--------------

### Default

    # Please overwrite your private network with netmask: ["10.0.0.1/24"]
    # homegw_openvpn_push_hostprefix_list: []

    # you can change the followings;
    homegw_openvpn_global_hostprefix: "{{ ansible_default_ipv4.address }}"

    # defaults file for ansible-homegw-openvpn
    homegw_openvpn_permission_owner: root
    homegw_openvpn_permission_group: root
    homegw_openvpn_permission_mode: "u+rwX,go-rwX"

    ## system config setting
    homegw_openvpn_name: p1194
    homegw_openvpn_root_dirpath: /etc/openvpn
    homegw_openvpn_port: 1194
    homegw_openvpn_tlsauth_filepath: files/hmac_secret
    homegw_openvpn_dh_filepath: files/dh2048.pem
    homegw_openvpn_cacert_filepath: files/cacert.pem
    homegw_openvpn_servercert_filepath: files/server_cert.pem
    homegw_openvpn_serverkey_filepath: files/server_key_nopass.pem
    homegw_openvpn_poolpersist_filepath: files/ipp_1194.txt
    
    homegw_openvpn_conf_server_subnet: 10.8.8.0
    homegw_openvpn_conf_server_subnetmask: 255.255.255.0
    
    homegw_openvpn_default_filepath: /etc/default/openvpn
    
Dependencies
------------
None


Example Playbook
----------------

Prepare your public key files under the {{ inventory_dir }}/files directory.

    - hosts: all
      vars:
        homegw_openvpn_push_hostprefix_list: ["10.0.0.0/24"]
        homegw_openvpn_tlsauth_filepath: {{ inventory_dir }}/files/hmac_secret
        homegw_openvpn_dh_filepath: {{ inventory_dir }}/files/dh2048.pem
        homegw_openvpn_cacert_filepath: {{ inventory_dir }}/files/cacert.pem
        homegw_openvpn_servercert_filepath: {{ inventory_dir }}/files/server_cert.pem
        homegw_openvpn_serverkey_filepath: {{ inventory_dir }}/files/server_key_nopass.pem
        homegw_openvpn_poolpersist_filepath: {{ inventory_dir }}/files/ipp_1194.txt
      roles:
         - YasuhiroABE.homegw-openvpn

License
-------

Apache License 2.0

Author Information
------------------

[Yasuhiro ABE](http://www.yasundial.org/foaf.xml)

