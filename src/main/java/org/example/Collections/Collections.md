# Java Collections Framework - Overview

The Java Collections Framework (JCF) is a unified architecture for representing and manipulating collections, enabling efficient data storage, retrieval, and manipulation. It is part of the `java.util` package and provides interfaces, implementations, and algorithms for working with groups of objects.

## High-Level Overview

- **Unified Architecture:** Provides a standard way to handle groups of objects (collections) in Java.
- **Core Interfaces:** Includes List, Set, Map, Queue, and Deque, each defining a different collection type.
- **Implementations:** Offers ready-to-use classes like ArrayList, LinkedList, HashSet, TreeSet, HashMap, LinkedHashMap, PriorityQueue, etc.
- **Algorithms:** Supplies utility methods for sorting, searching, shuffling, and more via the `Collections` class.
- **Type Safety:** Supports generics for compile-time type checking and to avoid ClassCastException.
- **Performance:** Different implementations offer various time complexities for add, remove, search, and access operations.
- **Thread Safety:** Most collections are not synchronized by default; thread-safe versions and concurrent collections are available.
- **Fail-Fast Iterators:** Iterators throw ConcurrentModificationException if the collection is modified during iteration (except via iterator's own methods).
- **Null Handling:** Some collections allow null elements/keys/values (e.g., ArrayList, HashMap), while others do not (e.g., Hashtable, TreeSet for keys).
- **Legacy Classes:** Includes older classes like Vector, Stack, and Hashtable for backward compatibility.
- **Interoperability:** Collections can be easily converted to arrays and vice versa.
- **Extensibility:** You can create custom collections by implementing core interfaces.
- **Best Practices:** Prefer using interfaces as reference types (e.g., List, Set, Map) for flexibility and maintainability.
- **Use Cases:** Choose the right collection based on requirements like ordering, uniqueness, sorting, thread safety, and performance.

> **Tip:** Mastering the Collections Framework is essential for efficient Java programming and is a frequent topic in technical interviews.

## Recommended Java Collections Framework Folder Structure (Corrected)

```
org.example.Collections/
├── List/
│   ├── ArrayList/
│   ├── LinkedList/
│   ├── Vector/
│   │   └── Stack/
├── Set/
│   ├── HashSet/
│   ├── LinkedHashSet/
│   └── SortedSet/
│       └── TreeSet/
├── Map/
│   ├── HashMap/
│   ├── LinkedHashMap/
│   └── Hashtable/
│   └── SortedMap/
│       └── TreeMap/
├── Queue/
│   ├── PriorityQueue/
│   └── Deque/
│       └── ArrayDeque/
```

- **List**: For ordered collections that allow duplicates (ArrayList, LinkedList, Vector). Stack is a legacy class that extends Vector, so it is placed inside Vector.
- **Set**: For collections that do not allow duplicates (HashSet, LinkedHashSet). TreeSet is a sorted set, so it is placed inside SortedSet.
- **Map**: For key-value pairs (HashMap, LinkedHashMap, TreeMap, Hashtable)
- **Queue**: For FIFO/LIFO collections (PriorityQueue, ArrayDeque, LinkedList)

> This structure reflects the inheritance and logical grouping of Java's collection classes more accurately.

## Main Interfaces
- **List**: Ordered collection (sequence) that allows duplicate elements. (e.g., ArrayList, LinkedList, Vector, Stack)
- **Set**: Collection that does not allow duplicate elements. (e.g., HashSet, LinkedHashSet, TreeSet)
- **Map**: Object that maps keys to values; cannot contain duplicate keys. (e.g., HashMap, LinkedHashMap, TreeMap, Hashtable)
- **Queue**: Collection for holding elements prior to processing, typically in FIFO order. (e.g., PriorityQueue, ArrayDeque, LinkedList)

## Key Implementations
- **ArrayList**: Resizable array, fast random access, allows duplicates.
- **LinkedList**: Doubly-linked list, efficient insertions/deletions.
- **Vector**: Synchronized resizable array.
- **Stack**: LIFO stack, extends Vector.
- **HashSet**: Hash table-based set, no duplicates, unordered.
- **LinkedHashSet**: Maintains insertion order.
- **TreeSet**: Sorted set, based on Red-Black tree.
- **HashMap**: Hash table-based map, allows null keys/values.
- **LinkedHashMap**: Maintains insertion order.
- **TreeMap**: Sorted map, based on Red-Black tree.
- **Hashtable**: Synchronized map, legacy class.
- **PriorityQueue**: Elements ordered by natural order or comparator.
- **ArrayDeque**: Resizable array for double-ended queue.

## Important Points for Interviews
- Collections Framework provides algorithms (sorting, searching, shuffling, etc.) via `Collections` utility class.
- All major collections except legacy classes are not synchronized by default.
- Prefer interfaces (`List`, `Set`, `Map`, `Queue`) as reference types for flexibility.
- Understand time complexity for basic operations (add, remove, get, contains, etc.).
- Know the difference between fail-fast and fail-safe iterators.
- Some collections allow nulls (e.g., ArrayList, HashMap), others do not (e.g., Hashtable, TreeSet for keys if comparator does not support null).
- Use wrapper classes for primitives (e.g., Integer, Double) in collections.
- Collections can be made thread-safe using `Collections.synchronizedXXX` or concurrent collections (e.g., `ConcurrentHashMap`).

## Commonly Used Methods in the Java Collections Framework

Below are the most important methods available at the Collections Framework level (mainly from the `Collections` utility class and core interfaces). Each method includes its use case, signature, and a usage example.

### 1. add
- **Use Case:** Adds an element to a collection.
- **Signature:** `boolean add(E e)`
- **Example:**
  ```java
  List<String> list = new ArrayList<>();
  list.add("Apple");
  ```

### 2. addAll
- **Use Case:** Adds all elements from another collection.
- **Signature:** `boolean addAll(Collection<? extends E> c)`
- **Example:**
  ```java
  List<String> list1 = new ArrayList<>();
  List<String> list2 = Arrays.asList("A", "B");
  list1.addAll(list2);
  ```

### 3. remove
- **Use Case:** Removes an element from a collection.
- **Signature:** `boolean remove(Object o)`
- **Example:**
  ```java
  list.remove("Apple");
  ```

### 4. removeAll
- **Use Case:** Removes all elements in the specified collection from this collection.
- **Signature:** `boolean removeAll(Collection<?> c)`
- **Example:**
  ```java
  list.removeAll(Arrays.asList("A", "B"));
  ```

### 5. retainAll
- **Use Case:** Retains only the elements in this collection that are contained in the specified collection.
- **Signature:** `boolean retainAll(Collection<?> c)`
- **Example:**
  ```java
  list.retainAll(Arrays.asList("A"));
  ```

### 6. clear
- **Use Case:** Removes all elements from the collection.
- **Signature:** `void clear()`
- **Example:**
  ```java
  list.clear();
  ```

### 7. contains
- **Use Case:** Checks if the collection contains a specific element.
- **Signature:** `boolean contains(Object o)`
- **Example:**
  ```java
  list.contains("Apple");
  ```

### 8. containsAll
- **Use Case:** Checks if the collection contains all elements of another collection.
- **Signature:** `boolean containsAll(Collection<?> c)`
- **Example:**
  ```java
  list.containsAll(Arrays.asList("A", "B"));
  ```

### 9. size
- **Use Case:** Returns the number of elements in the collection.
- **Signature:** `int size()`
- **Example:**
  ```java
  int count = list.size();
  ```

### 10. isEmpty
- **Use Case:** Checks if the collection is empty.
- **Signature:** `boolean isEmpty()`
- **Example:**
  ```java
  boolean empty = list.isEmpty();
  ```

### 11. iterator
- **Use Case:** Returns an iterator over the elements in the collection.
- **Signature:** `Iterator<E> iterator()`
- **Example:**
  ```java
  Iterator<String> it = list.iterator();
  while (it.hasNext()) {
      System.out.println(it.next());
  }
  ```

### 12. toArray
- **Use Case:** Converts the collection to an array.
- **Signature:** `Object[] toArray()`
- **Example:**
  ```java
  Object[] arr = list.toArray();
  ```

### 13. sort (Collections utility)
- **Use Case:** Sorts the specified list into ascending order.
- **Signature:** `static <T extends Comparable<? super T>> void sort(List<T> list)`
- **Example:**
  ```java
  Collections.sort(list);
  ```

### 14. reverse (Collections utility)
- **Use Case:** Reverses the order of the elements in the specified list.
- **Signature:** `static void reverse(List<?> list)`
- **Example:**
  ```java
  Collections.reverse(list);
  ```

### 15. shuffle (Collections utility)
- **Use Case:** Randomly permutes the elements in the specified list.
- **Signature:** `static void shuffle(List<?> list)`
- **Example:**
  ```java
  Collections.shuffle(list);
  ```

### 16. binarySearch (Collections utility)
- **Use Case:** Searches for an element in a sorted list.
- **Signature:** `static <T> int binarySearch(List<? extends Comparable<? super T>> list, T key)`
- **Example:**
  ```java
  int index = Collections.binarySearch(list, "Apple");
  ```

### 17. min/max (Collections utility)
- **Use Case:** Returns the minimum/maximum element of the given collection.
- **Signature:**
  - `static <T extends Object & Comparable<? super T>> T min(Collection<? extends T> coll)`
  - `static <T extends Object & Comparable<? super T>> T max(Collection<? extends T> coll)`
- **Example:**
  ```java
  String min = Collections.min(list);
  String max = Collections.max(list);
  ```

### 18. unmodifiableCollection (Collections utility)
- **Use Case:** Returns an unmodifiable view of the specified collection.
- **Signature:** `static <T> Collection<T> unmodifiableCollection(Collection<? extends T> c)`
- **Example:**
  ```java
  Collection<String> unmodifiable = Collections.unmodifiableCollection(list);
  ```

### 19. synchronizedCollection (Collections utility)
- **Use Case:** Returns a synchronized (thread-safe) collection backed by the specified collection.
- **Signature:** `static <T> Collection<T> synchronizedCollection(Collection<T> c)`
- **Example:**
  ```java
  Collection<String> sync = Collections.synchronizedCollection(list);
  ```

### 20. copy (Collections utility)
- **Use Case:** Copies all elements from one list to another.
- **Signature:** `static <T> void copy(List<? super T> dest, List<? extends T> src)`
- **Example:**
  ```java
  List<String> dest = new ArrayList<>(Arrays.asList("", "", ""));
  List<String> src = Arrays.asList("A", "B", "C");
  Collections.copy(dest, src);
  ```

## Categorized Methods in the Collections Utility Class

Below are the methods from `java.util.Collections` grouped by their primary purpose:

### 1. Adding Elements
- `addAll(Collection<? super T> c, T... elements)`: Adds all specified elements to the collection.

### 2. Removing Elements
- `removeAll(Collection<?> c)`: Removes all elements in the specified collection from this collection (from Collection interface).
- `clear()`: Removes all elements from the collection (from Collection interface).

### 3. Searching/Querying
- `binarySearch(List<? extends Comparable<? super T>> list, T key)`: Searches for key in a sorted list using binary search.
- `frequency(Collection<?> c, Object o)`: Counts the number of times the object occurs in the collection.
- `disjoint(Collection<?> c1, Collection<?> c2)`: Checks if two collections have no elements in common.
- `indexOfSubList(List<?> source, List<?> target)`: Returns the starting position of the first occurrence of target in source.
- `lastIndexOfSubList(List<?> source, List<?> target)`: Returns the starting position of the last occurrence of target in source.
- `contains(Object o)`: Checks if the collection contains a specific element (from Collection interface).
- `containsAll(Collection<?> c)`: Checks if the collection contains all elements of another collection (from Collection interface).

### 4. Modifying/Updating
- `copy(List<? super T> dest, List<? extends T> src)`: Copies all elements from src to dest.
- `fill(List<? super T> list, T obj)`: Replaces all elements with the specified value.
- `replaceAll(List<T> list, T oldVal, T newVal)`: Replaces all occurrences of oldVal with newVal.
- `swap(List<?> list, int i, int j)`: Swaps the elements at the specified positions.
- `rotate(List<?> list, int distance)`: Rotates the elements by the specified distance.

### 5. Sorting/Ordering
- `sort(List<T> list)`: Sorts the list into ascending order.
- `reverse(List<?> list)`: Reverses the order of elements.
- `shuffle(List<?> list)`: Randomly permutes the elements.
- `reverseOrder()`: Returns a comparator that imposes the reverse of the natural ordering.

### 6. Min/Max
- `min(Collection<? extends T> coll)`: Returns the minimum element.
- `max(Collection<? extends T> coll)`: Returns the maximum element.

### 7. Creating Special Collections
- `emptyList()`, `emptySet()`, `emptyMap()`: Returns immutable empty collections.
- `singleton(T o)`, `singletonList(T o)`, `singletonMap(K key, V value)`: Returns immutable collections with a single element.
- `nCopies(int n, T o)`: Returns an immutable list with n copies of the object.
- `newSetFromMap(Map<E,Boolean> map)`: Returns a set backed by the specified map.
- `asLifoQueue(Deque<T> deque)`: Returns a view of the deque as a LIFO queue.

### 8. Wrapping Collections
- `unmodifiableCollection(Collection<? extends T> c)`, `unmodifiableList(List<? extends T> list)`, `unmodifiableSet(Set<? extends T> s)`, `unmodifiableMap(Map<? extends K, ? extends V> m)`: Returns unmodifiable views.
- `synchronizedCollection(Collection<T> c)`, `synchronizedList(List<T> list)`, `synchronizedSet(Set<T> s)`, `synchronizedMap(Map<K,V> m)`: Returns synchronized (thread-safe) views.
- `checkedCollection(Collection<E> c, Class<E> type)`, `checkedList(List<E> list, Class<E> type)`, `checkedSet(Set<E> s, Class<E> type)`, `checkedMap(Map<K,V> m, Class<K> keyType, Class<V> valueType)`: Returns dynamically typesafe views.

### 9. Conversion Utilities
- `enumeration(Collection<T> c)`: Returns an enumeration over the collection.
- `list(Enumeration<T> e)`: Returns an array list containing the elements returned by the enumeration.

> This categorization helps you quickly identify which Collections methods to use for adding, removing, searching, sorting, wrapping, and converting collections.

## Example Usage
```java
import java.util.*;

public class CollectionsDemo {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        Set<Integer> set = new HashSet<>();
        Map<String, Integer> map = new HashMap<>();
        Queue<Double> queue = new PriorityQueue<>();
        // ...
    }
}
```

> **Tip:** For interviews, focus on use cases, time complexity, and differences between similar collections (e.g., ArrayList vs LinkedList, HashSet vs TreeSet, HashMap vs LinkedHashMap vs TreeMap).
