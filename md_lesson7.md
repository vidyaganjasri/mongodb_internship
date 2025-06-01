## 📥 1. Inserting Documents into a Collection

### 🔹 Insert One Document

```js
db.<collection>.insertOne(<document>)
```
✅ Example:

```js
db.grades.insertOne({
  student_id: 1001,
  grade: "A",
  subject: "Math"
})
```
If the grades collection doesn’t exist, MongoDB will automatically create it.

🔹 Insert Multiple Documents
```js

db.<collection>.insertMany([
  <document1>,
  <document2>,
  <document3>
])
```
✅ Example:

```js

db.students.insertMany([
  { name: "Alice", age: 21 },
  { name: "Bob", age: 22 },
  { name: "Charlie", age: 20 }
])
```
🔎 2. Finding Documents
🔹 Find All Documents
```js

db.<collection>.find()
```
```js

db.zips.find()
```
🔹 Find Specific Document(s)
➤ Equality Match
```js

db.zips.find({ state: "AZ" })
```
➤ $in Operator
```js

db.zips.find({ city: { $in: ["PHOENIX", "CHICAGO"] } })
```
⚖️ 3. Comparison Operators
Operator	Meaning

$gt	Greater than
$lt	Less than
$gte	Greater than or equal
$lte	Less than or equal

🔹 Syntax
```js

<field>: { <operator>: <value> }
```
✅ Example:

```js

db.sales.find({ "items.price": { $gt: 50 } })
```
📚 4. Querying Array Elements
🔹 $elemMatch for Arrays
```js

db.accounts.find({
  products: {
    $elemMatch: { $eq: "InvestmentStock" }
  }
})
```
Ensures products is an array containing "InvestmentStock".

⚙️ 5. Logical Operators
🔹 $and Operator
```js

db.users.find({
  $and: [
    { age: { $gte: 18 } },
    { status: "active" }
  ]
})
```
Or simply:

```js

db.users.find({ age: { $gte: 18 }, status: "active" })
```
🔹 $or Operator
```js
db.users.find({
  $or: [
    { age: { $lt: 18 } },
    { status: "inactive" }
  ]
})
```
⚠️ Rule for Repeating Operators
✅ Valid:

```js

db.collection.find({
  $and: [
    { $or: [...] },
    { $or: [...] }
  ]
})
```
❌ Invalid:

```js
db.collection.find({
  $or: [...],
  $or: [...]
})
```

