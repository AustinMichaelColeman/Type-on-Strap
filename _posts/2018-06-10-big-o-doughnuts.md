---
layout: post
title: Big O Explained With Doughnuts
tags: [Big O, Doughnuts]
excerpt_separator: <!--more-->
---

Do you love doughnuts? Do you love describing the efficiency of algorithms in the language of mathematics? If math is not your strong suit, no need to worry. Math is not so scary when you have doughnuts. Imagine one thousand doughnuts in front of you. Now imagine you want to eat a doughnut. What is the runtime of eating a doughnut? You pick up a doughnut and eat it. That would be constant time, or $$O(1)$$. The amount of time it takes to eat a doughnut is unaffected by how many doughnuts there are. Now imagine instead one of your favorite doughnuts is hidden among the thousand doughnuts. The amount of doughnuts you have to look through increases linearly, so the runtime of finding your favorite doughnut is $$O(n)$$. Big O allows you to compare how algorithms speeds change based on how the inputs change. An $$O(1)$$ algorithm is not necessarily always faster than an $$O(n)$$ algorithm. All it means is that some input exists where the $$O(n)$$ algorithm is more or less efficient than the $$O(1)$$ function. In this case, the $$O(n)$$ algorithm is slower in almost every case than the $$O(1)$$ algorithm. See the doughnut below:

<!--more-->

![Doughnuts]({{ site.baseurl }}/assets/img/pexels/doughnut-sprinkle.jpg)
<p align="center"><i>What is your favorite doughnut?</i></p>

## Linear and Constant Doughnuts

You go to your favorite bakery and the smell of freshly baked doughnuts has filled the room. Your baker friend made your favorite doughnut but it is in the pile of doughnuts. Imagine two algorithms for getting your favorite doughnut. The first is to search through every doughnut in the pile until you find the one you want. The second is bake your favorite doughnut from scratch. How does the runtime for these two algorithms change based on the number of doughnuts in the pile? In the first case, every doughnut you have to search through adds a linear amount of work, so it is $$O(n)$$. The second algorithm is unaffected by the number of doughnut in the pile, so it is $$O(1)$$. A constant function is not necessarily always faster than a linear function. It just means that at some point, a linear function will surpass a constant function as the size of the input grows. See the graph below:

![Doughnut Pile]({{ site.baseurl }}/assets/img/pexels/doughnuts.png)
<p align="center"><i>Mmmmmm doughnuts</i></p>

## Some Big O Runtimes

### $$O(\log n)$$
One example of an $$O(\log n)$$ algorithm is quick search. Imagine you had boxes of doughnuts with a name on each one. Imagine the boxes are sorted alphabetically. Your name is on one of the boxes and you are trying to find it. You look in the middle of the box pile first. If your name comes before that, you look halfway down the left. Otherwise you look halfway through the right. You repeat this process until you find their box. With each step, you eliminate half the choices. These kinds of algorithms take a large amount of input and after a few steps produce a result. After $$k$$ steps, you have eliminated $$2^k$$ of the $$n$$ possible results. Another way to write $$2^k = n$$ is $$k = \log n$$. 

![Doughnut Box]({{ site.baseurl }}/assets/img/pexels/doughnut-box.jpg)
<p align="center"><i>You found the box! Here is your reward.</i></p>

### $$O(n^2)$$
An example of $$O(n^2)$$ is filling a square box of length $$n$$ with doughnuts. How is the time to fill the square box affected as you increase the size of the box? With a square, every time you increase the width you increase the length by the same amount. So as you add $$n$$ meters to the square, the amount of extra room for doughnuts grows by $$n^2$$. 

![Squares]({{ site.baseurl }}/assets/img/pexels/squares.jpg)
<p align="center"><i>How many doughnuts do you think fit in each square?</i></p>

