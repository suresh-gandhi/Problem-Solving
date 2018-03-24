## Problem Statement

We are given a linked list and a value x, partition it such that all the nodes less than x come before nodes greater than or equal to x.

__NOTE__: The relative order of the nodes should be preserved.

## Sample Illustration

__Input:__

        head -> 4 -> 5 -> 8 -> 2 -> 1 -> 3 -> null
        partitionAbout x = 3
        
__Output:__
    
        head -> 2 -> 1 -> 4 -> 5 -> 8 -> 3 -> null
        
__Animation:__

 ![sampleillustration](https://user-images.githubusercontent.com/22399995/37825344-727cd09a-2eb5-11e8-90b3-f9658d59ef94.gif)


## Intuition

### Some Initial Intuitive thoughts 
We can create an array of the same size as that of linked list. Now we can traverse the linked list and start filling out the array with the values that are smaller than the partition. Scan the array again and fill out our remaining array with values greater than or equal to the partition. Now simply put back the array values in our linked list. Obviously the relative order is preserved as we have never disturbed the order in our algorithm. 

The animation given below better illustrates this:

![intuition1](https://user-images.githubusercontent.com/22399995/37829339-a4fcc35e-2ec4-11e8-91d9-33d369a5ef3b.gif)

### Whats inefficient about it?
Well this works perfectly but the only problem is that, it uses an extra space which is nothing but our auxiliarry array. If the length of the given linked list is very large for this problem then this algorithm would require a very large extra space as well which makes it space inefficient. Is there anything we can do to restructure(or partition) our linked list without using any extra space? :confused:

### A Better Approach
All we have to do is to partition the existing linked list into two parts which are 1. less than part 2. greater than or equal to part.
So what we can do is make two buckets (A and B). We traverse the given linked list from left to right and put the nodes in the respective bucket based on whether the data it contains is less than or greater than/equals to the partition. At last we simply connect both of them in order.

The approach is better illustrated through the animation given below:
![intuition2](https://user-images.githubusercontent.com/22399995/37860785-d28dc85c-2f52-11e8-96ad-e08b969c1553.gif)

We are simply rearranging the nodes here and hence using no extra space. :blush:

We will make the two buckets using two dummy nodes([When and How to use dummy/sentinel nodes](https://www.summigandhi.com/)). This would greatly help us to smoothen our implementation.

## Java Implementation

     class Solution {
        public ListNode partition(ListNode head, int x) {
        
               ListNode dummy1 = new ListNode(-1);
               ListNode dummy2 = new ListNode(-2);
               ListNode temp1 = dummy1;
               ListNode temp2 = dummy2;
    
               for(ListNode temp = head; temp != null; temp = temp.next){             // traversing the given linked list
                  if(temp.val < x){                                                   // if it belongs to the first bucket
                        temp1.next = temp;
                        temp1 = temp1.next;
                  }
                  else{                                                               // else it should belong to the second bucket
                        temp2.next = temp;
                        temp2 = temp2.next;
                  }
               }
        
               temp1.next = dummy2.next;                                              // bucket1 end -> bucket2 start
               temp2.next = null;                                                     // bucket2 end -> null
        
               return dummy1.next;                                                    // return bucket1 start
        }
     }

## Code Animation
The code animation given below illustrates the code better:
![codeanimation](https://user-images.githubusercontent.com/22399995/37863909-680a01dc-2f8c-11e8-9ca8-db2ba80224b7.gif)

## Think
* Try coding this problem without the use of dummy nodes and see the difference in implementation and checking of edge cases?






