
### **Question 1: Constructor Execution Order**  
What will be the output of the following Java code?  
```java
class A {
    A() {
        System.out.println("Constructor of A");
    }
}

class B extends A {
    B() {
        System.out.println("Constructor of B");
    }
}

class C extends B {
    C() {
        System.out.println("Constructor of C");
    }
}

public class Test {
    public static void main(String[] args) {
        C obj = new C();
    }
}
```
**A.**  
```
Constructor of A  
Constructor of B  
Constructor of C  
```
**B.**  
```
Constructor of C  
Constructor of B  
Constructor of A  
```
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: A**  
### **Explanation:**  
Constructors are called **from the base class to the derived class** during object creation.

---

### **Question 2: Method Overriding and Dynamic Dispatch**  
What will be the output?  
```java
class Parent {
    void show() {
        System.out.println("Parent's show()");
    }
}

class Child extends Parent {
    void show() {
        System.out.println("Child's show()");
    }
}

public class Test {
    public static void main(String[] args) {
        Parent obj = new Child();
        obj.show();
    }
}
```
**A.** `Parent's show()`  
**B.** `Child's show()`  
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: B**  
### **Explanation:**  
Even though `obj` is of type `Parent`, **method overriding** allows `Child`'s `show()` to be executed due to **runtime polymorphism**.

---

### **Question 3: Static Method Hiding**  
What will be the output?  
```java
class Parent {
    static void show() {
        System.out.println("Static method in Parent");
    }
}

class Child extends Parent {
    static void show() {
        System.out.println("Static method in Child");
    }
}

public class Test {
    public static void main(String[] args) {
        Parent obj = new Child();
        obj.show();
    }
}
```
**A.** `Static method in Parent`  
**B.** `Static method in Child`  
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: A**  
### **Explanation:**  
Static methods **are not overridden** but **hidden**, and method resolution is done based on **reference type** (`Parent`).

---

### **Question 4: Final Methods and Overriding**  
What will be the output?  
```java
class Parent {
    final void show() {
        System.out.println("Final method in Parent");
    }
}

class Child extends Parent {
    // void show() {   // Uncommenting this will cause a compilation error
    //     System.out.println("Child method");
    // }
}

public class Test {
    public static void main(String[] args) {
        Parent obj = new Child();
        obj.show();
    }
}
```
**A.** `Final method in Parent`  
**B.** `Child method`  
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: A**  
### **Explanation:**  
A **final method cannot be overridden**. Even if `Child` tries to override `show()`, it will cause a **compilation error**.

---

### **Question 5: Instance Block Execution**  
What will be the output?  
```java
class A {
    {
        System.out.println("Instance Block of A");
    }

    A() {
        System.out.println("Constructor of A");
    }
}

public class Test {
    public static void main(String[] args) {
        A obj1 = new A();
        A obj2 = new A();
    }
}
```
**A.**  
```
Instance Block of A  
Constructor of A  
Instance Block of A  
Constructor of A  
```
**B.**  
```
Constructor of A  
Instance Block of A  
Constructor of A  
Instance Block of A  
```
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: A**  
### **Explanation:**  
- **Instance blocks execute before constructors**.
- They run **every time** an object is created.

---

### **Question 6: Abstract Class and Method Implementation**  
What will be the output?  
```java
abstract class Base {
    abstract void show();

    void display() {
        System.out.println("Concrete Method in Base");
    }
}

class Derived extends Base {
    void show() {
        System.out.println("Implemented Abstract Method in Derived");
    }
}

public class Test {
    public static void main(String[] args) {
        Base obj = new Derived();
        obj.show();
        obj.display();
    }
}
```
**A.**  
```
Implemented Abstract Method in Derived  
Concrete Method in Base  
```
**B.**  
```
Concrete Method in Base  
Implemented Abstract Method in Derived  
```
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: A**  
### **Explanation:**  
- `show()` is an **abstract method**, so it must be implemented in `Derived`.  
- `display()` is already **concrete** in `Base`, so `Derived` inherits it.

---

### **Question 7: Constructor Chaining Using `this()`**  
What will be the output?  
```java
class Demo {
    Demo() {
        this(10);
        System.out.println("Default Constructor");
    }

    Demo(int x) {
        System.out.println("Parameterized Constructor: " + x);
    }
}

public class Test {
    public static void main(String[] args) {
        Demo obj = new Demo();
    }
}
```
**A.**  
```
Default Constructor  
Parameterized Constructor: 10  
```
**B.**  
```
Parameterized Constructor: 10  
Default Constructor  
```
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: B**  
### **Explanation:**  
- `this(10)` calls the parameterized constructor first.  
- After that, the **default constructor** executes.

