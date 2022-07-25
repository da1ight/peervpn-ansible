# Qualification task for peervpn install automation
Ansible playbooks for compile, build, install and publish peervpn package in local apt repo.

_NOTE:_ This code is not ready for production usage. Please use at your own risk.

# Requirements
The below requirements are needed on the repo_host.

>apt install python3-pip\
>pip3 install docker

python >= 2.6\
docker-py >= 1.7.0\
Docker API >= 1.20

**Usage:**

You need at least one remote host/vm for using this playbooks. If you want to use local host
please edit _remote_src_ parameter in build/compile tasks. 

1) Edit group_vars/all.yml to suite your setup
2) Put your private ssh key to maintainer_id_rsa in $pwd (should be added to target hosts)
3) To build peervpn from source and publish in local repo:

> ansible-playbook playbooks/process_peervpn.yml -i inventory --ask-become-pass

_NOTE:_ add `-e package_version=0.045` to specify peervpn builded package version (0.044 used by default)

4) Install peervpn package
> ansible-playbook playbooks/setup_peervpn.yml -i inventory --ask-become-pass
