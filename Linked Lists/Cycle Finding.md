## Problem Statement

We are given a singly linked list. We have to determine whether it has a cycle or not.

## Sample Illustration

__Input:__

![linkedlistcycleinputno](https://user-images.githubusercontent.com/22399995/37087100-51d48b32-221f-11e8-841f-d53864e10e70.jpg)

__Output:__ 
  
        False 


__Input:__ 

![linkedlistcycleinputyes](https://user-images.githubusercontent.com/22399995/37087122-6491b524-221f-11e8-9629-77ea555cde77.jpg)

__Output:__ 
  
        True
        
## Intuition

### What do we mean by a cycle?

If a list does not have a cycle then traversing the list from start to end would be visiting each node exactly once. It is illustrated in gif below:

![linkedlistcyclehelper](https://user-images.githubusercontent.com/22399995/37089070-6295b18e-2225-11e8-8344-117beee31873.gif)

But if the linked list has a cycle then we would loop around again and again. Hence we would be visiting the visited nodes multiple times. Illustrated below:

![linkedlistcyclehelper1](https://user-images.githubusercontent.com/22399995/37090290-c3cdbd08-2229-11e8-82ba-dea3ec0502b9.gif)

So basically somehow if we keep a track of visited nodes, then our problem is solved. This is because before visiting a node we can simply check if it is already visited. If it is => we have a cycle. If not => we never dealt with a node which was visited multiple times and so our list does not have a cycle. Bingo! :smirk:

### How can we keep track of visited nodes?
To keep track of the visited nodes we need to keep track of that property of a node which is unique to that node. Obviously we can't use the __data of a node__ here as two nodes may have the same data in them. However we can use the __address of a node__ for sure as it is unique.

Let us make a container __C__. Everytime we encounter an address we will check if it is already present in our container. If it is => cycle, else we repeat this for the next node. Clearly if there is no cycle in our linked list, we will reach null eventually and every node would have its address inserted into __C__.

It is better illustrated through an animation below:

![linkedlistcyclehelper2](https://user-images.githubusercontent.com/22399995/37115970-c346cb06-2272-11e8-806a-7afc33765382.gif)

## Java Implementation:


     public boolean hasCycle(ListNode head) {
     
        Set<ListNode> set = new HashSet<ListNode>();  //our container C
        
        ListNode temp = head;  // used for traversing the whole list
        
        while(temp != null){
            if(set.contains(temp)){  // if the address is already present in our container
                return true;
            }
            set.add(temp);
            temp = temp.next;
        }
        
        return false;  // if temp has reached the end and we found no repetitions.
     }

## Think: 
* What is the time and the space complexity of this solution?
* Can we do it without using our container C or in general without using any extra space? :confused:







 
