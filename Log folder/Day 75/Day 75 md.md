# Day 75

Tags: Blockchain
Date: September 27, 2023
Status: Done

**Tasks of the day**

- Blockchains
    - Solana
    - TON
    - EVM-Based
    - L2 Blockchains
        - Arbitrum
        - Moonbeam
- Oracles
    - Hybrid Smart Contracts
    - Chainlink
    - Oracle Networks

**[Connect APIs to your Smart Contracts using Chainlink](https://docs.alchemy.com/docs/connect-apis-to-your-smart-contracts-using-chainlink)**

---

### Blockchains

Blockchain systems vary considerably in their design, particularly with regard to the consensus mechanisms used to perform the essential task of verifying network data.

**Types of Blockchains: PoW, PoS, and Private**

*Blockchain systems vary considerably in their design, particularly with regard to the consensus mechanisms used to perform the essential task of verifying network data. The most common consensus mechanisms are Proof of Work (PoW), Proof of Stake (PoS), and methods used by private and consortium blockchains. Each design has different implications for the underlying blockchain’s security, accessibility, and sustainability.*

### **Contents**

- [Blockchain Types](https://www.gemini.com/cryptopedia/blockchain-types-pow-pos-private#section-blockchain-types)
- [Proof-of-Work Blockchains](https://www.gemini.com/cryptopedia/blockchain-types-pow-pos-private#section-proof-of-work-blockchains)
- [Proof-of-Stake Blockchains](https://www.gemini.com/cryptopedia/blockchain-types-pow-pos-private#section-proof-of-stake-blockchains)
- [Private and Consortium Blockchains](https://www.gemini.com/cryptopedia/blockchain-types-pow-pos-private#section-private-and-consortium-blockchains)

**Proof-of-Work Blockchains**

The Proof-of-Work (PoW) consensus mechanism is widely used in blockchain, with miners using computational power to solve mathematical puzzles and validate transactions. While PoW blockchains offer security and decentralization, they have limitations in speed and scalability. The high costs and energy consumption of mining rigs create barriers to participation and contribute to environmental damage. Efforts are being made to address these issues and alternative solutions are being explored.

**Proof-of-Stake Blockchains**

Proof of Stake (PoS) is a popular consensus mechanism that addresses the limitations of Proof-of-Work (PoW) blockchains. PoS blockchains like Polkadot, Avalanche, and Cardano use validators instead of miners to validate transactions, reducing energy consumption and improving scalability. Validators stake native tokens as collateral and are randomly selected to confirm data. PoS blockchains ensure security by slashing validators who act maliciously. While the barrier to entry is lower for validators, a sufficient amount of crypto is still required. PoS blockchains are more sustainable and there is a focus on employing them in future projects. Delegated Proof of Stake (DPoS) is an evolution of PoS where users elect delegates to validate blocks, offering a more decentralized and egalitarian process.

**Private and Consortium Blockchains**

Public blockchains like Bitcoin and Ethereum are decentralized and censorship-resistant, while private and consortium blockchains offer more control and privacy for enterprises. Consortium blockchains can have faster transaction processing times but limited usage outside of the consortium. Different consensus mechanisms have implications for accessibility and security. While PoW has been the standard, PoS, DPoS, and DLT are gaining traction in the blockchain world.

---

### Solana

Solana is a public blockchain platform with smart contract functionality. Its native cryptocurrency is SOL.

**What is Solana**

Solana is an open-source blockchain project created in 2017 that aims to achieve high scalability and low costs. It implements a hybrid consensus model combining proof-of-history (PoH) and proof-of-stake (PoS), allowing for a theoretical processing capacity of over 710,000 transactions per second (TPS). Solana's architecture supports smart contracts, decentralized finance (DeFi) platforms, and non-fungible token (NFT) marketplaces. The main network was launched in 2020 after multiple testnet phases.

**What makes Solona unique?**

Solana aims to solve the blockchain trilemma of decentralization, security, and scalability through its unique hybrid consensus mechanism. By compromising on decentralization to maximize speed, Solana combines PoS and PoH to increase throughput and scalability. The sequencing of messages between nodes and the use of a chain of transactions contribute to Solana's greater scalability and usability..

![Screen Shot 2023-09-27 at 10.46.51 AM.png](Day%2075%20ad5280b65ca24db59f5c754f42f804ff/Screen_Shot_2023-09-27_at_10.46.51_AM.png)

**TON**

TON is a fully decentralized layer-1 blockchain designed by Telegram to onboard billions of users. It boasts ultra-fast transactions, tiny fees, easy-to-use apps, and is environmentally friendly.

[https://www.youtube.com/watch?v=XgzHmV_nnpY&embeds_referring_euri=https://docs.ton.org/&embeds_referring_origin=https://docs.ton.org&source_ve_path=NzY3NTg&feature=emb_yt_watermark](https://www.youtube.com/watch?v=XgzHmV_nnpY&embeds_referring_euri=https://docs.ton.org/&embeds_referring_origin=https://docs.ton.org&source_ve_path=NzY3NTg&feature=emb_yt_watermark)

---

### L2 blockchains

Layer-2 refers to a network or technology that operates on top of an underlying blockchain protocol to improve its scalability and efficiency.
This category of scaling solutions entails shifting a portion of Ethereum’s transactional burden to an adjacent system architecture, which then handles the brunt of the network’s processing and only subsequently reports back to Ethereum to finalize its results.

****Layer-1 and Layer-2 Blockchain Scaling Solutions****

*To compete with legacy systems of payment processing, blockchain networks must become highly scalable — capable of accommodating an exponentially growing number of users, transactions, and data. Only by adequately incorporating scalability into their structure do blockchain networks stand to supersede other legacy systems. Layer-1 solutions add utility to a native blockchain to optimize its performance. Layer-2 solutions are third-party protocols that integrate with an underlying Layer-1 blockchain to increase transactional throughput.*

### **Contents**

- [What Is Blockchain Scalability?](https://www.gemini.com/cryptopedia/blockchain-layer-2-network-layer-1-network#section-what-is-blockchain-scalability)
- [Layer-1 Scaling Solutions](https://www.gemini.com/cryptopedia/blockchain-layer-2-network-layer-1-network#section-layer-1-scaling-solutions)
- [Layer-2 Scaling Solutions](https://www.gemini.com/cryptopedia/blockchain-layer-2-network-layer-1-network#section-layer-2-scaling-solutions)
- [Boosting Blockchain Network Scalability](https://www.gemini.com/cryptopedia/blockchain-layer-2-network-layer-1-network#section-boosting-blockchain-network-scalability)

---

### ****EVM based****

The Ethereum Virtual Machine (EVM) is a dedicated software virtual stack that executes smart contract bytecode and is integrated into each Ethereum node. Simply said, EVM is a software framework that allows developers to construct Ethereum-based decentralized applications (DApps). All Ethereum accounts and smart contracts are stored on this virtual computer.

Many blockchains have forked the Ethereum blockchain and added functionality on top, these blockchains are referred to as EVM-based blockchains.

Visit the following resources to learn more:

- **[What is Ethereum Virtual Machine?](https://moralis.io/evm-explained-what-is-ethereum-virtual-machine/)**
- **[Understanding the Ethereum Virtual Machine (EVM): Concepts and Architecture](https://www.youtube.com/watch?v=kCswGz9naZg)**

---

### ****Arbitrum****

Arbitrum aims to reduce transaction fees and congestion by moving as much computation and data storage off of Ethereum’s main blockchain (layer 1) as it can. Storing data off of Ethereum’s blockchain is known as Layer 2 scaling solutions.

Visit the following resources to learn more:

- **[Arbitrum whitepaper](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-kalodner.pdf)**
- **[Inside Arbitrum](https://developer.offchainlabs.com/docs/Inside_Arbitrum)**

---

### ****Moonbeam Moonriver****

Moonbeam is a Polkadot network parachain that promises cross-chain interoperability between the Ethereum and Polkadot . More specifically, Moonbeam is a smart contract platform that enables developers to move dApps between the two networks without having to rewrite code or redeploy infrastructure.

Moonriver is an incentivized testnet. It enables developers to create, test, and adjust their protocols prior to launching on Moonbeam. Moonbeam is the mainnet of the ecosystem.

Visit the following resources to learn more:

- **[About Moonbeam](https://docs.moonbeam.network/learn/platform/networks/moonbeam/)**
- **[Moonbeam Vision](https://docs.moonbeam.network/learn/platform/vision/)**

---

### Oracles

A blockchain oracle is a third-party service that connects smart contracts with the outside world, primarily to feed information in from the world, but also the reverse. Information from the world encapsulates multiple sources so that decentralized knowledge is obtained.

Visit the following resources to learn more:
• **[Blockchain Oracle](https://en.wikipedia.org/wiki/Blockchain_oracle)**
• **[What Is a Blockchain Oracle?](https://chain.link/education/blockchain-oracles)**

Oracles provide a way for the decentralized Web3 ecosystem to access existing [data sources](https://blog.chain.link/understanding-how-data-and-apis-power-next-generation-economies/), legacy systems, and advanced computations. Decentralized oracle networks (DONs) enable the creation of [hybrid smart contracts](https://blog.chain.link/hybrid-smart-contracts-explained/), where on-chain code and off-chain infrastructure are combined to support advanced decentralized applications (dApps) that react to real-world events and interoperate with traditional systems.

![Screen Shot 2023-09-27 at 11.34.06 AM.png](Day%2075%20ad5280b65ca24db59f5c754f42f804ff/Screen_Shot_2023-09-27_at_11.34.06_AM.png)

### **Types of blockchain oracles**

Given the extensive range of off-chain resources, blockchain oracles come in many shapes and sizes. Not only do hybrid smart contracts need various types of external data and computation, but they require various mechanisms for delivery and different levels of security. Generally, each type of oracle involves some combination of fetching, validating, computing upon, and delivering data to a destination.

### **Input Oracles**

The most widely recognized type of oracle today is known as an “input oracle,” which fetches data from the real-world (off-chain) and delivers it onto a blockchain network for smart contract consumption. These types of oracles are used to power Chainlink Price Feeds, providing DeFi smart contracts with on-chain access to financial market data.

### **Output Oracles**

The opposite of input oracles are “output oracles,” which allow smart contracts to send commands to off-chain systems that trigger them to execute certain actions. This can include informing a banking network to make a payment, telling a storage provider to store the supplied data, or pinging an IoT system to unlock a car door once the on-chain rental payment is made.

### **Cross-Chain Oracles**

Another type of oracle are cross-chain oracles that can read and write information between different blockchains. Cross-chain oracles enable interoperability for moving both data and assets between blockchains, such as using data on one blockchain to trigger an action on another or bridging assets cross-chain so they can be used outside the native blockchain they were issued on.

### **Compute-Enabled Oracles**

A new type of oracle becoming more widely used by smart contract applications are “compute-enabled oracles,” which use secure off-chain computation to provide decentralized services that are impractical to do on-chain due to technical, legal, or financial constraints. This can include using [Chainlink Automation](https://chain.link/automation) to trigger the running of smart contracts when predefined events take place, computing [zero-knowledge proofs](https://blog.chain.link/what-is-a-zero-knowledge-proof-zkp/) to generate data privacy, or running a [verifiable randomness function](https://blog.chain.link/chainlink-vrf-on-chain-verifiable-randomness/) to provide a tamper-proof and provably fair source of randomness to smart contracts.

---

### Hybrid Smart Contracts

A hybrid smart contract combines on-chain infrastructure with off-chain data and computation provided by [decentralized oracle networks](https://chain.link/education/blockchain-oracles) to create a feature-rich decentralized application. By being able to seamlessly combine on-chain and off-chain components, hybrid smart contracts can unlock [smart contract](https://chain.link/education/smart-contracts) use cases and functionality that wouldn’t be possible by using just one of the components.

Hybrid smart contracts have the tamper-proof and immutable properties of blockchains yet leverage secure off-chain oracle services to attain new capabilities, such as scalability, confidentiality, order fairness, and connectivity to any real-world data source or system.

Visit the following resources to learn more:

- **[Hybrid Smart Contracts Explained](https://blog.chain.link/hybrid-smart-contracts-explained/)**
- **[A complete guide to understand hybrid smart contracts](https://www.leewayhertz.com/hybrid-smart-contracts/)**

---

### **Chainlink**

Chainlink is a decentralized network of oracles that enables smart contracts to securely interact with real-world data and services that exist outside of blockchain networks.

Visit the following resources to learn more:

- **[What Is Chainlink? A Beginner’s Guide](https://blog.chain.link/what-is-chainlink/)**
- **[What Is Chainlink in 5 Minutes](https://www.gemini.com/cryptopedia/what-is-chainlink-and-how-does-it-work)**

---

### Oracles Networks

By leveraging many different data sources, and implementing an oracle system that isn’t controlled by a single entity, decentralized oracle networks provide an increased level of security and fairness to smart contracts.

Visit the following resources to learn more:

- **[Decentralized Oracle Networks](https://medium.com/coinmonks/decentralized-oracle-networks-9fead28f5fe5)**
- **[A Beginner’s Guide To The Evolution Of Decentralized Oracle Networks](https://chainlinktoday.com/a-beginners-guide-to-the-evolution-of-decentralized-oracle-networks/)**
- **[Understanding Oracle Networks](https://coinmetro.com/blog/understanding-oracle-networks/)**