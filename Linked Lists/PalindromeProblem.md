## Problem Statement

We are given a singly linked list. All we have to do is to determine whether it represents a palindrome or not.
    
## Sample Illustration

  * Input:
              
               head -> 1 -> 2 -> 4 -> 2 -> 1 -> null 
               
    Output: 
      
               True
    
 * Input:
 
               head -> 1 -> 3 -> 4 -> 9 -> null 
               
   Output: 
   
               False
    
## Intuition

### Very Intuitive Thoughts

Since a palindrome is symmetric, moving from both the ends simultaneously towards each other and comparing seems like a good approach. 
It is illustrated below:

   ![linkedlistpalindrome](https://user-images.githubusercontent.com/22399995/36960881-f038c6ce-206e-11e8-8f1d-0f8b7b02bec4.gif)

Alternatively, we can also start from the middle and move simultaneously towards both the ends. It is illustrated below:

   ![linkedlistpalindromeopp](https://user-images.githubusercontent.com/22399995/36960883-f0c8e6aa-206e-11e8-9d64-fc808074be70.gif)

One thing common in both of these approaches is that the __pointers always move in different directions__. 
                                                
### Why it is not so simple for our singly linked list?

For a singly linked list(which we are given with) the linking is always in one direction and therefore it is not possible
to move our pointer in the opposite direction of the linking. :confused:

### What can we do for it?

Since we have to traverse in opposite directions in both of our approaches, all we can do is __reverse either the first half or the second half of the linked list keeping the other half as it is.__

Consider our second approach. Here we moved away from the middle to either ends simultaneously and compared at each step. To use this approach for our linked list we can ->

1. Reverse the first half of the linked list(we will traverse in the opposite direction on this part i.e. from the middle to the left).
2. Keep the other half as it is(we will traverse from the middle to the right here). 
3. Now we have two linked lists and simply comparing these lists would yield our answer. :blush:

Inorder to reverse the first half, we should have an access to the middle node of the list. 

### Finding the middle node of the linked list

* A natural and simple way is to first find the length of the linked list and then move our pointer halfway. 
* A clever approach would be to make two pointers fast and slow. Move the fast pointer at two nodes per iteration and the slow pointer at one node per iteration. Eventually when the fast reaches the last node(in even lengthed list) or when the fast reaches null(in odd lengthed list), the slow pointer would point to the middle of the list. This approach is illustrated through an animation below:

![linkedlistpalindromehelper](https://user-images.githubusercontent.com/22399995/37052614-d95f2bf0-219f-11e8-8ecc-dc5ec405e397.gif)

We have the middle of the linked list now. All we need to do is now reverse the first half. Reversing a linked list is systematically explained [here](http://summigandhi.com/) and can be referred.

## Java Implementation

    /**
     * Definition for singly-linked list.
     * public class ListNode {
     *     int val;
     *     ListNode next;
     *     ListNode(int x) { val = x; }
     * }
     */

    public boolean isPalindrome(ListNode head) {
        if(head == null){                           
            return true;
        }
        
        // these pointers will help in finding the middle of the linked list.
        ListNode slow = head;
        ListNode fast = head.next;
        
        // these pointers will help in reversing the linked list. 
        ListNode past = null;
        ListNode future = slow.next;
        
        // going till the middle and reversing the first half of the list.
        while(fast != null && fast.next != null){
            slow.next = past;
            past = slow;
            slow = future;
            future = future.next;
            fast = fast.next.next;
        }
        
        // comparing lists at the last.
        if(fast == null){
            return compare(past, future);
        }
        else{       
            slow.next = past;
            return compare(slow, future);
        }
    }

## Code Animation

![linkedlistpalindromecode](https://user-images.githubusercontent.com/22399995/37053847-47d332ae-21a3-11e8-9e28-d86557141dce.gif)

## Think
* Our approach was to reverse the first half and keep the second half the same. It can also be done by reversing the second half and keeping the first half same. Writing the code for it could be a good programming practice.
* What is the time and space complexity of our approach?

