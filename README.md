# Automatic Remediation for SOLARIS 11.4 Hardening : 
## Installing Ansible in Solaris 11 :
```bash
    $pkgadd -d http://get.opencsw.org/now

    $/opt/csw/bin/pkgutil -y -i ansible 

    $/opt/csw/bin/pkgutil -y -i ansible 
```    
#

##  Verifying by the Version of Ansible :
```bash
    $/opt/csw/bin/ansible --version

    [output]:
    config file = /etc/opt/csw/ansible/ansible.cfg

```
#
## Changing to the ansible Directory :
```bash
    $cd /etc/opt/csw/ansible 
    $ls

    [output]:
    hosts  ansible.cfg  ansible.cfg.CSW  hosts.CSW
```

#
## Modifying the hosts file (Easy Access) :
```bash
    $cat <<EOF >> hosts
    localhost ansible_connection=local
    EOF
    
    $cat hosts | grep ansible_connection

    [output]:
    localhost ansible_connection=local
```
#
## Try to PING localhost :
```bash
    $/opt/csw/bin/ansible all -m ping --ask-pass
    
    [output]:
    SSH password: 
    localhost | SUCCESS => {
        "changed": false, 
        "ping": "pong"
    }

```

#
## Now execute the script :
```bash
    $/opt/csw/bin/ansible-playbook playbook.yml
    
    [output]:
    PLAY [all] *****************************************************

    TASK [setup] ***************************************************

    PLAY RECAP *****************************************************
    localhost       : ok=59   changed=27   unreachable=0    failed=0 

```
