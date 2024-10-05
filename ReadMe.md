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

jenkins/nexus/sonarqube - t2.med
sudo apt update - all 3

Jenkins:
install java17
chrome: jenkins on ubuntu/latest release
sudo cat /var - get pwd and open Jenkins dashboard
sudo systemctl enable jenkins
install docker: from chrome: 3 steps
sudo chmod 666 /var/run/docker.sock (one time permission to all users to use docker or else we need to mention sudo at every instance)
OR OR sudo usermod -aG docker ubuntu // newgrp docker (adding ubuntu to docker group)
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








