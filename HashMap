 Here are all the common ways to iterate through a `Map` in Java:

---

### **1. Iterating through Keys:**
Using `keySet()` to get all keys and iterate through them.

```java
Map<String, Integer> map = new HashMap<>();
map.put("A", 1);
map.put("B", 2);

for (String key : map.keySet()) {
    System.out.println("Key: " + key + ", Value: " + map.get(key));
}
```

---

### **2. Iterating through Values:**
Using `values()` to iterate only through the values.

```java
for (Integer value : map.values()) {
    System.out.println("Value: " + value);
}
```

---

### **3. Iterating through Entries (Key-Value Pairs):**
Using `entrySet()` to get all entries and iterate through them.

#### **Using a `for-each` loop:**
```java
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
}
```

#### **Using an Iterator:**
```java
Iterator<Map.Entry<String, Integer>> iterator = map.entrySet().iterator();
while (iterator.hasNext()) {
    Map.Entry<String, Integer> entry = iterator.next();
    System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue());
}
```

---

### **4. Using Lambda Expressions (Java 8+):**
Using the `forEach` method of the `Map`.

```java
map.forEach((key, value) -> {
    System.out.println("Key: " + key + ", Value: " + value);
});
```

---

### **5. Using Streams (Java 8+):**
#### **Entry Streams:**
```java
map.entrySet().stream()
   .forEach(entry -> System.out.println("Key: " + entry.getKey() + ", Value: " + entry.getValue()));
```

#### **Key Streams:**
```java
map.keySet().stream()
   .forEach(key -> System.out.println("Key: " + key + ", Value: " + map.get(key)));
```

#### **Value Streams:**
```java
map.values().stream()
   .forEach(value -> System.out.println("Value: " + value));
```

---

### **6. Using `Enumeration` (Legacy):**
If the `Map` is backed by a `Hashtable`, you can use `keys()` or `elements()` to enumerate keys or values.

```java
Hashtable<String, Integer> hashtable = new Hashtable<>();
hashtable.put("X", 10);
hashtable.put("Y", 20);

Enumeration<String> keys = hashtable.keys();
while (keys.hasMoreElements()) {
    String key = keys.nextElement();
    System.out.println("Key: " + key + ", Value: " + hashtable.get(key));
}
```

---

### **7. Iterating with `ListIterator` (Uncommon):**
If the keys or values are converted to a `List`, you can use a `ListIterator`.

```java
List<String> keys = new ArrayList<>(map.keySet());
ListIterator<String> listIterator = keys.listIterator();

while (listIterator.hasNext()) {
    String key = listIterator.next();
    System.out.println("Key: " + key + ", Value: " + map.get(key));
}
```

---

These approaches cover a wide variety of scenarios and are applicable depending on your needs and the Java version you're using. 🚀
