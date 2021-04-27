hadoop-datanode
================

This role Create a Hadoop datanode and configure it. This all done very quickly within a minutes.You can launch a aws instance and can use this role to setup hadoop datanode.

Hense, function of Role is :

- Create hadoop datanode
- Create a directory for hadoop datanode to save data.
- Connect it to namenode.

Requirements
------------
There are NO Requirement. ( Only Ansible successfully installed and all variable successfully entered )

Role Variables
--------------

Following parameters are there : 

| Sr.|  PARAMETER | NAME  | USE  | CHANGE PARAMETER AT LOCATION |
| ------------ | ------------ | ------------ | ------------ | ------------ |
|1. |   <b>nn_ip </b>     (String) ( Required )| Hadoop Namenode IP  | It is the hadoop namenode or Storage Master Node IP. | Update it in hadoop-datanode' role defaults/main.yml file  or   in setup.yml file |
|2. |   <b>dn_dir_path</b>     (String)  | Hadoop Datanode Directory Path  | It is the path of datanode directory. for e.g.: /datanode | Update it in 'hadoop-datanode' role defaults/main.yml file or in setup.yml file. |
|3. |   <b>nn_port</b>     (String) ( Required ) | Hadoop Namenode Port  | It is the hadoop namenode or Storage Master Port Number. | Update it in 'hadoop-datanode' role defaults/main.yml file or in setup.yml file. |


Use there parameters for better use.

Dependencies
------------

Master Node or Name node must already be created before datanode.

Example Playbook
----------------

### To create Datanode
```sh
---
- hosts: datanode
  become_user: root
  become: yes
  roles:
          - name: "Creating Datanode"
            role: hadoop-datanode
            vars:
                    nn_ip: 1.2.3.4
                    nn_port: 2345

```
### To add with ip in inventory 
```sh
---
- hosts: datanode
  become_user: root
  become: yes
  roles:
          - name: "Creating Datanode"
            role: hadoop-datanode
            vars:
                    nn_ip: "{{ groups["namenode"][0] }}"
                    nn_port: 2345
                    dn_dir_path: /dd

```

License
-------

BSD

Free to use.

Author Information
------------------

##### Maintained by: Kaushal Soni
 
### Support & Contact
<b>

Email: Kaushal95300@gmail.com

Linkedin : https://www.linkedin.com/in/sonikaushal

Github : https://github.com/kush95300

Medium : https://kaushalsoni.medium.com  </b>

<br>

