# Crypto zombies

# Making the zombie Factory

## **Chapter 1**

16-digit integer, like: 8356281049284737

---

## Chapter 2: Contracts

Contract.sol

## **Version Pragma**

All solidity source code should start with a "version pragma" — a declaration of the version of the Solidity compiler this code should use. This is to prevent issues with future compiler versions potentially introducing changes that would break your code.

For the scope of this tutorial, we'll want to be able to compile our smart contracts with any compiler version in the range of 0.5.0 (inclusive) to 0.6.0 (exclusive). It looks like this: `pragma solidity >=0.5.0 <0.6.0;`.

**Exercise**

To start creating our Zombie army, let's create a base contract called `ZombieFactory`.

1. In the box to the right, make it so our contract uses solidity version `>=0.5.0 <0.6.0`.
2. Create an empty contract called `ZombieFactory`.

**Code**

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {
}
```

---

## Chapter 3: State Variables & Integers

***State variables*** are permanently stored in contract storage. This means they're written to the Ethereum blockchain. Think of them like writing to a Database.

Example

```solidity
contract Example {
  // This will be stored permanently in the blockchain
  uint myUnsignedInteger = 100;
}
```

Unsigned Integers: uint

The **uint** data type is an unsigned integer, meaning its value must be non-negative. There’s also an **int** data type for signed integers.

***Note: In Solidity, `uint` is actually an alias for `uint256`, a 256-bit unsigned integer. You can declare uints with less bits — `uint8`, `uint16`, `uint32`, etc.. But in general you want to simply use `uint` except in specific cases, which we'll talk about in later lessons.*

Exercise

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {
    uint dnaDigits = 16;
}
```

---

## **Chapter 4: Math Operations**

Math in Solidity is pretty straightforward. The following operations are the same as in most programming languages:

- Addition: x + y
- Substraction: x - y
- Multiplication: x * y
- Division: x / y
- Modulus / remainder: `x % y` *(for example, `13 % 5` is `3`, because if you divide 5 into 13, 3 is the remainder)*

Solidity also supports an exponential operator (i.e. "x to the power of y", x^y):

```solidity
uint x = 5 ** 2; // equal to 5^2 = 25
```

Exercise

To make sure our Zombie's DNA is only 16 characters, let's make another `uint` equal to 10^16. That way we can later use the modulus operator `%` to shorten an integer to 16 digits.

1. Create a `uint` named `dnaModulus`, and set it equal to **10 to the power of `dnaDigits`**.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

};
```

---

## Chapter 5: Structs

Sometimes you need a more complex data type. For this, Solidity provides Structs:

```solidity
struct Person {
uint age;
string name;
}
```

Structs allow you to create more complicated data types that have multiple properties.

> Note that we just introduced a new type, string. String are used for arbitrary-lenght UTF-8 data. Ex. String greetign = “Hello world”
> 

Exercise

In our app, we're going to want to create some zombies! And zombies will have multiple properties, so this is a perfect use case for a struct.

1. Create a `struct` named `Zombie`.
2. Our `Zombie` struct will have 2 properties: `name` (a `string`), and `dna` (a `uint`).

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

}
```

---

## Chapter 6: Arrays

When you want a collection of something, you can use an **array**. There are two type of **arrays** in Solidity: fixed arrays and **dynamic** arrays:

Public Arrays

You can declare an array as public, and Solidity will automatically create a **getter** method for it. The syntax looks like:

```solidity
Person[] public people;
```

Other contracts would then be able to read from, but not write to, this array. So this is a useful pattern for storing public data in your contract.

Exercise

We’re going to want to store an army of zombies in our app. And we’re going to want to show off all our zombies to other apps, so we’ll want it to be public.

1. Create a public array of Zombie strucs, and name it zombies.

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

     Zombie[] public zombies;
}
```

---

## Chapter 7: Function Declarations

A function declaration in solidity looks like the following:

```solidity
function eatHamburgers(string memory _name, uint _amount) public {

}
```

This is a function named `eatHamburgers` that takes 2 parameters: a `string` and a `uint`. For now the body of the function is empty. Note that we're specifying the function visibility as `public`. We're also providing instructions about where the `_name` variable should be stored- in `memory`. This is required for all reference types such as arrays, structs, mappings, and strings.

What is a reference type you ask? 

Well, there are two ways in which you can pass an argument to a Solidity function:

- By value, which means that the Solidity compiler creates a new copy of the parameters’s value and passes it to your function. This allows your function. This allows your function to modify the value without worrying that the value of the initial parameters gets changed.
- By reference, which means that your function is called with a…reference to the original variable. Thus, if your function changes the value of the variable it receives, the value of the original variable gets changed.

> *Note: It's convention (but not required) to start function parameter variable names with an underscore (`_`) in order to differentiate them from global variables. We'll use that convention throughout our tutorial.*
> 

You would call this function like so:

```solidity
eatHamburgers("vitalik", 100);
```

Exercise

In our app, we're going to need to be able to create some zombies. Let's create a function for that.

1. Create a `public` function named `createZombie`. It should take two parameters: **_name** (a `string`), and **_dna** (a `uint`). Don't forget to pass the first argument by value by using the `memory` keyword

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    // function createZombie(string memory _name, uint _dna) public {

}
```

---

## Chapter 8: Working with Structs and Arrays

Creating New Structs

Remember our Person struct in the previous example?

```solidity
struct Person {
  uint age;
  string name;
}

Person[] public people;
```

Now we’re going to learn how to create new Persons and add them to our people array.

Now we're going to learn how to create new `Person`s and add them to our `people` array.

```solidity
// create a New Person:
Person satoshi = Person(172, "Satoshi");

// Add that person to the Array:
people.push(satoshi);

```

We can also combine these together and do them in one line of code to keep things clean:

```solidity
people.push(Person(16, "Vitalik"));

```

Note that `array.push()`adds something to the **end** of the array, so the elements are in the order we added them. See the following example:

```solidity
uint[] numbers;
numbers.push(5);
numbers.push(10);
numbers.push(15);
// numbers is now equal to [5, 10, 15]
```

Exercise

Let's make our createZombie function do something!

1. Fill in the function body so it creates a new `Zombie`, and adds it to the `zombies` array. The `name` and `dna` for the new Zombie should come from the function arguments.
2. Let's do it in one line of code to keep things clean.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    function createZombie (string memory _name, uint _dna) public {
        // zombies.push(Zombie(_name, _dna));
    }

}
```

---

## Chapter 9: Private / Public functions

In Solidity, functions are public by default. This means anyone (or any other contract) can call your contract’s function and execute its code.

Obviously this isn’t always desirable, and can make your contract vulnerable to attacks. Thus it’s good practice to mark your functions as private by default, and then only make public the functions you want to expose to the world.

Let’s look at how to declare a private function:

```solidity
uint[] numbers;

function _addToArray(uint _number) private {
  numbers.push(_number);
}
```

This means only other functions within our contract will be able to call this function and add to the numbers array.

As you can see, we use the keyword private after the function name. And as with function parameters, it’s convention to start private function names with an underscore(_).

Exercise

Our contract's `createZombie` function is currently public by default — this means anyone could call it and create a new Zombie in our contract! Let's make it private.

1. Modify `createZombie` so it's a private function. Don't forget the naming convention!

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    function _createZombie(string memory _name, uint _dna) private {
        zombies.push(Zombie(_name, _dna));
    }

}
```

---

## Chapter 10: More on Functions

In this chapter, we’re going to learn about function return values, and function modifers.

### Return Values

To return a value from a function, the declaration looks like this:

```solidity
string greeting = "What's up dog";

function sayHello() public returns (string memory) {
  return greeting;
}
```

In Solidity, the function declaration contains the type of the return value (in this case string)

## Function modifers

The above function doesn’t actually change state in Solidity - e.g it doesn’t change any values or write anything. 

So in this case we could declare it as a view function, meaning it’s only viewing the data but not modifying:

```solidity
function sayHello() public view returns (string memory) {
```

Solidity also contains pure functions, which means you’re not even accessing any data in the app. Consider the followingL

```solidity
function _multiply(uint a, uint b) private pure returns (uint) {
  return a * b;
}
```

This function doesn’t even read from the state of the app - its return value depends only on its function parameters. So in this case we would declare the function as pure.

> *Note: It may be hard to remember when to mark functions as pure/view. Luckily the Solidity compiler is good about issuing warnings to let you know when you should use one of these modifiers.*
> 

Exercise

We're going to want a helper function that generates a random DNA number from a string.

1. Create a `private` function called `_generateRandomDna`. It will take one parameter named `_str` (a `string`), and return a `uint`. Don't forget to set the data location of the `_str`parameter to `memory`.
2. This function will view some of our contract's variables but not modify them, so mark it as `view`.
3. The function body should be empty at this point — we'll fill it in later.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    function _createZombie(string memory _name, uint _dna) private {
        zombies.push(Zombie(_name, _dna));
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {

    }
}
```

---

## Chapter 11: Keccak256 and Typecasting

We want our _generateRandomDna function to return a (semi) random unit. 

How can we accomplish this?

Ethereum has the hash function keccak256 built in, which is a version of SHA3. A hash function basically maps an input into a random 256-bit hexadecimal number. A slight change in the input will cause a large change in the hash.

It’s useful for many purposes in Ethereum, but for right now we’re just going to use it for pseudo-random number generation.

Also important, `keccak256` expects a single parameter of type `bytes`. This means that we have to "pack" any parameters before calling `keccak256`:

Example:

```
//6e91ec6b618bb462a4a6ee5aa2cb0e9cf30f7a052bb467b0ba58b8748c00d2e5
keccak256(abi.encodePacked("aaaab"));
//b1f078126895a1424524de5321b339ab00408010b7cf0e6ed451514981e58aa9
keccak256(abi.encodePacked("aaaac"));
```

As you can see, the returned values are totally different despite only a 1 character change in the input.

> *Note: **Secure** random-number generation in blockchain is a very difficult problem. Our method here is insecure, but since security isn't top priority for our Zombie DNA, it will be good enough for our purposes.*
> 

Typecasting

Sometimes you need to convert between data types, take the following example:

```solidity
uint8 a = 5;
uint b = 6;
// throws an error because a * b returns a uint, not uint8:uint8 c = a * b;
// we have to typecast b as a uint8 to make it work:uint8 c = a * uint8(b);

```

In the above, `a * b` returns a `uint`, but we were trying to store it as a `uint8`, which could cause potential problems. By casting it as a `uint8`, it works and the compiler won't throw an error.

In the above, `a * b` returns a `uint`, but we were trying to store it as a `uint8`, which could cause potential problems. By casting it as a `uint8`
, it works and the compiler won't throw an error.

Exercise

Let's fill in the body of our `_generateRandomDna`function! Here's what it should do:

1. The first line of code should take the `keccak256`hash of `abi.encodePacked(_str)` to generate a pseudo-random hexadecimal, typecast it as a `uint`, and finally store the result in a `uint` called `rand`.
2. We want our DNA to only be 16 digits long (remember our `dnaModulus`?). So the second line of code should `return` the above value modulus (`%`) `dnaModulus`.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    function _createZombie(string memory _name, uint _dna) private {
        zombies.push(Zombie(_name, _dna));
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
 return rand % dnaModulus;
    }

}
```

---

## Chapter 12: Putting it Together

We’re close to being done with our random Zombie generator! Let’s create a public function that ties everything together.

We’re going to create a public function that takes an input, the zombie’s name, and uses the name to create a zombie with random DNA.

Exercise

1. Create a `public` function named `createRandomZombie`. It will take one parameter named `_name` (a `string` with the data location set to `memory`). *(Note: Declare this function `public`just as you declared previous functions `private`)*
2. The first line of the function should run the `_generateRandomDna` function on `_name`, and store it in a `uint` named `randDna`.
3. The second line should run the `_createZombie`function and pass it `_name` and `randDna`.
4. The solution should be 4 lines of code (including the closing `}` of the function).

Code

```solidity
pragma solidity  >=0.5.0 <0.6.0;

contract ZombieFactory {

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    function _createZombie(string memory _name, uint _dna) private {
        zombies.push(Zombie(_name, _dna));
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
			}
}
```

---

## Chapter 13: Events

Our contract is almost finished! Now let’s add an event.

Events are a way for your contract to communicate that something happened on the blockchain to your app front-end, which can be “listening” for certain events and take action when they happen.

Example

```solidity
// declare the eventevent IntegersAdded(uint x, uint y, uint result);

function add(uint _x, uint _y) public returns (uint) {
  uint result = _x + _y;
// fire an event to let the app know the function was called:emit IntegersAdded(_x, _y, result);
  return result;
}

```

Your app front-end could then listen for the event. A Javascript implementation would look something like:

```solidity
YourContract.IntegersAdded(function(error, result) {
// do something with result
})

```

Exercise

We want an event to let our front-end know every time a new zombie was created, so the app can display it.

1. Declare an `event` called `NewZombie`. It should pass `zombieId` (a `uint`), `name` (a `string`), and `dna` (a `uint`).
2. Modify the `_createZombie` function to fire the `NewZombie` event after adding the new Zombie to our `zombies` array.
3. You're going to need the zombie's `id`. `array.push()` returns a `uint` of the new length of the array - and since the first item in an array has index 0, `array.push() - 1` will be the index of the zombie we just added. Store the result of `zombies.push() - 1` in a `uint` called `id`, so you can use this in the `NewZombie` event in the next line.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

		event NewZombie(uint zombieId, string name, uint dna);

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    function _createZombie(string memory _name, uint _dna) private {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        emit NewZombie(id, _name, _dna);
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
    }

}
```

---

## Chapter 14: Web3.js

Our Solidity contract is complete! Now we need to write a javascript frontend that interacts with the contract.

Ethereum has a JavaScript library called Web3.js

In a later lesson, we’ll go over in depth how to deploy a contract and set up Web3.js. But for now let’s just look at some sample code for how Web3.js would interact with out deployed contract.

Don’t worry if this doesn’t all make sense yet.

```solidity
// Here's how we would access our contract:
var abi =/* abi generated by the compiler */
var ZombieFactoryContract = web3.eth.contract(abi)
var contractAddress =/* our contract address on Ethereum after deploying */
var ZombieFactory = ZombieFactoryContract.at(contractAddress)
// `ZombieFactory` has access to our contract's public functions and events// some sort of event listener to take the text input:$("#ourButton").click(function(e) {
  var name = $("#nameInput").val()
// Call our contract's `createRandomZombie` function:ZombieFactory.createRandomZombie(name)
})

// Listen for the `NewZombie` event, and update the UI
var event = ZombieFactory.NewZombie(function(error, result) {
  if (error) return
  generateZombie(result.zombieId, result.name, result.dna)
})

// take the Zombie dna, and update our imagefunction generateZombie(id, name, dna) {
  let dnaStr = String(dna)
// pad DNA with leading zeroes if it's less than 16 characterswhile (dnaStr.length < 16)
    dnaStr = "0" + dnaStr

  let zombieDetails = {
// first 2 digits make up the head. We have 7 possible heads, so % 7// to get a number 0 - 6, then add 1 to make it 1 - 7. Then we have 7// image files named "head1.png" through "head7.png" we load based on// this number:
    headChoice: dnaStr.substring(0, 2) % 7 + 1,
// 2nd 2 digits make up the eyes, 11 variations:
    eyeChoice: dnaStr.substring(2, 4) % 11 + 1,
// 6 variations of shirts:
    shirtChoice: dnaStr.substring(4, 6) % 6 + 1,
// last 6 digits control color. Updated using CSS filter: hue-rotate// which has 360 degrees:
    skinColorChoice: parseInt(dnaStr.substring(6, 8) / 100 * 360),
    eyeColorChoice: parseInt(dnaStr.substring(8, 10) / 100 * 360),
    clothesColorChoice: parseInt(dnaStr.substring(10, 12) / 100 * 360),
    zombieName: name,
    zombieDescription: "A Level 1 CryptoZombie",
  }
  return zombieDetails
}

```

What our Javascript then does is take the values generated in zombieDetails above, and use some browser-based Javascript magic (we’re using Vue.js) to swap out the images and apply CSS filters. You’ll get all the code for this in a later lesson.

Zombie: 

[Check out my CryptoZombie Joyboy!](https://share.cryptozombies.io/en/lesson/1/share/Joyboy?id=Y3p8NTc1NTIy)

---

# Zombies attack their victims

## Chapter 1: Lesson overview

**In lesson 1**, we created a function that takes a name, uses it to generate a random zombie, and adds that zombie to our app’s zombie database on the blockchain.

In lesson 2, we’re going to make our app more game-like: We’re going to make it multi-player, and we’ll also be adding a more fun way to create zombies instead of just generating them randomly.

How will we create new zombies? By having our zombies “feed” on other lifeforms!

### Zombie Feeding

When a zombie feeds, it infects the host with a virus. The virus then turns the host into a new zombie that joins your army. The new zombie's DNA will be calculated from the previous zombie's DNA and the host's DNA.

And what do our zombies like to feed on most?

To find that out... You'll have to complete lesson 2!

Exercise

There's a simple demo of feeding to the right. Click on a human to see what happens when your zombie feeds!

You can see that the new zombie's DNA is determined by your original zombie's DNA, as well as the host's DNA.

When you're ready, click "Next chapter" to move on, and let's get started by making our game multi-player.

---

## Chapter 2: Mappings and Addresses

Let’s make our game multi-player by giving the zombies in our database an owner.

To do this, we’ll need 2 new data types: mapping and address.

Addresses

The Ethereum blockchain is made up of ***accounts***, which you can think of like bank accounts. An account has a balance of ***Ether*** (the currency used on the Ethereum blockchain), and you can send and receive Ether payments to other accounts, just like your bank account can wire transfer money to other bank accounts.

Each account has an `address`, which you can think of like a bank account number. It's a unique identifier that points to that account, and it looks like this:

`0x0cE446255506E92DF41614C46F1d6df9Cc969183`

(This address belongs to the CryptoZombies team. If you're enjoying CryptoZombies, you can send us some Ether! 😉 )

We'll get into the nitty gritty of addresses in a later lesson, but for now you only need to understand that **an address is owned by a specific user** (or a smart contract).

So we can use it as a unique ID for ownership of our zombies. When a user creates new zombies by interacting with our app, we'll set ownership of those zombies to the Ethereum address that called the function.

Mappings

In Lesson 1 we looked at ***structs*** and ***arrays***. ***Mappings*** are another way of storing organized data in Solidity.

Defining a `mapping` looks like this:

```solidity
// For a financial app, storing a uint that holds the user's account balance:
mapping (address => uint) public accountBalance;
// Or could be used to store / lookup usernames based on userId
mapping (uint => string) userIdToName;

```

A mapping is essentially a key-value store for storing and looking up data. In the first example, the key is an `address` and the value is a `uint`, and in the second example the key is a `uint` and the value a `string`.

Exercise

To store zombie ownership, we're going to use two mappings: one that keeps track of the address that owns a zombie, and another that keeps track of how many zombies an owner has.

1. Create a mapping called `zombieToOwner`. The key will be a `uint` (we'll store and look up the zombie based on its id) and the value an `address`. Let's make this mapping `public`.
2. Create a mapping called `ownerZombieCount`, where the key is an `address` and the value a `uint`.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    event NewZombie(uint zombieId, string name, uint dna);

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    mapping (uint => address) public zombieToOwner;
    mapping (address => uint) ownerZombieCount;

    function _createZombie(string memory _name, uint _dna) private {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        emit NewZombie(id, _name, _dna);
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
    }

}
```

---

## Chapter 3: Msg.sender

Now that we have our mappings to keep track of who owns a zombie, we’ll want to update the _createZombie method to use them.

In order to do this, we need to use something called msg.sender.

msg.sender

In Solidity, there are certain global variable that are available to all functions. One of these is msg.sender, which refers to the address of the person (or smart contract) who called the current function.

> *Note: In Solidity, function execution always needs to start with an external caller. A contract will just sit on the blockchain doing nothing until someone calls one of its functions. So there will always be a `msg.sender`.*
> 

Here's an example of using `msg.sender` and updating a `mapping`:

```solidity
mapping (address => uint) favoriteNumber;

function setMyNumber(uint _myNumber) public {
  // Update our `favoriteNumber` mapping to store `_myNumber` under `msg.sender`
  favoriteNumber[msg.sender] = _myNumber;
  // ^ The syntax for storing data in a mapping is just like with arrays
}

function whatIsMyNumber() public view returns (uint) {
  // Retrieve the value stored in the sender's address
  // Will be `0` if the sender hasn't called `setMyNumber` yet
  return favoriteNumber[msg.sender];
}
```

In this trivial example, anyone could call `setMyNumber` and store a `uint` in our contract, which would be tied to their address. Then when they called `whatIsMyNumber`, they would be returned the `uint` that they stored.

Using `msg.sender` gives you the security of the Ethereum blockchain — the only way someone can modify someone else's data would be to steal the private key associated with their Ethereum address.

Exercise

Let's update our `_createZombie` method from lesson 1 to assign ownership of the zombie to whoever called the function.

1. First, after we get back the new zombie's `id`, let's update our `zombieToOwner` mapping to store `msg.sender` under that `id`.
2. Second, let's increase `ownerZombieCount` for this `msg.sender`.

In Solidity, you can increase a `uint` with `++`, just like in JavaScript:

```solidity
uint number = 0;
number++;
// `number` is now `1`

```

Your final answer for this chapter should be 2 lines of code.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    event NewZombie(uint zombieId, string name, uint dna);

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    mapping (uint => address) public zombieToOwner;
    mapping (address => uint) ownerZombieCount;

    function _createZombie(string memory _name, uint _dna) private {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
         zombieToOwner[id] = msg.sender;
         ownerZombieCount[msg.sender]++;
        emit NewZombie(id, _name, _dna);
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
    }

}
```

---

### Chapter 4: Require

In lesson 1, we made it so users can create new zombies by calling `createRandomZombie` and entering a name. However, if users could keep calling this function to create unlimited zombies in their army, the game wouldn't be very fun.

Let's make it so each player can only call this function once. That way new players will call it when they first start the game in order to create the initial zombie in their army.

How can we make it so this function can only be called once per player?

For that we use `require`. `require` makes it so that the function will throw an error and stop executing if some condition is not true:

If you call this function with `sayHiToVitalik("Vitalik")`, it will return "Hi!". If you call it with any other input, it will throw an error and not execute.

Thus `require` is quite useful for verifying certain conditions that must be true before running a function.

Exercise

In our zombie game, we don't want the user to be able to create unlimited zombies in their army by repeatedly calling `createRandomZombie` — it would make the game not very fun.

Let's use `require` to make sure this function only gets executed one time per user, when they create their first zombie.

1. Put a `require` statement at the beginning of `createRandomZombie`. The function should check to make sure `ownerZombieCount[msg.sender]` is equal to `0`, and throw an error otherwise.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    event NewZombie(uint zombieId, string name, uint dna);

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    mapping (uint => address) public zombieToOwner;
    mapping (address => uint) ownerZombieCount;

    function _createZombie(string memory _name, uint _dna) private {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        zombieToOwner[id] = msg.sender;
        ownerZombieCount[msg.sender]++;
        emit NewZombie(id, _name, _dna);
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        require(ownerZombieCount[msg.sender] == 0);
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
    }

}
```

---

### Chapter 5: Inheritance

Our game code is getting quite long. Rather than making one extremely long contract, sometimes it makes sense to splt your code logic across multiple contracts to organize the code.

One feature of solidity that makes this more manageable is contract inheritance:

`BabyDoge` ***inherits*** from `Doge`. That means if you compile and deploy `BabyDoge`, it will have access to both `catchphrase()` and `anotherCatchphrase()` (and any other public functions we may define on `Doge`).

This can be used for logical inheritance (such as with a subclass, a `Cat` is an `Animal`). But it can also be used simply for organizing your code by grouping similar logic together into different contracts.

