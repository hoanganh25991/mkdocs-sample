# Installation Guide

!!! warning "Note"
    For Backend, require node version `7.6.0` -> `7.10.0`, using `nvm`
    For Frontend, require `MetaMask` extension on Chrome, FireFox Browser to make Ethereum Transfer

!!! danger
    Ensure to have real Ropsten or Mainnet account with some ETH to deploy in production
    
## Development

####1. Blockchain Infrastructure

Install dependencies & run with pm2

    // At root project directory
    nvm use 7.6.0 && npm install && cd mockserver && npm install
    pm2 start bin/run-demo.js --name=testrpc

####2. Launch Frontend page

    // At root prject directory
    cd client && npm install && npm run start
      
## Frontend Overview
Decentralized Flight Delay insurance on the Ethereum Blockchain:

+ Users can select any flight and apply for an insurance policy in case the flight is late.
+ They pay a fair premium and automagically get a payout as soon as the plane has landed
  (except in the case of a punctal arrival, of course nothing is paid then).


Frontend page contains 2 tabs:

|   | Tab       | Description                                            |
|---|-----------|--------------------------------------------------------|
| 1 | Dashboard | Create new policy, preview policy info                 |
| 2 | Debug     | Fund to new account, update mock data, update contract |


+ Dashboard screen

![dashboard](images/blockchain-flightdelay/blockchain-flightdelay/dashboard-2018-03-11_110408.png)

+ Debug screen

![debug](images/blockchain-flightdelay/blockchain-flightdelay/debug-page-2018-03-11_110427.png)


## Demo Guide
Steps:

1. Using MetaMask to execute transaction
2. Funding demo account advanaced amount (ex: 10 ETH) to make a transaction
3. Create new policy
4. Fake flight status to watch different automagically payment by smart contract

#### 1. Using MetaMask

+ Go to [MetaMask on Chrome Webstore](https://goo.gl/GjRmQS)
+ Click "Add to Chrome" to install extension

![](images/blockchain-flightdelay/install-metamask-2018-03-11_121640.png)

+ Click MetaMask on Chrome Browser to create new Ethereum Account
+ Preview Account's address

![](images/blockchain-flightdelay/review-account-address-2018-03-11_122042.png)


#### 2. Funding demo account
New Account with balance as 0, fund this account, on "Debug" tab

    + At "Funding" section
    + Fill in accounts' address, you want to fund
    + Fill in ETH amount
    + Click Apply

+ Funding screen

![fund success](images/blockchain-flightdelay/fund-new-account-2018-03-11_122508.png)

#### 3. Create New Policy
Create new insurance policy for the flight we want

Fill in Policy Params

    + Customer name, email
    + Flight departure & arrival airport
    + Flight departure date
    + Pick flight we want
    + Pay fair premium
    
Click on `Apply` to accept transfer premium ETH

Example
![](images/blockchain-flightdelay/create-new-policy-2018-03-11_123519.png)

New Policy insurance success created

Preview policy on `Policy List` section

![](images/blockchain-flightdelay/policy-2018-03-11_124033.png)

When flight actually delayed, Customer receive compensation from Smart Contract

Click on policy to review details

![](images/blockchain-flightdelay/policy-compensation-2018-03-11_124604.png)

Customer new balance

![](images/blockchain-flightdelay/new-balance-2018-03-11_125140.png)

+ Note: Balance not exactly equal to compensation amount, because customer has to pay Ethereum Gas to execute Smart Contract


#### 4. Mock Flight Status
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

![](images/blockchain-flightdelay/mock-flight-delay-2018-03-11_130108.png)

Different Compensation Amount, based on `delay minutes` & `fair premium`

![](images/blockchain-flightdelay/different-compensation-2018-03-11_131249.png)
