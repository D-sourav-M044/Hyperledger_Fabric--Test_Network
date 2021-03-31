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
### Git
Install the latest version of git if it is not already installed.<br>
`sudo apt-get install git`
### cURL
Install the latest version of cURL if it is not already installed.<br>
`sudo apt-get install curl`
### Docker
Install the latest version of Docker if it is not already installed.<br>
`Sudo apt install docker`
<br>Make permission For Docker<br>
`dockr ps -a`
### Docker-Compose
Install the latest version of Docker-Compose if it is not already installed.<br>
`sudo apt-get -y install docker-compose`
<br>Once installed, confirm that the latest versions of both Docker and Docker Compose executables were installed.<br>
`docker --version`
<br>Docker version 19.03.12, build 48a66213fe<br>
`docker-compose --version`
<br>docker-compose version 1.27.2, build 18f557f9<br>
#### Docker-compose Update
<br> Sometimes latest docker don't comes with the latest version. So you can do it manually with the following process-<br>
<br>Remove the previous version of docker-compose<br>
`sudo apt-get remove docker-compose`
`sudo rm /usr/local/bin/docker-compose`
<br>version set<br>
`VERSION=$(curl --silent https://api.github.com/repos/docker/compose/releases/latest | jq .name -r)`
<br>Installation<br>
`DESTINATION=/usr/local/bin/docker-compose`
`sudo curl -L https://github.com/docker/compose/releases/download/${VERSION}/docker-compose-$(uname -s)-$(uname -m) -o $DESTINATION`
`sudo chmod 755 $DESTINATION`





