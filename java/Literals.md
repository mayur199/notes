### **Literals in Java (Hinenglish Notes)**

Literals are fixed values that are directly assigned to variables in Java. Yeh kisi bhi data ka fixed representation hote hain, jo program ke runtime par change nahi hote.

---

### **Types of Literals:**

1. **Integer Literals (Number values)**
   * Yeh whole numbers hote hain, jaise `1`, `100`, `-50`.
   * **Example:**
     ```java
     int num = 10;  // 10 is an integer literal
     ```
2. **Floating-point Literals (Decimal values)**
   * Yeh fractional values ya decimal numbers ko represent karte hain, jaise `3.14`, `-0.5`.
   * **Example:**
     ```java
     double pi = 3.1415;  // 3.1415 is a floating-point literal
     ```
3. **Character Literals (Single characters)**
   * Ek single character `' '` ke andar likha jata hai, jaise `'A'`, `'b'`, `'1'`.
   * **Example:**
     ```java
     char letter = 'A';  // 'A' is a character literal
     ```
4. **String Literals (Sequence of characters)**
   * Double quotes `"` ke andar likhe hue words ya sentences, jaise `"Hello"`, `"123"`.
   * **Example:**
     ```java
     String name = "Java";  // "Java" is a string literal
     ```
5. **Boolean Literals (True or False)**
   * Sirf `true` ya `false` value ko represent karta hai.
   * **Example:**
     ```java
     boolean isJavaFun = true;  // true is a boolean literal
     ```
6. **Null Literal**
   * `null` ek special literal hai jo kisi reference variable ko empty ya null banata hai.
   * **Example:**
     ```java
     String name = null;  // null is a literal
     ```
7. **Binary, Octal, Hexadecimal Literals**
   * Binary: `0b` ke sath start hota hai (e.g., `0b1010` -> 10).
   * Octal: `0` se start hota hai (e.g., `012` -> 10).
   * Hexadecimal: `0x` se start hota hai (e.g., `0x1F` -> 31).
   * **Example:**
     ```java
     int binary = 0b1010;      // Binary literal
     int octal = 012;          // Octal literal
     int hex = 0x1F;           // Hexadecimal literal
     ```
8. **Underscore in Literals (Readable numbers)**
   * Java allows `_` between numbers for better readability.
   * **Example:**
     ```java
     int bigNumber = 1_000_000;  // Easy to read
     ```

---

### **Notes:**

* Literals Java mein hardcoded values hote hain.
* Har literal ka ek specific **data type** hota hai, jaise `int`, `float`, `boolean`.
* Binary, Octal, aur Hexadecimal literals se large values ko easily represent kar sakte hain.
