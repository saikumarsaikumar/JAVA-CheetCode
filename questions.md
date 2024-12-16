## 1. DSA

### Frequency Map of Integers
```java
int[] numbers = {1, 2, 2, 3, 3, 3, 4, 4, 4, 4};
Map<Integer, Long> frequencyMap = Arrays.stream(numbers).boxed()
    .collect(Collectors.groupingBy(n -> n, Collectors.counting()));
// Arrays.stream(numbers).boxed(): Converts the int[] array to a Stream<Integer>
// Collectors.counting() returns a Long so map is Map<Integer, Long>

// For Map<Integer, Integer>
Map<Integer, Integer> frequencyMap = Arrays.stream(numbers).boxed()
    .collect(Collectors.groupingBy(n -> n, Collectors.collectingAndThen(Collectors.counting(), Long::intValue)));
```

### Valid Sudoku
- [Problem Link](https://leetcode.com/problems/valid-sudoku/)

### Group Anagrams
#### Problem
- [Problem Link](https://leetcode.com/problems/group-anagrams/description/) [Medium]
- Given an array of strings, group the anagrams together. Return the result in any order.

#### Example
```java
Input: ["eat", "tea", "tan", "ate", "nat", "bat"]
Output: [["bat"], ["nat", "tan"], ["ate", "eat", "tea"]]

Input: ["no", "on", "is"]
Output: [["is"], ["no", "on"]]
```
#### Complexity
- **Time Complexity:** O(n \* m \* log(m))
  - `n` is the number of strings.
  - `m` is the average length of the strings.

---

### Longest Substring Without Repeating Characters
#### Problem
```java
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

---

### Convert Array to List of 2D List
#### Problem
You are given an integer array `nums`. Create a 2D array from `nums` satisfying:
1. The 2D array contains only the elements of `nums`.
2. Each row contains distinct integers.
3. Minimize the number of rows.

#### Example
```java
Input: nums = [1,3,4,1,2,3,1]
Output: [[1,3,4,2], [1,3], [1]]
Explanation: Rows contain distinct integers.
```

#### Edge Cases
1. **Single Element:** `nums = [1]` → `[[1]]`
2. **All Identical:** `nums = [2, 2, 2, 2]` → `[[2], [2], [2], [2]]`
3. **Already Distinct:** `nums = [5, 6, 7, 8]` → `[[5, 6, 7, 8]]`
4. **Empty Array:** `nums = []` → `[]`

---

## 2. System Design

### Design Patterns (DPs) Used
1. **Strategy Pattern**
   - **When to Use:** When multiple algorithms can be swapped dynamically.
   - **When Not to Use:** If the algorithms are unlikely to change or are very simple.

2. **Observer Pattern**
#### Weather Monitoring System
**Objective:** Monitor weather conditions and notify users of changes in real-time.

#### Requirements
1. **Weather Station**:
   - Register, deregister, and notify multiple clients.
   - Maintain current temperature, humidity, and pressure values.
   - Publish weather reports at any time.

2. **Clients**:
   - Receive updates about weather data.
   - Examples: RADIO, INTERNET, TELEVISION, SMS.

3. **Example Displays**:
   - CurrentConditionsDisplay: Shows temperature and humidity.
   - StatisticsDisplay: Shows average temperature and humidity.
   - ForecastDisplay: Provides weather forecasts.

4. **Thread Safety**
   - Ensure proper handling of notifications and updates.

---

## 3. Java Basics

### String Equality
#### Code
```java
String str1 = "Hello";
String str2 = "Hello";
System.out.println(str1 == str2); // true

String str3 = new String("Hello");
String str4 = new String("Hello");
System.out.println(str3 == str4); // false
```
#### Explanation
- `str1 == str2`: True because they reference the same object in the string pool.
- `str3 == str4`: False because they are different objects in heap memory.

---

### Functional Interface and Lambda
#### Code
```java
interface MyFunction {
    void execute();
}

class HelloWorld {
    public static void main(String[] args) {
        MyFunction myFunction = () -> System.out.println("Lambda executed!");
        myFunction.execute();
    }
}
```

---

### Interface Conflict Resolution
#### Code
```java
interface A {
    default void display() {
        System.out.println("Display from Interface A");
    }
}

interface B {
    default void display() {
        System.out.println("Display from Interface B");
    }
}

interface C extends A, B {
    @Override
    default void display() {
        System.out.println("Display from Interface C");
    }
}

public class TestClass implements C {
    public static void main(String[] args) {
        C obj = new TestClass();
        obj.display();

        A objA = new TestClass();
        objA.display();

        B objB = new TestClass();
        objB.display();
    }
}
```
#### Output
```text
Display from Interface C
Display from Interface C
Display from Interface C
```

---

### Streams and Lazy Evaluation
#### Code
```java
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class TestStreams {
    public static void main(String[] args) {
        Stream<Integer> numberStream = Stream.of(1, 2, 3, 4, 5, 6);

        List<Integer> result = numberStream
            .filter(num -> {
                System.out.println("Filtering: " + num);
                return num % 2 == 0;
            })
            .map(num -> {
                System.out.println("Mapping: " + num);
                return num * 2;
            })
            .limit(2)
            .collect(Collectors.toList());

        System.out.println("Result: " + result);

        try {
            numberStream.forEach(System.out::println);
        } catch (Exception e) {
            System.out.println("Exception: " + e);
        }
    }
}
```
#### Output
```text
Filtering: 1
Filtering: 2
Mapping: 2
Filtering: 3
Filtering: 4
Mapping: 4
Result: [4, 8]
Exception: java.lang.IllegalStateException: stream has already been operated upon or closed
```

---

## 4. Spring Boot

### Concepts
#### POJO vs Java Bean vs Spring Bean

1. **POJO (Plain Old Java Object):**
   - Simple Java object without special restrictions.
   - No need for inheritance or specific interfaces.

2. **Java Bean:**
   - A POJO with conventions: no-arg constructor, private fields, getters/setters.

3. **Spring Bean:**
   - Managed by Spring IoC container.
   - Defined using annotations like `@Component` or `@Bean`.

#### ApplicationContext vs BeanFactory

---

## 5. EECF

### Concepts
1. **ACID Properties**
2. **Distributed Transactions**
   - **SAGA Pattern**
   - **2-Phase Commit** (e.g., Apache Zookeeper)

### Performance Optimization in Java
- Identify bottlenecks.
- Use profilers.
- Optimize database queries.
- Reduce synchronization.
- Use efficient data structures.