### $$O(2^k)$$
Imagine you want to make a big number and use a lot of stack space because that's how you roll. Also you love doughnuts, so you want to use the name of your favorite doughnut. You could try this:

	int makeAbigNumber(string doughnut)
	{
		if(doughnut.length <= 1) return 1;
		return makeABigNumber(doughnut.substring(0, doughnut.length - 1) + makeABigNumber(doughnut.substring(0, doughnut.length - 1));
	}

With a doughnut name of length $$n$$, it takes $$2^n$$ calculations to make the big number. The time it takes to calculate the number grows very fast, which means this algorithm is extremely slow. The runtime of this algorithm is $$O(2^n)$$. Can you think of another way to make an $$O(2^n)$$ algorithm relevant to doughnuts? Please share your knowledge in the comments. You will help doughnut and algorithm complexity fans everywhere.

![Skeleton at Computer]({{ site.baseurl }}/assets/img/pexels/computer-dead.jpg)
<p align="center"><i>You after calculating "Gluten free organic pumpkin spice doughnut with sprinkles and chocolate sauce"</i></p>

## Big O, Big Omega, and Big Theta
Big O comes from mathematics and has two cousins: big Omega ($$Ω$$) and big Theta ($$Θ$$). They all represent a bound on a runtime. Big O is an upper bound on a runtime. Big Omega is a lower bound on a runtime. Big Theta is a tight bound on the runtime of an algorithm: both the upper and lower bound. Big Theta is typically what the industry means by big O. When you search for your favorite doughnut in the pile, you look through at most $$n$$ doughnuts. That algorithm is $$O(n)$$ and mathematically speaking is also $$O(n^2)$$, $$O(n^3)$$, and $$O(2^n)$$. However, the software industry uses big O to mean the lowest upper bound and so $$O(n)$$ is the most useful description of the algorithm to the industry in this example. Big O, Omega, and Theta are different from the concept of best case, worst case, and average case though.

![Theta doughnut]({{ site.baseurl }}/assets/img/pexels/doughnut-theta.jpg)
<p align="center"><i>The industry would say Big Theta more if doughnuts were in the shape of Theta (ϴ).</i></p>

## Sprinkles, Syrup, Multiplication, and Domination
Imagine you want to add chocolate sauce and sprinkles to $$n$$ doughnuts. There are two ways to do this:

1. add sprinkles to each doughnut. then add chocolate syrup to each doughnut
2. add sprinkles and chocolate syrup simultaneously to each doughnut. 

Which one is faster? It depends. Maybe you are less coordinated doing two at a time so you slow down. Maybe it is faster to do one then the other. Maybe it is faster to do it one at a time. Big O tries to ignore these complicated details and look at how algorithms change when the size of the inputs change. So in big O notation, we drop the multiplication of constants. You might be tempted to say algorithm 1 is $$O(2n)$$ while algorithm 2 is $$O(n)$$, but we drop the constants and say they are both $$O(n)$$.

Big O also prefers dominant terms to non-dominant. For example, $$O(n^2 + n)$$ becomes $$O(n^2)$$. Big O represents an upper bound, which makes the $$+ n$$ irrelevant. You can imagine it like how many doughnuts you have. Imagine you have ten doughnuts. You could say you have less than eleven doughnuts and you could also say you have less than a thousand doughnuts. Both are true, but one might give you more useful information than the other. So an algorithm that is $$O(n)$$ is also mathematically $$O(n^2)$$, but typically we use big O to refer to the smallest upper bound. Another way to look at it is by dropping constants. $$n^2 + n < n^2 + n^2$$, and $$n^2 + n^2 = 2n^2$$. Then you can use the constant rule defined earlier. $$O(n^2 + n)$$ is also $$O(2n^2)$$ which is just $$O(n^2)$$. Therefore $$O(n^2 + n)$$ is $$O(n^2)$$. You cannot drop terms that you do not have information on though. In the case of $$O(n^2 + m)$$ you cannot drop $$m$$ because we do not have enough information on its growth. You cannot know for certain $$n^2 + m < n^2$$.

![Four doughnuts]({{ site.baseurl }}/assets/img/pexels/doughnut-four.jpg)
<p align="center"><i>Which doughnut is most dominating?</i></p>

## Best, Worst, Average Doughnut Cases
Algorithms have three different cases you can look at: best case, worst case, and average case. Best case scenario, your favorite doughnut in the pile is in the first doughnut you pick up. In that case, the algorithm would be $$O(1)$$. Worst case, you go through every doughnut and the last one you pick up is your favorite. So worst case, it is $$O(n)$$. On average, if there are $$n$$ doughnuts should find your favorite after $$n / 2$$ doughnuts. You might be tempted to call that $$O(n/2)$$. But remember in big O, we are not concerned with constants, just the rate of growth. So we can drop the $$/ 2$$ and say on average you will find a doughnut in $$O(n)$$ time. Most of the time the industry cares about the worst case scenario, that way they can guarantee the algorithm's runtime. 

![Case]({{ site.baseurl }}/assets/img/pexels/best-case.jpg)
<p align="center"><i>Best case this is filled with doughnuts</i></p>

## Complexity of Sprinkles and Syrup
Big O can describe different parts of a problem. Imagine you ordered $$n$$ boxes of doughnuts, but the baker accidentally put bagels instead of doughnuts in some of them. You also have stickers. You want to tell him how many boxes he got wrong. Here are two strategies you could employ:

1. Keep a running tally in your head. Open each box and count in your head if they had bagels in it. Then write the number of bagel boxes on one sticker.
2. For each box, put a sticker on the box if it has bagels in it. Then at the end, add up all the boxes with stickers on them.


Algorithm 1 is $$O(n)$$ in time, where $$n$$ is the number of boxes, and $$O(1)$$ when it comes to how many stickers used. No matter how many boxes there are, you will use a constant amount of stickers in algorithm 1: one. Algorithm 2 is $$O(n)$$ in time and $$O(n)$$ when it comes to stickers used. You have to mark each box, then go through each box again to add the numbers up. You might think this is $$O(n^2)$$ because you are going through each box twice, but that is incorrect. You also might be tempted to say going through each box is $$O(2n)$$ but remember in big O notation we drop constants and just say $$O(n)$$.


![Bagel]({{ site.baseurl }}/assets/img/pexels/bagels.jpg)
<p align="center"><i>Bagels, the delicious cousin of doughnuts.</i></p>


## Sprinkles and Syrup: Addition and Multiplication
Big O can have many different terms, and those terms can be added or multiplied. An example of addition would be, "add sprinkles to each round doughnut and then add syrup to each filled doughnut." That would be $$O(r + f)$$, where $$r$$ is the number of round doughnuts and $$f$$ is the number of filled doughnuts. An example of multiplication would be,  "Fill a swimming pool with doughnuts." That would be $$O(lwh)$$ because you are filling each length ($$l$$), width ($$w$$), and height ($$h$$) of the swimming pool with doughnuts. Changing the depth also changes how much more width and height of the pool you need to fill.

![Pool full of doughnuts]({{ site.baseurl }}/assets/img/pexels/pool.jpg)
<p align="center"><i>Pool full of doughnuts then you dive in it</i></p>

## The Magic of Amortized Time

Imagine you had a magic doughnut bag that can hold infinite doughnuts, except this bag has a special requirement. Every time the amount of doughnuts reaches a power of two, it gives you a new bag that lets you hold twice as many doughnuts as you currently have. So you need to move the doughnuts out of the old bag into the newer bag. How would you describe adding doughnuts to this bag in big O terms? Most of the time it does not matter how many doughnuts are in the bag, you just add the additional doughnut with constant time. But every power of two, you have to go through all your doughnuts and move them over. In that case, adding a doughnut takes $$O(n)$$ time. This is when amortized time comes in handy. 

As you add $$d$$ doughnuts, you need to move over the doughnuts to a new bag at sizes $$1, 2, 4, 8, ..., d / 2, d$$. If you add all these times together, you would get $$1 + 2 + 4 + ... + d / 2 + d$$, which is less than $$2d$$. If you find that hard to believe, imagine a square of doughnuts, then you add half a square of doughnuts to that. Then a quarter of a square of doughnuts. Then an eighth. You keep moving closer and closer but you never reach more than two squares of doughnuts. So if you add $$d$$ doughnuts, you will have to move at most $$2d$$ doughnuts. That means adding $$d$$ doughnuts take $$O(2d)$$ time and the amortized time for each doughnut you add is $$O(1)$$. Amortized time describes the time without taking into account the initial cost. 

![Magic bag]({{ site.baseurl }}/assets/img/pexels/magic-bag.jpg)
<p align="center"><i>You would still forget this magic bag in your trunk.</i></p>

## Doughnuts, Algorithm Complexity, and You
With a little help from doughnuts, Big O can be understood by anyone. Big O can be applied to your life and make it easier to compare doughnut eating algorithms. Big O is used to compare algorithms and how they grow as the inputs given to them change. Next time you pick up a doughnut, think about how you can apply what you learned about algorithm complexity analysis to the situation. Thanks for reading and enjoy your doughnuts.

![Person thinking]({{ site.baseurl }}/assets/img/pexels/thinking.jpg)
<p align="center"><i>All these doughnuts are making me want to learn about algorithm complexity</i></p>

