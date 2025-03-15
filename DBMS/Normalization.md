# **Database Normalization from Scratch**

## **1. Introduction to Normalization**
### **What is Normalization?**
Normalization is the process of organizing data in a relational database to minimize redundancy and improve data integrity. It involves decomposing a larger table into smaller, well-structured tables while preserving relationships among them.

### **Why is Normalization Needed?**
- **Reduces Data Redundancy** (avoids duplicate data)
- **Prevents Update Anomalies** (ensures consistency during updates)
- **Prevents Insert and Delete Anomalies** (allows better data management)
- **Improves Query Efficiency** (optimized storage and indexing)

---

## **2. Problem Without Normalization (Redundancy Issue)**
### **📝 Unnormalized Table (Before Normalization)**
| Order_ID | Customer_Name | Customer_Email     | Product  | Price  | Quantity |
|----------|--------------|--------------------|----------|--------|----------|
| 1001     | Alice        | alice@email.com   | Laptop   | 50000  | 1        |
| 1002     | Bob          | bob@email.com     | Phone    | 20000  | 2        |
| 1003     | Alice        | alice@email.com   | Keyboard | 2000   | 1        |

### **❌ Problems in This Table**
- **Data Redundancy** → "Alice" and her email appear twice (unnecessary duplication).
- **Update Anomaly** → If Alice changes her email, we must update it everywhere.
- **Insert Anomaly** → If a new customer hasn't placed an order yet, we can't store their details.
- **Delete Anomaly** → If all orders of a customer are deleted, their information is lost.

---

## **3. Normal Forms (NF) with Examples**
### **1NF (First Normal Form) – Atomicity**
**Rule:**
- Each column should have **atomic (indivisible) values**.
- No **repeating groups** or multiple values in a single column.

#### **Example: Unnormalized Table**
| Student_ID | Name  | Courses         |
|------------|------|----------------|
| 101        | Alice | Math, Physics  |
| 102        | Bob   | Chemistry      |

#### **Issue:**
- "Courses" column contains multiple values (violates atomicity).

#### **1NF Table (After Fixing Atomicity)**
| Student_ID | Name  | Course    |
|------------|------|---------|
| 101        | Alice | Math    |
| 101        | Alice | Physics |
| 102        | Bob   | Chemistry |

#### **Advantages:**
✅ Eliminates duplicate data within columns.
✅ Supports better indexing and searching.

#### **Disadvantages:**
❌ Data redundancy increases (e.g., "Alice" appears twice).

---

### **2NF (Second Normal Form) – Removing Partial Dependencies**
**Rule:**
- **Must be in 1NF**.
- **No Partial Dependencies** (every non-key attribute must depend on the entire primary key, not just part of it).

#### **Example: 1NF Table (Before 2NF)**
| Student_ID | Name  | Course    | Teacher |
|------------|------|---------|---------|
| 101        | Alice | Math    | Mr. A   |
| 101        | Alice | Physics | Mr. B   |
| 102        | Bob   | Chemistry | Mr. C |

#### **Issue:**
- The **primary key** `{Student_ID, Course}`.
- "Name" depends **only on Student_ID**, not on Course.

#### **2NF Tables (Splitting into Two Tables)**
**Student Table:**
| Student_ID | Name  |
|------------|------|
| 101        | Alice |
| 102        | Bob   |

**Enrollment Table:**
| Student_ID | Course    | Teacher |
|------------|---------|---------|
| 101        | Math    | Mr. A   |
| 101        | Physics | Mr. B   |
| 102        | Chemistry | Mr. C |

#### **Advantages:**
✅ Removes partial dependencies.
✅ Ensures better consistency.

#### **Disadvantages:**
❌ Increases number of tables.
❌ Queries require more joins.

---

### **3NF (Third Normal Form) – Removing Transitive Dependencies**
**Rule:**
- **Must be in 2NF**.
- **No Transitive Dependencies** (no non-key column should depend on another non-key column).

#### **Example: 2NF Table (Before 3NF)**
| Student_ID | Course    | Teacher | Department |
|------------|---------|---------|------------|
| 101        | Math    | Mr. A   | Science    |
| 101        | Physics | Mr. B   | Science    |
| 102        | Chemistry | Mr. C | Science    |

#### **Issue:**
- "Department" depends on "Teacher", not on "Student_ID or Course".

#### **3NF Tables (Splitting Further)**
**Course Table:**
| Course    | Teacher |
|---------|---------|
| Math    | Mr. A   |
| Physics | Mr. B   |
| Chemistry | Mr. C |

**Teacher Table:**
| Teacher | Department |
|---------|------------|
| Mr. A   | Science    |
| Mr. B   | Science    |
| Mr. C   | Science    |

#### **Advantages:**
✅ Eliminates redundant data.
✅ No unnecessary dependencies.

#### **Disadvantages:**
❌ Further increases table count.

---

### **BCNF (Boyce-Codd Normal Form) – Stronger 3NF**
**Rule:**
- **Must be in 3NF**.
- **Every determinant must be a candidate key**.

#### **Example: 3NF Table (Before BCNF)**
| Course    | Teacher | Room |
|---------|---------|------|
| Math    | Mr. A   | R101 |
| Physics | Mr. B   | R102 |
| Chemistry | Mr. C | R103 |
| Math    | Mr. D   | R104 |

#### **Issue:**
- A **course can be taught by multiple teachers**, so "Course" is **not a candidate key**.

#### **BCNF Tables (Splitting Further)**
**Course_Teacher Table:**
| Course    | Teacher |
|---------|---------|
| Math    | Mr. A   |
| Math    | Mr. D   |
| Physics | Mr. B   |
| Chemistry | Mr. C |

**Room Allocation Table:**
| Teacher | Room |
|---------|------|
| Mr. A   | R101 |
| Mr. D   | R104 |
| Mr. B   | R102 |
| Mr. C   | R103 |

---

## **4. Summary of Normal Forms**
| Normal Form | Purpose |
|------------|---------|
| **1NF**    | Removes **multi-valued** columns (atomicity) |
| **2NF**    | Removes **partial dependencies** |
| **3NF**    | Removes **transitive dependencies** |
| **BCNF**   | Ensures **every determinant is a candidate key** |

---
**End of Document.** 🚀