# Java Collections Learning Repository

## 1. Overview
This repository is a curated playground for learning and revising core Java concepts with a primary focus on the Java Collections Framework. It contains structured examples, explanations, and notes that are helpful for:
- Strengthening fundamentals
- Interview preparation
- Quick revision of APIs, behavior, and edge cases

> Target Audience: Java beginners to intermediate developers preparing for interviews or deepening their understanding of Collections.

## 2. Tech Stack
- Language: Java (JDK 8+ recommended; examples are compatible with JDK 17)
- Build Tool: Maven (`pom.xml` present)
- Structure: Standard Maven directory layout

## 3. Project Structure (Key Paths)
```
pom.xml
src/
  main/
    java/
      org/example/Collections/
        List/
          ArrayList/              # ArrayList notes & examples
          Linkedlist/             # (Placeholder for LinkedList content)
          Vector/                 # Vector basics; legacy synchronized list
            Stack/                # Stack (LIFO) extends Vector
          StackExample.java       # Stack usage example (if present)
        Set/
          HashSet/                # (Placeholder) HashSet internals
          LinkedHashSet/          # (Placeholder) Insertion-order Set
          HashSetExample.java
          LinkedHashSetExample.java
          SetExample.java
        Map/
          HashMap/                # (Placeholder)
          LinkedHashMap/          # (Placeholder)
          SortedMap/              # (Placeholder for SortedMap concepts)
            TreeMap/              # (Placeholder) TreeMap internals
          MapExample.java
          LinkedHashMapExample.java
          TreeMapExample.java
        Queue/
          QueueExample.java
          Deque/
            ArrayDeque/           # (Placeholder) ArrayDeque notes
          PriorityQueue/          # (Placeholder) PriorityQueue notes
      org/example/core/           # (Future space for non-collection core concepts)
  test/java/                      # (Add unit tests progressively)
```

## 4. Collections Framework – Concept Map
Interfaces → Implementations → Specializations:
- Collection
  - List → ArrayList, LinkedList, Vector (→ Stack)
  - Set → HashSet, LinkedHashSet, SortedSet → TreeSet
  - Queue → PriorityQueue, Deque → ArrayDeque / LinkedList
- Map (separate hierarchy) → HashMap, LinkedHashMap, SortedMap → TreeMap, Hashtable (legacy)

## 5. Core Characteristics Cheat Sheet
| Type | Ordering | Duplicates | Nulls | Performance Focus | Backing Structure |
|------|----------|-----------|-------|-------------------|------------------|
| ArrayList | Insertion order | Yes | Yes | Fast random access | Dynamic array |
| LinkedList | Insertion order | Yes | Yes | Fast insert/delete mid-list | Doubly linked nodes |
| Vector | Insertion order | Yes | Yes | Legacy synchronized | Dynamic array |
| Stack | LIFO | Yes | Yes | Stack operations | Vector |
| HashSet | None (hash order) | No | One null | Fast contains/add | Hash table (hash buckets) |
| LinkedHashSet | Insertion order | No | One null | Predictable iteration | Hash table + linked list |
| TreeSet | Sorted | No | No (unless custom comparator) | Ordered operations | Red-Black tree |
| HashMap | None (hash order) | Keys: 1 null, Values: many nulls | Fast lookup | Hash table + tree bins (JDK 8+) |
| LinkedHashMap | Insertion / access order (configurable) | Keys unique | Yes | Iteration + caching (LRU via access-order) | Hash + doubly linked list |
| TreeMap | Sorted by key | Keys unique | No null key | Range queries, sorted ops | Red-Black tree |
| Hashtable | None | Keys unique | No nulls | Legacy synchronized | Hash table |
| PriorityQueue | Heap order | Yes | No nulls | Priority retrieval | Binary heap |
| ArrayDeque | Insertion order | Yes | No nulls | Fast deque ops | Resizable circular array |

## 6. Big Interview Talking Points
- ArrayList vs LinkedList: Access O(1) vs O(n); middle insertion O(n) vs O(1) (with iterator); memory locality.
- HashSet vs TreeSet vs LinkedHashSet: Hash vs sorted vs order-preserving; TreeSet supports range queries (subSet/headSet/tailSet). 
- HashMap vs LinkedHashMap vs TreeMap: Unordered, insertion/access order, and sorted key ordering respectively.
- Load Factor & Capacity (HashMap): Default 0.75; resizing doubles capacity; impacts performance.
- Fail-Fast Iterators: Structural modification outside iterator leads to ConcurrentModificationException.
- Immutability Wrappers: `Collections.unmodifiableList(list)` for read-only views.
- Thread Safety: Prefer concurrent collections (e.g., `ConcurrentHashMap`) over `Collections.synchronizedMap` for high contention.
- TreeMap / TreeSet Ordering: Natural ordering or custom Comparator (provided at construction only).
- HashMap Collision Strategy (JDK 8+): Bucket transforms from linked list to balanced tree after threshold (typically 8) when capacity large enough.
- Equals & HashCode Contract: Required for correct behavior in hash-based collections.

## 7. Common Exceptions in Collections
| Scenario | Exception |
|----------|-----------|
| Invalid index (List) | IndexOutOfBoundsException |
| Using null in sorted structures (without support) | NullPointerException |
| Concurrent structural modification | ConcurrentModificationException |
| Adding null to PriorityQueue / ArrayDeque | NullPointerException |
| Duplicate key insertion in Map putIfAbsent semantics | (No exception; previous value overwritten unless using computeIfAbsent logic) |
| Negative initial capacity | IllegalArgumentException |

