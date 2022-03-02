# aggregators-depoyment

This is ansible code to delpoy multiple aggegators in a cluster, with FQDN and a single interface  

Tested on:  
Centra_version:39.2.4

# Instructions
-assign non persistent IP address on eth0 interface to allow communication between control node and aggregators on port 22  
ip addr add x.x.x.x/x dev eth0  
ip link set eth0 up  
ip r add default via x.x.x.x

-fill in all data in hosts_prep.xlxs. Subnet should be in the long format 255.255.0.0 and dns servers separated by space in the same cell. Copy the data from the Inventory column into the inventory file, below the [Aggr] stanza. Update your [all:vars] stanza with the correct old root password, new root password and secure communication password.

-verify SSH connectivity from control node to aggregator:  
nc -w 3 -z -v aggregator 22

-run ansible:  
ansible-playbook -i inventory prepare_ssh_aggr_nodes.yml
