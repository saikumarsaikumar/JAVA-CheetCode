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
                                                

    
    
