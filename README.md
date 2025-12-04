# Related Arrays and Enhanced For Loops

This lesson covers two additional techniques to manipulate and traverse arrays.

## 1. Related Arrays

### Goal
Store connected pieces of data using two (or more) arrays whose indices correspond.

### Design Approach
Two arrays are considered *related* when element `i` in one array refers to data that matches element `i` in another.  
This lets us keep separate lists (e.g., names and scores) but still treat each pair as a single “record.”

Typical uses:
- `firstName[]` + `lastName[]`
- `players[]` + `scores[]`
- `months[]` + `daysInMonth[]`

### Example: Players and Scores

```java
String[] players = {"Ana", "Ben", "Ming", "Lila"};
int[] scores = {12, 22, 18, 31};

// Print each name with matching score
for (int i = 0; i < players.length; i++) {
    System.out.println(players[i] + ": " + scores[i]);
}
```

### Why this technique matters
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
