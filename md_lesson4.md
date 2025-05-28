# 📘 MongoDB Data Modeling 

---

## 📌 What is Data Modeling?

In MongoDB, data modeling is about:

- How data is **stored**
- How different **entities are related**
- How your **application uses** this data

### While designing a data model, ask:
- What does my app do?
- What kind of data will be stored?
- What data types should be used?
- How will users access the data?
- What data is most valuable?

---

## 🎯 Purpose of a Good Data Model

- Faster **queries**
- Lower **CPU and memory usage**
- **Reduced costs**
- Easier to **maintain**
- **Scalable** structure

> 📘 Rule of Thumb: **Data that is accessed together should be stored together.**

---

## 🆚 Traditional Relational vs Document Model

| Feature     | Relational (SQL)  | Document (MongoDB)     |
|-------------|-------------------|-------------------------|
| Structure   | Tables, rows      | JSON-like documents     |
| Schema      | Fixed             | Flexible                |
| Joins       | Required          | Optional                |
| Scaling     | Harder (vertical) | Easier (horizontal)     |
| Best for    | Structured data   | Dynamic, nested data    |

---

## ✅ Why Use MongoDB's Document Model?

- **Flexible schema**: Different documents can have different fields (called *polymorphism*)
- **Schema validation** available if needed
- **Embedded documents** allow complex relationships
- **Fewer joins**, faster reads
- Works well with **real-time**, **fast-evolving** applications

---

## 🔗 Types of Relationships in MongoDB

1. **One-to-One**
2. **One-to-Many**
3. **Many-to-Many**

---

## 🧩 Modeling Relationships

### 1. Embedding (Nested Documents)

Put related data inside a single document.

✅ Good for:
- One-to-few relationships
- Data used together

```json
{
  "name": "Blog Post",
  "comments": [
    { "text": "Nice!" },
    { "text": "Great post!" }
  ]
}
```
### ✅ Pros of Embedding

- One query to get all data  
- Fast reads  
- One write to update  

### ⚠️ Cons of Embedding

- May lead to **large documents**  
- Max document size = **16MB**  
- May impact performance if not optimized  

---

## 2. Referencing (Normalization)

Store related data in a separate document and use `_id` as a reference.

### ✅ Good for:

- **Many-to-many** relationships  
- **Reusable** data  

```json
{
  "name": "Post",
  "author_id": ObjectId("...")
}
```
### ✅ Pros of Referencing

- Avoids **duplication**  
- Keeps documents **small**  

### ⚠️ Cons of Referencing

- Needs **multiple queries**  
- Slightly **slower reads**  

---

## ❗ Common Problems in Bad MongoDB Models

Bad modeling = **poor performance**:

- **Slow query times**  
- **High CPU/RAM usage**  
- **Large storage requirements**  
- **Non-scalable design**  

---

## ❌ Schema Anti-Patterns to Avoid

- **Massive arrays** in a single document  
- **Too many collections**  
- **Bloated documents** (too much embedded data)  
- **Unnecessary indexes**  
- **Queries with no indexes**  
- Storing related data in **different collections**  

---

## 🛠 MongoDB Tools to Help

### 1. Data Explorer

- See collections and indexes  
- Drop **unused indexes**  

### 2. Performance Advisor (Available in M10+ Tier)

- Recommends **new indexes**  
- Detects **unused/redundant indexes**  
- Flags **schema issues**  

---

## 🔁 Summary Tips

- **Store together what’s used together**  
- Use **embedding** for simple and fast access  
- Use **referencing** when data is **reused** or grows **large**  
- Avoid anti-patterns like **unbounded documents** or **too many arrays**
