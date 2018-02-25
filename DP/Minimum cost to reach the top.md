## Problem Definition

On a staircase, the i-th step has some non-negative cost cost[i] assigned (0 indexed).
Once you pay the cost, you can either climb one or two steps. You need to find minimum cost to reach the top of the floor, and you can either start from the step with index 0, or the step with index 1.

Input: cost = [10, 15, 20]
Output: 15
Explanation: Cheapest is start on cost[1], pay that cost and go to the top.


# Intuition

The main observations that are pretty obvious are:-

- We can only jump 1 or 2 step further.
- We need to reach the top.

Both these observations makes much more sense when thought simultaneously i.e. we can reach the top using either the last stair or 2nd last stair only.
Now suppose for simplicity we had only 2 elements( Ex- cost = [10 , 15] ). 
In this case we just need to select minimum of the two:
1. cost of the last element
2. cost of the 2nd last element

For our bigger problem, we just need to consider the cost to reach either of the 2 elements i.e.
For finding the minimum cost to reach the top, we just need to select the minimum of these two:

1. Minimum cost to reach the last element  +  Cost of the last element
2. Minimum cost to reach the 2nd last element  +  Cost of the 2nd last element

This would give us the minimum cost to reach the top for the given array.

### Recurrence relation and Optimal substructure

In the previous section we saw that in order to * * optimally * * reach the top we need to solve 2 similar problems that are:

1. Finding the * * minimum * * cost to reach the last element
2. Finding the * * minimum * * cost to reach the 2nd last element

So, we could say the recurrence relation for this problem is:    
       * *       T(n)             =             T(n-1)                      +            T(n-2)                                +        O(1)     * *
     {min cost to reach the top}      {min cost to reach the last element}     {min cost to reach the 2nd last element}    {Finding the min. of the two}

We also observe here that we took optimal solution for the smaller problems inorder to reach to the optimal solution for the given problem.
Hence, we could say that it shows * * Optimal Substructure Property * *.

### Overlapping subproblem

Consider for example an array, cost = [1, 2, 1, 4, 5, 2].
For this we have recurrence relations as follows:-  
* *T(6) = T(5) + T(4) + O(1)
T(5) = T(4) + T(3) + O(1)
T(4) = T(3) + T(2) + O(1)
.... * *

Here, we observe that T(3) is repeated in 2nd as well as 3rd equation i.e. we are solving it again.
As we go on solving for this problem we see many such repeated calculations. Hence, in order to be efficient we need to save this 
