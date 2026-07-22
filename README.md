# Ethernity NODE

This repository provides requirements and setup instructions to enable Ethernity NODE capabilities on a regular Linux system.


Currently the following operating systems are suported:
```
Ubuntu 18.04
```

We are planning support for the following operating systems:
```
Debian 10*
Fedora 30*
CentOS 7*
RHEL 8*
```

# 1. Install ansible

```bash
$ sudo apt update
$ sudo apt -y install software-properties-common
$ sudo apt-add-repository --yes --update ppa:ansible/ansible
$ sudo apt -y install ansible
```


# 2. Install the ansible virtualization roles

```bash
$ sudo ansible-galaxy collection install crivetimihai.virtualization
```


# 3. Clone the repository

```
$ git clone https://github.com/ethernity-cloud/mvp-pox-node.git
```


# 4. Create config file:

```bash
$ cd mvp-pox-node
$ cat << EOF > config
ADDRESS=0xf17f52151EbEF6C7334FAD080c5704D77216b732
PRIVATE_KEY=AE6AE8E5CCBFB04590405997EE2D52D2B330726137B875053C36D94E974D162F
RESULT_ADDRESS=0xC5fdf4076b8F3A5357c5E395ab970B5B54098Fef
RESULT_PRIVATE_KEY=0DBBE8E4AE425A6D2687F1A7E3BA17BC98C673636790F1B8AD91193C05875EF1
EOF
$
```


# 5. Run the playbook to install the kernel

```bash
$ sudo ansible-playbook -i localhost, playbook.yml \
  -e "ansible_python_interpreter=/usr/bin/python3"
```

After the first run of the script, the new kernel is installed and the following message will be displayed:

```
ok: [localhost] => {
    "msg": "The kernel has been updated, a reboot is required"
}
```

Reboot the system as requested.


# 6. Run the playbook to start the node

```bash
$ sudo ansible-playbook -i localhost, playbook.yml \
  -e "ansible_python_interpreter=/usr/bin/python3"
```

t
