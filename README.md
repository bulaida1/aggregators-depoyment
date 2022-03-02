# aggregators-depoyment

This is ansible code to delpoy multiple aggegators in a cluster, with FQDN and a single interface  

Tested on:  
Centra_version:39.2.4

# Instructions
-assign non persistent IP address on eth0 interface to allow communication between control node and aggregators on port 22  
ip addr add x.x.x.x/x dev eth0  
ip link set eth0 up  
ip r add default via x.x.x.x 

-verify IP connectivity:  
for i in $(cat ips) ; do nc -w 3 -z -v  $i 22 ; done  

-run ansible:  
ansible-playbook -i inventory prepare_ssh_aggr_nodes.yml
