### Jenkins-integration-with-kubernetes

CI/CD Pipeline for kubernetes deployment using Jenkins

### Project ARCH 

<img width="930" height="363" alt="image" src="https://github.com/user-attachments/assets/0c8c9c02-42c2-4ad7-bedf-6c34ab519662" />

- Create Jenkins as a docker container
     ( install docker & kubernetes pipeline plugin , write pipline , build the image )

### kubernetes-cluster-setup-using-kubeadm

1. Set Hostnames
    hostnamectl set-hostname k8smaster 
3. Assign Static IP
   nmcli con mod "connection name" ipv4.method manual ipv4.addresses 192.168.0.107/24               ipv4.gateway 192.168.0.1 ipv4.dns "192.168.2.254 8.8.8.8 8.8.4.4" && nmcli con down "Wired       connection 1"
   nmcli con up "connection name"
   nmcli con up "connection name"
   
5. Edit /etc/hosts file
   192.168.0.xxx k8smaster
   192.168.0.xxx k8sworker1
   192.168.0.xxx k8sworker2
   
7. Disable SELinux
   setenforce 0
   sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux
8. Disable firewall and edit Iptables settings
   systemctl disable firewalld
   cat <<EOF | tee /etc/modules-load.d/k8s.conf
br_netfilter
EOF

cat <<EOF | tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-iptables = 1
net.ipv4.ip_forward = 1
EOF

sysctl --system

10. Setup Kubernetes Repo
    
12. Installing Kubeadm and Docker, Enable and start the services
   yum install kubeadm docker -y
  systemctl enable kubelet
  systemctl start kubelet
  systemctl enable docker
  systemctl start docker

14. Disable Swap
    swapoff -a
    
15. Initialize Kubernetes Cluster
    kubeadm init
     
16. Installing Pod Network using Calico network
17. Join Worker Nodes


## Deploy node js app on k8s cluster
     

docker run -u 0 --privileged --name jenkins -it -d -p 8080:8080 -p 50000:50000
