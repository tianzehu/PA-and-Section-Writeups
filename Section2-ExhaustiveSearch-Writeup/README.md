# Section2-ExhaustiveSearch-WriteUp (Status: DRAFT, 1/28/18, noon)

## Introduction 
Today's section will be an introduction to the algorithmic structure of exhaustive
search and will help prepare you for PA3. The first part of the section will be
to generate all of the binary numbers for an N-bit number, in ascending order. 
The second part of the section will be to generate all of the possible dice roll
combinations for a six sided dice. This section will also reinforce your skills 
relating to arrays and recursion. 

Exhaustive search is where every possible solution is iterated over. This is also
known as the brute force approach. In many cases, exhaustive search is the simplest
solution to think of, but it is usually an inefficient solution. Throughout the 
semester we will introduce you to different search algorithms so you will be able
to see for yourself. 

Reminder: We encourage paired programming during section, so please work through the 
section activity with the student sitting next to you. Remember, in section you can 
share code. For programming assignments you cannot.

## Setup 
Go to the course webpage, click resources, and then click on the Section 2
URL.  It will be the URL for accepting the github classroom assignment
for Section 2.

Then you need to edit your .travis.yml file in your section2 repository on 
github, and then clone and import the Section 2 gitrepo.
  * Click on .travis.yml in github.  Then put in your email and commit that change on
    github. If you do not do this, you will run into issues later with pushing and
    TravisCI. 
  
  * Click on the green "Clone or download" button on the right of the web page 
    and copy the provided URL.

  * Import your Section 2 repository into Eclipse.
    * open Eclipse 
    * File —> Import —> Git —> Projects from Git, Next, Clone URI, Next, paste 
      in repository   URL from github
    * Next, Select the master branch, Next, make the local destination 
      /home/username/eclipse-workspace/Section2-ExhaustiveSearch-yourgithubid.
    * Next, Import existing Eclipse projects, Next, Finish.

Now you are ready to start coding. 

## The Assignment
This is the first assignment where you will have multiple classes. Part One should
be completed in the Section2Binary.java file and Part Two should be completed in the
Section2Dice.java file. 

Part One: Exhaustively print out 0-2^N - 1, where N is the number of bits, in ascending
order in binary.  	

Part Two: Exhaustively print out the dice rolling combinations for 5 six sided dice. 

### Step 0
Copy the code below into main and run it to make sure it compiles and prints. 
This initiates the first TravisCI build.  

```
        System.out.println("Welcome to Section 2!");
```

Then commit and push your changes to github. Here is a reminder of the steps:
Right click on Section1Main.java --> Team --> Commit, move unstaged files 
that you want to commit into staged changes, put in a commit message, and 
then click commit and push.



### Part 1 - Binary Introduction 
For Part 1 of this section we are not reading in a file from the command line, 
as this task does not rely on external input. We are completing a class that 
generates and prints out in ascending order all of the binary representations 
of the numbers 0-2^N - 1, where N represents the number of bits. 

For example, if N = 2, then the output would be:
```
00
01
10
11
``` 

If you would like a more in depth understanding of binary, refer to the lecture 
slides or do a quick Google search. Additionally, this activity relies on the 
enumerate and process structure described in class, so you should refer to those 
slides for help while working through this section. 

#### Step 1 
Start by declaring an integer in main to represent N, the number of bits. Set 
this integer equal to 5. 

Travis will be testing your output against the binary numbers of 0-2^5 - 1 in 
ascending order. Although it is not necessary to declare a variable to hold N, 
since Travis will only test for N = 5,  having a variable declared is better 
coding style as opposed to leaving 5s floating around in your code. This also 
allows you to alter your code at a single point to see outputs for higher bit 
binary numbers.

#### Step 2 
Consider what decisions need to be made in order to enumerate over all of the 
binary numbers starting from 00000 and getting to 11111. Discuss the following
questions with your paired programming partner. 

What parameters do you need with your enumerate method? What do these parameters
represent? How large should your array be that is holding the selected bits? 

What value, 0 or 1, should you start setting each bit to? What part of the 
enumeration method relates to changing the bit's value? 

How should you move to the next index of the bit being changed? How will
you achieve this in your recursive enumeration call? 

Look back at the lecture slides to recall the format of the enumerate and 
process structure and copy over any necessary code. 

#### Step 3
The enumerate and process structure requires a recursive call of the enumerate 
method. To conclude this activity, you need to implement process and select
a base case condition. Think and discuss with your partner the following 
questions. 

What two parameters should be equal for you to stop the recursion? 

Where should the base case be located in your enumerate function? 

Where should you call process? What should you pass process as a parameter? 

### Part Two - Dice Introduction 
Again, we are not reading in a file from the command line, as this task does 
not rely on external input. We are completing a class that generates and prints 
out in ascending order all of the possible combinations of 5 six-sided dice 
being rolled. The initial set of rolls outputted will be 11111 and the final 
set of rolls outputted will be 66666. This activity is very similar to the 
previous binary activity, so make sure to complete that activity first and 
reuse the enumerate and process structure here. 

#### Step 1 
Start by declaring an integer in main to represent the maximum number of dice 
to be rolled and set this integer equal to 5. 

Travis will be testing your output against the output for rolling 5 six-sided 
dice, but again it is good style to use variables to represent a value used
throughout your code. 

#### Step 2 
Consider what decisions need to be made in order to enumerate over all of the 
possible roll combinations. Discuss the following questions with your paired 
programming partner and refer back to your Part 1 decisions if you get stuck.  

What parameters do you need with your enumerate method? What do these parameters
represent? 

How large should your array be that is holding the value of the dice rolls? 

What value should you start setting each die to? Is this a different value than 
the start value used during the binary activity? 

How should you move to selecting the value of the next roll? How will
you achieve this in your recursive enumeration call? 

Look back at Part 1 or the lecture slides to recall the format of the enumerate 
and process structure to copy over any necessary code. 

#### Step 3
The enumerate and process structure requires a recursive call of the enumerate 
method. To conclude this activity, you need to implement process and select
a base case condition. Think and discuss with your partner the following 
questions. 

What two parameters should be equal for you to stop the recursion? 

Where should the base case be located in your enumerate function? 

Where should you call process? 


*** Remember to show your SL your output on Eclipse before leaving section. *** 


## Resources

The Java API and Google are your friend, look up methods to take advantage of 
Java's libraries. 

* System.out.println() is your friend for testing and output 
* Declaring an array:
	* int[] array = new int[5]; 
* Updating a value in an array: 
	* array[0] = 1; 
