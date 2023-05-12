Jenkins for Kubernetes with PersistentVolume /mnt/nfs_share/jenkins
NFS file share /mnt/nfs_share/jenkins has to be created before all steps.

0. Allow access to NFS share:

sudo mkdir /mnt/nfs_share/jenkins
sudo chmod -R  777 /mnt/nfs_share/jenkins

1. Create namespace: 

kubectl create namespace devops-tools

2. Create all necessary stuff (service, pods, persistent volume and persistent volume claim): 

kubectl apply -f jenkins-app.yaml

3. Set TLS secret for SSL certificate

cat tls.crt | base64
cat tls.key | base64

kubectl apply -f jenkins-tls.yaml


4. Create Ingress for access from outside:

kubectl apply -f jenkins-ingress.yaml 



References:

1) https://medium.com/@myte/kubernetes-nfs-and-dynamic-nfs-provisioning-97e2afb8b4a9
2) https://www.jenkins.io/doc/book/installing/kubernetes/
3) https://medium.com/@vishal.sharma./running-jenkins-in-kubernetes-cluster-with-persistent-volume-da6584edc126
4) https://gitlab.com/nb-tech-support/devops/-/blob/master/Deploy_Jenkins_on_Kubernetes.yaml



