  # Deploy Quorum Blockchain network in GKE

#### In this POC we will deploy quorum blockchain network in Kubernetes. Quorum is an open-source Ethereum client developed under the LGPL license and written in Go. Qubernetes is a project for generating Quorum network resources, and managing and interacting with a Quorum Kubernetes deployment.
  
  ### Prerequisite:
   - GCP Kubernetes cluster with client
   - Go install in the local system
   - Docker install in local system

1. Following are the steps to deploy the Quorum blockchain network in GKE cluster


* Run the kubectl command to list the Nodes.
```sh
$ kubectl get nodes
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/1.png)
 
* Run the Go command to install the qtcl client tool for quorum blockchain.
```sh
$ GO111MODULE=on go get github.com/ConsenSys/qubernetes/qctl
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/2.png)

* Run the following command to set the path for the config for the network.
```sh
$ export QUBE_CONFIG=$(pwd)/myconfig.yaml 
$ export QUBE_K8S_DIR=$(pwd)/out
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/3.png)

* Run the following command to initialize the network and generate the qubernetes config file.
```sh
$qctl init network --num 3  --consensus ibft --cakeshop --monitor
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/4.png)

**Note**: - If getting error run the command to add the user in Docker group, and start again from step 3.
```sh
$ sudo usermod -a -G docker ubuntu 
$ exec -l $SHELL
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/5.png)

* Run the following command to generate the qubernetes resources for the network.
```sh
$ qctl generate network --create
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/6.png)

* Run the following command to deploy the network as kubernetes resources.
```sh
$ qctl deploy network --wait
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/7.png)

* Run the kubectl command to view the quorum network nodes as pods.
```sh
$ kubectl get po
``` 
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/8.png)

* Run the following command to test the network.
```sh
$ qctl test contract quorum-node1
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/9.png)

* Run the following command to get the Ethereum block number.
```sh
$ qctl geth exec quorum-node1 'eth.blockNumber'
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/10.png)

*	Run the following command to list the quorum nodes.
```sh
$ qctl ls nodes
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/11.png)

2. Add the Nodes and delete the quorum blockchain Network .
*	Run the following command to add a node within the network
```sh
$ qctl add node quorum-node5
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/12.png)

 * Generate the resources for the new node and update to the network
```sh
$ qctl generate network --update
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/13.png)

* Run the following command to deploy the network. This will create Kubernetes resources for the new node.
```sh
$ qctl deploy network
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/14.png)

* Run the following command to attach with the nodes.
```sh
$ qctl geth attach quorum-node1
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/15.png)

* Run the following command to delete the blockchain network.
```sh
$ qctl destroy network
```
![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/deploy%20qourum%20in%20GKE/jpgs/16.png)
