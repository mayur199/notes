
HTTP methods define kaise client aur server interact karte hain web applications me. Ye methods batate hain ki ek request ka kya action hoga. Chaliye sabhi HTTP methods ko detail me samajhte hain:

---

### **1. GET**

🔹  **Purpose** : Server se data retrieve karne ke liye use hota hai. (Jaise ek webpage ya resource ko load karna)

🔹  **Features** :

* Sirf data fetch karta hai, modify nahi karta.
* Cache ho sakta hai.
* URL ke query string me parameters bhej sakte hain.

🔹  **Example** :

```http
GET /index.html HTTP/1.1
Host: www.example.com
```

---

### **2. POST**

🔹  **Purpose** : Server par naye data create karne ya form submit karne ke liye use hota hai.

🔹  **Features** :

* Data modify kar sakta hai.
* Request body me data bhejta hai (URL me visible nahi hota).
* Idempotent nahi hota (bar-bar request bhejne par alag effect ho sakta hai).

🔹  **Example** :

```http
POST /submit-form HTTP/1.1
Host: www.example.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

name=John&age=30
```

---

### **3. PUT**

🔹  **Purpose** : Ek existing resource ko replace karne ya naye resource ko create karne ke liye use hota hai.

🔹  **Features** :

* Agar resource exist karta hai, to replace ho jata hai.
* Agar resource exist nahi karta, to create ho sakta hai.
* Idempotent hota hai (bar-bar same request bhejne par same effect hoga).

🔹  **Example** :

```http
PUT /users/123 HTTP/1.1
Host: www.example.com
Content-Type: application/json
Content-Length: 32

{"name":"John", "age":30}
```

---

### **4. DELETE**

🔹  **Purpose** : Ek resource ko server se delete karne ke liye use hota hai.

🔹  **Features** :

* Resource remove kar deta hai.
* Idempotent hota hai (agar same request multiple times bheji jaye to bhi result same hi rahega).

🔹  **Example** :

```http
DELETE /users/123 HTTP/1.1
Host: www.example.com
```

---

### **5. PATCH**

🔹  **Purpose** : Resource ke sirf kuch parts ko update karne ke liye use hota hai.

🔹  **Features** :

* PUT ke opposite, ye sirf specific fields update karta hai.
* Idempotent hota hai (multiple baar same request bhejne se same effect hoga).

🔹  **Example** :

```http
PATCH /users/123 HTTP/1.1
Host: www.example.com
Content-Type: application/json
Content-Length: 18

{"age":31}
```

---

### **6. OPTIONS**

🔹  **Purpose** : Server se yeh puchhne ke liye ki ek resource ke liye kaunse HTTP methods allowed hain.

🔹  **Features** :

* Request send karke check kar sakte hain ki server kya support karta hai.
* CORS (Cross-Origin Resource Sharing) ke liye use hota hai.

🔹  **Example** :

```http
OPTIONS /users/123 HTTP/1.1
Host: www.example.com
```

---

### **7. HEAD**

🔹  **Purpose** : GET jaisa hi hota hai, lekin sirf headers return karta hai, response body nahi bhejta.

🔹  **Features** :

* Ye check karne ke liye useful hai ki resource exist karta hai ya nahi.
* Metadata retrieve karne ke liye use hota hai.

🔹  **Example** :

```http
HEAD /index.html HTTP/1.1
Host: www.example.com
```

---

### **8. TRACE**

🔹  **Purpose** : Request ko trace karne aur debugging ke liye use hota hai.

🔹  **Features** :

* Server request ko waise ka waise hi response me return karta hai.
* Mostly debugging aur diagnostics ke liye useful hota hai.

🔹  **Example** :

```http
TRACE /path/to/resource HTTP/1.1
Host: www.example.com
```

---

### **9. CONNECT**

🔹  **Purpose** : Ek secure tunnel establish karne ke liye use hota hai (jaise SSL ke liye).

🔹  **Features** :

* Mostly HTTP proxies ke through SSL/TLS connections establish karne ke liye use hota hai.

🔹  **Example** :

```http
CONNECT www.example.com:443 HTTP/1.1
Host: www.example.com
```

---

### **Summary Table: HTTP Methods in Hindi-English**

| **Method**  | **Purpose (Kya Karta Hai?)**               | **Key Features**                      |
| ----------------- | ------------------------------------------------ | ------------------------------------------- |
| **GET**     | Server se data fetch karna                       | Safe, cacheable, sirf retrieve karta hai.   |
| **POST**    | Server par naye data submit karna                | Data modify karta hai, non-idempotent.      |
| **PUT**     | Pura resource replace karna ya naya create karna | Idempotent, same request ka same result.    |
| **DELETE**  | Resource ko remove karna                         | Idempotent, delete ka same result hota hai. |
| **PATCH**   | Sirf kuch fields update karna                    | Partial update, idempotent hota hai.        |
| **OPTIONS** | Server se allowed methods ke baare me puchhna    | CORS aur API testing ke liye useful.        |
| **HEAD**    | Resource ka sirf header retrieve karna           | GET jaisa, but response body nahi bhejta.   |
| **TRACE**   | Request ko trace aur debug karna                 | Debugging aur diagnostics ke liye.          |
| **CONNECT** | SSL tunnel establish karna                       | Secure communication ke liye useful.        |

---

Agar tumhe ek web application banana hai, to ye HTTP methods samajhna zaroori hai. Agar kisi specific method ya real-world example ke baare me aur jaan'na hai, to batao! 🚀
