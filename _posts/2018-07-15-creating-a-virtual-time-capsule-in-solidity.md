---
layout: post
title: Creating a Virtual Time Capsule in Solidity
tags: [Solidity, Payable, Keyword]
image: /assets/img/pexels/payable.jpg
excerpt_separator: <!--more-->
---

One of the coolest parts of Solidity is you can create functions that control and manipulate the ether cryptocurrency. When you mark a function as `payable`, it means the function can receive the ether cryptocurrency. Code itself can control value, with any `owner` that we want to specify with our imagination. Additionally, certain aspects of time can be relied upon without having to trust any single entity, only the network itself. In this example, we will create a contract that locks the ether given to it for a certain amount of time. Once the time has elapsed, the `owner` can get the ether back out. This is just a start to get you familiar with the syntax, but with your creativity and imagination you could make something much cooler.

<!--more-->

![Queue]({{ site.baseurl }}/assets/img/pexels/payable.jpg)
<p align="center"><i>I'm ready to use the Solidity payable keyword!</i></p>

## Getting Started
To get started with this tutorial, click [this link](https://remix.ethereum.org/#version=soljson-v0.4.24+commit.e67f0147.js&optimize=false&gist=ba4d6b66827dbbb6a257ba8b962ce434) to view the code in Remix, an Ethereum web IDE. Once you open the link, click gist on the left then select `timeCapsule.sol` to view the code. If you are just getting started with Solidity, you might have more luck starting with the previous tutorial, [Getting Started with Solidity]({{site.baseurl}}/2018/07/07/getting-started-solidity.html). Otherwise feel free to continue and good luck on your Solidity learning adventures! 

## Payable Keyword
One awesome part of Solidity is that you can create functions that accept the ether cryptocurrency as payment. Functions in Solidity will automatically reject if you send ether to them and they are not `payable`. In order for a function to accept ether, you need to add the `payable` keyword to the function. There are a few different places where the `payable` keyword is used in this example: the `constructor`, the `fallback` function, and this example's custom `destroyCapsule` function.

## The constructor
{% highlight js %}
constructor() payable public {
    owner = msg.sender;
    withdrawTime = now + 365 days;
}
{% endhighlight %}

The `constructor` is called exactly once when a contract is created and never again after that. In this example, we set two variables: `owner` and `withdrawTime`. `owner` is the `owner` of the time capsule. We want to make sure others cannot destroy the time capsule, only the `owner` can. The second variable is how long this contract with lock the ether given to it. In this example, we set it to `now + 365 days`. `now` refers to the current block timestamp, which is roughly around the time when the contract is created. Since the `constructor` is `payable`, that means it can receive ether as payment when the contract is first created. The amount of ether stored by the contract can be seen by checking the value of `address(this).balance`.

## The fallback function

{% highlight js %}
function () payable public {
}
{% endhighlight %}

The `fallback` function is called whenever a contract receives ether without a function name. If this function did not exist, then it would not be possible to transfer ether to this contract via normal transactions. Using the `fallback` function to accept ether makes it easier for other contracts to send value to this contract. Other contracts can send ether to this contract by calling Solidity's built-in `transfer` function.

## destroyCapsule function
{% highlight js %}
function destroyCapsule() payable public {
    require(msg.sender == owner);
    require(now > withdrawTime);
    selfdestruct(owner);
}
{% endhighlight %}

`selfdestruct` is a built-in function in Solidity that will destroy the current contract and send all ether stored in the contract to the address specified. In this example, we are sending all the contract's ether back to the `owner` only if the `withdrawTime` has elapsed. `require(msg.sender == owner)` ensures this will only be run by the `owner`. `require(now > withdrawTime)` requires that the current block's timestamp is further into the future than the `withdrawTime` set in the `constructor`. Since we set `withdrawTime` to `now + 365 days`, that means we cannot withdraw the ether back out for approximately one year. The exact time of the `now` keyword can be manipulated by miners to a certain extent, but not enough to affect this use case drastically.

## Time in Solidity
The `now` keyword in solidity refers to the current block's timestamp. The timestamp must be greater than the timestamp of the previous block and fall somewhere between the timestamps of the next two consecutive blocks to be valid. So the timestamp is not always exactly the same time as the current timestamp, but it does roughly follow the current time. For the purposes of a year time capsule it works. But if you wanted to make some contract where every second counts, you may not be able to rely so heavily on the accuracy of the `now` keyword.

## Testing in Remix
1. Open the source code by clicking [this link](https://remix.ethereum.org/#version=soljson-v0.4.24+commit.e67f0147.js&optimize=false&gist=ba4d6b66827dbbb6a257ba8b962ce434)
2. Click gist on the left, then open `timeCapsule.sol`
3. Click Compile on the right
4. Click the run tab, and change your settings to look like this:
![Capsule Settings]({{ site.baseurl }}/assets/img/screenshots/capsuleSettings.png)

If you click Deploy, we will create a contract that will only let you withdraw the 5 ether passed into it once a year has passed. After deploying, click getBalance to see the amount of ether being stored by the contract:

![Capsule Settings]({{ site.baseurl }}/assets/img/screenshots/capsuleGetBalance.png)

The contract shows 5000000000000000000 because 1 ether has 18 decimal places. The smallest unit of ether is called a wei, so 1 ether is equal to 1000000000000000000 wei. Next, we can call destroyCapsule and see what happens:

![Destroy Fail]({{ site.baseurl }}/assets/img/screenshots/destroyFail.png)

As you can tell, we got an error because one year has not elapsed yet. It's not very practical to wait a year while testing, so try changing the value of time to `60 seconds` in the code and follow the instructions above to test again. You'll see after the time has elapsed we get a success:

![Destroy Succeed]({{ site.baseurl }}/assets/img/screenshots/destroySucceed.png)

## Wrapping Up
This was just a start to get familiar with some of the different keywords and built in functions to Solidity. What would you change to make this contract more useful? Looking forward to reading your comments. Thanks for reading and have a wonderful day.

## See also
* [Build an Unstoppable Counter with Solidity]({{ site.baseurl }}/2018/06/23/solidity.html) - Build an unstoppable counter! You can keep counting and counting. What will you do with this power?
* [Getting Started with Solidity]({{site.baseurl}}/2018/07/07/getting-started-solidity.html) - If you would like to learn how to get started with Solidity

## Other resources
* [Truffle](https://truffleframework.com/), which has a good selection of [tutorials](https://truffleframework.com/tutorials).
* [Ganache](https://truffleframework.com/ganache), often paired with Truffle. It's a fast Ethereum RPC client for testing and development of smart contracts.
* [Superblocks Studio](https://studio.superblocks.com/), a web IDE similar to Remix but also adds an easy way to create a website that interacts with your smart contract.