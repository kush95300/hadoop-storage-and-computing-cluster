hadoop-tasktracker
==================

This role Create a Hadoop Tasktracker  and configure it. This all done very quickly within a minutes.You can launch a aws instance and can u
se this role to setup hadoop tasktracker.

Hense, function of Role is :

- Create hadoop tasktracker.
- Connect to hadoop jobtracker to compute data.

Requirements
------------
There are NO Requirement. ( Only Ansible successfully installed and all variable successfully entered )

Role Variables
--------------

Following parameters are there : 

| Sr.|  PARAMETER | NAME  | USE  | CHANGE PARAMETER AT LOCATION |
| ------------ | ------------ | ------------ | ------------ | ------------ |
|1. |   <b>jt_ip</b>     (String) ( Required ) | Hadoop Jobtracker IP  | It is the hadoop Jobtracker or Computing Master Port Number.for e.g.: 1.2.3.4 | Update it in 'hadoop-tasktracker' role defaults/main.yml file or in setup.yml file. |
|2. |   <b>jt_port</b>     (String) ( Required ) | Hadoop Jobtracker Port (Default: 9002)  | It is the hadoop jobtracker or Computing Master Port Number.for e.g.: 9002 | Update it in 'hadoop-tasktracker' role defaults/main.yml file or in setup.yml file. |


Use there parameters for better use.

Dependencies
------------

Hadoop both hdfs (Storage)  and mapred (computing) cluster must be configured.

Example Playbook
----------------

### To create Tasktracker
```sh
---
- hosts: tasktracker
  become_user: root
  become: yes
  roles:
          - name: "Creating tasktracker"
            role: hadoop-tasktracker
            vars:
                jt_ip: 1.2.3.4
```
### To add with custom 
```sh
---
- hosts: tasktracker
  become_user: root
  become: yes
  roles:
          - name: "Creating Tasktracker"
            role: hadoop-tasktracker
            vars:
                jt_ip: "{{ groups["jobtracker"][0] }}"
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