---

### **Question 8: Exception Handling in Method Overriding**  
What will be the output?  
```java
class Parent {
    void show() throws Exception {
        System.out.println("Parent's show()");
    }
}

class Child extends Parent {
    void show() {
        System.out.println("Child's show()");
    }
}

public class Test {
    public static void main(String[] args) {
        Parent obj = new Child();
        obj.show();
    }
}
```
**A.** `Parent's show()`  
**B.** `Child's show()`  
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: B**  
### **Explanation:**  
- **Rule:** A subclass **cannot declare a broader exception** than its superclass.
- Since `Child` removes the `throws Exception`, it's valid.



Here are the same Java output-based questions in **objective (MCQ) format** with multiple choices:  

---

---

### **Question 2: Method Overriding and Dynamic Method Dispatch**  
What will be the output?  
```java
class A {
    void display() {
        System.out.println("A's display");
    }
}

class B extends A {
    void display() {
        System.out.println("B's display");
    }
}

public class Test {
    public static void main(String[] args) {
        A obj = new B();
        obj.display();
    }
}
```
**A.** `A's display`  
**B.** `B's display`  
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: B**  

---

### **Question 4: Order of Execution (Static Block, Instance Block, Constructor)**  
What will be the output?  
```java
class A {
    static {
        System.out.println("Static Block of A");
    }

    {
        System.out.println("Instance Block of A");
    }

    A() {
        System.out.println("Constructor of A");
    }
}

public class Test {
    public static void main(String[] args) {
        A obj1 = new A();
        A obj2 = new A();
    }
}
```
**A.**  
```
Static Block of A  
Instance Block of A  
Constructor of A  
Instance Block of A  
Constructor of A  
```
**B.**  
```
Instance Block of A  
Constructor of A  
Static Block of A  
Instance Block of A  
Constructor of A  
```
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: A**  

---



---

### **Question 6: Constructor Overloading and Default Values**  
What will be the output?  
```java
class Demo {
    int x;

    Demo() {
        this(10);
        System.out.println("Default Constructor");
    }

    Demo(int x) {
        this.x = x;
        System.out.println("Parameterized Constructor: " + x);
    }
}

public class Test {
    public static void main(String[] args) {
        Demo obj = new Demo();
    }
}
```
**A.**  
```
Default Constructor  
Parameterized Constructor: 10  
```
**B.**  
```
Parameterized Constructor: 10  
Default Constructor  
```
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: B**  

---

### **Question 7: Abstract Class and Method Implementation**  
What will be the output?  
```java
abstract class Base {
    abstract void show();

    void display() {
        System.out.println("Concrete Method in Base");
    }
}

class Derived extends Base {
    void show() {
        System.out.println("Implemented Abstract Method in Derived");
    }
}

public class Test {
    public static void main(String[] args) {
        Base obj = new Derived();
        obj.show();
        obj.display();
    }
}
```
**A.**  
```
Implemented Abstract Method in Derived  
Concrete Method in Base  
```
**B.**  
```
Concrete Method in Base  
Implemented Abstract Method in Derived  
```
**C.** Compilation Error  
**D.** Runtime Error  

✅ **Correct Answer: A**  

---

### **1. Which of the following is NOT a type of database model?**  
- a) Hierarchical Model  
- b) Relational Model  
- c) Network Model  
- d) Linear Model  

**Answer:** `d) Linear Model`  

---

### **2. What does ACID stand for in the context of databases?**  
- a) Atomicity, Consistency, Isolation, Durability  
- b) Accuracy, Consistency, Integrity, Dependency  
- c) Authorization, Classification, Integrity, Durability  
- d) Availability, Concurrency, Isolation, Data Integrity  

**Answer:** `a) Atomicity, Consistency, Isolation, Durability`  

---

### **3. In an RDBMS, which key uniquely identifies each row in a table?**  
- a) Foreign Key  
- b) Candidate Key  
- c) Primary Key  
- d) Super Key  

**Answer:** `c) Primary Key`  

---

### **4. Which SQL command is used to remove all records from a table without deleting the structure?**  
- a) `DELETE`  
- b) `DROP`  
- c) `TRUNCATE`  
- d) `REMOVE`  

**Answer:** `c) TRUNCATE`  

---

### **5. What is the role of a foreign key in a relational database?**  
- a) It uniquely identifies a record in a table  
- b) It ensures data integrity between two tables  
- c) It is used to store large data objects  
- d) It speeds up query performance  