Exercise

In the next chapters, we're going to be implementing the functionality for our zombies to feed and multiply. Let's put this logic into its own contract that inherits all the methods from `ZombieFactory`.

1. Make a contract called `ZombieFeeding` below `ZombieFactory`. This contract should inherit from our `ZombieFactory` contract.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    event NewZombie(uint zombieId, string name, uint dna);

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    mapping (uint => address) public zombieToOwner;
    mapping (address => uint) ownerZombieCount;

    function _createZombie(string memory _name, uint _dna) private {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        zombieToOwner[id] = msg.sender;
        ownerZombieCount[msg.sender]++;
        emit NewZombie(id, _name, _dna);
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        require(ownerZombieCount[msg.sender] == 0);
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
    }

}

contract ZombieFeeding is ZomnbieFactory{

}
```

### Chapter 5: Import

Our code was getting pretty long, so we split it up into multiple files to make it more manageable. This is normally how you will handle long codebases in your Solidity projects.

When you have multiple files and you want to import one file into another, Solidity uses the `import` keyword:

Exercise

Now that we've set up a multi-file structure, we need to use `import`to read the contents of the other file:

1. Import `zombiefactory.sol` into our new file, `zombiefeeding.sol`.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";
contract ZombieFeeding is ZombieFactory {

}
```

---

### Chapter 7: Storage vs Memory (Data location)

In Solidity, there are two locations you can store variables — in `storage` and in `memory`.

***Storage*** refers to variables stored permanently on the blockchain. ***Memory*** variables are temporary, and are erased between external function calls to your contract. Think of it like your computer's hard disk vs RAM.

Most of the time you don't need to use these keywords because Solidity handles them by default. State variables (variables declared outside of functions) are by default `storage` and written permanently to the blockchain, while variables declared inside functions are `memory` and will disappear when the function call ends.

However, there are times when you do need to use these keywords, namely when dealing with ***structs*** and ***arrays*** within functions:

Don't worry if you don't fully understand when to use which one yet — throughout this tutorial we'll tell you when to use `storage` and when to use `memory`, and the Solidity compiler will also give you warnings to let you know when you should be using one of these keywords.

For now, it's enough to understand that there are cases where you'll need to explicitly declare `storage` or `memory`!

Exercise

It's time to give our zombies the ability to feed and multiply!

When a zombie feeds on some other lifeform, its DNA will combine with the other lifeform's DNA to create a new zombie.

1. Create a function called `feedAndMultiply`. It will take two parameters: `_zombieId` (a `uint`) and `_targetDna` (also a `uint`). This function should be `public`.
2. We don't want to let someone else feed our zombie! So first, let's make sure we own this zombie. Add a `require` statement to verify that `msg.sender` is equal to this zombie's owner (similar to how we did in the `createRandomZombie` function).
    
    > Note: Again, because our answer-checker is primitive, it's expecting msg.sender to come first and will mark it wrong if you switch the order. But normally when you're coding, you can use whichever order you prefer — both are correct.
    > 
3. We're going to need to get this zombie's DNA. So the next thing our function should do is declare a local `Zombie` named `myZombie` (which will be a `storage` pointer). Set this variable to be equal to index `_zombieId` in our `zombies` array.

You should have 4 lines of code so far, including the line with the closing `}`.

We'll continue fleshing out this function in the next chapter!

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract ZombieFeeding is ZombieFactory {

   function feedAndMultiply(uint _zombieId, uint _targetDna) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
   }
}
```

---

### Chapter 8: Zombie DNA

Let's finish writing the `feedAndMultiply`function.

The formula for calculating a new zombie's DNA is simple: the average between the feeding zombie's DNA and the target's DNA.

For example:

```solidity
function testDnaSplicing() public {
  uint zombieDna = 2222222222222222;
  uint targetDna = 4444444444444444;
  uint newZombieDna = (zombieDna + targetDna) / 2;
// ^ will be equal to 3333333333333333
}

```

Later we can make our formula more complicated if we want to, like adding some randomness to the new zombie's DNA. But for now we'll keep it simple — we can always come back to it later.

Exercise

1. First we need to make sure that `_targetDna` isn't longer than 16 digits. To do this, we can set `_targetDna` equal to `_targetDna % dnaModulus` to only take the last 16 digits.
2. Next our function should declare a `uint`named `newDna`, and set it equal to the average of `myZombie`'s DNA and `_targetDna` (as in the example above).
    
    > Note: You can access the properties of myZombie using myZombie.name and myZombie.dna
    > 
3. Once we have the new DNA, let's call `_createZombie`. You can look at the `zombiefactory.sol` tab if you forget which parameters this function needs to call it. Note that it requires a name, so let's set our new zombie's name to `"NoName"` for now — we can write a function to change zombies' names later.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract ZombieFeeding is ZombieFactory {

  function feedAndMultiply(uint _zombieId, uint _targetDna) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    _createZombie("NoName", newDna);
  }
}
```

---

### Chapter 9: More on function visibility

The code in our previous lesson has a mistake!

If you try compiling it, the compiler will throw an error.

This issue is we tried calling the _createZombie function from within ZombieFeeding, but _createZombie is a private function inside ZombieFactory. This means none of the contracts that inherit from ZombieFactory can access it.

Internal and External

In addition to public and private, Solidity has two more types of visibility for functions: internal and external.

**Internal** is the same as private, except that it’s also accessible to contracts that inherit from this contract. 

**External** is similar to public, except that these functions can ONLY be called outside the contract — they can’t be called by other functions inside that contract. 

For declaring internal or external functions, the syntax is the same as private and public:

```solidity
contract Sandwich {
  uint private sandwichesEaten = 0;

  function eat() internal {
    sandwichesEaten++;
  }
}

contract BLT is Sandwich {
  uint private baconSandwichesEaten = 0;

  function eatWithBacon() public returns (string memory) {
    baconSandwichesEaten++;
// We can call this here because it's internal
    eat();
  }
}
```

Exercise

1. Change `_createZombie()` from `private` to `internal` so our other contract can access it.
    
    We've already focused you back to the proper tab, `zombiefactory.sol`.
    
    Code
    
    ```solidity
    pragma solidity >=0.5.0 <0.6.0;
    
    contract ZombieFactory {
    
        event NewZombie(uint zombieId, string name, uint dna);
    
        uint dnaDigits = 16;
        uint dnaModulus = 10 ** dnaDigits;
    
        struct Zombie {
            string name;
            uint dna;
        }
    
        Zombie[] public zombies;
    
        mapping (uint => address) public zombieToOwner;
        mapping (address => uint) ownerZombieCount;
    
        // edit function definition below
        function _createZombie(string memory _name, uint _dna) internal {
            uint id = zombies.push(Zombie(_name, _dna)) - 1;
            zombieToOwner[id] = msg.sender;
            ownerZombieCount[msg.sender]++;
            emit NewZombie(id, _name, _dna);
        }
    
        function _generateRandomDna(string memory _str) private view returns (uint) {
            uint rand = uint(keccak256(abi.encodePacked(_str)));
            return rand % dnaModulus;
        }
    
        function createRandomZombie(string memory _name) public {
            require(ownerZombieCount[msg.sender] == 0);
            uint randDna = _generateRandomDna(_name);
            _createZombie(_name, randDna);
        }
    
    }
    ```
    
    ### Chapter 10: What do Zombies eat?
    
    It’s time to feed our zombies! And what do zombies like to eat most?
    
    Well it just so happens that CryptoZombies love to eat…
    
    In order to do this we’ll need to read the kittyDna from the CryptoKitties smart contract. We can do that because the CryptoKitties data is stored openly on the blockchain. Isn’t the blockchain cool?!
    
    Don’t worry — our game isn’t actually going to hurt anyone’s CryptoKitty. We’re only reading the CryptoKitties data, we’re not able to actually delete it.
    
    Interacting with other contracts
    
    For our contract to talk to another contract on the blockchain that we don’t own, first we need to define an interface.
    
    Let’s look at a simple example. Say there was a contract on the blockchain that looked like this:
    
    ```solidity
    contract LuckyNumber {
      mapping(address => uint) numbers;
    
      function setNum(uint _num) public {
        numbers[msg.sender] = _num;
      }
    
      function getNum(address _myAddress) public view returns (uint) {
        return numbers[_myAddress];
      }
    }
    ```
    
    This would be a simple contract where anyone could store their lucky number, and it will be associated with their Ethereum address. Then anyone else could look up that person’s lucky number using their address.
    
    Now let’s say we had external contract that wanted to read the data in this contract using the getNum function.
    
    First we’d have to define an interface of the LuckyNumber contract:
    
    ```solidity
    contract NumberInterface {
      function getNum(address _myAddress) public view returns (uint);
    }
    ```
    
    Notice that this looks like defining a contract, with a few differences. For one, we’re only declaring the functions we want to interact with - in this case getNum - and we don’t mention any of the other functions or state variables.
    
    Secondly, we’re not defining the function bodies. Instead of curly braces ({and}), we’re simply ending the function declaration with a semi-colon (`;`).
    
    So it kind of looks like a contract skeleton. This is how the compiler knows it's an interface.
    
    By including this interface in our dapp's code our contract knows what the other contract's functions look like, how to call them, and what sort of response to expect.
    
    We'll get into actually calling the other contract's functions in the next lesson, but for now let's declare our interface for the CryptoKitties contract.
    
    Exercise
    
    We've looked up the CryptoKitties source code for you, and found a function called `getKitty` that returns all the kitty's data, including its "genes" (which is what our zombie game needs to form a new zombie!).
    
    The function looks like this:
    
    ```
    function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
    ) {
    Kitty storage kit = kitties[_id];
    
    // if this variable is 0 then it's not gestating
    isGestating = (kit.siringWithId != 0);
    isReady = (kit.cooldownEndBlock <= block.number);
    cooldownIndex = uint256(kit.cooldownIndex);
    nextActionAt = uint256(kit.cooldownEndBlock);
    siringWithId = uint256(kit.siringWithId);
    birthTime = uint256(kit.birthTime);
    matronId = uint256(kit.matronId);
    sireId = uint256(kit.sireId);
    generation = uint256(kit.generation);
    genes = kit.genes;
    }
    ```
    
    The function looks a bit different than we're used to. You can see it returns... a bunch of different values. If you're coming from a programming language like JavaScript, this is different — in Solidity you can return more than one value from a function.
    
    Now that we know what this function looks like, we can use it to create an interface:
    
    1. Define an interface called `KittyInterface`. Remember, this looks just like creating a new contract — we use the `contract` keyword.
    2. Inside the interface, define the function `getKitty`(which should be a copy/paste of the function above, but with a semi-colon after the `returns`statement, instead of everything inside the curly braces).

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

 contract KittyInterface{
			function getKitty(uint256 _id) external view returns (
			bool isGestating,
	    bool isReady,
	    uint256 cooldownIndex,
	    uint256 nextActionAt,
		  uint256 siringWithId,
	    uint256 birthTime,
	    uint256 matronId,
	    uint256 sireId,
	    uint256 generation,
	    uint256 genes
	  );
}

contract ZombieFeeding is ZombieFactory {

  function feedAndMultiply(uint _zombieId, uint _targetDna) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    _createZombie("NoName", newDna);
  }

}
```

---

### Chapter 11: Using an interface

Continuing our previous example with `NumberInterface`, once we've defined the interface as:

```solidity
contract NumberInterface {
  function getNum(address _myAddress) public view returns (uint);
}

```

We can use it in a contract as follows:

```solidity
contract MyContract {
  address NumberInterfaceAddress = 0xab38...
// ^ The address of the FavoriteNumber contract on Ethereum
  NumberInterface numberContract = NumberInterface(NumberInterfaceAddress);
// Now `numberContract` is pointing to the other contractfunction someFunction() public {
// Now we can call `getNum` from that contract:
    uint num = numberContract.getNum(msg.sender);
// ...and do something with `num` here
  }
}
```

In this way, your contract can interact with any other contract on the Ethereum blockchain, as long they expose those functions as `public` or `external`.

Exercise

Let's set up our contract to read from the CryptoKitties smart contract!

1. I've saved the address of the CryptoKitties contract in the code for you, under a variable named `ckAddress`. In the next line, create a `KittyInterface` named `kittyContract`, and initialize it with `ckAddress` — just like we did with `numberContract` above.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract KittyInterface {
  function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}

contract ZombieFeeding is ZombieFactory {

  address ckAddress = 0x06012c8cf97BEaD5deAe237070F9587f8E7A266d;
  KittyInterface kittyContract = KittyInterface(ckAddress);

  function feedAndMultiply(uint _zombieId, uint _targetDna) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    _createZombie("NoName", newDna);
  }

}
```

---

### Chapter 12: Handling multiple return values

This `getKitty` function is the first example we've seen that returns multiple values. Let's look at how to handle them:

```solidity
function multipleReturns() internal returns(uint a, uint b, uint c) {
  return (1, 2, 3);
}

function processMultipleReturns() external {
  uint a;
  uint b;
  uint c;
// This is how you do multiple assignment:
  (a, b, c) = multipleReturns();
}

// Or if we only cared about one of the values:function getLastReturnValue() external {
  uint c;
// We can just leave the other fields blank:
  (,,c) = multipleReturns();
}

```

Exercise

Time to interact with the CryptoKitties contract!

Let's make a function that gets the kitty genes from the contract:

1. Make a function called `feedOnKitty`. It will take 2 `uint` parameters, `_zombieId` and `_kittyId`, and should be a `public` function.
2. The function should first declare a `uint` named `kittyDna`.
    
    > Note: In our KittyInterface, genes is a uint256 — but if you remember back to lesson 1, uint is an alias for uint256 — they're the same thing.
    > 
3. The function should then call the `kittyContract.getKitty` function with `_kittyId`and store `genes` in `kittyDna`. Remember — `getKitty` returns a ton of variables. (10 to be exact — I'm nice, I counted them for you!). But all we care about is the last one, `genes`. Count your commas carefully!
4. Finally, the function should call `feedAndMultiply`, and pass it both `_zombieId` and `kittyDna`.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract KittyInterface {
  function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}

contract ZombieFeeding is ZombieFactory {

  address ckAddress = 0x06012c8cf97BEaD5deAe237070F9587f8E7A266d;
  KittyInterface kittyContract = KittyInterface(ckAddress);

  function feedAndMultiply(uint _zombieId, uint _targetDna) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    _createZombie("NoName", newDna);
  }

 function feedOnKitty(uint _zombieId, uint _kittyId) public {
    uint kittyDna;
    (,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);
    feedAndMultiply(_zombieId, kittyDna);
  }

}
```

---

### Chapter 13: Bonus: Kitty Genes

Our function logic is now complete... but let's add in one bonus feature.

Let's make it so zombies made from kitties have some unique feature that shows they're cat-zombies.

To do this, we can add some special kitty code in the zombie's DNA.

If you recall from lesson 1, we're currently only using the first 12 digits of our 16 digit DNA to determine the zombie's appearance. So let's use the last 2 unused digits to handle "special" characteristics.

We'll say that cat-zombies have `99` as their last two digits of DNA (since cats have 9 lives). So in our code, we'll say `if` a zombie comes from a cat, then set the last two digits of DNA to `99`.

If statements

If statements in Solidity look just like JavaScript:

```solidity
function eatBLT(string memory sandwich) public {
  // Remember with strings, we have to compare their keccak256 hashes
  // to check equality
  if (keccak256(abi.encodePacked(sandwich)) == keccak256(abi.encodePacked("BLT"))) {
    eat();
  }
}

```

Exercise

1. First, let's change the function definition for `feedAndMultiply` so it takes a 3rd argument: a `string` named `_species` which we'll store in `memory`.
2. Next, after we calculate the new zombie's DNA, let's add an `if` statement comparing the `keccak256` hashes of `_species` and the string `"kitty"`. We can't directly pass strings to `keccak256`. Instead, we will pass `abi.encodePacked(_species)` as an argument on the left side and `abi.encodePacked("kitty")`as an argument on the right side.
3. Inside the `if` statement, we want to replace the last 2 digits of DNA with `99`. One way to do this is using the logic: `newDna = newDna - newDna % 100 + 99;`.
    
    > Explanation: Assume newDna is 334455. Then newDna % 100 is 55, so newDna - newDna % 100is 334400. Finally add 99 to get 334499.
    > 
4. Lastly, we need to change the function call inside `feedOnKitty`. When it calls `feedAndMultiply`, add the parameter `"kitty"` to the end.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract KittyInterface {
  function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}

contract ZombieFeeding is ZombieFactory {

  address ckAddress = 0x06012c8cf97BEaD5deAe237070F9587f8E7A266d;
  KittyInterface kittyContract = KittyInterface(ckAddress);

 function feedAndMultiply(uint _zombieId, uint _targetDna, string memory _species) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    if (keccak256(abi.encodePacked(_species)) == keccak256(abi.encodePacked("kitty"))) {
      newDna = newDna - newDna % 100 + 99;
    }
    _createZombie("NoName", newDna);
  }

  function feedOnKitty(uint _zombieId, uint _kittyId) public {
    uint kittyDna;
    (,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);
    // And modify function call here:
    feedAndMultiply(_zombieId, kittyDna, "kitty");
  }

}
```

---

### Chapter 14: Wrapping it up

JavaScript implementation

Once we're ready to deploy this contract to Ethereum we'll just compile and deploy `ZombieFeeding` — since this contract is our final contract that inherits from `ZombieFactory`, and has access to all the public methods in both contracts.

Let's look at an example of interacting with our deployed contract using JavaScript and web3.js:

```solidity
var abi =/* abi generated by the compiler */
var ZombieFeedingContract = web3.eth.contract(abi)
var contractAddress =/* our contract address on Ethereum after deploying */
var ZombieFeeding = ZombieFeedingContract.at(contractAddress)

// Assuming we have our zombie's ID and the kitty ID we want to attacklet zombieId = 1;
let kittyId = 1;

// To get the CryptoKitty's image, we need to query their web API. This// information isn't stored on the blockchain, just their webserver.// If everything was stored on a blockchain, we wouldn't have to worry// about the server going down, them changing their API, or the company// blocking us from loading their assets if they don't like our zombie game ;)let apiUrl = "https://api.cryptokitties.co/kitties/" + kittyId
$.get(apiUrl, function(data) {
  let imgUrl = data.image_url
// do something to display the image
})

// When the user clicks on a kitty:$(".kittyImage").click(function(e) {
// Call our contract's `feedOnKitty` methodZombieFeeding.feedOnKitty(zombieId, kittyId)
})

// Listen for a NewZombie event from our contract so we can display it:
ZombieFactory.NewZombie(function(error, result) {
  if (error) return
// This function will display the zombie, like in lesson 1:
  generateZombie(result.zombieId, result.name, result.dna)
})

```

Exercise

Select the kitty you want to feed on. Your zombie's DNA and the kitty's DNA will combine, and you'll get a new zombie in your army!

Notice those cute cat legs on your new zombie? That's our final `99` digits of DNA at work 😉

You can start over and try again if you want. When you get a kitty zombie you're happy with (you only get to keep one), go ahead and proceed to the next chapter to complete lesson 2!

---

## Lesson 3: advanced Solidity Concepts

### **Chapter 1: Immutability of contracts**

Up until now, Solidity has looked quite similar to other languages like JavaScript. But there are a number of ways that Ethereum DApps are actually quite different from normal applications.

To start with, after you deploy a contract to Ethereum, it’s ***immutable***, which means that it can never be modified or updated again.

The initial code you deploy to a contract is there to stay, permanently, on the blockchain. This is one reason security is such a huge concern in Solidity. If there's a flaw in your contract code, there's no way for you to patch it later. You would have to tell your users to start using a different smart contract address that has the fix.

But this is also a feature of smart contracts. The code is law. If you read the code of a smart contract and verify it, you can be sure that every time you call a function it's going to do exactly what the code says it will do. No one can later change that function and give you unexpected results.

External dependencies

In Lesson 2, we hard-coded the CryptoKitties contract address into our DApp. But what would happen if the CryptoKitties contract had a bug and someone destroyed all the kitties?

It's unlikely, but if this did happen it would render our DApp completely useless — our DApp would point to a hardcoded address that no longer returned any kitties. Our zombies would be unable to feed on kitties, and we'd be unable to modify our contract to fix it.

For this reason, it often makes sense to have functions that will allow you to update key portions of the DApp.

For example, instead of hard coding the CryptoKitties contract address into our DApp, we should probably have a `setKittyContractAddress` function that lets us change this address in the future in case something happens to the CryptoKitties contract.

Exercise

Let's update our code from Lesson 2 to be able to change the CryptoKitties contract address.

1. Delete the line of code where we hard-coded `ckAddress`.
2. Change the line where we created `kittyContract` to just declare the variable — i.e. don't set it equal to anything.
3. Create a function called `setKittyContractAddress`. It will take one argument, `_address` (an `address`), and it should be an `external` function.
4. Inside the function, add one line of code that sets `kittyContract` equal to `KittyInterface(_address)`.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract KittyInterface {
  function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}

contract ZombieFeeding is ZombieFactory {
  KittyInterface kittyContract;

  function setKittyContractAddress(address _address) external {
		kittyContract = KittyInterface(_address);
}

  function feedAndMultiply(uint _zombieId, uint _targetDna, string memory _species) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    if (keccak256(abi.encodePacked(_species)) == keccak256(abi.encodePacked("kitty"))) {
      newDna = newDna - newDna % 100 + 99;
    }
    _createZombie("NoName", newDna);
  }

  function feedOnKitty(uint _zombieId, uint _kittyId) public {
    uint kittyDna;
    (,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);
    feedAndMultiply(_zombieId, kittyDna, "kitty");
  }

}
```

---

### Chapter 2: Ownable Contracts

Did you spot the security hole in the previous chapter?

`setKittyContractAddress` is `external`, so anyone can call it! That means anyone who called the function could change the address of the CryptoKitties contract, and break our app for all its users.

We do want the ability to update this address in our contract, but we don't want everyone to be able to update it.

To handle cases like this, one common practice that has emerged is to make contracts `Ownable` — meaning they have an owner (you) who has special privileges.

OpenZeppelin’s Ownable contract

Below is the `Ownable` contract taken from the ***OpenZeppelin*** Solidity library. OpenZeppelin is a library of secure and community-vetted smart contracts that you can use in your own DApps. After this lesson, we highly recommend you check out their site to further your learning!

Give the contract below a read-through. You're going to see a few things we haven't learned yet, but don't worry, we'll talk about them afterward.

A few new things here we haven't seen before:

- Constructors: `constructor()` is a ***constructor***, which is an optional special function. It will get executed only one time, when the contract is first created.
- Function Modifiers: `modifier onlyOwner()`. Modifiers are kind of half-functions that are used to modify other functions, usually to check some requirements prior to execution. In this case, `onlyOwner` can be used to limit access so **only** the **owner** of the contract can run this function. We'll talk more about function modifiers in the next chapter, and what that weird `_;` does.
- `indexed` keyword: don't worry about this one, we don't need it yet.

So the `Ownable` contract basically does the following:

1. When a contract is created, its constructor sets the `owner` to `msg.sender` (the person who deployed it)
2. It adds an `onlyOwner` modifier, which can restrict access to certain functions to only the `owner`
3. It allows you to transfer the contract to a new `owner`

`onlyOwner` is such a common requirement for contracts that most Solidity DApps start with a copy/paste of this `Ownable` contract, and then their first contract inherits from it.

Since we want to limit `setKittyContractAddress` to `onlyOwner`, we're going to do the same for our contract

Exercise

We've gone ahead and copied the code of the `Ownable`contract into a new file, `ownable.sol`. Let's go ahead and make `ZombieFactory` inherit from it.

1. Modify our code to `import` the contents of `ownable.sol`. If you don't remember how to do this take a look at `zombiefeeding.sol`.
2. Modify the `ZombieFactory` contract to inherit from `Ownable`. Again, you can take a look at `zombiefeeding.sol` if you don't remember how this is done.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

// import "./ownable.sol";

// 2. Inherit here:
contract ZombieFactory is Ownable {

    event NewZombie(uint zombieId, string name, uint dna);

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    mapping (uint => address) public zombieToOwner;
    mapping (address => uint) ownerZombieCount;

    function _createZombie(string memory _name, uint _dna) internal {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        zombieToOwner[id] = msg.sender;
        ownerZombieCount[msg.sender]++;
        emit NewZombie(id, _name, _dna);
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        require(ownerZombieCount[msg.sender] == 0);
        uint randDna = _generateRandomDna(_name);
        randDna = randDna - randDna % 100;
        _createZombie(_name, randDna);
    }

}
```

