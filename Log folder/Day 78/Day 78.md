# Day 78

Tags: Blockchain, Solidity
Date: September 30, 2023
Status: Done

Tasks of the day

- Smart Contract Framework
    - Hardhat
    - Brownie
    - Truffle
    - Foundry
- Management Platforms
    - Open Zeppelin

Creating an NFT with [Solmate](https://book.getfoundry.sh/tutorials/solmate-nft)

---

### Smart contracts frameworks

Building a full-fledged dapp requires different pieces of technology. Software frameworks include many of the needed features or provide easy plugin systems to pick the tools you desire.

**Introduction to frameworks**

Building a full-fledged dapp requires different pieces of technology. Software frameworks include many of the needed features or provide easy plugin systems to pick the tools you desire.

Frameworks come with a lot of out-of-the-box functionality, like:

- Features to spin up a local blockchain instance.
- Utilities to compile and test your smart contracts.
- Client development add-ons to build your user-facing application within the same project/repository.
- Configuration to connect to Ethereum networks and deploy contracts, whether to a locally running instance, or one of Ethereum's public networks.
- Decentralized app distribution - integrations with storage options like IPFS.

### Available frameworks

**Truffle -** ***A development environment, testing framework, build pipeline, and other tools.***

- [trufflesuite.com(opens in a new tab)](https://www.trufflesuite.com/)
- [GitHub(opens in a new tab)](https://github.com/trufflesuite/truffle)

**Hardhat -** ***Ethereum development environment for professionals.***

- [hardhat.org(opens in a new tab)](https://hardhat.org/)
- [GitHub(opens in a new tab)](https://github.com/nomiclabs/hardhat)

**Ape -** ***The smart contract development tool for Pythonistas, Data Scientists, and Security Professionals.***

- [Documentation(opens in a new tab)](https://docs.apeworx.io/ape/stable/)
- [GitHub(opens in a new tab)](https://github.com/ApeWorX/ape)

**Brownie -** ***Python-based development environment and testing framework.***

- [Documentation(opens in a new tab)](https://eth-brownie.readthedocs.io/en/latest/)
- [GitHub(opens in a new tab)](https://github.com/eth-brownie/brownie)

**Web3j -** ***A platform for developing blockchain applications on the JVM.***

- [Homepage(opens in a new tab)](https://www.web3labs.com/web3j-sdk)
- [Documentation(opens in a new tab)](https://docs.web3j.io/)
- [GitHub(opens in a new tab)](https://github.com/web3j/web3j)

**OpenZeppelin SDK -** ***The Ultimate Smart Contract Toolkit: A suite of tools to help you develop, compile, upgrade, deploy and interact with smart contracts.***

- [OpenZeppelin SDK(opens in a new tab)](https://openzeppelin.com/sdk/)
- [GitHub(opens in a new tab)](https://github.com/OpenZeppelin/openzeppelin-sdk)
- [Community Forum(opens in a new tab)](https://forum.openzeppelin.com/c/support/17)

**Create Eth App -** ***Create Ethereum-powered apps with one command. Comes with a wide offering of UI frameworks and DeFi templates to choose from.***

- [GitHub(opens in a new tab)](https://github.com/paulrberg/create-eth-app)
- [Templates(opens in a new tab)](https://github.com/PaulRBerg/create-eth-app/tree/develop/templates)

**Scaffold-Eth -** ***Ethers.js + Hardhat + React components and hooks for web3: everything you need to get started building decentralized applications powered by smart contracts.***

- [GitHub(opens in a new tab)](https://github.com/austintgriffith/scaffold-eth)

**Tenderly -** ***Web3 development platform that enables blockchain developers to build, test, debug, monitor, and operate smart contracts and improve dapp UX.***

- [Website(opens in a new tab)](https://tenderly.co/)
- [Documentation(opens in a new tab)](https://docs.tenderly.co/ethereum-development-practices)

**The Graph -** ***The Graph for querying blockchain data efficiently.***

- [Website(opens in a new tab)](https://thegraph.com/)
- [Tutorial](https://ethereum.org/en/developers/tutorials/the-graph-fixing-web3-data-querying/)

**Alchemy -** ***Ethereum Development Platform.***

- [alchemy.com(opens in a new tab)](https://www.alchemy.com/)
- [GitHub(opens in a new tab)](https://github.com/alchemyplatform)
- [Discord(opens in a new tab)](https://discord.com/invite/A39JVCM)

**Foundry -** ***A blazing fast, portable and modular toolkit for Ethereum application development written in Rust.***

- [Documentation(opens in a new tab)](https://book.getfoundry.sh/)
- [GitHub(opens in a new tab)](https://github.com/gakonst/foundry/)
- [Tools for Foundry(opens in a new tab)](https://github.com/crisgarner/awesome-foundry)

**NodeReal -** ***Ethereum Development Platform.***

- [Nodereal.io(opens in a new tab)](https://nodereal.io/)
- [GitHub(opens in a new tab)](https://github.com/node-real)
- [Discord(opens in a new tab)](https://discord.gg/V5k5gsuE)

**thirdweb SDK -** ***Build web3 applications that can interact with your smart contracts using our powerful SDKs and CLI.***

- [Documentation(opens in a new tab)](https://portal.thirdweb.com/sdk/)
- [GitHub(opens in a new tab)](https://github.com/thirdweb-dev/)

**Chainstack -** ***Web3 (Ethereum and otherwise) Development Platform.***

- [chainstack.com(opens in a new tab)](https://www.chainstack.com/)
- [GitHub(opens in a new tab)](https://github.com/chainstack)
- [Discord(opens in a new tab)](https://discord.gg/BSb5zfp9AT)

Visit the following resources to learn more:

- **[dApp Development Frameworks](https://ethereum.org/en/developers/docs/frameworks/)**
- **[A Definitive List of Ethereum Developer Tools - Frameworks](https://media.consensys.net/an-definitive-list-of-ethereum-developer-tools-2159ce865974#frameworks)**
- **[Top 10 Smart Contract Developer Tools You Need for 2022](https://medium.com/better-programming/top-10-smart-contract-developer-tools-you-need-for-2022-b763f5df689a)**

---

### Hardhat

Hardhat is a development environment for Ethereum software. It consists of different components for editing, compiling, debugging and deploying your smart contracts and dApps, all of which work together to create a complete development environment.

Hardhat Runner is the main component you interact with when using Hardhat. It's a flexible and extensible task runner that helps you manage and automate the recurring tasks inherent to developing smart contracts and dApps.

Hardhat Runner is designed around the concepts of **tasks** and **plugins**. Every time you're running Hardhat from the command-line, you're running a task. For example, `npx hardhat compile` runs the built-in `compile` task. Tasks can call other tasks, allowing complex workflows to be defined. Users and plugins can override existing tasks, making those workflows customizable and extendable.

Visit the following resources to learn more:

- **[Hardhat Overview](https://hardhat.org/hardhat-runner/docs/getting-started#overview)**
- **[Build and Deploy Smart Contracts using Hardhat](https://youtu.be/GBc3lBrXEBo)**

---

### Brownie

Brownie is a Python-based development and testing framework for smart contracts targeting the Ethereum Virtual Machine.

**Features**

- Full support for [Solidity](https://github.com/ethereum/solidity) and [Vyper](https://github.com/vyperlang/vyper)
- Contract testing via [pytest](https://github.com/pytest-dev/pytest), including trace-based coverage evaluation
- Property-based and stateful testing via [hypothesis](https://github.com/HypothesisWorks/hypothesis/tree/master/hypothesis-python)
- Powerful debugging tools, including python-style tracebacks and custom error strings
- Built-in console for quick project interaction
- Support for [ethPM](https://www.ethpm.com/) packages

Visit the following resources to learn more:

- **[Brownie Overview](https://eth-brownie.readthedocs.io/)**
- **[Python and Blockchain: Deploy Smart Contracts using Brownie](https://youtu.be/QfFO22lwSw4)**

---

### Truffle

A development environment, testing framework, and asset pipeline for blockchains using the Ethereum Virtual Machine (EVM), aiming to make life as a developer easier.

A world class development environment, testing framework and asset pipeline for blockchains using the Ethereum Virtual Machine (EVM), aiming to make life as a developer easier. With Truffle, you get:

- Built-in smart contract compilation, linking, deployment and binary management.
- [Advanced debugging](https://trufflesuite.com/docs/truffle/how-to/debug-test/use-the-truffle-debugger) with breakpoints, variable analysis, and step functionality.
- Use [console.log](https://trufflesuite.com/docs/truffle/reference/configuration/#soliditylog) in your smart contracts
- Deployments and transactions through MetaMask with [Truffle Dashboard](https://trufflesuite.com/docs/truffle/how-to/use-the-truffle-dashboard) to protect your mnemonic.
- External script runner that executes scripts within a Truffle environment.
- Interactive console for direct contract communication.
- Automated contract testing for rapid development.
- Scriptable, extensible deployment & migrations framework.
- Network management for deploying to any number of public & private networks.
- Package management with NPM, using the [ERC190](https://github.com/ethereum/EIPs/issues/190) standard.
- Configurable build pipeline with support for tight integration.

Visit the following resources to learn more:

- **[Truffle Overview](https://trufflesuite.com/docs/truffle/)**
- **[Truffle Tutorial for Beginners | Compile, Test & Deploy Smart contracts to any EVM Blockchain](https://youtu.be/62f757RVEvU)**

---

### [Foundry](https://www.paradigm.xyz/2022/03/foundry-02)

**What is Foundry?**

Foundry is **a portable, fast, and modular toolkit for Ethereum application development, written in Rust.** Our goal with Foundry is to create the best developer experience for building secure smart contracts on EVM chains. Most importantly: **Foundry is built by Solidity developers for Solidity developers.**

We [announced Foundry v0.1.0 in December 2021](https://www.paradigm.xyz/2021/12/introducing-the-foundry-ethereum-development-toolbox) as a first step towards improving the Ethereum development experience. This initial version centered on four key features:

1. Letting developers write tests in Solidity to minimize context switching;
2. Making tests and the compilation pipeline REALLY fast to keep the developer's feedback loop tight;
3. Using intuitive patterns for expanding test coverage, debugging, and testing against a live network's state; and,
4. Being easy to install and distribute across platforms.

The results since December have convinced us that Foundry solves some major development pain points. On [Solmate](https://github.com/Rari-Capital/solmate) for instance, it [took down](https://twitter.com/onbjerg/status/1506722848106328071?s=20&t=FCDvJyHDos97X8nu_lvOOA) testing time **from 393s to 2.8s, a 140x improvement**. Developers from top protocols like [Optimism](https://github.com/ethereum-optimism/optimistic-specs/pull/265) and [MakerDAO](https://github.com/makerdao/spells-mainnet#test-forge-without-optimizations) are using Foundry as a standalone framework, or will introduce it incrementally in their codebases to improve their build and test process.

Now we're excited to announce **Foundry v0.2.0**, a major step forward for the toolkit.

[Foundry Book](https://book.getfoundry.sh/)

---

### Management platforms

Managing smart contracts in a production environment (mainnet) can prove difficult as users must keep track of different versions, blockchains, deployments, etc. Using a tool for this process eliminates a lot of the risk that comes with manual tracking.

**OpenZeppelin** 

OpenZeppelin Contracts helps you minimize risk by using battle-tested libraries of smart contracts for Ethereum and other blockchains. It includes the most used implementations of ERC standards.

Visit the following resources to learn more:

- **[OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts/)**