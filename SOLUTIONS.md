# Related Arrays & Enhanced For Loops — Annotated Solutions

Each solution includes explanations to help understand the logic, purpose, and flow of each problem.

## Problem 1 — Print Names With Scores

Use a regular index loop because we must access two related arrays using the same index.

```java
public void run() {
    String[] names = {"Ana", "Ben", "Ming", "Lila", "Kai"};
    int[] scores = {12, 22, 18, 31, 15};

    // Traverse using same index i for both arrays
    for (int i = 0; i < names.length; i++) {
        System.out.println(names[i] + ": " + scores[i]);
    }
}
```

## Problem 2 — Highest Score and Player

Track the best score seen so far while scanning the arrays. Update both the score and name whenever a new maximum is found.

```java
public void run() {
    String[] names = {"Ana", "Ben", "Ming", "Lila", "Kai"};
    int[] scores = {12, 22, 18, 31, 15};

    int bestScore = scores[0];     // start by assuming first entry is best
    String bestPlayer = names[0];  // matching name

    // Start loop at index 1 because we already used index 0
    for (int i = 1; i < scores.length; i++) {
        if (scores[i] > bestScore) {
            bestScore = scores[i];
            bestPlayer = names[i]; // update matching player
        }
    }

    System.out.println("Top player: " + bestPlayer + " with " + bestScore + " points");
}
```

## Problem 3 — Average Temperature Using Enhanced For

Enhanced for loop simplifies reading values when index is not needed. We read the temperatures first, then sum them.

```java
public void run() {
    double[] temps = new double[5];

    // Read input into array using index loop
    for (int i = 0; i < temps.length; i++) {
        temps[i] = readDouble("Enter temperature #" + (i + 1) + ": ");
    }

    double total = 0;

    // Use enhanced for to accumulate values
    for (double temp : temps) {
        total += temp;
    }

    double average = total / temps.length;
    System.out.println("Average temperature = " + average + " °C");
}
```

## Problem 4 — Count Honour Roll Students

Use enhanced for to count elements satisfying a condition.

```java
public void run() {
    int[] averages = {81, 90, 99, 78, 77, 94};

    int count = 0;

    // Enhanced for is ideal for tallying
    for (int avg : averages) {
        if (avg >= 80) {
            count++;
        }
    }

    System.out.println("Honour roll students: " + count);
}
```

## Problem 5 — Month and Days Lookup

We search both related arrays using an index loop. If a match is found, we print and immediately exit using `return`.

```java
public void run() {
    String[] months = {"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug",
                       "Sep", "Oct", "Nov", "Dec"};
    int[] days = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};

    String input = readLine("Enter a month: ");

    // Search for index that matches the input
    for (int i = 0; i < months.length; i++) {
        if (input.equals(months[i])) {
            System.out.println(input + " has " + days[i] + " days.");
            return;  // exit method after printing result
        }
    }

    // Only prints if no match was found
    System.out.println("Month not found.");
}
```
You usually see `return` used to *return a value* from methods. Here, `return` in a `void` method simply ends the method early. This is a clean way to stop scanning once the answer is found.

### Alternate Solution w/o `return`
If you don't want to use `return`, here's an alternate solution that stores whether a match was found using a boolean flag and prints it afterwards. 

```java
public void run() {
    String[] months = {"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug",
                       "Sep", "Oct", "Nov", "Dec"};
    int[] days = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};

    String input = readLine("Enter a month: ");

    boolean found = false;  // track whether we find a match
    int index = 0;          // store matching index if found

    for (int i = 0; i < months.length; i++) {
        if (input.equals(months[i])) {
            found = true;
            index = i;
        }
    }

    if (found) {
        System.out.println(input + " has " + days[index] + " days.");
    } else {
        System.out.println("Month not found.");
    }
}
```

Note that this alternate solution isn't as performant as using `return` to exit the loop early. In the best case scenario, the user enters `Jan` and the loop exits after one iteration using `return`. In the alternate case, `Jan` is found, but the loop continues to run another 11 times, consuming additional CPU resources.

We don't really explore efficiency of algorithms until Grade 12, but it is worth noting here.


## Problem 6 — Sum of Prices

Enhanced for is cleanest when summing all values in a single array.

```java
public void run() {
    double[] prices = {5.99, 3.50, 12.00, 1.25};

    double total = 0;

    // Accumulate total using for-each
    for (double price : prices) {
        total += price;
    }

    System.out.println("Total = " + total);
}
```

## Problem 7 — Find Matching Last Names

Use two related arrays and check last names to print matching name pairs.

```java
public void run() {
    String[] firstNames = {"Amy", "Ben", "Chris", "Dana"};
    String[] lastNames  = {"Lee", "Wong", "Wong", "Patel"};

    String search = readLine("Search last name: ");

    // Use index loop to keep first+last combined at matching positions
    for (int i = 0; i < lastNames.length; i++) {
        if (search.equals(lastNames[i])) {
            System.out.println(firstNames[i] + " " + lastNames[i]);
        }
    }
}
```

## Problem 8 — Mirror Copy (Reverse Using Index Loop)

Build a new array where each element is filled from the end of the original. 

```java
public void run() {
    int[] original = new int[5];

    // Read values from user
    for (int i = 0; i < original.length; i++) {
        original[i] = readInt("Enter number #" + (i + 1) + ": ");
    }

    int[] reversed = new int[original.length];

    // reversed[i] = original[last - i]
    for (int i = 0; i < original.length; i++) {
        reversed[i] = original[original.length - 1 - i];
    }

    // Print original
    System.out.print("Original: ");
    for (int i = 0; i < original.length; i++) {
        System.out.print(original[i] + " ");
    }
    System.out.println();

    // Print reversed
    System.out.print("Reversed: ");
    for (int i = 0; i < reversed.length; i++) {
        System.out.print(reversed[i] + " ");
    }
}
```

Note the careful manipulation of array indices using `.length` and relative positions in both the forward and reversed array.

## Problem 9 — Count How Many Are Even

Condition-based counting using enhanced for.

```java
public void run() {
    int[] nums = {3, 10, 4, 7, 12, 5};

    int count = 0;

    // Boolean condition inside for-each
    for (int n : nums) {
        if (n % 2 == 0) {
            count++;
        }
    }

    System.out.println("Even numbers: " + count);
}
```

## Problem 10 — Parallel Search (Two Related Arrays)

Search for a matching string and print the related value at the same index.  
Use a regular index loop because enhanced for cannot access positions.

```java
public void run() {
    String[] items = {"Pen", "Notebook", "Eraser", "Pencil"};
    double[] costs = {1.25, 3.50, 0.99, 0.75};

    String search = readLine("Enter item: ");

    // Search for item using matching index
    for (int i = 0; i < items.length; i++) {
        if (search.equals(items[i])) {
            System.out.println("Price: $" + costs[i]);
            return; // stop method after finding a match
        }
    }

    System.out.println("Item not found.");
}
```
