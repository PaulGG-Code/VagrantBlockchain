Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y python3 python3-pip git gcc make libssl-dev

    # Installing nvm 
    mkdir nvm-installer
    cd nvm-installer
    wget https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh 
    bash install.sh
    export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
    [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
    cd ..

    # Installing node and npm
    nvm install node

    # Installing Mythril for Ethereum smart contract analysis
    pip3 install mythril    

    # Installing Oyente for smart contract analysis
    git clone https://github.com/melonproject/oyente.git
    cd oyente
    pip3 install -r requirements.txt
    cd ..

    # Install surya for Solidity static code analysis
    npm install -g surya
    
    # Downloading ethereum graph debugger
    git clone https://github.com/fergarrui/ethereum-graph-debugger.git

    # Downloading SCSVS
    git clone https://github.com/securing/SCSVS.git

    # Installing Slither for Solidity static analysis
    pip3 install slither-analyzer
    
    # Installing Truffle Framework for Ethereum development
    npm install -g truffle

    # Installing Hardhat
    npm install --save-dev hardhat

    # Installing solgraph
    npm install -g solgraph

    # Installing Ganache for Ethereum environment
    
    # Installing solhint
    npm install -g solhint

    # Installing Ethlint
    npm install -g ethlint

    # Installing Manticore
    pip3 install manticore

    # Downloading solcurity checklist
    git clone https://github.com/transmissions11/solcurity.git

    # Install abi-guesser
    npm i @openchainxyz/abi-guesser

    # Installing crytic-compile
    pip3 install crytic-compile

    # Installing Midusa
    wget https://github.com/crytic/medusa/releases/download/v0.1.0/medusa-linux-x64.zip

    # Any additional tools can be installed here
  SHELL
end
