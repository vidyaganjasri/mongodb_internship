# 🌐 Connecting to MongoDB Atlas Cluster Using Node.js

## 📦 What Are Drivers?

- Drivers help your app talk to MongoDB.
- The Node.js driver works with the built-in **BSON** package.
- It helps connect safely and follow good coding practices.
- You can run all database operations through it.
- Makes it easier to upgrade your app.

---

## 🛠️ Steps to Connect

### 1. Install the Official MongoDB Driver

Use this command:
```
npm install mongodb
```
---

### 2. Create a Single MongoClient

```js
const { MongoClient } = require('mongodb');

// Paste your connection string from MongoDB Atlas here
const uri = "mongodb+srv://<username>:<password>@<cluster-url>/";

const client = new MongoClient(uri);
```
##  Connect and Use It
```js
async function connect() {
  await client.connect();
  console.log("✅ Connected to MongoDB!");
  await client.close();
}

connect();
```
## 🔑 Where to Find the Connection String
Go to your MongoDB Atlas dashboard

Select your cluster

Click Connect

Choose the driver option (Node.js)

Copy the connection string

## 🧰 Troubleshooting
🔒 Network Access Error
Can’t connect to MongoDB?

Fix: Go to Atlas → Network Access → Add your IP address

❌ Connection Issues
Using the wrong connection string?

Fix: Make sure the string is copied from the Atlas dashboard

🔐 Authentication Error
Wrong password or username?

Fix: Update your connection string with the correct password

✅ Now you're ready to connect your Node.js app with MongoDB Atlas!
