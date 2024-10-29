# Ansible-Task
-Generate public key and private key
```
ssh-keygen -t rsa
choose path to create new dir for new keys --> /home/ammar/.ssh/CHOOSENAME
```
-Move public key of controller machine to containers
```
Docker inspect containername   -> to get IP
ssh-copy-id -i AnsibleKey.pub devops@172.17.0.2
```
