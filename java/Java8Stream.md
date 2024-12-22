Java 8 ne **Functional Programming** ko introduce kiya hai, jisme hum  **lambda expressions** ,  **streams** , aur **functional interfaces** ka use karte hain. Ye programming style code ko concise, readable aur easy banata hai. Main aapko Java 8 ke kuch important features explain karta hoon, jo functional programming se related hain.

### 1. **Lambda Expressions**

Lambda expressions ek simple tarika hain functions ko express karne ka. Yeh ek chhoti anonymous function hoti hai, jise hum as an argument pass kar sakte hain ya kisi variable mein store kar sakte hain.

#### Syntax:

```java
(parameters) -> expression
```

#### Example:

```java
import java.util.Arrays;
import java.util.List;

public class LambdaExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("John", "Jane", "Adam", "Eve");

        // Lambda expression for printing names
        names.forEach(name -> System.out.println(name));
    }
}
```

### Explanation:

* `names.forEach(name -> System.out.println(name));` mein lambda expression ka use kiya gaya hai. Yeh ek simple function hai jo har `name` ko print karta hai.

---

### 2. **Functional Interfaces**

Functional interfaces wo interfaces hote hain jisme sirf ek abstract method hota hai. Java 8 mein **@FunctionalInterface** annotation ka use karke hum ek interface ko functional interface bana sakte hain.

#### Example:

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void sayHello();  // Single abstract method
}

public class FunctionalInterfaceExample {
    public static void main(String[] args) {
        // Using lambda expression to implement functional interface
        MyFunctionalInterface hello = () -> System.out.println("Hello, World!");
        hello.sayHello();  // Output: Hello, World!
    }
}
```

### Explanation:

* `MyFunctionalInterface` mein ek hi abstract method `sayHello()` hai. Hum lambda expression ka use karke usse implement karte hain.

---

### 3. **Streams API**

Streams API Java 8 mein data ko process karne ka ek powerful way hai. Aap collections ke data ko filter, map, sort, aur reduce kar sakte hain. Yeh parallel processing ko bhi support karta hai.

#### Example (Filter and Map using Stream):

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamsExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("John", "Jane", "Adam", "Eve", "Jack");

        // Filter names that start with "J" and convert them to uppercase
        List<String> filteredNames = names.stream()
                                          .filter(name -> name.startsWith("J"))
                                          .map(name -> name.toUpperCase())
                                          .collect(Collectors.toList());

        System.out.println(filteredNames);  // Output: [JOHN, JACK]
    }
}
```

### Explanation:

* `stream()` method se hum list ko stream mein convert karte hain.
* `filter()` method se hum names ko filter karte hain jo "J" se start hote hain.
* `map()` method se hum un names ko uppercase mein convert karte hain.
* `collect()` se result ko list mein convert karte hain.

---

### 4. **Method References**

Method references bhi ek tarika hain lambda expressions ko replace karne ka. Yeh code ko aur concise aur readable banata hai.

#### Example:

```java
import java.util.Arrays;
import java.util.List;

public class MethodReferenceExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("John", "Jane", "Adam", "Eve");

        // Method reference for printing names
        names.forEach(System.out::println);
    }
}
```

### Explanation:

* `System.out::println` ek method reference hai jo `println` method ko call karta hai, jisme lambda expression ko replace kiya gaya hai.

---

### 5. **Optional Class**

Java 8 mein **Optional** class introduce ki gayi hai jo null values ko handle karne mein help karti hai. Yeh null pointer exceptions se bachne ka ek tareeka hai.

#### Example:

```java
import java.util.Optional;

public class OptionalExample {
    public static void main(String[] args) {
        String name = "John";

        // Creating an Optional object
        Optional<String> optionalName = Optional.ofNullable(name);

        // Checking if value is present
        optionalName.ifPresent(n -> System.out.println("Name: " + n));

        // Using orElse to provide default value
        String defaultName = optionalName.orElse("Default Name");
        System.out.println(defaultName);  // Output: John
    }
}
```

### Explanation:

* `Optional.ofNullable(name)` se hum ek Optional object create karte hain.
* `ifPresent()` se hum check karte hain ki value present hai ya nahi, aur agar hai toh usse use karte hain.
* `orElse()` se hum default value provide karte hain agar value null hai.

---

## Step by Step code break down

Ye code ek **Stream** ka use kar raha hai jo `names` list ke elements ko process karta hai. Main aapko step-by-step samjhaata hoon:

### Code Breakdown:

```java
List<String> filteredNames = names.stream()              // Step 1
                                  .filter(name -> name.startsWith("J"))  // Step 2
                                  .map(name -> name.toUpperCase())      // Step 3
                                  .collect(Collectors.toList());        // Step 4
```