---

### Chapter 3: onlyOwner Function Modifier

Now that our base contract `ZombieFactory` inherits from `Ownable`, we can use the `onlyOwner` function modifier in `ZombieFeeding` as well.

This is because of how contract inheritance works. Remember:

```solidity
ZombieFeeding is ZombieFactory
ZombieFactory is Ownable

```

Thus `ZombieFeeding` is also `Ownable`, and can access the functions / events / modifiers from the `Ownable`contract. This applies to any contracts that inherit from `ZombieFeeding` in the future as well.

Function Modifiers

A function modifier looks just like a function, but uses the keyword `modifier` instead of the keyword `function`. And it can't be called directly like a function can — instead we can attach the modifier's name at the end of a function definition to change that function's behavior.

Let's take a closer look by examining `onlyOwner`:

Notice the `onlyOwner` modifier on the `renounceOwnership` function. When you call `renounceOwnership`, the code inside `onlyOwner`executes **first**. Then when it hits the `_;` statement in `onlyOwner`, it goes back and executes the code inside `renounceOwnership`.

So while there are other ways you can use modifiers, one of the most common use-cases is to add a quick `require` check before a function executes.

In the case of `onlyOwner`, adding this modifier to a function makes it so **only** the **owner** of the contract (you, if you deployed it) can call that function.

Exercise

Now we can restrict access to `setKittyContractAddress` so that no one but us can modify it in the future.

1. Add the `onlyOwner` modifier to `setKittyContractAddress`.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract KittyInterface {
  function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}

contract ZombieFeeding is ZombieFactory {

  KittyInterface kittyContract;

  function setKittyContractAddress(address _address) external onlyOwner{
    kittyContract = KittyInterface(_address);
  }

  function feedAndMultiply(uint _zombieId, uint _targetDna, string memory _species) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    if (keccak256(abi.encodePacked(_species)) == keccak256(abi.encodePacked("kitty"))) {
      newDna = newDna - newDna % 100 + 99;
    }
    _createZombie("NoName", newDna);
  }

  function feedOnKitty(uint _zombieId, uint _kittyId) public {
    uint kittyDna;
    (,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);
    feedAndMultiply(_zombieId, kittyDna, "kitty");
  }

}
```

---

### Chapter 4: Gas

Great! Now we know how to update key portions of the DApp while preventing other users from messing with our contracts.

Let's look at another way Solidity is quite different from other programming languages:

Gas — the fuel Ethereum DApps run on

In Solidity, your users have to pay every time they execute a function on your DApp using a currency called ***gas***. Users buy gas with Ether (the currency on Ethereum), so your users have to spend ETH in order to execute functions on your DApp.

How much gas is required to execute a function depends on how complex that function's logic is. Each individual operation has a ***gas cost*** based roughly on how much computing resources will be required to perform that operation (e.g. writing to storage is much more expensive than adding two integers). The total ***gas cost*** of your function is the sum of the gas costs of all its individual operations.

Because running functions costs real money for your users, code optimization is much more important in Ethereum than in other programming languages. If your code is sloppy, your users are going to have to pay a premium to execute your functions — and this could add up to millions of dollars in unnecessary fees across thousands of users.

## **Why is gas necessary?**

Ethereum is like a big, slow, but extremely secure computer. When you execute a function, every single node on the network needs to run that same function to verify its output — thousands of nodes verifying every function execution is what makes Ethereum decentralized, and its data immutable and censorship-resistant.

The creators of Ethereum wanted to make sure someone couldn't clog up the network with an infinite loop, or hog all the network resources with really intensive computations. So they made it so transactions aren't free, and users have to pay for computation time as well as storage.

Struct packing to save gas

In Lesson 1, we mentioned that there are other types of `uint`s: `uint8`, `uint16`, `uint32`, etc.

Normally there's no benefit to using these sub-types because Solidity reserves 256 bits of storage regardless of the `uint` size. For example, using `uint8`instead of `uint` (`uint256`) won't save you any gas.

But there's an exception to this: inside `struct`s.

If you have multiple `uint`s inside a struct, using a smaller-sized `uint` when possible will allow Solidity to pack these variables together to take up less storage. For example:

```solidity
struct NormalStruct {
  uint a;
  uint b;
  uint c;
}

struct MiniMe {
  uint32 a;
  uint32 b;
  uint c;
}

// `mini` will cost less gas than `normal` because of struct packing
NormalStruct normal = NormalStruct(10, 20, 30);
MiniMe mini = MiniMe(10, 20, 30);

```

For this reason, inside a struct you'll want to use the smallest integer sub-types you can get away with.

You'll also want to cluster identical data types together (i.e. put them next to each other in the struct) so that Solidity can minimize the required storage space. For example, a struct with fields `uint c; uint32 a; uint32 b;` will cost less gas than a struct with fields `uint32 a; uint c; uint32 b;`because the `uint32` fields are clustered together.

Exercise

In this lesson, we're going to add 2 new features to our zombies: `level` and `readyTime` — the latter will be used to implement a cooldown timer to limit how often a zombie can feed.

So let's jump back to `zombiefactory.sol`.

1. Add two more properties to our `Zombie` struct: `level` (a `uint32`), and `readyTime` (also a `uint32`). We want to pack these data types together, so let's put them at the end of the struct.

32 bits is more than enough to hold the zombie's level and timestamp, so this will save us some gas costs by packing the data more tightly than using a regular `uint` (256-bits).

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./ownable.sol";

contract ZombieFactory is Ownable {

    event NewZombie(uint zombieId, string name, uint dna);

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
        uint32 level;
				uint32 readyTime;

    }

    Zombie[] public zombies;

    mapping (uint => address) public zombieToOwner;
    mapping (address => uint) ownerZombieCount;

    function _createZombie(string memory _name, uint _dna) internal {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        zombieToOwner[id] = msg.sender;
        ownerZombieCount[msg.sender]++;
        emit NewZombie(id, _name, _dna);
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        require(ownerZombieCount[msg.sender] == 0);
        uint randDna = _generateRandomDna(_name);
        randDna = randDna - randDna % 100;
        _createZombie(_name, randDna);
    }

}
```

---

### Chapter 5: Time Units

The `level` property is pretty self-explanatory. Later on, when we create a battle system, zombies who win more battles will level up over time and get access to more abilities.

The `readyTime` property requires a bit more explanation. The goal is to add a "cooldown period", an amount of time a zombie has to wait after feeding or attacking before it's allowed to feed / attack again. Without this, the zombie could attack and multiply 1,000 times per day, which would make the game way too easy.

In order to keep track of how much time a zombie has to wait until it can attack again, we can use Solidity's time units.

Time units

Solidity provides some native units for dealing with time.

The variable `now` will return the current unix timestamp of the latest block (the number of seconds that have passed since January 1st 1970). The unix time as I write this is `1515527488`.

> *Note: Unix time is traditionally stored in a 32-bit number. This will lead to the "Year 2038" problem, when 32-bit unix timestamps will overflow and break a lot of legacy systems. So if we wanted our DApp to keep running 20 years from now, we could use a 64-bit number instead — but our users would have to spend more gas to use our DApp in the meantime. Design decisions!*
> 

Solidity also contains the time units `seconds`, `minutes`, `hours`, `days`, `weeks`
 and `years`. These will convert to a `uint`of the number of seconds in that length of time. So `1 minutes`is `60`, `1 hours` is `3600`(60 seconds x 60 minutes), `1 days`
 is `86400`(24 hours x 60 minutes x 60 seconds), etc.

Here's an example of how these time units can be useful:

```solidity
uint lastUpdated;

// Set `lastUpdated` to `now`
function updateTimestamp() public {
  lastUpdated = now;
}

// Will return `true` if 5 minutes have passed since `updateTimestamp` was
// called, `false` if 5 minutes have not passed
function fiveMinutesHavePassed() public view returns (bool) {
  return (now >= (lastUpdated + 5 minutes));
}

```

We can use these time units for our Zombie `cooldown`feature.

Exercise

Let's add a cooldown time to our DApp, and make it so zombies have to wait **1 day** after attacking or feeding to attack again.

1. Declare a `uint` called `cooldownTime`, and set it equal to `1 days`. (Forgive the poor grammar — if you set it equal to "1 day", it won't compile!)
2. Since we added a `level` and `readyTime` to our `Zombie` struct in the previous chapter, we need to update `_createZombie()` to use the correct number of arguments when we create a new `Zombie` struct.
    
    Update the `zombies.push` line of code to add 2 more arguments: `1` (for `level`), and `uint32(now + cooldownTime)` (for `readyTime`).
    

> Note: The uint32(...) is necessary because nowreturns a uint256 by default. So we need to explicitly convert it to a uint32.
> 

`now + cooldownTime` will equal the current unix timestamp (in seconds) plus the number of seconds in 1 day — which will equal the unix timestamp 1 day from now. Later we can compare to see if this zombie's `readyTime` is greater than `now` to see if enough time has passed to use the zombie again.

We'll implement the functionality to limit actions based on `readyTime` in the next chapter.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./ownable.sol";

contract ZombieFactory is Ownable {

    event NewZombie(uint zombieId, string name, uint dna);

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;
    uint cooldownTime = 1 days;

    struct Zombie {
        string name;
        uint dna;
        uint32 level;
        uint32 readyTime;
    }

    Zombie[] public zombies;

    mapping (uint => address) public zombieToOwner;
    mapping (address => uint) ownerZombieCount;

    function _createZombie(string memory _name, uint _dna) internal {
        // 2. Update the following line:
        uint id = zombies.push(Zombie(_name, _dna, 1, uint32(now + cooldownTime))) - 1;
        zombieToOwner[id] = msg.sender;
        ownerZombieCount[msg.sender]++;
        emit NewZombie(id, _name, _dna);
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        require(ownerZombieCount[msg.sender] == 0);
        uint randDna = _generateRandomDna(_name);
        randDna = randDna - randDna % 100;
        _createZombie(_name, randDna);
    }

}
```

---

### Chapter 6: Zombie Cooldowns

Now that we have a `readyTime` property on our `Zombie` struct, let's jump to `zombiefeeding.sol` and implement a cooldown timer.

We're going to modify our `feedAndMultiply` such that:

1. Feeding triggers a zombie's cooldown, and
2. Zombies can't feed on kitties until their cooldown period has passed

This will make it so zombies can't just feed on unlimited kitties and multiply all day. In the future when we add battle functionality, we'll make it so attacking other zombies also relies on the cooldown.

First, we're going to define some helper functions that let us set and check a zombie's `readyTime`.

Passing structs as arguments

You can pass a storage pointer to a struct as an argument to a `private` or `internal` function. This is useful, for example, for passing around our `Zombie`structs between functions.

The syntax looks like this:

```solidity
function _doStuff(Zombie storage _zombie) internal {
  // do stuff with _zombie
}

```

This way we can pass a reference to our zombie into a function instead of passing in a zombie ID and looking it up.

Exercise

1. Start by defining a `_triggerCooldown` function. It will take 1 argument, `_zombie`, a `Zombie storage` pointer. The function should be `internal`.
2. The function body should set `_zombie.readyTime` to `uint32(now + cooldownTime)`.
3. Next, create a function called `_isReady`. This function will also take a `Zombie storage`argument named `_zombie`. It will be an `internal view` function, and return a `bool`.
4. The function body should return `(_zombie.readyTime <= now)`, which will evaluate to either `true` or `false`. This function will tell us if enough time has passed since the last time the zombie fed.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract KittyInterface {
  function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}

contract ZombieFeeding is ZombieFactory {

  KittyInterface kittyContract;

  function setKittyContractAddress(address _address) external onlyOwner {
    kittyContract = KittyInterface(_address);
  }

   function _triggerCooldown(Zombie storage _zombie) internal {
		_zombie.readyTime = uint32(now + cooldownTime);
		}

	function _isReady(Zombie storage _zombie) internal view returns (bool) {
		return (_zombie.readyTime <= now);
}

  function feedAndMultiply(uint _zombieId, uint _targetDna, string memory _species) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    if (keccak256(abi.encodePacked(_species)) == keccak256(abi.encodePacked("kitty"))) {
      newDna = newDna - newDna % 100 + 99;
    }
    _createZombie("NoName", newDna);
  }

  function feedOnKitty(uint _zombieId, uint _kittyId) public {
    uint kittyDna;
    (,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);
    feedAndMultiply(_zombieId, kittyDna, "kitty");
  }

}
```

---

### Chapter 7: Public Functions & Security

Now let's modify `feedAndMultiply` to take our cooldown timer into account.

Looking back at this function, you can see we made it `public` in the previous lesson. An important security practice is to examine all your `public` and `external`functions, and try to think of ways users might abuse them. Remember — unless these functions have a modifier like `onlyOwner`, any user can call them and pass them any data they want to.

Re-examining this particular function, the user could call the function directly and pass in any `_targetDna`or `_species` they want to. This doesn't seem very game-like — we want them to follow our rules!

On closer inspection, this function only needs to be called by `feedOnKitty()`, so the easiest way to prevent these exploits is to make it `internal`.

Exercise

1. Currently `feedAndMultiply` is a `public` function. Let's make it `internal` so that the contract is more secure. We don't want users to be able to call this function with any DNA they want.
2. Let's make `feedAndMultiply` take our `cooldownTime` into account. First, after we look up `myZombie`, let's add a `require` statement that checks `_isReady()` and passes `myZombie` to it. This way the user can only execute this function if a zombie's cooldown time is over.
3. At the end of the function let's call `_triggerCooldown(myZombie)` so that feeding triggers the zombie's cooldown time.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract KittyInterface {
  function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}

contract ZombieFeeding is ZombieFactory {

  KittyInterface kittyContract;

  function setKittyContractAddress(address _address) external onlyOwner {
    kittyContract = KittyInterface(_address);
  }

  function _triggerCooldown(Zombie storage _zombie) internal {
    _zombie.readyTime = uint32(now + cooldownTime);
  }

  function _isReady(Zombie storage _zombie) internal view returns (bool) {
      return (_zombie.readyTime <= now);
  }

  // 1. Make this function internal
  function feedAndMultiply(uint _zombieId, uint _targetDna, string memory _species) internal {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
     require(_isReady(myZombie));
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    if (keccak256(abi.encodePacked(_species)) == keccak256(abi.encodePacked("kitty"))) {
      newDna = newDna - newDna % 100 + 99;
    }
    _createZombie("NoName", newDna);
    _triggerCooldown(myZombie);
  }

  function feedOnKitty(uint _zombieId, uint _kittyId) public {
    uint kittyDna;
    (,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);
    feedAndMultiply(_zombieId, kittyDna, "kitty");
  }

}
```

---

### Chapter 8: More on Function Modifiers

Great! Our zombie now has a functional cooldown timer.

Next, we're going to add some additional helper methods. We've created a new file for you called `zombiehelper.sol`, which imports `zombiefeeding.sol`. This will help to keep our code organized.

Let's make it so zombies gain special abilities after reaching a certain level. But in order to do that, first we'll need to learn a little bit more about function modifiers.

Function modifiers with arguments

Previously we looked at the simple example of `onlyOwner`
. But function modifiers can also take arguments. For example:

```solidity
// A mapping to store a user's age:
mapping (uint => uint) public age;

// Modifier that requires this user to be older than a certain age:
modifier olderThan(uint _age, uint _userId) {
  require(age[_userId] >= _age);
  _;
}

// Must be older than 16 to drive a car (in the US, at least).// We can call the `olderThan` modifier with arguments like so:function driveCar(uint _userId) public olderThan(16, _userId) {
// Some function logic
}

```

You can see here that the `olderThan` modifier takes arguments just like a function does. And that the `driveCar` function passes its arguments to the modifier.

Let's try making our own `modifier` that uses the zombie `level` property to restrict access to special abilities.

Exercise

1. In `ZombieHelper`, create a `modifier` called `aboveLevel`. It will take 2 arguments, `_level` (a `uint`) and `_zombieId` (also a `uint`).
2. The body should check to make sure `zombies[_zombieId].level` is greater than or equal to `_level`.
3. Remember to have the last line of the modifier call the rest of the function with `_;`.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefeeding.sol";

contract ZombieHelper is ZombieFeeding {

  modifier aboveLevel(uint _level, uint _zombieId) {
    require(zombies[_zombieId].level >= _level);
    _;
 }
}
```

---

### Chapter 9: Zombie Modifiers

Now let's use our `aboveLevel` modifier to create some functions.

Our game will have some incentives for people to level up their zombies:

- For zombies level 2 and higher, users will be able to change their name.
- For zombies level 20 and higher, users will be able to give them custom DNA.

We'll implement these functions below. Here's the example code from the previous lesson for reference:

```solidity
// A mapping to store a user's age:
mapping (uint => uint) public age;

// Require that this user be older than a certain age:
modifier olderThan(uint _age, uint _userId) {
  require (age[_userId] >= _age);
  _;
}

// Must be older than 16 to drive a car (in the US, at least)function driveCar(uint _userId) public olderThan(16, _userId) {
// Some function logic
}

```

Exercise

1. Create a function called `changeName`. It will take 2 arguments: `_zombieId` (a `uint`), and `_newName` (a `string` with the data location set to `calldata` ), and make it `external`. It should have the `aboveLevel` modifier, and should pass in `2` for the `_level` parameter. (Don't forget to also pass the `_zombieId`).
2. In this function, first we need to verify that `msg.sender` is equal to `zombieToOwner[_zombieId]`. Use a `require`statement.
3. Then the function should set `zombies[_zombieId].name` equal to `_newName`.
4. Create another function named `changeDna`below `changeName`. Its definition and contents will be almost identical to `changeName`, except its second argument will be `_newDna` (a `uint`), and it should pass in `20` for the `_level` parameter on `aboveLevel`. And of course, it should set the zombie's `dna` to `_newDna` instead of setting the zombie's name.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefeeding.sol";

contract ZombieHelper is ZombieFeeding {

  modifier aboveLevel(uint _level, uint _zombieId) {
    require(zombies[_zombieId].level >= _level);
    _;
  }

  function changeName(uint _zombieId, string calldata _newName) external aboveLevel(2, _zombieId){
			require(msg.sender == zombieToOwner[_zombieId]);
			zombies[_zombieId].name = _newName;
}

	function changeDna(uint _zombieId, uint _newDna) external aboveLevel(20, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].dna = _newDna;
  }

}
```

---

### Chapter 10: Saving gas with “view” Functions

Awesome! Now we have some special abilities for higher-level zombies, to give our owners an incentive to level them up. We can add more of these later if we want to.

Let's add one more function: our DApp needs a method to view a user's entire zombie army — let's call it `getZombiesByOwner`.

This function will only need to read data from the blockchain, so we can make it a `view`function. Which brings us to an important topic when talking about gas optimization:

View functions don’t cost gas

`view` functions don't cost any gas when they're called externally by a user.

This is because `view` functions don't actually change anything on the blockchain – they only read the data. So marking a function with `view`tells `web3.js` that it only needs to query your local Ethereum node to run the function, and it doesn't actually have to create a transaction on the blockchain (which would need to be run on every single node, and cost gas).

We'll cover setting up web3.js with your own node later. But for now the big takeaway is that you can optimize your DApp's gas usage for your users by using read-only `external view`functions wherever possible.

Exercise

We're going to implement a function that will return a user's entire zombie army. We can later call this function from `web3.js` if we want to display a user profile page with their entire army.

This function's logic is a bit complicated so it will take a few chapters to implement.

1. Create a new function named `getZombiesByOwner`. It will take one argument, an `address` named `_owner`.
2. Let's make it an `external view` function, so we can call it from `web3.js` without needing any gas.
3. The function should return a `uint[]` (an array of `uint`) as `memory` data location.

Leave the function body empty for now, we'll fill it in in the next chapter.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefeeding.sol";

contract ZombieHelper is ZombieFeeding {

  modifier aboveLevel(uint _level, uint _zombieId) {
    require(zombies[_zombieId].level >= _level);
    _;
  }

  function changeName(uint _zombieId, string calldata _newName) external aboveLevel(2, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].name = _newName;
  }

  function changeDna(uint _zombieId, uint _newDna) external aboveLevel(20, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].dna = _newDna;
  }

   function getZombiesByOwner(address _owner) external view returns(uint[] memory){
}

}
```

---

### Chapter 11: Storage is expensive

One of the more expensive operations in Solidity is using `storage` — particularly writes.

This is because every time you write or change a piece of data, it’s written permanently to the blockchain. Forever! Thousands of nodes across the world need to store that data on their hard drives, and this amount of data keeps growing over time as the blockchain grows. So there's a cost to doing that.

In order to keep costs down, you want to avoid writing data to storage except when absolutely necessary. Sometimes this involves seemingly inefficient programming logic — like rebuilding an array in `memory` every time a function is called instead of simply saving that array in a variable for quick lookups.

In most programming languages, looping over large data sets is expensive. But in Solidity, this is way cheaper than using `storage` if it's in an `external view` function, since `view` functions don't cost your users any gas. (And gas costs your users real money!).

We'll go over `for` loops in the next chapter, but first, let's go over how to declare arrays in memory.

Declaring arrays in memory 

You can use the `memory` keyword with arrays to create a new array inside a function without needing to write anything to storage. The array will only exist until the end of the function call, and this is a lot cheaper gas-wise than updating an array in `storage` — free if it's a `view` function called externally.

Here's how to declare an array in memory:

```solidity
function getArray() external pure returns(uint[] memory) {
  // Instantiate a new array in memory with a length of 3
  uint[] memory values = new uint[](3);

  // Put some values to it
  values[0] = 1;
  values[1] = 2;
  values[2] = 3;

  return values;
}

```

This is a trivial example just to show you the syntax, but in the next chapter we'll look at combining this with `for` loops for real use-cases.

Exercise

In our `getZombiesByOwner` function, we want to return a `uint[]` array with all the zombies a particular user owns.

1. Declare a `uint[] memory` variable called `result`
2. Set it equal to a new `uint` array. The length of the array should be how many zombies this `_owner` owns, which we can look up from our `mapping` with: `ownerZombieCount[_owner]`.
3. At the end of the function return `result`. It's just an empty array right now, but in the next chapter we'll fill it in.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefeeding.sol";

