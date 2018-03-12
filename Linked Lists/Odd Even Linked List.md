## Problem Statement

Given a singly linked list, cluster all odd nodes together followed by the cluster of even nodes. While clustering you must not change 
the relative order inside these clusters.
It is also to be noted that here we are talking about the node number and not the value in the nodes. 

__**Note:__  It would be nice if you solve it without making a new linked list.

## Sample Illustration

__Input:__ 1->2->3->4->5->NULL,

__Output:__ 1->3->5->2->4->NULL.

## Intuition

For clustering all the odd nodes together we must link the 1st node to 3rd node, 3rd node to 5th and so on. And for clustering all the 
even nodes we must link the 2nd node to 4th node, 4th node to 6th and so on. And finally link the end of cluster1 to start of cluster2 and 
we are good to go.

![odd even linked list1](https://user-images.githubusercontent.com/22693609/37279827-ee9fd5d4-2611-11e8-8834-b33cba6d3eee.gif)


## Detailed Procedure

Now, for making the odd cluster we must maintain 2 pointers, one as its head and the other as its tail. Same goes for even cluster too. 
Inserting part in each of the cluster just adds the new node to its tail.


Animation for insertion :-


And at last we just link the end of cluster1 to start of cluster2.

Steps to follow are as follows:-

1. 
