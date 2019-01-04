Blockchain Workshop


1. Software Prerequisites

    - docker ps
    - git
    - node -v
    - go
    - npm -v
    - Visual studio Code

2. Fabric Samples
	
	> curl -sSL http://bit.ly/2ysbOFE | bash -s 1.4.0-rc2
 3. Clone Smartcontract
	
	> git clone https://github.com/vinoth-kumar-m/iit-workshop.git
	
4. Shim Setup
	
	> go get -u github.com/hyperledger/fabric/core/chaincode/shim

	> go build

5. Terminal 1
	
	> cd fabric-samples/chaincode-docker-devmode

	> docker-compose -f docker-compose-simple.yaml up

6. Terminal 2 
	> docker exec -it chaincode bash

	> mkdir iit

	> cd iit


	Copy the smart contract which was cloned into earlier into iit folder

	> go build

	> CORE_PEER_ADDRESS=peer:7052 CORE_CHAINCODE_ID_NAME=mycc:0 ./iit

7. Terminal 3

	> docker exec -it cli bash

	> peer chaincode install -p chaincodedev/chaincode/iit -n mycc -v 0

	> peer chaincode instantiate -n mycc -v 0 -c '{"Args":["a","10"]}' -C myc


	Invoke
	
	> peer chaincode invoke -C myc -n mycc -c '{"Args":["initMarble","marble1","blue","35","tom"]}'

	> peer chaincode invoke -C myc -n mycc -c '{"Args":["initMarble","marble2","red","50","tom"]}'

	> peer chaincode invoke -C myc -n mycc -c '{"Args":["initMarble","marble3","blue","70","tom"]}'


	Query
    
	> peer chaincode query -C myc -n mycc -c '{"Args":["readMarble","marble1"]}'