contract ZombieHelper is ZombieFeeding {

  modifier aboveLevel(uint _level, uint _zombieId) {
    require(zombies[_zombieId].level >= _level);
    _;
  }

  function changeName(uint _zombieId, string calldata _newName) external aboveLevel(2, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].name = _newName;
  }

  function changeDna(uint _zombieId, uint _newDna) external aboveLevel(20, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].dna = _newDna;
  }

  function getZombiesByOwner(address _owner) external view returns(uint[] memory) {
     uint[] memoryresult = new uint[](ownerZombieCount[_owner]);
return result;
  }

}
```

---

### Chapter 12: For loops

In the previous chapter, we mentioned that sometimes you'll want to use a `for` loop to build the contents of an array in a function rather than simply saving that array to storage.

Let's look at why.

For our `getZombiesByOwner` function, a naive implementation would be to store a `mapping` of owners to zombie armies in the `ZombieFactory`contract:

```solidity
mapping (address => uint[]) public ownerToZombies
```

Then every time we create a new zombie, we would simply use `ownerToZombies[owner].push(zombieId)`
 to add it to that owner's zombies array. And `getZombiesByOwner`
 would be a very straightforward function:

```solidity
function getZombiesByOwner(address _owner) external view returns (uint[] memory) {
  return ownerToZombies[_owner];
}
```

The problem with this approach 

This approach is tempting for its simplicity. But let's look at what happens if we later add a function to transfer a zombie from one owner to another (which we'll definitely want to add in a later lesson!).

That transfer function would need to:

1. Push the zombie to the new owner's `ownerToZombies` array,
2. Remove the zombie from the old owner's `ownerToZombies` array,
3. Shift every zombie in the older owner's array up one place to fill the hole, and then
4. Reduce the array length by 1.

Step 3 would be extremely expensive gas-wise, since we'd have to do a write for every zombie whose position we shifted. If an owner has 20 zombies and trades away the first one, we would have to do 19 writes to maintain the order of the array.

Since writing to storage is one of the most expensive operations in Solidity, every call to this transfer function would be extremely expensive gas-wise. And worse, it would cost a different amount of gas each time it's called, depending on how many zombies the user has in their army and the index of the zombie being traded. So the user wouldn't know how much gas to send.

Since `view` functions don't cost gas when called externally, we can simply use a for-loop in `getZombiesByOwner` to iterate the entire zombies array and build an array of the zombies that belong to this specific owner. Then our `transfer` function will be much cheaper, since we don't need to reorder any arrays in storage, and somewhat counter-intuitively this approach is cheaper overall.

Using for loops

The syntax of `for` loops in Solidity is similar to JavaScript.

Let's look at an example where we want to make an array of even numbers:

```solidity
function getEvens() pure external returns(uint[] memory) {
  uint[] memory evens = new uint[](5);
// Keep track of the index in the new array:uint counter = 0;
// Iterate 1 through 10 with a for loop:for (uint i = 1; i <= 10; i++) {
// If `i` is even...if (i % 2 == 0) {
// Add it to our array
      evens[counter] = i;
// Increment counter to the next empty index in `evens`:
      counter++;
    }
  }
  return evens;
}

```

This function will return an array with the contents `[2, 4, 6, 8, 10]`.

Exercise

Let's finish our `getZombiesByOwner` function by writing a `for` loop that iterates through all the zombies in our DApp, compares their owner to see if we have a match, and pushes them to our `result` array before returning it.

1. Declare a `uint` called `counter` and set it equal to `0`. We'll use this variable to keep track of the index in our `result` array.
2. Declare a `for` loop that starts from `uint i = 0` and goes up through `i < zombies.length`. This will iterate over every zombie in our array.
3. Inside the `for` loop, make an `if`statement that checks if `zombieToOwner[i]` is equal to `_owner`. This will compare the two addresses to see if we have a match.
4. Inside the `if` statement:
    1. Add the zombie's ID to our `result`array by setting `result[counter]`equal to `i`.
    2. Increment `counter` by 1 (see the `for`loop example above).

That's it — the function will now return all the zombies owned by `_owner` without spending any gas.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefeeding.sol";

contract ZombieHelper is ZombieFeeding {

  modifier aboveLevel(uint _level, uint _zombieId) {
    require(zombies[_zombieId].level >= _level);
    _;
  }

  function changeName(uint _zombieId, string calldata _newName) external aboveLevel(2, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].name = _newName;
  }

  function changeDna(uint _zombieId, uint _newDna) external aboveLevel(20, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].dna = _newDna;
  }

  function getZombiesByOwner(address _owner) external view returns(uint[] memory) {
    uint[] memory result = new uint[](ownerZombieCount[_owner]);
    uint counter = 0;
		for (uint i = 0; i < zombies.length; i++) {
		if (zombieToOwner[i] == _owner) {
		result[counter] = i;
		counter++;
		}
	}
    return result;
  }

}
```

---

## Lesson 4: Zombie Battle System

### Chapter 1: Payable

Up until now, we’re covered quite a few function modifiers. It can be difficult to try to remember everything, so let’s run through a quick review:

1. We have visibility modifiers that control when and where the function can be called from: `private` means it's only callable from other functions inside the contract; `internal` is like `private` but can also be called by contracts that inherit from this one; `external` can only be called outside the contract; and finally `public` can be called anywhere, both internally and externally.
2. We also have state modifiers, which tell us how the function interacts with the BlockChain: `view` tells us that by running the function, no data will be saved/changed. `pure` tells us that not only does the function not save any data to the blockchain, but it also doesn't read any data from the blockchain. Both of these don't cost any gas to call if they're called externally from outside the contract (but they do cost gas if called internally by another function).
3. Then we have custom `modifiers`, which we learned about in Lesson 3: `onlyOwner`and `aboveLevel`, for example. For these we can define custom logic to determine how they affect a function.

These modifiers can all be stacked together on a function definition as follows:

```
function test() external view onlyOwner anotherModifier { /* ... */ }

```

In this chapter, we're going to introduce one more function modifier: `payable`.

The payable modifier

`payable` functions are part of what makes Solidity and Ethereum so cool — they are a special type of function that can receive Ether.

Let that sink in for a minute. When you call an API function on a normal web server, you can't send US dollars along with your function call — nor can you send Bitcoin.

But in Ethereum, because the money (*Ether*), the data (*transaction payload*), and the contract code itself all live on Ethereum, it's possible for you to call a function ***and*** pay money to the contract at the same time.

This allows for some really interesting logic, like requiring a certain payment to the contract in order to execute a function.

Example

```solidity
contract OnlineStore {
  function buySomething() external payable {
    // Check to make sure 0.001 ether was sent to the function call:
    require(msg.value == 0.001 ether);
    // If so, some logic to transfer the digital item to the caller of the function:
    transferThing(msg.sender);
  }
}

```

Here, `msg.value` is a way to see how much Ether was sent to the contract, and `ether` is a built-in unit.

What happens here is that someone would call the function from web3.js (from the DApp's JavaScript front-end) as follows:

```
// Assuming `OnlineStore` points to your contract on Ethereum:
OnlineStore.buySomething({from: web3.eth.defaultAccount, value: web3.utils.toWei(0.001)})

```

Notice the `value` field, where the javascript function call specifies how much `ether` to send (0.001). If you think of the transaction like an envelope, and the parameters you send to the function call are the contents of the letter you put inside, then adding a `value` is like putting cash inside the envelope — the letter and the money get delivered together to the recipient.

Exercise

Let's create a `payable` function in our zombie game.

Let's say our game has a feature where users can pay ETH to level up their zombies. The ETH will get stored in the contract, which you own — this a simple example of how you could make money on your games!

1. Define a `uint` named `levelUpFee`, and set it equal to `0.001 ether`.
2. Create a function named `levelUp`. It will take one parameter, `_zombieId`, a `uint`. It should be `external` and `payable`.
3. The function should first `require` that `msg.value` is equal to `levelUpFee`.
4. It should then increment this zombie's `level`: `zombies[_zombieId].level++`.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefeeding.sol";

contract ZombieHelper is ZombieFeeding {

  uint levelUpFee = 0.001 ether;

  modifier aboveLevel(uint _level, uint _zombieId) {
    require(zombies[_zombieId].level >= _level);
    _;
  }

   function levelUp(uint _zombieId) external payable {
			require(msg.value == levelUpFee);
			zombies[_zombieId].level++;
}

  function changeName(uint _zombieId, string calldata _newName) external aboveLevel(2, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].name = _newName;
  }

  function changeDna(uint _zombieId, uint _newDna) external aboveLevel(20, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].dna = _newDna;
  }

  function getZombiesByOwner(address _owner) external view returns(uint[] memory) {
    uint[] memory result = new uint[](ownerZombieCount[_owner]);
    uint counter = 0;
    for (uint i = 0; i < zombies.length; i++) {
      if (zombieToOwner[i] == _owner) {
        result[counter] = i;
        counter++;
      }
    }
    return result;
  }

}
```

---

### Chapter 2: Withdraws

In the previous chapter, we learned how to send Ether to a contract. So what happens after you send it?

After you send Ether to a contract, it gets stored in the contract's Ethereum account, and it will be trapped there — unless you add a function to withdraw the Ether from the contract.

You can write a function to withdraw Ether from the contract as follows:

```solidity
contract GetPaid is Ownable {
  function withdraw() external onlyOwner {
    address payable _owner = address(uint160(owner()));
    _owner.transfer(address(this).balance);
  }
}

```

Note that we're using `owner()` and `onlyOwner`from the `Ownable` contract, assuming that was imported.

It is important to note that you cannot transfer Ether to an address unless that address is of type `address payable`. But the `_owner` variable is of type `uint160`, meaning that we must explicitly cast it to `address payable`.

Once you cast the address from `uint160` to `address payable`, you can transfer Ether to that address using the `transfer` function, and `address(this).balance` will return the total balance stored on the contract. So if 100 users had paid 1 Ether to our contract, `address(this).balance` would equal 100 Ether.

You can use `transfer` to send funds to any Ethereum address. For example, you could have a function that transfers Ether back to the `msg.sender` if they overpaid for an item:

```
uint itemFee = 0.001 ether;
msg.sender.transfer(msg.value - itemFee);
```

Or in a contract with a buyer and a seller, you could save the seller's address in storage, then when someone purchases his item, transfer him the fee paid by the buyer: `seller.transfer(msg.value)`.

These are some examples of what makes Ethereum programming really cool — you can have decentralized marketplaces like this that aren't controlled by anyone.

Exercise

1. Create a `withdraw` function in our contract, which should be identical to the `GetPaid` example above.
2. The price of Ether has gone up over 10x in the past year. So while 0.001 ether is about $1 at the time of this writing, if it goes up 10x again, 0.001 ETH will be $10 and our game will be a lot more expensive.
    
    So it's a good idea to create a function that allows us as the owner of the contract to set the `levelUpFee`.
    
    a. Create a function called `setLevelUpFee`that takes one argument, `uint _fee`, is `external`, and uses the modifier `onlyOwner`.
    
    b. The function should set `levelUpFee`equal to `_fee`.
    

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefeeding.sol";

contract ZombieHelper is ZombieFeeding {

  uint levelUpFee = 0.001 ether;

  modifier aboveLevel(uint _level, uint _zombieId) {
    require(zombies[_zombieId].level >= _level);
    _;
  }

  function withdraw() external onlyOwner {
    address payable _owner = address(uint160(owner()));
    _owner.transfer(address(this).balance);
  
}
   function setLevelUpFee(uint _fee) external onlyOwner {
    levelUpFee = _fee;
}

  function levelUp(uint _zombieId) external payable {
    require(msg.value == levelUpFee);
    zombies[_zombieId].level++;
  }

  function changeName(uint _zombieId, string calldata _newName) external aboveLevel(2, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].name = _newName;
  }

  function changeDna(uint _zombieId, uint _newDna) external aboveLevel(20, _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    zombies[_zombieId].dna = _newDna;
  }

  function getZombiesByOwner(address _owner) external view returns(uint[] memory) {
    uint[] memory result = new uint[](ownerZombieCount[_owner]);
    uint counter = 0;
    for (uint i = 0; i < zombies.length; i++) {
      if (zombieToOwner[i] == _owner) {
        result[counter] = i;
        counter++;
      }
    }
    return result;
  }

}
```

---

### Chapter 3: Zombie Battles

Now that we’ve learned about payable functions and contract balances, it’s time to add functionality for zombie battles!

Following the format from previous chapters, we’ll organize our code by creating a new file/ contract for the attack functionality that imports from the previous contract

Exercise

Let's review creating a new contract. Repetition leads to mastery!

If you can't remember the syntax for doing these, check `zombiehelper.sol` for the syntax — but try to do it without peeking first to test your knowledge.

1. Declare at the top of the file that we're using Solidity version `>=0.5.0 <0.6.0`.
2. `import` from `zombiehelper.sol`.
3. Declare a new `contract` called `ZombieAttack` that inherits from `ZombieHelper`. Leave the contract body empty for now.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiehelper.sol";

contract ZombieAttack is ZombieHelper{
}
```

---

### Chapter 4: Random Numbers

Great! Now let's figure out the battle logic.

All good games require some level of randomness. So how do we generate random numbers in Solidity?

The real answer here is, you can't. Well, at least you can't do it safely.

Let's look at why.

Random number generation via keccak256

The best source of randomness we have in Solidity is the `keccak256` hash function.

We could do something like the following to generate a random number:

```
// Generate a random number between 1 and 100:
uint randNonce = 0;
uint random = uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % 100;
randNonce++;
uint random2 = uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % 100;

```

What this would do is take the timestamp of `now`, the `msg.sender`, and an incrementing `nonce` (a number that is only ever used once, so we don't run the same hash function with the same input parameters twice).

It would then "pack" the inputs and use `keccak`to convert them to a random hash. Next, it would convert that hash to a `uint`, and then use `% 100` to take only the last 2 digits. This will give us a totally random number between 0 and 99.

This method is vulnerable to attack by a dishonest node

In Ethereum, when you call a function on a contract, you broadcast it to a node or nodes on the network as a ***transaction***. The nodes on the network then collect a bunch of transactions, try to be the first to solve a computationally-intensive mathematical problem as a "Proof of Work", and then publish that group of transactions along with their Proof of Work (PoW) as a ***block*** to the rest of the network.

Once a node has solved the PoW, the other nodes stop trying to solve the PoW, verify that the other node's list of transactions are valid, and then accept the block and move on to trying to solve the next block.

**This makes our random number function exploitable.**

Let's say we had a coin flip contract — heads you double your money, tails you lose everything. Let's say it used the above random function to determine heads or tails. (`random >= 50` is heads, `random < 50` is tails).

If I were running a node, I could publish a transaction **only to my own node** and not share it. I could then run the coin flip function to see if I won — and if I lost, choose not to include that transaction in the next block I'm solving. I could keep doing this indefinitely until I finally won the coin flip and solved the next block, and profit

So how do we generate random numbers safely in Ethereum?

Because the entire contents of the blockchain are visible to all participants, this is a hard problem, and its solution is beyond the scope of this tutorial. You can read [this StackOverflow thread](https://ethereum.stackexchange.com/questions/191/how-can-i-securely-generate-a-random-number-in-my-smart-contract) for some ideas. One idea would be to use an ***oracle*** to access a random number function from outside of the Ethereum blockchain.

Of course, since tens of thousands of Ethereum nodes on the network are competing to solve the next block, my odds of solving the next block are extremely low. It would take me a lot of time or computing resources to exploit this profitably — but if the reward were high enough (like if I could bet $100,000,000 on the coin flip function), it would be worth it for me to attack.

So while this random number generation is NOT secure on Ethereum, in practice unless our random function has a lot of money on the line, the users of your game likely won't have enough resources to attack it.

Because we're just building a simple game for demo purposes in this tutorial and there's no real money on the line, we're going to accept the tradeoffs of using a random number generator that is simple to implement, knowing that it isn't totally secure.

In a future lesson, we may cover using ***oracles***(a secure way to pull data in from outside of Ethereum) to generate secure random numbers from outside the blockchain

Exercise

1. Give our contract a `uint` called `randNonce`, and set it equal to `0`.
2. Create a function called `randMod`(random-modulus). It will be an `internal`function that takes a `uint` named `_modulus`, and `returns` a `uint`.
3. The function should first increment `randNonce` (using the syntax `randNonce++`).
4. Finally, it should (in one line of code) calculate the `uint` typecast of the `keccak256` hash of `abi.encodePacked(now,msg.sender,randNonce)` — and `return` that value `% _modulus`. (Whew! That was a mouthful. If you didn't follow that, just take a look at the example above where we generated a random number — the logic is very similar).

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiehelper.sol";

contract ZombieAttack is ZombieHelper {
  uint randNonce = 0;
	function randMod(uint _modulus) internal returns(uint) {
    randNonce++;
    return uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % _modulus;
  }

}
```

---

### Chapter 5: Zombie Fightin

Now that we have a source of some randomness in our contract, we can use it in our zombie battles to calculate the outcome.

Our zombie battles will work as follows:

- You choose one of your zombies, and choose an opponent's zombie to attack.
- If you're the attacking zombie, you will have a 70% chance of winning. The defending zombie will have a 30% chance of winning.
- All zombies (attacking and defending) will have a `winCount` and a `lossCount` that will increment depending on the outcome of the battle.
- If the attacking zombie wins, it levels up and spawns a new zombie.
- If it loses, nothing happens (except its `lossCount` incrementing).
- Whether it wins or loses, the attacking zombie's cooldown time will be triggered.

This is a lot of logic to implement, so we'll do it in pieces over the coming chapters.

Exercise

1. Give our contract a `uint` variable called `attackVictoryProbability`, and set it equal to `70`.
2. Create a function called `attack`. It will take two parameters: `_zombieId` (a `uint`) and `_targetId` (also a `uint`). It should be an `external` function.

Leave the function body empty for now.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiehelper.sol";

contract ZombieAttack is ZombieHelper {
  uint randNonce = 0;
  uint attackVictoryProbability = 70;

  function randMod(uint _modulus) internal returns(uint) {
    randNonce++;
    return uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % _modulus;
  }

   function attack(uint _zombieId, uint _targetId) external {
  }
}
```

---

### Chapter 6: Refactoring common logic

Whoever calls our `attack` function — we want to make sure the user actually owns the zombie they're attacking with. It would be a security concern if you could attack with someone else's zombie!

Can you think of how we would add a check to see if the person calling this function is the owner of the `_zombieId` they're passing in?

Give it some thought, and see if you can come up with the answer on your own.

Take a moment... Refer to some of our previous lessons' code for ideas...

Answer below, don't continue until you've given it some thought.

The answer

We've done this check multiple times now in previous lessons. In `changeName()`, `changeDna()`, and `feedAndMultiply()`, we used the following check:

```
require(msg.sender == zombieToOwner[_zombieId]);
```

This is the same logic we'll need for our `attack`function. Since we're using the same logic multiple times, let's move this into its own `modifier` to clean up our code and avoid repeating ourselves.

Exercise

1. Create a `modifier` called `ownerOf`. It will take 1 argument, `_zombieId` (a `uint`).
    
    The body should `require` that `msg.sender`is equal to `zombieToOwner[_zombieId]`, then continue with the function. You can refer to `zombiehelper.sol` if you don't remember the syntax for a modifier.
    
2. Change the function definition of `feedAndMultiply` such that it uses the modifier `ownerOf`.
3. Now that we're using a `modifier`, you can remove the line `require(msg.sender == zombieToOwner[_zombieId]);`

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract KittyInterface {
  function getKitty(uint256 _id) external view returns (
    bool isGestating,
    bool isReady,
    uint256 cooldownIndex,
    uint256 nextActionAt,
    uint256 siringWithId,
    uint256 birthTime,
    uint256 matronId,
    uint256 sireId,
    uint256 generation,
    uint256 genes
  );
}

contract ZombieFeeding is ZombieFactory {

  KittyInterface kittyContract;

	modifier ownerOf(uint _zombieId) {
    require(msg.sender == zombieToOwner[_zombieId]);
    _;
  }
  function setKittyContractAddress(address _address) external onlyOwner {
    kittyContract = KittyInterface(_address);
  }

  function _triggerCooldown(Zombie storage _zombie) internal {
    _zombie.readyTime = uint32(now + cooldownTime);
  }

  function _isReady(Zombie storage _zombie) internal view returns (bool) {
      return (_zombie.readyTime <= now);
  }

  // 2. Add modifier to function definition:
  function feedAndMultiply(uint _zombieId, uint _targetDna, string memory _species) internal ownerOf(_zombieId) {
    Zombie storage myZombie = zombies[_zombieId];
    require(_isReady(myZombie));
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    if (keccak256(abi.encodePacked(_species)) == keccak256(abi.encodePacked("kitty"))) {
      newDna = newDna - newDna % 100 + 99;
    }
    _createZombie("NoName", newDna);
    _triggerCooldown(myZombie);
  }

  function feedOnKitty(uint _zombieId, uint _kittyId) public {
    uint kittyDna;
    (,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);
    feedAndMultiply(_zombieId, kittyDna, "kitty");
  }
}
```

---

### Chapter 7: More Refactoring

We have a couple more places in `zombiehelper.sol` where we need to implement our new `modifier` `ownerOf`.

Exercise

1. Update `changeName()` to use `ownerOf`
2. Update `changeDna()` to use `ownerOf`

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefeeding.sol";

contract ZombieHelper is ZombieFeeding {

  uint levelUpFee = 0.001 ether;

  modifier aboveLevel(uint _level, uint _zombieId) {
    require(zombies[_zombieId].level >= _level);
    _;
  }

  function withdraw() external onlyOwner {
    address _owner = owner();
    _owner.transfer(address(this).balance);
  }

  function setLevelUpFee(uint _fee) external onlyOwner {
    levelUpFee = _fee;
  }

  function levelUp(uint _zombieId) external payable {
    require(msg.value == levelUpFee);
    zombies[_zombieId].level++;
  }

  // 1. Modify this function to use `ownerOf`:
  function changeName(uint _zombieId, string calldata _newName) external aboveLevel(2, _zombieId) ownerOf(_zombieId) {
    zombies[_zombieId].name = _newName;
  }

  // 2. Do the same with this function:
  function changeDna(uint _zombieId, uint _newDna) external aboveLevel(20, _zombieId) ownerOf(_zombieId) {
    zombies[_zombieId].dna = _newDna;
  }

  function getZombiesByOwner(address _owner) external view returns(uint[] memory) {
    uint[] memory result = new uint[](ownerZombieCount[_owner]);
    uint counter = 0;
    for (uint i = 0; i < zombies.length; i++) {
      if (zombieToOwner[i] == _owner) {
        result[counter] = i;
        counter++;
      }
    }
    return result;
  }

}
```

---

### Chapter 8: Back to attack

Enough refactoring — back to `zombieattack.sol`.

We're going to continue defining our `attack`function, now that we have the `ownerOf`modifier to use.

Exercise

1. Add the `ownerOf` modifier to `attack` to make sure the caller owns `_zombieId`.
2. The first thing our function should do is get a `storage` pointer to both zombies so we can more easily interact with them:
    
    a. Declare a `Zombie storage` named `myZombie`, and set it equal to `zombies[_zombieId]`.
    
    b. Declare a `Zombie storage` named `enemyZombie`, and set it equal to `zombies[_targetId]`.
    
3. We're going to use a random number between 0 and 99 to determine the outcome of our battle. So declare a `uint`named `rand`, and set it equal to the result of the `randMod` function with `100` as an argument.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiehelper.sol";

contract ZombieAttack is ZombieHelper {
  uint randNonce = 0;
  uint attackVictoryProbability = 70;

  function randMod(uint _modulus) internal returns(uint) {
    randNonce++;
    return uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % _modulus;

  }

   ownerOf [_zombieId]
  function attack(uint _zombieId, uint _targetId) external {
    Zombie storage myZombie = zombies[_zombieId];
    Zombie storage enemyZombie = zombies[_targetId];
    uint rand = randMod(100);
  }
}
```

---

### Chapter 9: Zombie Wins and Losses

For our zombie game, we're going to want to keep track of how many battles our zombies have won and lost. That way we can maintain a "zombie leaderboard" in our game state.

We could store this data in a number of ways in our DApp — as individual mappings, as leaderboard Struct, or in the `Zombie` struct itself.

Each has its own benefits and tradeoffs depending on how we intend on interacting with the data. In this tutorial, we're going to store the stats on our `Zombie` struct for simplicity, and call them `winCount` and `lossCount`.

So let's jump back to `zombiefactory.sol`, and add these properties to our `Zombie` struct.

