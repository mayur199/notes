### **🔹 `load-on-startup` Element in `web.xml`**

`load-on-startup` ek **optional** XML element hai jo **Servlet** ka initialization order define karta hai. Yeh element `web.xml` me  tag ke andar define hota hai.

---

### **🔹 Possible Values of `load-on-startup`**

| **Value**                                         | **Meaning (Matlab)**                                                                                                              |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Positive Number (0, 1, 2, etc.)**               | Servlet**container startup ke time**pe initialize hoga, aur jo number chhota hoga wo pehle initialize hoga. (Jaise priority list) |
| **Negative Number (-1, -2, etc.) or Not Defined** | Servlet**jab zarurat padegi tab initialize hoga**(Lazy Initialization)                                                            |

---

### **🔹 Example 1: Immediate (Eager) Loading (Positive Value)**

Agar `load-on-startup` **positive number** hai, to servlet **server start hone ke saath hi load** ho jayega.

```xml
<servlet>
    <servlet-name>MyServlet</servlet-name>
    <servlet-class>com.example.MyServlet</servlet-class>
    <load-on-startup>1</load-on-startup>
</servlet>
```

✅ **Explanation:**

* Yahaan `1` diya hai, iska matlab hai  **yeh servlet startup ke waqt initialize hoga** .
* Agar multiple servlets hain, to jo  **chhota number hoga wo pehle initialize hoga** .

---

### **🔹 Example 2: Lazy Loading (Negative Value or Not Defined)**

Agar `load-on-startup` **define nahi kiya** ya  **negative number diya** , to servlet  **tabhi initialize hoga jab pehli baar use hoga** .

```xml
<servlet>
    <servlet-name>LazyServlet</servlet-name>
    <servlet-class>com.example.LazyServlet</servlet-class>
    <load-on-startup>-1</load-on-startup>
</servlet>
```

✅ **Explanation:**

* Yahaan `-1` diya hai, iska matlab hai servlet tabhi load hoga  **jab pehli baar request aayegi** .
* Agar `load-on-startup` element likha hi nahi, tab bhi same behavior hoga.

---

### **🔹 Priority Order Example**

Agar multiple servlets hain aur alag-alag numbers diye hain:

```xml
<servlet>
    <servlet-name>FirstServlet</servlet-name>
    <servlet-class>com.example.FirstServlet</servlet-class>
    <load-on-startup>1</load-on-startup>
</servlet>

<servlet>
    <servlet-name>SecondServlet</servlet-name>
    <servlet-class>com.example.SecondServlet</servlet-class>
    <load-on-startup>2</load-on-startup>
</servlet>

<servlet>
    <servlet-name>ThirdServlet</servlet-name>
    <servlet-class>com.example.ThirdServlet</servlet-class>
    <load-on-startup>-1</load-on-startup>
</servlet>
```

✅ **Explanation:**

* `FirstServlet (1)` pehle initialize hoga.
* `SecondServlet (2)` uske baad initialize hoga.
* `ThirdServlet (-1)` sirf jab first request aayegi tab load hoga.

---

### **🔹 Summary Table - `load-on-startup` Values**

| **Value**                                    | **Initialization Time**              | **Use Case**                                                               |
| -------------------------------------------------- | ------------------------------------------ | -------------------------------------------------------------------------------- |
| **`0`ya positive number (`1, 2, 3...`)** | Server startup ke time (Eager Loading)     | Agar servlet**startup me load**karna hai (e.g., logging, pre-loading data) |
| **`-1`ya koi value na ho**                 | Jab pehli baar request aaye (Lazy Loading) | Jab servlet ka load**delay**karna ho                                       |

---

### **🚀 Conclusion**

* **Performance ke liye** : Frequently used servlets ko **startup pe load karna better hota hai** (`load-on-startup` with positive values).
* **Memory saving ke liye** : Rarely used servlets ke liye **lazy loading sahi hota hai** (`-1` ya missing `load-on-startup`).

Agar tumhe koi specific scenario ya doubt hai, to batao! 😊
