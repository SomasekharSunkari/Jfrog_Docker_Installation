# Jfrog_Docker_Installation


##Install in Amazon Ubuntu
#!/bin/bash
sudo apt update -y


sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -


sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic


stable" -y



sudo apt update -y


apt-cache policy docker-ce -y

sudo apt install docker-ce -y


#sudo systemctl status docker
sudo chmod 777 /var/run/docker.sock

##Install in Amazon Ubuntu

sudo usermod -aG docker $USER
docker pull docker.bintray.io/jfrog/artifactory-oss:latest
sudo mkdir -p /jfrog/artifactory


sudo chown -R 1030 /jfrog/


docker run --name artifactory -d -p 8081:8081 -p 8082:8082 -v

wget -O jfrog-deb-installer.tar.gz "https://releases.jfrog.io/artifactory/jfrog-prox/org/artifactory/pro/deb/jfrog-platform-trial-prox/[RELEASE]/jfrog-platform-trial-prox-[RELEASE]-deb.tar.gz"
tar -xvzf jfrog-deb-installer.tar.gz
cd jfrog-platform-trial-pro*
sudo ./install.sh
sudo systemctl start artifactory.service

/jfrog/artifactory:/var/opt/jfrog/artifactory docker.bintray.io/jfrog/artifactory-oss:latest
