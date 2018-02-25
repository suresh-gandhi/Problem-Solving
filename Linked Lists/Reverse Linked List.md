## Problem statement

You need to make changes to the given linked list in such a way that now it starts from tail of the given linked list and ends on head of the given linked list. 

Also, you need to reverse the direction of each of the links(next pointers) between adjacent nodes. 

![Example](https://vichargrave.github.io/img/reverse_linked_list.png)

## Intuition

If we observe the problem, it is telling us to just reverse all the next pointer links only(also to set the next of head to NULL). 

Now, for reversing a link we just need to set the next pointer of node B to node A as shown:-

....... A B C node of a linked list ........

But, if we link the next pointer of node B to node A, then we can't reach the node C from anywhere !!

For this we could save the next node(node C) too in another variable and go on repeating this process until we have reached NULL pointer. This whole process would be more clear in the next section.

## Detailed Procedure
 
For ease of understanding, we will have 3 pointers namely past, present and future.

1. "present" refers to the right node as referred earlier

2. "past" refers to the left node as referred earlier

3. "future" refers to the next node of right node as referred earlier

....... Present Past Future picture ........


Initially we have:-

- present = head

- past = NULL  {as there is no node left of head}

- future = none  {It could be set to present->next but will give error in case when present is NULL}

Now, inorder to reverse we just need to follow these steps:-

```
while present is not null :
  
  // Set future as the node to the right of present
  future = present->next
  
  // Linking part: Changes the next of present to past
  present->next = past
  
  // past moves forward
  past = present
  
  //present moves forward
  present = future

// When present has reached null past is the node left to this null, which is our new head to be returned
return past
```

## C++ Implementation

```
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
    
        ListNode *past = NULL, *present = head , *future;
        
        //Do until present has reached NULL
        while(present){
        
            future = present->next;
            
            //Linking the next pointer of present to past(i.e. reversing this link)
            present->next = past;
           
            past = present;
            present = future;
        }
        
        return past;
    }
};
```

### Further Thoughts for readers

Just go ahead and think of all the side cases that could happen in this problem(For Ex- Given linked list is NULL etc.). And, also check whether the code discussed above is capable enough to deal with it or not.