## 8. Frequently Used Methods (Selection)
- List: add, addAll, get, set, remove(int/Object), indexOf, subList, listIterator
- Set: add, contains, remove, iterator
- Map: put, putIfAbsent, get, getOrDefault, containsKey, keySet, entrySet, values, compute, merge
- Queue/Deque: offer, poll, peek, push, pop, addFirst/addLast, removeFirst/removeLast
- Collections (utility): sort, reverse, shuffle, binarySearch, min, max, frequency, unmodifiableXXX, synchronizedXXX

## 9. Sample Code Snippets
### 9.1 Safe Iteration with Removal
```java
List<String> list = new ArrayList<>(List.of("A","B","C"));
Iterator<String> it = list.iterator();
while (it.hasNext()) {
    if (it.next().equals("B")) {
        it.remove(); // safe removal
    }
}
```
### 9.2 Using Map.computeIfAbsent
```java
Map<String, List<Integer>> index = new HashMap<>();
index.computeIfAbsent("k", k -> new ArrayList<>()).add(42);
```
### 9.3 PriorityQueue Custom Ordering
```java
PriorityQueue<String> pq = new PriorityQueue<>(Comparator.comparingInt(String::length));
pq.addAll(List.of("banana","fig","apple"));
while (!pq.isEmpty()) {
    System.out.println(pq.poll()); // fig, apple, banana
}
```
### 9.4 LinkedHashMap as LRU Cache (Manual)
```java
int maxEntries = 100;
Map<Integer,String> lru = new LinkedHashMap<>(16, 0.75f, true) {
    protected boolean removeEldestEntry(Map.Entry<Integer,String> eldest) {
        return size() > maxEntries;
    }
};
```
### 9.5 TreeSet with Custom Comparator
```java
Set<String> set = new TreeSet<>(Comparator.comparingInt(String::length).thenComparing(Comparator.naturalOrder()));
set.addAll(List.of("bbb","a","cc","dddd"));
// Iteration yields: a, cc, bbb, dddd
```

## 10. Performance Complexity Summary (Typical)
| Operation | ArrayList | LinkedList | HashSet / HashMap | TreeSet / TreeMap | PriorityQueue | ArrayDeque |
|-----------|----------|------------|-------------------|------------------|---------------|-----------|
| Add (amortized end) | O(1) | O(1) | O(1) | O(log n) | O(log n) | O(1) |
| Add (middle) | O(n) | O(1) (with iterator) | - | - | - | O(1) ends |
| Remove by value | O(n) | O(n) | O(1) | O(log n) | O(n) | O(1) ends |
| Remove first/last | O(n)/O(1)* | O(1) | - | - | - | O(1) |
| Get by index | O(1) | O(n) | - | - | - | - |
| Contains | O(n) | O(n) | O(1) | O(log n) | O(n) | O(n) |
| Peek (head) | O(1) | O(1) | - | - | O(1) | O(1) |
| Poll (head) | O(n) shift | O(1) | - | - | O(log n) | O(1) |
*ArrayList remove first element requires shift.

## 11. Suggested Learning Path
1. Understand interfaces (List, Set, Map, Queue, Deque)
2. Explore concrete classes & use-cases
3. Practice iteration patterns & safe modification
4. Internal data structures (array vs linked nodes vs hash table vs tree vs heap)
5. Performance measurement (write micro-benchmarks if curious)
6. Concurrency considerations & immutable views
7. Advanced Map operations: compute*, merge, replaceAll

## 12. Best Practices
- Program to interfaces (`List<String> l = new ArrayList<>();`)
- Prefer immutability for shared data (`List.copyOf`, `Collections.unmodifiableList`)
- Avoid premature optimization – choose based on access vs mutation patterns
- Override `equals` & `hashCode` consistently for custom key types
- Use `EnumSet` / `EnumMap` for enums (future addition to repo)
- Favor `Deque` (ArrayDeque) over `Stack`
- Use `computeIfAbsent` to simplify nested-collection population

## 13. Planned Enhancements (TODO)
- Add LinkedList detailed notes & examples
- Add TreeMap internal mechanics (rotations, ordering rules)
- Add concurrency examples (`ConcurrentHashMap`, `CopyOnWriteArrayList`)
- Add Stream API integration examples with collections
- Add unit tests (JUnit) for demonstration code
- Add memory layout notes and sizing strategies

## 14. How to Build & Run
From project root (where `pom.xml` lives):
```bash
mvn clean compile
mvn exec:java -Dexec.mainClass="org.example.Collections.Map.MapExample"   # Adjust main class as needed
```
(If `exec-maven-plugin` not configured yet, create simple runnable main classes and run via IDE.)

## 15. Contributing / Extending Locally
- Add new topic under appropriate package
- Include a short `README.md` in each subfolder for theory + code
- Keep examples minimal & focused
- Avoid adding external dependencies unless necessary

## 16. Quick Reference: Utility Methods (Collections)
Key static helpers: sort, reverse, shuffle, binarySearch, min, max, frequency, fill, copy, unmodifiableList, synchronizedMap, newSetFromMap, asLifoQueue.

## 17. License / Usage
Educational use. Adapt freely for personal learning. (Add a LICENSE file if you want explicit terms.)

## 18. Feedback
If something is missing or unclear, extend the markdowns or add a new example class. Iterative improvement is encouraged.

---
Happy Learning! Build, run, tweak, and observe behavior—experimentation accelerates mastery.

