
## **Statement** and **PreparedStatement**

**Statement** and **PreparedStatement** are two interfaces in Java's JDBC API used to execute SQL queries. They differ in functionality, performance, and security. Here’s a comparison explained in  **Hinenglish** :

---

### **1. Statement** :

* **Definition** : Ek **Statement** object SQL query ko directly execute karta hai.
* **Usage** : Jab query static ho aur parameters change na ho.
* **Security** : Vulnerable to **SQL Injection** (Unsafe hai agar user inputs directly queries mein use hote hain).
* **Performance** : Har baar query execute karte time SQL ko compile karna padta hai, so slower for repetitive queries.

 **Example** :

```java
Statement stmt = connection.createStatement();
String query = "INSERT INTO students (id, name) VALUES (1, 'Rahul')";
stmt.executeUpdate(query);
```

---

### **2. PreparedStatement** :

* **Definition** : Ek **PreparedStatement** object SQL query ko pre-compiled statement ke form mein maintain karta hai.
* **Usage** : Jab query mein parameters change hote hain (dynamic queries).
* **Security** : Safe from **SQL Injection** (User inputs automatically sanitized hote hain).
* **Performance** : Faster for repetitive queries because query compile ek baar hoti hai, aur baad mein execute hoti hai.

 **Example** :

```java
PreparedStatement pstmt = connection.prepareStatement("INSERT INTO students (id, name) VALUES (?, ?)");
pstmt.setInt(1, 1); // Replace first '?' with 1
pstmt.setString(2, "Rahul"); // Replace second '?' with 'Rahul'
pstmt.executeUpdate();
```

---

### **Comparison Table** :

| **Feature**           | **Statement**           | **PreparedStatement**   |
| --------------------------- | ----------------------------- | ----------------------------- |
| **Query Compilation** | Har baar compile hoti hai     | Ek baar compile hoti hai      |
| **Dynamic Query**     | Support nahi karta            | Support karta hai             |
| **Security**          | SQL Injection ka risk zyada   | SQL Injection safe            |
| **Performance**       | Slower for repetitive queries | Faster for repetitive queries |
| **Ease of Use**       | Simple for static queries     | Better for dynamic queries    |

---

### Kab use karein?

* **Statement** : Jab simple aur static queries ho.
* **PreparedStatement** : Jab queries dynamic ho ya performance aur security important ho.

Let me know if you need a practical example for each! 😊
