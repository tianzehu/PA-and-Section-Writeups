# PA2-HashMaps-Key (Status: Released 1/22/18 8:30am)
PA2-HashMaps assignment key and initial assignment writeup draft.

## Learning Objectives

The goal of this assignment is to learn how to use the dictionary abstract 
data type in Java.  

In Java, a HashMap implements a dictionary.  By the end of the assignment 
you will have practiced using the following operations on a HashMap:
  * insertion,
  * deletion,
  * modifying the value for a particular key,
  * iterating over all of the key,value pairs, and
  * the fact that HashMaps do NOT store their key,value pairs in order 
    and how to handle it.

## The Assignment

For this project we will be using flight data that you can download from 
the following website: 
https://www.kaggle.com/open-flights/flight-route-database.
When you click the Data tab and then try to download the routes.csv
file, you will be asked to create a kaggle account.
The easiest way to do so is to create a kaggle account with your UA email by 
selecting the Google option under sign up with one click. 

Similarly to PA1, you will be taking an input file on the command line. 
However, the input will be slightly different as it is in csv format. 
You can read more about the input format on the kaggle description. 

The program should have the following usage:
```
    java PA2Main infile COMMAND optional
```
In addition to the input file, the second command-line argument will be a 
command to run on the data from your input file. The commands consist of 
MAX, DEPARTURES and LIMIT. 

Each command will be most easily implemented with a HashMap.  Therefore,
your implementation will read in the csv file and be using one
or more HashMaps.

***MAX*** - This function prints the airport with the maximum number 
of total flights.  The total flights includes both arriving 
and departing flights for each airport.  In the case of ties, keep 
track of all airports with the maximum number of flights
and output them alphabetically, see decomposition below for 
help and PublicTestCases/cmdMAX-test1.out for formatting. 

***DEPARTURES*** - The goal of this function is to print an alphabetical 
list of all destinations an airport flies to. Each airport with its 
destinations should be outputted on a separate line, see Output below 
or PublicTestCases/cmdDEPARTURES-test1.out for a visual. 
    

***LIMIT*** - The limit function requires an additional integer argument 
on the command line.  This integer is used as a cut off to eliminate 
airports that have a total number of flights less than or equal to the limit. 
So, this function is similar to MAX as it relies on a mapping of airports to 
the total number of flights. After the totals are calculated, the airports 
with a total number of flights less than or equal to the limit should be 
ignored and only the remaining airports should be output in alphabetical order. 
See Output below for formatting help and decomposition for help alphabetically 
ordering the airports.
Hint: To avoid a Concurrent Modification Exception, you cannot use remove 
when looping over the keys, you must use a supplementary data structure. 

    
## Input and Output
Example input (see Kaggle for entire file and more in-depth description):
```
airline	airline ID	 source airport	 source airport id	 destination airport	 destination airport id	 codeshare	 stops	 equipment
2B	410	AER	2965	KZN	2990		0	CR2
2B	410	ASF	2966	KZN	2990		0	CR2
2B	410	ASF	2966	MRV	2962		0	CR2
2B	410	CEK	2968	KZN	2990		0	CR2
```

MAX Output 
```
MAX FLIGHTS 3 : KZN
```

DEPARTURES Output 
```
AER flys to KZN
ASF flys to KZN MRV
CEK flys to KZN
```

LIMIT 1 Output 
```
ASF - 2
KZN - 3
```

## Getting Started

The process for getting started will be very similar to what was done in PA1.
* There is a github assignment link on the class web page --> resources link.
  Accept the assignment to have a github repository be created for you.
* Edit the .travis.yml file on github to put in your email address (the one
  associated with your github account).  Commit that change in github.
* Import your PA2 repository into Eclipse (see PA1 writeup for details).

If you didn't already provide us with your github ID,
fill out the google form at https://goo.gl/forms/Aeukbr19M8XXk1Uq1

## Decomposition Ideas

The section activity provides an introduction to reading csv files and
creating a hashmap for departures. Refer to this activity to get started. 

When selecting your keys and values consider what types you need them to be
to complete the command. 

Since HashMaps are unordered, special steps must be taken for them to be 
outputted in an ordered format. As shown below, take the set of keys and 
input it into an ArrayList of type String. Then use a Collections sort to 
sort the keys in place. Since the keys are sorted in the existing data 
structure, you do not need to set the Collections.sort() call to store a 
returned value.

```
	ArrayList<String> sortedKeys = new ArrayList<String>(APDepartures.keySet());
	Collections.sort(sortedKeys);
```

## Grading Criteria

Half of the PA2 grade will be correctness.  For this assignment, there
will be some private test cases.  Partial points will be given if just
one or two of the commands is implemented and works on those test cases.

The other half of the PA2 grade will be your decomposition and code clarity.

Decomposition
* Should carefully select data structures that implement the 
  required functionality.  For example, if you avoid using HashMaps,
  it will probably result in more complicated code and thus points off.

* Should just use static methods in the single PA1Main class.

* Use a single file.  This should be a small program (<300 lines).

* Each static method should be less than 30 lines.

* Make things as simple as possible.
  * Avoid nested loops.
  * Avoid nesting conditionals.
  * Avoid chaining, i.e., too many levels of user-defined methods 
    calling other user-defined methods.


Code Clarity
* YOU should be able to read, understand, and explain your own code
to someone else a couple days after you wrote it.

* The file header should include instructions on how someone would
use this program.

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

