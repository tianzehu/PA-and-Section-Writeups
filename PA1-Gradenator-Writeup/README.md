# PA1 Gradenator (Status: Draft, 12/22/17)

The goals for PA1 are to get started with Java and figure out how to 
calculate your current CS 210 grade.

## Input File

Each line should be in the following format:
```
  <string with no commas>, <number>%, <number> <number> ...
```
  
Specifically a string with any characters except a comma, a comma, a
double in the inclusive range 0 to 100 [0,100], a comma, and one or more
doubles in the inclusive range 0 to 100 [0,100] separated by one or more
spaces. The Java Scanner class with its nextLine() method can handle whatever
line ending your file system uses.

Example input (see the syllabus for percentages):
```
  final, 20%, 80
  programming assignments, 25%, 90 60 80
```

An overall grade will be calculated by averaging the grades listed at the end
of each line (e.g. avg(90 60 80) ==> 76.67) and then computing a total grade
based on the percentages indicated on each line (e.g. 0.20\*80 + 0.25\*76.67
==> 35.17). Note that if the input percentages do not add up 100%, then the
total grade will not be out of 100%. In the example above the best possible
grade would be 20% + 25% ==> 45%.

The output will be the average grade per line and a total line. Example
output:
``` (FIXME: how would output actually be formatted?  Have the key do percents as integers.  Change the spec above.)
  final, 20%, 80
  programming assignments, 25%, 76.66666666666667
  TOTAL = 35.17% out of 45%
```

Your PA1 program can assume that all input follows the format. Any input that 
does not follow the input format will result in undefined behavior.

## Getting Started

0. Fill out the google form at https://goo.gl/forms/iwkZLI61EtIXECOv1 to
provide us your github id.  We cannot collect your assignment unless you do.

(FIXME: update the link when have the actual assignment ready)
1. Use the assignment URL https://classroom.github.com/a/ffjzXCRo to set 
up a github repository.  And then clicked on that repository in your 
web browser (pa1-gradenator-yourgithubid).

There is a tutorial with screen shots for steps 2 through 4 at
https://docs.google.com/document/d/1CjE24ccurIDIHjMTgvu4cUuhKtMgUQKxjYaL3zH_nOE/edit?usp=sharing.

LEFTOFF: FIXME: still editing this.
5. Setting up automatic testing of your program with the public test cases.
   We are using Travis CI to run our grade script on your program and the
   publicly available test cases in the PublicTestCases/ subdirectory of your
   repository.  To make this work you need to edit the .travis.yml file.
    4. Within 5-10 minutes, you should receive an email from Travis CI to
    your github email address letting you know that your current program is NOT
    passing the public test cases.  However, if the program compiles in Eclipse,
    then it should compile with the grading script.

2. Click on the green "Clone or download" button on the right of the web page
and copy the provided URL.  It should look like 
(https://github.com/UACS210Spring2018/pa1-gradenator-yourgithubid...).

3. Import your PA1 repository into Eclipse.
    1. Open up Eclipse on a lab machine or your machine (if you are working on
       your own machine, you will need to install Eclipse).

    2. File —> Import —> Git —> Projects from Git, Next, Clone URI, Next,
       paste in repository URL from github

    3. Next, Select the master branch, Next, make the local destination 
       /home/username/eclipse-workspace/pa1-gradenator-yourgithubid.  
       This is where the local git repository will be placed.

    4. Next, Import existing Eclipse projects, Next, Finish.

    5. Test that it runs.  Right click on the PA1Main.java file, Run As, 
       Run Configurations.  Select Java Application and then for the 
       Program Arguments paste in (PublicTestCases/inputReal1.in), 
       without the parens.  This is the relative path to a sample input 
       file.  Then click Run.

4. Edit, commit, and push a small change to the program.
    1. Put the code `System.out.println("Hello");` into the main method.
    
    2. Run the program and see that "Hello" is printed to the Eclipse Console.
    
    3. Right click on PA1Main.java --> Team --> Commit, move unstaged files
       that you want to commit into staged changes, put in a commit message,
       and then click commit and push.


## Testing your program

If your program cannot compile and run, then you should feel very
uncomfortable.  Experienced programmers write a little bit of new functionality
and then quickly compile and run it.  When you ask CS 210 staff questions
about your program, we will want to see that it compiles and runs.  Comment
out new stuff you have added until it compiles and runs.  Show us what compiles 
and runs, and then add the one small piece that breaks it.

We recommend you do a commit every time you add a small piece and your
program compiles and run.  We recommend a commit and push at least once
a day to see where you stand with the grading script and the public
test cases.

System.out.println is your friend.  It can help you figure out what 
the value of variables are at various points in your program.


## More than one revision

The first time we write a piece of a program, it is really a draft.
We want to get the syntax right and figure out the functionality.
After that, we need to fix our initial comments so they clarify
what the code is doing.  Help your future self and others who
will be reading your code.  Plan on rewriting pieces of your
program multiple times to produce a professional and clear program.


## Decomposition Ideas

The first set of Drills will help with figuring out how to decompose and
implement this program.  Here are some Java classes and methods that might
also be helpful (lookup online examples of how to use these and what their 
parameter and return values are):
* System.out.println() is your friend
* new Scanner(System.in)
  * hasNextLine()
  * nextLine()
  * close()
* String
  * substring()
  * indexOf()
  * trim()
  * split()
* Iterating over an array of strings,
  https://www.guru99.com/foreach-loop-java.html


## Grading Criteria

Half of the PA1 grade will be correctness.  For this assignment, if your
program works for all of the test cases in PublicTestCases/, then you will
earn all of the correctness points.

The other half of the PA1 grade will be your decomposition and code clarity.

Decomposition
* Should just use static methods in the single PA1Main class.

* Use a single file.  This should be a small program (<200 lines).

* Each static method should be less than 30 lines.

* Make things as simple as possible.
  * Avoid nested loops.
  * Avoid nesting conditionals.
  * Avoid too many levels of user-defined methods calling other
  user-defined methods.


Code Clarity
* YOU should be able to read, understand, and explain your own code
a couple days after you wrote it.

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

