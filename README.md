[servers-db]
192.168.33.14

[servers-web]
192.168.33.15
---------------------------------------------------------------------
cette commande permet de copier:
			ssh-copy-id -i id_rsa.pub 192.168.33.14
-----------------------------------------------------------------------
cette commande permet de se connecter à un server distant:
ssh 192.168.33.14
----------------------------------------------------------------------
on met cette partie dans le fichier de config, voici le repertoire:
sudo vi /etc/ansible/ansible.cfg

[defaults]
inventory = /home/vagrant/labAnsible/lab1/inventory/hosts/hosts
key-file = /home/vagrant/.ssh/id_rsa
-------------------------------------------------------------------------
pour faire le ping:
	ansible all -m ping
-------------------------------------------------------------------------
cette commande permet de créer un fichier playbook.yaml:
	touch playbook.yaml
cette commande permet d'executer le playbook:
        ansible-playbook --become playbook.yaml
-------------------------------------------------------------------------
pour mettre à jour le fichier cache:
- name: update repository index
  apt:
    update_cache: yes
  when: ansible_distribution == "Ubuntu"
-------------------------------------------------------------------------
- name: installation
  become: true
  apt:
    name: nginx
    state: present
  when: ansible_distribution == "Ubuntu"

- name: Restart Nginx
  service:
    name: nginx
    state: restarted
-------------------------------------------------------------------------
- name: Installer les paquets nécessaires
  apt:
    update_cache=yes
  when: ansible_distribution == "Ubuntu"

- name: Installer les paquets nécessaires
  become: true
  apt:
    name: postgresql
    state: present
  when: ansible_distribution == "Ubuntu"
-----------------------------------------------------------------------------
cette commande permet de connecter à postgres:
sudo -i -u postgres psql

--------------------------------------------------------------------------
docker:installation de docker
---
- name: Install aptitude
  apt:
    name: aptitude
    state: latest
    update_cache: true

- name: Install required system packages
  apt:
    pkg:
      - apt-transport-https
      - ca-certificates
      - curl
      - software-properties-common
      - python3-pip
      - virtualenv
      - python3-setuptools
    state: latest
    update_cache: true
- name: Add Docker GPG apt Key
  apt_key:
    url: https://download.docker.com/linux/ubuntu/gpg
    state: present

- name: Add Docker Repository
  apt_repository:
    repo: deb https://download.docker.com/linux/ubuntu focal stable
    state: present
- name: Update apt and install docker-ce
  apt:
    name: docker-ce
    state: latest
    update_cache: true

- name: Install Docker Module for Python
  pip:
    name: docker
-----------------------------------------------------------------
Pour faire du DevOps, voici les concepts à connaitre:
Automatisation
Orchestration
CI/CD
Monitoring ou Observabilité
