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
