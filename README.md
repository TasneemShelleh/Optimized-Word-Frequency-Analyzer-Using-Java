# Optimized-Word-Frequency-Analyzer-Using-Java-main

A Java-based word frequency analyzer that reads a large text file, counts word occurrences, and displays the top 10 most frequent words. The project uses multithreading to improve performance by dividing the input text into smaller parts and processing them in parallel.

This project demonstrates how multithreading, file handling, collections, and sorting can be used to optimize text processing tasks.

## Project Overview

The goal of this project is to analyze a text file and find the most frequent words efficiently. The program reads the content of a file named `text.txt`, splits the text into words, divides the words between multiple threads, counts the frequency of each word, combines the results, sorts them by frequency, and prints the top 10 most common words.

The project is implemented using Java and focuses on performance improvement using multithreading.

## Repository Structure

```text
Optimized-Word-Frequency-Analyzer-Using-Java-main/
│
├── MultithreadingApproach.java          # Main class that runs the word frequency analyzer
├── MultithreadingApproachThread.java    # Callable thread class for counting word frequencies
├── WordCount.java                       # Helper class for storing a word and its count
├── WordFrequencyPair.java               # Helper class for storing final word-frequency pairs
├── OS_project_report.pdf                # Project report/documentation
└── README.md                            # Project documentation
```

## Main Features

* Reads text from an input file
* Splits the text into words
* Divides the work among multiple threads
* Counts word frequencies in each thread
* Combines partial thread results
* Sorts words by frequency
* Prints the top 10 most frequent words
* Measures execution time
* Uses Java collections such as `ArrayList`, `TreeMap`, and `Future`
* Uses `ExecutorService` for thread management

## How the Program Works

```text
Read text.txt
     ↓
Split text into words
     ↓
Divide words into parts
     ↓
Assign each part to a thread
     ↓
Each thread counts local word frequencies
     ↓
Main thread collects all results
     ↓
Merge duplicate words
     ↓
Sort by frequency
     ↓
Print top 10 words
```

## Classes Description

### 1. MultithreadingApproach.java

This is the main class of the project.

It performs the following operations:

* Reads the text file using `Files.readAllBytes()`
* Splits the file content into words
* Creates a fixed thread pool using `ExecutorService`
* Divides the word array into parts
* Sends each part to a thread
* Collects the results using `Future`
* Combines word frequencies from all threads
* Sorts the final results by frequency
* Prints the top 10 most frequent words
* Prints execution time

### 2. MultithreadingApproachThread.java

This class implements:

```java
Callable<TreeMap<String, Integer>>
```

Each thread receives a part of the word array and counts the frequency of the words in that part.

It returns a `TreeMap<String, Integer>` where:

* The key is the word
* The value is the number of occurrences

### 3. WordCount.java

This is a helper class used to store:

* A word
* Its count

It also contains an `increment()` method to increase the count of a word.

### 4. WordFrequencyPair.java

This class stores the final result as a word-frequency pair.

It contains:

* `word`
* `frequency`

It implements `Comparable<WordFrequencyPair>` to allow sorting based on frequency in descending order.

## Input File

The program expects an input file named:

```text
text.txt
```

This file should be placed in the same directory where the program is executed.

Example content:

```text
Java is fast and Java is powerful. Multithreading makes Java faster for large tasks.
```

## Output

The program prints:

* Total number of words
* Time taken by threads
* Top 10 most frequent words
* Total execution time

Example output:

```text
Total words: 120000
finished threads, in: 2
the 8950
and 7420
to 6901
of 6500
a 6100
in 5990
is 4210
java 3900
for 3500
data 3120
Total execution time: 2
Full total execution time in nano: 2456789000
```

## How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/Optimized-Word-Frequency-Analyzer-Using-Java-main.git
```

### 2. Open the Project Folder

```bash
cd Optimized-Word-Frequency-Analyzer-Using-Java-main
```

### 3. Prepare the Input File

Create or add a text file named:

```text
text.txt
```

Place it inside the project folder or in the working directory used when running the program.

### 4. Package Note

The Java files use the package name:

```java
package temp;
```

So the recommended structure is:

```text
Optimized-Word-Frequency-Analyzer-Using-Java-main/
├── MultithreadingApproach.java
├── MultithreadingApproachThread.java
├── WordCount.java
└── WordFrequencyPair.java
```

If the files are not inside a `temp` folder, either move them into a folder named `temp` or remove the `package temp;` line from all Java files.

### 5. Compile the Program

From the folder that contains the `temp` directory, run:

```bash
javac temp/*.java
```

### 6. Run the Program

```bash
java temp.MultithreadingApproach
```

## Running in an IDE

You can also run the project using:

* IntelliJ IDEA
* Eclipse
* NetBeans
* VS Code

Steps:

1. Create a new Java project
2. Create a package named `temp`
3. Add all `.java` files inside the `temp` package
4. Add `text.txt` to the project working directory
5. Run `MultithreadingApproach.java`

## Changing the Number of Threads

Inside `MultithreadingApproach.java`, you can change the number of threads using this line:

```java
int numberOfThreads = 1;
```

For example:

```java
int numberOfThreads = 4;
```

You can test different values such as:

```text
1, 2, 4, 6, 8
```

Using more threads may improve performance for large files, but too many threads can also increase overhead.

## Technologies Used

* Java
* Multithreading
* ExecutorService
* Callable
* Future
* TreeMap
* ArrayList
* File handling
* Sorting and comparators

## Learning Outcomes

This project demonstrates:

* How to read files in Java
* How to split a large task into smaller parts
* How to use multithreading for performance optimization
* How to use `ExecutorService` and `Callable`
* How to collect results from multiple threads using `Future`
* How to merge partial results
* How to sort objects based on frequency
* How to measure execution time

## Notes

* The input file must be named `text.txt`.
* The program currently splits words using spaces.
* Punctuation may be treated as part of the word unless additional cleaning is added.
* The number of threads can be modified manually in the source code.
* For best results, use a large text file to observe the effect of multithreading.

## Author

Tasneem Shelleh
