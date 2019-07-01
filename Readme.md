# Ansible

#### Ansible installation

```shell
  sudo apt-get install software-properties-common
  sudo apt-add-repository ppa:ansible/ansible
  sudo apt-get update
  sudo apt-get install ansible
```


**ansible --version**

```shell
  ansible 2.7.10
  config file = /home/$HOME/workflow/master-ansible/ansible.cfg
  configured module search path = [u'/home/$HOME/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.15rc1 (default, Nov 12 2018, 14:31:15) [GCC 7.3.0]

```


[virtual box download](https://drive.google.com/drive/folders/1YdYFT_AbtVCkedOJU0k88VzY2ir_Lo2z?usp=sharing)

in virtualbox, if internet is not enable
maybe you need configure nameserver 8.8.4.4 in /etc/resolve.conf



generate ssh for all centos1 and ubuntu1
```shell

  for host in centos1 centos2 centos3 ubuntu1 ubuntu2 ubuntu3;
  do
    ssh-keygen -H -F ${host}
    ssh-copy-id packt@${host}
  done
```


### hosts
```shell
  [all]
  ubuntu1 ansible_host=192.168.15.112
  centos1 ansible_host=192.168.15.164
```

### ansible.cfg
```shell
  [defaults]
  inventory = hosts
  host_key_checking = False
  private_key_file = ~/.ssh/id_rsa
  remote_user = packt
```

#### Test with ping module
```shell
ansible all -m ping
```

#### list hosts
```shell
ansible all --list-hosts
```