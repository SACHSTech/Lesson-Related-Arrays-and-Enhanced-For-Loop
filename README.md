# Related Arrays and Enhanced For Loops

This lesson covers two additional techniques to manipulate and traverse arrays.

## 1. Related Arrays

### Goal
Store connected pieces of data using two (or more) arrays whose **indices correspond**, allowing us to treat the arrays together as a unified data structure.

## Design Approach
Two arrays are considered *related* when element `i` in one array refers to data that matches element `i` in another.  
This lets us keep separate lists (e.g., names and scores) but still treat each pair as a single “record.”

Typical use cases:
- `firstName[]` and `lastName[]`
- `players[]` and `scores[]`
- `products[]` and `prices[]`
- `countries[]` and `populations[]`
- `cities[]` and `temperatures[]`

When using related arrays:
- ensure both arrays have the same length
- always use the **same index variable** when traversing them
- use **regular for loops**, not enhanced for loops, because you need index access

#### Example 1: Student Names and Grades

```java
String[] names = {"Ava", "Liam", "Noah", "Zoe"};
int[] grades = {85, 92, 77, 90};

for (int i = 0; i < names.length; i++) {
    System.out.println(names[i] + " scored " + grades[i]);
}
```

#### Example 2: Product and Price Lookup

```java
String[] products = {"Milk", "Eggs", "Bread", "Apples"};
double[] prices = {2.99, 3.49, 2.50, 4.25};

for (int i = 0; i < products.length; i++) {
    System.out.println(products[i] + " costs $" + prices[i]);
}
```

#### Example 3: Country and Population

```java
String[] countries = {"Canada", "Japan", "Brazil"};
int[] populationMillions = {38, 125, 214};

for (int i = 0; i < countries.length; i++) {
    System.out.println(countries[i] + ": " + populationMillions[i] + " million");
}
```

### Why Related Arrays Matter
Related arrays let us keep different pieces of information connected by using the same index. This is useful when the data naturally comes in pairs or groups.

When applying the technique of related arrays, make sure to:
- keep arrays the same length  
- always traverse them using the same index variable  


## 2. Enhanced For Loop (*for-each*)

### Goal
Use a simpler loop structure when you only need to *read* each value in an array, one at a time, in order. 

### Design Approach

A regular `for` loop gives you the index, which lets you access positions, update values, and work with related arrays:

```java
int[] marks = {72, 85, 90};

for (int i = 0; i < marks.length; i++) {
    System.out.println("Index " + i + ": " + marks[i]);
}
```

This prints:
```
Index 0: 72
Index 1: 85
Index 2: 90
```

In this form, you can use `i` for:
- finding the last element  
- modifying an element (e.g., `marks[i] = ...`)  
- using the same index for two related arrays (e.g., `names[i]` and `scores[i]`)  

An **enhanced for loop** (also called *for-each*) automatically gives you each **value**, not the index:

```java
int[] marks = {72, 85, 90};

for (int mark : marks) {
    System.out.println(mark);
}
```

This prints:
```
72
85
90
```

This form is ideal when you:
- only need the value  
- are reading, printing, summing, or counting  
- are not modifying the array  
- are not working with related arrays  


### Choosing names for the loop variable
The loop variable should describe the **kind of data** you are handling. For example:

```java
for (String name : names)
for (int mark : marks)
for (double temp : temperatures)
for (char letter : letters)
```

Note the differentiation between *singular* (individual array element) and *plural* (array of elements).

Avoid vague names like `x`, `item`, or `thing`.

The examples below show the enhanced for loop in the situations where it shines: clean, readable processing of each element when the index is irrelevant.

#### Example 1: Printing names

```java
String[] players = {"Ana", "Ben", "Ming", "Hermione"};

for (String player : players) {
    System.out.println(player);
}
```

#### Example 2: Counting how many scores are passing

```java
int[] scores = {98, 55, 40, 91, 30};

int count = 0;

for (int score : scores) {
    if (score >= 50) {
        count++;
    }
}

System.out.println("Passing scores: " + count);
```

