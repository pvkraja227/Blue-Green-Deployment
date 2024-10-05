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

jenkins/nexus.sonarqube - t2.med
sudo apt update

Jenkins

install jdk17
install jenkins









