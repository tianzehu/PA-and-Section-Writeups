# PA3-ExhaustingPastries-Key (Status: Posted, 1/29/18 at 10:30am, Edited, 1/30/18 at 11:20am)

PA3-ExhaustingPastries project writeup.

## Learning Objectives
The goal of this assignment is to practice the following decomposition, algorithm pattern, and data structure approaches.

 - Algorithmic pattern: exhaustive search

 - Decomposition approach: separating out iteration over all possibilities from the evaluation of each possibility

 - Data structure: arrays and collections

The assignment will also require checking that the input data is valid.

## The Assignment

For this assignment, you are simulating a bakery.
You will be given an input file which lists every pastry the bakery is selling today.
The pastries can be cut into slices which are sold for different amounts depending on their length.
Your goal is to maximize the bakery's profits by finding which combination of slices 
will maximize your profits.
Once you have sliced the pastries and set their prices, you will take the role 
of the customer. Given a certain budget, you will find the maximum number of 
unique pastries the customer can purchase.  The customer will be buying all
of any one pastry.


## Input File

The program should have the following usage: 

```
java PA3Main inputFile
```

The input file should have the following format:
```
<customer budget integer>
<string>: <integer cost of 1in slice> <integer cost of 2in slice> <integer cost of 3in slice> ...
<string>: <integer cost of 1in slice> <integer cost of 2in slice> <integer cost of 3in slice> ...
...
...
...
```
The first integer is the budget customers have for buying pastries. 
This is followed by a list 
of pastries, starting with a pastry name, then followed by the price for 
length of 1 unit, price per length of 2 units, etc.
The file could have any number of lines and each pastry line could have any number of length costs.
If a pastry has X costs after it, then it is X inches long.

## Example

As an example, consider the PublicTestCases/simple.in file:
```
5
baguette: 2 3 3 4
donut: 1 2 3 4
baumkuchen: 1 2 3 4 
```
The customer has a $5 budget.  The pastry shop has a baguette that is
4 inches long with one-inch pieces costing $2 each, 
two-inch pieces costing $3 each, three-inch pieces costing $3 each, 
and a four-inch piece is $4 each.  The baker also has a donut
and a baumkuchen that can be broken into 1in pieces for $1 each,
2inch pieces for $2 each, etc.

For the baker, the idea is to enumerate over all possible ways to cut 
up the pastry and determine which cutting costs the most and thus 
makes the most for the baker.
For the customer, the idea is to buy as many full pastries as possible.

### Baker perspective

Below is an enumeration of all possible ways to cut the baguette based
on the number of pieces of each size.  The last column is how much money
such a cutting will make.  The enumeration is not showing combinations
that are not physically possible.  For example, a 4in baguette cannot be
broken into 5 1in pieces.
The baker will want to pick the highest one.
```
 #1in #2in #3in #4in  $$
   0   0    0    0    0
   1   0    0    0    2
   2   0    0    0    4
   3   0    0    0    6
   4   0    0    0    8
   1   1    0    0    5
   2   1    0    0    7
   1   0    1    0    5
   ...
```

A similar enumeration should be done for the donut and the baumkuchen.

### Customer perspective

Then the customer will buy the maximum number of unique pastries they can with
their budget.  For this example the customer would
do the following enumeration over combinations that cost less than the budget:

```
baguette donut baumkuchen  cost   #unique
   0       0        0        0       0
   0       4        0        4       1
   0       0        4        4       1
```

Here we have a tie.  For ties the customer will buy the item
that comes first alphabetically.  Thus for this example
the customer would choose the baumkuchen.

Here is what the final output would be for this example:

```
baguette costs $8
baumkuchen costs $4
donut costs $4

Can buy baumkuchen for $4

The max number of unique pastries that can be bought with $5 is: 1
```

For this simple example, the budget of $5 is enough to buy
the $4 configuration of the baumkuchen.  It could buy the donut
instead, but since either could be bought, the on that comes
alphabetically first is selected instead.

### Other points to consider

* The lines containing the pastry costs are listed in 
alphabetical order by the name of each pastry.

* The lines which show each 
unique pastry that can be bought are listed in ascending order by price, 
and within each price listed alphabetically.

* You can assume the prices are separated by a single space.  We are not going
to have any tricky inputs with delimiters other than a single space.

* Any pastry with no prices given will considered length 0 for price 0.

