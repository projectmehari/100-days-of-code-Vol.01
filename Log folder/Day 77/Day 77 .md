# Day 77

Tags: Blockchain, Solidity
Date: September 29, 2023
Status: Done

Tasks of the day

- Programming Languages
    - Solidity
    - Vyper
    - Rust
- Testing
    - Unit Tests
    - Integration tests
    - Code Coverage
- Smart contracts
    - Deployment
    - Monitoring
    - Upgrades

[How to build a random number generator for the blockchain](https://blog.logrocket.com/build-random-number-generator-blockchain/)

---

### Programming Languages ****

Smart contracts can be programmed using relatively developer-friendly languages. If you’re experienced with Python or any curly-bracket language, you can find a language with familiar syntax.

**Solidity**

Solidity is an object-oriented programming language created specifically by Ethereum Network team for constructing smart contracts on various blockchain platforms, most notably, Ethereum.

- It’s used to create smart contracts that implements business logic and generate a chain of transaction records in the blockchain system.
- It acts as a tool for creating machine-level code and compiling it on the Ethereum Virtual Machine (EVM).

Like any other programming languages, Solidity also has variables, functions, classes, arithmetic operations string manipulation, and many more.

[https://www.youtube.com/watch?v=ipwxYa-F1uY](https://www.youtube.com/watch?v=ipwxYa-F1uY)

**Vyper**

Vyper is a contract-oriented, pythonic programming language that targets the Ethereum Virtual Machine (EVM).

[Learn Vyper in Y Minutes](https://learnxinyminutes.com/docs/vyper/)

**Rust**

Rust is a multi-paradigm, general-purpose programming language. Rust emphasizes performance, type safety, and concurrency. It is popular on smart contract chains Solana and Polkadot.

Visit the following resources to learn more:

- **[Rust Programming Language](https://www.rust-lang.org/)**
- **[How to write and deploy a smart contract in Rust](https://learn.figment.io/tutorials/write-and-deploy-a-smart-contract-on-near)**

---

## Testing

Testing smart contracts is one of the most important measures for improving smart contract security. Unlike traditional software, smart contracts cannot typically be updated after launching, making it imperative to test rigorously before deploying contracts onto mainnet.

Public blockchains like Ethereum are immutable, making it difficult to change a smart contracts code after deployment. [Contract upgrade patterns](https://ethereum.org/en/developers/docs/smart-contracts/upgrading/) for performing "virtual upgrades" exist, but these are difficult to implement and require social consensus. Moreover, an upgrade can only fix an error *after* it is discovered—if an attacker discovers the vulnerability first, your smart contract is at risk of an exploit.

**What is smart contract testing?**

Smart contract testing is the process of verifying that the code of a smart contract works as expected. Testing is useful for checking if a particular smart contract satisfies requirements for reliability, usability, and security.

Although approaches vary, most testing methods require executing a smart contract with a small sample of the data it is expected to handle. If the contract produces correct results for sample data, it is assumed to be functioning properly. Most testing tools provide resources for writing and executing [test cases(opens in a new tab)](https://en.m.wikipedia.org/wiki/Test_case) to check if a contracts execution matches the expected results.

### **Why is it important to test smart contracts?**

As smart contracts often manage high-value financial assets, minor programming errors can and often lead to [massive losses for users(opens in a new tab)](https://rekt.news/leaderboard/). Rigorous testing can, however, help you discover defects issues in a smart contracts code early and fix them before launching on Mainnet.

While it is possible to upgrade a contract if a bug is discovered, upgrades are complex and can [result in errors(opens in a new tab)](https://blog.trailofbits.com/2018/09/05/contract-upgrade-anti-patterns/) if handled improperly. Upgrading a contract further negates the principle of immutability and burdens users with additional trust assumptions. Conversely, a comprehensive plan for testing your contract mitigates smart contract security risks and reduces the need to perform complex logic upgrades after deploying.

### **Methods for testing smart contracts**

Methods for testing Ethereum smart contracts exist fall under two broad categories: **automated testing** and **manual testing**. Automated testing and manual testing offer unique benefits and tradeoffs, but you can combine both to create a robust plan for analyzing your contracts.****

**Automated testing**

Automated testing uses tools that automatically check a smart contracts code for errors in execution. The benefit of automated testing comes from using [scripts(opens in a new tab)](https://www.techtarget.com/whatis/definition/script?amp=1) to guide the evaluation of contract functionalities. Scripted tests can be scheduled to run repeatedly with minimal human intervention, making automated testing more efficient than manual approaches to testing.

Automated testing is particularly useful when tests are repetitive and time-consuming; difficult to carry out manually; susceptible to human error; or involve evaluating critical contract functions. But automated testing tools can have drawbacks—they may miss certain bugs and produce many [false positives(opens in a new tab)](https://www.contrastsecurity.com/glossary/false-positive). Hence, pairing automated testing with manual testing for smart contracts is ideal.

**Manual testing**

Manual testing is human-aided and involves executing each test case in your test suite one after the other when analyzing a smart contracts correctness. This is unlike automated testing where you can simultaneously run multiple isolated tests on a contract and get a report showing all failing and passing tests.

Manual testing can be carried out by a single individual following a written test plan that covers different test scenarios. You could also have multiple individuals or groups interact with a smart contract over a specified period as part of manual testing. Testers will compare the actual behavior of the contract against the expected behavior, flagging any difference as a bug.

Effective manual testing requires considerable resources (skill, time, money, and effort), and it is possible—due to human error—to miss certain errors while executing tests. But manual testing can also be beneficial—for example, a human tester (e.g., an auditor) may use intuition to detect edge cases that an automated testing tool would miss.

### **Automated testing for smart contracts**

**Unit testing**

Unit testing evaluates contract functions separately and checks that each component works correctly. Good unit tests should be simple, quick to run and provide a clear idea of what went wrong if tests fail.

Unit tests are useful for checking that functions return expected values and that contract storage is updated properly after function execution. Moreover, running unit tests after making changes to a contracts codebase ensures adding new logic does not introduce errors. Below are some guidelines for running effective unit tests:

Guidelines for unit testing smart contracts

1. **Understand your contracts business logic and workflow**
    
    Before writing unit tests, it helps to know what functionalities a smart contract offers and how users will access and use those functions. This is particularly useful for running [happy path tests(opens in a new tab)](https://en.m.wikipedia.org/wiki/Happy_path) that determine if functions in a contract return the correct output for valid user inputs. We'll explain this concept using this (abridged) example of [an auction contract(opens in a new tab)](https://docs.soliditylang.org/en/v0.8.17/solidity-by-example.html?highlight=Auction%20contract#simple-open-auction)
    

```solidity
constructor(
2	        uint biddingTime,
3	        address payable beneficiaryAddress
4	    ) {
5	        beneficiary = beneficiaryAddress;
6	        auctionEndTime = block.timestamp + biddingTime;
7	    }
8	
9	function bid() external payable {
10	
11	      if (block.timestamp > auctionEndTime)
12	            revert AuctionAlreadyEnded();
13	
14	      if (msg.value <= highestBid)
15	            revert BidNotHighEnough(highestBid);
16	
17	 if (highestBid != 0) {
18	    pendingReturns[highestBidder] += highestBid;
19	        }
20	        highestBidder = msg.sender;
21	        highestBid = msg.value;
22	        emit HighestBidIncreased(msg.sender, msg.value);
23	    }
24	
25	 function withdraw() external returns (bool) {
26	        uint amount = pendingReturns[msg.sender];
27	        if (amount > 0) {
28	           pendingReturns[msg.sender] = 0;
29	
30	        if (!payable(msg.sender).send(amount)) {
31	                pendingReturns[msg.sender] = amount;
32	                return false;
33	            }
34	        }
35	        return true;
36	    }
37	
38	function auctionEnd() external {
39	       if (block.timestamp < auctionEndTime)
40	            revert AuctionNotYetEnded();
41	        if (ended)
42	            revert AuctionEndAlreadyCalled();
43	
44	        ended = true;
45	        emit AuctionEnded(highestBidder, highestBid);
46	
47	        beneficiary.transfer(highestBid);
48	    }
49	}
```

This is a simple auction contract designed to receive bids during the bidding period. If the `highestBid` increases, the previous highest bidder receives their money; once the bidding period is over, the `beneficiary` calls the contract to get their money.

Unit tests for a contract like this would cover different functions a user might call when interacting with the contract. An example would be unit a test that checks if a user can place a bid while the auction is ongoing (i.e., calls to `bid()` succeed) or one that checks if a user can place a higher bid than the current `highestBid`.

Understanding a contracts operational workflow also helps with writing unit tests that check if execution meet requirements. For example, the auction contract specifies that users cannot place bids when the auction has ended (i.e., when `auctionEndTime` is lower than `block.timestamp`). Thus, a developer might run a unit test that checks if calls to the `bid()` function succeed or fail when the auction is over (i.e., when `auctionEndTime` > `block.timestamp`).

1. **Evaluate all assumptions related to contract execution**

It is important to document any assumptions about a contract’s execution and write unit tests to verify the validity of those assumptions. Apart from offering protection against unexpected execution, testing assertions forces you to think about operations that could break a smart contracts security model. A useful tip is to go beyond "happy user tests" and write negative tests that check if a function fails for the wrong inputs.

Many unit testing frameworks allow you to create assertions—simple statements that state what a contract can and cannot do—and run tests to see if those assertions hold under execution. A developer working on the auction contract described earlier could make the following assertions about its behavior before running negative tests:

- Users cannot place bids when the auction is over or hasn't begun.
- The auction contract reverts if a bid is below the acceptable threshold.
- Users who fail to win the bid are credited with their funds

1. **Measure code coverage**

[Code coverage(opens in a new tab)](https://en.m.wikipedia.org/wiki/Code_coverage) is a testing metric that tracks the number of branches, lines, and statements in your code executed during tests. Tests should have good code coverage, otherwise you may get "false negatives" which happen a contract passes all tests, but vulnerabilities still exist in the code. Recording high code coverage, however, gives the assurance all statements/functions in a smart contract were sufficiently tested for correctness

1. **Use well-developed testing frameworks**
    
    The quality of the tools used in running unit tests for your smart contracts is crucial. An ideal testing framework is one that's regularly maintained; provides useful features (e.g., logging and reporting capabilities); and must have been extensively used and vetted by other developers.
    
    Unit testing frameworks for Solidity smart contracts come in different languages (mostly JavaScript, Python, and Rust). See some of the guides below for information on how to start running unit tests with different testing frameworks:
    
    - **[Running unit tests with Truffle(opens in a new tab)](https://trufflesuite.com/docs/truffle/testing/testing-your-contracts/)**
    - **[Running unit tests with Brownie(opens in a new tab)](https://eth-brownie.readthedocs.io/en/v1.0.0_a/tests.html)**
    - **[Running unit tests with Foundry(opens in a new tab)](https://book.getfoundry.sh/forge/writing-tests)**
    - **[Running unit tests with Waffle(opens in a new tab)](https://ethereum-waffle.readthedocs.io/en/latest/getting-started.html#writing-tests)**
    - **[Running unit tests with Remix(opens in a new tab)](https://remix-ide.readthedocs.io/en/latest/unittesting.html#write-tests)**
    - **[Running unit tests with Ape(opens in a new tab)](https://docs.apeworx.io/ape/stable/userguides/testing.html)**
    - **[Running unit tests with Hardhat(opens in a new tab)](https://hardhat.org/hardhat-runner/docs/guides/test-contracts)**

**Integration testing**

While unit testing debugs contract functions in isolation, integration tests evaluate the components of a smart contract as a whole. Integration testing can detect issues arising from cross-contract calls or interactions between different functions in the same smart contract. For example, integration tests can help check if things like [inheritance(opens in a new tab)](https://docs.soliditylang.org/en/v0.8.12/contracts.html#inheritance) and dependency injection work properly.

Integration testing is useful if your contract adopts a modular architecture or interfaces with other on-chain contracts during execution. One way of running integration tests is to fork the blockchain at a specific height (using a tool like [Ganache(opens in a new tab)](https://trufflesuite.com/docs/ganache/) or [Hardhat(opens in a new tab)](https://hardhat.org/hardhat-network/docs/guides/forking-other-networks)) and simulate interactions between your contract and deployed contracts.

The forked blockchain will behave similarly to Mainnet and have accounts with associated states and balances. But it only acts as a sandboxed local development environment, meaning you won't need real ETH for transactions, for example, nor will your changes affect the real Ethereum protocol.

**Property-based testing**

Property-based testing is the process of checking that a smart contract satisfies some defined property. Properties assert facts about a contract’s behavior that are expected to remain true in different scenarios—an example of a smart contract property could be "Arithmetic operations in the contract never overflow or underflow.”

**Static analysis** and **dynamic analysis** are two common techniques for executing property-based testing, and both can verify that the code for a program (a smart contract in this case) satisfies some predefined property. Some property-based testing tools come with predefined rules about expected contract properties and check the code against those rules, while others allow you to create custom properties for a smart contract.

**Static analysis**

A static analyzer takes as input the source code of a smart contract and outputs results declaring whether a contract satisfies a property or not. Unlike dynamic analysis, static analysis doesn't involve executing a contract to analyze it for correctness. Static analysis instead reasons about all the possible paths that a smart contract could take during execution (i.e., by examining the structure of the source code to determine what it would mean for the contracts operation at runtime).

[Linting(opens in a new tab)](https://www.perforce.com/blog/qac/what-lint-code-and-why-linting-important) and [static testing(opens in a new tab)](https://www.techtarget.com/whatis/definition/static-analysis-static-code-analysis) are common methods for running static analysis on contracts. Both require analyzing low-level representations of a contracts execution such as [abstract syntax trees(opens in a new tab)](https://en.m.wikipedia.org/wiki/Abstract_syntax_tree) and [control flow graphs(opens in a new tab)](https://www.geeksforgeeks.org/software-engineering-control-flow-graph-cfg/amp/) output by the compiler.

In most cases, static analysis is useful for detecting safety issues like use of unsafe constructs, syntax errors, or violations of coding standards in a contracts code. However, static analyzers are known to be generally unsound at detecting deeper vulnerabilities, and may produce excessive false positives.

**Dynamic analysis**

Dynamic analysis generates symbolic inputs (e.g., in [symbolic execution(opens in a new tab)](https://en.m.wikipedia.org/wiki/Symbolic_execution)) or concrete inputs (e.g., in [fuzzing(opens in a new tab)](https://owasp.org/www-community/Fuzzing)) to a smart contracts functions to see if any execution trace(s) violates specific properties. This form of property-based testing differs from unit tests in that test cases cover multiple scenarios and a program handles the generation of test cases.

[Fuzzing(opens in a new tab)](https://halborn.com/what-is-fuzz-testing-fuzzing/) is an example of a dynamic analysis technique for verifying arbitrary properties in smart contracts. A fuzzer invokes functions in a target contract with random or malformed variations of a defined input value. If the smart contract enters an error state (e.g., one where an assertion fails), the problem is flagged and inputs that drive execution toward the vulnerable path are produced in a report.

Fuzzing is useful for evaluating a smart contracts input validation mechanism since improper handling of unexpected inputs might result in unintended execution and produce dangerous effects. This form of property-based testing can be ideal for many reasons:

1. **Writing test cases to cover many scenarios is difficult.** A property test only requires that you define a behavior and a range of data to test the behavior with—the program automatically generates test cases based on the defined property.
2. **Your test suite may not sufficiently cover all possible paths within the program.**Even with 100% coverage, it is possible to miss out on edge cases.
3. **Unit tests prove a contract executes correctly for sample data, but whether the contract executes correctly for inputs outside the sample remains unknown.**Property tests execute a target contract with multiple variations of a given input value to find execution traces that cause assertion failures. Thus, a property test provides more guarantees that a contract executes correctly for a broad class of input data.

**Guidelines for running property-based testing for smart contracts**

Running property-based testing typically starts with defining a property (e.g., absence of [integer overflows(opens in a new tab)](https://github.com/ConsenSys/mythril/wiki/Integer-Overflow)) or collection of properties that you want to verify in a smart contract. You may also need to define a range of values within which the program can generate data for transaction inputs when writing property tests.

Once configured properly, the property testing tool will execute your smart contracts functions with randomly generated inputs. If there are any assertion violations, you should get a report with concrete input data that violates the property under evaluation. See some of the guides below to get started with running property-based testing with different tools:

- **[Static analysis of smart contracts with Slither(opens in a new tab)](https://github.com/crytic/building-secure-contracts/tree/master/program-analysis/slither#slither)**
- **[Property-based testing with Brownie(opens in a new tab)](https://eth-brownie.readthedocs.io/en/stable/tests-hypothesis-property.html)**
- **[Fuzzing contracts with Foundry(opens in a new tab)](https://book.getfoundry.sh/forge/fuzz-testing)**
- **[Fuzzing contracts with Echidna(opens in a new tab)](https://github.com/crytic/building-secure-contracts/tree/master/program-analysis/echidna#echidna-tutorial)**
- **[Symbolic execution of smart contracts with Manticore(opens in a new tab)](https://github.com/crytic/building-secure-contracts/tree/master/program-analysis/manticore#manticore-tutorial)**
- **[Symbolic execution of smart contracts with Mythril(opens in a new tab)](https://mythril-classic.readthedocs.io/en/master/tutorial.html)**

### Manual Testing for smart contracts

Manual testing of smart contracts often comes later in the development cycle after running automated tests. This form of testing evaluates the smart contract as one fully integrated product to see if it performs as specified in the technical requirements.****

**Testing contracts on a local blockchain**

While automated testing performed in a local development environment can provide useful debugging information, you'll want to know how your smart contract behaves in a production environment. However, deploying to the main Ethereum chain incurs gas fees—not to mention that you or your users can lose real money if your smart contract still has bugs.

Testing your contract on a local blockchain (also known as a [development network](https://ethereum.org/en/developers/docs/development-networks/)) is a recommended alternative to testing on Mainnet. A local blockchain is a copy of the Ethereum blockchain running locally on your computer which simulates the behavior of Ethereum's execution layer. As such, you can program transactions to interact with a contract without incurring significant overhead.

Running contracts on a local blockchain could be useful as a form of manual integration testing. [Smart contracts are highly composable](https://ethereum.org/en/developers/docs/smart-contracts/composability/), allowing you to integrate with existing protocols—but you'll still need to ensure that such complex on-chain interactions produce the correct results.

**Testing contracts on testnets**

A test network or testnet works exactly like Ethereum Mainnet, except that it uses Ether (ETH) with no real-world value. Deploying your contract on a [testnet](https://ethereum.org/en/developers/docs/networks/#ethereum-testnets) means anyone can interact with it (e.g., via the dapp's frontend) without putting funds at risk.

This form of manual testing is useful for evaluating the end-to-end flow of your application from a user’s point of view. Here, beta testers can also perform trial runs and report any issues with the contract’s business logic and overall functionality.

Deploying on a testnet after testing on a local blockchain is ideal since the former is closer to the behavior of the Ethereum Virtual Machine. Therefore, it is common for many Ethereum-native projects to deploy dapps on testnets to evaluate a smart contracts operation under real-world conditions.

### Testing vs Formal verification

While testing helps confirm that a contract returns the expected results for some data inputs, it cannot conclusively prove the same for inputs not used during tests. Testing a smart contract, therefore, cannot guarantee "functional correctness" (i.e., it cannot show that a program behaves as required for *all* sets of input values).

Formal verification is an approach to assessing the correctness of software by checking whether a formal model of the program matches the formal specification. A formal model is an abstract mathematical representation of a program, while a formal specification defines a program's properties (i.e., logical assertions about the program's execution).

Because properties are written in mathematical terms, it becomes possible to verify that a formal (mathematical) model of the system satisfies a specification using logical rules of inference. Thus, formal verification tools are said to produce ‘mathematical proof’ of a system’s correctness.

Unlike testing, formal verification can be used to verify a smart contracts execution satisfies a formal specification for *all* executions (i.e., it has no bugs) without needing to execute it with sample data. Not only does this reduce time spent on running dozens of unit tests, but it is also more effective at catching hidden vulnerabilities. That said, formal verification techniques lie on a spectrum depending on their difficulty of implementation and usefulness.

### Testing vs audits and bug bounties

As mentioned, rigorous testing can rarely guarantee the absence of bugs in a contract; formal verification approaches can provide stronger assurances of correctness but are currently difficult to use and incur considerable costs.

Still, you can further increase the possibility of catching contract vulnerabilities by getting an independent code review. [Smart contract audits(opens in a new tab)](https://www.immunebytes.com/blog/what-is-a-smart-contract-audit/) and [bug bounties(opens in a new tab)](https://medium.com/immunefi/a-defi-security-standard-the-scaling-bug-bounty-9b83dfdc1ba7)are two ways of getting others to analyze your contracts.

Audits are performed by auditors experienced at finding cases of security flaws and poor development practices in smart contracts. An audit will usually include testing (and possibly formal verification) as well as a manual review of the entire codebase.

Conversely, a bug bounty program usually involves involves offering a financial reward to an individual (commonly described as [whitehat hackers(opens in a new tab)](https://en.wikipedia.org/wiki/White_hat_(computer_security))) that discovers a vulnerability in a smart contract and discloses it to developers. Bug bounties are similar to audits since it involves asking others to help find defects in smart contracts.

The major difference is that bug bounty programs are open to the wider developer/hacker community and attract a broad class of ethical hackers and independent security professionals with unique skills and experience. This may be an advantage over smart contract audits that mainly rely on teams who may possess limited or narrow expertise.

Visit the following resources to learn more:

- **[How to Test Ethereum Smart Contracts](https://betterprogramming.pub/how-to-test-ethereum-smart-contracts-35abc8fa199d)**
- **[Writing automated smart contract tests](https://docs.openzeppelin.com/learn/writing-automated-tests)**

---

### Deployment

Unlike other software, smart contracts don’t run on a local computer or a remote server: they live on the blockchain. Thus, interacting with them is different from more traditional applications.

**Deploying smart contracts**

What you’ll need

- your contract's bytecode – this is generated through [compilation](https://ethereum.org/en/developers/docs/smart-contracts/compiling/)
- ETH for gas – you'll set your gas limit like other transactions so be aware that contract deployment needs a lot more gas than a simple ETH transfer
- a deployment script or plugin
- access to an [Ethereum node](https://ethereum.org/en/developers/docs/nodes-and-clients/), either by running your own, connecting to a public node, or via an API key using a [node service](https://ethereum.org/en/developers/docs/nodes-and-clients/nodes-as-a-service/)

Once deployed, your contract will have an Ethereum address like other [accounts](https://ethereum.org/en/developers/docs/accounts/).****

## RELATED TOOLS

**Remix - *Remix IDE allows developing, deploying and administering smart contracts for Ethereum like blockchains***

- [Remix(opens in a new tab)](https://remix.ethereum.org/)

**Tenderly - *Web3 development platform that provides debugging, observability, and infrastructure building blocks for developing, testing, monitoring, and operating smart contracts***

- [tenderly.co(opens in a new tab)](https://tenderly.co/)
- [Docs(opens in a new tab)](https://docs.tenderly.co/)
- [GitHub(opens in a new tab)](https://github.com/Tenderly)
- [Discord(opens in a new tab)](https://discord.gg/eCWjuvt)

**Hardhat - *A development environment to compile, deploy, test, and debug your Ethereum software***

- [hardhat.org(opens in a new tab)](https://hardhat.org/getting-started/)
- [Docs on deploying your contracts(opens in a new tab)](https://hardhat.org/guides/deploying.html)
- [GitHub(opens in a new tab)](https://github.com/nomiclabs/hardhat)
- [Discord(opens in a new tab)](https://discord.com/invite/TETZs2KK4k)

**Truffle -** ***A development environment, testing framework, build pipeline, and other tools.***

- [trufflesuite.com(opens in a new tab)](https://www.trufflesuite.com/)
- [Docs on networks and app deployment(opens in a new tab)](https://www.trufflesuite.com/docs/truffle/advanced/networks-and-app-deployment)
- [GitHub(opens in a new tab)](https://github.com/trufflesuite/truffle)

**thirdweb - *Easily deploy any contract to any EVM compatible chain, using a single command***

- [Documentation(opens in a new tab)](https://portal.thirdweb.com/deploy/)

---

### Monitoring

Monitoring smart contracts allow their authors to view its activity and interactions based on generated transactions and events, allowing verification of the contract’s intended purpose and functionality.

Visit the following resources to learn more:

- **[Monitoring Smart Contracts](https://consensys.github.io/smart-contract-best-practices/development-recommendations/solidity-specific/event-monitoring/)**

---

### Upgrades

Smart contracts are immutable by default. Once they are created there is no way to alter them, effectively acting as an unbreakable contract among participants. However, for some scenarios, it is desirable to be able to modify them.

**Upgrading smart contracts**

Smart contracts on Ethereum are self-executing programs that run in the Ethereum Virtual Machine (EVM). These programs are immutable by design, which prevents any updates to the business logic once the contract is deployed.

While immutability is necessary for trustlessness, decentralization, and security of smart contracts, it may be a drawback in certain cases. For instance, immutable code can make it impossible for developers to fix vulnerable contracts.

However, increased research into improving smart contracts has led to the introduction of several upgrade patterns. These upgrade patterns enable developers to upgrade smart contracts (while preserving immutability) by placing business logic in different contracts.

**What is a smart contract upgrade**

A smart contract upgrade involves changing the business logic of a smart contract while preserving the contract’s state. It is important to clarify that upgradeability and mutability are not the same, especially in the context of smart contracts.

You still cannot change a program deployed to an address on the Ethereum network. But you can change the code that’s executed when users interact with a smart contract.

This can be done via the following methods:

1. Creating multiple versions of a smart contract and migrating state (i.e data) from the old contract to a new instance of the contract.
2. Creating separate contracts to store business logic and state.
3. Using proxy patterns to delegate function calls from an immutable proxy contract to a modifiable logic contract.
4. Creating an immutable main contract that interfaces with and relies on flexible satelite contracts to execute specific functions.
5. Using the diamond pattern to delegate function calls from a proxy contract to logic contracts.

```solidity
      [Old Contract]              [Separate Contracts]          [Immutable Proxy]
     +--------------+           +----------------------+     +----------------------+
     |              |           |                      |     |                      |
     |     (1)      |           |         (2)          |     |         (3)          |
     |              |           |                      |     |                      |
     +--------------+           +----------------------+     +----------------------+
             |                             |                            |
             |                             |                            |
             v                             v                            v
        Migrate Data                Business Logic                 Function Calls
           (1)                         (2)                            (3)
             |                             |                            |
             |                             |                            |
             v                             v                            v
       [New Contract]                [Business Logic]             [Logic Contract]
```

**Upgrading mechanism #1: Contract migration**

Contract migration is based on versioning—the idea of creating and managing unique states of the same software. Contract migration involves deploying a new instance of an existing smart contract and transferring storage and balances to the new contract.

The newly deployed contract will have an empty storage, allowing you to recover data from the old contract and write it to the new implementation. Afterward, you will need to update all contracts that interacted with the old contract to reflect the new address.

The last step in contract migration is to convince users to switch to using the new contract. The new contract version will retain user balances and addresses, which preserves immutability. If it's a token-based contract, you will also need to contact exchanges to discard the old contract and use the new contract.

Contract migration is a relatively straightforward and safe measure for upgrading smart contracts without breaking user interactions. However, manually migrating user storage and balances to the new contract is time-intensive and can incur high gas costs.

[More on contract migration.(opens in a new tab)](https://blog.trailofbits.com/2018/10/29/how-contract-migration-works/)

**Upgrade mechanism #2: Data separation**

Another method for upgrading smart contracts is to separate business logic and data storage into separate contracts. This means users interact with the logic contract, while data is stored in the storage contract.

The logic contract contains the code executed when users interact with the application. It also holds the storage contract's address and interacts with it to get and set data.

Meanwhile, the storage contract holds the state associated with the smart contract, such as user balances and addresses. Note that the storage contract is owned by the logic contract and is configured with the latter's address at deployment. This prevents unauthorized contracts from calling the storage contract or updating its data.

By default, the storage contract is immutable—but you can replace the logic contract it points to with a new implementation. This will change the code that runs in the EVM, while keeping storage and balances intact.

Using this upgrade method requires updating the logic contract's address in the storage contract. You must also configure the new logic contract with the storage contract's address for reasons explained earlier.

The data separation pattern is arguably easier to implement compared to contract migration. However, you'll have to manage multiple contracts and implement complex authorization schemes to protect smart contracts from malicious upgrades.

**Upgrade mechanism #3: Proxy patterns**

The proxy pattern also uses data separation to keep business logic and data in separate contracts. However, in a proxy pattern, the storage contract (called a proxy) calls the logic contract during code execution. This is a reverse of the data separation method, where the logic contract calls the storage contract.

This is what happens in a proxy pattern:

1. Users interact with the proxy contract, which stores data, but doesn't hold the business logic.
2. The proxy contract stores the address of the logic contract and delegates all function calls to the logic contract (which holds the business logic) using the `delegatecall` function.
3. After the call is forwarded to the logic contract, the returned data from the logic contract is retrieved and returned to the user.

Using the proxy patterns requires an understanding of the **delegatecall** function. Basically, `delegatecall` is an opcode that allows a contract to call another contract, while the actual code execution happens in the context of the calling contract. An implication of using `delegatecall` in proxy patterns is that the proxy contract reads and writes to its storage and executes logic stored at the logic contract as if calling an internal function.

From the [Solidity documentation(opens in a new tab)](https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html#delegatecall-callcode-and-libraries):

> There exists a special variant of a message call, named delegatecall which is identical to a message call apart from the fact that the code at the target address is executed in the context (i.e. at the address) of the calling contract and msg.senderand msg.value do not change their values. This means that a contract can dynamically load code from a different address at runtime. Storage, current address and balance still refer to the calling contract, only the code is taken from the called address.
> 

The proxy contract knows to invoke `delegatecall` whenever a user calls a function because it has a `fallback` function built into it. In Solidity programming the [fallback function(opens in a new tab)](https://docs.soliditylang.org/en/latest/contracts.html#fallback-function) is executed when a function call does not match functions specified in a contract.

Making the proxy pattern work requires writing a custom fallback function that specifies how the proxy contract should handle function calls it does not support. In this case the proxy's fallback function is programmed to initiate a delegatecall and reroute the user's request to the current logic contract implementation.

The proxy contract is immutable by default, but new logic contracts with updated business logic can be created. Performing the upgrade is then a matter of changing the address of the logic contract referenced in the proxy contract.

By pointing the proxy contract to a new logic contract, the code executed when users call the proxy contract function changes. This allows us to upgrade a contract's logic without asking users to interact with a new contract.

Proxy patterns are a popular method for upgrading smart contracts because they eliminate the difficulties associated with contract migration. However, proxy patterns are more complicated to use and can introduce critical flaws, such as [function selector clashes(opens in a new tab)](https://medium.com/nomic-foundation-blog/malicious-backdoors-in-ethereum-proxies-62629adf3357), if used improperly.

**Upgrade mechanism #4: Strategy pattern**

This technique is influenced by the [strategy pattern(opens in a new tab)](https://en.wikipedia.org/wiki/Strategy_pattern), which encourages creating software programs that interface with other programs to implement specific features. Applying the strategy pattern to Ethereum development would mean building a smart contract that calls functions from other contracts.

The main contract in this case contains the core business logic, but interfaces with other smart contracts ("satellite contracts") to execute certain functions. This main contract also stores the address for each satellite contract and can switch between different implementations of the satellite contract.

You can build a new satellite contract and configure the main contract with the new address. This allows you to change *strategies* (i.e., implement new logic) for a smart contract.

Although similar to the proxy pattern discussed earlier, the strategy pattern is different because the main contract, which users interact with, holds the business logic. Using this pattern affords you the opportunity to introduce limited changes to a smart contract without affecting the core infrastructure.

The main drawback is that this pattern is mostly useful for rolling out minor upgrades. Also, if the main contract is compromised (e.g., via a hack), you cannot use this upgrade method.

**Upgrade mechanism #5: Diamond pattern**

The diamond pattern can be considered an improvement on the proxy pattern. Diamond patterns differ from proxy patterns because the diamond proxy contract can delegate function calls to more than one logic contract.

The logic contracts in the diamond pattern are known as *facets*. To make the diamond pattern work, you need to create a mapping in the proxy contract that maps [function selectors(opens in a new tab)](https://docs.soliditylang.org/en/latest/abi-spec.html#function-selector) to different facet addresses.

When a user makes a function call, the proxy contract checks the mapping to find the facet responsible for executing that function. Then it invokes `delegatecall` (using the fallback function) and redirects the call to the appropriate logic contract.

The diamond upgrade pattern has some advantages over traditional proxy upgrade patterns:

1. It allows you to upgrade a small part of the contract without changing all of the code. Using the proxy pattern for upgrades requires creating an entirely new logic contract, even for minor upgrades.
2. All smart contracts (including logic contracts used in proxy patterns) have a 24KB size limit, which can be a limitation—especially for complex contracts requiring more functions. The diamond pattern makes it easy to solve this problem by splitting functions across multiple logic contracts.
3. Proxy patterns adopt a catch-all approach to access controls. An entity with access to upgrade functions can change the *entire* contract. But the diamond pattern enables a modular permissions approach, where you can restrict entities to upgrading certain functions within a smart contract.

### Pros and cons of upgrading smart contracts

**Pros**

- A smart contract upgrade can make it easier to fix vulnerabilities discovered in the post-deployment phase
- Developers can use logic upgrades to add new features to decentralized applications
- Smart contract upgrades can improve safety for end-users since bugs can be fixed quickly.
- Contract upgrades give developers more room to experiment with different features and improve dapps over time.

**Cons**

- Upgrading smart contracts negates the idea of code immutability, which has implications for decentralization and security.
- Users must trust developers not to modify smart contracts arbitrarily.
- Programming upgrade functionality into smart contracts adds another layer of complexity and increases the possibility of critical flaws.
- The opportunity to upgrade smart contracts may encourage developers to launch projects faster without doing due diligence during the development phase.
- Insecure access control or centralization in smart contracts can make it easier for malicious actors to perform unauthorized upgrades.

**Considerations for upgrading smart contracts**

1. Use secure access control/authorization mechanisms to prevent unauthorized smart contract upgrades, especially if using proxy patterns, or data separation. An example is restricting access to the upgrade function, such the only contract’s owner can call it.
2. Upgrading smart contracts is a complex activity and requires a high level of diligence to prevent the introduction of vulnerabilities.
3. Reduce **trust assumptions** by decentralizing the process of implementing upgrades. Possible strategies include using a [multi-sig wallet contract](https://ethereum.org/en/developers/docs/smart-contracts/#multisig) to control upgrades, or requiring [members of a DAO](https://ethereum.org/en/dao/) to vote on approving the upgrade.
4. Be aware of the costs involved in upgrading contracts. For instance, copying state (e.g., user balances) from an old contract to a new contract during contract migration may require more than one transaction, meaning more gas fees.
5. Consider implementing **timelocks** to protect users. A timelock refers to a delay enforced on changes to a system. Timelocks can be combined with a multi-sig governance system to control upgrades: if a proposed action reaches the required approval threshold, it doesn't execute until the predefined delay period elapses.

Timelocks give users some time to exit the system if they disagree with a proposed change (e.g., logic upgrade or new fee schemes). Without timelocks, users need to trust developers not to implement arbitrary changes in a smart contract without prior notice. The drawback here is that timelocks restrict the ability to quickly patch vulnerabilities.

[](https://medium.com/coinmonks/ethereum-smart-contract-migration-13f6f12539bd)

Visit the following resources to learn more:

- **[Upgrading smart contracts](https://docs.openzeppelin.com/learn/upgrading-smart-contracts)**
- **[What are Upgradable Smart Contracts? Full Guide](https://moralis.io/what-are-upgradable-smart-contracts-full-guide/)**
- **[Upgrading your Smart Contracts | A Tutorial & Introduction](https://youtu.be/bdXJmWajZRY)**

---