Exercise

1. Modify our `Zombie` struct to have 2 more properties:
    
    a. `winCount`, a `uint16`
    
    b. `lossCount`, also a `uint16`
    
    > Note: Remember, since we can pack uints inside structs, we want to use the smallest uints we can get away with. A uint8 is too small, since 2^8 = 256 — if our zombies attacked once per day, they could overflow this within a year. But 2^16 is 65536 — so unless a user wins or loses every day for 179 years straight, we should be safe here.
    > 
2. Now that we have new properties on our `Zombie` struct, we need to change our function definition in `_createZombie()`.
    
    Change the zombie creation definition so it creates each new zombie with `0` wins and `0` losses.
    
    Code
    
    ```solidity
    pragma solidity >=0.5.0 <0.6.0;
    
    import "./ownable.sol";
    
    contract ZombieFactory is Ownable {
    
        event NewZombie(uint zombieId, string name, uint dna);
    
        uint dnaDigits = 16;
        uint dnaModulus = 10 ** dnaDigits;
        uint cooldownTime = 1 days;
    
        struct Zombie {
          string name;
          uint dna;
    			uint winCount;
          uint lossCount;
          uint32 level;
          uint32 readyTime;
          uint16 winCount;
          uint16 lossCount;
    
        Zombie[] public zombies;
    
        mapping (uint => address) public zombieToOwner;
        mapping (address => uint) ownerZombieCount;
    
        function _createZombie(string memory _name, uint _dna) internal {
            // 2. Modify new zombie creation here:
            uint id = zombies.push(Zombie(_name, _dna, 1, uint32(now + cooldownTime), 0, 0)) - 1;
            zombieToOwner[id] = msg.sender;
            ownerZombieCount[msg.sender]++;
            emit NewZombie(id, _name, _dna);
        }
    
        function _generateRandomDna(string memory _str) private view returns (uint) {
            uint rand = uint(keccak256(abi.encodePacked(_str)));
            return rand % dnaModulus;
        }
    
        function createRandomZombie(string memory _name) public {
            require(ownerZombieCount[msg.sender] == 0);
            uint randDna = _generateRandomDna(_name);
            randDna = randDna - randDna % 100;
            _createZombie(_name, randDna);
        }
    
    }
    ```
    
    ---
    
    ### Chapter 10: Zombie victory
    
    Now that we have a `winCount` and `lossCount`, we can update them depending on which zombie wins the fight.
    
    In chapter 6 we calculated a random number from 0 to 100. Now let's use that number to determine who wins the fight, and update our stats accordingly.
    
    Exercise
    
    1. Create an `if` statement that checks if `rand`is ***less than or equal to***`attackVictoryProbability`.
    2. If this condition is true, our zombie wins! So:
        
        a. Increment `myZombie`'s `winCount`.
        
        b. Increment `myZombie`'s `level`. (Level up!!!!!!!)
        
        c. Increment `enemyZombie`'s `lossCount`. (Loser!!!!!! 😫 😫 😫)
        
        d. Run the `feedAndMultiply` function. Check `zombiefeeding.sol` to see the syntax for calling it. For the 3rd argument (`_species`), pass the string `"zombie"`. (It doesn't actually do anything at the moment, but later we could add extra functionality for spawning zombie-based zombies if we wanted to).
        
    
    Code
    
    ```solidity
    import "./zombiehelper.sol";
    
    contract ZombieAttack is ZombieHelper {
      uint randNonce = 0;
      uint attackVictoryProbability = 70;
    
      function randMod(uint _modulus) internal returns(uint) {
        randNonce++;
        return uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % _modulus;
      }
    
      function attack(uint _zombieId, uint _targetId) external ownerOf(_zombieId) {
        Zombie storage myZombie = zombies[_zombieId];
        Zombie storage enemyZombie = zombies[_targetId];
        uint rand = randMod(100);
        if (rand <= attackVictoryProbability) {
           myZombie.winCount++;
           myZombie.level++;
           enemyZombie.lossCount++;
           feedAndMultiply(_zombieId, enemyZombie.dna, "zombie");
         }
      }
    }
    ```
    
    ---
    
    ### Chapter 11: Zombie loss
    
    Now that we've coded what happens when your zombie wins, let's figure out what happens when it **loses**.
    
    In our game, when zombies lose, they don't level down — they simply add a loss to their `lossCount`, and their cooldown is triggered so they have to wait a day before attacking again.
    
    To implement this logic, we'll need an `else`statement.
    
    `else` statements are written just like in JavaScript and many other languages:
    
    ```solidity
    if (zombieCoins[msg.sender] > 100000000) {
    // You rich!!!
    } else {
    // We require more ZombieCoins...
    }
    
    ```
    
    Exercise
    
    1. Add an `else` statement. If our zombie loses:
        
        a. Increment `myZombie`'s `lossCount`.
        
        b. Increment `enemyZombie`'s `winCount`.
        
        c. Run the `_triggerCooldown` function on `myZombie`. This way the zombie can only attack once per day. (Remember, `_triggerCooldown` is already run inside `feedAndMultiply`. So the zombie's cooldown will be triggered whether he wins or loses.)
        
        Code
        
        ```solidity
        pragma solidity >=0.5.0 <0.6.0;
        
        import "./zombiehelper.sol";
        
        contract ZombieAttack is ZombieHelper {
          uint randNonce = 0;
          uint attackVictoryProbability = 70;
        
          function randMod(uint _modulus) internal returns(uint) {
            randNonce++;
            return uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % _modulus;
          }
        
          function attack(uint _zombieId, uint _targetId) external ownerOf(_zombieId) {
            Zombie storage myZombie = zombies[_zombieId];
            Zombie storage enemyZombie = zombies[_targetId];
            uint rand = randMod(100);
            if (rand <= attackVictoryProbability) {
              myZombie.winCount++;
              myZombie.level++;
              enemyZombie.lossCount++;
              feedAndMultiply(_zombieId, enemyZombie.dna, "zombie");
            }  else {
              myZombie.lossCount++;
              enemyZombie.winCount++;
              _triggerCooldown(myZombie);
            }
          }
        }
        ```
        
        ---
        
        ## Lesson ERC721 & Crypto-Collectibles
        
        ### Chapter 1: Tokens on Ethereum
        
        Let's talk about ***tokens***.
        
        If you've been in the Ethereum space for any amount of time, you've probably heard people talking about tokens — specifically ***ERC20 tokens***.
        
        A ***token*** on Ethereum is basically just a smart contract that follows some common rules — namely it implements a standard set of functions that all other token contracts share, such as `transferFrom(address _from, address _to, uint256 _amount)` and `balanceOf(address _owner)`.
        
        Internally the smart contract usually has a mapping, `mapping(address => uint256) balances`, that keeps track of how much balance each address has.
        
        So basically a token is just a contract that keeps track of who owns how much of that token, and some functions so those users can transfer their tokens to other addresses.
        
        ### Why does it matter?
        
        Since all ERC20 tokens share the same set of functions with the same names, they can all be interacted with in the same ways.
        
        This means if you build an application that is capable of interacting with one ERC20 token, it's also capable of interacting with any ERC20 token. That way more tokens can easily be added to your app in the future without needing to be custom coded. You could simply plug in the new token contract address, and boom, your app has another token it can use.
        
        One example of this would be an exchange. When an exchange adds a new ERC20 token, really it just needs to add another smart contract it talks to. Users can tell that contract to send tokens to the exchange's wallet address, and the exchange can tell the contract to send the tokens back out to users when they request a withdraw.
        
        The exchange only needs to implement this transfer logic once, then when it wants to add a new ERC20 token, it's simply a matter of adding the new contract address to its database.
        
        ### Other token standards
        
        ERC20 tokens are really cool for tokens that act like currencies. But they're not particularly useful for representing zombies in our zombie game.
        
        For one, zombies aren't divisible like currencies — I can send you 0.237 ETH, but transfering you 0.237 of a zombie doesn't really make sense.
        
        Secondly, all zombies are not created equal. Your Level 2 zombie "**Steve**" is totally not equal to my Level 732 zombie "**H4XF13LD MORRIS 💯💯😎💯💯**". (Not even close, *Steve*).
        
        There's another token standard that's a much better fit for crypto-collectibles like CryptoZombies — and they're called ***ERC721 tokens.***
        
        ***ERC721 tokens*** are **not** interchangeable since each one is assumed to be unique, and are not divisible. You can only trade them in whole units, and each one has a unique ID. So these are a perfect fit for making our zombies tradeable.
        
        > Note that using a standard like ERC721 has the benefit that we don't have to implement the auction or escrow logic within our contract that determines how players can trade / sell our zombies. If we conform to the spec, someone else could build an exchange platform for crypto-tradable ERC721 assets, and our ERC721 zombies would be usable on that platform. So there are clear benefits to using a token standard instead of rolling your own trading logic.
        > 
        
        ## Exercise
        
        We're going to dive into the ERC721 implementation in the next chapter. But first, let's set up our file structure for this lesson.
        
        We're going to store all the ERC721 logic in a contract called `ZombieOwnership`.
        
        1. Declare our `pragma` version at the top of the file (check previous lessons' files for the syntax).
        2. This file should `import` from `zombieattack.sol`.
        3. Declare a new contract, `ZombieOwnership`, that inherits from `ZombieAttack`. Leave the body of the contract empty for now
        
        Code
        
        ```solidity
        **pragma solidity >=0.5.0 <0.6.0;
        
        import "./zombieattack.sol";
        
        contract ZombieOwnership is ZombieAttack {
        
        }**
        ```
        
        ---
        
        # **Chapter 2: ERC721 Standard, Multiple Inheritance**
        
        Let's take a look at the ERC721 standard:
        
        ```
        contract ERC721 {
          event Transfer(address indexed _from, address indexed _to, uint256 indexed _tokenId);
          event Approval(address indexed _owner, address indexed _approved, uint256 indexed _tokenId);
        
          function balanceOf(address _owner) external view returns (uint256);
          function ownerOf(uint256 _tokenId) external view returns (address);
          function transferFrom(address _from, address _to, uint256 _tokenId) external payable;
          function approve(address _approved, uint256 _tokenId) external payable;
        }
        
        ```
        
        This is the list of methods we'll need to implement, which we'll be doing over the coming chapters in pieces.
        
        It looks like a lot, but don't get overwhelmed! We're here to walk you through it.
        
        ### Implementing a token contract
        
        When implementing a token contract, the first thing we do is copy the interface to its own Solidity file and import it, `import "./erc721.sol";`. Then we have our contract inherit from it, and we override each method with a function definition.
        
        But wait — `ZombieOwnership` is already inheriting from `ZombieAttack` — how can it also inherit from `ERC721`?
        
        Luckily in Solidity, your contract can inherit from multiple contracts as follows:
        
        ```
        contract SatoshiNakamoto is NickSzabo, HalFinney {
        // Omg, the secrets of the universe revealed!
        }
        
        ```
        
        As you can see, when using multiple inheritance, you just separate the multiple contracts you're inheriting from with a comma, `,`. In this case, our contract is inheriting from `NickSzabo`and `HalFinney`.
        
        Let's give it a try.
        
        ## Exercise
        
        We've already created `erc721.sol` with the interface above for you.
        
        1. Import `erc721.sol` into `zombieownership.sol`
        2. Declare that `ZombieOwnership` inherits from `ZombieAttack` AND `ERC721`
        
        Code
        
        ```solidity
        pragma solidity >=0.5.0 <0.6.0;
        
        import "./zombieattack.sol";
        import "./erc721.sol";
        
        // Declare ERC721 inheritance here
        contract ZombieOwnership is ZombieAttack, ERC721 {
        
        }
        ```
        
        ---
        
        ## Chapter 3: BalanceOf & ownerOf
        
        Great, let's dive into the ERC721 implementation!
        
        We've gone ahead and copied the empty shell of all the functions you'll be implementing in this lesson.
        
        In this chapter, we're going to implement the first two methods: `balanceOf` and `ownerOf`.
        
        # balanceOf
        
        ```
          function balanceOf(address _owner) external view returns (uint256 _balance);
        
        ```
        
        This function simply takes an `address`, and returns how many tokens that `address` owns.
        
        In our case, our "tokens" are Zombies. Do you remember where in our DApp we stored how many zombies an owner has?
        
        # ownerOf
        
        ```
          function ownerOf(uint256 _tokenId) external view returns (address _owner);
        
        ```
        
        This function takes a token ID (in our case, a Zombie ID), and returns the `address` of the person who owns it.
        
        Again, this is very straightforward for us to implement, since we already have a `mapping` in our DApp that stores this information. We can implement this function in one line, just a `return`statement.
        
        > Note: Remember, uint256 is equivalent to uint. We've been using uint in our code up until now, but we're using uint256 here because we copy/pasted from the spec.
        > 
        
        ## Exercise
        
        I'll leave it to you to figure out how to implement these 2 functions.
        
        Each function should simply be 1 line of code, a `return` statement. Take a look at our code from previous lessons to see where we're storing this data. If you can't figure it out, you can hit the "show me the answer" button for some help.
        
        1. Implement `balanceOf` to return the number of zombies `_owner` has.
        2. Implement `ownerOf` to return the address of whoever owns the zombie with ID `_tokenId`.
        
        Code
        
        ```solidity
        pragma solidity >=0.5.0 <0.6.0;
        
        import "./zombieattack.sol";
        import "./erc721.sol";
        
        contract ZombieOwnership is ZombieAttack, ERC721 {
        
          function balanceOf(address _owner) external view returns (uint256) {
             return ownerZombieCount[_owner];
          }
        
          function ownerOf(uint256 _tokenId) external view returns (address) {
             return zombieToOwner[_tokenId];
          }
        
          function transferFrom(address _from, address _to, uint256 _tokenId) external payable {
        
          }
        
          function approve(address _approved, uint256 _tokenId) external payable {
        
          }
        }
        ```
        
        ---
        
        ### Chapter 4:Refactoring
        
        Uh oh! We've just introduced an error in our code that will make it not compile. Did you notice it?
        
        In the previous chapter we defined a function called `ownerOf`. But if you recall from Lesson 4, we also created a `modifier` with the same name, `ownerOf`, in `zombiefeeding.sol`.
        
        If you tried compiling this code, the compiler would give you an error saying you can't have a modifier and a function with the same name.
        
        So should we just change the function name in `ZombieOwnership` to something else?
        
        No, we can't do that!!! Remember, we're using the ERC721 token standard, which means other contracts will expect our contract to have functions with these exact names defined. That's what makes these standards useful — if another contract knows our contract is ERC721-compliant, it can simply talk to us without needing to know anything about our internal implementation decisions.
        
        So that means we'll have to refactor our code from Lesson 4 to change the name of the `modifier` to something else.
        
        ## Exercise
        
        We're back in `zombiefeeding.sol`. We're going to change the name of our `modifier` from `ownerOf` to `onlyOwnerOf`.
        
        1. Change the name of the modifier definition to `onlyOwnerOf`
        2. Scroll down to the function `feedAndMultiply`, which uses this modifier. We'll need to change the name here as well.
        
        > Note: We also use this modifier in zombiehelper.sol and zombieattack.sol, but so we don't spend too much of this lesson refactoring, we've gone ahead and changed the modifier names in those files for you
        > 
        
        Code
        
        ```solidity
        pragma solidity >=0.5.0 <0.6.0;
        
        import "./zombiefactory.sol";
        
        contract KittyInterface {
          function getKitty(uint256 _id) external view returns (
            bool isGestating,
            bool isReady,
            uint256 cooldownIndex,
            uint256 nextActionAt,
            uint256 siringWithId,
            uint256 birthTime,
            uint256 matronId,
            uint256 sireId,
            uint256 generation,
            uint256 genes
          );
        }
        
        contract ZombieFeeding is ZombieFactory {
        
          KittyInterface kittyContract;
        
          // 1. Change modifier name to `onlyOwnerOf`
          modifier onlyownerOf(uint _zombieId) {
            require(msg.sender == zombieToOwner[_zombieId]);
            _;
          }
        
          function setKittyContractAddress(address _address) external onlyOwner {
            kittyContract = KittyInterface(_address);
          }
        
          function _triggerCooldown(Zombie storage _zombie) internal {
            _zombie.readyTime = uint32(now + cooldownTime);
          }
        
          function _isReady(Zombie storage _zombie) internal view returns (bool) {
              return (_zombie.readyTime <= now);
          }
        
          // 2. Change modifier name here as well
          function feedAndMultiply(uint _zombieId, uint _targetDna, string memory _species) internal onlyownerOf(_zombieId) {
            Zombie storage myZombie = zombies[_zombieId];
            require(_isReady(myZombie));
            _targetDna = _targetDna % dnaModulus;
            uint newDna = (myZombie.dna + _targetDna) / 2;
            if (keccak256(abi.encodePacked(_species)) == keccak256(abi.encodePacked("kitty"))) {
              newDna = newDna - newDna % 100 + 99;
            }
            _createZombie("NoName", newDna);
            _triggerCooldown(myZombie);
          }
        
          function feedOnKitty(uint _zombieId, uint _kittyId) public {
            uint kittyDna;
            (,,,,,,,,,kittyDna) = kittyContract.getKitty(_kittyId);
            feedAndMultiply(_zombieId, kittyDna, "kitty");
          }
        }
        ```
        
        ---
        
        # **Chapter 5: ERC721: Transfer Logic**
        
        Great, we've fixed the conflict!
        
        Now we're going to continue our ERC721 implementation by looking at transfering ownership from one person to another.
        
        Note that the ERC721 spec has 2 different ways to transfer tokens:
        
        `function transferFrom(address _from, address _to, uint256 _tokenId) external payable;`
        
        and
        
        `function approve(address _approved, uint256 _tokenId) external payable;`
        
        `function transferFrom(address _from, address _to, uint256 _tokenId) external payable;`
        
        1. The first way is the token's owner calls `transferFrom` with his `address` as the `_from`parameter, the `address` he wants to transfer to as the `_to` parameter, and the `_tokenId` of the token he wants to transfer.
        2. The second way is the token's owner first calls `approve` with the address he wants to transfer to, and the `_tokenID` . The contract then stores who is approved to take a token, usually in a `mapping (uint256 => address)`. Then, when the owner or the approved address calls `transferFrom`, the contract checks if that `msg.sender` is the owner or is approved by the owner to take the token, and if so it transfers the token to him.
        
        Notice that both methods contain the same transfer logic. In one case the sender of the token calls the `transferFrom` function; in the other the owner or the approved receiver of the token calls it.
        
        So it makes sense for us to abstract this logic into its own private function, `_transfer`, which is then called by `transferFrom`.
        
        ## Exercise
        
        Let's define the logic for `_transfer`.
        
        1. Define a function named `_transfer`. It will take 3 arguments, `address _from`, `address _to`, and `uint256 _tokenId`. It should be a `private` function.
        2. We have 2 mappings that will change when ownership changes: `ownerZombieCount`(which keeps track of how many zombies an owner has) and `zombieToOwner` (which keeps track of who owns what).
            
            The first thing our function should do is increment `ownerZombieCount` for the person **receiving** the zombie (`address _to`). Use `++` to increment.
            
        3. Next, we'll need to **decrease** the `ownerZombieCount` for the person **sending** the zombie (`address _from`). Use `-` to decrement.
        4. Lastly, we'll want to change `zombieToOwner` mapping for this `_tokenId` so it now points to `_to`.
        5. I lied, that wasn't the last step. There's one more thing we should do.
            
            The ERC721 spec includes a `Transfer` event. The last line of this function should fire `Transfer` with the correct information — check `erc721.sol` to see what arguments it's expecting to be called with and implement it here.
            
            Code
            
            ```solidity
            pragma solidity >=0.5.0 <0.6.0;
            
            import "./zombieattack.sol";
            import "./erc721.sol";
            
            contract ZombieOwnership is ZombieAttack, ERC721 {
            
              function balanceOf(address _owner) external view returns (uint256) {
                return ownerZombieCount[_owner];
              }
            
              function ownerOf(uint256 _tokenId) external view returns (address) {
                return zombieToOwner[_tokenId];
              }
            
              // Define _transfer() here
            
              function _transfer(address _from, address _to, uint256 _tokenId) private {
            			ownerZombieCount[_to]++;
            			ownerZombieCount[_from]--;
            			zombieToOwner[_tokenId] = _to;
            			emit Transfer(_from, _to, _tokenId);
              }
            **function transferFrom(address _from, address _to, uint256 _tokenId) external payable {
            }**
              function approve(address _approved, uint256 _tokenId) external payable {
              }
            }
            ```
            
            ---
            
            # **Chapter 6: ERC721: Transfer Cont'd**
            
            Great! That was the difficult part — now implementing the external `transferFrom`function will be easy, since our `_transfer`function already does almost all the heavy lifting.
            
            ## Exercise
            
            1. First, we want to make sure only the owner or the approved address of a token/zombie can transfer it. Let's define a mapping called `zombieApprovals`. It should map a `uint` to an `address`. This way, when someone that is not the owner calls `transferFrom` with a `_tokenId`, we can use this mapping to quickly look up if he is approved to take that token.
            2. Next, let's add a `require` statement to `transferFrom`. It should make sure that only the owner or the approved address of a token/zombie can transfer it.
            3. Lastly, don't forget to call `_transfer`.
            
            > Note: Checking that only the owner or the approved address of a token/zombie can transfer it means that at least one of these conditions must be true:
            > 
            
            > zombieToOwner for _tokenId is equal to msg.sender
            > 
            
            > or
            > 
            
            > zombieApprovals for _tokenId is equal to msg.sender
            > 
            
            Don't worry about filling in data in the `zombieApprovals` mapping, we'll do it in the next chapter.
            
            Code
            
            ```solidity
            pragma solidity >=0.5.0 <0.6.0;
            
            import "./zombieattack.sol";
            import "./erc721.sol";
            
            contract ZombieOwnership is ZombieAttack, ERC721 {
            
             mapping (uint => address) zombieApprovals;
            
              function balanceOf(address _owner) external view returns (uint256) {
                return ownerZombieCount[_owner];
              }
            
              function ownerOf(uint256 _tokenId) external view returns (address) {
                return zombieToOwner[_tokenId];
              }
            
              function _transfer(address _from, address _to, uint256 _tokenId) private {
                ownerZombieCount[_to]++;
                ownerZombieCount[_from]--;
                zombieToOwner[_tokenId] = _to;
                emit Transfer(_from, _to, _tokenId);
              }
            
              function transferFrom(address _from, address _to, uint256 _tokenId) external payable {
            	    
            require (zombieToOwner[_tokenId] == msg.sender || zombieApprovals[_tokenId] == msg.sender);
            		  _transfer(_from, _to, _tokenId);
            }
            
              function approve(address _approved, uint256 _tokenId) external payable {
            
              }
            
            }
            ```
            
        
        ---
        
        ### Chapter 7: ERC721: Approve
        
        Now, let's implement `approve`.
        
        Remember, with `approve` the transfer happens in 2 steps:
        
        1. You, the owner, call `approve` and give it the `_approved` address of the new owner, and the `_tokenId` you want them to take.
        2. The new owner calls `transferFrom` with the `_tokenId`. Next, the contract checks to make sure the new owner has been already approved, and then transfers them the token.
        
        Because this happens in 2 function calls, we need to use the `zombieApprovals` data structure to store who's been approved for what in between function calls.
        
        ### Exercise
        
        1. In the `approve` function, we want to make sure only the owner of the token can give someone approval to take it. So we need to add the `onlyOwnerOf`modifier to `approve`
        2. For the body of the function, set `zombieApprovals` for `_tokenId` equal to the `_approved` address
        
        Code
        
        ```solidity
        pragma solidity >=0.5.0 <0.6.0;
        
        import "./zombieattack.sol";
        import "./erc721.sol";
        
        contract ZombieOwnership is ZombieAttack, ERC721 {
        
          mapping (uint => address) zombieApprovals;
        
          function balanceOf(address _owner) external view returns (uint256) {
            return ownerZombieCount[_owner];
          }
        
          function ownerOf(uint256 _tokenId) external view returns (address) {
            return zombieToOwner[_tokenId];
          }
        
          function _transfer(address _from, address _to, uint256 _tokenId) private {
            ownerZombieCount[_to]++;
            ownerZombieCount[_from]--;
            zombieToOwner[_tokenId] = _to;
            emit Transfer(_from, _to, _tokenId);
          }
        
          function transferFrom(address _from, address _to, uint256 _tokenId) external payable {
            require (zombieToOwner[_tokenId] == msg.sender || zombieApprovals[_tokenId] == msg.sender);
            _transfer(_from, _to, _tokenId);
          }
        
          
          function approve(address _approved, uint256 _tokenId) external payable {
            function approve(address _approved, uint256 _tokenId) external payable onlyOwnerOf(_tokenId) {
              zombieApprovals[_tokenId] = _approved;
          }
        
        }
        ```
        
        ---
        
        ### Chapter 8: ERC721: Approve
        
        Great, we are almost done!
        
        There is one more thing to do- there's an `Approval` event in the ERC721 spec. So we should fire this event at the end of the `approve` function.
        
        ## Exercise
        
        1. Let's fire the `Approval` event. Take a look at the `erc721.sol` file for the arguments, and be sure to use `msg.sender` as `_owner`.
        
        Great, we have finished our ERC721 implementation!
        
    
    Code
    
    ```solidity
    pragma solidity >=0.5.0 <0.6.0;
    
    import "./zombieattack.sol";
    import "./erc721.sol";
    
    contract ZombieOwnership is ZombieAttack, ERC721 {
    
      mapping (uint => address) zombieApprovals;
    
      function balanceOf(address _owner) external view returns (uint256) {
        return ownerZombieCount[_owner];
      }
    
      function ownerOf(uint256 _tokenId) external view returns (address) {
        return zombieToOwner[_tokenId];
      }
    
      function _transfer(address _from, address _to, uint256 _tokenId) private {
        ownerZombieCount[_to]++;
        ownerZombieCount[_from]--;
        zombieToOwner[_tokenId] = _to;
        emit Transfer(_from, _to, _tokenId);
      }
    
      function transferFrom(address _from, address _to, uint256 _tokenId) external payable {
        require (zombieToOwner[_tokenId] == msg.sender || zombieApprovals[_tokenId] == msg.sender);
        _transfer(_from, _to, _tokenId);
      }
    
      function approve(address _approved, uint256 _tokenId) external payable onlyOwnerOf(_tokenId) {
        zombieApprovals[_tokenId] = _approved;
    		emit Approval(msg.sender, _approved, _tokenId);
      }
    
    }
    ```
    
    ---
    
    ### Chapter 9: Preventing Overflows
    
    Congratulations, that completes our ERC721 and ERC721x implementation!
    
    That wasn't so tough, was it? A lot of this Ethereum stuff sounds really complicated when you hear people talking about it, so the best way to understand it is to actually go through an implementation of it yourself.
    
    Keep in mind that this is only a minimal implementation. There are extra features we may want to add to our implementation, such as some extra checks to make sure users don't accidentally transfer their zombies to address `0` (which is called "burning" a token — basically it's sent to an address that no one has the private key of, essentially making it unrecoverable). Or to put some basic auction logic in the DApp itself. (Can you think of some ways we could implement that?)
    
    But we wanted to keep this lesson manageable, so we went with the most basic implementation. If you want to see an example of a more in-depth implementation**, you can take a look at the OpenZeppelin ERC721 contract after this tutorial.**
    
    ### Contract security enhancements: Overflows and Underflows
    
    We're going to look at one major security feature you should be aware of when writing smart contracts: Preventing overflows and underflows.
    
    What's an ***overflow***?
    
    Let's say we have a `uint8`, which can only have 8 bits. That means the largest number we can store is binary `11111111` (or in decimal, 2^8 - 1 = 255).
    
    Take a look at the following code. What is `number` equal to at the end?
    
    ```
    uint8 number = 255;
    number++;
    
    ```
    
    In this case, we've caused it to overflow — so `number` is counterintuitively now equal to `0`even though we increased it. (If you add 1 to binary `11111111`, it resets back to `00000000`, like a clock going from `23:59` to `00:00`).
    
    An underflow is similar, where if you subtract `1` from a `uint8` that equals `0`, it will now equal `255` (because `uint`s are unsigned, and cannot be negative).
    
    While we're not using `uint8` here, and it seems unlikely that a `uint256` will overflow when incrementing by `1` each time (2^256 is a really big number), it's still good to put protections in our contract so that our DApp never has unexpected behavior in the future.
    
    ### Using SafeMath
    
    To prevent this, OpenZeppelin has created a ***library*** called SafeMath that prevents these issues by default.
    
    But before we get into that... What's a library?
    
    A ***library*** is a special type of contract in Solidity. One of the things it is useful for is to attach functions to native data types.
    
    For example, with the SafeMath library, we'll use the syntax `using SafeMath for uint256`. The SafeMath library has 4 functions — `add`, `sub`, `mul`, and `div`. And now we can access these functions from `uint256`as follows:
    
    ```
    using SafeMath for uint256;
    
    uint256 a = 5;
    uint256 b = a.add(3);// 5 + 3 = 8uint256 c = a.mul(2);// 5 * 2 = 10
    ```
    
    We'll look at what these functions do in the next chapter, but for now let's add the SafeMath library to our contract.
    
    ### Exercise
    
    We've already included OpenZeppelin's `SafeMath` library for you in `safemath.sol`. You can take a quick peek at the code now if you want to, but we'll be looking at it in depth in the next chapter.
    
    First let's tell our contract to use SafeMath. We'll do this in ZombieFactory, our very base contract — that way we can use it in any of the sub-contracts that inherit from this one.
    
    1. Import `safemath.sol` into `zombiefactory.sol`.
    2. Add the declaration `using SafeMath for uint256;`.
    
    Code
    
    ```solidity
    pragma solidity >=0.5.0 <0.6.0;
    
    import "./ownable.sol";
    import "./safemath.sol";
    
    contract ZombieFactory is Ownable {
    
      using SafeMath for uint256;
    
      event NewZombie(uint zombieId, string name, uint dna);
    
      uint dnaDigits = 16;
      uint dnaModulus = 10 ** dnaDigits;
      uint cooldownTime = 1 days;
    
      struct Zombie {
        string name;
        uint dna;
        uint32 level;
        uint32 readyTime;
        uint16 winCount;
        uint16 lossCount;
      }
    
      Zombie[] public zombies;
    
      mapping (uint => address) public zombieToOwner;
      mapping (address => uint) ownerZombieCount;
    
      function _createZombie(string memory _name, uint _dna) internal {
        uint id = zombies.push(Zombie(_name, _dna, 1, uint32(now + cooldownTime), 0, 0)) - 1;
        zombieToOwner[id] = msg.sender;
        ownerZombieCount[msg.sender]++;
        emit NewZombie(id, _name, _dna);
      }
    
      function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
      }
    
      function createRandomZombie(string memory _name) public {
        require(ownerZombieCount[msg.sender] == 0);
        uint randDna = _generateRandomDna(_name);
        randDna = randDna - randDna % 100;
        _createZombie(_name, randDna);
      }
    
    }
    ```
    
    ---
    
    ### Chapter 10: SafeMath Part 2
    
    Let's take a look at the code behind SafeMath:
    
    ```solidity
    library SafeMath {
    
      function mul(uint256 a, uint256 b) internal pure returns (uint256) {
        if (a == 0) {
          return 0;
        }
        uint256 c = a * b;
        assert(c / a == b);
        return c;
      }
    
      function div(uint256 a, uint256 b) internal pure returns (uint256) {
    // assert(b > 0); // Solidity automatically throws when dividing by 0
        uint256 c = a / b;
    // assert(a == b * c + a % b); // There is no case in which this doesn't holdreturn c;
      }
    
      function sub(uint256 a, uint256 b) internal pure returns (uint256) {
        assert(b <= a);
        return a - b;
      }
    
      function add(uint256 a, uint256 b) internal pure returns (uint256) {
        uint256 c = a + b;
        assert(c >= a);
        return c;
      }
    }
    
    ```
    
    First we have the `library` keyword — libraries are similar to `contract`s but with a few differences. For our purposes, libraries allow us to use the `using` keyword, which automatically tacks on all of the library's methods to another data type:
    
    ```
    using SafeMath for uint;
    // now we can use these methods on any uint
    uint test = 2;
    test = test.mul(3); // test now equals 6
    test = test.add(5); // test now equals 11
    
    ```
    
    Note that the `mul` and `add` functions each require 2 arguments, but when we declare `using SafeMath for uint`, the `uint` we call the function on (`test`) is automatically passed in as the first argument.
    
    Let's look at the code behind `add` to see what SafeMath does:
    
    ```
    function add(uint256 a, uint256 b) internal pure returns (uint256) {
      uint256 c = a + b;
      assert(c >= a);
      return c;
    }
    
    ```
    
    Basically `add` just adds 2 `uint`s like `+`, but it also contains an `assert` statement to make sure the sum is greater than `a`. This protects us from overflows.
    
    `assert` is similar to `require`, where it will throw an error if false. The difference between `assert` and `require` is that `require`will refund the user the rest of their gas when a function fails, whereas `assert` will not. So most of the time you want to use `require` in your code; `assert` is typically used when something has gone horribly wrong with the code (like a `uint` overflow).
    
    So, simply put, SafeMath's `add`, `sub`, `mul`, and `div` are functions that do the basic 4 math operations, but throw an error if an overflow or underflow occurs.
    
    ### Using SafeMath in our code.
    
    To prevent overflows and underflows, we can look for places in our code where we use `+`, `-`, `*`, or `/`, and replace them with `add`, `sub`, `mul`, `div`.
    
    Ex. Instead of doing:
    
    ```
    myUint++;
    ```
    
    We would do:
    
    ```
    myUint = myUint.add(1);
    ```
    
    ### Exercise
    
    We have 2 places in `ZombieOwnership` where we used math operations. Let's swap them out with SafeMath methods.
    
    1. Replace `++` with a SafeMath method.
    2. Replace `-` with a SafeMath method.
    
    Code
    
    ```solidity
    pragma solidity >=0.5.0 <0.6.0;
    
    import "./zombieattack.sol";
    import "./erc721.sol";
    import "./safemath.sol";
    
    contract ZombieOwnership is ZombieAttack, ERC721 {
    
      using SafeMath for uint256;
    
      mapping (uint => address) zombieApprovals;
    
      function balanceOf(address _owner) external view returns (uint256) {
        return ownerZombieCount[_owner];
      }
    
      function ownerOf(uint256 _tokenId) external view returns (address) {
        return zombieToOwner[_tokenId];
      }
    
      function _transfer(address _from, address _to, uint256 _tokenId) private {
       
    		ownerZombieCount[_to] = ownerZombieCount[_to].add(1); 
        ownerZombieCount[_from] = ownerZombieCount[_from].sub(1);
        zombieToOwner[_tokenId] = _to;
        emit Transfer(_from, _to, _tokenId);
      }
    
      function transferFrom(address _from, address _to, uint256 _tokenId) external payable {
        require (zombieToOwner[_tokenId] == msg.sender || zombieApprovals[_tokenId] == msg.sender);
        _transfer(_from, _to, _tokenId);
      }
    
      function approve(address _approved, uint256 _tokenId) external payable onlyOwnerOf(_tokenId) {
        zombieApprovals[_tokenId] = _approved;
        emit Approval(msg.sender, _approved, _tokenId);
      }
    
    }
    ```
    
    ---
    
    ### Chapter 11: SafeMath Part 3
    
    Great, now our ERC721 implementation is safe from overflows & underflows!
    
    Going back through the code we wrote in previous lessons, there's a few other places in our code that could be vulnerable to overflows or underflows.
    
    For example, in ZombieAttack we have:
    
    ```
    myZombie.winCount++;myZombie.level++;enemyZombie.lossCount++;
    ```
    
    We should prevent overflows here as well just to be safe. (It's a good idea in general to just use SafeMath instead of the basic math operations. Maybe in a future version of Solidity these will be implemented by default, but for now we have to take extra security precautions in our code).
    
    However we have a slight problem — `winCount` and `lossCount` are `uint16`s, and `level` is a `uint32`. So if we use SafeMath's `add` method with these as arguments, it won't actually protect us from overflow since it will convert these types to `uint256`:
    
    ```
    function add(uint256 a, uint256 b) internal pure returns (uint256){
      uint256 c = a + b;
      assert(c >= a);
      return c;
    }// If we call `.add` on a `uint8`, it gets converted to a `uint256`.// So then it won't overflow at 2^8, since 256 is a valid `uint256`.
    ```
    
    This means we're going to need to implement 2 more libraries to prevent overflow/underflows with our `uint16`s and `uint32`s. We can call them `SafeMath16` and `SafeMath32`.
    
    The code will be exactly the same as SafeMath, except all instances of `uint256` will be replaced with `uint32` or `uint16`.
    
    We've gone ahead and implemented that code for you — go ahead and look at `safemath.sol` to see the code.
    
    Now we need to implement it in ZombieFactory.
    
    ### Exercise
    
    Assignment:
    
    1. Declare that we're using `SafeMath32` for `uint32`.
    2. Declare that we're using `SafeMath16` for `uint16`.
    3. There's one more line of code in ZombieFactory where we should use a SafeMath method. We've left a comment to indicate where
    
    Code
    
    ```solidity
    pragma solidity >=0.5.0 <0.6.0;
    
    import "./ownable.sol";
    import "./safemath.sol";
    
    contract ZombieFactory is Ownable {
    
      using SafeMath for uint256;
      using SafeMath32 for uint32;
      using SafeMath16 for uint16;
    
      event NewZombie(uint zombieId, string name, uint dna);
    
      uint dnaDigits = 16;
      uint dnaModulus = 10 ** dnaDigits;
      uint cooldownTime = 1 days;
    
      struct Zombie {
        string name;
        uint dna;
        uint32 level;
        uint32 readyTime;
        uint16 winCount;
        uint16 lossCount;
      }
    
      Zombie[] public zombies;
    
      mapping (uint => address) public zombieToOwner;
      mapping (address => uint) ownerZombieCount;
    
      function _createZombie(string memory _name, uint _dna) internal {
        // Note: We chose not to prevent the year 2038 problem... So don't need
        // worry about overflows on readyTime. Our app is screwed in 2038 anyway ;)
        uint id = zombies.push(Zombie(_name, _dna, 1, uint32(now + cooldownTime), 0, 0)) - 1;
        zombieToOwner[id] = msg.sender;
        // 3. Let's use SafeMath's `add` here:
        ownerZombieCount[msg.sender]= ownerZombieCount[msg.sender].add(1);
        emit NewZombie(id, _name, _dna);
      }
    
      function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
      }
    
      function createRandomZombie(string memory _name) public {
        require(ownerZombieCount[msg.sender] == 0);
        uint randDna = _generateRandomDna(_name);
        randDna = randDna - randDna % 100;
        _createZombie(_name, randDna);
      }
    
    }
    ```
    

---

### Chapter 12: SafeMath part 4

Great, now we can implement SafeMath on all the types of `uint`s we used in our DApp!

Let's fix all those potential issues in `ZombieAttack`. (There was also one `zombies[_zombieId].level++;` that needed to be fixed in `ZombieHelper`, but we've taken care of that one for you so we don't take an extra chapter to do so 😉).

### Exercise

Go ahead and implement SafeMath methods on all the `++` increments in `ZombieAttack`. We've left comments in the code to make them easy to find.

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombiehelper.sol";

contract ZombieAttack is ZombieHelper {
  uint randNonce = 0;
  uint attackVictoryProbability = 70;

  function randMod(uint _modulus) internal returns(uint) {
    // Here's one!
    randNonce = randNonce.add(1);
    return uint(keccak256(abi.encodePacked(now, msg.sender, randNonce))) % _modulus;
  }

  function attack(uint _zombieId, uint _targetId) external onlyOwnerOf(_zombieId) {
    Zombie storage myZombie = zombies[_zombieId];
    Zombie storage enemyZombie = zombies[_targetId];
    uint rand = randMod(100);
    if (rand <= attackVictoryProbability) {
      // Here's 3 more!
      myZombie.winCount = myZombie.winCount.add(1);
      myZombie.level = myZombie.level.add(1);
      enemyZombie.lossCount = enemyZombie.lossCount.add(1);
      feedAndMultiply(_zombieId, enemyZombie.dna, "zombie");
    } else {
      // ...annnnd another 2!
      myZombie.lossCount = myZombie.lossCount.add(1);
      enemyZombie.winCount = enemyZombie.winCount(1);
      _triggerCooldown(myZombie);
    }
  }
}
```

---

### Chapter 13: Comments

The Solidity code for our zombie game is finally finished!

In the next lessons, we'll look at how to deploy the code to Ethereum, and how to interact with it with Web3.js.

But one final thing before we let you go in Lesson 5: Let's talk about **commenting your cod**

## **Syntax for comments**

Commenting in Solidity is just like JavaScript. You've already seen some examples of single line comments throughout the CryptoZombies lessons:

```
// This is a single-line comment. It's kind of like a note to self (or to others)

```

Just add double `//` anywhere and you're commenting. It's so easy that you should do it all the time.

But I hear you — sometimes a single line is not enough. You are born a writer, after all!

Thus we also have multi-line comments:

```
contract CryptoZombies {
/* This is a multi-lined comment. I'd like to thank all of you
    who have taken your time to try this programming course.
    I know it's free to all of you, and it will stay free
    forever, but we still put our heart and soul into making
    this as good as it can be.

    Know that this is still the beginning of Blockchain development.
    We've come very far but there are so many ways to make this
    community better. If we made a mistake somewhere, you can
    help us out and open a pull request here:
    https://github.com/loomnetwork/cryptozombie-lessons

    Or if you have some ideas, comments, or just want to say
    hi - drop by our Telegram community at https://t.me/loomnetworkdev
  */
}

```

In particular, it's good practice to comment your code to explain the expected behavior of every function in your contract. This way another developer (or you, after a 6 month hiatus from a project!) can quickly skim and understand at a high level what your code does without having to read the code itself.

The standard in the Solidity community is to use a format called ***natspec***, which looks like this:

```
/// @title A contract for basic math operations/// @author H4XF13LD MORRIS 💯💯😎💯💯/// @notice For now, this contract just adds a multiply function
contract Math {
/// @notice Multiplies 2 numbers together/// @param x the first uint./// @param y the second uint./// @return z the product of (x * y)/// @dev This function does not currently check for overflowsfunction multiply(uint x, uint y) returns (uint z) {
// This is just a normal comment, and won't get picked up by natspec
    z = x * y;
  }
}

```

`@title` and `@author` are straightforward.

`@notice` explains to a **user** what the contract / function does. `@dev` is for explaining extra details to developers.

`@param` and `@return` are for describing what each parameter and return value of a function are for.

Note that you don't always have to use all of these tags for every function — all tags are optional. But at the very least, leave a `@dev`note explaining what each function does.

### Exercise

If you haven't noticed by now, the CryptoZombies answer-checker ignores comments when it checks your answers. So we can't actually check your natspec code for this chapter ;)

However, by now you're a Solidity whiz — we're just going to assume you've got this!

Give it a try anyway, and try adding some natspec tags to `ZombieOwnership`:

1. `@title` — E.g. A contract that manages transfering zombie ownership
2. `@author` — Your name!
3. `@dev` — E.g. Compliant with OpenZeppelin's implementation of the ERC721 spec draft

Code

```solidity
pragma solidity >=0.5.0 <0.6.0;

import "./zombieattack.sol";
import "./erc721.sol";
import "./safemath.sol";

/// TODO: Replace this with natspec descriptions
contract ZombieOwnership is ZombieAttack, ERC721 {

  using SafeMath for uint256;

  mapping (uint => address) zombieApprovals;

  function balanceOf(address _owner) external view returns (uint256) {
    return ownerZombieCount[_owner];
  }

  function ownerOf(uint256 _tokenId) external view returns (address) {
    return zombieToOwner[_tokenId];
  }

  function _transfer(address _from, address _to, uint256 _tokenId) private {
    ownerZombieCount[_to] = ownerZombieCount[_to].add(1);
    ownerZombieCount[msg.sender] = ownerZombieCount[msg.sender].sub(1);
    zombieToOwner[_tokenId] = _to;
    emit Transfer(_from, _to, _tokenId);
  }

  function transferFrom(address _from, address _to, uint256 _tokenId) external payable {
    require (zombieToOwner[_tokenId] == msg.sender || zombieApprovals[_tokenId] == msg.sender);
    _transfer(_from, _to, _tokenId);
  }

  function approve(address _approved, uint256 _tokenId) external payable onlyOwnerOf(_tokenId) {
    zombieApprovals[_tokenId] = _approved;
    emit Approval(msg.sender, _approved, _tokenId);
  }

}
```

---

### Chapter 14: Wrapping it up

Congratulations! That concludes Lesson 5.

As a reward, we've transferred you your very own Level 10 **H4XF13LD MORRIS 💯💯😎💯💯** zombie!

(Omg, the legendary **H4XF13LD MORRIS 💯💯😎💯💯** zombie!!!!111)

Now you have 4 zombies in your army.

Before you move on, you have the option to rename any of them if you'd like by clicking on them to the right and entering a new name. (Though I don't know why you would ever want to rename **H4XF13LD MORRIS 💯💯😎💯💯**, clearly the best name ever).

## **Let's recap:**

In this lesson we learned about:

- Tokens, the ERC721 standard, and tradable assets/zombies
- Libraries and how to use them
- How to prevent overflows and underflows using the SafeMath library
- Commenting your code and the natspec standard

This lesson concludes our game's Solidity code! (For now — we may add even more lessons in the future).

In the next 2 lessons, we're going to look at how to deploy your contracts and interact with them using ***web3.js*** (so you can build a front-end for your DApp).

Go ahead and rename any of your zombies if you like, then proceed to the next chapter to complete the lesson.

---

## Lesson 6: App Front-ends & Web3.js

### Chapter 1: intro to Web3.js

By completing Lesson 5, our zombie DApp is now complete. Now we're going to create a basic web page where your users can interact with it.

To do this, we're going to use a JavaScript library from the Ethereum Foundation called ***Web3.js***.

## **What is Web3.js?**

Remember, the Ethereum network is made up of nodes, with each containing a copy of the blockchain. When you want to call a function on a smart contract, you need to query one of these nodes and tell it:

1. The address of the smart contract
2. The function you want to call, and
3. The variables you want to pass to that function.

Ethereum nodes only speak a language called ***JSON-RPC***, which isn't very human-readable. A query to tell the node you want to call a function on a contract looks something like this:

```
// Yeah... Good luck writing all your function calls this way!
// Scroll right ==>
{"jsonrpc":"2.0","method":"eth_sendTransaction","params":[{"from":"0xb60e8dd61c5d32be8058bb8eb970870f07233155","to":"0xd46e8dd67c5d32be8058bb8eb970870f07244567","gas":"0x76c0","gasPrice":"0x9184e72a000","value":"0x9184e72a","data":"0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"}],"id":1}

```

Luckily, Web3.js hides these nasty queries below the surface, so you only need to interact with a convenient and easily readable JavaScript interface.

Instead of needing to construct the above query, calling a function in your code will look something like this:

```
CryptoZombies.methods.createRandomZombie("Vitalik Nakamoto 🤔")
  .send({ from: "0xb60e8dd61c5d32be8058bb8eb970870f07233155", gas: "3000000" })

```

We'll explain the syntax in detail over the next few chapters, but first let's get your project set up with Web3.js.

## **Getting started**

Depending on your project's workflow, you can add Web3.js to your project using most package tools:

```
// Using NPM
npm install web3

// Using Yarn
yarn add web3

// Using Bower
bower install web3

// ...etc.

```

Or you can simply download the minified `.js`file from [github](https://github.com/ChainSafe/web3.js/blob/1.x/dist/web3.min.js) and include it in your project:

```
<script language="javascript" type="text/javascript" src="web3.min.js"></script>

```

Since we don't want to make too many assumptions about your development environment and what package manager you use, for this tutorial we're going to simply include Web3 in our project using a script tag as above.

### Exercise

We've created a shell of an HTML project file for you, `index.html`. Let's assume we have a copy of `web3.min.js` in the same folder as `index.html`.

1. Go ahead and copy/paste the script tag above into our project so we can use `web3.js`

Code

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>CryptoZombies front-end</title>
    <script language="javascript" type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script language="javascript" type="text/javascript" src="web3.min.js"></script>
  </head>
  <body>

  </body>
</html>
```

---

### Chapter 2: Web3 Providers

Great! Now that we have Web3.js in our project, let's get it initialized and talking to the blockchain.

The first thing we need is a ***Web3 Provider***.

Remember, Ethereum is made up of ***nodes***that all share a copy of the same data. Setting a Web3 Provider in Web3.js tells our code **which node** we should be talking to handle our reads and writes. It's kind of like setting the URL of the remote web server for your API calls in a traditional web app.

You could host your own Ethereum node as a provider. However, there's a third-party service that makes your life easier so you don't need to maintain your own Ethereum node in order to provide a DApp for your users — ***Infura***.

## **Infura**

[Infura](https://infura.io/) is a service that maintains a set of Ethereum nodes with a caching layer for fast reads, which you can access for free through their API. Using Infura as a provider, you can reliably send and receive messages to/from the Ethereum blockchain without needing to set up and maintain your own node.

You can set up Web3 to use Infura as your web3 provider as follows:

```
var web3 = new Web3(new Web3.providers.WebsocketProvider("wss://mainnet.infura.io/ws"));

```

However, since our DApp is going to be used by many users — and these users are going to WRITE to the blockchain and not just read from it — we'll need a way for these users to sign transactions with their private key.

> Note: Ethereum (and blockchains in general) use a public / private key pair to digitally sign transactions. Think of it like an extremely secure password for a digital signature. That way if I change some data on the blockchain, I can prove via my public key that I was the one who signed it — but since no one knows my private key, no one can forge a transaction for me.
> 

Cryptography is complicated, so unless you're a security expert and you really know what you're doing, it's probably not a good idea to try to manage users' private keys yourself in our app's front-end.

But luckily you don't need to — there are already services that handle this for you. The most popular of these is ***Metamask***.

## **Metamask**

[Metamask](https://metamask.io/) is a browser extension for Chrome and Firefox that lets users securely manage their Ethereum accounts and private keys, and use these accounts to interact with websites that are using Web3.js. (If you haven't used it before, you'll definitely want to go and install it — then your browser is Web3 enabled, and you can now interact with any website that communicates with the Ethereum blockchain!).

And as a developer, if you want users to interact with your DApp through a website in their web browser (like we're doing with our CryptoZombies game), you'll definitely want to make it Metamask-compatible.

> Note: Metamask uses Infura's servers under the hood as a web3 provider, just like we did above — but it also gives the user the option to choose their own web3 provider. So by using Metamask's web3 provider, you're giving the user a choice, and it's one less thing you have to worry about in your app.
> 

## **Using Metamask's web3 provider**

Metamask injects their web3 provider into the browser in the global JavaScript object `web3`. So your app can check to see if `web3`exists, and if it does use `web3.currentProvider` as its provider.

Here's some template code provided by Metamask for how we can detect to see if the user has Metamask installed, and if not tell them they'll need to install it to use our app:

```
window.addEventListener('load', function() {

// Checking if Web3 has been injected by the browser (Mist/MetaMask)if (typeof web3 !== 'undefined') {
// Use Mist/MetaMask's provider
    web3js = new Web3(web3.currentProvider);
  } else {
// Handle the case where the user doesn't have web3. Probably// show them a message telling them to install Metamask in// order to use our app.
  }

// Now you can start your app & access web3js freely:
  startApp()

})

```

You can use this boilerplate code in all the apps you create in order to require users to have Metamask to use your DApp.

> Note: There are other private key management programs your users might be using besides MetaMask, such as the web browser Mist. However, they all implement a common pattern of injecting the variable web3, so the method we describe here for detecting the user's web3 provider will work for these as well.
> 

### Exercise

We've created some empty script tags before the closing `</body>` tag in our HTML file. We can write our JavaScript code for this lesson here.

1. Go ahead and copy/paste the template code from above for detecting Metamask. It's the block that starts with `window.addEventListener`.

Code

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>CryptoZombies front-end</title>
    <script language="javascript" type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script language="javascript" type="text/javascript" src="web3.min.js"></script>
  </head>
  <body>

    <script>
  window.addEventListener('load', function() {

if (typeof web3! == 'undefined') {

web3js = new Web3(web3.currentProvider);
} else {

}

startApp()

      })

    </script>
  </body>
</html>
```

---

### Chapter 3: Talking to contracts

Now that we've initialized Web3.js with MetaMask's Web3 provider, let's set it up to talk to our smart contract.

Web3.js will need 2 things to talk to your contract: its ***address*** and its ***ABI***.

## **Contract Address**

After you finish writing your smart contract, you will compile it and deploy it to Ethereum. We're going to cover **deployment** in the **next lesson**, but since that's quite a different process from writing code, we've decided to go out of order and cover Web3.js first.

After you deploy your contract, it gets a fixed address on Ethereum where it will live forever. If you recall from Lesson 2, the address of the CryptoKitties contract on Ethereum mainnet is `0x06012c8cf97BEaD5deAe237070F9587f8E7A266d`.

You'll need to copy this address after deploying in order to talk to your smart contract.

## **Contract ABI**

The other thing Web3.js will need to talk to your contract is its ***ABI***.

ABI stands for Application Binary Interface. Basically it's a representation of your contracts' methods in JSON format that tells Web3.js how to format function calls in a way your contract will understand.

When you compile your contract to deploy to Ethereum (which we'll cover in Lesson 7), the Solidity compiler will give you the ABI, so you'll need to copy and save this in addition to the contract address.

Since we haven't covered deployment yet, for this lesson we've compiled the ABI for you and put it in a file named `cryptozombies_abi.js`, stored in variable called `cryptoZombiesABI`.

If we include `cryptozombies_abi.js` in our project, we'll be able to access the CryptoZombies ABI using that variable.

## **Instantiating a Web3.js Contract**

Once you have your contract's address and ABI, you can instantiate it in Web3 as follows:

```
// Instantiate myContract
var myContract = new web3js.eth.Contract(myABI, myContractAddress);

```

### Exercise

1. In the `<head>` of our document, include another script tag for `cryptozombies_abi.js` so we can import the ABI definition into our project.
2. At the beginning of our `<script>` tag in the `<body>`, declare a `var` named `cryptoZombies`, but don't set it equal to anything. Later we'll use this variable to store our instantiated contract.
3. Next, create a `function` named `startApp()`. We'll fill in the body in the next 2 steps.
4. The first thing `startApp()` should do is declare a `var` named `cryptoZombiesAddress` and set it equal to the string `"YOUR_CONTRACT_ADDRESS"`(this is the address of the CryptoZombies contract on mainnet).
5. Lastly, let's instantiate our contract. Set `cryptoZombies` equal to a new `web3js.eth.Contract` like we did in the example code above. (Using `cryptoZombiesABI`, which gets imported with our script tag, and `cryptoZombiesAddress` from above).

Code

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>CryptoZombies front-end</title>
    <script language="javascript" type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script language="javascript" type="text/javascript" src="web3.min.js"></script>
    <script language="javascript" type="text/javascript" src="cryptozombies_abi.js"></script>
  </head>
  <body>

    <script>
       var cryptoZombies;

				function startApp() {
						var cryptoZombiesAddress = "YOUR_CONTRACT_ADDRESS";
						cryptoZombies = new web3js.eth.Contract(cryptoZombiesABI, cryptoZombiesAddress);
							}

      window.addEventListener('load', function() {

        // Checking if Web3 has been injected by the browser (Mist/MetaMask)
        if (typeof web3 !== 'undefined') {
          // Use Mist/MetaMask's provider
          web3js = new Web3(web3.currentProvider);
        } else {
          // Handle the case where the user doesn't have Metamask installed
          // Probably show them a message prompting them to install Metamask
        }

        // Now you can start your app & access web3 freely:
        startApp()

      })
    </script>
  </body>
</html>
```

---

### Chapter 4: Calling Contract Functions

Our contract is all set up! Now we can use Web3.js to talk it.

Web3.js has two methods we will use to call functions on our contract: call and send.

### Call

`call` is used for `view` and `pure` functions. It only runs on the local node, and won't create a transaction on the blockchain.

> Review: view and pure functions are read-only and don't change state on the blockchain. They also don't cost any gas, and the user won't be prompted to sign a transaction with MetaMask.
> 

Using Web3.js, you would `call` a function named `myMethod` with the parameter `123` as follows:

```
myContract.methods.myMethod(123).call()

```

### Send

`send` will create a transaction and change data on the blockchain. You'll need to use `send` for any functions that aren't `view` or `pure`.

> Note: sending a transaction will require the user to pay gas, and will pop up their Metamask to prompt them to sign a transaction. When we use Metamask as our web3 provider, this all happens automatically when we call send(), and we don't need to do anything special in our code. Pretty cool!
> 

Using Web3.js, you would `send` a transaction calling a function named `myMethod` with the parameter `123` as follows:

```
myContract.methods.myMethod(123).send()

```

The syntax is almost identical to `call()`.

## **Getting Zombie Data**

Now let's look at a real example of using `call` to access data on our contract.

Recall that we made our array of zombies `public`:

```
Zombie[] public zombies;
```

In Solidity, when you declare a variable `public`, it automatically creates a public "getter" function with the same name. So if you wanted to look up the zombie with id `15`, you would call it as if it were a function: `zombies(15)`.

Here's how we would write a JavaScript function in our front-end that would take a zombie id, query our contract for that zombie, and return the result:

> Note: All the code examples we're using in this lesson are using version 1.0 of Web3.js, which uses promises instead of callbacks. Many other tutorials you'll see online are using an older version of Web3.js. The syntax changed a lot with version 1.0, so if you're copying code from other tutorials, make sure they're using the same version as you!
> 

```
function getZombieDetails(id) {
  return cryptoZombies.methods.zombies(id).call()
}

// Call the function and do something with the result:
getZombieDetails(15)
.then(function(result) {
  console.log("Zombie 15: " + JSON.stringify(result));
});

```

Let's walk through what's happening here.

`cryptoZombies.methods.zombies(id).call()` will communicate with the Web3 provider node and tell it to return the zombie with index `id` from `Zombie[] public zombies` on our contract.

Note that this is **asynchronous**, like an API call to an external server. So Web3 returns a promise here. (If you're not familiar with JavaScript promises... Time to do some additional homework before continuing!)

Once the promise resolves (which means we got an answer back from the web3 provider), our example code continues with the `then`statement, which logs `result` to the console.

`result` will be a JavaScript object that looks like this:

```
{
  "name": "H4XF13LD MORRIS'S COOLER OLDER BROTHER",
  "dna": "1337133713371337",
  "level": "9999",
  "readyTime": "1522498671",
  "winCount": "999999999",
  "lossCount": "0"// Obviously.
}

```

We could then have some front-end logic to parse this object and display it in a meaningful way on the front-end.

### Exercise

We've gone ahead and copied `getZombieDetails` into the code for you.

1. Let's create a similar function for `zombieToOwner`. If you recall from `ZombieFactory.sol`, we had a mapping that looked like:
    
    ```
    mapping (uint => address) public zombieToOwner;
    
    ```
    
    Define a JavaScript function called `zombieToOwner`. Similar to `getZombieDetails` above, it will take an `id` as a parameter, and will return a Web3.js `call` to `zombieToOwner` on our contract.
    
2. Below that, create a third function for `getZombiesByOwner`. If you recall from `ZombieHelper.sol`, the function definition looked like this:
    
    ```
    function getZombiesByOwner(address _owner)
    
    ```
    
    Our function `getZombiesByOwner` will take `owner` as a parameter, and return a Web3.js `call` to `getZombiesByOwner`.
    

Code

```solidity
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>CryptoZombies front-end</title>
    <script language="javascript" type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script language="javascript" type="text/javascript" src="web3.min.js"></script>
    <script language="javascript" type="text/javascript" src="cryptozombies_abi.js"></script>
  </head>
  <body>

    <script>
      var cryptoZombies;

      function startApp() {
        var cryptoZombiesAddress = "YOUR_CONTRACT_ADDRESS";
        cryptoZombies = new web3js.eth.Contract(cryptoZombiesABI, cryptoZombiesAddress);
      }

      function getZombieDetails(id) {
        return cryptoZombies.methods.zombies(id).call();
      }

       function zombieToOwner(id) {
        return cryptoZombies.methods.zombieToOwner(id).call();
      }

	     function getZombiesByOwner(owner) {
        return cryptoZombies.methods.getZombiesByOwner(owner).call();
      }

      window.addEventListener('load', function() {

        // Checking if Web3 has been injected by the browser (Mist/MetaMask)
        if (typeof web3 !== 'undefined') {
          // Use Mist/MetaMask's provider
          web3js = new Web3(web3.currentProvider);
        } else {
          // Handle the case where the user doesn't have Metamask installed
          // Probably show them a message prompting them to install Metamask
        }

        // Now you can start your app & access web3 freely:
        startApp()

      })
    </script>
  </body>
</html>
```

---

### Chapter 5: Metamask & Accounts

Awesome! You've successfully written front-end code to interact with your first smart contract.

Now let's put some pieces together — let's say we want our app's homepage to display a user's entire zombie army.

Obviously we'd first need to use our function `getZombiesByOwner(owner)` to look up all the IDs of zombies the current user owns.

But our Solidity contract is expecting `owner`to be a Solidity `address`. How can we know the address of the user using our app?

## **Getting the user's account in MetaMask**

MetaMask allows the user to manage multiple accounts in their extension.

We can see which account is currently active on the injected `web3` variable via:

```
var userAccount = web3.eth.accounts[0]

```

Because the user can switch the active account at any time in MetaMask, our app needs to monitor this variable to see if it has changed and update the UI accordingly. For example, if the user's homepage displays their zombie army, when they change their account in MetaMask, we'll want to update the page to show the zombie army for the new account they've selected.

We can do that with a `setInterval` loop as follows:

```
var accountInterval = setInterval(function() {
  // Check if account has changed
  if (web3.eth.accounts[0] !== userAccount) {
    userAccount = web3.eth.accounts[0];
    // Call some function to update the UI with the new account
    updateInterface();
  }
}, 100);

```

What this does is check every 100 milliseconds to see if `userAccount` is still equal `web3.eth.accounts[0]` (i.e. does the user still have that account active). If not, it reassigns `userAccount` to the currently active account, and calls a function to update the display.

### Exercise

Let's make it so our app will display the user's zombie army when the page first loads, and monitor the active account in MetaMask to refresh the display if it changes.

1. Declare a `var` named `userAccount`, but don't assign it to anything.
2. At the end of `startApp()`, copy/paste the boilerplate `accountInterval` code from above
3. Replace the line `updateInterface();`with a call to `getZombiesByOwner`, and pass it `userAccount`
4. Chain a `then` statement after `getZombiesByOwner` and pass the result to a function named `displayZombies`. (The syntax is: `.then(displayZombies);`).
    
    We don't have a function called `displayZombies` yet, but we'll implement it in the next chapter.
    

Code

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>CryptoZombies front-end</title>
    <script language="javascript" type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script language="javascript" type="text/javascript" src="web3.min.js"></script>
    <script language="javascript" type="text/javascript" src="cryptozombies_abi.js"></script>
  </head>
  <body>

    <script>
      var cryptoZombies;
      var userAccount;

      function startApp() {
        var cryptoZombiesAddress = "YOUR_CONTRACT_ADDRESS";
        cryptoZombies = new web3js.eth.Contract(cryptoZombiesABI, cryptoZombiesAddress);

        var accountInterval = setInterval(function() {
          if (web3.eth.accounts[0] !== userAccount) {
            userAccount = web3.eth.accounts[0];

            getZombiesByOwner(userAccount)
            .then(displayZombies);
          }
         }, 100);
        }
      

      function getZombieDetails(id) {
        return cryptoZombies.methods.zombies(id).call()
      }

      function zombieToOwner(id) {
        return cryptoZombies.methods.zombieToOwner(id).call()
      }

      function getZombiesByOwner(owner) {
        return cryptoZombies.methods.getZombiesByOwner(owner).call()
      }

      window.addEventListener('load', function() {

        // Checking if Web3 has been injected by the browser (Mist/MetaMask)
        if (typeof web3 !== 'undefined') {
          // Use Mist/MetaMask's provider
          web3js = new Web3(web3.currentProvider);
        } else {
          // Handle the case where the user doesn't have Metamask installed
          // Probably show them a message prompting them to install Metamask
        }

        // Now you can start your app & access web3 freely:
        startApp()

      })
    </script>
  </body>
</html>
```

---

### Chapter 6: Displaying our Zombie Army

This tutorial wouldn't be complete if we didn't show you how to actually display the data you get back from the contract.

However, realistically, you'll want to use a front-end framework like React or Vue.js in your app, since they make your life a lot easier as a front-end developer. But covering React or Vue.js is way outside the scope of this tutorial — that would be an entire tutorial of multiple lessons in itself.

So in order to keep CryptoZombies.io focused on Ethereum and smart contracts, we're just going to show a quick example in JQuery to demonstrate how you could parse and display the data you get back from your smart contract.

## **Displaying zombie data — a rough example**

We've added an empty `<div id="zombies"></div>` to the body of our document, as well as an empty `displayZombies` function.

Recall that in the previous chapter we called `displayZombies` from inside `startApp()`with the result of a call to `getZombiesByOwner`. It will be passed an array of zombie IDs that looks something like:

```
[0, 13, 47]

```

Thus we'll want our `displayZombies` function to:

1. First clear the contents of the `#zombies`div, if there's anything already inside it. (This way if the user changes their active MetaMask account, it will clear their old zombie army before loading the new one).
2. Loop through each `id`, and for each one call `getZombieDetails(id)` to look up all the information for that zombie from our smart contract, then
3. Put the information about that zombie into an HTML template to format it for display, and append that template to the `#zombies` div.

Again, we're just using JQuery here, which doesn't have a templating engine by default, so this is going to be ugly. But here's a simple example of how we could output this data for each zombie:

```
// Look up zombie details from our contract. Returns a `zombie` object
getZombieDetails(id)
.then(function(zombie) {
// Using ES6's "template literals" to inject variables into the HTML.// Append each one to our #zombies div
  $("#zombies").append(`<div class="zombie">
    <ul>
      <li>Name: ${zombie.name}</li>
      <li>DNA: ${zombie.dna}</li>
      <li>Level: ${zombie.level}</li>
      <li>Wins: ${zombie.winCount}</li>
      <li>Losses: ${zombie.lossCount}</li>
      <li>Ready Time: ${zombie.readyTime}</li>
    </ul>
  </div>`);
});

```

## **What about displaying the zombie sprites?**

In the above example, we're simply displaying the DNA as a string. But in your DApp, you would want to convert this to images to display your zombie.

We did this by splitting up the DNA string into substrings, and having every 2 digits correspond to an image. Something like:

```
// Get an integer 1-7 that represents our zombie head:
var head = parseInt(zombie.dna.substring(0, 2)) % 7 + 1

// We have 7 head images with sequential filenames:
var headSrc = "../assets/zombieparts/head-" + head + ".png"

```

Each component is positioned with CSS using absolute positioning, to overlay it over the other images.

If you want to see our exact implementation, we've open sourced the Vue.js component we use for the zombie's appearance, which you can view [here](https://github.com/loomnetwork/zombie-char-component).

However, because there's a lot of code in that file, it's outside the scope of this tutorial. For this lesson, we'll stick with the extremely simple JQuery implementation above, and leave it to you to dive into a more beautiful implementation as homework 😉

### Exercise

We created an empty `displayZombies`function for you. Let's fill it in.

1. The first thing we'll want to do is empty the `#zombies` div. In JQuery, you can do this with `$("#zombies").empty();`.
2. Next, we'll want to loop through all the ids, using a for loop: `for (const id of ids) {}`
3. Inside the for loop, copy/paste the code block above that called `getZombieDetails(id)` for each id and then used `$("#zombies").append(...)`to add it to our HTML.

Code

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>CryptoZombies front-end</title>
    <script language="javascript" type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script language="javascript" type="text/javascript" src="web3.min.js"></script>
    <script language="javascript" type="text/javascript" src="cryptozombies_abi.js"></script>
  </head>
  <body>
    <div id="zombies"></div>

    <script>
      var cryptoZombies;
      var userAccount;

      function startApp() {
        var cryptoZombiesAddress = "YOUR_CONTRACT_ADDRESS";
        cryptoZombies = new web3js.eth.Contract(cryptoZombiesABI, cryptoZombiesAddress);

        var accountInterval = setInterval(function() {
          // Check if account has changed
          if (web3.eth.accounts[0] !== userAccount) {
            userAccount = web3.eth.accounts[0];
            // Call a function to update the UI with the new account
            getZombiesByOwner(userAccount)
            .then(displayZombies);
          }
        }, 100);
      }

      function displayZombies(ids) {
         $("#zombies").empty();
        for (const id of ids) {
         
          getZombieDetails(id)
          .then(function(zombie) {
           
           
            $("#zombies").append(`<div class="zombie">
              <ul>
                <li>Name: ${zombie.name}</li>
                <li>DNA: ${zombie.dna}</li>
                <li>Level: ${zombie.level}</li>
                <li>Wins: ${zombie.winCount}</li>
                <li>Losses: ${zombie.lossCount}</li>
                <li>Ready Time: ${zombie.readyTime}</li>
              </ul>
            </div>`);
          });
        }
      }

      function getZombieDetails(id) {
        return cryptoZombies.methods.zombies(id).call()
      }

      function zombieToOwner(id) {
        return cryptoZombies.methods.zombieToOwner(id).call()
      }

      function getZombiesByOwner(owner) {
        return cryptoZombies.methods.getZombiesByOwner(owner).call()
      }

      window.addEventListener('load', function() {

        // Checking if Web3 has been injected by the browser (Mist/MetaMask)
        if (typeof web3 !== 'undefined') {
          // Use Mist/MetaMask's provider
          web3js = new Web3(web3.currentProvider);
        } else {
          // Handle the case where the user doesn't have Metamask installed
          // Probably show them a message prompting them to install Metamask
        }

        // Now you can start your app & access web3 freely:
        startApp()

      })
    </script>
  </body>
</html>
```

### Chapter 7: sending transactions

Awesome! Now our UI will detect the user's metamask account, and automatically display their zombie army on the homepage.

Now let's look at using `send` functions to change data on our smart contract.

There are a few major differences from `call`functions:

1. `send`ing a transaction requires a `from`address of who's calling the function (which becomes `msg.sender` in your Solidity code). We'll want this to be the user of our DApp, so MetaMask will pop up to prompt them to sign the transaction.
2. `send`ing a transaction costs gas
3. There will be a significant delay from when the user `send`s a transaction and when that transaction actually takes effect on the blockchain. This is because we have to wait for the transaction to be included in a block, and the block time for Ethereum is on average 15 seconds. If there are a lot of pending transactions on Ethereum or if the user sends too low of a gas price, our transaction may have to wait several blocks to get included, and this could take minutes.
    
    Thus we'll need logic in our app to handle the asynchronous nature of this code.
    

## **Creating zombies**

Let's look at an example with the first function in our contract a new user will call: `createRandomZombie`.

As a review, here is the Solidity code in our contract:

```
function createRandomZombie(string _name) public {
  require(ownerZombieCount[msg.sender] == 0);
  uint randDna = _generateRandomDna(_name);
  randDna = randDna - randDna % 100;
  _createZombie(_name, randDna);
}

```

Here's an example of how we could call this function in Web3.js using MetaMask:

```
function createRandomZombie(name) {
// This is going to take a while, so update the UI to let the user know// the transaction has been sent
  $("#txStatus").text("Creating new zombie on the blockchain. This may take a while...");
// Send the tx to our contract:return cryptoZombies.methods.createRandomZombie(name)
  .send({ from: userAccount })
  .on("receipt", function(receipt) {
    $("#txStatus").text("Successfully created " + name + "!");
// Transaction was accepted into the blockchain, let's redraw the UI
    getZombiesByOwner(userAccount).then(displayZombies);
  })
  .on("error", function(error) {
// Do something to alert the user their transaction has failed
    $("#txStatus").text(error);
  });
}

```

Our function `send`s a transaction to our Web3 provider, and chains some event listeners:

- `receipt` will fire when the transaction is included into a block on Ethereum, which means our zombie has been created and saved on our contract
- `error` will fire if there's an issue that prevented the transaction from being included in a block, such as the user not sending enough gas. We'll want to inform the user in our UI that the transaction didn't go through so they can try again.

> Note: You can optionally specify gas and gasPrice when you call send, e.g. .send({ from: userAccount, gas: 3000000 }). If you don't specify this, MetaMask will let the user choose these values.
> 

## **Put it to the Test**

We've added a `div` with ID `txStatus` — this way we can use this div to update the user with messages with the status of our transactions.

1. Below `displayZombies`, copy / paste the code from `createRandomZombie` above.
2. Let's implement another function: `feedOnKitty`.
    
    The logic for calling `feedOnKitty` will be almost identical — we'll send a transaction that calls the function, and a successful transaction results in a new zombie being created for us, so we'll want to redraw the UI after it's successful.
    
    Make a copy of `createRandomZombie`right below it, but make the following changes:
    
    a) Call the 2nd function `feedOnKitty`, which takes 2 arguments: `zombieId` and `kittyId`
    
    b) The `#txStatus` text should update to: `"Eating a kitty. This may take a while..."`
    
    c) Make it call `feedOnKitty` on our contract, and pass the same 2 arguments
    
    d) The success message on `#txStatus`should read: `"Ate a kitty and spawned a new Zombie!"`
    
    Code
    
    ```html
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8">
        <title>CryptoZombies front-end</title>
        <script language="javascript" type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
        <script language="javascript" type="text/javascript" src="web3.min.js"></script>
        <script language="javascript" type="text/javascript" src="cryptozombies_abi.js"></script>
      </head>
      <body>
        <div id="txStatus"></div>
        <div id="zombies"></div>
    
        <script>
          var cryptoZombies;
          var userAccount;
    
          function startApp() {
            var cryptoZombiesAddress = "YOUR_CONTRACT_ADDRESS";
            cryptoZombies = new web3js.eth.Contract(cryptoZombiesABI, cryptoZombiesAddress);
    
            var accountInterval = setInterval(function() {
              // Check if account has changed
              if (web3.eth.accounts[0] !== userAccount) {
                userAccount = web3.eth.accounts[0];
                // Call a function to update the UI with the new account
                getZombiesByOwner(userAccount)
                .then(displayZombies);
              }
            }, 100);
          }
    
          function displayZombies(ids) {
            $("#zombies").empty();
            for (const id of ids) {
              // Look up zombie details from our contract. Returns a `zombie` object
              getZombieDetails(id)
              .then(function(zombie) {
                // Using ES6's "template literals" to inject variables into the HTML.
                // Append each one to our #zombies div
                $("#zombies").append(`<div class="zombie">
                  <ul>
                    <li>Name: ${zombie.name}</li>
                    <li>DNA: ${zombie.dna}</li>
                    <li>Level: ${zombie.level}</li>
                    <li>Wins: ${zombie.winCount}</li>
                    <li>Losses: ${zombie.lossCount}</li>
                    <li>Ready Time: ${zombie.readyTime}</li>
                  </ul>
                </div>`);
              });
            }
          }
    
          function createRandomZombie(name) {
           
           
            $("#txStatus").text("Creating new zombie on the blockchain. This may take a while...");
           
            return cryptoZombies.methods.createRandomZombie(name)
            .send({ from: userAccount })
            .on("receipt", function(receipt) {
              $("#txStatus").text("Successfully created " + name + "!");
             
              getZombiesByOwner(userAccount).then(displayZombies);
            })
            .on("error", function(error) {
             
              $("#txStatus").text(error);
            });
          }
    
          function feedOnKitty(zombieId, kittyId) {
           
           
            $("#txStatus").text("Eating a kitty. This may take a while...");
           
            return cryptoZombies.methods.feedOnKitty(zombieId, kittyId)
            .send({ from: userAccount })
            .on("receipt", function(receipt) {
              $("#txStatus").text("Ate a kitty and spawned a new Zombie!");
             
              getZombiesByOwner(userAccount).then(displayZombies);
            })
            .on("error", function(error) {
             
              $("#txStatus").text(error);
            });
          }
    
          function getZombieDetails(id) {
            return cryptoZombies.methods.zombies(id).call()
          }
    
          function zombieToOwner(id) {
            return cryptoZombies.methods.zombieToOwner(id).call()
          }
    
          function getZombiesByOwner(owner) {
            return cryptoZombies.methods.getZombiesByOwner(owner).call()
          }
    
          window.addEventListener('load', function() {
    
            // Checking if Web3 has been injected by the browser (Mist/MetaMask)
            if (typeof web3 !== 'undefined') {
              // Use Mist/MetaMask's provider
              web3js = new Web3(web3.currentProvider);
            } else {
              // Handle the case where the user doesn't have Metamask installed
              // Probably show them a message prompting them to install Metamask
            }
    
            // Now you can start your app & access web3 freely:
            startApp()
    
          })
        </script>
      </body>
    </html>
    ```
    

---

Chapter 8: Calling payable Functions

The logic for `attack`, `changeName`, and `changeDna` will be extremely similar, so they're trivial to implement and we won't spend time coding them in this lesson.

> In fact, there's already a lot of repetitive logic in each of these function calls, so it would probably make sense to refactor and put the common code in its own function. (And use a templating system for the txStatus messages — already we're seeing how much cleaner things would be with a framework like Vue.js!)
> 