**Answer:** `b) It ensures data integrity between two tables`  

---

### **6. Which normal form eliminates partial dependencies in a relational database?**  
- a) First Normal Form (1NF)  
- b) Second Normal Form (2NF)  
- c) Third Normal Form (3NF)  
- d) Boyce-Codd Normal Form (BCNF)  

**Answer:** `b) Second Normal Form (2NF)`  

---

### **7. What is the main advantage of using an index in a database?**  
- a) It increases storage requirements  
- b) It speeds up data retrieval  
- c) It prevents duplicate data  
- d) It enforces constraints  

**Answer:** `b) It speeds up data retrieval`  

---

### **8. Which SQL clause is used to filter results based on a condition?**  
- a) `ORDER BY`  
- b) `HAVING`  
- c) `WHERE`  
- d) `GROUP BY`  

**Answer:** `c) WHERE`  

---

### **9. What type of JOIN returns all records from both tables when there is a match, and NULLs for unmatched records?**  
- a) INNER JOIN  
- b) LEFT JOIN  
- c) RIGHT JOIN  
- d) FULL OUTER JOIN  

**Answer:** `d) FULL OUTER JOIN`  

---

### **10. In a relational database, what does a "transaction" refer to?**  
- a) A collection of SQL queries  
- b) A sequence of operations performed as a single logical unit of work  
- c) A backup operation on the database  
- d) A stored procedure execution  

**Answer:** `b) A sequence of operations performed as a single logical unit of work`  

---


---

### **Dummy Table: `employees`**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50),
    salary INT
);

