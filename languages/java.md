# 📖 Java Basics
Java is an object-oriented, class-based, concurrent, secured and general-purpose computer-programming language.

## 🚀 Data Types in Java
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

## 🚀 Java Collections and Classes Initialization 
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

## 🚀 Access Modifiers in Java
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

## 🚀 Object-Oriented Programming (OOP) Concepts 

- Classes : A class is like a blueprint for creating objects. 
- Objects : An object is an instance of a class.

**Example**: Consider a Car class that defines the properties and behaviors of a car.

Example:

java

public class Car {
    // Fields (properties)
    String brand;
    String model;
    int year;

    // Constructor
    public Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }

    // Method (behavior)
    public void displayInfo() {
        System.out.println("Brand: " + brand + ", Model: " + model + ", Year: " + year);
    }

    // Main method to create an object and call its method
    public static void main(String[] args) {
        Car car1 = new Car("Toyota", "Camry", 2020);
        car1.displayInfo();  // Outputs: Brand: Toyota, Model: Camry, Year: 2020
    }
}

Inheritance

Inheritance allows a class (child class) to inherit properties and methods from another class (parent class).

Real-Life Example:

Consider Vehicle as a parent class and Car and Bike as child classes.

Example:

java

// Parent class
class Vehicle {
    void start() {
        System.out.println("Vehicle is starting.");
    }

    void stop() {
        System.out.println("Vehicle is stopping.");
    }
}

// Child class
class Car extends Vehicle {
    void openTrunk() {
        System.out.println("Opening the car trunk.");
    }

    public static void main(String[] args) {
        Car car = new Car();
        car.start();  // Inherited method
        car.openTrunk();  // Car-specific method
        car.stop();  // Inherited method
    }
}

Polymorphism

Polymorphism allows methods to do different things based on the object it is acting upon. It can be achieved by method overriding (runtime polymorphism) and method overloading (compile-time polymorphism).

Real-Life Example:

Different animals make different sounds.

Example:

java

class Animal {
    void makeSound() {
        System.out.println("Some generic animal sound.");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Bark");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Meow");
    }
}

public class PolymorphismExample {
    public static void main(String[] args) {
        Animal myDog = new Dog();
        Animal myCat = new Cat();

        myDog.makeSound();  // Outputs: Bark
        myCat.makeSound();  // Outputs: Meow
    }
}

Encapsulation

Encapsulation is the concept of wrapping the data (variables) and code (methods) together as a single unit, and restricting access to some of the object's components.

Real-Life Example:

Consider a BankAccount class with private fields and public getter and setter methods.

Example:

java

public class BankAccount {
    // Private fields
    private String accountNumber;
    private double balance;

    // Constructor
    public BankAccount(String accountNumber, double balance) {
        this.accountNumber = accountNumber;
        this.balance = balance;
    }

    // Getter and setter methods
    public String getAccountNumber() {
        return accountNumber;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }

    public static void main(String[] args) {
        BankAccount account = new BankAccount("123456789", 1000.0);
        account.deposit(500.0);
        account.withdraw(200.0);
        System.out.println("Account Number: " + account.getAccountNumber());
        System.out.println("Balance: " + account.getBalance());
    }
}

Abstraction

Abstraction is the concept of hiding the implementation details and showing only the functionality to the user.

Real-Life Example:

Consider an AbstractClass for a template and a concrete class that implements the abstract methods.

Example:

java

abstract class Vehicle {
    // Abstract method (does not have a body)
    abstract void fuelType();

    // Regular method
    void start() {
        System.out.println("Vehicle is starting.");
    }
}

class Car extends Vehicle {
    // Implementing the abstract method
    void fuelType() {
        System.out.println("Car runs on petrol.");
    }

    public static void main(String[] args) {
        Vehicle myCar = new Car();
        myCar.start();  // Outputs: Vehicle is starting.
        myCar.fuelType();  // Outputs: Car runs on petrol.
    }
}

Day 7: Exception Handling and File I/O
Exception Handling

