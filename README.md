# MWAD-EX_03-To-Do-List-using-JavaScript
## Date:30/04/2025
## Name: GURU PRASATH R
## Reg.no:212223040053

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            text-align: center;
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 400px;
        }

        h1 {
            font-size: 2rem;
            margin-bottom: 20px;
        }

        .todo-input {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
        }

        #todo-input {
            width: 75%;
            padding: 10px;
            font-size: 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        #add-btn {
            width: 20%;
            background-color: #4CAF50;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        #add-btn:hover {
            background-color: #45a049;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        li {
            background-color: #fafafa;
            margin: 10px 0;
            padding: 10px;
            border-radius: 4px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        button.delete-btn {
            background-color: #f44336;
            color: white;
            padding: 5px 10px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        button.delete-btn:hover {
            background-color: #e53935;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>To-Do App</h1>
        <div class="todo-input">
            <input type="text" id="todo-input" placeholder="Enter a new task" />
            <button id="add-btn">Add</button>
        </div>
        <ul id="todo-list"></ul>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const inputField = document.getElementById('todo-input');
            const addButton = document.getElementById('add-btn');
            const todoList = document.getElementById('todo-list');

            // Load tasks from localStorage
            const loadTasks = () => {
                const tasks = JSON.parse(localStorage.getItem('tasks')) || [];
                tasks.forEach(task => addTaskToDOM(task));
            };

            // Add task to the DOM
            const addTaskToDOM = (task) => {
                const li = document.createElement('li');
                li.textContent = task.text;
                if (task.completed) {
                    li.style.textDecoration = 'line-through';
                }

                // Add delete button
                const deleteBtn = document.createElement('button');
                deleteBtn.textContent = 'Delete';
                deleteBtn.classList.add('delete-btn');
                deleteBtn.onclick = () => {
                    removeTaskFromLocalStorage(task.id);
                    li.remove();
                };

                li.appendChild(deleteBtn);
                li.onclick = () => {
                    toggleTaskCompletion(task.id, li);
                };

                todoList.appendChild(li);
            };

            // Add task to localStorage
            const addTaskToLocalStorage = (text) => {
                const tasks = JSON.parse(localStorage.getItem('tasks')) || [];
                const newTask = { id: Date.now(), text, completed: false };
                tasks.push(newTask);
                localStorage.setItem('tasks', JSON.stringify(tasks));
            };

            // Remove task from localStorage
            const removeTaskFromLocalStorage = (id) => {
                let tasks = JSON.parse(localStorage.getItem('tasks')) || [];
                tasks = tasks.filter(task => task.id !== id);
                localStorage.setItem('tasks', JSON.stringify(tasks));
            };

            // Toggle task completion
            const toggleTaskCompletion = (id, li) => {
                let tasks = JSON.parse(localStorage.getItem('tasks')) || [];
                const task = tasks.find(task => task.id === id);
                if (task) {
                    task.completed = !task.completed;
                    localStorage.setItem('tasks', JSON.stringify(tasks));
                    li.style.textDecoration = task.completed ? 'line-through' : 'none';
                }
            };

            // Handle adding new task
            addButton.addEventListener('click', () => {
                const taskText = inputField.value.trim();
                if (taskText) {
                    addTaskToLocalStorage(taskText);
                    addTaskToDOM({ id: Date.now(), text: taskText, completed: false });
                    inputField.value = '';
                }
            });

            // Initial load of tasks
            loadTasks();
        });
    </script>
</body>
</html>


## OUTPUT
![Screenshot 2025-04-30 093147](https://github.com/user-attachments/assets/c02a845c-23a4-4af0-b5a5-a046b3bcdd8f)


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