INSERT INTO employees (id, name, department, salary) VALUES
(1, 'Alice', 'HR', 60000),
(2, 'Bob', 'IT', 75000),
(3, 'Charlie', 'Finance', 50000),
(4, 'David', 'IT', 80000),
(5, 'Eve', 'HR', 62000);
```

---

### **1. I want to retrieve the names of all employees who work in the 'IT' department. Which query should I use?**
- a) ```SELECT name FROM employees WHERE department = 'IT';```  
- b) ```SELECT department FROM employees WHERE name = 'IT';```  
- c) ```SELECT name FROM employees WHERE department == 'IT';```  
- d) ```SELECT * FROM employees WHERE department = 'IT';```  

**Answer:** `a) SELECT name FROM employees WHERE department = 'IT';`  

---

### **2. I need to find the employees whose salary is exactly 75000. Which query is correct?**
- a) ```SELECT name FROM employees WHERE salary == 75000;```  
- b) ```SELECT name FROM employees WHERE salary = 75000;```  
- c) ```SELECT salary FROM employees WHERE name = 75000;```  
- d) ```SELECT * FROM employees WHERE salary = '75000';```  

**Answer:** `b) SELECT name FROM employees WHERE salary = 75000;`  

---

### **3. I want to find the details of employees who have a salary greater than 60,000. Which query is valid?**
- a) ```SELECT name, salary FROM employees WHERE salary > 60000;```  
- b) ```SELECT name, salary FROM employees WHERE salary >= 60000;```  
- c) ```SELECT name, salary FROM employees WHERE salary => 60000;```  
- d) ```SELECT name, salary FROM employees WHERE salary => '60000';```  

**Answer:** `a) SELECT name, salary FROM employees WHERE salary > 60000;`  

---

### **4. I want to find employees who are not in the HR department. Which query should I use?**
- a) ```SELECT name FROM employees WHERE department != 'HR';```  
- b) ```SELECT name FROM employees WHERE department <> 'HR';```  
- c) ```SELECT name FROM employees WHERE department NOT 'HR';```  
- d) ```SELECT name FROM employees WHERE department != 'HR' OR department = NULL;```  

**Answer:** `a) SELECT name FROM employees WHERE department != 'HR';` and `b) SELECT name FROM employees WHERE department <> 'HR';`  

---

### **5. I want to retrieve the names of employees who earn between 50,000 and 75,000. Which query should I use?**
- a) ```SELECT name FROM employees WHERE salary >= 50000 AND salary <= 75000;```  
- b) ```SELECT name FROM employees WHERE salary BETWEEN 50000 AND 75000;```  
- c) ```SELECT name FROM employees WHERE salary > 50000 AND salary < 75000;```  
- d) ```SELECT name FROM employees WHERE salary IN (50000, 75000);```  

**Answer:** `a) SELECT name FROM employees WHERE salary >= 50000 AND salary <= 75000;` and `b) SELECT name FROM employees WHERE salary BETWEEN 50000 AND 75000;`  

---

### **6. I need to find employees whose names start with 'A'. Which query should I use?**
- a) ```SELECT name FROM employees WHERE name LIKE 'A%';```  
- b) ```SELECT name FROM employees WHERE name = 'A%';```  
- c) ```SELECT name FROM employees WHERE name LIKE '%A';```  
- d) ```SELECT name FROM employees WHERE name == 'A%';```  

**Answer:** `a) SELECT name FROM employees WHERE name LIKE 'A%';`  

---

### **7. I want to find employees whose names end with 'e'. Which query should I use?**
- a) ```SELECT name FROM employees WHERE name LIKE '%e';```  
- b) ```SELECT name FROM employees WHERE name LIKE 'e%';```  
- c) ```SELECT name FROM employees WHERE name LIKE 'e';```  
- d) ```SELECT name FROM employees WHERE name IN ('%e');```  

**Answer:** `a) SELECT name FROM employees WHERE name LIKE '%e';`  

---

### **8. I want to find all employees who are either in the 'IT' or 'Finance' department. Which query should I use?**
- a) ```SELECT name FROM employees WHERE department = 'IT' OR department = 'Finance';```  
- b) ```SELECT name FROM employees WHERE department IN ('IT', 'Finance');```  
- c) ```SELECT name FROM employees WHERE department LIKE 'IT' AND 'Finance';```  
- d) ```SELECT name FROM employees WHERE department == 'IT' OR 'Finance';```  

**Answer:** `a) SELECT name FROM employees WHERE department = 'IT' OR department = 'Finance';` and `b) SELECT name FROM employees WHERE department IN ('IT', 'Finance');`  

---

### **9. I need to find employees whose salary is NOT 75000. Which query should I use?**
- a) ```SELECT name FROM employees WHERE salary != 75000;```  
- b) ```SELECT name FROM employees WHERE salary <> 75000;```  
- c) ```SELECT name FROM employees WHERE salary NOT 75000;```  
- d) ```SELECT name FROM employees WHERE salary != '75000';```  

**Answer:** `a) SELECT name FROM employees WHERE salary != 75000;` and `b) SELECT name FROM employees WHERE salary <> 75000;`  

---

### **10. I want to retrieve the details of employees whose name contains 'a'. Which query should I use?**
- a) ```SELECT * FROM employees WHERE name LIKE '%a%';```  
- b) ```SELECT * FROM employees WHERE name LIKE 'a%';```  
- c) ```SELECT * FROM employees WHERE name LIKE '%a';```  
- d) ```SELECT * FROM employees WHERE name == '%a%';```  

**Answer:** `a) SELECT * FROM employees WHERE name LIKE '%a%';`  

---

---

### **Dummy Table: `employees`**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50),
    salary INT
);

INSERT INTO employees (id, name, department, salary) VALUES
(1, 'Alice', 'HR', 60000),
(2, 'Bob', 'IT', 75000),
(3, 'Charlie', 'Finance', 50000),
(4, 'David', 'IT', 80000),
(5, 'Eve', 'HR', 62000);
```

---

### **1. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE department = 'HR';
```
What will be the output of the above query?  

- a) `Alice`  
- b) `Eve`  
- c) `Alice, Eve`  
- d) `No output`  

**Answer:** `c) Alice, Eve`  

---

### **2. Consider the following SQL query:**
```sql
SELECT name, salary FROM employees WHERE salary > 70000;
```
Which of the following will be returned?  

- a) `Bob, 75000`  
- b) `David, 80000`  
- c) `Bob, 75000 and David, 80000`  
- d) `Charlie, 50000`  

**Answer:** `c) Bob, 75000 and David, 80000`  

---

### **3. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE salary < 60000;
```
What will be the output?  

- a) `Charlie`  
- b) `Alice, Charlie`  
- c) `David, Bob`  
- d) `No output`  

**Answer:** `a) Charlie`  

---

### **4. Consider the following SQL query:**
```sql
SELECT * FROM employees WHERE name = 'David';
```
What will be the output?  

- a) All details of `David`  
- b) Only `David's` name  
- c) The department and salary of `David`  
- d) No output  

**Answer:** `a) All details of David`  

---

### **5. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE department != 'IT';
```
Which names will be included in the result?  

- a) `Alice, Charlie, Eve`  
- b) `Bob, David`  
- c) `Alice, Bob`  
- d) `Charlie, Eve`  

**Answer:** `a) Alice, Charlie, Eve`  

---

### **6. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE salary >= 62000;
```
Which names will be included in the result?  

