
# Inclusion–exclusion 

One of the most useful principles of enumeration in discrete probability and combinatorial 
theory is the celebrated principle of inclusion–exclusion. When skillfully applied, this 
principle has yielded the solution to many a combinatorial problem.



## Examples 

### Counting integers 
How many integers in {1,...,100} are not divisible by 2, 3 or 5?
Let S = {1,...,100} and P1 the property that an integer is divisible by 2, 
P2 the property that an integer is divisible by 3 and P3 the property that an integer is divisible by 5. 
Letting Ai be the subset of S whose elements have property Pi we have by elementary counting: |A1| = 50, |A2| = 33, and |A3| = 20. 
There are 16 of these integers divisible by 6, 10 divisible by 10 and 6 divisible by 15. Finally, there are just 3 integers 
divisible by 30, so the number of integers not divisible by any of 2, 3 or 5 is given by:

100 − (50 + 33 + 20) + (16 + 10 + 6) − 3 = 26.


### Euler problem 193 
