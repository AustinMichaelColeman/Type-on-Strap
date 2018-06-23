---
layout: post
title: Build an Unstoppable Counter With Solidity
tags: [Getting, Started, Solidity, Ethereum, Introduction]
image: /assets/img/pexels/journey.jpg
excerpt_separator: <!--more-->
---

You are about to wield the full power of the blockchain. All hail the all mighty censorship-resistent integer. Okay, the contract you will make is not going to be very useful for any real world applications, but it will be useful for the knowledge you gain from it. You may not solve all the world's problems with this smart contract, but your journey can start with the small step you take here.
<!--more-->

![Journey]({{ site.baseurl }}/assets/img/pexels/journey.jpg)
<p align="center"><i>The road to learning Solidity smart contract programming</i></p>

## Example code

In this example, we will be walking through a contract that stores a number. The main contract is called `Counter.sol` and it inherits from `Ownable.sol`. You can read them below:

<script src="https://gist.github.com/AustinMichaelColeman/32718162270c6125c98afa48c4fdfcd5.js"></script>

## Solidity

Solidity is a contract-oriented programming language, which is most often used on the Ethereum blockchain. Ethereum is a blockchain that has a virtual machine where the state of the virtual machine is copied over thousands of computers. To run programs on the ethereum virtual machine, you pay for the cost of computation and storage with the ether token. It is a global shared computer that enables us to create programs that are virtually impossible to shut down or stop. It is the platform that brought us ICOs, or initial coin offerings, a tool used to fund development of new ideas. You also can build dapps, or decentralized applications, using Solidity. Dapps are like websites that interact with Ethereum smart contracts. Lets get started with Remix.

## Remix - Solidity IDE

