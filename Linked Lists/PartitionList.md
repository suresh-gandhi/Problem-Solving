## Problem Statement

We are given a linked list and a value x, partition it such that all the nodes less than x come before nodes greater than or equal to x.

__NOTE__: The relative order of the nodes in each of the two partitions should be preserved.

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