* When a customer buys a pastry, they buy all pieces of the pastry.
  The bakery only has the one pastry of each kind that it cut into pieces.
  This is a simplification to make the problem a bit easier.

## Error Checking
For this assignment, you will be responsible for developing checks on the input data.

Required error checking:
```
If an invalid file is given then print the following and exit the program:
'ERROR: File not found' and exit with a status code of 1

If budget is not a number print the following and exit the program:
'ERROR: Incorrect budget input' and exit with a status code of 1

If any price per length is not a number print the following, 
ignore that pastry, but continue processing:
'ERROR: Incorrect price input' and continue reading the other pastries
  ```
 
Any pastry with no prices given will considered length 0 for price 0.
This is NOT an error.

## More Examples

### An Example with an Error
Given the following input file:
```
300
Cheese Cake: 62 83 44 48 
Chocolate Cake: 97 100 11 49 z 96 28 33 45 
Baguette: 24 24 58 79 12 83 79 44 13 5 
Blank Pastry: 
```

The output should be: 
```
ERROR: Incorrect price input
Baguette costs $240
Blank Pastry costs $0
Cheese Cake costs $248

Can buy Blank Pastry for $0
Can buy Baguette for $240

The max number of unique pastries that can be bought with $300 is: 2
```

Notice the one error print out due to the 'Chocolate Cake' pastry has a 'z' in it.
Thus it is ignored, but processing continues.

Also notice that the lines containing the pastry costs are listed in 
alphabetical order by the name of each pastry. The lines which show each 
unique pastry that can be bought are listed in ascending order by price, 
and within each price listed alphabetically.

### Another Error Example
Given the following input file:

```
IncorrectBudget
Cheese Cake: 62 83 44 48 
Chocolate Cake: 97 100 11 49 96 28 33 45 
Baguette: 24 24 58 79 12 83 79 44 13 5 
Blank Pastry: 
```
The output should be: 
```
ERROR: Incorrect budget input

```



## Testing your program

When you commit and push, Travis CI will send you an email to let you know
if the public test cases failed.
We STRONGLY recommend you put some of your own test cases in PublicTestCases/.
Read grade.py to see how the .in and .out files should be named.
Also look at the examples that are already in the PublicTestCases/ subdirectory.

Upload it to Gradescope and you will be able to see 
which public test cases were passed/failed.


## Decomposition Ideas

See the slides from class and examples from Section 2 about 
performing exhaustive searches.  What will the stopping
criteria be for the TWO exhaustive searches this program
will need to do?



## Grading Criteria

Half of the PA3 grade will be correctness.  For this assignment, there
will be some private test cases.  Partial points will be given if just
one or two of the commands is implemented and works on those test cases.

The other half of the PA3 grade will be your decomposition and code clarity.

Decomposition
* Should carefully select data structures that implement the 
  required functionality.  For example, if you avoid using HashMaps,
  it will probably result in more complicated code and thus points off.

* Should just use static methods in the single PA3Main class.

* Use a single file.  This should be a small program (<300 lines).

* Each static method should be less than 30 lines.  This INCLUDES
  comments.  It is easier to read a function if it can all fit on
  one screen.

* Make things as simple as possible.
  * Avoid nested loops.
  * Avoid nesting conditionals.
  * Avoid chaining, i.e., too many levels of user-defined methods 
    calling other user-defined methods.  Putting most of the functionality
    in another static method that returns void that main calls is an 
    example of this.


Code Clarity
* YOU should be able to read, understand, and explain your own code
to someone else a couple days after you wrote it.

* There needs to be a balance between no comments and a comment for
every line in the program.  Either extreme will result in points off.

* The file header should include instructions on how someone would
use this program.  To use the program, one would need to know the
input file format.

* Use meaningful variable names.  Loop iterators can
be simple (i for integers, s for strings, n for numbers, etc.).

* The clearest code examples will be anonymously shown in class.

* The most obfuscated code examples will be anonymously shown in class
with suggestions for improvement.


The coding style in terms of spacing, etc. should be done automatically
every time you save in Eclipse.  As long as you stick with those defaults,
the syntax style should be fine.

Write your own code.  We will be using a tool that finds overly similar code.
I recommend that when talking with others about the assignment, do not write
anything down.

## Submission

For PA3, you are required to submit your PA3Main.java file to Gradescope.
