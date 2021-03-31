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
 **You can find the scripts to bring up the network in the test-network directory of the fabric-samples repository. Navigate to the test network directory by using the following command:**
 <br>
 <br>
 `cd fabric-samples/test-network`
 <br>
 <br>
 **From inside the test-network directory, run the following command to remove any containers or artifacts from any previous runs:**
 <br>
 <br>
 `./network.sh down`
 <br>
 <br>
 **You can then bring up the network by issuing the following command. You will experience problems if you try to run the script from another directory:**
 <br>
 <br>
 `./network.sh up`
 <br>
 <br>
**After your test network is deployed, you can take some time to examine its components. Run the following command to list all of Docker containers that are running on your machine. You should see the three nodes that were created by the network.sh script:**
<br>
<br>
`docker ps -a`
<br>
<br
**You can use the network.sh script to create a channel between Org1 and Org2 and join their peers to the channel. Run the following command to create a channel with the default name of mychannel:**
<br>
<br>
`./network.sh createChannel`
<br>
<br>
**You can also use the channel flag to create a channel with custom name. As an example, the following command would create a channel named channel1:**
<br>
<br>
`./network.sh createChannel -c channel1`
<br>
<br>
**After you have used the network.sh to create a channel, you can start a chaincode on the channel using the following command:**
`./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go -ccl go`
<br>
<br>
**Make sure that you are operating from the test-network directory. If you followed the instructions to install the Samples, Binaries and Docker Images, You can find the peer binaries in the bin folder of the fabric-samples repository. Use the following command to add those binaries to your CLI Path:**
<br>
<br>
`export PATH=${PWD}/../bin:$PATH`
<br>
<br>
**You also need to set the FABRIC_CFG_PATH to point to the core.yaml file in the fabric-samples repository:**
<br>
<br>
`export FABRIC_CFG_PATH=$PWD/../config/`
<br>
<br>
**You can now set the environment variables that allow you to operate the peer CLI as Org1:**
<br>
<br>
`export CORE_PEER_TLS_ENABLED=true`
`export CORE_PEER_LOCALMSPID="Org1MSP"`
`export CORE_PEER_TLS_ROOTCERT_FILE=${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt`
`export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp`
`export CORE_PEER_ADDRESS=localhost:7051`
<br>
<br>
**Run the following command to initialize the ledger with assets:**
<br>
<br>
`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n basic --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"InitLedger","Args":[]}'`
<br>
<br>
**You can now query the ledger from your CLI. Run the following command to get the list of assets that were added to your channel ledger:**
<br>
<br>
`peer chaincode query -C mychannel -n basic -c '{"Args":["GetAllAssets"]}'`
<br>
<br>
**Chaincodes are invoked when a network member wants to transfer or change an asset on the ledger. Use the following command to change the owner of an asset on the ledger by invoking the asset-transfer (basic) chaincode:**
<br>
<br>
`peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n basic --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"TransferAsset","Args":["asset6","Christopher"]}'`
<br>
<br>
**you can do all the same process for org2 also**
<br>
**After you have done all of this successfully-down the network**
<br>
<br>
`./network.sh down`
<br>
<br>
