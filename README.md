# ansible-ethminer (proof of concept)
Ansible-script to mine ethereum on Ubuntu 16.04 (in Amazon AWS EC2)

## Comment
It's not worth to mine on Amazon EC2 because the costs are too high for the given graphics performance! The ethereum you will mine is not enough to defray the costs.

But you can modify this script to run the miner on your own machines.

## Conditions
- Amazon EC2 p*- or g*-Instance
- NVIDIA Graphics Card
- Ubuntu 16.04
- ~10GB Storage (should be enough)
- Mining-Pool-URL (e.g. ethermine.org)

## Steps
1. Install ansible on your local machine. (https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
2. Your public ssh-Key has to be added to the host, to connect without Username and Passwort (default for EC2). (hint: ssh-keygen; ssh-copy-id)
3. Enter the Public IP of the host in file "hosts".
4. Change the Ethereum-Pool-URL in "group_vars/all".
5. Execute:
```
ansible-playbook ethminer-playbook.yml -i hosts
```
Now on the target-System will be a systemd-service that starts mining. You can check this with:
```
sudo journalctl -f -u ethminer.service
```

That's it!