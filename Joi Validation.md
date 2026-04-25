# 📊 Joi Validation – Notes

## 🚀 What is Joi?

**Joi** is a powerful validation library for Node.js used to validate incoming request data.

👉 It ensures:

* Correct data format
* Required fields are present
* Invalid data is rejected

---

## 💡 Simple Definition

> Joi is used to validate request data before processing it in backend APIs.

---

## ⚙️ Installation

```bash id="z3m2qa"
npm install joi
```

---

## 🔧 Basic Usage

```js id="c5t8kp"
const Joi = require("joi");

const schema = Joi.object({
  name: Joi.string().required(),
  email: Joi.string().email().required(),
  age: Joi.number().min(18)
});

const data = {
  name: "Akanksha",
  email: "test@gmail.com",
  age: 22
};

const { error, value } = schema.validate(data);

if (error) {
  console.log(error.message);
} else {
  console.log("Valid data ✅");
}
```

---

## ❌ Example of Invalid Data

```js id="m6q1sv"
const data = {
  name: "Akanksha",
  email: "wrong-email",
  age: 15
};
```

👉 Output:

```id="xqk8zu"
"email must be a valid email"
```

---

## 🧠 Common Joi Validations

### 🔹 String

```js id="8y4n1j"
Joi.string()
```

---

### 🔹 Required Field

```js id="m2p4as"
Joi.string().required()
```

---

### 🔹 Email

```js id="j2k5vd"
Joi.string().email()
```

---

### 🔹 Number

```js id="h4p9rx"
Joi.number().min(1)
```

---

### 🔹 Boolean

```js id="a1v6nd"
Joi.boolean()
```

---

### 🔹 Array

```js id="t9b7kp"
Joi.array().items(Joi.string())
```

---

### 🔹 Password (min length)

```js id="n8c3dz"
Joi.string().min(6)
```

---

## 🔥 Real Backend Example (Your Use Case)

### Allowance Validation Schema

```js id="k3s9vf"
const Joi = require("joi");

const allowanceSchema = Joi.object({
  employeeId: Joi.string().required(),
  category: Joi.string().required(),
  amount: Joi.number().required(),
  description: Joi.string().optional(),
  month: Joi.number().min(1).max(12).required(),
  year: Joi.number().required(),
  approvedBy: Joi.string().optional()
});
```

---

### Use in Controller

```js id="g5m2lp"
const { error } = allowanceSchema.validate(req.body);

if (error) {
  return res.status(400).json({
    message: error.message
  });
}
```

---

## 🔄 Validation Flow

1. Client sends request
2. Joi validates data
3. ❌ If invalid → return error
4. ✅ If valid → continue logic

---

## 🔧 Custom Error Messages

```js id="r7q4bn"
const schema = Joi.object({
  name: Joi.string().required().messages({
    "string.empty": "Name is required"
  })
});
```

---

## 🔥 Why Use Joi?

### ✅ Data Safety

Prevents invalid data from entering DB

### ✅ Clean Code

Centralized validation logic

### ✅ Better UX

Clear error messages

---

## ⚠️ Without Joi

* Invalid data stored in database
* More bugs
* Hard to debug

---

## 💡 Summary

* Validates request body
* Prevents bad data
* Easy to use
* Essential for backend

---
