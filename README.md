# JAVA-CheetCode
---
### 1.  int[] to freq Map
    int[] numbers = {1, 2, 2, 3, 3, 3, 4, 4, 4, 4};
    Map<Integer, Long> frequencyMap = Arrays.stream(numbers).boxed()
                                            .collect(Collectors.groupingBy(n -> n, Collectors.counting()));
    //Arrays.stream(numbers).boxed(): Converts the int[] array to a Stream<Integer>
    // Collectors.counting() return a Long so map is Map<Integer, Long>
    // for Map<Integer, Integer>
    Map<Integer, Integer> frequencyMap = Arrays.stream(numbers).boxed().collect(Collectors.groupingBy(n -> n,
                                                Collectors.collectingAndThen(Collectors.counting(), Long::intValue)));

---
### 2.  String to freq Map
    Map<Character, Long> frequencyMap = input.chars().mapToObj(c -> (char) c)
                                                 .collect(Collectors.groupingBy(c -> c, Collectors.counting()));
    // for Map<Character, Integer>
     Map<Character, Integer> frequencyMap = input.chars().mapToObj(c -> (char) c).collect(Collectors.toMap(
                                                        c -> c,
                                                        c -> 1,
                                                        (existingValue, newValue) -> existingValue + newValue));
---
### 3.  Sort a String
     String sortedString = input.chars()
                                .mapToObj(c -> (char) c)  // Convert int to char
                                .sorted()                 // Sort the characters
                                .map(String::valueOf)      // Convert each character to a string
                                .collect(Collectors.joining());
    
                                                

    
    