Let's look at another type of function that requires special treatment in Web3.js — `payable` functions.

## **Level Up!**

Recall in `ZombieHelper`, we added a payable function where the user can level up:

```
function levelUp(uint _zombieId) external payable {
  require(msg.value == levelUpFee);
  zombies[_zombieId].level++;
}

```

The way to send Ether along with a function is simple, with one caveat: we need to specify how much to send in `wei`, not Ether.

## **What's a Wei?**

A `wei` is the smallest sub-unit of Ether — there are 10^18 `wei` in one `ether`.

That's a lot of zeroes to count — but luckily Web3.js has a conversion utility that does this for us.

```
// This will convert 1 ETH to Wei
web3js.utils.toWei("1");

```

In our DApp, we set `levelUpFee = 0.001 ether`, so when we call our `levelUp` function, we can make the user send `0.001` Ether along with it using the following code:

```
cryptoZombies.methods.levelUp(zombieId)
.send({ from: userAccount, value: web3js.utils.toWei("0.001", "ether") })

```

### Exercise

Let's add a `levelUp` function below `feedOnKitty`. The code will be very similar to `feedOnKitty`, but:

1. The function will take 1 parameter, `zombieId`
2. Pre-transaction, it should display the `txStatus` text `"Leveling up your zombie..."`
3. When it calls `levelUp` on the contract, it should send `"0.001"` ETH converted `toWei`, as in the example above
4. Upon success it should display the text `"Power overwhelming! Zombie successfully leveled up"`
5. We **don't** need to redraw the UI by querying our smart contract with `getZombiesByOwner` — because in this case we know the only thing that's changed is the one zombie's level.

