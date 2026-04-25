# 📊 Morgan (HTTP Logger)

## 🚀 What is Morgan?

**Morgan** is a middleware in Express.js used to log HTTP requests in the terminal.

👉 It helps developers:

* Track API calls
* Debug errors
* Monitor performance

---

## 💡 Simple Definition

> Morgan logs every request made to your server, including method, URL, status code, and response time.

---

## ⚙️ Installation

```bash
npm install morgan
```

---

## 🔧 Usage

```js
const express = require("express");
const morgan = require("morgan");

const app = express();

app.use(morgan("dev"));
```

---

## 🔍 Example Log Output

```bash
GET /api/users 200 15ms
```

### 🧠 Meaning:

* **GET** → Request method
* **/api/users** → API endpoint
* **200** → Status code (Success)
* **15ms** → Response time

---

## 🧠 Different Log Formats

### 🔹 dev (Recommended)

```js
app.use(morgan("dev"));
```

👉 Output:

```
GET /api/users 200 10ms
```

---

### 🔹 combined

```js
app.use(morgan("combined"));
```

👉 Output:

```
127.0.0.1 - - [date] "GET /api/users HTTP/1.1" 200
```

---

### 🔹 tiny

```js
app.use(morgan("tiny"));
```

👉 Minimal log info

---

## 🔥 Why Use Morgan?

### ✅ Debugging

* Check if API is hit
* Identify failing routes

### ✅ Monitoring

* Track response time
* Observe traffic

---

## ❌ Without Morgan

* No visibility of API calls
* Hard to debug issues

---

## ✅ With Morgan

* Clear request logs
* Easy debugging

---

## 🎯 Real Example

When API fails:

```
POST /api/payroll/allowance 500 8ms
```

👉 Meaning:

* API endpoint failed
* Status code = 500 (Server error)

---

## 🧠 Best Practice

Use Morgan only in development mode:

```js
if (process.env.NODE_ENV === "development") {
  app.use(morgan("dev"));
}
```


