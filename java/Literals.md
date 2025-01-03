
#### Java Literals

**Java Literals** simple values hote hain jo code mein directly represent kiye jaate hain. Ye fixed values hote hain jo program mein variables ko assign ki jati hain.

Chaliye Java mein available different types of literals ko samajhte hain in  **Hinenglish** :

---

### 1. **Integer Literals**

* Integer literals wo numbers hote hain jo directly likhe jaate hain.
* Example:

  ```java
  int x = 100;   // Decimal
  int y = 0b1010; // Binary (starts with 0b or 0B)
  int z = 077;    // Octal (starts with 0)
  int w = 0xFF;   // Hexadecimal (starts with 0x or 0X)
  ```

  #### Points:


  * `100`: Decimal number.
  * `0b1010`: Binary number.
  * `077`: Octal number.
  * `0xFF`: Hexadecimal number.

---

### 2. **Floating-Point Literals**

* Ye decimal point wale numbers hote hain.
* Example:
  ```java
  double pi = 3.14;     // Regular floating-point
  float rate = 2.5F;    // Float literal (suffix 'F' lagta hai)
  double exp = 1.2e3;   // Exponential form (1.2 * 10^3)
  ```

---

### 3. **Character Literals**

* Single character ko single quotes `' '` ke andar likha jata hai.
* Example:

  ```java
  char grade = 'A';        // Single character
  char num = '5';          // Digit as a character
  char unicode = '\u0041'; // Unicode character for 'A'
  ```

  #### Unicode:


  * `\u0041` ek Unicode representation hai.

---

### 4. **String Literals**

* Multiple characters ko double quotes `"` ke andar likha jata hai.
* Example:
  ```java
  String message = "Hello, World!";
  ```

---

### 5. **Boolean Literals**

* Boolean literals sirf do values lete hain: `true` ya `false`.
* Example:
  ```java
  boolean isActive = true;
  boolean isClosed = false;
  ```

---

### 6. **Null Literal**

* `null` ka use reference variables ke liye kiya jata hai jab unhe kisi object ka reference na diya jaye.
* Example:
  ```java
  String name = null;
  ```

---

### 7. **Literal Suffixes**

* Kuch literals ke saath suffix lagta hai:
  * `L` ya `l` (long literals):
    ```java
    long bigNum = 10000000000L;
    ```
  * `F` ya `f` (float literals):
    ```java
    float pi = 3.14F;
    ```
  * `D` ya `d` (optional for double, default):
    ```java
    double e = 2.718D;
    ```

---

### 8. **Binary, Octal, and Hexadecimal Literals**

* Binary: `0b` ya `0B` ke saath shuru hota hai.
  ```java
  int binaryNum = 0b1010; // 10 in decimal
  ```
* Octal: `0` ke saath shuru hota hai.
  ```java
  int octalNum = 071; // 57 in decimal
  ```
* Hexadecimal: `0x` ya `0X` ke saath shuru hota hai.
  ```java
  int hexNum = 0x1F; // 31 in decimal
  ```

---

### 9. **Underscore in Numeric Literals**

* Numeric values ko readable banane ke liye underscores (`_`) ka use kar sakte hain.
* Example:
  ```java
  int largeNum = 1_000_000;   // Same as 1000000
  double preciseValue = 3.14_15_92;
  ```

---

### Summary in Hinenglish:

* **Literals** wo fixed values hain jo Java mein variables ko assign ki ja sakti hain.
* **Types** : Integer, Floating-point, Character, String, Boolean, Null.
* **Special Features** : Underscores, Binary/Octal/Hexadecimal formats.

Agar kisi point mein confusion ho ya aur examples chahiye, toh batao! 😊
