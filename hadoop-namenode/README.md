hadoop-namenode
================

This role Create a Hadoop Namenode  and configure it. This all done very quickly within a minutes.You can launch a aws instance and can use this role to setup hadoop namenode.

Hense, function of Role is :

- Create hadoop namenode
- Create a directory for hadoop namenode to save data.

Requirements
------------
There are NO Requirement. ( Only Ansible successfully installed and all variable successfully entered )

Role Variables
--------------

Following parameters are there : 

| Sr.|  PARAMETER | NAME  | USE  | CHANGE PARAMETER AT LOCATION |
| ------------ | ------------ | ------------ | ------------ | ------------ |
|1. |   <b>nn_dir_path</b>     (String)  | Hadoop Namenode Directory Path  | It is the path of namenode directory. for e.g.: /namenode | Update it in 'hadoop-namenode' role defaults/main.yml file or in setup.yml file. |
|2. |   <b>nn_port</b>     (String) ( Required ) | Hadoop Namenode Port  | It is the hadoop namenode or Storage Master Port Number. | Update it in 'hadoop-namenode' role defaults/main.yml file or in setup.yml file. |


Use there parameters for better use.

Dependencies
------------

No Dependencies.

Example Playbook
----------------

### To create Namenode
```sh
---
- hosts: namenode
  become_user: root
  become: yes
  roles:
          - name: "Creating Namenode"
            role: hadoop-namenode
```
### To add with custom port and dir 
```sh
---
- hosts: namenode
  become_user: root
  become: yes
  roles:
          - name: "Creating Namenode"
            role: hadoop-namenode
            vars:
                    nn_port: 2345
                    nn_dir_path: /namenode

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

