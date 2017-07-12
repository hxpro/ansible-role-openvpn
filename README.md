hxpro.openvpn
=============

OpenVPN server

This role si under development. Do not use it in production.

Tested on CentOS 7

Requirements
------------

  - Public certificate of Certificate Authority `ovpn_ca`
  - Server key `ovpn_key` and certificate `ovpn_cert` issued by CA

Role Variables
--------------

    ovpn_port: 1194
    ovpn_proto: udp
    ovpn_device: tun
    ovpn_user: openvpn
    ovpn_group: openvpn
    ovpn_max_clients: 30
    
    ovpn_log: /var/log/openvpn
    ovpn_verb: 1
    
    ovpn_home: /etc/openvpn/server/
    ovpn_ca: ca.pem
    ovpn_cert: server.crt
    ovpn_key: server.key
    ovpn_dh: dh.pem

    ovpn_push:
      - "route 192.168.0.0 255.255.255.0"
      - "dhcp-option DNS 192.168.0.1"
    
    ovpn_server_network: 192.168.5.0
    ovpn_server_netmask: 255.255.255.0
    
    ovpn_ipv4_forwarding: true

Dependencies
------------

  - hxpro.epel
  - hxpro.selinux

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: hxpro.openvpn
           ovpn_proto: tcp

License
-------

WTFPL

Author Information
------------------

Matěj Koudelka <matej@hxpro.cz>
