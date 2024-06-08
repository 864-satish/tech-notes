# Java Basics
Java is an object-oriented, class-based, concurrent, secured and general-purpose computer-programming language.

### Data Types in Java
1. Primitive [8]: Predefined by the language and are not objects.
```java
byte: 8-bit signed integer. Range: -128 to 127.
short: 16-bit signed integer. Range: -32,768 to 32,767.
int: 32-bit signed integer. Range: -2<sup>31</sup> to 2<sup>31</sup>-1.
long: 64-bit signed integer. Range: -2<sup>63</sup> to 2<sup>63</sup>-1.
float: 32-bit floating-point number.
double: 64-bit floating-point number.
boolean: Represents true or false.
char: 16-bit Unicode character.
```
2. Reference : These data types are used to refer to objects. They are not actual data stored in a variable but rather references to objects stored in memory. Reference data types include classes, interfaces, arrays, enumerations, and annotations.

```java
public class DataTypesExample {
    public static void main(String[] args) {
        // Primitive data types
        byte myByte = 10;
        short myShort = 500;
        int myInt = 10000;
        long myLong = 1000000000L; //'L' suffix for long literals
        float myFloat = 3.14f; //'f' suffix for float literals
        double myDouble = 3.14159;
        boolean myBoolean = true;
        char myChar = 'A';

        // Reference data type (String)
        String myString = "Hello, Java!";
    }
}
```

### Java Collections and Classes Initialization 
Common Java collections, classes and List of methods available in them.

- Integer 
```java
Integer integerExample = Integer.valueOf(10);
```
    intValue()
    byteValue()
    shortValue()
    longValue()
    floatValue()
    doubleValue()
    compareTo(Integer anotherInteger)
    equals(Object obj)
    hashCode()
    parseInt(String s)
    parseInt(String s, int radix)
    toString()
    toString(int i)
    valueOf(String s)
    valueOf(int i)
- String 
```java
String stringExample = "Hello, World!";
```

    charAt(int index)
    compareTo(String anotherString)
    compareToIgnoreCase(String str)
    concat(String str)
    contains(CharSequence s)
    endsWith(String suffix)
    equals(Object anObject)
    equalsIgnoreCase(String anotherString)
    format(String format, Object... args)
    getBytes()
    getBytes(String charsetName)
    indexOf(int ch)
    indexOf(String str)
    isEmpty()
    length()
    replace(char oldChar, char newChar)
    replace(CharSequence target, CharSequence replacement)
    split(String regex)
    split(String regex, int limit)
    startsWith(String prefix)
    substring(int beginIndex)
    substring(int beginIndex, int endIndex)
    toLowerCase()
    toUpperCase()
    trim()
    valueOf(boolean b)
    valueOf(char c)
    valueOf(int i)
    valueOf(long l)
    valueOf(float f)
    valueOf(double d)
    valueOf(Object obj)
- Arrays 
```java
int[] arrayExample = {1, 2, 3, 4, 5};
```
    asList(T... a)
    binarySearch(T[] a, T key)
    copyOf(T[] original, int newLength)
    copyOfRange(T[] original, int from, int to)
    equals(Object[] a, Object[] a2)
    fill(T[] a, T val)
    fill(T[] a, int fromIndex, int toIndex, T val)
    sort(T[] a)
    sort(T[] a, Comparator<? super T> c)
    toString(Object[] a)
- ArrayList
```java 
import java.util.ArrayList;

ArrayList<String> arrayListExample = new ArrayList<>();
arrayListExample.add("Apple");
```
    add(E e)
    add(int index, E element)
    addAll(Collection<? extends E> c)
    addAll(int index, Collection<? extends E> c)
    clear()
    contains(Object o)
    ensureCapacity(int minCapacity)
    get(int index)
    indexOf(Object o)
    isEmpty()
    iterator()
    lastIndexOf(Object o)
    remove(int index)
    remove(Object o)
    removeAll(Collection<?> c)
    retainAll(Collection<?> c)
    set(int index, E element)
    size()
    subList(int fromIndex, int toIndex)
    toArray()
    toArray(T[] a)

- Map and HashMap
```java
import java.util.Map;
import java.util.HashMap;

Map<String, Integer> mapExample = new HashMap<>();
mapExample.put("Apple", 1);

HashMap<String, Integer> hashMapExample = new HashMap<>();
hashMapExample.put("Apple", 1);
```
    clear()
    containsKey(Object key)
    containsValue(Object value)
    entrySet()
    get(Object key)
    isEmpty()
    keySet()
    put(K key, V value)
    putAll(Map<? extends K,? extends V> m)
    putIfAbsent(K key, V value)
    remove(Object key)
    remove(Object key, Object value)
    replace(K key, V value)
    replace(K key, V oldValue, V newValue)
    size()
    values()

