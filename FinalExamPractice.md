# Run the API Server Locally

## Create the Project

```bash
mkdir task-api
cd task-api
npm init -y
npm install express cors
```

## Create **server.js**

```js
const express = require("express");
const cors = require("cors");

const app = express();
app.use(cors());
app.use(express.json());

// In-memory "database"
let tasks = [
  {
    id: 1,
    title: "Buy groceries",
    description: "Milk, eggs, bread",
    isDone: false,
  },
  {
    id: 2,
    title: "Finish SwiftUI assignment",
    description: "CRUD + API integration",
    isDone: false,
  },
];

let nextId = 3;

// GET all tasks
app.get("/tasks", (req, res) => {
  res.json(tasks);
});

// GET single task
app.get("/tasks/:id", (req, res) => {
  const id = Number(req.params.id);
  const task = tasks.find((t) => t.id === id);
  if (!task) return res.status(404).json({ message: "Task not found" });
  res.json(task);
});

// POST create task
app.post("/tasks", (req, res) => {
  const { title, description, isDone } = req.body;

  const newTask = {
    id: nextId++,
    title,
    description,
    isDone: isDone ?? false,
  };

  tasks.push(newTask);
  res.status(201).json(newTask);
});

// PUT update task
app.put("/tasks/:id", (req, res) => {
  const id = Number(req.params.id);
  const { title, description, isDone } = req.body;

  const index = tasks.findIndex((t) => t.id === id);
  if (index === -1) return res.status(404).json({ message: "Task not found" });

  const updated = {
    id,
    title,
    description,
    isDone,
  };

  tasks[index] = updated;
  res.json(updated);
});

// DELETE task
app.delete("/tasks/:id", (req, res) => {
  const id = Number(req.params.id);
  const index = tasks.findIndex((t) => t.id === id);
  if (index === -1) return res.status(404).json({ message: "Task not found" });

  tasks.splice(index, 1);
  res.status(204).send();
});

app.listen(3000, () => {
  console.log("Task API running on http://localhost:3000");
});
```

## Run Server

```bash
node server.js
```
