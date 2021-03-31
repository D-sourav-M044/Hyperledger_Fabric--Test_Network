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
# **Linux**
------------
---
<span style="color:blue">Git</span>.
---
Install the latest version of git if it is not already installed.<br>
<span style="color:blue">hello</span>.
<br>
`sudo apt-get install git`
<br>
<br>
<br>
## cURL
---
Install the latest version of cURL if it is not already installed.<br><br>
`sudo apt-get install curl`
<br>
<br>
## Docker
---
Install the latest version of Docker if it is not already installed.<br><br>
`Sudo apt install docker`
<br><br>Make permission For Docker<br><br>
`dockr ps -a`
<br>
<br>
## Docker-Compose
---
Install the latest version of Docker-Compose if it is not already installed.<br><br>
`sudo apt-get -y install docker-compose`
<br><br>Once installed, confirm that the latest versions of both Docker and Docker Compose executables were installed.<br><br>
`docker --version`
<br><br>Docker version 19.03.12, build 48a66213fe<br><br>
`docker-compose --version`
<br><br>docker-compose version 1.27.2, build 18f557f9<br><br>
  #### Docker-compose Update
Sometimes latest docker don't comes with the latest version. So you can do it manually with the following process-<br>
<br>Remove the previous version of docker-compose<br><br>
`sudo apt-get remove docker-compose`
`sudo rm /usr/local/bin/docker-compose`
<br><br>version set<br><br>
`VERSION=$(curl --silent https://api.github.com/repos/docker/compose/releases/latest | jq .name -r)`
<br><br>Installation<br><br>
`DESTINATION=/usr/local/bin/docker-compose`
`sudo curl -L https://github.com/docker/compose/releases/download/${VERSION}/docker-compose-$(uname -s)-$(uname -m) -o $DESTINATION`
`sudo chmod 755 $DESTINATION`
<br>
<br>
## Docker Daemon
---
Make sure the Docker daemon is running.<br><br>
`sudo systemctl start docker`
<br><br>  Optional: If you want the Docker daemon to start when the system starts, use the following:<br><br>
`sudo systemctl enable docker`
<br>
<br>
## Docker Group
---
Add your user to the Docker group.<br><br>
`sudo usermod -a -G docker <username>`
<br>
<br>
## Go
---
Optional: Install the latest version of Go if it is not already installed (only required if you will be writing Go chaincode or SDK applications).<br><br>
`sudo apt install golang-go`
<br><br>With this command you can't have golang with the latest version sometimes<br>
<br>For the latest version of Go you have go through these following process<br><br>
**1. Download the Golang**
<br> Because the Golang package is not always up to date in the Ubuntu repository, it's preferred to download the official website's latest version.<br>
<br>Change to a temporary directory for the installation.<br><br>
`cd /tmp`
<br><br>Select the latest package for your architecture from https://golang.org/dl/ and download it.<br><br>
`wget https://golang.org/dl/go1.<VERSION_NUMBER>.linux-amd64.tar.gz`
<br><br> use the requied version at the place of <VERSION_NUMBER><br> 
For example - version 1.15.4<br>
`wget https://golang.org/dl/go1.15.4.linux-amd64.tar.gz`
<br>**2. Extract to the Installation Location**<br>
Extract the Golang executable to /usr/local.<br><br>
`sudo tar -C /usr/local -xzf go1.<VERSION_NUMBER>.linux-amd64.tar.gz`
<br>**3. Set Environment**<br>
<br>To use Golang, set the required environment variables in your .profile.<br><br>
`echo "export PATH=$PATH:/usr/local/go/bin" >> ~/.profile`
`echo "export GOPATH=~/.go" >> ~/.profile`
<br><br>Reload your profile to begin using Golang.<br><br>
`source ~/.profile`
<br><br>**4. Test the Installation**<br>
Verify you installed the expected version of Golang.<br><br>
`go version`
<br>
<br>
## Node.js
---
Install the latest version of nodejs if it is not already installed.<br><br>
`sudo apt-get install nodejs`
<br>
<br>

## npm
---
Install the latest version of npm if it is not already installed.<br><br>
`sudo apt-get install npm`

<br>
<br>
<br>
<br>
<br>

# Download Fabric samples, docker images, and binaries.
---

**Make a new directory for latest fabric sample**
<br><br>
`mkdir hyper`
<br>
`cd hyper`
<br><br>
**use these following two commands to avoid interruptions**<br><br>
`git config --global core.autocrlf false`
<br>
`git config --global core.longpaths true`

**Download the latest release of Fabric samples, docker images, and binaries.**
<br><br>
`curl -sSL https://bit.ly/2ysbOFE | bash -s`
<br><br>**To download a specific release, pass a version identifier for Fabric and Fabric CA Docker images. The command below demonstrates how to download the latest production releases -**<br><br>
`curl -sSL https://bit.ly/2ysbOFE | bash -s -- <fabric_version> <fabric-ca_version>`
<br>
`curl -sSL https://bit.ly/2ysbOFE | bash -s -- 2.3.1 1.4.9`
<br><br> 
**If you get server error, you can use these following commands-**
<br><br>
`curl -sSL https://raw.githubusercontent.com/hyperledger/fabric/master/scripts/bootstrap.sh | bash -s -- 2.3.1 1.4.9`
       <br><br> you can also use version 1.1.0<br> 
 <br>
 <br>
 <br>
 <br>
 # Using the Fabric test network
 ---
 