- Set and HashSet
```java
import java.util.Set;
import java.util.HashSet;

Set<String> setExample = new HashSet<>();
setExample.add("Apple");

HashSet<String> hashSetExample = new HashSet<>();
hashSetExample.add("Apple");
```
    add(E e)
    addAll(Collection<? extends E> c)
    clear()
    contains(Object o)
    containsAll(Collection<?> c)
    equals(Object o)
    hashCode()
    isEmpty()
    iterator()
    remove(Object o)
    removeAll(Collection<?> c)
    retainAll(Collection<?> c)
    size()
    toArray()
    toArray(T[] a)

- LinkedList and Queue

```java
import java.util.Queue;
import java.util.LinkedList;

LinkedList<String> linkedListExample = new LinkedList<>();
linkedListExample.add("Apple");

Queue<String> queueExample = new LinkedList<>();
queueExample.add("Apple");
```
LinkedList (implements List, Deque, Queue)

    add(E e)
    add(int index, E element)
    addAll(Collection<? extends E> c)
    addAll(int index, Collection<? extends E> c)
    addFirst(E e)
    addLast(E e)
    clear()
    contains(Object o)
    descendingIterator()
    element()
    get(int index)
    getFirst()
    getLast()
    indexOf(Object o)
    isEmpty()
    iterator()
    lastIndexOf(Object o)
    offer(E e)
    offerFirst(E e)
    offerLast(E e)
    peek()
    peekFirst()
    peekLast()
    poll()
    pollFirst()
    pollLast()
    pop()
    push(E e)
    remove()
    remove(int index)
    remove(Object o)
    removeFirst()
    removeFirstOccurrence(Object o)
    removeLast()
    removeLastOccurrence(Object o)
    size()
    toArray()
    toArray(T[] a)

Queue

    add(E e)
    offer(E e)
    remove()
    poll()
    element()
    peek()

- Stack
```java
import java.util.Stack;

Stack<String> stackExample = new Stack<>();
stackExample.push("Apple");
```
    empty()
    peek()
    pop()
    push(E item)
    search(Object o)

- PriorityQueue

```java
import java.util.PriorityQueue;

PriorityQueue<String> priorityQueueExample = new PriorityQueue<>();
priorityQueueExample.add("Apple");
```
    add(E e)
    clear()
    contains(Object o)
    iterator()
    offer(E e)
    peek()
    poll()
    remove(Object o)
    size()
    toArray()
    toArray(T[] a)

These methods provide a comprehensive toolkit for working with these collections and classes in Java.

### Access Modifiers in Java
Access modifiers in Java determine the visibility and accessibility of classes, methods, and other members.
Java provides 4 primary access modifiers:
- Public: Accessible from any other class.
- Protected: Accessible within the same package and by subclasses.
- Default (Package-Private): Accessible only within the same package. If no access modifier is specified, it is the default.
- Private: Accessible only within the same class.

```java
package example;

// Public class accessible from anywhere
public class AccessModifiersExample {
    
    // Public method accessible from anywhere
    public void publicMethod() {
        System.out.println("This is a public method.");
    }
    
    // Protected method accessible within the same package and by subclasses
    protected void protectedMethod() {
        System.out.println("This is a protected method.");
    }
    
    // Default method accessible only within the same package
    void defaultMethod() {
        System.out.println("This is a default method.");
    }
    
    // Private method accessible only within the same class
    private void privateMethod() {
        System.out.println("This is a private method.");
    }
    
    // Static method accessible without instantiating the class
    public static void staticMethod() {
        System.out.println("This is a static method.");
    }
}

```

Combining with Other Modifiers

- Static: The static keyword allows a member to be accessed without instantiating the class.
- Final: The final keyword prevents a variable from being reassigned, a method from being overridden, or a class from being subclassed.
- Abstract: The abstract keyword is used to declare a class that cannot be instantiated, or a method that must be implemented by subclasses.

The main method in Java is the entry point of any Java application and must always be public and static:
```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```
public: The main method must be accessible from anywhere.
static: The main method must be called without creating an instance of the class.

This table summarizes the accessibility of members with different access modifiers.

| Modifier    | Class | Package | Subclass | World |
|-------------|-------|---------|----------|-------|
| **public**  |  Yes  |   Yes   |   Yes    |  Yes  |
| **protected**|  Yes  |   Yes   |   Yes    |   No  |
| **default** |  Yes  |   Yes   |    No    |   No  |
| **private** |  Yes  |    No   |    No    |   No  |

Understanding these access modifiers allows you to design your classes with proper encapsulation and control over access to class members.

### Glossary
- JPA (Java Persistence API), Hibernate, JDBC, POJO