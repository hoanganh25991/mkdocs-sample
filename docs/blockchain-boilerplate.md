# Installation Guide

!!! warning "Note"
    This installation requires **git** be installed on your server

!!! danger
    Ensure to have XXX if you want to use this in production.
        
    
##Steps

####1. Do a git clone of the deployment 

     git clone https://DigitalBusiness@bitbucket.org/DevOpsDEC/devopsdocs.git
    
####2. Access the server with web browser
      
  
## Helpful commands
####Restarting all containers:
    
    xxx restart
####View logs from all services:
    
    xxx logs


##Install and run Demo DApp locally

Think of this app as a proof of concept and our playground for trying out ideas. While we may eventually reuse pieces of this in production, this is by no means what we envision as the final product. We thought it would be helpful to demonstrate how the various technologies work together from end to end.


####1. Make sure you have `node` version 8.5.0 or greater
```
node --version
```

####2. Download [truffle](http://truffleframework.com/):
```
npm install -g truffle
```
####3. Clone Origin:
```
git clone https://github.com/xxx-dapp blocklancer-dapp && cd blocklancer-dapp
```
####4. Start truffle:
```
truffle develop
```
 This will begin a new Ethereum blockchain. It will output 10 accounts that it has put 100 ETH into, and the mnemonic to generate them.

####5. In the truffle console, type `migrate`. This will compile our contracts and add them to the blockchain.

####6. Install [Metamask Chrome Browser Extension](https://metamask.io/).

####7. Click the Metamask icon in the toolbar, accept terms, and then click `Import Existing DEN`

####8. Enter the seed phrase (Mnemonic):
```
candy maple cake sugar pudding cream honey rich smooth crumble sweet treat
```
 This is the default seed phrase for truffle development.

####9. Click where it says "Ethereum Main Network", select "Custom RPC" and enter `http://localhost:9545/`. This takes us off of the real ETH blockchain and onto our local blockchain. Click the back arrow to return to your account.

 **Be careful not to mix up your test wallet with your real one on the Main Network.**

####10. You should see your first test account now has 100 ETH. (Address of `0x627306090abaB3A6e1400e9345bC60c78a8BEf57`) Additional generated accounts will also have this amount.

####11. In a new terminal tab, install and start the Blocklancer node application.
```
npm install
npm run start
```

####12. A browser will open to http://localhost:3000