Code

```solidity
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>CryptoZombies front-end</title>
    <script language="javascript" type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script language="javascript" type="text/javascript" src="web3.min.js"></script>
    <script language="javascript" type="text/javascript" src="cryptozombies_abi.js"></script>
  </head>
  <body>
    <div id="txStatus"></div>
    <div id="zombies"></div>

    <script>
      var cryptoZombies;
      var userAccount;

      function startApp() {
        var cryptoZombiesAddress = "YOUR_CONTRACT_ADDRESS";
        cryptoZombies = new web3js.eth.Contract(cryptoZombiesABI, cryptoZombiesAddress);

        var accountInterval = setInterval(function() {
         
          if (web3.eth.accounts[0] !== userAccount) {
            userAccount = web3.eth.accounts[0];
           
            getZombiesByOwner(userAccount)
            .then(displayZombies);
          }
        }, 100);
      }

      function displayZombies(ids) {
        $("#zombies").empty();
        for (const id of ids) {
         
          getZombieDetails(id)
          .then(function(zombie) {
           
           
            $("#zombies").append(`<div class="zombie">
              <ul>
                <li>Name: ${zombie.name}</li>
                <li>DNA: ${zombie.dna}</li>
                <li>Level: ${zombie.level}</li>
                <li>Wins: ${zombie.winCount}</li>
                <li>Losses: ${zombie.lossCount}</li>
                <li>Ready Time: ${zombie.readyTime}</li>
              </ul>
            </div>`);
          });
        }
      }

      function createRandomZombie(name) {
       
       
        $("#txStatus").text("Creating new zombie on the blockchain. This may take a while...");
       
        return cryptoZombies.methods.createRandomZombie(name)
        .send({ from: userAccount })
        .on("receipt", function(receipt) {
          $("#txStatus").text("Successfully created " + name + "!");
         
          getZombiesByOwner(userAccount).then(displayZombies);
        })
        .on("error", function(error) {
         
          $("#txStatus").text(error);
        });
      }

      function feedOnKitty(zombieId, kittyId) {
        $("#txStatus").text("Eating a kitty. This may take a while...");
        return cryptoZombies.methods.feedOnKitty(zombieId, kittyId)
        .send({ from: userAccount })
        .on("receipt", function(receipt) {
          $("#txStatus").text("Ate a kitty and spawned a new Zombie!");
          getZombiesByOwner(userAccount).then(displayZombies);
        })
        .on("error", function(error) {
          $("#txStatus").text(error);
        });
      }

      function levelUp(zombieId) {
        $("#txStatus").text("Leveling up your zombie...");
        return cryptoZombies.methods.levelUp(zombieId)
        .send({ from: userAccount, value: web3js.utils.toWei("0.001", "ether") })
        .on("receipt", function(receipt) {
          $("#txStatus").text("Power overwhelming! Zombie successfully leveled up");
        })
        .on("error", function(error) {
          $("#txStatus").text(error);
        });
      }

      function getZombieDetails(id) {
        return cryptoZombies.methods.zombies(id).call()
      }

      function zombieToOwner(id) {
        return cryptoZombies.methods.zombieToOwner(id).call()
      }

      function getZombiesByOwner(owner) {
        return cryptoZombies.methods.getZombiesByOwner(owner).call()
      }

      window.addEventListener('load', function() {

       
        if (typeof web3 !== 'undefined') {
         
          web3js = new Web3(web3.currentProvider);
        } else {
         
         
        }

       
        startApp()

      })
    </script>
  </body>
</html>
```

