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
	# you need to specifiy following
	# your global ip address and netmask: "10.0.0.1/24"
	homegw_openvpn_internal_hostprefix: ""

	# you can change the followings, but don't need to do.
	homegw_openvpn_global_hostprefix: "{{ ansible_default_ipv4.address }}"

	# defaults file for ansible-homegw-openvpn
	homegw_openvpn_script_permission_owner: root
	homegw_openvpn_script_permission_group: root
	homegw_openvpn_script_permission_mode: 400
	homegw_openvpn_directory_permission_owner: root
	homegw_openvpn_directory_permission_group: root
	homegw_openvpn_directory_permission_mode: 700

	## system config setting
	homegw_openvpn_name: p1194
	homegw_openvpn_root_dirpath: /etc/openvpn
	homegw_openvpn_port: 1194
	homegw_openvpn_tlsauth_filename: hmac_secret 0
	homegw_openvpn_dh_filename: dh2048.pem
	homegw_openvpn_cacert_filename: cacert.pem
	homegw_openvpn_servercert_filename: server_cert.pem
	homegw_openvpn_serverkey_filename: server_key_nopass.pem
	homegw_openvpn_poolpersist_filename: ipp_1194.txt

	homegw_openvpn_default_filepath: /etc/default/openvpn


Dependencies
------------



Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
	  vars:
        homegw_openvpn_internal_hostprefix: "10.0.0./24"
      roles:
         - YasuhiroABE.homegw-openvpn

License
-------

Apache License 2.0

Author Information
------------------

[Yasuhiro ABE](http://www.yasundial.org/foaf.xml)

