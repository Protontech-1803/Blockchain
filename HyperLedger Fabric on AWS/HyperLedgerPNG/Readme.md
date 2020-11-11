# Build and Deploy a Supply Chain Solution using Hyperledger Fabric on AWS Managed Blockchain

This POC illustrates how to build, deploy and track the Supply Chain for Hyperledger Fabric on AWS Managed Blockchain.

The following are the steps to query the Chaincode by creating Hyperledger Fabric Channel in in AWS Managed Blockchain network:

1.	Create the Managed Blockchain Network and First member using Hyperledger Fabric framework in AWS console.
    ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/CreateNetwork.jpg)

2.	Create an interface VPC endpoint in the Managed Blockchain console.
    ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/VPCendpoint.jpg)

3.	Set up the Hyperledger Fabric CA Client 
    
    a.	Create an EC2 Instance using Amazon Linux AMI, connect the instance to putty and install packages such as telnet, emacs, docker, docker-compose, go and git.
    
    b.	Verify the connectivity to the Hyperledger Fabric CA by listing the members in Managed Blockchain network
        ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/GetMember1.jpg)
 
    c.	Set up the Hyperledger fabric CA client by connecting the instance to Hyperledger Fabric CA using telnet command.
         ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/Telnet.jpg)
    
    
4.	Enroll the administrative user to the member’s certificate authority (CA).
   
    a.	Create the certificate file by providing the region of managed blockchain.
         ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/CertificateFile.jpg)
         
    b.	Enroll the administrative user by using the CA endpoint, administrator profile and the certificate file by using the fabric-ca-client enroll command.
        ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/FabricEnroll.jpg)
        
    c.	Configure and run the Docker Compose to start the Hyperledger Fabric CLI. Verify the CLI is running successfully by listing the Docker containers.
    
      ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/DockerContainers.jpg)
        
    d.	Copy the certificates for the MSP 

5.	Create a Peer Node in the member of the Managed Blockchain network

    ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/PeerNode.jpg)

6.	Create a Hyperledger Fabric Channel in AWS Managed Blockchain 
    
    a.	Create and generate a configuration file for the Hyperledger Fabric Channel creation. It creates a CHANNEL.pb block file.
        ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/Channel1.jpg)
        
    b.	Set the environment variables for the Orderer
    
    c.	Create a channel using the variables that is created and config peer block.
        ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/Channel2.jpg)

7.	Join the Peer Node to the channel created
    ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/JoinPeer.jpg)

8.	Run the Chaincode in AWS Managed Blockchain

    a.	Install and run the Chaincode on the Peer node
        ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/Chaincode1.jpg)
    
    b.	Instantiate the Chaincode on the Peer node
        ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/Chaincode2.jpg)
    
    c.	Query and invoke the chaincode on the Peer node

9.	View the fabric metrics, Chaincode logs In the AWS Peer node console
    ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/ChaincodeLogs.jpg)

10.	Propose the Invitation from the member to AWS account by specifying the ID of AWS account 
    ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/ProposalInvitation.jpg) 

11.	Vote for the proposal as ‘YES’ in the AWS Managed Blockchain console.

12.	View the Proposal Invitations proposed by the member in the Managed Blockchain network.
    ![Alt text](https://github.com/Protontech-1803/Blockchain/blob/main/HyperLedger%20Fabric%20on%20AWS/HyperLedgerPNG/GetMember2.jpg)

