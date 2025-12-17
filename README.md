# 📝 TDS Bonus Mark Setup Guide

> Complete guide for creating and submitting your exam questions
> 
<img width="1536" height="1024" alt="ChatGPT Image Dec 17, 2025, 11_16_47 AM" src="https://github.com/user-attachments/assets/c07b26af-f9a3-4e2f-88c8-445ad0214687" />

## 🎯 Roll Number
**22f300XXXX**

---

## 📋 Prerequisites

Before you begin, ensure:
- ✅ Repository is already forked/cloned
- ✅ You are inside `exam-repo-public-release/` directory

---

## 🚀 Step-by-Step Instructions

### **Step 1** — Create Your Branch

```bash
git checkout -b exam-22f3001994
```

---

### **Step 2** — Create Question Files

All files must be created inside the `src/` directory.

#### Question 1: Basic CLI Command
**File:** `src/q-cli-basic.js`

```javascript
import { html } from "https://cdn.jsdelivr.net/npm/lit-html@3/lit-html.js";

export default async function ({ user, weight = 1 }) {
  const id = "q-cli-basic";
  const title = "Basic CLI Command";

  const answer = "ls -la";

  const question = html`
    <div class="mb-3">
      <p>
        Which Linux command lists <strong>all files</strong> (including hidden ones)
        in the current directory in <strong>long format</strong>?
      </p>
      <label for="${id}" class="form-label">Command:</label>
      <input class="form-control" id="${id}" name="${id}" />
    </div>
  `;

  return { id, title, weight, question, answer };
}
```

#### Question 2: Create a Git Branch
**File:** `src/q-git-branch.js`

```javascript
import { html } from "https://cdn.jsdelivr.net/npm/lit-html@3/lit-html.js";

export default async function ({ user, weight = 1 }) {
  const id = "q-git-branch";
  const title = "Create a Git Branch";

  const answer = "git checkout -b feature-x";

  const question = html`
    <div class="mb-3">
      <p>
        What Git command creates a new branch named <code>feature-x</code>
        and switches to it in one step?
      </p>
      <label for="${id}" class="form-label">Command:</label>
      <input class="form-control" id="${id}" name="${id}" />
    </div>
  `;

  return { id, title, weight, question, answer };
}
```

#### Question 3: POST JSON using curl
**File:** `src/q-curl-post.js`

```javascript
import { html } from "https://cdn.jsdelivr.net/npm/lit-html@3/lit-html.js";

export default async function ({ user, weight = 1 }) {
  const id = "q-curl-post";
  const title = "POST JSON using curl";

  const answer = 'curl -X POST -H "Content-Type: application/json" -d \'{"a":1}\' https://example.com';

  const question = html`
    <div class="mb-3">
      <p>
        Write a <code>curl</code> command to send the JSON
        <code>{"a":1}</code> via POST to <code>https://example.com</code>.
      </p>
      <label for="${id}" class="form-label">Command:</label>
      <input class="form-control" id="${id}" name="${id}" />
    </div>
  `;

  return { id, title, weight, question, answer };
}
```

#### Question 4: SQL COUNT Query
**File:** `src/q-sql-count.js`

```javascript
import { html } from "https://cdn.jsdelivr.net/npm/lit-html@3/lit-html.js";

export default async function ({ user, weight = 1 }) {
  const id = "q-sql-count";
  const title = "SQL COUNT Query";

  const answer = "SELECT COUNT(*) FROM users;";

  const question = html`
    <div class="mb-3">
      <p>
        Write an SQL query to count the total number of rows
        in a table named <code>users</code>.
      </p>
      <label for="${id}" class="form-label">Query:</label>
      <input class="form-control" id="${id}" name="${id}" />
    </div>
  `;

  return { id, title, weight, question, answer };
}
```

#### Question 5: Parse JSON in JavaScript
**File:** `src/q-json-parse.js`

```javascript
import { html } from "https://cdn.jsdelivr.net/npm/lit-html@3/lit-html.js";

export default async function ({ user, weight = 1 }) {
  const id = "q-json-parse";
  const title = "Parse JSON in JavaScript";

  const answer = "JSON.parse";

  const question = html`
    <div class="mb-3">
      <p>
        Which JavaScript function converts a JSON string
        into a JavaScript object?
      </p>
      <label for="${id}" class="form-label">Function name:</label>
      <input class="form-control" id="${id}" name="${id}" />
    </div>
  `;

  return { id, title, weight, question, answer };
}
```

---

### **Step 3** — Create Your Exam File

**File:** `src/exam-22f3001994.js`

```javascript
import { displayQuestions } from "./utils/display.js";

export async function questions(user, elementMap) {
  const results = [
    ...(await import("./q-cli-basic.js").then(m => [m.default({ user })])),
    ...(await import("./q-git-branch.js").then(m => [m.default({ user })])),
    ...(await import("./q-curl-post.js").then(m => [m.default({ user })])),
    ...(await import("./q-sql-count.js").then(m => [m.default({ user })])),
    ...(await import("./q-json-parse.js").then(m => [m.default({ user })])),
  ];

  displayQuestions(results, elementMap);

  return Object.fromEntries(
    results.map(({ id, ...rest }) => [id, rest])
  );
}
```

---

### **Step 4** — Commit and Push

```bash
git add src/
git commit -m "Add 5 TDS bonus questions"
git push origin exam-22f3001994
```

---

### **Step 5** — Create Pull Request

Go to your repository on GitHub and create a new Pull Request with:

- **Base:** `main`
- **Compare:** `exam-22f3001994`
- **Title:** `Add Questions: exam-22f3001994`

---

## ✅ Completion Checklist

- [ ] Branch created
- [ ] 5 question files created in `src/`
- [ ] Exam file created
- [ ] Changes committed
- [ ] Changes pushed to remote
- [ ] Pull request created

---

## 📚 Question Topics Summary

| # | Topic | File |
|---|-------|------|
| 1 | Linux CLI | `q-cli-basic.js` |
| 2 | Git Branching | `q-git-branch.js` |
| 3 | curl POST | `q-curl-post.js` |
| 4 | SQL COUNT | `q-sql-count.js` |
| 5 | JSON Parsing | `q-json-parse.js` |

---

**Good luck! 🎓**
