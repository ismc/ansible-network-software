network-software
=========

A role to maintain the system software (check, stage, install, and clean) for various Cisco platforms

Requirements
------------

The inventory must be properly setup for the platforms being used from the [Ansible Network Modules](https://docs.ansible.com/ansible/latest/network/index.html).  This role uses net_put to push images to devices which requites Ansible 2.7.


Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

```
really_delete_files: no

network_version_map:
  WS-C3850:
    version: '16.06.03'
    software: 'cat3k_16.6.3'
  N5K-C5548UP:
    version: '7.1(4)N1(1)'
    software: 'nxos_7.1(4)N1(1)'
  N3K-C3064PQ:
    version: '6.0(2)U6(9)'
    software: 'nxos_6.0(2)U6(9)'

network_image_map:
  'cat3k_16.6.3':
    system_image_url: http://1.2.3.4/cisco/3850/cat3k_caa-universalk9.16.06.03.SPA.bin
    system_image_size: 410434678
    system_image_checksum: 16fdc2dd9b8a5f7096a71e04ead0431d
  'cat3k_3.6.8E':
    system_image_url: http://1.2.3.4/cisco/3850/cat3k_caa-universalk9.SPA.03.06.08.E.152-2.E8.bin
    system_image_size: 305292424
    system_image_checksum: a04a54d69cb2b4d2867ed369e73598ae
  'cat3k_3.6.8E_local':
    system_image_url: file:///Users/scarter/Downloads/cisco/cat3850/cat3k_caa-universalk9.SPA.03.06.08.E.152-2.E8.bin
    system_image_size: 305292424
    system_image_checksum: a04a54d69cb2b4d2867ed369e73598ae
  'nxos_7.3(3)N1(1)':
    system_image_url: http://1.2.3.4/cisco/nexus/n5000-uk9.7.3.3.N1.1.bin
    system_image_size: 206130057
    system_image_checksum: a828dc515a2f5ca796a8dab1d86d2eed
    kickstart_image_url: http://1.2.3.4/cisco/nexus/n5000-uk9-kickstart.7.3.3.N1.1.bin
    kickstart_image_size: 34375680
    kickstart_image_checksum: 2200d5880dc68820d9cba8083fe9f88c
  'nxos_6.0(2)U6(10)':
    system_image_url: http://1.2.3.4/cisco/nexus/n3000-uk9.6.0.2.U6.10.bin
    system_image_size: 206130057
    system_image_checksum: 98b1ba8106afbc85b83c0f985a66cd30
    kickstart_image_url: http://1.2.3.4/cisco/nexus/n3000-uk9-kickstart.6.0.2.U6.10.bin
    kickstart_image_size: 37881856
    kickstart_image_checksum: f07cbe12d2e489ce02b9577b59753335
  'nxos_7.0(3)I4(7)':
    system_image_url: http://1.2.3.4/cisco/nexus/nxos.7.0.3.I4.7.bin
    system_image_size: 702663680
    system_image_checksum: 9ccc1acb081a93e977e7654709518d90
  'nxos_7.1(4)N1(1)':
    system_image_url: http://1.2.3.4/cisco/nexus/n5000-uk9.7.1.4.N1.1.bin
    system_image_size: 327996211
    system_image_checksum: b9eadf4bd74e9b8b62d958bbf3d83db3
    kickstart_image_url: http://1.2.3.4/cisco/nexus/n5000-uk9-kickstart.7.1.4.N1.1.bin
    kickstart_image_size: 34799104
    kickstart_image_checksum: 65434f65a591257a93627670ce363cf9
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      gather_facts: no
      tasks:
        - include_role:
            name: network-software
            tasks_from: "{{ network_software_task | default('facts') }}"

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
