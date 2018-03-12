# SSHD
Create networking between two containers

## Aim
1. SSH to Container1
2. SSH from container1 to Container2
### Commands
1. To copy the id_rsa.pub to current directory
```sh
./copy.sh
```
2. Execute the ansible-playbook
```sh
ansible-playbook docker.yml
```
NB. Container1 will listen on 1234 port
    Container2 will listen on 2345 port
3.  To ssh into first container
password: admin
```sh
$ ssh root@localhost -p 1234
```

