# Day 81

Tags: Blockchain, Solidity
Date: October 3, 2023
Status: Done

**Task of the days**

dApps - Decentralized Applications

- Client libraries
    - Ethers.js
    - Web3
    - Moralis
- Client Nodes
    - Geth
    - Besu
    - Nethermind
    - Substrate
- Applicability
    - DeFi
    - DAOs
    - NFT’s
    - Payments
    - Insurance
- Testing
- Deployment
- Maintenance
- Architecture
- Security

---

### [dApps - Decentralized Applications](https://www.coindesk.com/learn/what-is-a-dapp-decentralized-apps-explained/)

A [decentralized application](https://www.coindesk.com/learn/what-is-a-decentralized-application/) – or dapp – is like a digital app found on any smartphone or laptop, with the additional feature of employing [blockchain technology](https://www.coindesk.com/learn/what-is-blockchain-technology/) to keep users’ data out of the hands of the organizations behind it. Just like [cryptocurrency](https://www.coindesk.com/learn/what-is-cryptocurrency/) is decentralized money, dapps are decentralized apps.

The blockchain stores copies of its expanding stack of data on a larger number of participating computers, known as “nodes”, all at once. These computers are owned by users, not by the creators of the dapp. 

Dapps are as varied conventional apps: They can provide social networks, games, entertainment, productivity tools and so on. Many are designed as tools to help consumers access decentralized financial services, or DeFi. This latter function is so widespread that the Ethereum network white-paper categorized dapps into “financial”, “semi-financial” and “other”.

Ethereum has been the dominant host for dapps so far. At its foundation, one of the primary goals of the network was to make dapps easier to create. 

Dapp users may feel more secure in the knowledge that the creators of the application cannot control how it is used - at least, not in the conventional way. For example, the creators of a social network dapp are powerless to remove a post or exclude a user. They are also unable to sell users’ data to other entities because dapps run autonomously once they’re launched.

How is this possible? It’s all down to the use of [smart contracts](https://www.coindesk.com/learn/how-do-ethereum-smart-contracts-work/) – computer programs deployed and on a blockchain designed to execute the rules of a contract without human involvement. For example, a smart contract could be coded to issue a loan once a user deposits a sufficient amount of collateral into it. Dapps are also commonly open source, meaning that anyone can view and use the underlying code.

Decentralized autonomous organizations, or [DAOs](https://www.coindesk.com/learn/what-is-a-dao/), can be seen as a kind of dapp. They aim to use an intricate arrangement of smart contracts to achieve the functions of a traditional organization without the need for corporate executives and hierarchies. They determine policy entirely through a weighted voting system where members who lock away more tokens possess greater voting power. The idea behind this concept is that those who have committed more funds to a DAO will be more likely to participate in it honestly, for the good of the organization.

---

### Client libraries

**[Ethers.js](https://docs.ethers.io/)** 

The ethers.js library aims to be a complete and compact library for interacting with the Ethereum Blockchain and its ecosystem. It was originally designed for use with ethers.io and has since expanded into a more general-purpose library.

[Web3.js](https://web3js.readthedocs.io/)

web3.js is a collection of libraries that allow you to interact with a local or remote ethereum node using HTTP, IPC or WebSocket.

---

### Client nodes

A blockchain is a distributed network of computers (known as nodes) running software that can verify blocks and transaction data. The software application, known as a client, must be run on your computer to turn it into a blockchain node.

- [**Geth**](https://geth.ethereum.org/docs)
    
    Go Ethereum (Geth) is one of the three original implementations (along with C++ and Python) of the Ethereum protocol. It is written in Go, fully open source and licensed under the GNU LGPL v3.
    

- [**Besu](https://github.com/hyperledger/besu)**
Besu is an Apache 2.0 licensed, MainNet compatible, Ethereum client written in Java

- **[Nethermind](https://docs.nethermind.io/nethermind/)**
Nethermind is a high-performance, highly configurable full Ethereum protocol client built on .NET that runs on Linux, Windows, and macOS, and supports Clique, Aura, Ethash, and Proof-of-Stake consensus algorithms.

- **[Substrate](https://docs.substrate.io/quick-start/substrate-at-a-glance/)**
**What is Substrate**
Substrate is a Software Development Kit (SDK) that uses Rust-based libraries and tools to enable you to build application-specific blockchains from modular and extensible components. Application-specific blockchains that are built with Substrate can run as standalone services or in parallel with other chains to take advantage of the shared security provided by the Polkadot ecosystem. Substrate includes default implementations of the core components of the blockchain infrastructure to allow you to focus on the application logic.
    
    **What is FRAME?**
    
    FRAME provides the core modular and extensible components that make the Substrate software development kit flexible and adaptable to different use cases. FRAME include Rust-based programs and libraries that simplify and streamline the development of application-specific logic. Most of the functionality that FRAME provides takes the form of plug-in modules called **pallets** that you can add and configure to suit your requirements.
    
    **Why use Substrate and FRAME?**
    
    By using Substrate and FRAME, you can build proof-of-concept application-specific blockchains without the complexity of building a blockchain from scratch or the limitations of building on a general-purpose blockchain. With Substrate and FRAME, you can focus on crafting the business logic that makes your chain unique and innovative with the additional benefits of flexibility, upgradeability, open source licensing, and cross-consensus interoperability.
    

**What is a Substrate node?**

Every blockchain platform relies on a decentralized network of computers—called nodes—that communicate with each other about transactions and blocks. In general, a node in this context is the software running on the connected devices rather than the physical or virtual machine in the network. As software, Substrate nodes consist of two main parts with separate responsibilities:

- A **core client** with outer node services to handle network and blockchain infrastructure activity.
- A **runtime** with the business logic for state transitions and the current state of the blockchain.

**Why build a custom runtime**

The separation of responsibilities into client-driven activity and runtime-driven activity is a critical part of what makes Substrate nodes upgradeable. The application logic is what makes your chain unique and it's stored on-chain in the form of a WebAssembly binary. If you make changes to the application logic, you simply compile a new WebAssembly binary. You can then submit a transaction to update the WebAssembly binary currently stored on-chain with your updated binary. Because the custom runtime is a self-contained object that's stored as part of the chain state, you can easily iterate on the application design and evolve your project as your community evolves.

---

### Applicability

dApps can be used for just about anything that requires two or more parties to agree on something. When the appropriate conditions are met, the smart contract will execute automatically. An important differentiation is that these transactions are no longer based on trust but they are rather based on cryptographically-backed smart contracts.

**[DeFi](https://www.coinbase.com/learn/crypto-basics/what-is-defi)**
Decentralized finance offers financial instruments without relying on intermediaries such as brokerages, exchanges, or banks by using smart contracts on a blockchain.

**[DAOs](https://consensys.io/blog/what-is-a-dao-and-how-do-they-work)**
A decentralized autonomous organization (DAO) is an emerging form of legal structure. With no central governing body, every member within a DAO typically shares a common goal and attempt to act in the best interest of the entity. Popularized through cryptocurrency enthusiasts and blockchain technology, DAOs are used to make decisions in a bottoms-up management approach.

[NFTs](https://www.investopedia.com/non-fungible-tokens-nft-5115211)
A non-fungible token (NFT) is a financial security consisting of digital data stored in a blockchain, a form of distributed ledger. The ownership of an NFT is recorded in the blockchain, and can be transferred by the owner, allowing NFTs to be sold and traded.

---

### [dApps  architecture](https://www.preethikasireddy.com/post/the-architecture-of-a-web-3-0-application)

The architecture of Web3 application are completely different from Web 2.0 applications.

Take Medium, for example, a simple blogging site that let’s users publish their own content and interact with content from others.

As a web 2.0 application, it may sound simple, but there’s a lot that goes into Medium’s architecture to make it all possible:

**First**, there must be a place to store essential data, such as users, posts, tags, comments, like, and so on. This requires a constantly updated database.

**Second**, backend code (written in a language like Node.js, Java, or Python) must define Meidum’s business logic. For examepl, what happens when a new user signs up, publishes a new blog, or comments on someone else’s blog?

**Third,** frontend code (typically written in Javascript, HTML, and CSS) must define Medium’s UI logic. For instance, what does the site look like, and what happens when a user interacts with each element on the page?

Putting it all together, when you write a blog post on Medium, you interact with its frontend, which talks to its backend, which talks to tis database. All of this code is hosted on centralized servers and sent to users throught an internet browser. This is a good high-level summary of how most Web 2.0 applications work today.

![Screen Shot 2023-10-01 at 1.41.48 PM.png](Day%2081%204a627163f45b49c199b0349ad24b9769/Screen_Shot_2023-10-01_at_1.41.48_PM.png)

But all of that’s changing.

Blockchain technology has unlocked an exciting new direction for Web 3.0 applications. In this article, we're going to focus on what the Ethereum blockchain brings to the table.

### What makes Web3 different?

Unlike Web 2.0 applications like Medium, Web 3.0 eliminates the middle man. There’s no centralized database that stores the application state, and there’s no centralized web server where the backend logic resides.

Instead, you can leverage blockchain to build apps on a decentralized state machine that’s maintained by anonymous nodes on the internet.

By “state machine,” I mean a machine that maintains some given program state and future states allowed on that machine. Blockchains are state machines that are instantiated with some genesis state and have very strict rules (i.e., consensus) that define how that state can transition.

Better yet, no single entity controls this decentralized state machine — it is collectively maintained by everyone in the network.

And what about a backend server? Instead of how Medium’s backend was controlled, in Web 3.0 you can write smart contracts that define the logic of your applications and deploy them onto the decentralized state machine. This means that every person who wants to build a blockchain application deploys their code on this shared state machine.

And the front end? It pretty much stays the same, with some exceptions, which we will cover later.

Here’s what the architecture looks like:

![Screen Shot 2023-10-01 at 2.47.43 PM.png](Day%2081%204a627163f45b49c199b0349ad24b9769/Screen_Shot_2023-10-01_at_2.47.43_PM.png)

### How does the frontend code communicate with smart contracts on ethereum?

We want our frontend to communicate with our smart contracts so that they can invoke functions, but recall that Ethereum is a decentralized network. Every node in the Ethereum network keeps a copy of all states on the Ethereum state machine, including the code and data associated with every smart contract.

When we want to interact with the data and code on a blockchain, we need to interact with one of these nodes. This is because any node can broadcast a request for a transaction to be executed on the EVM. A miner will then execute the transaction and propagate the resulting state change to the rest of the network.

There are two ways to broadcast a new transaction:

1. Set up your own node which runs the ethereum blockchain software
2. Use nodes provided by third-party services like infura, alchemy and quicknode

If you use a third-party service, you don’t have to deal with all the headaches of running a full node yourself. After all, setting up a new Ethereum node on your own server can take days. (There’s a lot of data to sync — It can even take up more bandwidth and storage than a typical laptop can handle.)

Moreover, the cost of storing the full Ethereum blockchain goes up as your DApp scales, and you need to add more nodes to expand your infrastructure. That’s why, as your infrastructure becomes more complex, you’ll need full-time DevOps engineers. They’ll help you maintain the infrastructure to ensure reliable uptime and fast response times.

All that to say, avoiding these headaches is why many DApps choose to use services like Infura or Alchemy to manage their node infrastructure for them. Of course, there’s a trade-off since this creates a centralized chokepoint, but let’s leave that rabbit hole for another day. ;)

Moving on, let’s talk about providers. The nodes that you connect with when you need to interact with the blockchain (whether you set them up yourself or use existing ones from third-party services) are often called “providers.”

![Screen Shot 2023-10-01 at 2.50.47 PM.png](Day%2081%204a627163f45b49c199b0349ad24b9769/Screen_Shot_2023-10-01_at_2.50.47_PM.png)

Every Ethereum client (i.e. provider) implements a JSON-RPC specification. This ensures that there’s a uniform set of methods when frontend applications want to interact with the blockchain. If you need a primer on JSON-RPC, it’s a stateless, lightweight remote procedure call (RPC) protocol that defines several data structures and the rules for their processing. It’s transport-agnostic, so the concepts can be used within the same process, over sockets, over HTTP, or in many various message-passing environments. It uses JSON (RFC 4627) as a data format.

Once you connect to the blockchain through a provider, you can read the state stored on the blockchain. But if you want to write to the state, there’s still one more thing you need to do before you can submit the transaction to the blockchain— “sign” the transaction using your private key.

For instance, imagine we have a DApp that lets users read or publish blog posts to the blockchain. You might have a button on the frontend that allows anyone to query for the blog posts written by a particular user. (Recall that reading from the blockchain does not require a user to sign a transaction.)

However, when a user wants to publish a new post onto the chain, our DApp would ask the user to “sign” the transaction using their private key — only then would the DApp relay the transaction to the blockchain. Otherwise, the nodes wouldn’t accept the transaction.

This “signing” of transactions is where [Metamask](https://metamask.io/) typically comes in.

![Screen Shot 2023-10-01 at 3.23.44 PM.png](Day%2081%204a627163f45b49c199b0349ad24b9769/Screen_Shot_2023-10-01_at_3.23.44_PM.png)

Metamask is a tool that makes it easy for applications to handle key management and transaction signing. It’s pretty simple: Metamask stores a user’s private keys in the browser, and whenever the frontend needs the user to sign a transaction, it calls on Metamask.

Metamask also provides a connection to the blockchain (as a “provider”) since it already has a connection to the nodes provided by Infura since it needs it to sign transactions. In this way, Metamask is both a provider and a signer.

### Storage on the blockchain

Of course, this architecture makes sense if you’re building an app where all of the smart contracts and data live entirely on the Ethereum blockchain. But anyone who has built apps on Ethereum knows that storing everything on the blockchain gets really expensive, really fast.

Keep in mind that, with Ethereum, the user pays every time they add new data to the blockchain. That’s because adding a state to the decentralized state machine increases the costs for nodes that are maintaining that state machine.

Asking users to pay extra for using your DApp every time their transaction requires adding a new state is not the best user experience. One way to combat this is to use a decentralized off-chain storage solution, like [IPFS](https://ipfs.io/) or [Swarm](https://www.ethswarm.org/)

IPFS is a distributed file system for storing and accessing data. So, rather than storing data in a centralized database, the IPFS system distributes and stores the data in a peer-to-peer network. This makes it easy for you to retrieve it when you need to.

IPFS also has an incentive layer known as “Filecoin.” This layer incentivizes nodes around the world to store and retrieve this data. You can use a provider like Infura (which provides you with an IPFS node) or Pinata (which provides an easy-to-use service where you can “pin” your files to IPFS and take the IPFS hash and store that on the blockchain).

Swarm is similar in that it’s a decentralized storage network, but there’s one notable difference. While Filecoin is a separate system, Swarm’s incentive system is built-in and enforced through smart contracts on the Ethereum blockchain for storing and retrieving data.

So now, with IPFS or Swarm, our application architecture looks like this:

![Screen Shot 2023-10-01 at 3.27.38 PM.png](Day%2081%204a627163f45b49c199b0349ad24b9769/Screen_Shot_2023-10-01_at_3.27.38_PM.png)

Astute readers may also have noticed in the diagram below that the frontend code is not stored on the blockchain. We could host this code on AWS, as we normally would in Web 2.0, but that creates a centralization chokepoint for your DApp. What if AWS goes down? What if it censors your app?

That’s why, if you want to build a truly decentralized app, you might choose to host your frontend on a decentralized storage solution, like IPFS or Swarm.

So now your application architecture looks more like this:

![Screen Shot 2023-10-01 at 3.30.04 PM.png](Day%2081%204a627163f45b49c199b0349ad24b9769/Screen_Shot_2023-10-01_at_3.30.04_PM.png)

**Querying the blockchain**

So far, we’ve talked about how to write to the blockchain by signing transactions and then sending them to the blockchain. But what about reading data from the smart contracts on the blockchain? There are two primary ways to do this:

1) Smart Contract Events

You can use the Web3.js library to query and listen for smart contract events. You can listen to specific events and specify a callback every time the event is fired. For instance, if you have a smart contract that sends a continuous payment stream from person A to person B every block, then you can emit an event every time a new payment is made to person B. Your frontend code can listen to events being fired by the smart contract and carry out specific actions based on it.

2) The Graph

The above approach works, but it has some limitations. For instance, what if you deploy a smart contract and later realize you need an event emitted that you didn’t originally include? Unfortunately, you’d have to redeploy a new smart contract with that event and data. Moreover, using callbacks to handle various UI logic gets very complex very quickly.

This is where “[The Graph](https://thegraph.com/)” comes in.

The Graph is an off-chain indexing solution that makes it easier to query data on the Ethereum blockchain. The Graph allows you to define which smart contracts to index, which events and function calls to listen to, and how to transform incoming events into entities that your frontend logic (or whatever is using the API) can consume. It uses GraphQL as a query language, which many frontend engineers love because of how expressive it is compared to traditional REST APIs.

By indexing blockchain data, The Graph lets us query on-chain data in our application logic with low latency.

Now, your DApp architecture looks like this:

![Screen Shot 2023-10-01 at 3.32.46 PM.png](Day%2081%204a627163f45b49c199b0349ad24b9769/Screen_Shot_2023-10-01_at_3.32.46_PM.png)

### Scaling Your DApp

As you may have heard, Ethereum doesn’t scale - at least, not yet

Clearly, we have a problem here. Building a DApp on Ethereum with high gas fees and full blocks leads to a very bad UX. Thankfully, there are some solutions under development.

One popular scaling solution is [Polygon](https://polygon.technology/) , an L2 scaling solution. Instead of executing transactions on the main blockchain, Polygon has “sidechains” that process and execute transactions. A sidechain is a secondary blockchain that interfaces with the main chain. Every so often, the sidechain submits an aggregation of its recent blocks back to the primary chain.

![Screen Shot 2023-10-01 at 3.36.13 PM.png](Day%2081%204a627163f45b49c199b0349ad24b9769/Screen_Shot_2023-10-01_at_3.36.13_PM.png)

Other examples of L2 solutions are [Optimistic Rollups and zkRollups](https://ethereum.org/en/developers/docs/scaling/layer-2-rollups).  The idea here is similar: We batch transactions off-chain using a “rollup” smart contract and then periodically commit these transactions to the main chain.

The take-home idea is this: L2 solutions do transaction execution (i.e., the slow part) off-chain, with only the transaction data stored on-chain. This lets us scale the blockchain because we don’t have to execute every single transaction on-chain. This also makes transactions faster and cheaper — and they can still communicate with the main Ethereum blockchain when necessary.

![Screen Shot 2023-10-01 at 3.36.42 PM.png](Day%2081%204a627163f45b49c199b0349ad24b9769/Screen_Shot_2023-10-01_at_3.36.42_PM.png)

### Cobbling it all together

If all of this is making your head spin, you’re not alone. Cobbling together all of these tools is complex and can lead to a painful developer experience. But don’t worry — we’re starting to see new developer frameworks which really improve the experience for developers.

For instance, [Hardhat](https://hardhat.org/) is a developer framework that makes it easier for Ethereum developers to build, deploy, and test their smart contracts. Hardhat offers the “Hardhat Network,” which developers can use to deploy their smart contracts onto a local network — without having to deal with live environments. Better yet, it offers a great [plugin ecosystem](https://hardhat.org/plugins/) that makes developers’ lives much easier. Hardhat also provides console.log() functionality, similar to javascript, for debugging purposes.

Of course, this is just the beginning. I hope that we continue to see better developer tooling in the future.

**Conclusion**

Most people spend months figuring out how the tooling chain works, so if you’re a new DApp developer, I hope this article saved you some time. It’s time to get building!

If building Web 3.0 applications is something you are interested in, then sign up for our next cohort of the [DappCamp](https://www.dappcamp.xyz/), where you will learn how to build and deploy your first Dapp on Ethereum.

As always, if you have any questions or found any errors in this blog post, please let me know in the comments! :)

### [Security](https://github.com/Dexaran/DAPP-security-standards/blob/master/README.md)

dApps face unique security challenges as they run on immutable blockchains. dApps are harder to maintain, and developers cannot modify or update their codes once deployed. Therefore, special consideration must be taken before putting it on the blockchain.

Visit the following resources to learn more:

- **[DAPP Security Standards](https://github.com/Dexaran/DAPP-security-standards/blob/master/README.md)**
- **[dApp Security Considerations](https://livebook.manning.com/book/building-ethereum-dapps/chapter-14/)**
- **[dApp Security:All You Need to Know](https://www.immunebytes.com/blog/dapp-security/#Benefits_of_DApps_Security)**

Visit the following resources to learn more:

- **[What Is a dApp? A Guide to Decentralized Applications](https://www.sofi.com/learn/content/what-is-a-dapp/)**
- **[Blockchain Use Cases and Applications by Industry](https://consensys.net/blockchain-use-cases/)**
- **[The real-world use cases for blockchain technology](https://roboticsandautomationnews.com/2022/05/20/the-real-world-use-cases-for-blockchain-technology/)**

****