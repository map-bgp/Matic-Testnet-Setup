# Installation of GO 

	sudo snap install go

# set the GO paths
	curl https://gist.githubusercontent.com/vaibhavchellani/cbe0fa947dc0a6557cb9583d081ff8ce/raw/d47b3df14ccffdd7a965e44c39fb5ec235360166/new.sh > install_go.sh

	bash install_go.sh

# install RabbitMq

	sudo apt-get install rabbitmq-server


# Starting the RabbitMq Server

	sudo service rabbitmq-server start

# installed the Make and other dependencies 

	sudo apt-get install build-essential

# install Heimdall

	mkdir -p $GOPATH/src/github.com/maticnetwork
	cd $GOPATH/src/github.com/maticnetwork
	git clone https://github.com/maticnetwork/heimdall
	cd heimdall

	// Checkout to a public-testnet version.
	$ git checkout v0.3.0
	make install

# Check Heimdall Installation 

	heimdalld --help

# This below command setups a new node

	heimdalld init
	{
  "chain_id": "heimdall-OkvnJT",
  "node_id": "d294831a58712a04d1c6080a7787600b5d7d35da"
}

	echo "export HEIMDALLDIR=~/.heimdalld" >> ~/.bashrc
	source ~/.bashrc

# install Bor

	mkdir -p $GOPATH/src/github.com/maticnetwork

	cd $GOPATH/src/github.com/maticnetwork

	git clone https://github.com/maticnetwork/bor

	$ cd bor

	// Checkout to a public-testnet version.
	$ git checkout v0.2.6
	$ make bor

-- bor binary is avaliable in build/bin/bor

# Getting Heimdall genesis config#
	cd ..

	git clone https://github.com/maticnetwork/public-testnets

	cd public-testnets/CS-2008/without-sentry

	echo "export CONFIGPATH=$PWD" >> ~/.bashrc

	source ~/.bashrc

	// copy heimdall genesis file to config directory
	cp $CONFIGPATH/heimdall/config/genesis.json  $HEIMDALLDIR/config/genesis.json

	// copy config file to config directory
	cp $CONFIGPATH/heimdall/config/heimdall-config.toml $HEIMDALLDIR/config/heimdall-config.toml

# Added the infura URL 
	Add your API key in file ~/.heimdalld/config/heimdall-config.toml under the key "eth_RPC_URL" as https://goerli.infura.io/v3/a06215a0c7614477a5f1a1ef08534463

# Added the validators private key
	heimdallcli generate-validatorkey <Your Ethereum/Goerli wallet private key>

	mv ./priv_validator_key.json $HEIMDALLDIR/config

# added a persistent peer to the config.toml
1f1b21cacf3ac8a1e1402646e023811b250e2d76@54.211.245.52:26656
~/.heimdalld/config/config.toml under persistent_peers with the format NodeID@IP:PORT or NodeID@DOMAIN:PORT


# Before Starting heimdall , configure logs:
	heimdalld start
	cd
	mkdir ~/.heimdalld/logs/

# verify Commit ids :
	// In bor folder and heimdall folder and compare the commit ids
	git log 

# Deploy root contracts:
	export MNEMONIC="257bc7bbb735c3cb39d0b809f9d95dc5e5385ba7444f0459d231cfd1f1f954ff"

# installing nvm 

curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | bash

# install node js and Truffle 

# Later setup matic contracts
$ git clone https://github.com/maticnetwork/contracts
$ cd contracts