#### Example 3: Finding the total (sum)

```java
int[] prices = {5, 3, 10, 2};

int total = 0;

for (int price : prices) {
    total += price;
}

System.out.println("Total = " + total);
```

#### Example 4: Reading characters from a character array

```java
char[] vowels = {'a', 'e', 'i', 'o', 'u'};

for (char vowel : vowels) {
    System.out.println("Vowel: " + vowel);
}
```

#### Example 5: Printing temperatures with units

```java
double[] temps = {18.5, 20.1, 22.8};

for (double temp : temps) {
    System.out.println(temp + " °C");
}
```


## Summary

- **Related arrays** let us store connected data across multiple arrays where index alignment matters.
- Use **regular index loops** when you need index access or are working across multiple arrays.
- Use the **enhanced for loop** when you only need the values and want cleaner syntax.

<br>

# Practice Problems — Related Arrays & Enhanced For Loops
Annotated solutions to this problem set can be found [here](SOLUTIONS.md).

## Problem 1 — Print Names With Scores
Create two related arrays:

- `String[] names` with 5 player names
- `int[] scores` with 5 corresponding scores

Print each player’s name and score on the same line using a regular index-based loop.

### Example Output
```
Ana: 12
Ben: 22
Ming: 18
Lila: 31
Kai: 15
```

## Problem 2 — Highest Score and Player
Using the same two related arrays (`names[]` and `scores[]`):

Write code to find:
- the **highest score**
- the **name** of the player who earned it

Then print the pair together.

### Example Output
```
Top player: Lila with 31 points
```

## Problem 3 — Average Temperature Using Enhanced For
Ask the user for **5 temperature readings** and store them in a `double[] temps`.

Use an enhanced for loop to compute the average.

### Example Output
```
Average temperature = 21.44 °C
```

## Problem 4 — Count Honour Roll Students
Given:
```java
int[] averages = {81, 90, 99, 78, 77, 94};
```
Use an enhanced for loop to count how many students have made the honour roll with an average of 80 percent or higher.

Print the count.

### Example Output
```
Honour roll students: 4
```

## Problem 5 — Month and Days Lookup
Create the following related arrays:
```java
String[] months = {"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"};
int[] days    = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
```

Ask the user for a month abbreviation (e.g., `"Apr"`).  
Find the matching index and print how many days are in that month.

### Example Output
```
Enter a month: Apr
Apr has 30 days.
```

## Problem 6 — Sum of Prices
Given:
```java
double[] prices = {5.99, 3.50, 12.00, 1.25};
```
Use an enhanced for loop to compute the total.

### Example Output
```
Total = 22.74
```

## Problem 7 — Find Matching Last Names
Create two related arrays:
```java
String[] firstNames = {"Amy", "Ben", "Chris", "Dana"};
String[] lastNames  = {"Lee", "Wong", "Wong", "Patel"};
```

Ask the user for a last name.  
Print all **first + last** name pairs that match the search.

### Example Output
```
Search last name: Wong
Ben Wong
Chris Wong
```

## Problem 8 — Mirror Copy (Reverse Using Index Loop)
Ask the user for **5 integers**, store them in an array, then create a **new array** where the values appear in reverse order.

Use a normal index loop (not enhanced for) to build the reversed array.

### Example Output
```
Original: 3 9 1 4 7
Reversed: 7 4 1 9 3
```

## Problem 9 — Count How Many Are Even (Enhanced For)
Given:
```java
int[] nums = {3, 10, 4, 7, 12, 5};
```

Use an enhanced for loop to count how many numbers are even.
Print the final count.

### Example Output
```
Even numbers: 3
```

## Problem 10 — Parallel Search (Two Related Arrays)
Create two related arrays:
```java
String[] items = {"Pen", "Notebook", "Eraser", "Pencil"};
double[] costs = {1.25, 3.50, 0.99, 0.75};
```

Ask the user for the name of an item.  
Search for it using a regular for loop and print the matching price.

### Example Output
```
Enter item: Eraser
Price: $0.99
```
