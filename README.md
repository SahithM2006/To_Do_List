# Ex03 To-Do List using JavaScript
## Date:

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
```
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Interactive To-Do App</title>

<style>

body
{
    font-family: Arial;
    background:#f4f6fb;
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
    transition:0.3s;
}

.dark
{
    background:#1e1e2f;
    color:white;
}

.container
{
    width:500px;
    background:white;
    padding:25px;
    border-radius:10px;
    box-shadow:0 10px 20px rgba(0,0,0,0.2);
}

.dark .container
{
    background:#2a2a40;
}

h1
{
    text-align:center;
}

.input-section
{
    display:flex;
    gap:8px;
    margin-bottom:10px;
}

input,select
{
    padding:8px;
    border-radius:5px;
    border:1px solid #ccc;
}

button
{
    padding:8px 12px;
    border:none;
    background:#4a6cf7;
    color:white;
    border-radius:5px;
    cursor:pointer;
}

button:hover
{
    opacity:0.8;
}

.filters
{
    margin:10px 0;
    display:flex;
    gap:10px;
}

ul
{
    list-style:none;
    padding:0;
}

li
{
    background:#f1f1f1;
    padding:10px;
    margin-bottom:8px;
    border-radius:6px;
    transition:0.3s;
}

li:hover
{
    transform:scale(1.02);
}

.completed
{
    text-decoration:line-through;
    color:gray;
}

.progress
{
    width:100%;
    background:#ddd;
    height:8px;
    border-radius:5px;
    margin-top:10px;
}

.progress-bar
{
    height:8px;
    width:0%;
    background:#4a6cf7;
    border-radius:5px;
}

.priority-high
{
    border-left:5px solid red;
}

.priority-medium
{
    border-left:5px solid orange;
}

.priority-low
{
    border-left:5px solid green;
}

.task-buttons button
{
    font-size:12px;
    margin-right:5px;
}

.toggle
{
    float:right;
}

</style>
</head>

<body>

<div class="container">

<h1>Interactive To-Do List</h1>

<button class="toggle" onclick="toggleTheme()">🌙</button>

<div class="input-section">
<input type="text" id="taskInput" placeholder="Enter task">
<select id="priority">
<option value="low">Low</option>
<option value="medium">Medium</option>
<option value="high">High</option>
</select>
<input type="date" id="date">
<button onclick="addTask()">Add</button>
</div>

<div class="filters">
<button onclick="filterTasks('all')">All</button>
<button onclick="filterTasks('completed')">Completed</button>
<button onclick="filterTasks('pending')">Pending</button>
</div>

<ul id="taskList"></ul>

<div class="progress">
<div class="progress-bar" id="progressBar"></div>
</div>

</div>

<script>

let taskList=document.getElementById("taskList")

function addTask()
{
let text=document.getElementById("taskInput").value
let priority=document.getElementById("priority").value
let date=document.getElementById("date").value

if(text==="")
{
alert("Enter a task")
return
}

let li=document.createElement("li")
li.classList.add("priority-"+priority)

li.innerHTML=`
<span onclick="toggleTask(this)">${text}</span>
<div>Due: ${date}</div>
<div class="task-buttons">
<button onclick="editTask(this)">Edit</button>
<button onclick="deleteTask(this)">Delete</button>
</div>
`

taskList.appendChild(li)

document.getElementById("taskInput").value=""

updateProgress()
}

function toggleTask(element)
{
element.classList.toggle("completed")
updateProgress()
}

function deleteTask(btn)
{
btn.parentElement.parentElement.remove()
updateProgress()
}

function editTask(btn)
{
let span=btn.parentElement.parentElement.querySelector("span")

let newText=prompt("Edit task",span.innerText)

if(newText)
span.innerText=newText
}

function filterTasks(type)
{
let tasks=document.querySelectorAll("li")

tasks.forEach(task=>
{
if(type==="all")
task.style.display="block"

else if(type==="completed")
task.style.display=task.querySelector("span").classList.contains("completed")?"block":"none"

else
task.style.display=!task.querySelector("span").classList.contains("completed")?"block":"none"
})
}

function updateProgress()
{
let tasks=document.querySelectorAll("li")
let completed=document.querySelectorAll(".completed")

let percent=0

if(tasks.length>0)
percent=(completed.length/tasks.length)*100

document.getElementById("progressBar").style.width=percent+"%"
}

function toggleTheme()
{
document.body.classList.toggle("dark")
}

</script>

</body>
</html>

```

## OUTPUT
<img width="1897" height="1027" alt="Screenshot 2026-03-10 102823" src="https://github.com/user-attachments/assets/1e4d7728-88d4-436f-ba65-5f433566f841" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