---

### Chapter 9: Subscribing to Events

As you can see, interacting with your contract via Web3.js is pretty straightforward — once you have your environment set up, `call`ing functions and `send`ing transactions is not all that different from a normal web API.

There's one more aspect we want to cover — subscribing to events from your contract.

### **Listening for New Zombies**

If you recall from `zombiefactory.sol`, we had an event called `NewZombie` that we fired every time a new zombie was created:

```
event NewZombie(uint zombieId, string name, uint dna);

```

In Web3.js, you can **subscribe** to an event so your web3 provider triggers some logic in your code every time it fires:

```
cryptoZombies.events.NewZombie()
.on("data", function(event) {
  let zombie = event.returnValues;
  // We can access this event's 3 return values on the `event.returnValues` object:
  console.log("A new zombie was born!", zombie.zombieId, zombie.name, zombie.dna);
}).on("error", console.error);

```

Note that this would trigger an alert every time ANY zombie was created in our DApp — not just for the current user. What if we only wanted alerts for the current user?

### **Using `indexed`**

In order to filter events and only listen for changes related to the current user, our Solidity contract would have to use the `indexed` keyword, like we did in the `Transfer`event of our ERC721 implementation:

```
event Transfer(address indexed _from, address indexed _to, uint256 _tokenId);

```

In this case, because `_from` and `_to` are `indexed`, that means we can filter for them in our event listener in our front end:

```
// Use `filter` to only fire this code when `_to` equals `userAccount`
cryptoZombies.events.Transfer({ filter: { _to: userAccount } })
.on("data", function(event) {
  let data = event.returnValues;
  // The current user just received a zombie!
  // Do something here to update the UI to show it
}).on("error", console.error);

```

As you can see, using `event`s and `indexed`fields can be quite a useful practice for listening to changes to your contract and reflecting them in your app's front-end.

### **Querying past events**

We can even query past events using `getPastEvents`, and use the filters `fromBlock` and `toBlock` to give Solidity a time range for the event logs ("block" in this case referring to the Ethereum block number):

```
cryptoZombies.getPastEvents("NewZombie", { fromBlock: 0, toBlock: "latest" })
.then(function(events) {
// `events` is an array of `event` objects that we can iterate, like we did above// This code will get us a list of every zombie that was ever created
});

```

Because you can use this method to query the event logs since the beginning of time, this presents an interesting use case: **Using events as a cheaper form of storage**.

If you recall, saving data to the blockchain is one of the most expensive operations in Solidity. But using events is much much cheaper in terms of gas.

The tradeoff here is that events are not readable from inside the smart contract itself. But it's an important use-case to keep in mind if you have some data you want to be historically recorded on the blockchain so you can read it from your app's front-end.

For example, we could use this as a historical record of zombie battles — we could create an event for every time one zombie attacks another and who won. The smart contract doesn't need this data to calculate any future outcomes, but it's useful data for users to be able to browse from the app's front-end.

### Exercise

Let's add some code to listen for the `Transfer` event, and update our app's UI if the current user receives a new zombie.

We'll need to add this code at the end of the `startApp` function, to make sure the `cryptoZombies` contract has been initialized before adding an event listener.

1. At the end of `startApp()`, copy/paste the code block above listening for `cryptoZombies.events.Transfer`
2. For the line to update the UI, use `getZombiesByOwner(userAccount).then(displayZombies);`

Code

```solidity
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>CryptoZombies front-end</title>
    <script language="javascript" type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
    <script language="javascript" type="text/javascript" src="web3.min.js"></script>
    <script language="javascript" type="text/javascript" src="cryptozombies_abi.js"></script>
  </head>
  <body>
    <div id="txStatus"></div>
    <div id="zombies"></div>

    <script>
      var cryptoZombies;
      var userAccount;

      function startApp() {
        var cryptoZombiesAddress = "YOUR_CONTRACT_ADDRESS";
        cryptoZombies = new web3js.eth.Contract(cryptoZombiesABI, cryptoZombiesAddress);

        var accountInterval = setInterval(function() {
          // Check if account has changed
          if (web3.eth.accounts[0] !== userAccount) {
            userAccount = web3.eth.accounts[0];
            // Call a function to update the UI with the new account
            getZombiesByOwner(userAccount)
            .then(displayZombies);
          }
        }, 100);

        cryptoZombies.events.Transfer({ filter: { _to: userAccount } })
        .on("data", function(event) {
          let data = event.returnValues;
          getZombiesByOwner(userAccount).then(displayZombies);
        }).on("error", console.error);
      }

      function displayZombies(ids) {
        $("#zombies").empty();
        for (const id of ids) {
          // Look up zombie details from our contract. Returns a `zombie` object
          getZombieDetails(id)
          .then(function(zombie) {
            // Using ES6's "template literals" to inject variables into the HTML.
            // Append each one to our #zombies div
            $("#zombies").append(`<div class="zombie">
              <ul>
                <li>Name: ${zombie.name}</li>
                <li>DNA: ${zombie.dna}</li>
                <li>Level: ${zombie.level}</li>
                <li>Wins: ${zombie.winCount}</li>
                <li>Losses: ${zombie.lossCount}</li>
                <li>Ready Time: ${zombie.readyTime}</li>
              </ul>
            </div>`);
          });
        }
      }

      function createRandomZombie(name) {
        // This is going to take a while, so update the UI to let the user know
        // the transaction has been sent
        $("#txStatus").text("Creating new zombie on the blockchain. This may take a while...");
        // Send the tx to our contract:
        return cryptoZombies.methods.createRandomZombie(name)
        .send({ from: userAccount })
        .on("receipt", function(receipt) {
          $("#txStatus").text("Successfully created " + name + "!");
          // Transaction was accepted into the blockchain, let's redraw the UI
          getZombiesByOwner(userAccount).then(displayZombies);
        })
        .on("error", function(error) {
          // Do something to alert the user their transaction has failed
          $("#txStatus").text(error);
        });
      }

      function feedOnKitty(zombieId, kittyId) {
        $("#txStatus").text("Eating a kitty. This may take a while...");
        return cryptoZombies.methods.feedOnKitty(zombieId, kittyId)
        .send({ from: userAccount })
        .on("receipt", function(receipt) {
          $("#txStatus").text("Ate a kitty and spawned a new Zombie!");
          getZombiesByOwner(userAccount).then(displayZombies);
        })
        .on("error", function(error) {
          $("#txStatus").text(error);
        });
      }

      function levelUp(zombieId) {
        $("#txStatus").text("Leveling up your zombie...");
        return cryptoZombies.methods.levelUp(zombieId)
        .send({ from: userAccount, value: web3.utils.toWei("0.001", "ether") })
        .on("receipt", function(receipt) {
          $("#txStatus").text("Power overwhelming! Zombie successfully leveled up");
        })
        .on("error", function(error) {
          $("#txStatus").text(error);
        });
      }

      function getZombieDetails(id) {
        return cryptoZombies.methods.zombies(id).call()
      }

      function zombieToOwner(id) {
        return cryptoZombies.methods.zombieToOwner(id).call()
      }

      function getZombiesByOwner(owner) {
        return cryptoZombies.methods.getZombiesByOwner(owner).call()
      }

      window.addEventListener('load', function() {

        // Checking if Web3 has been injected by the browser (Mist/MetaMask)
        if (typeof web3 !== 'undefined') {
          // Use Mist/MetaMask's provider
          web3js = new Web3(web3.currentProvider);
        } else {
          // Handle the case where the user doesn't have Metamask installed
          // Probably show them a message prompting them to install Metamask
        }

        // Now you can start your app & access web3 freely:
        startApp()

      })
    </script>
  </body>
</html>
```

---

### Chapter 10: Wrapping it up

Congratulations! You've successfully written your first Web3.js front-end that interacts with your smart contract.

As a reward, you get your very own `The Phantom of Web3` zombie! Level 3.0 (for Web 3.0 😉), complete with fox mask. Check him out to the right.

## **Next Steps**

This lesson was intentionally basic. We wanted to show you the core logic you would need in order to interact with your smart contract, but didn't want to take up too much time in order to do a full implementation since the Web3.js portion of the code is quite repetitive, and we wouldn't be introducing any new concepts by making this lesson any longer.

So we've left this implementation bare-bones. Here's a checklist of ideas for things we would want to implement in order to make our front-end a full implementation for our zombie game, if you want to run with this and build it on your own:

1. Implementing functions for `attack`, `changeName`, `changeDna`, and the ERC721 functions `transfer`, `ownerOf`, `balanceOf`, etc. The implementation of these functions would be identical to all the other `send` transactions we covered.
2. Implementing an "admin page" where you can execute `setKittyContractAddress`, `setLevelUpFee`, and `withdraw`. Again, there's no special logic on the front-end here — these implementations would be identical to the functions we've already covered. You would just have to make sure you called them from the same Ethereum address that deployed the contract, since they have the `onlyOwner` modifier.
3. There are a few different views in the app we would want to implement:
    
    a. An individual zombie page, where you can view info about a specific zombie with a permalink to it. This page would render the zombie's appearance, show its name, its owner (with a link to the user's profile page), its win/loss count, its battle history, etc.
    
    b. A user page, where you could view a user's zombie army with a permalink. You would be able to click on an individual zombie to view its page, and also click on a zombie to attack it if you're logged into MetaMask and have an army.
    
    c. A homepage, which is a variation of the user page that shows the current user's zombie army. (This is the page we started implementing in index.html).
    
4. Some method in the UI that allows the user to feed on CryptoKitties. We could have a button by each zombie on the homepage that says "Feed Me", then a text box that prompted the user to enter a kitty's ID (or a URL to that kitty, e.g. [https://www.cryptokitties.co/kitty/578397](https://www.cryptokitties.co/kitty/578397)). This would then trigger our function `feedOnKitty`.
5. Some method in the UI for the user to attack another user's zombie.
    
    One way to implement this would be when the user was browsing another user's page, there could be a button that said "Attack This Zombie". When the user clicked it, it would pop up a modal that contains the current user's zombie army and prompt them "Which zombie would you like to attack with?"
    
    The user's homepage could also have a button by each of their zombies that said "Attack a Zombie". When they clicked it, it could pop up a modal with a search field where they could type in a zombie's ID to search for it. Or an option that said "Attack Random Zombie", which would search a random number for them.
    
    We would also want to grey out the user's zombies whose cooldown period had not yet passed, so the UI could indicate to the user that they can't yet attack with that zombie, and how long they will have to wait.
    
6. The user's homepage would also have options by each zombie to change name, change DNA, and level up (for a fee). Options would be greyed out if the user wasn't yet high enough level.
7. For new users, we should display a welcome message with a prompt to create the first zombie in their army, which calls `createRandomZombie()`.
8. We'd probably want to add an `Attack`event to our smart contract with the user's `address` as an `indexed` property, as discussed in the last chapter. This would allow us to build real-time notifications — we could show the user a popup alert when one of their zombies was attacked, so they could view the user/zombie who attacked them and retaliate.
9. We would probably also want to implement some sort of front-end caching layer so we aren't always slamming Infura with requests for the same data. (Our current implementation of `displayZombies`calls `getZombieDetails` for every single zombie every time we refresh the interface — but realistically we only need to call this for the new zombie that's been added to our army).
10. A real-time chat room so you could trash talk other players as you crush their zombie army? Yes plz.

That's just a start — I'm sure we could come up with even more features — and already it's a massive list.

Since there's a lot of front-end code that would go into creating a full interface like this (HTML, CSS, JavaScript and a framework like React or Vue.js), building out this entire front-end would probably be an entire course with 10 lessons in itself. So we'll leave the awesome implementation to you.

> Note: Even though our smart contract is decentralized, this front-end for interacting with our DApp would be totally centralized on our web-server somewhere.However, with the SDK we're building at Loom Network, soon you'll be able to serve front-ends like this from their own DAppChain instead of a centralized web server. That way between Ethereum and the Loom DAppChain, your entire app would run 100% on the blockchain.
> 

## **Conclusion**

This concludes Lesson 6. You now have all the skills you need to code a smart contract and a front-end that allows users to interact with it!

In the next lesson, we're going to be covering the final missing piece in this puzzle — deploying your smart contracts to Ethereum.

Go ahead and click "Next Chapter" to claim your rewards!