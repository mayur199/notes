Yeh rahe SQL ke kuch basic aur important notes jo aapko seekhne me madad karenge:

---

### **1. SQL (Structured Query Language)**

SQL ek standard programming language hai jo relational databases ko manage karne ke liye use hoti hai. Iska use data ko query (retrieve), insert, update, aur delete karne ke liye hota hai.

---

### **2. SQL Ke Basic Commands**

* **SELECT** : Data retrieve karne ke liye.

```sql
  SELECT column_name FROM table_name;
```

* **INSERT** : Data insert karne ke liye.

```sql
  INSERT INTO table_name (column1, column2) VALUES (value1, value2);
```

* **UPDATE** : Data update karne ke liye.

```sql
  UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```

* **DELETE** : Data delete karne ke liye.

```sql
  DELETE FROM table_name WHERE condition;
```

---

### **3. SQL Clauses**

* **WHERE** : Conditions apply karne ke liye.

```sql
  SELECT * FROM employees WHERE age > 30;
```

* **ORDER BY** : Data ko ascending ya descending order me sort karne ke liye.

```sql
  SELECT * FROM employees ORDER BY name DESC;
```

* **GROUP BY** : Data ko group karne ke liye (usually aggregate functions ke sath).

```sql
  SELECT department, COUNT(*) FROM employees GROUP BY department;
```

* **HAVING** : Grouped data ko filter karne ke liye.

```sql
  SELECT department, COUNT(*) FROM employees GROUP BY department HAVING COUNT(*) > 5;
```

---

### **4. SQL Joins**

* **INNER JOIN** : Only matching rows ko return karta hai.

```sql
  SELECT * FROM table1 INNER JOIN table2 ON table1.id = table2.id;
```

* **LEFT JOIN** : Left table ke sabhi rows aur right table ke matching rows ko return karta hai.

```sql
  SELECT * FROM table1 LEFT JOIN table2 ON table1.id = table2.id;
```

* **RIGHT JOIN** : Right table ke sabhi rows aur left table ke matching rows ko return karta hai.

```sql
  SELECT * FROM table1 RIGHT JOIN table2 ON table1.id = table2.id;
```

* **FULL OUTER JOIN** : Dono tables ke sabhi rows ko return karta hai (matching ya non-matching).

```sql
  SELECT * FROM table1 FULL OUTER JOIN table2 ON table1.id = table2.id;
```

---

### **5. SQL Functions**

* **Aggregate Functions** :
* `COUNT()`: Records ki total count return karta hai.
  ```sql
  SELECT COUNT(*) FROM employees;
  ```
* `SUM()`: Total sum of a column return karta hai.
  ```sql
  SELECT SUM(salary) FROM employees;
  ```
* `AVG()`: Average value of a column return karta hai.
  ```sql
  SELECT AVG(salary) FROM employees;
  ```
* `MIN()`, `MAX()`: Minimum ya maximum value return karta hai.
  ```sql
  SELECT MIN(salary), MAX(salary) FROM employees;
  ```
* **String Functions** :
* `CONCAT()`: Strings ko concatenate karta hai.
  ```sql
  SELECT CONCAT(first_name, ' ', last_name) FROM employees;
  ```
* `LENGTH()`: String ki length return karta hai.
  ```sql
  SELECT LENGTH(name) FROM employees;
  ```
* **Date Functions** :
* `NOW()`: Current date aur time return karta hai.
  ```sql
  SELECT NOW();
  ```
* `DATE_ADD()`: Date me specified interval add karta hai.
  ```sql
  SELECT DATE_ADD(NOW(), INTERVAL 10 DAY);
  ```

---

### **6. Subqueries**

* **Simple Subquery** : Ek query jo doosri query ke andar hoti hai.

```sql
  SELECT name FROM employees WHERE department_id = (SELECT id FROM departments WHERE name = 'HR');
```

* **Correlated Subquery** : Subquery me outer query ke values use hoti hain.

```sql
  SELECT name FROM employees e WHERE salary > (SELECT AVG(salary) FROM employees WHERE department_id = e.department_id);
```

---

### **7. SQL Constraints**

* **PRIMARY KEY** : Table me unique aur non-null values specify karta hai.

```sql
  CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50)
  );
```

* **FOREIGN KEY** : Ek table ko doosre table ke column se link karta hai.

```sql
  CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(id)
  );
```

* **NOT NULL** : Column me null values nahi allow karta.
* **UNIQUE** : Column ke values ko unique banata hai.

---

### **8. Normalization**

* **1NF (First Normal Form)** : Har column ko atomic value (single value) hona chahiye.
* **2NF (Second Normal Form)** : 1NF aur non-prime attributes ko fully functional dependencies ke sath organize karta hai.
* **3NF (Third Normal Form)** : 2NF aur transitive dependencies ko eliminate karta hai.

---

### **9. Indexing**

* **INDEX** : Performance improve karne ke liye table pe indexing hoti hai.

```sql
  CREATE INDEX idx_name ON table_name (column_name);
```

---

Yeh SQL ke kuch important topics the. Agar aapko koi specific topic ya example chahiye ho, toh bataiye!
