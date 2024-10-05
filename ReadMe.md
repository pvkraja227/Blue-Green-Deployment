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
