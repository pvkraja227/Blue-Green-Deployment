server - t2.med

sudo apt update

(install aws cli)

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip
unzip awscliv2.zip
sudo ./aws/install

aws configure (provide access keys and region)

(install terraform)

sudo snap install terraform --classic

git clone https://github.com/pvkraja227/Blue-Green-Deployment.git (goto Cluster folder)
terraform init
terraform plan (17 to add)
terraform apply --auto-approve
install kubectl (sudo snap install kubectl --classic)
aws eks --region ap-south-1 update-kubeconfig --name devopsshack-cluster (inorder to connect to cluster)
kubectl get nodes - 3

(in Cluster folder)
kubectl create ns webapps
vi svc.yml
kubectl apply -f svc.yml
vi role.yml
kubectl apply -f role.yml
vi rolebind.yml
kubectl apply -f rolebind.yml
(goto link)
vi secret.yml
kubectl apply -f secret.yml -n webapps

kubectl describe secret mysecretname -n webapps (copy token for authentication): jenkins dashboard/credentials/secret text/paste token

jenkins/nexus/sonarqube - t2.med
sudo apt update - all 3

Jenkins:
install java17
chrome: jenkins on ubuntu/latest release
sudo cat /var - get pwd and open Jenkins dashboard
sudo systemctl enable jenkins
install docker: from chrome: 3 steps
sudo chmod 666 /var/run/docker.sock (one time permission to all users to use docker or else we need to mention sudo at every instance)
sudo usermod -aG docker ubuntu (adding ubuntu to docker group)
sudo usermod -aG docker jenkins (adding jenkins to docker group)
install trivy
install kubectl (sudo snap install kubectl --classic) \

sonarqube:
install docker
sudo chmod 666 /var/run/docker.sock (one time permission to all users to use docker or else we need to mention sudo at every instance)
OR OR sudo usermod -aG docker ubuntu // newgrp docker (adding ubuntu to docker group)
docker run -itd -p 9000:9000 sonarqube:lts-community
docker ps
chrome: publicIP:9000 (default: admin/admin, create new pwd)
generate token \

Nexus:
install docker
sudo chmod 666 /var/run/docker.sock (one time permission to all users to use docker or else we need to mention sudo at every instance)
OR OR sudo usermod -aG docker ubuntu // newgrp docker (adding ubuntu to docker group)
docker run -itd -p 8081:8081 sonatype/nexus3
docker ps
chrome: publicIP:8081 (default: admin/for pwd .. need to enter into container)
docker exec -it containedID /bin/bash
cat sonatype-work/nexus3/admin.password (copy pwd and later change) \

Jenkins Dashboard:

manage jenkins/plugins/available plugins \

SonarQube Scanner
Maven Integration
Pipeline Maven Integration
Config File Provider (for Nexus)
Kubernetes
Kubernetes credentials
Kubernetes CLI
Kubernetes Client API
Docker
Docker Pipeline
Pipeline Stage View
Eclipse Temurin Installer (for java 17) \

new item/pipeline/old builds-2/pipeline script

(trivy, docker, jdk - directly installed in Jenkins server // but for plugins installed we to need define in tools section: maven, sonarqube)
manage jenkins/tools/
maven: name: maven3
sonarqube: name: sonar-scanner

manage jenkins/credentials/ 
k8s - already done
sonar - secret text/
docker - username and password

we have to integrate sonarqube server to jenkins
manage jenkins/system/sonarqube servers/sonarqube installations
name: sonar/url:http://43.205.120.211:9000/add token

manage jenkins/managed files/add a new config/global maven settings/ID: maven-settings/next
<server>
      <id>maven-releases</id>
      <username>admin</username>
      <password>nexus</password>
    </server>
    
    <server>
      <id>maven-snapshots</id>
      <username>admin</username>
      <password>nexus</password>
    </server>

copy releases and snapshots links from nexus dashboard and update in pom.xml

copy jenkins url/in sonar dashboard/administration/webhooks/create
name: Jenkins
URL: http://3.108.184.60:8080/sonarqube/webhook/ .. create

buildnow

kubectl get all -n webapps
kubectl logs bankapp-blue-5f8cdb7bd9-mzq5j -n webapps
take LB link .. 

change: build with parameters from blue to green/switch traffic



