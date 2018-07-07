---
layout: post
title: Getting Started with Solidity
tags: [Solidity, Introduction, Getting, Started]
image: /assets/img/pexels/world.jpg
excerpt_separator: <!--more-->
---

Today begins your adventures with Solidity, the smart contract programming language invented for the Ethereum blockchain. Solidity allows your to harness the power of a global shared computer. Anyone can add programs and call functions on this computer. You can upload anything you want to this computer and nobody is going to stop you as long as you follow the rules of the network. Ethereum's website says the network "allows you to build applications that run exactly as programmed without any possibility of downtime, censorship, fraud, or third-party interference." Lets get started!

<!--more-->

![Queue]({{ site.baseurl }}/assets/img/pexels/world.jpg)
<p align="center"><i>Hello world</i></p>

## Hello world
To get started you will write a "hello world" program in Solidity. This simple contract will store a string and have a couple functions for updating and reading the string. You will get a feel for how to use Remix, the Ethereum smart contract web IDE. Remix is a great tool for beginners because you do not have to install anything to get started. You can dive in right away.


## Getting Started

1. Go to https://remix.ethereum.org/
2. Click the + sign in the top left corner
3. Type "hello.sol" (without quotes) and then click Ok.
4. Then paste the code below for the hello contract we will write

### hello.sol:
{% highlight js %}
pragma solidity ^0.4.24;

contract hello {
    string message;
    
    constructor(string _message) public {
        message = _message;
    }
    
    function getMessage() public view returns (string) {
        return message;
    }
    
    function setMessage(string _message) public {
        message = _message;
    }
}
{% endhighlight %}

## hello.sol explained

{% highlight js %}
pragma solidity ^0.4.24;
{% endhighlight %}

This is the pragma statement for Solidity. This lets compiler know what version of Solidity to expect. As Solidity evolves, it will usually make backwards compatible changes for the last number. The second number will change when they make backwards incompatible changes. It lets future readers know how old the code is they are reading.

{% highlight js %}
contract hello {
{% endhighlight %}
This declares a contract named hello. Contracts store data and functions that modify the data they hold. They are similar to classes in other programming languages.

{% highlight js %}
    string message;
{% endhighlight %}
This holds a string, which is a list of alphanumeric characters that changes its size dynamically to fit whatever string it is holding.

{% highlight js %}
    constructor(string _message) public {
        message = _message;
    }
{% endhighlight %}
The constructor function is called when the contract is first created. This constructor takes one argument, a string named _message.


{% highlight js %}
    function getMessage() public view returns (string) {
        return message;
    }
}
{% endhighlight %}
This function returns the string that we set earlier. The view keyword means the function only reads data. It does not modify data.

{% highlight js %}
    function setMessage(string _message) public {
        message = _message;
    }
{% endhighlight %}
This function sets our message to whatever was passed to it.


## Hello world in action

### Compiling
First, we need to compile the contract. Under the compile tab, click compile. It should look like this:
![Hello world]({{ site.baseurl }}/assets/img/screenshots/compilehello.png)

### Running
Next, we will simulate running this on the Ethereum blockchain. We will use a JavaScript VM to run a virtual blockchain in memory. With a simple contract like this, there is no reason to deploy it to the main network. Under the Run tab, make sure "JavaScript VM" is selected for the environment:
![Hello world]({{ site.baseurl }}/assets/img/screenshots/javascriptvm.png)

### Deploying
Next, we will deploy the contract. Select hello from the list of contracts and type "hello world" for the argument:
![Hello world]({{ site.baseurl }}/assets/img/screenshots/helloworld.png)

### Hello world
To verify it is working, we can click getMessage to see the message we set:
![Hello world]({{ site.baseurl }}/assets/img/screenshots/helloworlddeployed.png)

### Setting hello friends
The next thing we can do is set a new message: "hello friends":
![Hello world]({{ site.baseurl }}/assets/img/screenshots/hellofriends.png)

### Hello friends
Finally, we can click getMessage again to see the new message:
![Hello world]({{ site.baseurl }}/assets/img/screenshots/gethellofriends.png)

## Wrapping up
You now have the basic information you need to get started with Solidity. There is much more to learn, but hopefully this is enough to get you started. There are more links at the bottom to continue your Solidity adventure. Good luck out there!

## See more
* [Build an Unstoppable Counter with Solidity]({{ site.baseurl }}/2018/06/23/solidity.html) - Build an unstoppable counter! You can keep counting and counting. What will you do with this power?
	
## Other resources
* [Truffle Framework](https://truffleframework.com/) - A development framework for Ethereum 
* [Superblocks Studio](https://studio.superblocks.com/) - Easy dapp development 
* [CryptoZombies](https://cryptozombies.io/) - A fun Solidity tutorial series 
	