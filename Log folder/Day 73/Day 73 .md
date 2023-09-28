# Day 73

Tags: Blockchain
Date: September 25, 2023
Status: Done

Task of the day

- General Blockchain Knowledge
    - Storage
    - Cryptography
    - Consensus Protocols
    - Blockchain Interoperability

Exercise

**[How to Build "Buy Me a Coffee" DeFi dapp](https://docs.alchemy.com/docs/how-to-build-buy-me-a-coffee-defi-dapp)**

---

## Storage

Unlike a centralized server operated by a single company or organization, decentralized storage systems consist of a peer-to-peer network of user-operators who hold a portion of the overall data, creating a resilient file storage sharing system.

### **Decentralized storage**

Decentralized storage systems consist of a peer-to-peer network of user-operators who hold a portion of the overall data, creating a resilient file storage sharing system. These can be in a blockchain-based application or any peer-to-peer-based network.

When looking at decentralized storage (dStorage) options, there are a few things a user must keep in mind.

**Persistence mechanism / incentive structure**

1. **Blockchain based:** For a piece of data to persist forever, we need to use a persistence mechanism. For example, on Ethereum, the persistence mechanism is that the whole chain needs to be accounted for when running a node. New pieces of data get tacked onto the end of the chain, and it continues to grow - requiring every node to replicate all the embedded data. This is known as **blockchain-based** persistence.
    1. The blockchain must also have some type of incentive structure. For blockchain-based persistence, there is a payment made to the validator. When the data is added to the chain, the validators are paid to add the data on.
        
        Platforms with blockchain-based persistence:
        
        - Ethereum
        - [Arweave(opens in a new tab)](https://www.arweave.org/)

1. **Contract-based** persistence has the intuition that data cannot be replicated by every node and stored forever, and instead must be upkept with contract agreements. These are agreements made with multiple nodes that have promised to hold a piece of data for a period of time. They must be refunded or renewed whenever they run out to keep the data persisted.
    
    In most cases, instead of storing all data on-chain, the hash of where the data is located on a chain gets stored. This way, the entire chain doesn't need to scale to keep all of the data
    
    - Platforms with contract-based persistence:
        - [Filecoin(opens in a new tab)](https://docs.filecoin.io/about-filecoin/what-is-filecoin/)
        - [Skynet(opens in a new tab)](https://siasky.net/)
        - [Storj(opens in a new tab)](https://storj.io/)
        - [0Chain(opens in a new tab)](https://0chain.net/)
        - [Crust Network(opens in a new tab)](https://crust.network/)
        - [Swarm(opens in a new tab)](https://www.ethswarm.org/)
        - [4EVERLAND(opens in a new tab)](https://www.4everland.org/)

**Additional considerations**

IPFS is a distributed system for storing and accessing files, websites, applications, and data. It doesn't have a built-in incentive scheme, but can instead be used with any of the contract-based incentive solutions above for longer-term persistence. Another way to persist data on IPFS is to work with a pinning service, which will "pin" your data for you. You can even run your own IPFS node and contribute to the network to persist your and/or other's data for free!

- [IPFS(opens in a new tab)](https://docs.ipfs.io/concepts/what-is-ipfs/)
- [Pinata(opens in a new tab)](https://www.pinata.cloud/) *(IPFS pinning service)*
- [web3.storage(opens in a new tab)](https://web3.storage/) *(IPFS/Filecoin pinning service)*
- [Infura(opens in a new tab)](https://infura.io/product/ipfs) *(IPFS pinning service)*
- [IPFS Scan(opens in a new tab)](https://ipfs-scan.io/) *(IPFS pinning explorer)*
- [4EVERLAND(opens in a new tab)](https://www.4everland.org/)*（IPFS pinning service）*
- [Filebase(opens in a new tab)](https://filebase.com/) *(IPFS Pinning Service)*

SWARM is a decentralized data storage and distribution technology with a storage incentive system and a storage rent price oracle.****

### Data retention enforcement

**Challenge mechanism**

One of the most popular ways to make sure data is retained, is to use some type of cryptographic challenge that is issued to the nodes to make sure they still have the data. A simple one is looking at Arweave's proof-of-access. They issue a challenge to the nodes to see if they have the data at both the most recent block and a random block in the past. If the node can't come up with the answer, they are penalized.

Types of dStorage with a challenge mechanism:

- 0Chain
- Skynet
- Arweave
- Filecoin
- Crust Network
- 4EVERLAND

### Decentrality

There aren't great tools to measure the level of decentralization of platforms, but in general, you'll want to use tools that don't have some form of KYC to provide evidence they are not centralized.

Decentralized tools without KYC:

- 0Chain (implementing a non-KYC edition)
- Skynet
- Arweave
- Filecoin
- IPFS
- Ethereum
- Crust Network
- 4EVERLAND

### Consensus

Most of these tools have their own version of a [consensus mechanism](https://ethereum.org/en/developers/docs/consensus-mechanisms/) but generally they are based on either **[proof-of-work (PoW)](https://ethereum.org/en/developers/docs/consensus-mechanisms/pow/)** or **[proof-of-stake (PoS)](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/)**.

Proof-of-work based:

- Skynet
- Arweave

Proof-of-stake based:

- Ethereum
- Filecoin
- 0Chain
- Crust Network

---

## **[How IPFS works](https://docs.ipfs.tech/concepts/how-ipfs-works/#subsystems-overview)**

 The three key responsibilities of the IPFS subsystems are:

- **Representing and addressing data:**
- **Routing data**
- **Transferring data**

While these are the key responsibilities, IPFS's functionality spans beyond these three.

Data in IPFS is addressed by its contents (content addressing), rather than a location, such as an IP address (location addressing).

---

## Cryptography

### **Definition**

Cryptography provides for secure communication in the presence of malicious third-parties—known as adversaries. Encryption uses an algorithm and a key to transform an input (i.e., plaintext) into an encrypted output (i.e., ciphertext). A given algorithm will always transform the same plaintext into the same ciphertext if the same key is used. Algorithms are considered secure if an attacker cannot determine any properties of the plaintext or key, given the ciphertext. An attacker should not be able to determine anything about a key given a large number of plaintext/ciphertext combinations which used the key.

### What is the difference between symmetric and asymmetric cryptography

With symmetric cryptography, the same key is used for both encryption and decryption. A sender and a recipient must already have a shared key that is known to both. Key distribution is a tricky problem and was the impetus for developing asymmetric cryptography.

With asymmetric crypto, two different keys are used for encryption and decryption. Every user in an asymmetric cryptosystem has both a public key and a private key. The private key is kept secret at all times, but the public key may be freely distributed.

Data encrypted with a public key may only be decrypted with the corresponding private key. So, sending a message to John requires encrypting that message with John’s public key. Only John can decrypt the message, as only John has his private key. Any data encrypted with a private key can only be decrypted with the corresponding public key. Similarly, Jane could digitally sign a message with her private key, and anyone with Jane’s public key could decrypt the signed message and verify that it was in fact Jane who sent it.

Symmetric is generally very fast and ideal for encrypting large amounts of data (e.g., an entire disk partition or database). Asymmetric is much slower and can only encrypt pieces of data that are smaller than the key size (typically 2048 bits or smaller). Thus, asymmetric crypto is generally used to encrypt symmetric encryption keys which are then used to encrypt much larger blocks of data. For digital signatures, asymmetric crypto is generally used to encrypt the hashes of messages rather than entire messages.

A cryptosystem provides for managing cryptographic keys including generation, exchange, storage, use, revocation, and replacement of the keys.

### What problems does cryptography solve?

A secure system should provide several assurances such as confidentiality, integrity, and availability of data as well as authenticity and non-repudiation. When used correctly, crypto helps to provide these assurances. Cryptography can ensure the confidentiality and integrity of both data in transit as well as data at rest. It can also authenticate senders and recipients to one another and protect against repudiation.

Software systems often have multiple endpoints, typically multiple clients, and one or more back-end servers. These client/server communications take place over networks that cannot be trusted. Communication occurs over open, public networks such as the Internet, or private networks which may be compromised by external attackers or malicious insiders.

It can protect communications that traverse untrusted networks. There are two main types of attacks that an adversary may attempt to carry out on a network. Passive attacks involve an attacker simply listening on a network segment and attempting to read sensitive information as it travels. Passive attacks may be online (in which an attacker reads traffic in real-time) or offline (in which an attacker simply captures traffic in real-time and views it later—perhaps after spending some time decrypting it). Active attacks involve an attacker impersonating a client or server, intercepting communications in transit, and viewing and/or modifying the contents before passing them on to their intended destination (or dropping them entirely).

The confidentiality and integrity protections offered by cryptographic protocols such as SSL/TLS can protect communications from malicious eavesdropping and tampering. Authenticity protections provide assurance that users are actually communicating with the systems as intended. For example, are you sending your online banking password to your bank or someone else?

It can also be used to protect data at rest. Data on a removable disk or in a database can be encrypted to prevent disclosure of sensitive data should the physical media be lost or stolen. In addition, it can also provide integrity protection of data at rest to detect malicious tampering.

### What are the principles

The most important principle to keep in mind is that you should never attempt to design your own cryptosystem. The world’s most brilliant cryptographers (including Phil Zimmerman and Ron Rivest) routinely create cryptosystems with serious security flaws in them. In order for a cryptosystem to be deemed “secure,” it must face intense scrutiny from the security community. Never rely on security through obscurity, or the fact that attackers may not have knowledge of your system. Remember that malicious insiders and determined attackers will attempt to attack your system.

The only things that should be “secret” when it comes to a secure cryptosystem are the keys themselves. Be sure to take appropriate steps to protect any keys that your systems use. Never store encryption keys in clear text along with the data that they protect. This is akin to locking your front door and placing the key under the doormat. It is the first place an attacker will look. Here are three common methods for protecting keys (from least secure to most secure):

1. Store keys in a filesystem and protect them with strong access control lists (ACLs). Remember to adhere to the principal of least privilege.
2. Encrypt your data encryption keys (DEKs) with a second key encrypting key (KEK). The KEK should be generated using password-based encryption (PBE). A password known to a minimal number of administrators can be used to generate a key using an algorithm such as bcrypt, scrypt, or PBKDF2 and used to bootstrap the cryptosystem. This removes the need to ever store the key unencrypted anywhere.
3. A hardware security module (HSM) is a tamper-resistant hardware appliance that can be used to store keys securely. Code can make API calls to an HSM to provide keys when needed or to perform decryption of data on the HSM itself.

Make sure that you only use algorithms, key strengths, and modes of operation that conform to industry best practices. Advanced encryption standard (AES) (with 128, 192, or 256-bit keys) is the standard for symmetric encryption. RSA and elliptical curve cryptography (ECC) with at least 2048-bit keys are the standard for asymmetric encryption. Be sure to avoid insecure modes of operation such as AES in Electronic Codebook (ECB) mode or RSA with no padding.

---

### Consensus protocols

Consensus for blockchain is a procedure in which the peers of a Blockchain network reach agreement about the present state of the data in the network. Through this, consensus algorithms establish reliability and trust in the Blockchain network.

The goal of a consensus mechanism in the world of crypto is to prevent bad actors from deliberately cheating. The classic example of cheating in the world of crypto is “[double-spending](https://en.wikipedia.org/wiki/Double-spending).”

**Type of consensus mechanisms**

The two most widespread consensus mechanism are:

- [Proof-of-Work](https://www.coindesk.com/learn/2020/12/16/what-is-proof-of-work/), which [Bitcoin](https://www.coindesk.com/learn/what-is-bitcoin/) and [Dogecoin](https://www.coindesk.com/learn/want-to-buy-dogecoin-read-this-first/), among others, use for their [BTC](https://www.coindesk.com/price/bitcoin/)and [DOGE](https://www.coindesk.com/price/dogecoin/) currencies
- [Proof-of-Stake](https://www.coindesk.com/learn/2020/12/30/what-is-proof-of-stake/), which [Cardano](https://www.coindesk.com/learn/how-to-stake-cardano-ada/), Solana and [Avalanche](https://www.coindesk.com/learn/what-is-avalanche-a-look-at-the-popular-ethereum-killer-blockchain/), for example, use for [ADA](https://www.coindesk.com/price/cardano/), [SOL](https://www.coindesk.com/price/solana/) and [AVAX](https://www.coindesk.com/price/avax/), respectively

**How consensus works**

In the case of Proof-of-Work blockchains such as Bitcoin, consensus requires a significant amount of energy, hardware and computing power to propose a new group of transactions – called a block – to the ledger.

The nodes that validate transactions and propose new blocks are called [miners](https://www.coindesk.com/learn/how-bitcoin-mining-works-2/). Miners compete to generate a random number to unlock the next block on the chain. The quickest miner to reach that number adds the next block and in exchange for the effort it receives a [block reward](https://www.coindesk.com/learn/what-is-a-block-reward/). The only way to win is to generate random numbers as quickly as possible (the "work" in the name) and get lucky. That is a contest of computing power, which in turn requires hardware and electricity.

When it comes to Proof-of-Stake blockchains, the nodes – often referred to as validators – that verify transactions and propose new blocks are required to lock up a certain amount of value in the form of the blockchain’s native token – that’s their stake in the system. The more value a validator deposits, the bigger chance they have to propose a new block and earn the block reward. If a validator commits an error, it has to pay a fee or can be excluded from the validation.

---

## Blockchain interoperability

The concept of “blockchain interoperability” refers to the ability of different blockchain networks to exchange and leverage data between one another and to move unique types of digital assets between the networks’ respective blockchains.

### **Benefits of blockchain interoperability**

While there already exist impressive and diverse blockchain ecosystems contained within individual networks like [Ethereum](https://www.gemini.com/cryptopedia/ethereum-smart-contracts-tokens-use-cases), [Polkadot](https://www.gemini.com/cryptopedia/polkadot-crypto-dot-coin), and [Solana](https://www.gemini.com/cryptopedia/solana-blockchain), the ability of such different networks to interact meaningfully with one another — referred to as interoperability — is expected to enable a wide range of blockchain-enabled products and services. More specifically:

- **Customizable Web3 services:** The ability of blockchain protocols and applications to mix and match different “lego pieces” is key to creating entirely new [Web3](https://www.gemini.com/cryptopedia/glossary#web-3-0-web-3) instruments and platforms that aren’t possible with legacy industries and business models of the [Web2](https://www.gemini.com/cryptopedia/glossary#web-2-0-web-2) era. Many experts argue that interoperable [smart contracts](https://www.gemini.com/cryptopedia/smart-contract-examples-smart-contract-use-cases) could supercharge industries like healthcare, law, or real estate, for instance by allowing important business information to be sent back and forth between private networks and public networks in a customizable and controllable manner. Blockchain interoperability may also eventually enable multi-token transactions and multi-token wallet systems, which would greatly streamline the crypto user experience.
- **A more decentralized ecosystem:** While pure decentralization within individual blockchain networks is a top priority for many blockchain projects, the ability to establish network interoperability across multiple blockchains presents an even more advanced embodiment of blockchain technology’s promise to decentralize systems and economies. Instead of having one blockchain like Ethereum processing all the transactions for thousands of [decentralized applications (dApps)](https://www.gemini.com/cryptopedia/dapps-ethereum-decentralized-application), there could one day be thousands of application-specific blockchains that communicate with one another through a decentralized main hub.
- **Enhanced cross-industry collaboration**: Blockchain technology has a wide range of industry-specific use cases, but ultimately the primary benefits come down to data transparency and verifiability, [smart contract](https://www.gemini.com/cryptopedia/crypto-smart-contracts-explained) execution, and decentralized consensus. Once blockchains used by different organizations and industries are able to interact with one another, independent markets and business applications that were previously considered entirely separate will be able to more easily transfer data and value. This means organizations and communities that wouldn’t typically interact with one another would be able to exchange information, leverage each other’s strengths, and cultivate innovation more effortlessly and effectively

### How is blockchain interoperability achieved?

Most existing [Layer-1 blockchains](https://www.gemini.com/cryptopedia/glossary#layer-1-blockchain) lack built-in features that support [cross-chain interoperability](https://www.gemini.com/cryptopedia/glossary#cross-chain-communication). However, there are a variety of tools today that are increasing the level of interoperability between blockchain networks:

**Sidechains**: A type of [Layer-2 platform](https://www.gemini.com/cryptopedia/blockchain-layer-2-network-layer-1-network), [sidechains](https://www.gemini.com/cryptopedia/glossary#sidechain-side-chain) are separate blockchain networks that are compatible with a single mainchain. Each sidechain has its own [consensus mechanism](https://www.gemini.com/cryptopedia/glossary#consensus-mechanism), security parameters, and tokens. These sidechains generally have their own specific use cases that are distributed accordingly in order to improve the overall ecosystem’s processing efficiency and self-sovereignty. Several major crypto projects such as Polkadot and [Cosmos](https://www.gemini.com/cryptopedia/cosmos-crypto-network-internet-of-blockchains) were designed from the ground up to be comprehensive cross-chain infrastructure solutions, with the ultimate goal being to establish an interoperable “network of networks.”

**Oracles**: Within the context of blockchain technology, [oracles](https://www.gemini.com/cryptopedia/crypto-oracle-blockchain-overview) bridge the information gap between on-chain and off-chain environments. Decentralized oracle services like [Chainlink](https://www.gemini.com/cryptopedia/chainlink-oracle-what-is-chainlink-crypto) and [API3](https://www.gemini.com/cryptopedia/api3-democratizing-information-with-decentralized-apis) play a crucial role in feeding off-chain data to blockchain-enabled smart contracts and contribute to blockchain interoperability by ensuring that different ecosystems are referring to a common source of truth.

**Bridges and swaps**: Cross-chain bridges enable a digital asset owned by a party to be locked on one chain while an identical asset is “minted” on another chain and sent to an address owned by the original owner. In contrast, [atomic swaps](https://www.gemini.com/cryptopedia/what-is-an-atomic-swap-token-swap) enable users to exchange tokens from different blockchain networks in a decentralized manner. Both are automatically enabled through the use of smart contracts and play a central role in facilitating seamless cross-chain value transfers.