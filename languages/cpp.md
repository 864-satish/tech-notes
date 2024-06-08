# 📖 C++ Basics
C++ is a powerful general-purpose programming language that offers low-level memory manipulation features along with high-level abstractions. It is widely used for system/software development, game development, and more.

## 🚀 Data Types in C++
1. **Primitive Types**: Represent basic data types directly supported by the language.
```cpp
char: 8-bit signed integer. Range: -128 to 127.
short: 16-bit signed integer. Range: -32,768 to 32,767.
int: 32-bit signed integer. Range: -2<sup>31</sup> to 2<sup>31</sup>-1.
long: 64-bit signed integer. Range: -2<sup>63</sup> to 2<sup>63</sup>-1.
float: 32-bit floating-point number.
double: 64-bit floating-point number.
bool: Represents true or false.

    Compound Types: Composed of other types or built-in types and include arrays, pointers, references, and user-defined types such as structures and classes.

```cpp

#include <iostream>
#include <string>

using namespace std;

int main() {
    // Primitive data types
    char myChar = 'A';
    short myShort = 500;
    int myInt = 10000;
    long myLong = 1000000000L; // 'L' suffix for long literals
    float myFloat = 3.14f; // 'f' suffix for float literals
    double myDouble = 3.14159;
    bool myBool = true;

    // Compound data type (String)
    string myString = "Hello, C++!";
    
    return 0;
}
```

C++ Standard Library

C++ provides a rich set of libraries for various functionalities including I/O operations, string manipulation, containers, algorithms, etc.

    iostream: Input/output stream functionality.
    string: String manipulation operations.
    vector: Dynamic array implementation.
    map and unordered_map: Associative containers to store key-value pairs.
    set and unordered_set: Containers to store unique elements.
    algorithm: Common algorithms like sorting, searching, etc.

```cpp

#include <iostream>
#include <vector>
#include <map>
#include <algorithm>

using namespace std;

int main() {
    // Example usage of standard libraries
    vector<int> numbers = {3, 1, 4, 1, 5, 9, 2, 6, 5, 3};
    sort(numbers.begin(), numbers.end());

    map<string, int> ages;
    ages["Alice"] = 30;
    ages["Bob"] = 25;

    return 0;
}
```

## 🚀 Access Modifiers in C++

Access modifiers control the visibility and accessibility of class members.
C++ provides three access specifiers:

    public: Accessible from anywhere.
    protected: Accessible within the class and by derived classes.
    private: Accessible only within the class.

```cpp

class MyClass {
public:
    int publicVar;
    void publicMethod() {
        cout << "This is a public method." << endl;
    }

protected:
    int protectedVar;
    void protectedMethod() {
        cout << "This is a protected method." << endl;
    }

private:
    int privateVar;
    void privateMethod() {
        cout << "This is a private method." << endl;
    }
};

int main() {
    MyClass obj;
    obj.publicVar = 10;
    obj.publicMethod();
    // obj.protectedVar = 20; // Error: Cannot access protected member outside the class
    // obj.privateVar = 30; // Error: Cannot access private member outside the class

    return 0;
}

```


