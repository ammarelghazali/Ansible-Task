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

-Ping all servers in inventory
```
ansible all -i inventory --private-key AnsibleKey -u devops -m ping

```

-run playbook
```
ansible-playbook playbook.yaml 
```

-Run playbook with tag name
```
ansible-playbook playbook.yaml --tags third
```

-Run playbook and skip tag name
```
ansible-playbook playbook.yaml --skip-tags third
```

-Always and Never
```
[thirdtag,never] || [thirdtag,always]
```


-Loop
```
- name: play1
  hosts: all
  gather_facts: false
  tasks:
   - name: install many servies
     apt:
       name: "{{ item }}"
       state: latest
     loop:
       - curl
       - nginx
       - foo
```
