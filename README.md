# Assignment-01-2Sum-and-Complexity
The problem gives us a vector, and a target int. We have to use the brute hash to see the pros and cons 
of how each find the answer.

# Brut Force
It tries all possible solutions until the right one is found which means that it reads every singles pair of elements in the array
, and checks if each pair is the sum of the target.

#Time Complexity: O(n^2) 

Compares i and j each time until it gets the target sum, through nested loops(every single iteration i and j are compared).

Example:

={2,3,12,25,54}

target = 2

(i= 0 num = 2) compares (j= 1 num= 3) = 2+3 = 6.


+Space Continuity:O(1)

It only has 2 variables wich are i and j.

Example:

i= 0,1,2,3,4

j=1,2,3,4

# Hash
It just searches the number your looking for, and tells you where it exactly is without going through every possible solution.

+Time Complexity: O(n) 

 It goes once through list since it knows what look for.
 
 Example: 
 
 I need 2 -> Do I have what i need? -> Yes then return, if not just store. 

+Space Continuity:O(n)

Every single iteration gets a space made for them in the hash map.

Example: 

Apple -> Box 1

Pear -> Box 2

Pencil -> Box 3

Cat -> Box 4
