# PA3-ExhaustingPastries-Key (Status: DRAFT, 1/28/18 at 11:30am)

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
unique pastries the customer can purchase.


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

## Simple Example

As an example, consider the PublicTestCases/simple.in file:
```
10
baguette: 2 3 3 4
```
The customer has a $10 budget.  The pastry shop has only a baguette that is
4 inches long.  A one-inch pieces is $2, a two-inch pieces is $3, a three-inch
piece is $3, and a four-inch piece is $4.

The idea is to enumerate over all possible ways to cut up the pastry and
determine which cutting costs the most and thus makes the most for the
baker.

Below is an enumeration of all possible ways to cut the baguette based
on number of pieces of each size.  The last column is how much money
such a cutting will make.  The baker will want to pick the highest one.
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

Then the customer will buy the maximum number of unique pastries they can with
their budget.


## Error Checking
For this assignment, you will be responsible for developing checks on the input data.

Required error checking:
```
If an invalid file is given then print:
'ERROR: File not found' and exit with a status code of 1

If budget is not a number print:
'ERROR: Incorrect budget input' and exit with a status code of 1

If any price per length is not a number print:
'ERROR: Incorrect price input' and continue reading in values, ignoring the non numeric value.
  ```
  

Any pastry with no prices given will considered length 0 for price 0.

## Examples

### Example 1
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
ERROR: Incorrect price input
Baguette: 240
Blank Pastry: 0
Cheese Cake: 248
Chocolate Cake: 873
The max number of unique pastries that can be bought with $300 is: 2
```

Notice the two error print outs. First error because the 'Chocolate Cake' pastry has a 'z' in it, and second
error because the 'Blank Pastry' is of length 0

### Example 2
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


## Getting Started
You will first need to consider all the different combinations of cuts and compare their prices to find the best one. 
For example, consider the following baguette:
```
baguette 2, 8, 4, 6

This baguette can be sliced into lengths of 1, 2, 3, and 4. 
Possible combinations are:
 A single length 4 slice for $6
 A slice length 3 for $4 and a slice length 1 for $2
 Two slices length 2 for a total of $16
 Four slices length 1 for a total of $8
 Two slices of length 1 and one slice of length 2 for a total of $12
 
 The best way to slice would be 2 slices for $8 each. Set this as the cost for baguettes.  
```

You will need to consider how to exhaustively search through all possible slicing combinations to find the best one.

After you have set all the prices for the pastries, put yourself in the shoes of the customer. For example:
```
Your budget is $30.
baguette = $16
cupcake = $12
pie = $14
cookie = $4

The highest amount of unique pastries you can buy are the cookie, cupcake, and pie for 3 pastries total.

You can only buy 2 if you buy the baguette.

```

Print the max number of unique pastries when you have found it:
"The max number of unique pastries that can be bought with $budget is: " followed by an int value.
So the example above would print:
"The max number of unique pastries that can be bought with $30 is: 3" 

## Testing your program <----- UNFINISHED


Upload it to gradescope under the current project, and you will be able to see which test cases were passed/failed.


## Decomposition Ideas <----- UNFINISHED

Section activites
* System.out.println() is your friend
* Recursion is your friend
* new Scanner(File)
  * hasNextLine()
  * nextLine()
  * next()
  * nextInt()
  * close()
* String
  * trim()
  * split()
* Collections
  * add()
  * sort()
* Iterating over an array of strings,
  https://www.guru99.com/foreach-loop-java.html


## Grading Criteria

Half of the PA2 grade will be correctness.  For this assignment, there
will be some private test cases.  Partial points will be given if just
one or two of the commands is implemented and works on those test cases.

The other half of the PA2 grade will be your decomposition and code clarity.

Decomposition
* Should carefully select data structures that implement the 
  required functionality.  For example, if you avoid using HashMaps,
  it will probably result in more complicated code and thus points off.

* Should just use static methods in the single PA2Main class.

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

For PA2, you are required to submit your PA2Main.java file to Gradescope.
