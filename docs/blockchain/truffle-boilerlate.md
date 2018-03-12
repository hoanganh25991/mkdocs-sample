# Blockchain Development Boilerlate

## Truffle Introduction
Truffle is the most popular development framework for Ethereum, which supports deploy and test Smart Contract with simple setup.

Truffle features:

+ Built-in smart contract compilation
+ Automated contract testing
+ Scriptable deployment & migrations framework

## Truffle Box react-uport
With `truffle unbox` commands, truffle works as project-generator

We choose `react-uport`, this box adds: react-router, redux and redux-auth-wrapper for authentication powered by [UPort](https://www.uport.me/). The easiest way to get started with UPort. 

## Development

#### 1. Create project
Install truffle globally

```javascript
npm install -g truffle
```

Create project folder directory, go inside & unbox react-uport

```javascript
mkdir [PROJECT_NAME] && 
cd    [PROJECT_NAME] &&
truffle unbox react-uport
```

Project Structure

```
Folders split into 2 main groups:
+ Smart Contract
+ Client Page with React

blockchain-project
├── contracts   <- Directory for Solidity contracts
├── test        <- Directory for test files
├── migrations  <- Directory for scriptable deployment files
├── truffle.js  <- Truffle configuration file

├── src         <- React component
├── public      <- React index page

└── scripts     <- Project scripts
```

#### 2. Client Page
React client page served on port 3000

```javascript
npm run start
```

#### 3. Test
Run tests for both written in Solidity and JavaScript against Smart Contracts

```javascript
truffle test
```

#### 4. Deploy Smart Contract
##### 4.1. On development

###### Update truffle-config.js

```javascript
module.exports = {
  // See <http://truffleframework.com/docs/advanced/configuration>
  // to customize your Truffle configuration!
  networks: {
        development: {
        host: 'localhost',
        port: 9545,
        network_id: '*',
    },
  }
};
```

###### Run private blockchain

```javascript
truffle develop
// Truffle wrap `testrpc` to create private blockchain
// By default, truffle attach private blockchain on port 9545
```

###### Deploy with migrate

```javascript
truffle migrate --network development
```

+ Migration output with Smart Contract's address, example:

```
Running migration: 1_initial_migration.js
  Deploying Migrations...
  ... 0x4e0e6a78bb8fc2288e0d8f860bc48dcb239d4d622c18d1108a18eced6725225a
  Migrations: 0x8cdaf0cd259887258bc13a92c0a6da92698644c0
Saving successful migration to network...
  ... 0xd7bc86d31bee32fa3988f1c1eabce403a1b5d570340a3a9cdba53a472ee8c956
Saving artifacts...
Running migration: 2_deploy_contracts.js
  Deploying SimpleStorage...
  ... 0x1996f862cb21d0f5153dc315a34cd7bc6cbc5871018b8fd04d972921d42cd671
  SimpleStorage: 0x345ca3e014aaf5dca488057592ee47305d9b3e10
Saving successful migration to network...
  ... 0xf36163615f41ef7ed8f4a8f192149a0bf633fe1a2398ce001bf44c43dc7bdda0
Saving artifacts...
```

+ As above output, we can see that `SimpleStorage` address

    0x345ca3e014aaf5dca488057592ee47305d9b3e10

+ Update `migrations/2_deploy_contracts.js` to store Smart Contract programmatically

##### 4.2. On production

@TODO

## Utils with Truffle
Compile the Smart Contract
    
```javascript
truffle compile
// Built files stored under `build/contracts`
```

## FAQ

* __How do I use this with the EthereumJS TestRPC?__

    It's as easy as modifying the config file! [Check out our documentation on adding network configurations](http://truffleframework.com/docs/advanced/configuration#networks).

* __Why is there both a truffle.js file and a truffle-config.js file?__

    `truffle-config.js` is a copy of `truffle.js` for compatibility with Windows development environments. Feel free to it if it's irrelevant to your platform.

* __Where is my production build?__

    The production build will be in the build_webpack folder. This is because Truffle outputs contract compilations to the build folder.

* __Where can I find more documentation?__

    This box is a marriage of [Truffle](http://truffleframework.com/) and a React setup created with [create-react-app](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md). Either one would be a great place to start!
