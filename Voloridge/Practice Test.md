Write an `SQL` query that returns
- Each department name
- The number of employees in that department
- Only departments with at least 3 employees
- Ordered by employee count descending

```sql
SELECT COUNT(e.id) AS num_employees, d.dept_name
FROM employees AS e
JOIN departments AS d
  ON e.dept_id = d.id
GROUP BY d.dept_name
HAVING COUNT(e.id) > 2
ORDER BY num_employees DESC
```

---

## Q8 – Mini Backend API + Minimal Front-End (10 pts)
### Backend
Use **either Express (Node.js)** or **Flask (Python)**.
Implement:
1. `GET /users`
    - Returns array of all users.
2. `POST /users`
    - Accepts JSON: `{ "name": "Alice" }`
    - Creates a user with fields:
        - `id` (auto-increment int)
        - `name` (string)
        - `created_at` (timestamp from server)
    - Returns `201 Created`, new user JSON, and `Location: /users/{id}`.

Use an **in-memory array** for your user list.
### Frontend
Write minimal HTML + JS that:
- On page load, fetches `/users` and lists their names.
- Provides an `<input>` and `<button>` to add a new user via `POST /users`.
- Appends the newly created user to the existing list without refreshing the page.


```js
const express = require("express");
const app = express()

app.use(express.json());

//in memory array
users = [
	{
		name: "aasdf",
	},
	{
		name: "aasdf",
	}
]
let autoIncrement = 1;


//helper function to hash password
function fakeHash(unHashed_password):
	return hashedPassword;


//get
//simply returns the array held within memory
//if this was within mongodb we would connect using connection string and validate response from mongo
app.get("/users", (req, res) async => {
	await return JSON.stringify(users);
})

//post
app.post("/users", (req, res) =>{
  const { name } = req.body;

  if (typeof name !== "string" || name.trim() === "") {
    return res
      .status(400)
      .json({ error: "name is required and must be a non-empty string" });
  }

	  const newUser = createUser(name.trim());
	  users.push(newUser);

	res
	    .status(201)
	    .location(`/users/${newUser.id}`)
	    .json(newUser);
	});
	
})


```


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Users</title>
</head>
<body>
  <h1>Users</h1>

  <!-- New user form -->
  <form id="new-user-form">
    <input
      type="text"
      id="new-user-name"
      placeholder="Enter user name"
      required
    />
    <button type="submit">Add User</button>
  </form>

  <h2>Current Users</h2>
  <ul id="user-list"></ul>

  <script>
    const userListEl = document.getElementById("user-list");
    const formEl = document.getElementById("new-user-form");
    const nameInputEl = document.getElementById("new-user-name");

    // Helper to render a single user
    function appendUser(user) {
      const li = document.createElement("li");
      li.textContent = user.name;
      li.dataset.id = user.id;
      userListEl.appendChild(li);
    }

    // Load users on page load
    async function loadUsers() {
      try {
        const res = await fetch("/users");
        if (!res.ok) {
          console.error("Failed to load users", res.status);
          return;
        }
        const users = await res.json();
        userListEl.innerHTML = "";
        users.forEach(appendUser);
      } catch (err) {
        console.error("Error fetching users", err);
      }
    }

    // Handle new user creation
    formEl.addEventListener("submit", async (event) => {
      event.preventDefault();
      const name = nameInputEl.value.trim();
      if (!name) return;

      try {
        const res = await fetch("/users", {
          method: "POST",
          headers: {
            "Content-Type": "application/json"
          },
          body: JSON.stringify({ name })
        });

        if (!res.ok) {
          console.error("Failed to create user", res.status);
          return;
        }

        const newUser = await res.json();
        appendUser(newUser);
        nameInputEl.value = "";
      } catch (err) {
        console.error("Error creating user", err);
      }
    });

    document.addEventListener("DOMContentLoaded", loadUsers);
  </script>
</body>
</html>

```


---


`employees`
- `id` (PK)
- `name`
- `department_id`

`departments`
- `id` (PK)
- `name`

`projects`
- `id` (PK)
- `name`
- `department_id`

`employee_projects`
- `employee_id` (FK to employees.id)
- `project_id` (FK to projects.id)

**Task:**
Write a SQL query to retrieve, for each department, the following information:
- `department_name`
- `num_employees` – the number of employees in that department
- `num_projects` – the number of projects in that department
- Only include departments that have **at least one employee** and **at least one project**.
- Order the result by `department_name` in ascending order.

You may assume standard SQL (e.g., PostgreSQL / MySQL style).
**Answer format:**  
Write a single SQL query using `SELECT`, `FROM`, `JOIN`, `GROUP BY`, and `HAVING` as needed.

```sql
SELECT d.name, COUNT(e.id) AS num_employees, COUNT(p.id) AS num_projects
FROM departments AS d
JOIN projects as p
  ON p.department_id = d.id
JOIN employees as e
  ON e.department_id = d.id
GROUP BY d.name
HAVING COUNT(e.id) > 0 AND COUNT(p.id) > 0
ORDER BY d.name
```

```sql
SELECT 
    d.name AS department_name,
    e.num_employees,
    p.num_projects
FROM departments d
JOIN (
    SELECT department_id, COUNT(*) AS num_employees
    FROM employees
    GROUP BY department_id
) e ON e.department_id = d.id
JOIN (
    SELECT department_id, COUNT(*) AS num_projects
    FROM projects
    GROUP BY department_id
) p ON p.department_id = d.id
ORDER BY d.name;

```