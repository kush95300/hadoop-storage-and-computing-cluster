Hadoop-Storage-Computing-Cluster-Maker
=====================================

This repository helps in  creating a Hadoop Computing Storage Cluster  and during craetion automatically creates AWS ec2 instance and update inventory file as group name grp_name and each entry of group conatin IP address, ansible_user, ansible_key_file and ansible_connection. Thall done in just 5-10 minutes.  

Hense, function of Repository are :

- Create Ec2 Instance of all nodes
- Create Hadoop Namenode, Datanode, Jobtracker, tasktracker and client.
- Write inventory entry for further automation.
- Connect all nodes together.

Requirements
------------
There are NO Requirement. ( Only Ansible successfully installed)

<b> NOTE: All variable should be provided as mentioned in all roles and setup file.</b>

Variables
--------------

Following parameters are there : 

| Sr.|  PARAMETER | NAME  | USE  | CHANGE PARAMETER AT LOCATION |
| ------------ | ------------ | ------------ | ------------ | ------------ |
| 1.| **i_name**   (String) ( Recommended change ) | Instance Name  |  It is name tag for instance. | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 2.|   **key**   (String) | Aws key name  | It is the aws key which in ec2 key section. NOTE:  write keyname only (not  Key extt. like: newkey.pem or newkey.ppk )   | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 3.|  **i_type**    (String) | Instance type | Aws Instance type like: t2.micro , t2.medium etc.    | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 4. |   **img**    (String) | Aws AMI ID  | It denotes AMI iD. AMI ID is the image through which instance will launch. e.g. - ami-xxxxxxxxx  | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 5. |   **subnet**    (String) | Aws VPC Subnet ID  | It denotes VPC subnet ID. e.g. - subnet-xxxxxxxxx)   | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 6. |  **SG**    (String) | Security Group ID  | It is the Ec2 Security Group ID. e.g. - sg-xxxxxxxxxx   | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 7. |  **counts**    (Number) | counts  | Counts denotes number of instance to launch. e.g. - 2   | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 8. |   **zone**    (String) | Availability Zone or region  | It is the AZ from where resorces are used. e.g. - 'ap-south-1'   | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 9. |  **inventory**    (String) | inventory file path  | it denotes inventory file path ( as it write group tag in inventory ). e.g. - "/etc/ansible/hosts"   | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 10. |  **grp_tag**    (String) () Recommended change )  |  Inventory Group Tag  | It denotes inventory group tag, so that after launching instance inventory entry automatically done.  | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
| 11. |   **tag**    (String) ( Recommended change )  | Instance Tag  | It is Instance tag to differenciate or compare instances.  | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
|12. |   **ssh_key_full_path**    (String) | Aws key path (Local path,)  | It denotes full key path, where key is there, so that it can write it in inventory as automatic entry..  | Update it in 'aws_instance_launcher' role defaults dir or   in setup.yml file. |
|13. |   <b>access_pass </b>     (String) ( Required )| AWS IAM user Access Key  | It denotes aws access key. | Update it in 'aws_instance_launcher' role defaults/main.yml file or 'aws_instance_launcher' role vars/main.yml file or   in setup.yml file or in ansible vault |
|14. |   <b>secret_pass</b>     (String) ( Required ) | AWS IAM user Secret key  | It denotes aws secret key. | Update it in 'aws_instance_launcher' role defaults/main.yml file or 'aws_instance_launcher' role vars/main.yml file or   in setup.yml file or in ansible vault |
|15. |   <b>nn_ip</b>     (String)  | Hadoop Namenode IP  | It is the Namenode or Storage Master Node IP. for e.g.: 1.2.3.4 | Update it in parameter file or in setup.yml file. |
|16. |   <b>nn_port</b>     (String) ( Required ) | Hadoop Namenode Port (Default: 9001)  | It is the hadoop namenode or Storage Master Port Number.for e.g.: 9001 | Update it in parameter file or in setup.yml file. |
|17. |   <b>jt_ip</b>     (String) ( Required ) | Hadoop Jobtracker IP  | It is the hadoop Jobtracker or Computing Master Port Number.for e.g.: 1.2.3.4 | Update it in parameter file or in setup.yml file. |
|18. |   <b>jt_port</b>     (String) ( Required ) | Hadoop Jobtracker Port (Default: 9002)  | It is the hadoop jobtracker or Computing Master Port Number.for e.g.: 9001 | Update it in parameter file or in setup.yml file. |
|19. |   <b>nn_dir_path</b>     (String)  | Hadoop Namenode Directory Path  | It is the path of namenode directory. for e.g.: /namenode | Update it in parameter file or in setup.yml file. |
|20. |   <b>dn_dir_path</b>     (String)  | Hadoop Datanode Directory Path  | It is the path of datanode directory. for e.g.: /datanode | Update it in parameter file or in setup.yml file. |

Use there parameters for better use.

Dependencies
------------

There are NO Dependencies.

Example Playbook
----------------

### To create Master INstance
```sh
---
- hosts: server
  become_user: root
  become: yes
  roles:
          - name: "Creating Master instance"
            role: aws_instance_launcher
            vars:
                    i_name: kk_master
                    access_pass: AKIYYLPPOFNCRT2W
                    secret_pass: e33HrqVMMTsS53RxbXjbIerUjXj
                    grp_tag: kk_master
                    tag: master

```
### To add kubernetes-master-setup Role ( without previledges)
```sh
---
- hosts: localhost
  roles:
          - name: "Creating Master instance"
            role: aws_instance_launcher
            vars:
                    i_name: kk_master
                    access_pass: AKIYYLPPOFNCRT2W
                    secret_pass: e33HrqVMMTsS53RxbXjbIerUjXj
                    grp_tag: kk_master
                    tag: master

```
### To create a instance with group tag database
```sh
---
- hosts: localhost
  roles:
          - name: "Creating instance"
            role: aws_instance_launcher
            vars:
                    i_name: db1
                    access_pass: AKIYYLPPOFNCRT2W
                    secret_pass: e33HrqVMMTsS53RxbXjbIerUjXj
                    grp_tag: database

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

Medium : https://kaushalsoni.medium.com </b> 

<br>

