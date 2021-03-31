# Hyperledger_Fabric--Test_Network
 Describes the process of installing hyperledger fabric on local machine. Also contains the process of testing the test network.
 
## # The Fabric application stack has five layers:

 ## Fabric Application Stack
         1. Prerequisite software: the base layer needed to run the software, for example, Docker.
         2. Fabric and Fabric samples: the Fabric executables to run a Fabric network along with sample code.
         3. Contract APIs: to develop smart contracts executed on a Fabric Network.
         4. Application SDKs: to develop your blockchain application.
         5. The Application: your blockchain application will utilize the Application SDKs to call smart contracts running on a Fabric network.
 
# Prerequisites-
## **Linux**
------------
---
### Git
---
Install the latest version of git if it is not already installed.<br>
<br>
`sudo apt-get install git`
<br>
<br>
<br>
<br>

### cURL
---
Install the latest version of cURL if it is not already installed.<br><br>
`sudo apt-get install curl`


### Docker
---
Install the latest version of Docker if it is not already installed.<br><br>
`Sudo apt install docker`
<br><br>Make permission For Docker<br><br>
`dockr ps -a`
### Docker-Compose
Install the latest version of Docker-Compose if it is not already installed.<br>
`sudo apt-get -y install docker-compose`
<br>Once installed, confirm that the latest versions of both Docker and Docker Compose executables were installed.<br>
`docker --version`
<br>Docker version 19.03.12, build 48a66213fe<br>
`docker-compose --version`
<br>docker-compose version 1.27.2, build 18f557f9<br>
  ##### Docker-compose Update
Sometimes latest docker don't comes with the latest version. So you can do it manually with the following process-<br>
<br>Remove the previous version of docker-compose<br>
`sudo apt-get remove docker-compose`
`sudo rm /usr/local/bin/docker-compose`
<br>version set<br>
`VERSION=$(curl --silent https://api.github.com/repos/docker/compose/releases/latest | jq .name -r)`
<br>Installation<br>
`DESTINATION=/usr/local/bin/docker-compose`
`sudo curl -L https://github.com/docker/compose/releases/download/${VERSION}/docker-compose-$(uname -s)-$(uname -m) -o $DESTINATION`
`sudo chmod 755 $DESTINATION`
### Docker Daemon
Make sure the Docker daemon is running.<br>
`sudo systemctl start docker`
<br>  Optional: If you want the Docker daemon to start when the system starts, use the following:<br>
`sudo systemctl enable docker`
### Docker Group
Add your user to the Docker group.<br>
`sudo usermod -a -G docker <username>`
### Go
Optional: Install the latest version of Go if it is not already installed (only required if you will be writing Go chaincode or SDK applications).<br>
`sudo apt install golang-go`
<br>With this command you can't have golang with the latest version sometimes<br>
<br>For the latest version of Go you have go through these following process<br>
**1. Download the Golang**
<br> Because the Golang package is not always up to date in the Ubuntu repository, it's preferred to download the official website's latest version.<br>
<br>Change to a temporary directory for the installation.<br>
`cd /tmp`
<br>Select the latest package for your architecture from https://golang.org/dl/ and download it.<br>
`wget https://golang.org/dl/go1.<VERSION_NUMBER>.linux-amd64.tar.gz`
<br> use the requied version at the place of <VERSION_NUMBER><br> 
For example - version 1.15.4
`wget https://golang.org/dl/go1.15.4.linux-amd64.tar.gz`
<br>**2. Extract to the Installation Location**<br>
Extract the Golang executable to /usr/local.<br>
`sudo tar -C /usr/local -xzf go1.<VERSION_NUMBER>.linux-amd64.tar.gz`
<br>**3. Set Environment**<br>
<br>To use Golang, set the required environment variables in your .profile.<br>
`echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.profile`
`echo "export GOPATH=~/.go" >> ~/.profile`
<br>Reload your profile to begin using Golang.<br>
`source ~/.profile`
<br>**4. Test the Installation**
Verify you installed the expected version of Golang.<br>
`go version`







