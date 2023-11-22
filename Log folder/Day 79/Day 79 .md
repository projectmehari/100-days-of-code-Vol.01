# Day 79

Tags: Solidity
Date: October 1, 2023
Status: Done

Tasks of the day

- Security
    - [Practices](https://consensys.github.io/smart-contract-best-practices/)
        - Fuzz Testing & Static Analysis
        - Common Threat Vectors
        - Source of Randomness Attacks
    - Tools
        - Slither
        - MythX
        - Manticore
        - Echidna

---

### Security

Smart contracts are extremely flexible, capable of both holding large quantities of tokens (often in excess of $1B) and running immutable logic based on previously deployed smart contract code. While this has created a vibrant and creative ecosystem of trustless, interconnected smart contracts, it is also the perfect ecosystem to attract attackers looking to profit by exploiting vulnerabilities

Smart contracts are extremely flexible, and capable of controlling large amounts of value and data, while running immutable logic based on code deployed on the blockchain. This has created a vibrant ecosystem of trustless and decentralized applications that provide many advantages over legacy systems. They also represent opportunities for attackers looking to profit by exploiting vulnerabilities in smart contracts.

Public blockchains, like Ethereum, further complicate the issue of securing smart contracts. Deployed contract code *usually* cannot be changed to patch security flaws, while assets stolen from smart contracts are extremely difficult to track and mostly irrecoverable due to immutability.

Although figures vary, it is estimated that the total amount of value stolen or lost due to security defects in smart contracts is easily over $1 billion. This includes high-profile incidents, such as the [DAO hack(opens in a new tab)](https://hackingdistributed.com/2016/06/18/analysis-of-the-dao-exploit/) (3.6M ETH stolen, worth over $1B in today’s prices), [Parity multi-sig wallet hack(opens in a new tab)](https://www.coindesk.com/30-million-ether-reported-stolen-parity-wallet-breach) ($30M lost to hackers), and the [Parity frozen wallet issue(opens in a new tab)](https://www.theguardian.com/technology/2017/nov/08/cryptocurrency-300m-dollars-stolen-bug-ether) (over $300M in ETH locked forever).

The aforementioned issues make it imperative for developers to invest effort in building secure, robust, and resilient smart contracts. Smart contract security is serious business, and one that every developer will do well to learn. This guide will cover security considerations for Ethereum developers and explore resources for improving smart contract security.

**Guidelines for building secure ethereum smart contracts**

**Design proper access controls:** 

In smart contracts, functions marked `public` or `external` can be called by any externally owned accounts (EOAs) or contract accounts. Specifying public visibility for functions is necessary if you want others to interact with your contract. Functions marked `private` however can only be called by functions within the smart contract, and not external accounts. Giving every network participant access to contract functions can cause problems, especially if it means anyone can perform sensitive operations (e.g., minting new tokens).

To prevent unauthorized use of smart contract functions, it is necessary to implement secure access controls. Access control mechanisms restrict the ability to use certain functions in a smart contract to approved entities, such as accounts responsible for managing the contract. The **Ownable pattern** and **role-based control** are two patterns useful for implementing access control in smart contracts:

**Ownable pattern**

In the Ownable pattern, an address is set as the “owner” of the contract during the contract-creation process. Protected functions are assigned an `OnlyOwner` modifier, which ensures the contract authenticates the identity of the calling address before executing the function. Calls to protected functions from other addresses aside from the contract owner always revert, preventing unwanted access.

**Role-based access control**

Registering a single address as `Owner` in a smart contract introduces the risk of centralization and represents a single point-of-failure. If the owner’s account keys are compromised, attackers can attack the owned contract. This is why using a role-based access control pattern with multiple administrative accounts may be a better option.

In role-based access control, access to sensitive functions is distributed between a set of trusted participants. For instance, one account may be responsible for minting tokens, while another account performs upgrades or pauses the contract. Decentralizing access control this way eliminates single points of failure and reduces trust assumptions for users.

**Using multi-signature wallets**

Another approach for implementing secure access control is using a [multi-signature account](https://ethereum.org/en/developers/docs/smart-contracts/#multisig) to manage a contract. Unlike a regular EOA, multi-signature accounts are owned by multiple entities and require signatures from a minimum number of accounts—say 3-of-5—to execute transactions.

Using a multisig for access control introduces an extra layer of security since actions on the target contract require consent from multiple parties. This is particularly useful if using the Ownable pattern is necessary, as it makes it more difficult for an attacker or rogue insider to manipulate sensitive contract functions for malicious purposes.

**Use require(), asserts(), and revert() statements to guard contract operations**

As mentioned, anyone can call public functions in your smart contract once it is deployed on the blockchain. Since you cannot know in advance how external accounts will interact with a contract, it is ideal to implement internal safeguards against problematic operations before deploying. You can enforce correct behavior in smart contracts by using the `require()`, `assert()`, and `revert()` statements to trigger exceptions and revert state changes if execution fails to satisfy certain requirements.

- **`require()`**: `require` are defined at the start of functions and ensures predefined conditions are met before the called function is executed. A `require` statement can be used to validate user inputs, check state variables, or authenticate the identity of the calling account before progressing with a function.
- **`assert()`**: `assert()` is used to detect internal errors and check for violations of “invariants” in your code. An invariant is a logical assertion about a contract’s state that should hold true for all function executions. An example invariant is the maximum total supply or balance of a token contract. Using `assert()` ensures that your contract never reaches a vulnerable state, and if it does, all changes to state variables are rolled back.
- **`revert()`**: `revert()` can be used in an if-else statement that triggers an exception if the required condition is not satisfied. The sample contract below uses `revert()` to guard the execution of functions:

```solidity
pragma solidity ^0.8.4;

contract VendingMachine {
    address owner;
    error Unauthorized();
    function buy(uint amount) public payable {
        if (amount > msg.value / 2 ether)
            revert("Not enough Ether provided.");
        // Perform the purchase.
    }
    function withdraw() public {
        if (msg.sender != owner)
            revert Unauthorized();

        payable(msg.sender).transfer(address(this).balance);
    }
}
```

**Test smart contracts and verify code correctness**

The immutability of code running in the [Ethereum Virtual Machine](https://ethereum.org/en/developers/docs/evm/) means smart contracts demand a higher level of quality assessment during the development phase. Testing your contract extensively and observing it for any unexpected results will improve security a great deal and protect your users in the long run.

The usual method is to write small unit tests using mock data that the contract is expected to receive from users. [Unit testing](https://ethereum.org/en/developers/docs/smart-contracts/testing/#unit-testing) is good for testing the functionality of certain functions and ensuring a smart contract works as expected.

Unfortunately, unit testing is minimally effective for improving smart contract security when used in isolation. A unit test might prove a function executes properly for mock data, but unit tests are only as effective as the tests that are written. This makes it difficult to detect missed edge cases and vulnerabilities that could break the safety of your smart contract.

A better approach is to combine unit testing with property-based testing performed using [static and dynamic analysis(opens in a new tab)](https://ethereum.org/developers/docs/smart-contracts/testing/#static-dynamic-analysis). Static analysis relies on low-level representations, such as [control flow graphs(opens in a new tab)](https://en.wikipedia.org/wiki/Control-flow_graph) and [abstract syntax trees(opens in a new tab)](https://deepsource.io/glossary/ast/) to analyze reachable program states and execution paths. Meanwhile, dynamic analysis techniques, such as fuzzing, execute contract code with random input values to detect operations that violate security properties.

[Formal verification](https://ethereum.org/en/developers/docs/smart-contracts/formal-verification/) is another technique for verifying security properties in smart contracts. Unlike regular testing, formal verification can conclusively prove the absence of errors in a smart contract. This is achieved by creating a formal specification that captures desired security properties and proving that a formal model of the contracts adheres to this specification.

**Ask for an independent review of your code**

After testing your contract, it is good to ask others to check the source code for any security issues. Testing will not uncover every flaw in a smart contract, but getting an independent review increases the possibility of spotting vulnerabilities.

**Audits**

Commissioning a smart contract audit is one way of conducting an independent code review. Auditors play an important role in ensuring that smart contracts are secure and free from quality defects and design errors.

That said, you should avoid treating audits as a silver bullet. Smart contract audits won't catch every bug and are mostly designed to provide an additional round of reviews, which can help detect issues missed by developers during initial development and testing. You should also follow [best practices for working with auditors(opens in a new tab)](https://twitter.com/tinchoabbate/status/1400170232904400897), such as documenting code properly and adding inline comments, to maximize the benefit of a smart contract audit.

**Bug bounties**

Setting up a bug bounty program is another approach for implementing external code reviews. A bug bounty is a financial reward given to individuals (usually whitehat hackers) that discover vulnerabilities in an application.

When used properly, bug bounties give members of the hacker community incentive to inspect your code for critical flaws. A real-life example is the “infinite money bug” that would have let an attacker create an unlimited amount of Ether on [Optimism(opens in a new tab)](https://www.optimism.io/), a [Layer 2](https://ethereum.org/en/layer-2/) protocol running on Ethereum. Fortunately, a whitehat hacker [discovered the flaw(opens in a new tab)](https://www.saurik.com/optimism.html) and notified the team, [earning a large payout in the process(opens in a new tab)](https://cryptoslate.com/critical-bug-in-ethereum-l2-optimism-2m-bounty-paid/).

A useful strategy is to set the payout of a bug bounty program in proportion to the amount of funds at stake. Described as the “[scaling bug bounty(opens in a new tab)](https://medium.com/immunefi/a-defi-security-standard-the-scaling-bug-bounty-9b83dfdc1ba7)”, this approach provides financial incentives for individuals to responsibly disclose vulnerabilities instead of exploiting them.

**Follow best practice during smart contract development**

The existence of audits and bug bounties doesn’t excuse your responsibility to write high-quality code. Good smart contract security starts with following proper design and development processes:

- Store all code in a version control system, such as git
- Make all code modifications via pull requests
- Ensure pull requests have at least one independent reviewer—if you are working solo on a project, consider finding other developers and trade code reviews
- Use a [development environment](https://ethereum.org/en/developers/docs/frameworks/) for testing, compiling, deploying smart contracts
- Run your code through basic code analysis tools, such as Mythril and Slither. Ideally, you should do this before each pull request is merged and compare differences in output
- Ensure your code compiles without errors, and the Solidity compiler emits no warnings
- Properly document your code (using [NatSpec(opens in a new tab)](https://solidity.readthedocs.io/en/develop/natspec-format.html)) and describe details about the contract architecture in easy-to-understand language. This will make it easier for others to audit and review your code.

**Implement robust disaster recovery plans**

Designing secure access controls, implementing function modifiers, and other suggestions can improve smart contract security, but they cannot rule out the possibility of malicious exploits. Building secure smart contracts requires “preparing for failure” and having a fallback plan for responding effectively to attacks. A proper disaster recovery plan will incorporate some or all of the following components:

**Contract upgrades**

While Ethereum smart contracts are immutable by default, it is possible to achieve some degree of mutability by using upgrade patterns. Upgrading contracts is necessary in cases where a critical flaw renders your old contract unusable and deploying new logic is the most feasible option.

Contract upgrade mechanisms work differently, but the “proxy pattern” is one of the more popular approaches for upgrading smart contracts. Proxy patterns split an application’s state and logic between *two* contracts. The first contract (called a ‘proxy contract’) stores state variables (e.g., user balances), while the second contract (called a ‘logic contract’) holds the code for executing contract functions.

Accounts interact with the proxy contract, which dispatches all function calls to the logic contract using the `[delegatecall()`(opens in a new tab)](https://docs.soliditylang.org/en/v0.8.16/introduction-to-smart-contracts.html?highlight=delegatecall#delegatecall-callcode-and-libraries) low-level call. Unlike a regular message call, `delegatecall()` ensures the code running at the logic contract’s address is executed in the context of the calling contract. This means the logic contract will always write to the proxy’s storage (instead of its own storage) and the original values of `msg.sender` and `msg.value` are preserved.

Delegating calls to the logic contract requires storing its address in the proxy contract's storage. Hence, upgrading the contract's logic is only a matter of deploying another logic contract and storing the new address in the proxy contract. As subsequent calls to the proxy contract are automatically routed to the new logic contract, you would have “upgraded” the contract without actually modifying the code.

**Emergency stops**

As mentioned, extensive auditing and testing cannot possibly discover all bugs in a smart contract. If a vulnerability appears in your code after deployment, patching it is impossible since you cannot change the code running at the contract address. Also, upgrade mechanisms (e.g., proxy patterns) may take time to implement (they often require approval from different parties), which only gives attackers more time to cause more damage.

The nuclear option is to implement an “emergency stop” function that blocks calls to vulnerable functions in a contract. Emergency stops typically comprise the following components:

1. A global Boolean variable indicating if the smart contract is in a stopped state or not. This variable is set to `false` when setting up the contract, but will revert to `true` once the contract is stopped.
2. Functions that reference the Boolean variable in their execution. Such functions are accessible when the smart contract is not stopped, and become inaccessible when the emergency stop feature is triggered.
3. An entity that has access to the emergency stop function, which sets the Boolean variable to `true`. To prevent malicious actions, calls to this function can be restricted to a trusted address (e.g., the contract owner).

Once the contract activates the emergency stop, certain functions will not be callable. This is achieved by wrapping select functions in a modifier that references the global variable. Below is [an example(opens in a new tab)](https://github.com/fravoll/solidity-patterns/blob/master/EmergencyStop/EmergencyStop.sol) describing an implementation of this pattern in contracts:

```solidity
// This code has not been professionally audited and makes no promises about safety or correctness. Use at your own risk.

contract EmergencyStop {

    bool isStopped = false;

    modifier stoppedInEmergency {
        require(!isStopped);
        _;
    }

    modifier onlyWhenStopped {
        require(isStopped);
        _;
    }

    modifier onlyAuthorized {
        // Check for authorization of msg.sender here
        _;
    }

    function stopContract() public onlyAuthorized {
        isStopped = true;
    }

    function resumeContract() public onlyAuthorized {
        isStopped = false;
    }

    function deposit() public payable stoppedInEmergency {
        // Deposit logic happening here
    }

    function emergencyWithdraw() public onlyWhenStopped {
        // Emergency withdraw happening here
    }
}
```

This example shows the basic features of emergency stops:

- `isStopped` is a Boolean that evaluates to `false` at the beginning and `true` when the contract enters emergency mode.
- The function modifiers `onlyWhenStopped` and `stoppedInEmergency` check the `isStopped` variable. `stoppedInEmergency` is used to control functions that should be inaccessible when the contract is vulnerable (e.g., `deposit()`). Calls to these functions will simply revert.

`onlyWhenStopped` is used for functions that should be callable during an emergency (e.g., `emergencyWithdraw()`). Such functions can help resolve the situation, hence their exclusion from the “restricted functions” list.

Using an emergency stop functionality provides an effective stopgap for dealing with serious vulnerabilities in your smart contract. However, it increases the need for users to trust developers not to activate it for self-serving reasons. To this end, decentralizing control of the emergency stop either by subjecting it to an on-chain voting mechanism, timelock, or approval from a multisig wallet are possible solutions.

**Event monitoring**

[Events(opens in a new tab)](https://docs.soliditylang.org/en/v0.8.15/contracts.html#events) allow you to track calls to smart contract functions and monitor changes to state variables. It is ideal to program your smart contract to emit an event whenever some party takes a safety-critical action (e.g., withdrawing funds).

Logging events and monitoring them off-chain provides insights on contract operations and aids faster discovery of malicious actions. This means your team can respond faster to hacks and take action to mitigate impact on users, such as pausing functions or performing an upgrade.

You can also opt for an off-the-shelf monitoring tool that automatically forwards alerts whenever someone interacts with your contracts. These tools will allow you to create custom alerts based on different triggers, such as transaction volume, frequency of function calls, or the specific functions involved. For example, you could program an alert that comes in when the amount withdrawn in a single transaction crosses a particular threshold.

**Design secure governance systems**

You may want to decentralize your application by turning over control of core smart contracts to community members. In this case, the smart contract system will include a governance module—a mechanism that allows community members to approve administrative actions via an on-chain governance system. For example, a proposal to upgrade a proxy contract to a new implementation may be voted upon by token-holders.

Decentralized governance can be beneficial, especially because it aligns the interests of developers and end-users. Nevertheless, smart contract governance mechanisms may introduce new risks if implemented incorrectly. A plausible scenario is if an attacker acquires enormous voting power (measured in number of tokens held) by taking out a [flash loan](https://ethereum.org/en/defi/#flash-loans) and pushes through a malicious proposal.

One way of preventing problems related to on-chain governance is to [use a timelock(opens in a new tab)](https://blog.openzeppelin.com/protect-your-users-with-smart-contract-timelocks/). A timelock prevents a smart contract from executing certain actions until a specific amount of time passes. Other strategies include assigning a “voting weight” to each token based on how long it has been locked up for, or measuring the voting power of an address at a historical period (for example, 2-3 blocks in the past) instead of the current block. Both methods reduce the possibility of quickly amassing voting power to swing on-chain votes.

More on [designing secure governance systems(opens in a new tab)](https://blog.openzeppelin.com/smart-contract-security-guidelines-4-strategies-for-safer-governance-systems/) and [different voting mechanisms in DAOs(opens in a new tab)](https://hackernoon.com/governance-is-the-holy-grail-for-daos).

**Reduce complexity in code to a minimum**

Traditional software developers are familiar with the KISS (“keep it simple, stupid”) principle, which advises against introducing unnecessary complexity into software design. This follows the long-held thinking that “complex systems fail in complex ways” and are more susceptible to costly errors.

Keeping things simple is of particular importance when writing smart contracts, given that smart contracts are potentially controlling large amounts of value. A tip for achieving simplicity when writing smart contracts is to reuse existing libraries, such as [OpenZeppelin Contracts(opens in a new tab)](https://docs.openzeppelin.com/contracts/4.x/), where possible. Because these libraries have been extensively audited and tested by developers, using them reduces the chances of introducing bugs by writing new functionality from scratch.

Another common advice is to write small functions and keep contracts modular by splitting business logic across multiple contracts. Not only does writing simpler code reduce the attack surface in a smart contract, it also makes it easier to reason about the correctness of the overall system and detect possible design errors early.

**Defend against common smart contract vulnerabilities**

**Reentrancy**

The EVM doesn’t permit concurrency, meaning two contracts involved in a message call cannot run simultaneously. An external call pauses the calling contract's execution and memory until the call returns, at which point execution proceeds normally. This process can be formally described as transferring [control flow(opens in a new tab)](https://www.computerhope.com/jargon/c/contflow.htm) to another contract.

Although mostly harmless, transferring control flow to untrusted contracts can cause problems, such as reentrancy. A reentrancy attack occurs when a malicious contract calls back into a vulnerable contract before the original function invocation is complete. This type of attack is best explained with an example.

Consider a simple smart contract (‘Victim’) that allows anyone to deposit and withdraw Ether:

```solidity
// This contract is vulnerable. Do not use in production

contract Victim {
    mapping (address => uint256) public balances;

    function deposit() external payable {
        balances[msg.sender] += msg.value;
    }

    function withdraw() external {
        uint256 amount = balances[msg.sender];
        (bool success, ) = msg.sender.call.value(amount)("");
        require(success);
        balances[msg.sender] = 0;
    }
}
```

This contract exposes a `withdraw()` function to allow users to withdraw ETH previously deposited in the contract. When processing a withdrawal, the contract performs the following operations:

1. Checks the user’s ETH balance
2. Sends funds to the calling address
3. Resets their balance to 0, preventing additional withdrawals from the user

The `withdraw()` function in `Victim` contract follows a “checks-interactions-effects” pattern. It *checks* if conditions necessary for execution are satisfied (i.e., the user has a positive ETH balance) and performs the *interaction* by sending ETH to the caller’s address, before applying the *effects* of the transaction (i.e., reducing the user’s balance).

If `withdraw()` is called from an externally owned account (EOA), the function executes as expected: `msg.sender.call.value()` sends ETH to the caller. However, if `msg.sender` is a smart contract account calls `withdraw()`, sending funds using `msg.sender.call.value()` will also trigger code stored at that address to run.

Imagine this is the code deployed at the contract address:

```solidity
contract Attacker {
    function beginAttack() external payable {
        Victim(victim_address).deposit.value(1 ether)();
        Victim(victim_address).withdraw();
    }

    function() external payable {
        if (gasleft() > 40000) {
            Victim(victim_address).withdraw();
        }
    }
}
```

This contract is designed to do three things:

1. Accept a deposit from another account (likely the attacker’s EOA)
2. Deposit 1 ETH into the Victim contract
3. Withdraw the 1 ETH stored in the smart contract

There’s nothing wrong here, except that `Attacker` has another function that calls `withdraw()` in `Victim` again if the gas left over from the incoming `msg.sender.call.value` is more than 40,000. This gives `Attacker` the ability to reenter `Victim` and withdraw more funds *before* the first invocation of `withdraw` completes. The cycle looks like this:

```solidity
- Attacker's EOA calls `Attacker.beginAttack()` with 1 ETH
- `Attacker.beginAttack()` deposits 1 ETH into `Victim`
- `Attacker` calls `withdraw() in `Victim`
- `Victim` checks `Attacker`’s balance (1 ETH)
- `Victim` sends 1 ETH to `Attacker` (which triggers the default function)
- `Attacker` calls `Victim.withdraw()` again (note that `Victim` hasn’t reduced `Attacker`’s balance from the first withdrawal)
- `Victim` checks `Attacker`’s balance (which is still 1 ETH because it hasn’t applied the effects of the first call)
- `Victim` sends 1 ETH to `Attacker` (which triggers the default function and allows `Attacker` to reenter the `withdraw` function)
- The process repeats until `Attacker` runs out of gas, at which point `msg.sender.call.value` returns without triggering additional withdrawals
- `Victim` finally applies the results of the first transaction (and subsequent ones) to its state, so `Attacker`’s balance is set to 0
```

The summary is that because the caller’s balance isn't set to 0 until the function execution completes, subsequent invocations will succeed and allow the caller to withdraw their balance multiple times. This kind of attack can be used to drain a smart contract of its funds, like what happened in the [2016 DAO hack(opens in a new tab)](https://www.coindesk.com/learn/2016/06/25/understanding-the-dao-attack/). Reentrancy attacks are still a critical issue for smart contracts today as [public listings of reentrancy exploits(opens in a new tab)](https://github.com/pcaversaccio/reentrancy-attacks) show.

**How to prevent reentrancy attacks**

An approach to dealing with reentrancy is following the [checks-effects-interactions pattern(opens in a new tab)](https://docs.soliditylang.org/en/develop/security-considerations.html#use-the-checks-effects-interactions-pattern). This pattern orders the execution of functions in a way that code that performs necessary checks before progressing with execution comes first, followed by code that manipulates contract state, with code that interacts with other contracts or EOAs arriving last.

The checks-effect-interaction pattern is used in a revised version of the `Victim` contract shown below:

```solidity
contract NoLongerAVictim {
    function withdraw() external {
        uint256 amount = balances[msg.sender];
        balances[msg.sender] = 0;
        (bool success, ) = msg.sender.call.value(amount)("");
        require(success);
    }
}
```

This contract performs a *check* on the user’s balance, applies the *effects* of the `withdraw()` function (by resetting the user’s balance to 0), and proceeds to perform the *interaction* (sending ETH to the user’s address). This ensures the contract updates its storage before the external call, eliminating the re-entrancy condition that enabled the first attack. The `Attacker` contract could still call back into `NoLongerAVictim`, but since `balances[msg.sender]` has been set to 0, additional withdrawals will throw an error.

Another option is to use a mutual exclusion lock (commonly described as a "mutex") that locks a portion of a contract’s state until a function invocation completes. This is implemented using a Boolean variable that is set to `true` before the function executes and reverts to `false` after the invocation is done. As seen in the example below, using a mutex protects a function against recursive calls while the original invocation is still processing, effectively stopping reentrancy.

```solidity
pragma solidity ^0.7.0;

contract MutexPattern {
    bool locked = false;
    mapping(address => uint256) public balances;

    modifier noReentrancy() {
        require(!locked, "Blocked from reentrancy.");
        locked = true;
        _;
        locked = false;
    }
    // This function is protected by a mutex, so reentrant calls from within `msg.sender.call` cannot call `withdraw` again.
    //  The `return` statement evaluates to `true` but still evaluates the `locked = false` statement in the modifier
    function withdraw(uint _amount) public payable noReentrancy returns(bool) {
        require(balances[msg.sender] >= _amount, "No balance to withdraw.");

        balances[msg.sender] -= _amount;
        bool (success, ) = msg.sender.call{value: _amount}("");
        require(success);

        return true;
    }
}
```

You can also use a [pull payments(opens in a new tab)](https://docs.openzeppelin.com/contracts/4.x/api/security#PullPayment) system that requires users to withdraw funds from the smart contracts, instead of a "push payments" system that sends funds to accounts. This removes the possibility of inadvertently triggering code at unknown addresses (and can also prevent certain denial-of-service attacks).

**Integer underflows and overflows**

An integer overflow occurs when the results of an arithmetic operation falls outside the acceptable range of values, causing it to "roll over" to the lowest representable value. For example, a `uint8` can only store values up to 2^8-1=255. Arithmetic operations that result in values higher than `255` will overflow and reset `uint` to `0`, similar to how the odometer on a car resets to 0 once it reaches the maximum mileage (999999).

Integer underflows happen for similar reasons: the the results of an arithmetic operation falls below the acceptable range. Say you tried decrementing `0` in a `uint8`, the result would simply roll over to the maximum representable value (`255`).

Both integer overflows and underflows can lead to unexpected changes to a contract’s state variables and result in unplanned execution. Below is an example showing how an attacker can exploit arithmetic overflow in a smart contract to perform an invalid operation:

```solidity
pragma solidity ^0.7.6;

// This contract is designed to act as a time vault.
// User can deposit into this contract but cannot withdraw for at least a week.
// User can also extend the wait time beyond the 1 week waiting period.

/*
1. Deploy TimeLock
2. Deploy Attack with address of TimeLock
3. Call Attack.attack sending 1 ether. You will immediately be able to
   withdraw your ether.

What happened?
Attack caused the TimeLock.lockTime to overflow and was able to withdraw
before the 1 week waiting period.
*/

contract TimeLock {
    mapping(address => uint) public balances;
    mapping(address => uint) public lockTime;

    function deposit() external payable {
        balances[msg.sender] += msg.value;
        lockTime[msg.sender] = block.timestamp + 1 weeks;
    }

    function increaseLockTime(uint _secondsToIncrease) public {
        lockTime[msg.sender] += _secondsToIncrease;
    }

    function withdraw() public {
        require(balances[msg.sender] > 0, "Insufficient funds");
        require(block.timestamp > lockTime[msg.sender], "Lock time not expired");

        uint amount = balances[msg.sender];
        balances[msg.sender] = 0;

        (bool sent, ) = msg.sender.call{value: amount}("");
        require(sent, "Failed to send Ether");
    }
}

contract Attack {
    TimeLock timeLock;

    constructor(TimeLock _timeLock) {
        timeLock = TimeLock(_timeLock);
    }

    fallback() external payable {}

    function attack() public payable {
        timeLock.deposit{value: msg.value}();
        /*
        if t = current lock time then we need to find x such that
        x + t = 2**256 = 0
        so x = -t
        2**256 = type(uint).max + 1
        so x = type(uint).max + 1 - t
        */
        timeLock.increaseLockTime(
            type(uint).max + 1 - timeLock.lockTime(address(this))
        );
        timeLock.withdraw();
    }
}
```

**How to prevent integer underflows and overflows**

As of version 0.8.0, the Solidity compiler rejects code that results in integer underflows and overflows. However, contracts compiled with a lower compiler version should either perform checks on functions involving arithmetic operations or use a library (e.g., [SafeMath(opens in a new tab)](https://docs.openzeppelin.com/contracts/2.x/api/math)) that checks for underflow/overflow.

**Oracle manipulation**

[Oracles](https://ethereum.org/en/developers/docs/oracles/) source off-chain information and send it on-chain for smart contracts to use. With oracles, you can design smart contracts that interoperate with off-chain systems, such as capital markets, greatly expanding their application.

But if the oracle is corrupted and sends incorrect information on-chain, smart contracts will execute based on erroneous inputs, which can cause problems. This is the basis of the “oracle problem”, which concerns the task of making sure information from a blockchain oracle is accurate, up-to-date, and timely.

A related security concern is using an on-chain oracle, such as a decentralized exchange, to get the spot price for an asset. Lending platforms in the [decentralized finance (DeFi)](https://ethereum.org/en/defi/) industry often do this to determine the value of a user’s collateral to determine how much they can borrow.

DEX prices are often accurate, largely due to arbitrageurs restoring parity in markets. However, they are open to manipulation, particularly if the on-chain oracle calculates asset prices based on historical trading patterns (as is usually the case).

For instance, an attacker could artificially pump the spot price of an asset by taking out a flash loan right before interacting with your lending contract. Querying the DEX for the asset’s price would return a higher-than-normal value (due to the attacker’s large “buy order” skewing demand for the asset), allowing them to borrow more than they should. Such "flash loan attacks" have been used to exploit reliance on price oracles among DeFi applications, costing protocols millions in lost funds.

**How to prevent oracle manipulation**

The minimum requirement to avoid oracle manipulation is to use a decentralized oracle network that queries information from multiple sources to avoid single points of failure. In most cases, decentralized oracles have built-in cryptoeconomic incentives to encourage oracle nodes to report correct information, making them more secure than centralized oracles.

If you plan on querying an on-chain oracle for asset prices, consider using one that implements a time-weighted average price (TWAP) mechanism. A [TWAP oracle(opens in a new tab)](https://docs.uniswap.org/contracts/v2/concepts/core-concepts/oracles) queries the price of an asset at two different points in time (which you can modify) and calculates the spot price based on the average obtained. Choosing longer time periods protects your protocol against price manipulation since large orders executed recently cannot impact asset prices.

**Resources**

### Tools for analyzing smart contracts and verifying code correctness

- **[Testing tools and libraries](https://ethereum.org/en/developers/docs/smart-contracts/testing/#testing-tools-and-libraries)** - *Collection of industry-standard tools and libraries for performing unit tests, static analysis, and dynamic analysis on smart contracts.*
- **[Formal verification tools](https://ethereum.org/en/developers/docs/smart-contracts/formal-verification/#formal-verification-tools)** - *Tools for verifying functional correctness in smart contracts and checking invariants.*
- **[Smart contract auditing services](https://ethereum.org/en/developers/docs/smart-contracts/testing/#smart-contract-auditing-services)** - *Listing of organizations providing smart contract auditing services for Ethereum development projects.*
- **[Bug bounty platforms](https://ethereum.org/en/developers/docs/smart-contracts/testing/#bug-bounty-platforms)** - *Platforms for coordinating bug bounties and rewarding responsible disclosure of critical vulnerabilities in smart contracts.*
- **[Fork Checker(opens in a new tab)](https://forkchecker.hashex.org/)** - *A free online tool for checking all available information regarding a forked contract.*
- **[ABI Encoder(opens in a new tab)](https://abi.hashex.org/)** - *A free online service for encoding your Solidity contract functions and constructor arguments.*

### Tools for monitoring smart contracts

- **[OpenZeppelin Defender Sentinels(opens in a new tab)](https://docs.openzeppelin.com/defender/sentinel)** - *A tool for automatically monitoring and responding to events, functions, and transaction parameters on your smart contracts.*
- **[Tenderly Real-Time Alerting(opens in a new tab)](https://tenderly.co/alerting/)** - *A tool for getting real-time notifications when unusual or unexpected events happen on your smart contracts or wallets.*

### Tools for secure administration of smart contracts

- **[OpenZeppelin Defender Admin(opens in a new tab)](https://docs.openzeppelin.com/defender/admin)** - *Interface for managing smart contract administration, including access controls, upgrades, and pausing.*
- **[Safe(opens in a new tab)](https://safe.global/)** - *Smart contract wallet running on Ethereum that requires a minimum number of people to approve a transaction before it can occur (M-of-N).*
- **[OpenZeppelin Contracts(opens in a new tab)](https://docs.openzeppelin.com/contracts/4.x/)** - *Contract libraries for implementing administrative features, including contract ownership, upgrades, access controls, governance, pauseability, and more.*

### Smart contract auditing services

- **[ConsenSys Diligence(opens in a new tab)](https://consensys.net/diligence/)** - *Smart contract auditing service helping projects across the blockchain ecosystem ensure their protocols are ready for launch and built to protect users.*
- **[CertiK(opens in a new tab)](https://www.certik.com/)** - *Blockchain security firm pioneering the use of cutting-edge formal Verification technology on smart contracts and blockchain networks.*
- **[Trail of Bits(opens in a new tab)](https://www.trailofbits.com/)** - *Cybersecurity company that combines security research with an attacker mentality to reduce risk and fortify code.*
- **[PeckShield(opens in a new tab)](https://peckshield.com/)** - *Blockchain security company offering products and services for the security, privacy, and usability of the entire blockchain ecosystem.*
- **[QuantStamp(opens in a new tab)](https://quantstamp.com/)** - *Auditing service facilitating the mainstream adoption of blockchain technology through security and risk assessment services.*
- **[OpenZeppelin(opens in a new tab)](https://www.openzeppelin.com/security-audits)** - *Smart contract security company providing security audits for distributed systems.*
- **[Runtime Verification(opens in a new tab)](https://runtimeverification.com/)** - *Security company specializing in formal modeling and verification of smart contracts.*
- **[Hacken(opens in a new tab)](https://hacken.io/)** - *Web3 cybersecurity auditor bringing the 360-degree approach to blockchain security.*
- **[Nethermind(opens in a new tab)](https://nethermind.io/smart-contracts-audits)** - *Solidity and Cairo auditing services, ensuring the integrity of smart contracts and the safety of users across Ethereum and Starknet.*
- **[HashEx(opens in a new tab)](https://hashex.org/)** - *HashEx focuses on blockchain and smart contract auditing to ensure the security of cryptocurrencies, providing services such as smart contract development, penetration testing, blockchain consulting.*
- **[Code4rena(opens in a new tab)](https://code4rena.com/)** - *Competitive audit platform that incentivizes smart contract security experts to find vulnerabilities and help make web3 more secure.*

### Bug bounty platforms

- **[Immunefi(opens in a new tab)](https://immunefi.com/)** - *Bug bounty platform for smart contracts and DeFi projects, where security researchers review code, disclose vulnerabilities, get paid, and make crypto safer.*
- **[HackerOne(opens in a new tab)](https://www.hackerone.com/)** - *Vulnerability coordination and bug bounty platform that connects businesses with penetration testers and cybersecurity researchers.*
- **[HackenProof(opens in a new tab)](https://hackenproof.com/)** - *Expert bug bounty platform for crypto projects (DeFi, Smart Contracts, Wallets, CEX and more), where security professionals provide triage services and researchers get paid for relevant, verified bug reports.*

### Publications of known smart contract vulnerabilities and exploits

- **[ConsenSys: Smart Contract Known Attacks(opens in a new tab)](https://consensys.github.io/smart-contract-best-practices/attacks/)** - *Beginner-friendly explanation of the most significant contract vulnerabilities, with sample code for most cases.*
- **[SWC Registry(opens in a new tab)](https://swcregistry.io/)** - *Curated list of Common Weakness Enumeration (CWE) items that apply to Ethereum smart contracts.*
- **[Rekt(opens in a new tab)](https://rekt.news/)** - *Regularly updated publication of high-profile crypto hacks and exploits, along with detailed post-mortem reports.*

### Challenges for learning smart contract security

- **[Awesome BlockSec CTF(opens in a new tab)](https://github.com/blockthreat/blocksec-ctfs)** - *Curated list of blockchain security wargames, challenges, and [Capture The Flag(opens in a new tab)](https://www.webopedia.com/definitions/ctf-event/amp/) competitions and solution writeups.*
- **[Damn Vulnerable DeFi(opens in a new tab)](https://www.damnvulnerabledefi.xyz/)** - *Wargame to learn offensive security of DeFi smart contracts and build skills in bug-hunting and security auditing.*
- **[Ethernaut(opens in a new tab)](https://ethernaut.openzeppelin.com/)** - *Web3/Solidity-based wargame where each level is a smart contract that needs to be 'hacked'.*

### Best practices for securing smart contracts

- **[ConsenSys: Ethereum Smart Contract Security Best Practices(opens in a new tab)](https://consensys.github.io/smart-contract-best-practices/)** - *Comprehensive list of guidelines for securing Ethereum smart contracts.*
- **[Nascent: Simple Security Toolkit(opens in a new tab)](https://github.com/nascentxyz/simple-security-toolkit)** - *Collection of practical security-focused guides and checklists for smart contract development.*
- **[Solidity Patterns(opens in a new tab)](https://fravoll.github.io/solidity-patterns/)** - *Useful compilation of secure patterns and best practices for the smart contract programming language Solidity.*
- **[Solidity Docs: Security Considerations(opens in a new tab)](https://docs.soliditylang.org/en/v0.8.16/security-considerations.html)** - *Guidelines for writing secure smart contracts with Solidity.*
- **[Smart Contract Security Verification Standard(opens in a new tab)](https://github.com/securing/SCSVS)** - *Fourteen-part checklist created to standardize the security of smart contracts for developers, architects, security reviewers and vendors.*

Visit the following resources to learn more:

- **[Smart Contract Security](https://ethereum.org/en/developers/docs/smart-contracts/security/)**
- **[Ethereum Smart Contract Security Recommendations](https://consensys.net/blog/developers/ethereum-smart-contract-security-recommendations/)**

---

### Fuzzing testing and static analysis

Fuzzing or fuzz testing is an automated software testing technique that involves providing invalid, unexpected, or random data as inputs to a smart contract.

Static analysis is the analysis of smart contracts performed without executing them.

[https://www.youtube.com/watch?v=LRyyNzrqgOc](https://www.youtube.com/watch?v=LRyyNzrqgOc)

Visit the following resources to learn more:

- **[Getting Started with Smart Contract Fuzzing](https://www.immunebytes.com/blog/getting-started-with-smart-contract-fuzzing/)**
- **[Solidity smart contract Static Code Analysis](https://lightrains.com/blogs/solidity-static-analysis-tools/#static-code-analysis)**
- **[Smart contract Fuzzing](https://youtu.be/LRyyNzrqgOc)**

---

### Common threat vectors

Smart contract audits enable developers to provide a thorough analysis of smart contract sets. The main goal of a smart contract audit is to detect and eliminate vulnerabilities, starting with the most common threat vectors.

Examples of smart contract vulnerabilities

- [Insufficient Gas Griefing](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/insufficient-gas-griefing.md)
- [Reentrancy](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/reentrancy.md)
- [Integer Overflow and Underflow](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/overflow-underflow.md)
- [Timestamp Dependence](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/timestamp-dependence.md)
- [Authorization Through tx.origin](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/authorization-txorigin.md)
- [Floating Pragma](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/floating-pragma.md)
- [Outdated Compiler Version](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/outdated-compiler-version.md)
- [Unsafe Low-Level Call](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/unsafe-low-level-call.md)
- [Uninitialized Storage Pointer](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/uninitialized-storage-pointer.md)
- [Assert Violation](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/assert-violation.md)
- [Use of Deprecated Functions](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/use-of-deprecated-functions.md)
- [Delegatecall to Untrusted Callee](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/delegatecall-untrusted-callee.md)
- [Signature Malleability](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/signature-malleability.md)
- [Incorrect Constructor Name](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/incorrect-constructor.md)
- [Shadowing State Variables](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/shadowing-state-variables.md)
- [Weak Sources of Randomness from Chain Attributes](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/weak-sources-randomness.md)
- [Missing Protection against Signature Replay Attacks](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/missing-protection-signature-replay.md)
- [Requirement Validation](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/requirement-violation.md)
- [Write to Arbitrary Storage Location](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/arbitrary-storage-location.md)
- [Incorrect Inheritance Order](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/incorrect-inheritance-order.md)
- [Presence of Unused Variables](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/unused-variables.md)
- [Unencrypted Private Data On-Chain](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/unencrypted-private-data-on-chain.md)
- [Inadherence to Standards](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/inadherence-to-standards.md)
- [Asserting Contract from Code Size](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/asserting-contract-from-code-size.md)
- [Transaction-Ordering Dependence](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/transaction-ordering-dependence.md)
- [DoS with Block Gas Limit](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/dos-gas-limit.md)
- [DoS with (Unexpected) revert](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/dos-revert.md)
- [Unexpected `ecrecover` null address](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/unexpected-ecrecover-null-address.md)
- [Default Visibility](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/default-visibility.md)
- [Insufficient Access Control](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/insufficient-access-control.md)
- [Off-By-One](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/off-by-one.md)
- [Lack of Precision](https://github.com/kadenzipfel/smart-contract-vulnerabilities/blob/master/vulnerabilities/lack-of-precision.md)

Visit the following resources to learn more:
• **[Smart Contract Attack Vectors](https://github.com/kadenzipfel/smart-contract-attack-vectors)**
• **[Solidity Security: Comprehensive list of known attack vectors and common anti-patterns](https://blog.sigmaprime.io/solidity-security.html)**
• **[Blockchain Attack Vectors: Vulnerabilities of the Most Secure Technology](https://www.apriorit.com/dev-blog/578-blockchain-attack-vectors)**

---

### Source of Randomness Attacks

The security of cryptographic systems depends on some secret data that is known to authorized persons but unknown and unpredictable to others. To achieve this unpredictability, some randomization is typically employed. Modern cryptographic protocols often require frequent generation of random quantities. Cryptographic attacks that subvert or exploit weaknesses in this process are known as randomness attacks.

Visit the following resources to learn more:

- **[Smart Contract Randomness or ReplicatedLogic Attack](https://blog.finxter.com/randomness-or-replicatedlogic-attack-on-smart-contracts/)**

---

### **Tools**

Blockchain and smart contract technology is fairly new, therefore, you should expect constant changes in the security landscape, as new bugs and security risks are discovered, and new best practices are developed. Keeping track of this constantly moving landscape proves difficult, so using tools to aid this mission is important. The cost of failing to properly secure smart contracts can be high, and because change can be difficult, we must make use of these tools.

**[Slither](https://github.com/crytic/slither/blob/master/README.md)**

Slither is a Solidity static analysis framework written in Python 3. It runs a suite of vulnerability detectors, prints visual information about contract details, and provides an API to easily write custom analyses. Slither enables developers to find vulnerabilities, enhance their code comprehension, and quickly prototype custom analyses.

**[Mythx**](https://mythx.io)
MythX is a comprehensive smart contract security analysis tools developed by Consensys. It allows users to detect security vulnerabilities in Ethereum smart contracts throughout the development life cycle as well as analyze Solidity dapps for security holes and known smart contract vulnerabilities.

**[Manticore](https://manticore.readthedocs.io)**
Manticore is a symbolic execution tool for analysis of smart contracts and binaries.

**[Echidna](https://roadmap.sh/blockchain)**

Echidna is a Haskell program designed for fuzzing/property-based testing of Ethereum smarts contracts. It uses sophisticated grammar-based fuzzing campaigns based on a contract ABI to falsify user-defined predicates or Solidity assertions.

**Features**

- Generates inputs tailored to your actual code
- Optional corpus collection, mutation and coverage guidance to find deeper bugs
- Powered by [Slither](https://github.com/crytic/slither) to extract useful information before the fuzzing campaign
- Source code integration to identify which lines are covered after the fuzzing campaign
- Interactive terminal UI, text-only or JSON output
- Automatic test case minimization for quick triage
- Seamless integration into the development workflow
- Maximum gas usage reporting of the fuzzing campaign
- Support for a complex contract initialization with [Etheno](https://github.com/crytic/etheno) and Truffle

Visit the following resources to learn more:

- **[Echidna: A Fast Smart Contract Fuzzer](https://github.com/crytic/echidna/blob/master/README.md)**