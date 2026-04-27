# 📁 What is the migrations/ folder?

- 👉 It contains files that manage changes to your database structure over time

- 💡 In simple words:
   - Migrations = version control for your database
     
--- 
##  🧠 Why do we need migrations?

#### Imagine this:

- Today → you create students table
- Tomorrow → you add age column
- Later → you rename a column

#### ⚠️ Without migrations:

- You forget what changes you made ❌
- Team gets different DB structure ❌
- Deployment becomes messy ❌

--- 
👉 Migrations solve this 👍

## 🔄 What a migration does

Each migration file:
- Creates table
- Updates table
- Deletes table
- Adds/removes columns

--- 
##### 📂 Example inside migrations/
migrations/
│── 001_create_students_table.js
│── 002_add_age_column.js
│── 003_create_marks_table.js

##### 🧩 Example Migration File
```
exports.up = async (pgm) => {
  pgm.createTable("students", {
    id: "id",
    name: { type: "varchar(100)", notNull: true },
    email: { type: "varchar(100)", unique: true }
  });
};

exports.down = async (pgm) => {
  pgm.dropTable("students");
};
```
--- 
## 🔼 up vs 🔽 down
| Function | Purpose                             |
| -------- | ----------------------------------- |
| `up`     | Apply changes (create/update table) |
| `down`   | Undo changes (rollback)             |

--- 
### 🚀 How migrations work
```
npx migrate up     # apply changes
npx migrate down   # rollback
``` 
--- 

### 🎯 Real Flow
Code change → Migration file → Run migration → DB updated
🔥 Why this is IMPORTANT (Interview Point ⭐)

Say this:

“Migrations help maintain database consistency across environments and allow safe schema changes with rollback support.”

--- 

### ⚡ Without vs With Migrations
| Without          | With          |
| ---------------- | ------------- |
| Manual SQL       | Automated     |
| Error-prone      | Safe          |
| No history       | Full history  |
| Hard to rollback | Easy rollback |


#### 🧠 Simple Analogy

- 👉 Think of migrations like:
       - Git commits for your database

#### 💡 Bonus (Very Important)

Tools you might be using:

 Sequelize CLI
- Knex
- Prisma
- node-pg-migrate

