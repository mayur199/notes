### **RDBMS Basics in Hinglish**

**RDBMS (Relational Database Management System)** ek software hai jo **relational model** ke upar kaam karta hai. Iska use **data ko store, manage, aur retrieve** karne ke liye hota hai. Data ko **tables (rows aur columns)** ke form me organize kiya jata hai, jisme har table ek specific **entity** ko represent karta hai.

---

### **Key Features of RDBMS:**

1. **Structured Data Storage** : Data ko **tables** ke form me store karta hai.
2. **Primary Key** : Har row ko uniquely identify karne ke liye ek **primary key** hoti hai.
3. **Relationships** : Tables ke beech **relationships** banakar data ko efficiently link kiya jata hai.
4. **SQL (Structured Query Language)** : RDBMS ke sath kaam karne ke liye SQL use hoti hai.
5. **Data Integrity** : Rules define kiye jate hain jo ensure karte hain ki data correct aur consistent ho.

---

### **RDBMS Components:**

1. **Tables (Entities)** :

* Data ko rows (tuples) aur columns (attributes) me store kiya jata hai.
* Example: `Student` table| ID  | Name  | Age |
  | --- | ----- | --- |
  | 101 | Raj   | 20  |
  | 102 | Priya | 22  |

1. **Keys** :

* **Primary Key** : Har row ka unique identifier (e.g., `ID` column).
* **Foreign Key** : Do tables ke beech relation establish karne ke liye use hoti hai.

1. **Schema** :

* Ek blueprint jo table ka structure define karta hai (columns aur data types).

1. **Indexes** :

* Query ko fast banane ke liye column pe index banaya jata hai.

1. **SQL Commands** :

* Data manage karne ke liye **SQL** commands ka use hota hai, jaise:
  * **DDL (Data Definition Language)** : Create, Alter, Drop
  * **DML (Data Manipulation Language)** : Insert, Update, Delete
  * **DQL (Data Query Language)** : Select

---

### **Benefits of RDBMS:**

1. **Consistency** : Data redundancy aur inconsistency avoid hoti hai.
2. **Data Security** : Access controls aur permissions ke sath secure environment provide karta hai.
3. **Scalability** : Large data ko handle kar sakta hai.
4. **Ease of Use** : SQL queries ke sath easily interact kar sakte hain.

---

### **Popular RDBMS Software:**

1. Oracle
2. MySQL
3. PostgreSQL
4. Microsoft SQL Server
5. SQLite

---

### **Basic Example in SQL:**

1. **Create a Table** :

```sql
   CREATE TABLE Student (
       ID INT PRIMARY KEY,
       Name VARCHAR(50),
       Age INT
   );
```

1. **Insert Data** :

```sql
   INSERT INTO Student (ID, Name, Age) VALUES (101, 'Raj', 20);
   INSERT INTO Student (ID, Name, Age) VALUES (102, 'Priya', 22);
```

1. **Select Data** :

```sql
   SELECT * FROM Student;
```

1. **Update Data** :

```sql
   UPDATE Student SET Age = 21 WHERE ID = 101;
```

1. **Delete Data** :

```sql
   DELETE FROM Student WHERE ID = 102;
```

---

### **Relationships in RDBMS:**

1. **One-to-One** : Ek row ka dusri table me ek hi row se relation.

* Example: Aadhaar details aur user login.

1. **One-to-Many** : Ek row ka multiple rows se relation.

* Example: Ek teacher ka multiple students ko padhaana.

1. **Many-to-Many** : Do tables me multiple rows ka relation.

* Example: Students aur courses.

---

### **Real-Life Use Case in Hinglish:**

Agar aapke paas ek school hai aur uska data manage karna hai (students, teachers, courses, attendance), to RDBMS ka use karke aap tables create karenge:

1. **Student Table** : ID, Name, Class
2. **Teacher Table** : ID, Name, Subject
3. **Attendance Table** : StudentID, Date, Status

---

### **Conclusion:**

RDBMS ek efficient tarika hai structured data ko handle karne ke liye. Iske through aap apne applications ke liye robust aur scalable database system bana sakte hain. SQL seekhna RDBMS me kaam karne ke liye essential hai.
