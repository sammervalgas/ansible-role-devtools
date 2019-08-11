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

  >   IMPORTANT: If role not found enter the installation folder path of /etc/ansible/ansible.cfg in the argument roles_path:
    Ex: My local roles path is ~/.ansible/roles/ then I had to do:

```bash
  # Append one line after roles_path into ansible.cfg
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

Ex:
```bash
$ cd ansible-role-devtools; ln -s $PWD ~/.ansible/roles  

$ ansible-playbook tests/test.yaml

# If you just want one stack
$ ansible-playbook tests/test.yaml --tags docker
```
    - hosts: localhost
      roles:
         - ansible-role-devtools

License
-------

BSD

Author Information
------------------

Sammer Valgas - XGH Expert