### Explanation (Step-by-Step):

1. **`names.stream()`** :

* Yeh line `names` list ko **stream** mein convert kar rahi hai.
* Stream ek pipeline create karta hai jisme hum data ko manipulate karte hain. List ko stream mein convert karne ka matlab hai ki hum list ke elements ko ek sequence mein process kar sakte hain.

1. **`filter(name -> name.startsWith("J"))`** :

* Yeh step ek **filter** operation hai.
* `name -> name.startsWith("J")` ek lambda expression hai, jo har name ko check karta hai aur sirf unhi names ko rakhne ka kaam karta hai jo "J" se start hote hain.
* Agar name "J" se start hota hai, toh wo stream mein rakha jata hai, baaki names remove ho jate hain.

1. **`map(name -> name.toUpperCase())`** :

* Yeh **map** operation hai.
* `name -> name.toUpperCase()` lambda expression har name ko uppercase (bade letters) mein convert kar raha hai.
* Matlab, jo bhi name "J" se start hota hai, usse capital letters mein convert kiya ja raha hai.

1. **`collect(Collectors.toList())`** :

* Yeh line stream ke processed results ko ek list mein convert kar rahi hai.
* `Collectors.toList()` stream ke elements ko collect karke ek new **List** mein daal deta hai.

### Example with Names:

Agar `names` list mein yeh values hain:

```java
List<String> names = Arrays.asList("John", "Jane", "Adam", "Jack");
```

Toh ye code  **John** ,  **Jane** , aur **Jack** ko filter karega (kyunki sab "J" se start hote hain), phir unhe uppercase mein convert karega (John → JOHN, Jane → JANE, Jack → JACK), aur end mein unhe ek **List** ke form mein return karega:

### Output:

```
[JOHN, JANE, JACK]
```

### Simple Samajh:

* **Stream** ka matlab hai ki aap ek sequence mein data ko process kar rahe ho.
* **Filter** se hum unwanted elements ko hata dete hain.
* **Map** se hum data ko modify karte hain (jaise uppercase karna).
* **Collect** se hum final result ko ek list mein store karte hain.

---

## Convert to employee object using map


Agar aap `names` list ke elements ko **Employee** objects mein convert karna chahte hain, jisme har `Employee` object ka ek **name** field ho, toh aap thoda modification kar sakte hain. Sabse pehle, aapko **Employee** class banani padegi, aur phir stream ko modify karke `Employee` object create kar sakte hain.

### Step-by-Step:

1. **Employee Class** Banaiye:
   * Employee class mein `name` field hoga, aur constructor ke through name ko set karenge.
2. **Stream Processing** :

* List ko filter aur map karenge, aur phir **Employee** object create karenge.

### Code Example:

#### 1. Employee Class:

```java
public class Employee {
    private String name;

    // Constructor
    public Employee(String name) {
        this.name = name;
    }

    // Getter for name
    public String getName() {
        return name;
    }

    @Override
    public String toString() {
        return "Employee{name='" + name + "'}";
    }
}
```

#### 2. Main Class to Convert Names to Employee Objects:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class EmployeeExample {
    public static void main(String[] args) {
        // Initial list of names
        List<String> names = Arrays.asList("John", "Jane", "Adam", "Jack");

        // Convert names to Employee objects
        List<Employee> employees = names.stream()                       // Step 1: Convert list to stream
                                       .filter(name -> name.startsWith("J"))   // Step 2: Filter names starting with "J"
                                       .map(name -> new Employee(name.toUpperCase()))  // Step 3: Create Employee objects
                                       .collect(Collectors.toList());    // Step 4: Collect to List of Employee objects

        // Print list of employees
        employees.forEach(System.out::println);  // Output the employee list
    }
}
```

### Explanation:

* **`Employee` class** : Isme ek `name` field hai aur constructor ke through name set kiya jata hai.
* **Stream Operations** :

1. **`names.stream()`** : List ko stream mein convert kiya gaya hai.
2. **`filter(name -> name.startsWith("J"))`** : Filter operation jo sirf un names ko rakhta hai jo "J" se start hote hain.
3. **`map(name -> new Employee(name.toUpperCase()))`** : Har filtered name ko uppercase mein convert kar ke ek `Employee` object create kiya gaya hai.
4. **`collect(Collectors.toList())`** : Stream ke results ko `List<Employee>` mein convert kiya gaya hai.

### Output:

```
Employee{name='JOHN'}
Employee{name='JANE'}
Employee{name='JACK'}
```

### Summary:

* Humne **names** list ko filter kiya, uske baad unhe uppercase mein convert karke **Employee** objects banaye, aur phir unhe list mein store kiya.
