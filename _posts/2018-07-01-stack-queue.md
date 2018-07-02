---
layout: post
title: Stack vs Queue
tags: [Stack, Queue]
image: /assets/img/pexels/stack.jpg
excerpt_separator: <!--more-->
---

Today you will learn the basics of what a stack and a queue are. Stacks and queues are ordered lists of things. They could be strings, numbers, or anything else you can think of. Stacks and queues each have a unique way of adding and removing elements from their data structure. In a stack, you push elements when you add them and pop elements when you remove them. In a queue, you enqueue elements when you add them and dequeue elements when you remove them.
<!--more-->

![Rock Balancing]({{ site.baseurl }}/assets/img/pexels/stack.jpg)
<p align="center"><i>A stack of stones</i></p>

## Rock Balancing

Rock balancing is the art of stacking stones on top of each other without them falling. It is common to see these stacks of rocks at the beach. Rock balancers push stones to the top of the stone stack. If they wanted to remove a stone, they would pop the stone off of the top. The stones are added one on top of the other. This is exactly how stacks work as well. You use a stack when you want to store and access data in a LIFO order, or last-in-first-out order. The last stone you add is the first stone you have access to if you want to remove one.

![Queue]({{ site.baseurl }}/assets/img/pexels/queue.jpg)
<p align="center"><i>A queue for some good German food</i></p>

## Queue

The queue data structure stores data in a FIFO order, or first-in-first-out order. One example of this is a line for your favorite restaurant. The first person to stand in line is the first one to get served. Everyone else queues up behind them. A computer scientist would say they enqueue themselves onto the line. And when they got their food, they would say they have been dequeued from the line. The first element enqueued onto a queue is the first element to be removed when dequeued.

## Why

Many problems can be solved easier thanks to queue and stack abstractions. For example, in a depth-first search of a tree, you could use a stack to go down a tree until you reach a leaf. Once you reach the leaf, you pop back to get to the next path. You can use a queue to do breadth-first search of a tree. At each depth of a tree, you can add the next path to go down onto a queue. Once you are done with one level of the tree, you can dequeue it and go to the next level. Hope that helps you on your computer science journey.