Exception handling is a mechanism to handle runtime errors, allowing the program to continue execution.

Real-Life Example:

Consider handling an array out-of-bounds exception.

Example:

java

public class ExceptionHandlingExample {
    public static void main(String[] args) {
        try {
            int[] array = new int[5];
            System.out.println(array[5]);  // This will throw an ArrayIndexOutOfBoundsException
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Array index is out of bounds!");
        } finally {
            System.out.println("This block always executes.");
        }
    }
}

File I/O

File I/O involves reading from and writing to files.

Real-Life Example:

Reading from a file and writing to a file.

Example: Reading a file:

java

import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class FileReadingExample {
    public static void main(String[] args) {
        try (BufferedReader br = new BufferedReader(new FileReader("example.txt"))) {
            String line;
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

Example: Writing to a file:

java

import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class FileWritingExample {
    public static void main(String[] args) {
        try (BufferedWriter bw = new BufferedWriter(new FileWriter("example.txt"))) {
            bw.write("Hello, world!");
            bw.newLine();
            bw.write("This is a new line.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

Summary

    Day 6 covers the basics of OOP in Java: classes, objects, inheritance, polymorphism, encapsulation, and abstraction with real-life examples.

## 🚀 Object-Oriented Programming (OOP) Concepts
Real-Life Example:
Imagine you are modeling a library system. A Book class represents books in the library.

Example:

java

public class Book {
    // Fields (properties)
    String title;
    String author;
    int yearPublished;

    // Constructor
    public Book(String title, String author, int yearPublished) {
        this.title = title;
        this.author = author;
        this.yearPublished = yearPublished;
    }

    // Method (behavior)
    public void displayInfo() {
        System.out.println("Title: " + title + ", Author: " + author + ", Year Published: " + yearPublished);
    }

    // Main method to create an object and call its method
    public static void main(String[] args) {
        Book book1 = new Book("1984", "George Orwell", 1949);
        book1.displayInfo();  // Outputs: Title: 1984, Author: George Orwell, Year Published: 1949
    }
}

In this example, Book is a class with properties like title, author, and yearPublished, and a method displayInfo() to display book details. The main method creates an instance of Book and calls the displayInfo() method.
Inheritance

Inheritance allows a class to inherit the properties and methods of another class.

Real-Life Example:
Consider a library system where Media is a parent class, and Book and DVD are child classes.

Example:

java

// Parent class
class Media {
    String title;
    int yearPublished;

    // Constructor
    public Media(String title, int yearPublished) {
        this.title = title;
        this.yearPublished = yearPublished;
    }

    // Method
    public void displayInfo() {
        System.out.println("Title: " + title + ", Year Published: " + yearPublished);
    }
}

// Child class
class Book extends Media {
    String author;

    // Constructor
    public Book(String title, String author, int yearPublished) {
        super(title, yearPublished);
        this.author = author;
    }

    // Method
    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Author: " + author);
    }

    public static void main(String[] args) {
        Book book = new Book("1984", "George Orwell", 1949);
        book.displayInfo();  // Outputs: Title: 1984, Year Published: 1949, Author: George Orwell
    }
}

// Child class
class DVD extends Media {
    String director;

    // Constructor
    public DVD(String title, String director, int yearPublished) {
        super(title, yearPublished);
        this.director = director;
    }

    // Method
    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Director: " + director);
    }

    public static void main(String[] args) {
        DVD dvd = new DVD("Inception", "Christopher Nolan", 2010);
        dvd.displayInfo();  // Outputs: Title: Inception, Year Published: 2010, Director: Christopher Nolan
    }
}

Here, Book and DVD classes inherit the properties and methods from the Media class. This means Book and DVD classes can use and override the methods of Media.
Polymorphism

Polymorphism allows methods to do different things based on the object it is acting upon.

Real-Life Example:
In a library system, different types of media (books, DVDs) have a common method to display information.

Example:

java

class Media {
    String title;
    int yearPublished;

    // Constructor
    public Media(String title, int yearPublished) {
        this.title = title;
        this.yearPublished = yearPublished;
    }

    // Method
    public void displayInfo() {
        System.out.println("Title: " + title + ", Year Published: " + yearPublished);
    }
}

class Book extends Media {
    String author;

    public Book(String title, String author, int yearPublished) {
        super(title, yearPublished);
        this.author = author;
    }

    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Author: " + author);
    }
}

class DVD extends Media {
    String director;

    public DVD(String title, String director, int yearPublished) {
        super(title, yearPublished);
        this.director = director;
    }

    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Director: " + director);
    }
}

public class PolymorphismExample {
    public static void main(String[] args) {
        Media book = new Book("1984", "George Orwell", 1949);
        Media dvd = new DVD("Inception", "Christopher Nolan", 2010);

        book.displayInfo();  // Outputs: Title: 1984, Year Published: 1949, Author: George Orwell
        dvd.displayInfo();   // Outputs: Title: Inception, Year Published: 2010, Director: Christopher Nolan
    }
}

In this example, displayInfo() is called on different types of Media objects (book and DVD), and the correct version of the method is executed based on the actual object type.
Encapsulation

Encapsulation is the mechanism of wrapping the data (fields) and methods (code) together as a single unit and restricting access to some of the object's components.

Real-Life Example:
In a banking system, a BankAccount class encapsulates the details of a bank account.

Example:

java

public class BankAccount {
    // Private fields
    private String accountNumber;
    private double balance;

    // Constructor
    public BankAccount(String accountNumber, double balance) {
        this.accountNumber = accountNumber;
        this.balance = balance;
    }

    // Getter and setter methods
    public String getAccountNumber() {
        return accountNumber;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }

    public static void main(String[] args) {
        BankAccount account = new BankAccount("123456789", 1000.0);
        account.deposit(500.0);
        account.withdraw(200.0);
        System.out.println("Account Number: " + account.getAccountNumber());
        System.out.println("Balance: " + account.getBalance());  // Outputs: Balance: 1300.0
    }
}

In this example, the BankAccount class encapsulates the account number and balance fields. The fields are private and can only be accessed through public getter and setter methods.
Abstraction

Abstraction is the concept of hiding the implementation details and showing only the functionality to the user.

Real-Life Example:
In a library system, an abstract class Media defines abstract methods to be implemented by subclasses.

Example:

java

abstract class Media {
    String title;
    int yearPublished;

    // Constructor
    public Media(String title, int yearPublished) {
        this.title = title;
        this.yearPublished = yearPublished;
    }

    // Abstract method
    abstract void displayInfo();

    // Regular method
    void start() {
        System.out.println("Starting media.");
    }
}

class Book extends Media {
    String author;

    public Book(String title, String author, int yearPublished) {
        super(title, yearPublished);
        this.author = author;
    }

    @Override
    void displayInfo() {
        System.out.println("Title: " + title + ", Year Published: " + yearPublished + ", Author: " + author);
    }
}

class DVD extends Media {
    String director;

    public DVD(String title, String director, int yearPublished) {
        super(title, yearPublished);
        this.director = director;
    }

    @Override
    void displayInfo() {
        System.out.println("Title: " + title + ", Year Published: " + yearPublished + ", Director: " + director);
    }
}

public class AbstractionExample {
    public static void main(String[] args) {
        Media book = new Book("1984", "George Orwell", 1949);
        Media dvd = new DVD("Inception", "Christopher Nolan", 2010);

        book.displayInfo();  // Outputs: Title: 1984, Year Published: 1949, Author: George Orwell
        dvd.displayInfo();   // Outputs: Title: Inception, Year Published: 2010, Director: Christopher Nolan
    }
}

Here, the Media class is abstract and defines an abstract method displayInfo(). Subclasses Book and DVD implement this method, providing specific behavior for each type of media.

## 🚀 Glossary
- JPA (Java Persistence API), Hibernate, JDBC, POJO