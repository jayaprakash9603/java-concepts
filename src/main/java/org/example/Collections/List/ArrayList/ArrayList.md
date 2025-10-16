# Java ArrayList - Complete Guide

## Overview
ArrayList is a part of Java's Collection Framework and is present in `java.util` package. It implements the List interface and provides a dynamic array for storing elements. ArrayList allows duplicate elements, maintains insertion order, and supports random access via indexing.

## Key Features
- **Allows Duplicates:** You can store duplicate elements in an ArrayList.
- **Indexing Supported:** Elements can be accessed using zero-based indices.
- **Dynamic Size:** ArrayList grows automatically as elements are added.
- **Maintains Insertion Order:** Elements are stored in the order they are inserted.
- **Modification Supported:** You can add, remove, or update elements at any position.
- **Null Elements Allowed:** ArrayList can store null values.
- **Not Synchronized:** Not thread-safe by default; use `Collections.synchronizedList()` for thread safety.
- **Random Access:** Provides fast access to elements using indices (O(1) time complexity).
- **Implements Serializable, Cloneable, and RandomAccess interfaces.**

## Important Interview Points
- ArrayList is backed by a dynamic array, so resizing may involve copying elements to a new array.
- The default initial capacity is 10.
- ArrayList is slower than LinkedList for insertions/deletions in the middle but faster for random access.
- ArrayList is preferred when frequent access and iteration are required.
- Use `List` as the reference type for flexibility (e.g., `List<String> list = new ArrayList<>();`).
- ArrayList is not suitable for primitive types; use wrapper classes (e.g., Integer, Double).
- ArrayList can be converted to an array using `toArray()` method.
- Fail-fast behavior: Throws `ConcurrentModificationException` if modified while iterating (except via iterator).

## Commonly Used Methods
| Method | Description | Throws Exception |
|--------|-------------|-----------------|
| `add(E e)` | Adds element to end | - |
| `add(int index, E element)` | Inserts element at index | `IndexOutOfBoundsException` |
| `get(int index)` | Returns element at index | `IndexOutOfBoundsException` |
| `set(int index, E element)` | Replaces element at index | `IndexOutOfBoundsException` |
| `remove(int index)` | Removes element at index | `IndexOutOfBoundsException` |
| `remove(Object o)` | Removes first occurrence of object | - |
| `clear()` | Removes all elements | - |
| `size()` | Returns number of elements | - |
| `isEmpty()` | Checks if list is empty | - |
| `contains(Object o)` | Checks if element exists | - |
| `indexOf(Object o)` | Returns index of first occurrence | - |
| `lastIndexOf(Object o)` | Returns index of last occurrence | - |
| `toArray()` | Converts list to array | - |
| `iterator()` | Returns iterator | - |
| `listIterator()` | Returns list iterator | - |
| `subList(int fromIndex, int toIndex)` | Returns view of portion of list | `IndexOutOfBoundsException`, `IllegalArgumentException` |
| `ensureCapacity(int minCapacity)` | Increases capacity | - |
| `trimToSize()` | Trims capacity to current size | - |
| `clone()` | Returns shallow copy | - |
| `forEach(Consumer<? super E> action)` | Performs action for each element | - |
| `replaceAll(UnaryOperator<E> operator)` | Replaces each element | - |
| `sort(Comparator<? super E> c)` | Sorts list | - |
| `removeIf(Predicate<? super E> filter)` | Removes elements matching filter | - |

## Methods That Throw Exceptions
- `get(int index)`, `set(int index, E element)`, `add(int index, E element)`, `remove(int index)`, `subList(int fromIndex, int toIndex)` throw `IndexOutOfBoundsException` if the index is out of range.
- `subList(int fromIndex, int toIndex)` can also throw `IllegalArgumentException` if `fromIndex > toIndex`.
- Iterators throw `ConcurrentModificationException` if the list is structurally modified after the iterator is created (except through the iterator's own methods).

## Example Usage
```java
import java.util.ArrayList;

public class ArrayListDemo {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Apple");
        list.add("Banana");
        list.add("Apple"); // Duplicates allowed
        System.out.println(list.get(1)); // Output: Banana
        list.set(1, "Orange");
        list.remove("Apple"); // Removes first occurrence
        System.out.println(list); // Output: [Banana, Orange]
    }
}
```

## Related Collections Packages
- `java.util.List` (ArrayList, LinkedList, Vector, Stack)
- `java.util.Set` (HashSet, LinkedHashSet, TreeSet)
- `java.util.Map` (HashMap, LinkedHashMap, TreeMap, Hashtable)
- `java.util.Queue` (PriorityQueue, ArrayDeque, LinkedList)

## Packages Structure for Java Collections Framework
- `org.example.Collections.List.ArrayList`
- `org.example.Collections.List.LinkedList`
- `org.example.Collections.List.Vector`
- `org.example.Collections.List.Stack`
- `org.example.Collections.Set.HashSet`
- `org.example.Collections.Set.LinkedHashSet`
- `org.example.Collections.Set.TreeSet`
- `org.example.Collections.Map.HashMap`
- `org.example.Collections.Map.LinkedHashMap`
- `org.example.Collections.Map.TreeMap`
- `org.example.Collections.Map.Hashtable`
- `org.example.Collections.Queue.PriorityQueue`
- `org.example.Collections.Queue.ArrayDeque`
- `org.example.Collections.Queue.LinkedList`

> **Tip:** For interviews, focus on time complexity, use cases, and differences between ArrayList and other collections like LinkedList, HashSet, and HashMap.

