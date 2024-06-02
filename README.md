### zkSync HandBbook for Developers


What is zkSync and What it does
To start with, we all know gas fee is a brick wall that afflicts developers and traders in Ethereum. Complaints and frustration is a regular rhythm in the world of Ethereum especially with the Eth token (nicknamed the hot boy token or big ballers token).



But today zkSync says lament no more, bye bye to exorbitant fees paid for gas.

zkSync is a Layer 2 encompassing solution for Ethereum that significantly improves transaction speed and reduces costs.



zkSync is a Layer 2 encompassing solution for Ethereum that significantly improves transaction speed and reduces costs. By using zero-knowledge rollups, zkSync processes transactions off-chain and bundles them into a single proof, which is then verified on-chain. This method ensures Ethereum’s security while enhancing its efficiency and accessibility.



What does this mean in simpler terms
Imagine Ethereum as a busy highway with lots of cars (transactions) traveling on it. Sometimes, this highway gets congested, causing delays and high tolls (transaction fees).

Now, zkSync is like a special fast lane (Layer 2 solution) built beside the main highway. It helps to speed up the traffic and lower the toll costs. It does this by grouping many transactions together (bundling them) and proving they're all okay without actually driving each one down the main highway. Instead, it just sends one proof (like a ticket) to Ethereum's main highway, where it gets checked and approved. This way, Ethereum's security is still ensured, but things move faster and cheaper for everyone using zkSync.



The problem it solves
Ethereum sometimes gets crowded and expensive when a lot of people are using it at once. But zkSync helps out by:

Cutting Costs: It makes transactions cheaper by doing some of the work off the main Ethereum road, so you pay less in gas fees.

Speeding Things Up: Imagine it like adding more lanes to the Ethereum highway. With zkSync, lots of transactions can go through quickly, easing the traffic jams.

Keeping Things Safe: Even though zkSync does some processing off the main Ethereum road, it still keeps everything secure using fancy math tricks called zero-knowledge proofs. So, your transactions stay safe and sound.



Challenges I ran into
1. Learning Curve: Understanding how zkSync works and its special math tricks (zero-knowledge proofs) took more time compared to regular Ethereum development.



2. Compatibility Hurdles: Making sure my code played nicely with tools other developers use on Ethereum, like Hardhat and OpenZeppelin, was a bit tricky at first.



3. Testing Complications: Fixing and testing my code on zkSync was tougher than on regular Ethereum because things work differently when you're dealing with Layer 2 instead of Layer 1.



Technologies Used in zkSync Development 
1. zkSync:

  - zkSync CLI

  - zkSync bridge

  - zkSync Sepolia explorer



2. Ethereum Development Frameworks:

  - Ethers.js: JavaScript library for interacting with the Ethereum blockchain.

  - Hardhat: Ethereum development environment to compile, deploy, test, and debug Ethereum software.



3. Solidity:

  - Used to write our smart contracts



4. Node.js Package Managers (npm)

 

5. Hardhat 



6. Compilers:

  - zksolc: Custom Solidity compiler for zkSync.

  - solc: Standard Solidity compiler used alongside zksolc.



7. JavaScript and TypeScript

  

How to build, deploy and Interact with a Smart Contract on zkSync


We will walk you through the process of deploying and utilising a smart contract on zkSync in this tutorial. creating smart contracts, deploying them on zkSync, and configuring your development environment. This all-inclusive guide explains everything.



Fund your wallet:
You can get ETH directly into zkSync testnet following this link: https://faucet.chainstack.com/zksync-testnet-faucet or by getting sepoliaETH from the faucets: https://docs.zksync.io/build/tooling/network-faucets.html and bridging it using: https://portal.zksync.io/bridge/?network=sepolia. Feel free to check your balance here https://sepolia.explorer.zksync.io



Fund Your Wallet:
1. Obtain testnet ETH for zkSync using Chainstack's faucet.
2. Alternatively, get SepoliaETH from available faucets and bridge it to zkSync Sepolia testnet.
3. Check your balance using the zkSync Sepolia explorer.

Create the Project:
1. Run npx zksync-cli create hello-zksync to create a new project.
2. Choose the following options:
   - Project type: Contracts
   - Ethereum framework: Ethers v6
   - Template: Hardhat + Solidity
   - (Optional) Private key for deploying contracts
   - Package manager: yarn
3. The project structure includes:
   - hardhat.config.ts for general configuration.
   - /contracts for smart contracts, including examples like ERC20, NFT, and Greeter.
   - /deploy for deployment scripts.
4. Focus on the Greeter.sol contract in /contracts.

Compile the Contract:
1. Navigate to the project directory: cd hello-zksync.
2. Compile the contracts with yarn compile.
3. The output will show the compiled artifacts in the /artifacts-zk folder.

Deploy and Verify:
1. Use the deployment script in /deploy/deploy.ts:
   
TypeScript

   import { deployContract } from "./utils";

   export default async function () {
     const contractArtifactName = "Greeter";
     const constructorArguments = ["Hi there!"];
     await deployContract(contractArtifactName, constructorArguments);
   }
   
2. Run the deployment script with yarn deploy.
3. The script will deploy the contract and verify it, providing details like the contract address and verification ID.

Interact with the Contract:
1. Update the CONTRACT_ADDRESS in /deploy/interact.ts:
   
TypeScript

   import * as hre from "hardhat";
   import { getWallet } from "./utils";
   import { ethers } from "ethers";

   const CONTRACT_ADDRESS = "";

   export default async function () {
     console.log(`Running script to interact with contract ${CONTRACT_ADDRESS}`);
     const contractArtifact = await hre.artifacts.readArtifact("Greeter");
     const contract = new ethers.Contract(CONTRACT_ADDRESS, contractArtifact.abi, getWallet());
     const response = await contract.greet();
     console.log(`Current message is: ${response}`);
     const transaction = await contract.setGreeting("Hello people!");
     console.log(`Transaction hash: ${transaction.hash}`);
     await transaction.wait();
     console.log(`The message now is: ${await contract.greet()}`);
   }
   
2. Run the interaction script with yarn interact.


What we learned
What zkSync Does: It's a tool that makes Ethereum faster and cheaper by processing transactions differently.

Improvements to Ethereum: zkSync speeds up transactions, reduces costs, and maintains Ethereum's security.

We've also had a better grasp of what zkSync is and how to build, deploy and interact with a deployed contract 



What's next 


In the Next wave I'll be talking about a more advanced level in using zkSync to defeat the plagues that Afflicts Ethereum Developers
Chainstack
zkSync Faucet - Get Free zkSync Testnet ETH

Get free zkSync testnet tokens from Chainstack's faucet. Sign up and get free zkSync testnet ETH tokens.

