# Day 74

Tags: Blockchain
Date: September 26, 2023
Status: Done

Task of the day

- Mining and Incentives Models
- Decentralization vs Trust
- Blockchain Forking
- Cryptocurrencies
- Cryptowallets

---

### Mining and incentive models

Mining is the process of adding transaction details to the Blockchain, like sender address, hash value, etc. The Blockchain contains all the history of the transactions that have taken place in the past for record purposes and it is stored in such a manner that, it can’t be manipulated.
An Incentive is basically a reward given to a Blockchain Miner for speeding up the transactions and making correct decisions while processing the complete transaction securely.

### Consensus mechanism

The term 'consensus mechanism' is often used colloquially to refer to 'proof-of-stake', 'proof-of-work' or 'proof-of-authority' protocols. However, these are just components in consensus mechanisms that protect against Sybil attacks. Consensus mechanisms are the complete stack of ideas, protocols and incentives that enable a distributed set of nodes to agree on the state of a blockchain.****

**What is conensus?**

By consensus, we mean that a general agreement has been reached. Consider a group of people going to the cinema. If there is no disagreement on a proposed choice of film, then a consensus is achieved. If there is disagreement, the group must have the means to decide which film to see. In extreme cases, the group will eventually split.

In regard to the Ethereum blockchain, the process is formalized, and reaching consensus means that at least 66% of the nodes on the network agree on the global state of the network.

**What is a consensus mechanism?**

The term consensus mechanism refers to the entire stack of protocols, incentives and ideas that allow a network of nodes to agree on the state of a blockchain.

Ethereum uses a proof-of-stake-based consensus mechanism that derives its crypto-economic security from a set of rewards and penalties applied to capital locked by stakers. This incentive structure encourages individual stakers to operate honest validators, punishes those who don't, and creates an extremely high cost to attack the network.

Then, there is a protocol that governs how honest validators are selected to propose or validate blocks, process transactions and vote for their view of the head of the chain. In the rare situations where multiple blocks are in the same position near the head of the chain, there is a fork-choice mechanism that selects blocks that make up the 'heaviest' chain, measured by the number of validators that voted for the blocks weighted by their staked ether balance.

Some concepts are important to consensus that are not explicitly defined in code, such as the additional security offered by potential out-of-band social coordination as a last line of defense against attacks on the network.

**Types of consensus mechanisms**

**Proof-of-work based**

Like Bitcoin, Ethereum once used a **proof-of-work (PoW)** based consensus protocol.****

**Security**

The network is kept secure by the fact that you'd need 51% of the network's computing power to defraud the chain. This would require such huge investments in equipment and energy; you're likely to spend more than you'd gain.

**Proof-of-stake based**

Ethereum now uses a **proof-of-stake (PoS)** based consensus protocol.****

**Block creation**

Validators create blocks. One validator is randomly selected in each slot to be the block proposer. Their consensus client requests a bundle of transactions as an 'execution payload' from their paired execution client. They wrap this in consensus data to form a block, which they send to other nodes on the Ethereum network. This block production is rewarded in ETH. In rare cases when multiple possible blocks exist for a single slot, or nodes hear about blocks at different times, the fork choice algorithm picks the block that forms the chain with the greatest weight of attestations (where weight is the number of validators attesting scaled by their ETH balance).****

**Security**

A proof-of-stake system is secure crypto-economically because an attacker attempting to take control of the chain must destroy a massive amount of ETH. A system of rewards incentivizes individual stakers to behave honestly, and penalties disincentivize stakers from acting maliciously.

**Sybil resistance & chain selection**

Proof-of-work and proof-of-stake alone are not consensus protocols, but they are often referred to as such for simplicity. They are actually Sybil resistance mechanisms and block author selectors; they are a way to decide who is the author of the latest block. Another important component is the chain selection (aka fork choice) algorithm that enables nodes to pick one single correct block at the head of the chain in scenarios where multiple blocks exist in the same position.

