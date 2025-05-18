<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Dynamic To-Do & Contact Form</title>
  <link rel="stylesheet" href="style.css" />
<style>
* {
  box-sizing: border-box;
  font-family: Arial, sans-serif;
}

body {
  margin: 0;
  padding: 0;
}

header {
  background-color: #f1a10b;
  color: white;
  padding: 1em;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

nav a {
  color: white;
  margin-left: 15px;
  text-decoration: none;
}

.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2em;
  padding: 2em;
}

section {
  background-color: #f4f4f4;
  padding: 1em;
  border-radius: 8px;
}

input, button {
  display: block;
  margin: 10px 0;
  padding: 10px;
  width: 100%;
}

#taskList li {
  background-color: #ddd;
  padding: 8px;
  margin: 5px 0;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
}

@media (max-width: 768px) {
  .grid-container {
    grid-template-columns: 1fr;
  }
}
</style>
</head>
<body>
  <header>
    <h1>My Project</h1>
    <nav>
      <a href="#">Home</a>
      <a href="#">Contact</a>
    </nav>
  </header>

  <main class="grid-container">
    <!-- Contact Form -->
    <section class="form-section">
      <h2>Contact Us</h2>
      <form id="contactForm">
        <input type="text" id="name" placeholder="Your Name" required />
        <input type="email" id="email" placeholder="Your Email" required />
        <button type="submit">Submit</button>
        <p id="formMessage"></p>
      </form>
    </section>

    <!-- To-Do List -->
    <section class="todo-section">
      <h2>To-Do List</h2>
      <input type="text" id="taskInput" placeholder="Enter a task" />
      <button onclick="addTask()">Add Task</button>
      <ul id="taskList"></ul>
    </section>
  </main>

  <script>// Contact Form Validation
document.getElementById("contactForm").addEventListener("submit", function (e) {
  e.preventDefault();
  const name = document.getElementById("name").value.trim();
  const email = document.getElementById("email").value.trim();
  const message = document.getElementById("formMessage");

  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

  if (!name || !email) {
    message.textContent = "All fields are required.";
    message.style.color = "red";
  } else if (!emailRegex.test(email)) {
    message.textContent = "Invalid email format.";
    message.style.color = "red";
  } else {
    message.textContent = "Form submitted successfully!";
    message.style.color = "green";
    this.reset();
  }
});

// To-Do List Functionality
function addTask() {
  const taskInput = document.getElementById("taskInput");
  const task = taskInput.value.trim();
  if (task === "") return;

  const li = document.createElement("li");
  li.textContent = task;

  const removeBtn = document.createElement("button");
  removeBtn.textContent = "Remove";
  removeBtn.onclick = () => li.remove();

  li.appendChild(removeBtn);
  document.getElementById("taskList").appendChild(li);
  taskInput.value = "";
}
</script>
</body>
</html>
