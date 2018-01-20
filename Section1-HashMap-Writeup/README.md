# Section1-HashMap-WriteUp 

## Introduction 
Today's section will be an introduction to Java HashMaps and it will prepare
you for PA2 by farmiliarizing you with the relevant data set. Hashmaps are
similar to Python's dictionaries. The similarities include both data structures
being a mapping from keys to values and that they are unordered data structures.
Below are some of the basic Java hashmap methods compared to their equivalent 
python method. 

Java					vs 	Python 

get(key); 			|	get(key)

put(key, value);		| 	dict[key] = value

remove(key);			|	pop(key); 


Here is a link to Java's API that describes the HashMap data type and how 
to use all of its built in constructors and methods: https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html

The Java API is a great resource for better understanding the lanaguge and
I encourage you to utilize this resource as you are learning about Java this
semester. Additionally, we encourage paired programming during section, so 
please work through the section activity with the student sitting next to you. 

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
the relevant data read in from the input file. The HashMap will have the 
three letter airport code as keys and the number of flights as the values. 	

### Step Zero 
Copy the code below into main and run it to make sure it compiles and prints. 


```
        System.out.println("Welcome to Section 1!");
```

Then commit and push your changes to github. Here is a reminder of the steps:
Right click on Section1Main.java --> Team --> Commit, move unstaged files 
that you want to commit into staged changes, put in a commit message, and 
then click commit and push.



### Step One - Open the file 
Similarly to PA1 you will be reading in a file from the command line. Begin 
by initializing a Scanner object, or other file reader of your choice, as 
demonstrated in class. Test that you are able to open routesSec1.csv when 
given the file on the command line. 

If you get stuck, here is example code demonstrating the use of Scanner.

```
public static void main(String[] args) {
	Scanner input = null; 
	
	System.out.println("args[0]="+args[0]);
	try {
		input = new Scanner(new File(args[0]));
		while (input.hasNextLine()) {
			System.out.println(input.nextLine());
		}
		input.close();
	} catch (Exception ex) {
		ex.printStackTrace();
	}
}
```
The scanner input is initialized to null at the beginning of main so that the
count departures method can be called outside of and after the try catch block. 

### Step Two - Construct the HashMap 
Before declaring your HashMap, think about the mapping structure you will need 
to keep track of the number of departing flights for each airport. What should 
be stored in your keys and values? What types should they be? Remember to 
discuss your ideas with your partner. 

Hint: There are many types in Java, consider solutions that use Strings, Arrays 
and/or Ints. There are several designs that would work, so try to think of a 
few different designs. 

Here is an example HashMap declaration. This example demonstrates the suggested 
types for the HashMap and is what will be referenced through the remainder of 
the activity. 

```
HashMap<String, Integer> airportToNumFlights = new HashMap<String, Integer>();
```
The HashMap declaration should occur in the countDepartures method. This method 
is also where the reading of the data will occur and the HashMap created will 
be returned to main for printing. Since the reading will occur in the function, 
the scanner must be passed into the countDepartures method as a parameter.  

### Step Three - Read the data into the HashMap 
Read in each line and process the string to place it into your HashMap.* Since 
each line contains data about a new flight, your HashMap should be altered for 
each line in the file. Use the put(key, value) method to add a new key to your 
list and replace(key, value) or put(key,value) to update a key if necessary. It
is interesting to note that put(key, value) will replace the value stored in the
HashMap if the key exists already with the value passed in as a parameter and so
will replace(key, value). 

It is important to note, the file you will be reading in is routesSec1.csv. CSV
means comma separated values, so each value in each row is separated by a comma.
Since this is the case, what should each line be split on? 

Below is a reminder of how to use the split method. 

```
String[] strs = s1.split(" ");
```

Determine which element of the array you will need to access in order to read in
the source airport. The three letter source airport code will be your key and the
count of flights will be your value. What value should you initialize each key to?
When should you increment the value? How should you update the value?  

Hint: The get(key) method returns the value associated with the key 

*See Resources below for a reminder about methods relating to Scanner and String. 

### Step Four - Output the Results 
Once you have totaled all departing flights, print the output with this format:
Three Digit Airport Code - Number of flights 

Example 

```
 MRV - 1
 GYD - 1 
```

Remember a HashMap is unordered, so you will have to take the following step 
to alphabatize the output in order to run it through TravisCI. In the code 
below, the set of key airport codes are retrived from the HashMap by calling
keySet() on the HashMap airportToNumFlights. These key values are then stored
in an ArrayList in order to complete a sort on them that will place them in 
alphabetical order. The Collections sort is an inplace sort, so you do not 
need to store a return as the keys are sorted inside of the exisiting 
data structure. 

```
ArrayList<String> airportsSorted = new ArrayList<String>(airportToNumFlights.keySet());
Collections.sort(airportsSorted);
```

Now it is possible to iterate over the HashMap and have output print in 
alphabetical order. This can be done via the following loop. The loop 
iterates over each element in the ordered list airportsSorted and then 
access the corresponding value in the HashMap. 

```
for (String airport : airportsSorted) {
	System.out.println(airport + " - " + airportToNumFlights.get(airport));
}
```

## Reminders
* System.out.println() is your friend
* new Scanner(new File(args[0]))
  * hasNextLine()
  * getNextLine()
  * close()
* String
  * substr()
  * indexOf()
  * trim()
  * split()


