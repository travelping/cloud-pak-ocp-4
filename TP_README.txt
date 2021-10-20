All nodes you can find in ibm console
https://cloud.ibm.com/gen1/infrastructure/devices?search=ibm-01

Login to bastion node:
ssh root@161.156.29.163
from there you can use k8s api:
oc --kubeconfig /ocp_install/auth/kubeconfig get nodes

login to master-01 (use private IP of ibm server):
ssh core@10.75.122.167

Network on that servers is minimally configured by dhcp server which installed on bastion host with cloud-pak ansible stuff.
Public network and MTU configuration is missing there, i guess it is possible to use MachineConfig operator for such tasks.
All nodes has access to internet via bastion host (there manually enabled forwarding and masquerading).

Metallb/Ingress is missing because public network is not configured on servers.
