# To-do-list
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List App</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>To-Do List</h1>
        <form id="task-form">
            <input type="text" id="task-input" placeholder="Add a new task">
            <button type="submit">Add Task</button>
        </form>
        <ul id="task-list"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>
document.addEventListener('DOMContentLoaded', function() {
    const taskForm = document.getElementById('task-form');
    const taskInput = document.getElementById('task-input');
    const taskList = document.getElementById('task-list');

    taskForm.addEventListener('submit', function(e) {
        e.preventDefault();
        const taskText = taskInput.value.trim();
        if (taskText !== '') {
            addTask(taskText);
            taskInput.value = '';
        }
    });

    taskList.addEventListener('click', function(e) {
        if (e.target.classList.contains('delete')) {
            e.target.parentElement.remove();
        } else if (e.target.tagName === 'LI') {
            e.target.classList.toggle('completed');
        }
    });

    function addTask(taskText) {
        const li = document.createElement('li');
        li.appendChild(document.createTextNode(taskText));

        const deleteBtn = document.createElement('button');
        deleteBtn.className = 'delete';
        deleteBtn.appendChild(document.createTextNode('X'));
        li.appendChild(deleteBtn);

        taskList.appendChild(li);
    }
});
body {
    font-family: Arial, sans-serif;
    background: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.container {
    background: white;
    padding: 20px;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 300px;
}

h1 {
    text-align: center;
}

form {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
}

form input {
    flex: 1;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 3px;
}

form button {
    padding: 10px;
    background: #5cb85c;
    color: white;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

form button:hover {
    background: #4cae4c;
}

ul {
    list-style: none;
    padding: 0;
}

ul li {
    background: #f9f9f9;
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 3px;
    display: flex;
    justify-content: space-between;
}

ul li.completed {
    text-decoration: line-through;
    color: #888;
}

ul li button {
    background: #d9534f;
    color: white;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}

ul li button:hover {
    background: #c9302c;
}
