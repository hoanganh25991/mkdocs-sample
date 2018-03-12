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

# Flight Delay Insurance
Decentralized Flight Delay insurance on the Ethereum Blockchain:

+ Users can select any flight and apply for an insurance policy in case the flight is late.
+ They pay a fair premium and automagically get a payout as soon as the plane has landed
  (except in the case of a punctal arrival, of course nothing is paid then).

## Frontend Overview
Frontend page contains 2 tabs:

|   | Tab       | Description                                            |
|---|-----------|--------------------------------------------------------|
| 1 | Dashboard | Create new policy, preview policy info                 |
| 2 | Debug     | Fund to new account, update mock data, update contract |


+ Dashboard screen

![dashboard](https://goo.gl/YBnB7r)

+ Debug screen

![debug](https://goo.gl/53Y4LQ)


## Demo Guide
Steps:

1. Using MetaMask to execute transaction
2. Funding demo account advanaced amount (ex: 10 ETH) to make a transaction
3. Create new policy
4. Fake flight status to watch different automagically payment by smart contract

### Step 1: Using MetaMask

+ Go to [MetaMask on Chrome Webstore](https://goo.gl/GjRmQS)
+ Click "Add to Chrome" to install extension

![](https://goo.gl/1Gb6QU)

+ Click MetaMask on Chrome Browser to create new Ethereum Account
+ Preview Account's address

![](https://goo.gl/WgtUcj)


### Step 2: Funding demo account
New Account with balance as 0, fund this account, on "Debug" tab

    + At "Funding" section
    + Fill in accounts' address, you want to fund
    + Fill in ETH amount
    + Click Apply

+ Funding screen

![fund success](https://goo.gl/BSwchr)

### Step 3: Create New Policy
Create new insurance policy for the flight we want

Fill in Policy Params

    + Customer name, email
    + Flight departure & arrival airport
    + Flight departure date
    + Pick flight we want
    + Pay fair premium
    
Click on `Apply` to accept transfer premium ETH

Example
![](https://goo.gl/nBDGdG)

New Policy insurance success created

Preview policy on `Policy List` section

![](https://goo.gl/1mT3C8)

When flight actually delayed, Customer receive compensation from Smart Contract

Click on policy to review details

![](https://goo.gl/H8qpYq)

Customer new balance

![](https://goo.gl/CdQNXv)

+ Note: Balance not exactly equal to compensation amount, because customer has to pay Ethereum Gas to execute Smart Contract


### Step 4: Mock Flight Status
Base on flight delay in minute, Smart Contract define `how much` should be compensated

There are 3 levels:

|   | Level | Delay in minutes | Payout    |
|---|-------|------------------|-----------|
| 1 |       | <15   minutes    | No Payout |
| 2 | I     | 15-30 minutes    | Payout    |
| 3 | II    | 30-45 minutes    | Payout    |
| 4 | III   | > 45  minutes    | Payout    |


To mock flight status, on "Debug" tab

	+ At "Fake Status" section
	+ Fill in flight's carrier, ex: "HA"
	+ Fill in flight's number, ex: "21"
	+ Fill in delay in minutes, ex: "16"
	+ Click Apply
	
Example

![](https://goo.gl/nHP4pm)

Different Compensation Amount, based on `delay minutes` & `fair premium`

![](https://goo.gl/gu496p)
