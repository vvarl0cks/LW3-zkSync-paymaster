# Building a custom paymaster on zkSync Era

In this lesson, you'll learn about paymasters and how you can set them up on zkSync Era to accept any ERC-20 token as gas. This can be useful for your dApps if you want to give users the flexibility to use your site without converting the tokens they have to ETH, hence improving the overall user-experience.  

## What is a paymaster?  

A paymaster is essentially a contract that is used to either sponsor gas fees or accept any ERC20 token instead of just ETH. EIP 4337 describes how a custom paymaster should function. Having a paymaster is very useful when you're using account abstraction, since it allows you to abstract away the process of collecting gas fee from the user. This leads to a decrease in the user drop-off percentage as it makes your dApp user friendly.  

## So.. what are we building?

- This tutorial shows you how to build a custom paymaster that allows users to pay fees with any ERC20 token. You will:
- Create a paymaster that assumes a single unit of an ERC20 token is enough to cover any transaction fee.  
- Create the ERC20 token contract and send some tokens to a new wallet.  

Send a `mint` transaction from the newly created wallet via the paymaster. Although the transaction normally requires ETH to pay the gas fee, our paymaster executes the transaction in exchange for 1 unit of the ERC20 token.  

## Pre-requisites

- A Node.js installation running Node.js version 16. https://nodejs.org/en/download  
- Some familiarity with deploying smart contracts on zkSync. If not, please refer to the first section of the quickstart tutorial. https://era.zksync.io/docs/dev/building-on-zksync/hello-world.html  
- Some background knowledge on the concepts covered by the tutorial would be helpful too. Have a look at the following docs:  
- Account abstraction protocol. https://era.zksync.io/docs/reference/concepts/aa.html  
- Introduction to system contracts. https://era.zksync.io/docs/reference/architecture/contracts/system-contracts.html  
- Smart contract deployment on zkSync Era. https://era.zksync.io/docs/reference/architecture/contracts/contract-deployment.html  
- Gas estimation for transactions guide.   
- You should also know how to get your private key from your MetaMask wallet

## Let's get buidling🛠️🛠️

Code for the "Build a custom paymaster" tutorial from the [zkSync v2 documentation](https://v2-docs.zksync.io/dev/).

You can find a full step-by-step guide to build this project [in this article](https://v2-docs.zksync.io/dev/tutorials/custom-paymaster-tutorial.html#prerequisite).

## Installation and compilation

You need Node.js and Yarn.

Install all dependencies with `yarn add`.

Compile contracts with `yarn hardhat compile`

## Deployment and usage

To run the scripts that deploy, use the `zksync-deploy` command:

- `yarn hardhat deploy-zksync --script deploy-paymaster.ts`: deploys the contracts
- `yarn hardhat deploy-zksync --script use-paymaster.ts`: executes the `use-paymaster.ts` script.

## Support

Check out the [common errors section in the tutorial](https://v2-docs.zksync.io/dev/tutorials/custom-paymaster-tutorial.html#prerequisite), open an issue, or [contact us on Discord](https://discord.com/invite/px2aR7w).   

## Deploy

```shell
(main) $ yarn hardhat deploy-zksync --script deploy-paymaster.ts
yarn run v1.22.19
$ /workspace/LW3-zkSync-paymaster/node_modules/.bin/hardhat deploy-zksync --script deploy-paymaster.ts
Empty wallet's address: 0x18D60ea654c1850B28dcD660068a27B4eBa4F876
Empty wallet's private key: <PRIVATE KEY>
ERC20 address: 0xD10D3dAB526F4FF50c24880EB8Cc630082c8c1f3
Paymaster address: 0xF16f3DFbEDd9De27AEd27737cc4E9C07794D16A0
Funding paymaster with ETH
Paymaster ETH balance is now 6000000000000000
Minted 3 tokens for the empty wallet
Done!
Done in 15.31s.
gitpod /workspace/LW3-zkSync-paymaster (main) $ 
```

```shell
(main) $ yarn hardhat deploy-zksync --script use-paymaster.ts
yarn run v1.22.19
$ /workspace/LW3-zkSync-paymaster/node_modules/.bin/hardhat deploy-zksync --script use-paymaster.ts
ERC20 token balance of the empty wallet before mint: 3
Paymaster ETH balance is 6000000000000000
Transaction fee estimation is :>>  131382500000000
Minting 5 tokens for empty wallet via paymaster...
Paymaster ERC20 token balance is now 1
Paymaster ETH balance is now 5947990500000000
ERC20 token balance of the empty wallet after mint: 7
Done in 6.72s.
```