For this example, we will be using [Remix](http://remix.ethereum.org/#version=soljson-v0.4.24+commit.e67f0147.js&optimize=false&gist=32718162270c6125c98afa48c4fdfcd5). Remix is a web integrated development environment (IDE). Remix a great tool for learning Solidity smart contract development. It is very easy to get started because you do not have to install anything. You can get coding right away.

## Example Smart Contract

In this example, we will create a contract that stores a number. We will also let anyone add one to this number. We will also let the owner reset the number if they choose. We will create a powerful, unstoppable, censorship-resistant number. We will create two contracts: `Ownable` and `Counter`. `Counter` will inherit from `Ownable`. In other words, `Counter` is `Ownable`, which means `Counter` gains access to the data and functions of `Ownable`.

## Importing into Remix

1. To begin, open [this link](http://remix.ethereum.org/#version=soljson-v0.4.24+commit.e67f0147.js&optimize=false&gist=32718162270c6125c98afa48c4fdfcd5) and the code for this example will be automatically imported.
2. In Remix, click gist on left to show the contracts in this example
![Gist]({{ site.baseurl }}/assets/img/screenshots/gist.png)
3. In Remix, click `Counter.sol` and `Ownable.sol` to open and read them.

Read through the code and get a feel for it. `Ownable.sol` and `Counter.sol` are used together to create an integer `counter` that can only be reset by the creator of the contract. 

## Playing with the code

1. In compile tab, click compile. You need to open the files first before Remix will compile them. Once they are compiled, Remix will look like this:
![Compile]({{ site.baseurl }}/assets/img/screenshots/compiled.png)
2. In the run tab, change your settings to look like this:
![Run]({{ site.baseurl }}/assets/img/screenshots/run.png)
3. Click the deploy button to deploy the Counter contract. You should see this:
![Counter]({{ site.baseurl }}/assets/img/screenshots/counter.png)

This creates the contract and calls the constructor. At the bottom you can interact with your deployed contract and call functions defined earlier. Try pressing buttons and see what they do. You can also change which address you are sending from by selecting a different account near the top:

![Accounts]({{ site.baseurl }}/assets/img/screenshots/accounts.png)

Try seeing what happens if you try to call `Reset` from a different address.

## Walking through code: Ownable

{% highlight js %}
pragma solidity^0.4.24;
{% endhighlight js %}

Every programming language is continually evolving. Sometimes changes to the design of a language can make it incompatible with previous syntax. Therefore, Solidity and other programming languages like it use a `pragma` statement to let the compiler know which version of the programming language this code is expected to run with. This statement means that the code not compile with a solidity compiler version below 0.4.24. The carrot `^` means it also will not compile with a version starting with 0.5.0 and above.

{% highlight js %}
contract Ownable {
{% endhighlight js %}

Contracts in solidity store data and allow functions to be defined that return or modify the data it stores. In this example, we define a contract named `Ownable`.

{% highlight js %}
    /* Define owner of the type address */
    address owner;
{% endhighlight js %}

We create a variable named owner of type `address` to keep track of the contract owner. An `address` in Ethereum is a 20-byte value. Every ether token is associated with an `address`. When you send ether to someone else, you send it to their `address`. Your ether tokens in the Ethereum network are attributed to a public `address`, generated from a private key. Your private key allows you to sign messages that the network can verify. Others cannot spend your ether without your private key.

{% highlight js %}
    modifier onlyOwner {
        require (msg.sender == owner);
        _;
    }
{% endhighlight js %}
    
Modifiers in Solidity partially define functions. This modifier is named `onlyOwner`, and any other function can add `onlyOwner` to the end of it to add the above code to the function. `require` is a built-in function in solidity that is used to check for conditions and throw an exception if it is not met. `msg.sender` is the `address` of the person who created the transaction that called this function. Every time any code is ran in solidity, it is ran by a transaction with a sender. 

{% highlight js %}
    /* This function is executed at initialization and sets the owner of the contract */
    constructor() public { 
        owner = msg.sender; 
    }
{% endhighlight js %}

When a contract is created, the `constructor` is called exactly one time and never called again. `Ownable`'s `constructor` sets the `owner` variable to `msg.sender`. `msg.sender` is the address of the transaction calling this code. Since the `constructor` is only called once upon creation, `msg.sender` is the address of the creator of this contract in this context.

## Walking through code: Counter

{% highlight js %}
import "./Ownable.sol";
{% endhighlight js %}

`import` statements copy the code from the contract it is importing so that this contract can use it when compiled. The `Counter` contract `import`s `Ownable` because we want to make this `Counter` contract `Ownable`.

{% highlight js %}
contract Counter is Ownable {
{% endhighlight js %}

Solidity supports inheritance, which defines an "is a" relationship between the contracts. In this case, `Counter` `is` `Ownable`. `Counter` gains access to all data and functions defined in `Ownable`. It makes it easier to define other contracts where you only want the owner to be able to take action.

{% highlight js %}
    int counter;
{% endhighlight js %}

This is where we store the unstoppable, uncensorable all-powerful `counter`. What you choose to do when you wield this power is your choice. `counter` is an `int`, or integer, a number that is stored by the contract.

{% highlight js %}
    constructor() public {
       counter = 0;
    }
{% endhighlight js %}

As explained earlier, the `constructor` is called exactly one time when the contract is first created. In this case, it sets `counter` to 0. Since this contract inherits from `Ownable`, it also means the `Ownable` `constructor` is called.

{% highlight js %}
    // From Ownable.sol:
    modifier onlyOwner {
        require (msg.sender == owner);
        _;
    }
    // From Counter.sol:
    function reset() public onlyOwner {
        counter = 0;
    }
{% endhighlight js %}

The `reset` function shows an example of using a modifier to change the behavior of a function. In this example, the `reset` function is modified by the `onlyOwner` modifier. In the modifier, the `_;` is where the rest of the function is called. If someone tries to call the `reset` function and they are not the owner, it will fail. If they are `owner`, it will set `counter` to zero again.
    
{% highlight js %}
    function add() public {
        counter += 1;
    }
{% endhighlight js %}

Functions can be defined that modify data stored in the contract. In this example, `add()` will add 1 to the counter stored in the contract.
    
{% highlight js %}
    function getCounter() public view returns (int) {
        return counter;
    }
{% endhighlight js %}

Adding the `view` keyword to a function means that the function will not cost any gas to execute because it does not modify any data. It does not require every other computer on the Ethereum network to do anything. You can read the data locally. `returns (int)` means this function will return an integer when you call it. In this case, we return counter.

## Going "live" on Rinkeby test net
You can deploy this contract on the Rinkeby Ethereum test net. Rinkeby is the name of one of Ethereum's test networks. It is designed as a testing ground for creating smart contracts. It allows you to code for Ethereum without having to spend real money while you develop. Here is how you can get started:

1. Install metamask https://metamask.io/
2. At the top of Metamask, switch your network to the Rinkeby test net:
![Rinkeby]({{ site.baseurl }}/assets/img/screenshots/rinkeby.png)
2. Create an address and copy it
![Copy address]({{ site.baseurl }}/assets/img/screenshots/copyaddress.png)
3. Create public post with your address, for example:
![Public address]({{ site.baseurl }}/assets/img/screenshots/publicaddress.png)
4. Go to the [Rinkeby faucet](https://faucet.rinkeby.io/), paste the link to post with your address
![Rinkeby faucet]({{ site.baseurl }}/assets/img/screenshots/rinkebyfaucet.png)
5. In the run tab of Remix, change Environment to "Injected web3"
![Injected Web3]({{ site.baseurl }}/assets/img/screenshots/injectedweb3.png)
6. Click deploy again:
![Deploy]({{ site.baseurl }}/assets/img/screenshots/deploy.png)
7. Metamask should ask you to confirm. If it fails, try increasing your gas limit.
![Metamask]({{site.baseurl}}/assets/img/screenshots/metamask.png)
8. Once it is published, Remix will give a link where you can see the transaction published:
![Metamask]({{site.baseurl}}/assets/img/screenshots/countercreation.png)

It usually is accepted by the network within about a minute. Deploying to live works pretty much exactly the same, except it costs you main net ether instead of free test ether. 

## Other useful tools

* [Truffle](https://truffleframework.com/), which has a good selection of [tutorials](https://truffleframework.com/tutorials).
* [Ganache](https://truffleframework.com/ganache), often paired with Truffle. It's a fast Ethereum RPC client for testing and development of smart contracts.
* [Superblocks Studio](https://studio.superblocks.com/), a web IDE similar to Remix but also adds an easy way to create a website that interacts with your smart contract.

## Next steps

It is up to you now to use your wit and creativity to create an awesome smart contract. What will you do with the unstoppable integer? You can learn more about ERC20, which is the most popular standard for creating tokens on Ethereum. You can also find a local meetup in your area and ask for help there. Hope you have fun on your blockchain adventures.