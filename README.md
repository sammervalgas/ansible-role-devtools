Ansible role tools for development (Centos / Fedora / RHEL)
=========

Ansible role contains the stacks:
* [Git](https://git-scm.com/doc)
* [Guake Terminal](http://guake-project.org/)
* [Atom](https://atom.io/docs)
* [NodeJS](https://nodejs.org/en/docs/)
* [Ionic](https://ionicframework.com/)
* [Java](https://www.oracle.com/technetwork/java/javase/downloads/index.html#JDK8)
* [Maven](https://maven.apache.org/)
* [Gradle](https://docs.gradle.org/current/userguide/userguide.html)
* [Android SDK](https://developer.android.com/studio/intro/?gclid=CjwKCAjw1rnqBRAAEiwAr29IIzAZiW7pii526JbDGlPYaGb7ejrkUkOzn1BUd2JdON_OqTannmbswBoCa4UQAvD_BwE)
* [Docker](https://docs.docker.com/)
* [VirtualBox](https://www.virtualbox.org/)


Requirements
------------

Install ansible:

CentOS:

```bash
$ sudo yum update -y; yum install -y ansible
```

Ubuntu:

```bash
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install ansible
```

Pip
```bash
$ sudo pip install ansible
```



---
If you want to run locally (localhost) without setup inventory, follow next step:  
Before start we configure the ansible hosts from local.
```bash
sudo /bin/bash -c 'echo -e "
[localhost:vars] \n
ansible_user=YOUR_USER \n
ansible_pass=YOUR_PASS \n
ansible_become=YOUR_SUDO_PASS \n
ansible_port=22 \n
ansible_connection=local \n

[localhost]
127.0.0.1 # localhost ip
"' >> /etc/ansible/hosts
```
---
  > :warning:  ***IMPORTANT:***   
  If role not found enter the installation folder path of /etc/ansible/ansible.cfg in the argument roles_path:
    Ex: My local roles path is ~/.ansible/roles/ then I had to do:

```bash
# Append one line after roles_path argument into ansible.cfg
$ sed -i.$(date +%s).bkp '/roles_path/s/$/\:\~\/.ansible\/roles\//' /etc/ansible/ansible.cfg
```

Role Variables
--------------

TO BE DEFINED

Dependencies
------------
None:

Example Playbook
----------------

Enter inside role folder and create a symbolic link to your ansible roles path:

Run locally:

```bash
$ git clone https://github.com/sammervalgas/ansible-role-devtools.git
$ cd ansible-role-devtools; ln -s $PWD ~/.ansible/roles
$ ansible-playbook -i tests/inventory tests/test.yaml

# If you just want one stack
$ ansible-playbook -i tests/inventory tests/test.yaml --tags docker
```
---
_Playbook_
```yaml

    - hosts: localhost
      roles:
         - ansible-role-devtools
```
License
-------

BSD

Author Information
------------------

Sammer Valgas - XGH Expert