- **Sybil resistance** measures how a protocol fares against a [Sybil attack(opens in a new tab)](https://wikipedia.org/wiki/Sybil_attack). Sybil attacks are when one user or group pretends to be many users. Resistance to this type of attack is essential for a decentralized blockchain and enables miners and validators to be rewarded equally based on resources put in. Proof-of-work and proof-of-stake protect against this by making users expend a lot of energy or put up a lot of collateral. These protections are an economic deterrent to Sybil attacks.
- A **chain selection rule** is used to decide which chain is the "correct" chain. Bitcoin uses the "longest chain" rule, which means that whichever blockchain is the longest will be the one the rest of the nodes accept as valid and work with. For proof-of-work chains, the longest chain is determined by the chain's total cumulative proof-of-work difficulty. Ethereum used to use the longest chain rule too; however, now that Ethereum runs on proof-of-stake it adopted an updated fork-choice algorithm that measures the 'weight' of the chain. The weight is the accumulated sum of validator votes, weighted by validator staked-ether balances.

Ethereum uses a consensus mechanism known as [Gasper](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/gasper/) that combines [Casper FFG proof-of-stake(opens in a new tab)](https://arxiv.org/abs/1710.09437) with the [GHOST fork-choice rule(opens in a new tab)](https://arxiv.org/abs/2003.03052).

---

### Decentralized vs trust

Blockchains, cryptocurrency, smart contracts, and oracles have emerged as new technologies for coordinating social and economic activities in a more secure, transparent, and accessible manner. Most importantly, these technologies are revealing the power of cryptographic guarantees—what we often call cryptographic truth—in restoring users’ trust in everyday interactions.

[What Crypto Is Really About | Chainlink Blog](https://blog.chain.link/what-crypto-is-really-about/)

---

### [Blockchain forking](https://www.investopedia.com/terms/h/hard-fork.asp)

### **What is a hard fork?**

A hard fork (or hardfork), as it relates to [blockchain](https://www.investopedia.com/terms/b/blockchain.asp) technology, is a radical change to a network's protocol that makes previously invalid blocks and transactions valid, or vice-versa. A hard fork requires all nodes or users to upgrade to the latest version of the protocol software.

Forks may be initiated by developers or members of a crypto community who grow dissatisfied with functionalities offered by existing blockchain implementations. They may also emerge as a way to crowdsource funding for new technology projects or [cryptocurrency](https://www.investopedia.com/terms/c/cryptocurrency.asp) offerings.

### KEY TAKEAWAYS

- A hard fork refers to a radical change to the protocol of a blockchain network that effectively results in two branches, one that follows the previous protocol and one that follows the new version.
- In a hard fork, holders of tokens in the original blockchain will be granted tokens in the new fork as well, but miners must choose which blockchain to continue verifying.
- A hard fork can occur in any blockchain, and not only Bitcoin (where hard forks have created Bitcoin Cash and Bitcoin SV, among several others, for example).

### **Hard Forks vs. Soft Forks**

Hard forks and soft forks are essentially the same in the sense that when a cryptocurrency platform's existing code is changed, an old version remains on the network while the new version is created.

With a soft fork, only one blockchain will remain valid as users adopt the update. Whereas with a hard fork, both the old and new blockchains exist side by side, which means that the software must be updated to work by the new rules. Both forks create a split, but a hard fork creates two blockchains and a soft fork is meant to result in one.

Considering the differences in security between hard and soft forks, almost all users and developers call for a hard fork, even when a soft fork seems like it could do the job. Overhauling the blocks in a blockchain requires a tremendous amount of computing power, but the privacy gained from a hard fork makes more sense than using a soft fork

---

### Cryptocurrencies

A cryptocurrency, crypto-currency, or crypto is a digital currency designed to work as a medium of exchange through a blockchain, which is not reliant on any central authority, such as a government or bank, to uphold or maintain it.

[Cryptocurrency, Explained: A Guide for Beginners - NerdWallet](https://www.nerdwallet.com/article/investing/cryptocurrency)

---

### Cryptowallets

A cryptocurrency wallet is an application that functions as a wallet for your cryptocurrency.

### KEY TAKEAWAYS:

- A cryptocurrency wallet is a device or program that stores your cryptocurrency keys and allows you to access your coins.
- Wallets contain a public key (the wallet address) and your private keys needed to sign cryptocurrency transactions. Anyone who knows the private key can control the coins associated with that address.
- There are several different types of wallets, each with its own features and levels of security.
- Many cryptocurrency wallets can be used to store key for different cryptocurrencies.

[Cryptocurrency Wallet: What It Is, How It Works, Types, Security](https://www.investopedia.com/terms/b/bitcoin-wallet.asp)

---