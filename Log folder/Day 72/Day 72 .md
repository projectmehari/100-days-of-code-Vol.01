# Day 72

Tags: Blockchain
Date: September 24, 2023
Status: Done

Task of the day

- Basic Blockchain Knowledge
    - What is Blockchain
    - Decentralization
    - Why it matters?
    - Blockchain Structure
    - Basic Blockchain Operations
    - Applications and Uses

Exercise

**[How to Develop an NFT Smart Contract (ERC721) with Alchemy](https://docs.alchemy.com/docs/how-to-develop-an-nft-smart-contract-erc721-with-alchemy)**

---

### Blockchain

A blockchain is a decentralized, distributed, and oftentimes public, digital ledger consisting of records called blocks that is used to record transactions across many computers so that any involved block cannot be altered retroactively, without the alteration of all subsequent blocks.

Visit the following resources to learn more:

- **[Blockchain Explained](https://www.investopedia.com/terms/b/blockchain.asp)**
- **[What is decentralization?](https://aws.amazon.com/blockchain/decentralization-in-blockchain/)**
- **[How does a blockchain work?](https://youtu.be/SSo_EIwHSd4)**
- **[What Is a Blockchain? | Blockchain Basics for Developers](https://youtu.be/4ff9esY_4aU)**

---

### Decentralization

In blockchain, decentralization refers to the transfer of control and decision-making from a centralized entity (individual, organization, or group thereof) to a distributed network. Decentralized networks strive to reduce the level of trust that participants must place in one another, and deter their ability to exert authority or control over one another in ways that degrade the functionality of the network.

Visit the following resources to learn more:

- **[What is decentralization?](https://aws.amazon.com/blockchain/decentralization-in-blockchain/)**
- **[What is Decentralization in Blockchain?](https://www.blockchain-council.org/blockchain/what-is-decentralization-in-blockchain/)**

---

### Why it matter

The nature of blockchain allows for trustless systems to be built on top of it. Users don’t rely on a centralized group of people, such as a bank, to make decisions and allow transactions to flow through. Because the system is decentralized, users know that transactions will never be denied for non-custodial reasons.

This decentralization enables use-cases that were previously impossible, such as parametric insurance, decentralized finance, and decentralized organizations (DAOs), among a few. This allows developers to build products that provide immediate value without having to go through a bureaucratic process of applications, approvals, and general red tape.

Visit the following resources to learn more:

- **[Why Blockchain?](https://www.blockchain.education/blockchain101/blockchain)**
- **[What Is The Blockchain And Why Does It Matter?](https://www.forbes.com/sites/theyec/2020/05/18/what-is-the-blockchain-and-why-does-it-matter/)**
- **[Web3/Crypto: Why Bother?](https://continuations.com/post/671863718643105792/web3crypto-why-bother)**
- **[Why is Blockchain Important and Why Does it Matter](https://www.simplilearn.com/tutorials/blockchain-tutorial/why-is-blockchain-important)**

---

### Blockchain Structure

The blockchain gets its name from its underlying structure. The blockchain is organized as a series of “blocks” that are “chained” together.
Understanding blockchain security requires understanding how the blockchain is put together. This requires knowing what the blocks and chains of blockchain are and why they are designed the way that they are.

Visit the following resources to learn more:

- **[Blockchain Architecture Basics: Components, Structure, Benefits & Creation](https://mlsdev.com/blog/156-how-to-build-your-own-blockchain-architecture)**
- **[Blockchain Architecture 101: Components, Structure, and Benefits](https://komodoplatform.com/en/academy/blockchain-architecture-101/)**
- **[Blockchain structure](https://resources.infosecinstitute.com/topic/blockchain-structure/)**
- **[Blockchain Basics | Coursera](https://www.coursera.org/lecture/blockchain-basics/blockchain-structure-5rj9Z)**

---

### Basic Blockchain operations

Operations in a decentralized networks are the responsibility of the peer participants and their respective computational nodes. These are specific for each type of blockchain.

Visit the following resources to learn more:

- **[Blockchain Basics: Structure, Operations, and the Bitcoin Blockchain](https://www.mlq.ai/blockchain-basics/)**
- **[How Bitcoin blockchain actually work (Video)](https://www.youtube.com/watch?v=bBC-nXj3Ng4)**
- **[Bitcoin blockchain transactions | Bitcoin Developer](https://developer.bitcoin.org/reference/transactions.html)**
- **[Ethereum blockchain transactions | ethereum.org](https://ethereum.org/en/developers/docs/transactions/)**
- **[Blockchain Basics | Coursera](https://www.coursera.org/lecture/blockchain-basics/basic-operations-OxILB)**

---

### Applications and uses of Blockchain technology

Blockchain applications go far beyond cryptocurrency and bitcoin. With its ability to create more transparency and fairness while also saving businesses time and money, the technology is impacting a variety of sectors in ways that range from how contracts are enforced to making government work more efficiently.

---

### Smart contract (ERC721) template from Open Zepplin

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721Enumerable.sol";
import "@openzeppelin/contracts/token/ERC721/extensions/ERC721URIStorage.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/Counters.sol";

contract MyFirst is ERC721, ERC721Enumerable, ERC721URIStorage, Ownable {
    using Counters for Counters.Counter;

    Counters.Counter private _tokenIdCounter;

    constructor() ERC721("MyFirst", "Frst") {}

    function safeMint(address to, string memory uri) public onlyOwner {
        uint256 tokenId = _tokenIdCounter.current();
        _tokenIdCounter.increment();
        _safeMint(to, tokenId);
        _setTokenURI(tokenId, uri);
    }

    // The following functions are overrides required by Solidity.

    function _beforeTokenTransfer(address from, address to, uint256 tokenId, uint256 batchSize)
        internal
        override(ERC721, ERC721Enumerable)
    {
        super._beforeTokenTransfer(from, to, tokenId, batchSize);
    }

    function _burn(uint256 tokenId) internal override(ERC721, ERC721URIStorage) {
        super._burn(tokenId);
    }

    function tokenURI(uint256 tokenId)
        public
        view
        override(ERC721, ERC721URIStorage)
        returns (string memory)
    {
        return super.tokenURI(tokenId);
    }

    function supportsInterface(bytes4 interfaceId)
        public
        view
        override(ERC721, ERC721Enumerable, ERC721URIStorage)
        returns (bool)
    {
        return super.supportsInterface(interfaceId);
    }
}
```

Deployed contract hash 

[https://sepolia.etherscan.io/tx/0xe2024a6391fc3b6dc69a5ac0008430b6b89b7764ac5d98bef85fb739b7c946b7](https://sepolia.etherscan.io/tx/0xe2024a6391fc3b6dc69a5ac0008430b6b89b7764ac5d98bef85fb739b7c946b7)