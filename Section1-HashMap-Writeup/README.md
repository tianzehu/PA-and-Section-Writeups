# Section1-HashMap-WriteUp 

## Introduction 
Today's section will be an introduction to Java HashMaps and it will prepare
you for PA2 by farmiliarizing you with the relevant data set. Hashmaps are
similar to Python's dictionaries. The similarities include a mapping from 
keys to values and the keys are unordered. Below are some of the basic Java 
hashmap methods compared to the equivalent python method. 

Java					vs 	Python 

get(key); 			|	get(key)

put(key, value);		| 	dict[key] = value

remove(key);			|	pop(key); 


Here is a link to Java's API that describes the HashMap data type and how 
to use all of its built in constructors and methods: https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html

The Java API is a great resource for better understanding the lanaguge and
I encourage you to utilize this resource as you are learning about Java this
semester. 

## Setup 
The first step is to clone and import the Section1 gitrepo. 

Click on the green "Clone or download" button on the right of the web page 
and copy the provided URL.

Import your Section1 repository into Eclipse.
- open Eclipse 
- File —> Import —> Git —> Projects from Git, Next, Clone URI, Next, paste in repository URL from github
- Next, Select the master branch, Next, make the local destination /home/username/eclipse-workspace/Section1-yourgithubid.
- Next, Import existing Eclipse projects, Next, Finish.

Now you are ready to get started coding. 

## The Assignment
Overview : Read in the given file from the command line and calculate the 
number of departing flights for each airport by using a hashmap that stores
the relevant data read in from the input file. 

### Step One - Open the file 
Similarly to PA1 you will be reading in a file from the command line. Begin 
by initializing a Scanner object, or other file reader of your choice, as 
demonstrated in class. Test that you are able to open routesSec1.csv when 
given it on the command line. 

### Step Two - Construct the HashMap 
Before declaring your HashMap, think about the mapping structure you will need 
to keep track of the number of departing flights for each airport. What should 
be stored in your keys and values? What types should they be? 

Hint: There are many types in Java, consider solutions that use String, Lists, 
Arrays and/or Ints. There are several designs that would work, so try to think 
of a few different designs. 

Once you have determined the types you would like to use, declare your HashMap. 
HashMap<Type1, Type2> nameOfHashMap = new HashMap<Type1, Type2>();

### Step Three - Read the data into the HashMap 
It is important to note, the file you will be reading in is routesSec1.csv. CSV
means comma separated values, so each value in each row is separated by a comma. 

Read in each line and process the string to place it into your HashMap.* Since 
each line contains data about a new flight, your HashMap should be altered for 
each line in the file. Use the put(key, value) method to add a new key to your 
list and replace(key, value) to update a key. 

*See Resources below for a reminder about methods relating to Scanner and String. 

### Step Four - Output the Results 
Once you have totaled all departing flights, print the output with this format:
Three Digit Airport Code - Number of flights 

Example 
```
 MRV - 1
 GYD - 1 
```

Remember a HashMap is unordered, so the following for loop format can be used:

for (DataType variableName : List) {
	System.out.println(variableName); 
}

In this case the List can be a list of the keys, so consider using the method
keySet() on your HashMap. 

## Reminders
* System.out.println() is your friend
* new Scanner(System.in)
  * hasNextLine()
  * getNextLine()
  * close()
* String
  * substr()
  * indexOf()
  * trim()
  * split()