- a) `Alice, Eve, Bob, David`  
- b) `Charlie`  
- c) `Bob, David`  
- d) `Eve`  

**Answer:** `a) Alice, Eve, Bob, David`  

---

### **7. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE name LIKE '%e';
```
What will be the output?  

- a) `Alice, Eve`  
- b) `Charlie, Eve`  
- c) `Bob, Charlie`  
- d) `David, Eve`  

**Answer:** `b) Charlie, Eve`  

---

### **8. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE department = 'IT' AND salary > 75000;
```
Which of the following names will be returned?  

- a) `Bob`  
- b) `David`  
- c) `Bob, David`  
- d) `No output`  

**Answer:** `b) David`  

---

### **9. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE salary BETWEEN 50000 AND 60000;
```
Which names will be included in the result?  

- a) `Alice, Eve`  
- b) `Charlie, Alice`  
- c) `Charlie`  
- d) `Charlie, Eve`  

**Answer:** `c) Charlie`  

---

### **10. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE department = 'Finance' OR salary > 70000;
```
Which names will be included in the result?  

- a) `Charlie, Bob, David`  
- b) `Alice, Bob, Eve`  
- c) `Charlie, Alice, David`  
- d) `Bob, David, Eve`  

**Answer:** `a) Charlie, Bob, David`  

---
---

### **Dummy Table: `employees`**
```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50),
    salary INT
);

INSERT INTO employees (id, name, department, salary) VALUES
(1, 'Alice', 'HR', 60000),
(2, 'Bob', 'IT', 75000),
(3, 'Charlie', 'Finance', 50000),
(4, 'David', 'IT', 80000),
(5, 'Eve', 'HR', 62000);
```

---

### **1. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE department = 'HR';
```
What will be the output of the above query?  

- a) `Alice`  
- b) `Eve`  
- c) `Alice, Eve`  
- d) `No output`  

**Answer:** `c) Alice, Eve`  

---

### **2. Consider the following SQL query:**
```sql
SELECT name, salary FROM employees WHERE salary > 70000;
```
Which of the following will be returned?  

- a) `Bob, 75000`  
- b) `David, 80000`  
- c) `Bob, 75000 and David, 80000`  
- d) `Charlie, 50000`  

**Answer:** `c) Bob, 75000 and David, 80000`  

---

### **3. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE salary < 60000;
```
What will be the output?  

- a) `Charlie`  
- b) `Alice, Charlie`  
- c) `David, Bob`  
- d) `No output`  

**Answer:** `a) Charlie`  

---

### **4. Consider the following SQL query:**
```sql
SELECT * FROM employees WHERE name = 'David';
```
What will be the output?  

- a) All details of `David`  
- b) Only `David's` name  
- c) The department and salary of `David`  
- d) No output  

**Answer:** `a) All details of David`  

---

### **5. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE department != 'IT';
```
Which names will be included in the result?  

- a) `Alice, Charlie, Eve`  
- b) `Bob, David`  
- c) `Alice, Bob`  
- d) `Charlie, Eve`  

**Answer:** `a) Alice, Charlie, Eve`  

---

### **6. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE salary >= 62000;
```
Which names will be included in the result?  

- a) `Alice, Eve, Bob, David`  
- b) `Charlie`  
- c) `Bob, David`  
- d) `Eve`  

**Answer:** `a) Alice, Eve, Bob, David`  

---

### **7. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE name LIKE '%e';
```
What will be the output?  

- a) `Alice, Eve`  
- b) `Charlie, Eve`  
- c) `Bob, Charlie`  
- d) `David, Eve`  

**Answer:** `b) Charlie, Eve`  

---

### **8. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE department = 'IT' AND salary > 75000;
```
Which of the following names will be returned?  

- a) `Bob`  
- b) `David`  
- c) `Bob, David`  
- d) `No output`  

**Answer:** `b) David`  

---

### **9. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE salary BETWEEN 50000 AND 60000;
```
Which names will be included in the result?  

- a) `Alice, Eve`  
- b) `Charlie, Alice`  
- c) `Charlie`  
- d) `Charlie, Eve`  

**Answer:** `c) Charlie`  

---

### **10. Consider the following SQL query:**
```sql
SELECT name FROM employees WHERE department = 'Finance' OR salary > 70000;
```
Which names will be included in the result?  

- a) `Charlie, Bob, David`  
- b) `Alice, Bob, Eve`  
- c) `Charlie, Alice, David`  
- d) `Bob, David, Eve`  

**Answer:** `a) Charlie, Bob, David`  

---
