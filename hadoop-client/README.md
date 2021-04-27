hadoop-client
==============

This role Create a Hadoop Client  and configure it. This all done very quickly within a minutes.You can launch a aws instance and can use this role to setup hadoop client.

Hense, function of Role is :

- Create hadoop client
- Connect it to namenode and jobtracker.

Requirements
------------
There are NO Requirement. ( Only Ansible successfully installed and all variable successfully entered )

Role Variables
--------------

Following parameters are there : 

| Sr.|  PARAMETER | NAME  | USE  | CHANGE PARAMETER AT LOCATION |
| ------------ | ------------ | ------------ | ------------ | ------------ |
|1. |   <b>nn_ip</b>     (String)  | Hadoop Namenode IP  | It is the Namenode or Storage Master Node IP. for e.g.: 1.2.3.4 | Update it in 'hadoop-client' role defaults/main.yml file or in setup.yml file. |
|2. |   <b>nn_port</b>     (String) ( Required ) | Hadoop Namenode Port (Default: 9001)  | It is the hadoop namenode or Storage Master Port Number.for e.g.: 9001 | Update it in 'hadoop-client' role defaults/main.yml file or in setup.yml file. |
|3. |   <b>jt_ip</b>     (String) ( Required ) | Hadoop Jobtracker IP  | It is the hadoop Jobtracker or Computing Master Port Number.for e.g.: 1.2.3.4 | Update it in 'hadoop-client' role defaults/main.yml file or in setup.yml file. |
|4. |   <b>jt_port</b>     (String) ( Required ) | Hadoop Jobtracker Port (Default: 9002)  | It is the hadoop jobtracker or Computing Master Port Number.for e.g.: 9001 | Update it in 'hadoop-client' role defaults/main.yml file or in setup.yml file. |


Use there parameters for better use.

Dependencies
------------

Hadoop both hdfs (Storage)  and mapred (computing) cluster must be configured.

Example Playbook
----------------

### To create Cliente
```sh
---
- hosts: client
  become_user: root
  become: yes
  roles:
          - name: "Creating Client"
            role: hadoop-client
            vars:
                nn_ip: 1.2.3.4
                jt_ip: 1.2.3.4
```
### To add with custom 
```sh
---
- hosts: client
  become_user: root
  become: yes
  roles:
          - name: "Creating Client"
            role: hadoop-client
            vars:
                nn_ip: "{{ groups["namenode"][0] }}"
                jt_ip: "{{ groups["jobtracker"][0] }}"
                nn_port: 2345
                jt_port: 2346

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

