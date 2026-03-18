# web-development
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Task 2 Project</title>
  <style>
    body {
      font-family: Arial;
      margin: 0;
      padding: 0;
      background: #f4f4f4;
    }

    header {
      background: teal;
      color: white;
      padding: 15px;
      text-align: center;
    }

    .container {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
      padding: 20px;
    }

    .box {
      background: white;
      padding: 20px;
      border-radius: 10px;
    }

    input, textarea, button {
      width: 100%;
      margin: 10px 0;
      padding: 10px;
    }

    button {
      background: teal;
      color: white;
      border: none;
      cursor: pointer;
    }

    ul {
      list-style: none;
      padding: 0;
    }

    li {
      background: #eee;
      margin: 5px 0;
      padding: 10px;
      display: flex;
      justify-content: space-between;
    }

    /* Responsive */
    @media(max-width: 768px) {
      .container {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>

<header>
  <h1>Intermediate Web Project</h1>
</header>

<div class="container">

  <!-- Contact Form -->
  <div class="box">
    <h2>Contact Form</h2>
    <form id="form">
      <input type="text" id="name" placeholder="Name">
      <input type="email" id="email" placeholder="Email">
      <textarea id="message" placeholder="Message"></textarea>
      <button type="submit">Submit</button>
      <p id="error" style="color:red;"></p>
    </form>
  </div>

  <!-- To-Do List -->
  <div class="box">
    <h2>To-Do List</h2>
    <input type="text" id="taskInput" placeholder="Enter task">
    <button onclick="addTask()">Add Task</button>
    <ul id="taskList"></ul>
  </div>

</div>

<script>
  // Form Validation
  document.getElementById("form").addEventListener("submit", function(e) {
    e.preventDefault();

    let name = document.getElementById("name").value;
    let email = document.getElementById("email").value;
    let error = document.getElementById("error");

    if (name === "" || email === "") {
      error.innerText = "All fields are required!";
    } else if (!email.includes("@")) {
      error.innerText = "Enter valid email!";
    } else {
      error.innerText = "Form submitted successfully!";
    }
  });

  // To-Do List
  function addTask() {
    let input = document.getElementById("taskInput");
    let task = input.value;

    if (task === "") return;

    let li = document.createElement("li");
    li.innerHTML = task + " <button onclick='this.parentElement.remove()'>X</button>";

    document.getElementById("taskList").appendChild(li);
    input.value = "";
  }
</script>

</body>
</html>
