Jenkins for Kubernetes with PersistentVolume /mnt/nfs_share/jenkins
NFS file share /mnt/nfs_share/jenkins has to be created before all steps.

0. Allow access to NFS share:

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







