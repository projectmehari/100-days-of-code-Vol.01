# Day 82

Tags: Blockchain
Date: October 4, 2023
Status: Done

Task of the day

- Node as a service
    - Alchemy
    - Infura
    - Moralis
    - Quicknode
    
    Building for scale
    
    - State and payment Channels
    - Optmistic Rollups & Fraud Proofs
    - Zk Rollsups & Zero knowledge proof
    - Validum
    - Plasma
    - Sidechains
    - Ethereum 2.0
    - On-chain Scalling

---

### Node as a Service

Running your own blockchain node can be challenging, especially when getting started or while scaling fast. There are a number of services that run optimized node infrastructures for you, so you can focus on developing your application or product instead.

**Stakers**

Solo stakers must run their own infrastructure rather than relying on third-party providers. This means running an execution client coupled with a consensus client. Before [The Merge](https://ethereum.org/en/roadmap/merge/), it was possible to run a consensus client only and use a centralized provider for execution data; this is no longer possible - a solo staker must run both clients. However, there are services available to ease this process.

[Read more on running a node](https://ethereum.org/en/developers/docs/nodes-and-clients/run-a-node/).

The services described on this page are for non-staking nodes.

**How do Node services work?**

Node service providers run distributed node clients behind the scenes for you, so you don't have to.

These services typically provide an API key that you can use to write to and read from the blockchain. They often include access to [Ethereum testnets](https://ethereum.org/en/developers/docs/networks/#ethereum-testnets) in addition to Mainnet.

Some services offer you your own dedicated node that they manage for you, while others use load balancers to distribute activity across nodes.

Almost all node services are extremely easy to integrate with, involving one line changes in your code to swap out your self hosted node, or even switch between the services themselves.

Often times node services will run a variety of [node clients](https://ethereum.org/en/developers/docs/nodes-and-clients/#execution-clients) and [types](https://ethereum.org/en/developers/docs/nodes-and-clients/#node-types), allowing you to access full and archive nodes in addition to client specific methods in one API.

It's important to note that node services do not and should not store your private keys or information.****

**What are the benefits of using a node service?**

The main benefit for using a node service is not having to spend engineering time maintaining and managing nodes yourself. This allows you to focus on building your product rather than having to worry about infrastructure maintenance.

Running your own nodes can be very expensive from storage to bandwidth to valuable engineering time. Things like spinning up more nodes when scaling, upgrading nodes to the latest versions, and ensuring state consistency, can distract from building and spending resources on your desired web3 product.

**What are the cons of using a node service?**

By using a node service you are centralizing the infrastructure aspect of your product. For this reason, projects that hold decentralization to the upmost importance might prefer self-hosting nodes rather than outsourcing to a 3rd party.

Read more about the [benefits of running your own node](https://ethereum.org/en/developers/docs/nodes-and-clients/#benefits-to-you).****

Visit the following resources to learn more:

- **[Blockchain Node Providers and How They Work](https://www.infoq.com/articles/blockchain-as-a-service-get-block/)**
- **[Node as a Service - Ethereum](https://ethereum.org/en/developers/docs/nodes-and-clients/nodes-as-a-service/)**

---

### NaaS - Alchemy

Alchemy is a developer platform that empowers companies to build scalable and reliable decentralized applications without the hassle of managing blockchain infrastructure in-house.

[Case study - Zapper](https://www.alchemy.com/case-study/zapper)

---

### Infura

Infura provides the tools and infrastructure that allow developers to easily take their blockchain application from testing to scaled deployment - with simple, reliable access to Ethereum and IPFS.

Visit the following resources to learn more:

- **[Infura official site](https://infura.io/)**

---

### Quicknode

QuickNode is a Web3 developer platform used to build and scale blockchain applications.

Visit the following resources to learn more:
-  **[Quicknode official site](https://www.quicknode.com/)**

---

### Building for scale

**[State and payment channels](https://education.district0x.io/general-topics/understanding-ethereum/basics-state-channels/)**

State channels refer to the process in which users transact with one another directly outside of the blockchain, or ‘off-chain,’ and greatly minimize their use of ‘on-chain’ operations. It’s one of the most exciting Ethereum scaling solutions in development and the closest advancement to being production ready.

State channels are very similar to the concept of payment channels in Bitcoin’s Lightning Network, but instead of only supporting payments, they also support general ‘state updates.’ For example, votes conducted on the [District Registry](https://education.district0x.io/district0x-specific-topics/understanding-distict0x/the-district-registry/) could be updated in a state channel and only broadcasted to the Ethereum network once all votes have been collected. This magnifies the number of computation developers can move off-chain.

**Why is this exciting?**

While at first glance it might seem like transactions within state channels aren’t backed up by the same level of security as on-chain transactions, the magic is that we can achieve the same level of security without using as much of the network’s resources. By being able to always revert back to the main chain as an arbitration mechanism, users are game-theoretically incentivized to act rationally. Also, each transaction is signed the same way a valid Ethereum transaction would be.

On-chain transactions aren’t completely eliminated but rather reduced to only the necessary sequences. Users have to create and pay for an Ethereum transaction when they first open up the channel. When they’re ready to close the channel, they again have to pay fees to process a transaction on the Ethereum blockchain. Cutting the number of necessary on-chain transactions down to two drastically reduces the costs and increase the speed associated with using Ethereum.

Think of State Channels like a time card you’d use at work. You punch in when you begin working (Transaction #1) and you punch out at the end of the shift (Transaction #2). Every action that happens in the middle doesn’t need to be logged on the time card.

**State channels under the hood**

State Channels sound great in theory, but they’re even more interesting when looking at them in practice. Here’s a brief example to illustrate how they functionally work:

1. Users lock up a portion of the state by sending money to a multi-signature contract that has the ability to accept Ether and payout all parties who have sent it Ether.
2. Users sign transactions and send them to one another, each one making a copy of the signature for later reference.
3. Each transaction contains a nonce so the smart contract can know the chronological order of transactions.
4. Once both parties are done, they close the state by submitting a transaction to the Ethereum blockchain.
5. After the state is updated and unlocked, the smart contract sends each party their remaining Ether balance.

**Why it’s important**

Scaling is arguably the biggest obstacle that blockchains face when it comes to achieving mainstream adoption. While some applications can thrive today, most are still too slow and expensive for regular users.

State channels increase the throughput of public blockchains because they decrease the computational load that nodes have to expend when processing and storing transactions. This will make it easier to run a node, which makes the job of validating the miners’ work more decentralized. Similarly, State Channels reduce the costs required to use the Ethereum network. Instead of paying fees for each transaction, users only have to pay for gas when they open and close a channel.

State channels also help preserve user privacy. Transactions within a channel are only known by the participants in the channel. This is in contrast to transacting on the Ethereum blockchain where every transaction is recorded in a publicly auditable ledger.

Lastly, transactions within state channels get instant finality. Users don’t have to wait for each transaction to confirm onto the blockchain because each signed transaction abides by the network rules. This makes the user experience seamless and more mirrors how popular online applications operate today.

Visit the following resources to learn more:

- **[The Basics of State Channels](https://education.district0x.io/general-topics/understanding-ethereum/basics-state-channels/)**
- **[State Channels: An Introduction to Off-chain Transactions](https://www.talentica.com/blogs/state-channels-an-introduction-to-off-chain-transactions/)**

---

### Optimistic Rollups and Fraud Proofs

‍Optimistic rollups are a layer 2 (L2) construction that improves throughput and latency on Ethereum’s base layer by moving computation and data storage off-chain. An optimistic rollup processes transactions outside of Ethereum Mainnet, reducing congestion on the base layer and improving scalability.

Optimistic rollups allow anyone to publish blocks without providing proofs of validity. However, to ensure the chain remains safe, optimistic rollups specify a time window during which anyone can dispute a state transition.

Visit the following resources to learn more:

- **[How Do Optimistic Rollups Work (The Complete Guide)](https://www.alchemy.com/overviews/optimistic-rollups)**

---

### Zero Knowledge Rollups and Zero Knowledge Proof

Zero-knowledge rollups (ZK-rollups) are layer 2 [scaling solutions](https://ethereum.org/en/developers/docs/scaling/) that increase throughput on Ethereum Mainnet by moving computation and state-storage off-chain. ZK-rollups can process thousands of transactions in a batch and then only post some minimal summary data to Mainnet. This summary data defines the changes that should be made to the Ethereum state and some cryptographic proof that those changes are correct.****

**What are Zero-knowledge rollups?**

**Zero-knowledge rollups (ZK-rollups)** bundle (or 'roll up') transactions into batches that are executed off-chain. Off-chain computation reduces the amount of data that has to be posted to the blockchain. ZK-rollup operators submit a summary of the changes required to represent all the transactions in a batch rather than sending each transaction individually. They also produce validity proofs to prove the correctness of their changes.

The ZK-rollup's state is maintained by a smart contract deployed on the Ethereum network. To update this state, ZK-rollup nodes must submit a validity proof for verification. As mentioned, the validity proof is a cryptographic assurance that the state-change proposed by the rollup is really the result of executing the given batch of transactions. This means that ZK-rollups only need to provide validity proofs to finalize transactions on Ethereum instead of posting all transaction data on-chain like [optimistic rollups](https://ethereum.org/en/developers/docs/scaling/optimistic-rollups/).

There are no delays when moving funds from a ZK-rollup to Ethereum because exit transactions are executed once the ZK-rollup contract verifies the validity proof. Conversely, withdrawing funds from optimistic rollups is subject to a delay to allow anyone to challenge the exit transaction with a fraud proof.

ZK-rollups write transactions to Ethereum as `calldata`. `calldata` is where data that is included in external calls to smart contract functions gets stored. Information in `calldata` is published on the blockchain, allowing anyone to reconstruct the rollup’s state independently. ZK-rollups use compression techniques to reduce transaction data—for example, accounts are represented by an index rather than an address, which saves 28 bytes of data. On-chain data publication is a significant cost for rollups, so data compression can reduce fees for users.

**How do zk-rollups interact with ethereum?**

A ZK-rollup chain is an off-chain protocol that operates on top of the Ethereum blockchain and is managed by on-chain Ethereum smart contracts. ZK-rollups execute transactions outside of Mainnet, but periodically commit off-chain transaction batches to an on-chain rollup contract. This transaction record is immutable, much like the Ethereum blockchain, and forms the ZK-rollup chain.

The ZK-rollup’s core architecture is made up of the following components:

1. **On-chain contracts**: As mentioned, the ZK-rollup protocol is controlled by smart contracts running on Ethereum. This includes the main contract which stores rollup blocks, tracks deposits, and monitors state updates. Another on-chain contract (the verifier contract) verifies zero-knowledge proofs submitted by block producers. Thus, Ethereum serves as the base layer or "layer 1" for the ZK-rollup.
2. **Off-chain virtual machine (VM)**: While the ZK-rollup protocol lives on Ethereum, transaction execution and state storage happen on a separate virtual machine independent of the [EVM](https://ethereum.org/en/developers/docs/evm/). This off-chain VM is the execution environment for transactions on the ZK-rollup and serves as the secondary layer or "layer 2" for the ZK-rollup protocol. Validity proofs verified on Ethereum Mainnet guarantee the correctness of state transitions in the off-chain VM.

ZK-rollups are "hybrid scaling solutions"—off-chain protocols that operate independently but derive security from Ethereum. Specifically, the Ethereum network enforces the validity of state updates on the ZK-rollup and guarantees the availability of data behind every update to the rollup's state. As a result, ZK-rollups are considerably safer than pure off-chain scaling solutions, such as [sidechains](https://ethereum.org/en/developers/docs/scaling/sidechains/), which are responsible for their security properties, or [validiums](https://ethereum.org/en/developers/docs/scaling/validium/), which also verify transactions on Ethereum with validity proofs, but store transaction data elsewhere.

ZK-rollups rely on the main Ethereum protocol for the following:

**Data availability** 

ZK-rollups publish state data for every transaction processed off-chain to Ethereum. With this data, it is possible for individuals or businesses to reproduce the rollup’s state and validate the chain themselves. Ethereum makes this data available to all participants of the network as `calldata`.

ZK-rollups don’t need to publish much transaction data on-chain because validity proofs already verify the authenticity of state transitions. Nevertheless, storing data on-chain is still important because it allows permissionless, independent verification of the L2 chain's state which in turn allows anyone to submit batches of transactions, preventing malicious operators from censoring or freezing the chain.

On-chain is required for users to interact with the rollup. Without access to state data users cannot query their account balance or initiate transactions (e.g., withdrawals) that rely on state information.****

**Transaction finality**

Ethereum acts as a settlement layer for ZK-rollups: L2 transactions are finalized only if the L1 contract accepts the validity proof. This eliminates the risk of malicious operators corrupting the chain (e.g., stealing rollup funds) since every transaction must be approved on Mainnet. Also, Ethereum guarantees that user operations cannot be reversed once finalized on L1.****

**Censorship resistance**

Most ZK-rollups use a "supernode" (the operator) to execute transactions, produce batches, and submit blocks to L1. While this ensures efficiency, it increases the risk of censorship: malicious ZK-rollup operators can censor users by refusing to include their transactions in batches.

As a security measure, ZK-rollups allow users to submit transactions directly to the rollup contract on Mainnet if they think they are being censored by the operator. This allows users to force an exit from the ZK-rollup to Ethereum without having to rely on the operator’s permission.****

### **How do ZK-Rollups work?**

**Transactions**

Users in the ZK-rollup sign transactions and submit to L2 operators for processing and inclusion in the next batch. In some cases, the operator is a centralized entity, called a sequencer, who executes transactions, aggregates them into batches, and submits to L1. The sequencer in this system is the only entity allowed to produce L2 blocks and add rollup transactions to the ZK-rollup contract.

Other ZK-rollups may rotate the operator role by using a [proof-of-stake](https://ethereum.org/en/developers/docs/consensus-mechanisms/pos/) validator set. Prospective operators deposit funds in the rollup contract, with the size of each stake influencing the staker’s chances of getting selected to produce the next rollup batch. The operator’s stake can be slashed if they act maliciously, which incentivizes them to post valid blocks.

**How Zk-rollups publish transaction data on Ethereum**

As explained, transaction data is published on Ethereum as `calldata`. `calldata` is a data area in a smart contract used to pass arguments to a function and behaves similarly to [memory](https://ethereum.org/en/developers/docs/smart-contracts/anatomy/#memory). While `calldata` isn’t stored as part of Ethereum’s state, it persists on-chain as part of the Ethereum chain's [history logs(opens in a new tab)](https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html?highlight=memory#logs). `calldata` does not affect Ethereum's state, making it a cheap way to store data on-chain.

The `calldata` keyword often identifies the smart contract method being called by a transaction and holds inputs to the method in the form of an arbitrary sequence of bytes. ZK-rollups use `calldata` to publish compressed transaction data on-chain; the rollup operator simply adds a new batch by calling the required function in the rollup contract and passes the compressed data as function arguments. This helps reduce costs for users since a large part of rollup fees go toward storing transaction data on-chain.

**State commitments**

The ZK-rollup’s state, which includes L2 accounts and balances, is represented as a [Merkle tree](https://ethereum.org/en/whitepaper/#merkle-trees). A cryptographic hash of the Merkle tree’s root (Merkle root) is stored in the on-chain contract, allowing the rollup protocol to track changes in the state of the ZK-rollup.

The rollup transitions to a new state after the execution of a new set of transactions. The operator who initiated the state transition is required to compute a new state root and submit to the on-chain contract. If the validity proof associated with the batch is authenticated by the verifier contract, the new Merkle root becomes the ZK-rollup’s canonical state root.

Besides computing state roots, the ZK-rollup operator also creates a batch root—the root of a Merkle tree comprising all transactions in a batch. When a new batch is submitted, the rollup contract stores the batch root, allowing users to prove a transaction (e.g., a withdrawal request) was included in the batch. Users will have to provide transaction details, the batch root, and a [Merkle proof](https://ethereum.org/en/developers/tutorials/merkle-proofs-for-offline-data-integrity/) showing the inclusion path.

### **Validity proofs**

The new state root that the ZK-rollup operator submits to the L1 contract is the result of updates to the rollup’s state. Say Alice sends 10 tokens to Bob, the operator simply decreases Alice’s balance by 10 and increments Bob’s balance by 10. The operator then hashes the updated account data, rebuilds the rollup's Merkle tree, and submits the new Merkle root to the on-chain contract.

But the rollup contract won’t automatically accept the proposed state commitment until the operator proves the new Merkle root resulted from correct updates to the rollup’s state. The ZK-rollup operator does this by producing a validity proof, a succinct cryptographic commitment verifying the correctness of batched transactions.

Validity proofs allow parties to prove the correctness of a statement without revealing the statement itself—hence, they are also called zero-knowledge proofs. ZK-rollups use validity proofs to confirm the correctness of off-chain state transitions without having to re-execute transactions on Ethereum. These proofs can come in the form of a [ZK-SNARK(opens in a new tab)](https://arxiv.org/abs/2202.06877) (Zero-Knowledge Succinct Non-Interactive Argument of Knowledge) or [ZK-STARK(opens in a new tab)](https://eprint.iacr.org/2018/046) (Zero-Knowledge Scalable Transparent Argument of Knowledge).

Both SNARKs and STARKs help attest to the integrity of off-chain computation in ZK-rollups, although each proof type has distinctive features.

**ZK-SNARKs**

For the ZK-SNARK protocol to work, creating a Common Reference String (CRS) is necessary: the CRS provides public parameters for proving and verifying validity proofs. The security of the proving system depends on the CRS setup; if information used to create public parameters fall into the possession of malicious actors they may be able to generate false validity proofs.

Some ZK-rollups attempt to solve this problem by using a [multi-party computation ceremony (MPC)(opens in a new tab)](https://zkproof.org/2021/06/30/setup-ceremonies/amp/), involving trusted individuals, to generate public parameters for the ZK-SNARK circuit. Each party contributes some randomness (called "toxic waste") to the construct the CRS, which they must destroy immediately.

Trusted setups are used because they increase the security of the CRS setup. As long as one honest participant destroys their input, the security of the ZK-SNARK system is guaranteed. Still, this approach requires trusting those involved to delete their sampled randomness and not undermine the system's security guarantees.

Trust assumptions aside, ZK-SNARKs are popular for their small proof sizes and constant-time verification. As proof verification on L1 constitutes the larger cost of operating a ZK-rollup, L2s use ZK-SNARKs to generate proofs that can be verified quickly and cheaply on Mainnet.

**ZK-STARKs**

Like ZK-SNARKs, ZK-STARKs prove the validity of off-chain computation without revealing the inputs. However, ZK-STARKs are considered an improvement on ZK-SNARKs because of their scalability and transparency.

ZK-STARKs are 'transparent', as they can work without the trusted setup of a Common Reference String (CRS). Instead, ZK-STARKs rely on publicly verifiable randomness to set up parameters for generating and verifying proofs.

ZK-STARKs also provide more scalability because the time needed to prove and verify validity proofs increases *quasilinearly* in relation to the complexity of the underlying computation. With ZK-SNARKs, proving and verification times scale *linearly* in relation to the size of the underlying computation. This means ZK-STARKs require less time than ZK-SNARKs for proving and verifying when large datasets are involved, making them useful for high-volume applications.

ZK-STARKs are also secure against quantum computers, while the Elliptic Curve Cryptography (ECC) used in ZK-SNARKs is widely believed to be susceptible to quantum computing attacks. The downside to ZK-STARKs is that they produce larger proof sizes, which are more expensive to verify on Ethereum.

### How do validity proofs work in ZK-rollups?

Proof generation

Before accepting transactions, the operator will perform the usual checks. This includes confirming that:

- The sender and receiver accounts are part of the state tree.
- The sender has enough funds to process the transaction.
- The transaction is correct and matches the sender’s public key on the rollup.
- The sender’s nonce is correct, etc.

Once the ZK-rollup node has enough transactions, it aggregates them into a batch and compiles inputs for the proving circuit to compile into a succinct ZK-proof. This includes:

- A Merkle tree comprising all the transactions in the batch.
- Merkle proofs for transactions to prove inclusion in the batch.
- Merkle proofs for each sender-receiver pair in transactions to prove those accounts are part of the rollup's state tree.
- A set of intermediate state roots, derived from updating the state root after applying state updates for each transaction (i.e., decreasing sender accounts and increasing receiver accounts).

The proving circuit computes the validity proof by "looping" over each transaction and performing the same checks the operator completed before processing the transaction. First, it verifies the sender's account is part of the existing state root using the provided Merkle proof. Then it reduces the sender's balance, increases their nonce, hashes the updated account data and combines it with the Merkle proof to generate a new Merkle root.

This Merkle root reflects the sole change in the ZK-rollup's state: a change in the sender's balance and nonce. This is possible because the Merkle proof used to prove the account's existence is used to derive the new state root.

The proving circuit performs the same process on the receiver's account. It checks if the receiver's account exists under the intermediate state root (using the Merkle proof), increases their balance, re-hashes the account data and combines it with the Merkle proof to generate a new state root.

The process repeats for every transaction; each "loop" creates a new state root from updating the sender's account and a subsequent new root from updating the receiver's account. As explained, every update to the state root represents one part of the rollup's state tree changing.

The ZK-proving circuit iterates over the entire transaction batch, verifying the sequence of updates that result in a final state root after the last transaction is executed. The last Merkle root computed becomes the newest canonical state root of the ZK-rollup.

### Proof verification

After the proving circuit verifies the correctness of state updates, the L2 operator submits the computed validity proof to the verifier contract on L1. The contract's verification circuit verifies the proof's validity and also checks public inputs that form part of the proof:

- **Pre-state root**: The ZK-rollup’s old state root (i.e., before the batched transactions were executed), reflecting the L2 chain's last known valid state.
- **Post-state root**: The ZK-rollup’s new state root (i.e., after the execution of batched transactions), reflecting the L2 chain's newest state. The post-state root is the final root derived after applying state updates in the proving circuit.
- **Batch root**: The Merkle root of the batch, derived by *merklizing* transactions in the batch and hashing the tree's root.
- **Transaction inputs**: Data associated with the transactions executed as part of the submitted batch.

If the proof satisfies the circuit (i.e., it is valid), it means that there exists a sequence of valid transactions that transition the rollup from the previous state (cryptographically fingerprinted by the pre-state root) to a new state (cryptographically fingerprinted by the post-state root). If the pre-state root matches the root stored in the rollup contract, and the proof is valid, the rollup contract takes the post-state root from the proof and updates its state tree to reflect the rollup's changed state.

**Entries and exists**

Users enter the ZK-rollup by depositing tokens in the rollup's contract deployed on the L1 chain. This transaction is queued up since only operators can submit transactions to the rollup contract.

If the pending deposit queue starts filling up, the ZK-rollup operator will take the deposit transactions and submit them to the rollup contract. Once the user's funds are in the rollup, they can start transacting by sending transactions to the operator for processing. Users can verify balances on the rollup by hashing their account data, sending the hash to the rollup contract, and providing a Merkle proof to verify against the current state root.

Withdrawing from a ZK-rollup to L1 is straightforward. The user initiates the exit transaction by sending their assets on the rollup to a specified account for burning. If the operator includes the transaction in the next batch, the user can submit a withdrawal request to the on-chain contract. This withdrawal request will include the following:

- Merkle proof proving the inclusion of the user's transaction to the burn account in a transaction batch
- Transaction data
- Batch root
- L1 address to receive deposited funds

The rollup contract hashes the transaction data, checks if the batch root exists, and uses the Merkle proof to check if the transaction hash is part of the batch root. Afterward, the contract executes the exit transaction and sends funds to the user's chosen address on L1.

**ZK-Rollups and EVM compatibility**

Unlike optimistic rollups, ZK-rollups are not readily compatible with the [Ethereum Virtual Machine (EVM)](https://ethereum.org/en/developers/docs/evm/). Proving general-purpose EVM computation in circuits is more difficult and resource-intensive than proving simple computations (like the token transfer described previously).

However, [advances in zero-knowledge technology(opens in a new tab)](https://hackmd.io/@yezhang/S1_KMMbGt#Why-possible-now) are igniting renewed interest in wrapping EVM computation in zero-knowledge proofs. These efforts are geared towards creating a zero-knowledge EVM (zkEVM) implementation that can efficiently verify the correctness of program execution. A zkEVM recreates existing EVM opcodes for proving/verification in circuits, allowing to execute smart contracts.

Like the EVM, a zkEVM transitions between states after computation is performed on some inputs. The difference is that the zkEVM also creates zero-knowledge proofs to verify the correctness of every step in the program’s execution. Validity proofs could verify the correctness of operations that touch the VM’s state (memory, stack, storage) and the computation itself (i.e., did the operation call the right opcodes and execute them correctly?).

The introduction of EVM-compatible ZK-rollups is expected to help developers leverage the scalability and security guarantees of zero-knowledge proofs. More importantly, compatibility with native Ethereum infrastructure means developers can build ZK-friendly dapps using familiar (and battle-tested) tooling and languages.

**How do ZK-Rolllup fees work?**

How much users pay for transactions on ZK-rollups is dependent on the gas fee, just like on Ethereum Mainnet. However, gas fees work differently on L2 and are influenced by the following costs:

1. **State write**: There is a fixed cost for writing to Ethereum’s state (i.e., submitting a transaction on the Ethereum blockchain). ZK-rollups reduce this cost by batching transactions and spreading fixed costs across multiple users.
2. **Data publication**: ZK-rollups publish state data for every transaction to Ethereum as `calldata`. `calldata` costs are currently governed by [EIP-1559(opens in a new tab)](https://eips.ethereum.org/EIPS/eip-1559), which stipulates a cost of 16 gas for non-zero bytes and 4 gas for zero bytes of `calldata`, respectively. The cost paid on each transaction is influenced by how much `calldata` needs to be posted on-chain for it.
3. **L2 operator fees**: This is the amount paid to the rollup operator as compensation for computational costs incurred in processing transactions, much like miner fees on Ethereum.
4. **Proof generation and verification**: ZK-rollup operators must produce validity proofs for transaction batches, which is resource-intensive. Verifying zero-knowledge proofs on Mainnet also costs gas (~ 500,000 gas).

Apart from batching transactions, ZK-rollups reduce fees for users by compressing transaction data. You can [see a real-time overview(opens in a new tab)](https://l2fees.info/) of how it costs to use Ethereum ZK-rollups.

### How do ZK-Rollups scale ethereum?

**Transaction data compression**

ZK-rollups extend the throughput on Ethereum’s base layer by taking computation off-chain, but the real boost for scaling comes from compressing transaction data. Ethereum’s [block size](https://ethereum.org/en/developers/docs/blocks/#block-size)limits the data each block can hold and, by extension, the number of transactions processed per block. By compressing transaction-related data, ZK-rollups significantly increase the number of transactions processed per block

ZK-rollups can compress transaction data better than optimistic rollups since they don't have to post all the data required to validate each transaction. They only have to post the minimal data required to rebuild the latest state of accounts and balances on the rollup.

**Recursive proofs**

An advantage of zero-knowledge proofs is that proofs can verify other proofs. For example, a single ZK-SNARK can verify other ZK-SNARKs. Such "proof-of-proofs" are called recursive proofs and dramatically increase throughput on ZK-rollups.

Currently, validity proofs are generated on a block-by-block basis and submitted to the L1 contract for verification. However, verifying single block proofs limits the throughput that ZK-rollups can achieve since only one block can be finalized when the operator submits a proof.

Recursive proofs, however, make it possible to finalize several blocks with one validity proof. This is because the proving circuit recursively aggregates multiple block proofs until one final proof is created. The L2 operator submits this recursive proof, and if the contract accepts it, all the relevant blocks will be finalized instantly. With recursive proofs, the number of ZK-rollup transactions that can be finalized on Ethereum at intervals increases.

**Pros and cons of ZK-rollups**

**Pros**

- Validity proofs ensure correctness of off-chain transactions and prevent operators from executing invalid state transitions.
- Offers faster transaction finality as state updates are approved once validity proofs are verified on L1.
- Relies on trustless cryptographic mechanisms for security, not the honesty of incentivized actors as with[optimistic rollups](https://ethereum.org/en/developers/docs/scaling/optimistic-rollups/#optimistic-pros-and-cons)
- Stores data needed to recover the off-chain state on L1, which guarantees security, censorship-resistance, and decentralization.
- Users benefit from greater capital efficiency and can withdraw funds from L2 without delays.
- Doesn't depend on liveness assumptions and users don't have to validate the chain to protect their funds.
- Better data compression can help reduce the costs of publishing `calldata` on Ethereum and minimize rollup fees for users.

**Cons**

- The cost associated with computing and verifying validity proofs is substantial and can increase fees for rollup users.
- Building EVM-compatible ZK-rollups is difficult due to complexity of zero-knowledge technology.
- Producing validity proofs requires specialized hardware, which may encourage centralized control of the chain by a few parties.
- Centralized operators (sequencers) can influence the ordering of transactions.
- Hardware requirements may reduce the number of participants that can force the chain to make progress, increasing the risk of malicious operators freezing the rollup's state and censoring users.
- Some proving systems (e.g., ZK-SNARK) require a trusted setup which, if mishandled, could potentially compromise a ZK-rollup's security model.

**Further readings on zk-rollups** 

- [What Are Zero-Knowledge Rollups?(opens in a new tab)](https://coinmarketcap.com/alexandria/glossary/zero-knowledge-rollups)
- [What are zero-knowledge rollups?(opens in a new tab)](https://alchemy.com/blog/zero-knowledge-rollups)
- [STARKs vs SNARKs(opens in a new tab)](https://consensys.net/blog/blockchain-explained/zero-knowledge-proofs-starks-vs-snarks/)
- [What is a zkEVM?(opens in a new tab)](https://www.alchemy.com/overviews/zkevm)
- [Intro to zkEVM(opens in a new tab)](https://hackmd.io/@yezhang/S1_KMMbGt)
- [Awesome-zkEVM resources(opens in a new tab)](https://github.com/LuozhuZhang/awesome-zkevm)
- [ZK-SNARKS under the hood(opens in a new tab)](https://vitalik.ca/general/2017/02/01/zk_snarks.html)
- [How are SNARKs possible?(opens in a new tab)](https://vitalik.ca/general/2021/01/26/snarks.html)

[https://www.youtube.com/watch?v=7pWxCklcNsU&source_ve_path=Mjg2NjY&feature=emb_logo](https://www.youtube.com/watch?v=7pWxCklcNsU&source_ve_path=Mjg2NjY&feature=emb_logo)

Visit the following resources to learn more:

• **[Zero-Knowledge Rollups - Ethereum](https://ethereum.org/en/developers/docs/scaling/zk-rollups)**
• **[Why and How zk-SNARK Works](https://medium.com/@imolfar/why-and-how-zk-snark-works-1-introduction-the-medium-of-a-proof-d946e931160)**
• **[Introduction to zk-SNARKs](https://vitalik.ca/general/2021/01/26/snarks.html)**

---

### Validium

Validiums are scaling solutions that use off-chain data availability and computation designed to improve throughput by processing transactions off the Ethereum Mainnet. Like zero-knowledge rollups (ZK-rollups), validiums publish zero-knowledge proofs to verify off-chain transactions on Ethereum. This prevents invalid state transitions and enhances the security guarantees of a validium chain.

Visit the following resources to learn more:

- **[Validium - Ethereum](https://ethereum.org/en/developers/docs/scaling/validium/)**

---

### Plasma

A Plasma chain is a separate blockchain anchored to Ethereum Mainnet but executing transactions off-chain with its own mechanism for block validation. Plasma chains are sometimes referred to as “child” chains, essentially smaller copies of the Ethereum Mainnet Plasma chains use fraud proofs (like [optimistic rollups](https://ethereum.org/en/developers/docs/scaling/optimistic-rollups/)) to arbitrate disputes.

Merkle trees enable the creation of an endless stack of these chains that can work to offload bandwidth from parent chains (including Ethereum Mainnet). However, while these chains derive some security from Ethereum (Via fraud proofs), their security and efficiency are affected by several design limitations.

Visit the following resources to learn more:

- **[Plasma Chains - Ethereum](https://ethereum.org/en/developers/docs/scaling/plasma/)**

---

### Sidechains

A sidechain is a separate blockchain that runs independent of Ethereum and is connected to Ethereum Mainnet by a two-way bridge. Sidechains can have separate block parameters and [consensus algorithms](https://ethereum.org/en/developers/docs/consensus-mechanisms/), which are often designed for efficient processing of transactions. Using a sidechain involves trade-offs, though, as they do not inherit Ethereum's security properties. Unlike [layer 2 scaling solutions](https://ethereum.org/en/layer-2/), sidechains do not post state changes and transaction data back to Ethereum Mainnet.

Sidechains also sacrifice some measure of decentralization or security to achieve high throughput ([scalability trilemma(opens in a new tab)](https://vitalik.ca/general/2021/05/23/scaling.html)). Ethereum is, however, committed to scaling without compromising on decentralization and security as outlined in its [vision statement](https://ethereum.org/en/roadmap/vision/) for upgrades.

visit the following resources to learn more:

- **[Sidechains - Ethereum](https://ethereum.org/en/developers/docs/scaling/sidechains/)**
- **[An Introduction to Sidechains](https://www.coindesk.com/learn/an-introduction-to-sidechains)**

---

### Ethereum 2.0 ( the merge)

Ethereum 2.0 marks a long-anticipated upgrade to the Ethereum public mainnet. Designed to accelerate Ethereum’s usage and adoption by improving its performance, Ethereum 2.0 implements Proof of Stake.

Visit the following resources to learn more:

- **[What Is Ethereum 2.0?](https://consensys.net/blog/blockchain-explained/what-is-ethereum-2/)**
- **[What Is Ethereum 2.0? Understanding The Merge](https://www.forbes.com/advisor/investing/cryptocurrency/ethereum-2/)**

---

### On-chain scaling

On-chain scaling refers to any direct modification made to a blockchain, like data sharding and execution sharding in the incoming version of Ethereum 2.0. Another type of on-chain scaling would be a sidechain with two-way bridge to Ethereum, like Polygon.

As the number of people using Ethereum has grown, the blockchain has reached certain capacity limitations. This has driven up the cost of using the network, creating the need for "scaling solutions." There are multiple solutions being researched, tested and implemented that take different approaches to achieve similar goals.

The main goal of scalability is to increase transaction speed (faster finality), and transaction throughput (high transactions per second), without sacrificing decentralization or security (more on the [Ethereum vision](https://ethereum.org/en/roadmap/vision/)). On the layer 1 Ethereum blockchain, high demand leads to slower transactions and nonviable [gas prices](https://ethereum.org/en/developers/docs/gas/). Increasing the network capacity in terms of speed and throughput is fundamental to the meaningful and mass adoption of Ethereum.

While speed and throughput are important, it is essential that scaling solutions enabling these goals remain decentralized and secure. Keeping the barrier to entry low for node operators is critical in preventing a progression towards centralized and insecure computing power.

Conceptually we first categorize scaling as either on-chain scaling or off-chain scaling.

Visit the following resources to learn more:

- **[Scaling - Ethereum](https://ethereum.org/en/developers/docs/scaling/)**