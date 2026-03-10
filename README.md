# Ex03 To-Do List using JavaScript
## Date: 10/03/2026

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
<title>Dashboard To-Do App</title>

<style>

body
{
margin:0;
font-family:Segoe UI;
background:linear-gradient(270deg,#667eea,#764ba2,#6dd5ed,#2193b0);
background-size:600% 600%;
animation:bg 15s ease infinite;
height:100vh;
display:flex;
color:white;
}

@keyframes bg
{
0%{background-position:0% 50%}
50%{background-position:100% 50%}
100%{background-position:0% 50%}
}

.sidebar
{
width:220px;
background:rgba(0,0,0,0.4);
backdrop-filter:blur(10px);
padding:20px;
display:flex;
flex-direction:column;
}

.sidebar h2
{
margin-bottom:20px;
}

.sidebar button
{
margin-bottom:10px;
padding:8px;
border:none;
background:#ffffff22;
color:white;
cursor:pointer;
border-radius:6px;
}

.sidebar button:hover
{
background:#ffffff55;
}

.main
{
flex:1;
padding:25px;
overflow:auto;
}

.header
{
display:flex;
justify-content:space-between;
align-items:center;
margin-bottom:20px;
}

input
{
padding:8px;
border-radius:6px;
border:none;
}

.task-input
{
display:flex;
gap:10px;
margin-bottom:20px;
}

button
{
padding:8px 12px;
border:none;
background:#00c6ff;
color:white;
border-radius:6px;
cursor:pointer;
}

.task-board
{
display:grid;
grid-template-columns:repeat(auto-fill,minmax(250px,1fr));
gap:15px;
}

.task
{
background:rgba(255,255,255,0.2);
padding:12px;
border-radius:10px;
transition:0.3s;
}

.task:hover
{
transform:scale(1.05);
}

.completed
{
text-decoration:line-through;
opacity:0.6;
}

.progress
{
margin-top:20px;
background:#ffffff33;
height:10px;
border-radius:10px;
}

.bar
{
height:10px;
width:0%;
background:#00ff9d;
border-radius:10px;
}

.dark
{
background:#111;
}

</style>
</head>

<body>

<div class="sidebar">

<h2>⚡ Tasks</h2>

<button onclick="filterTasks('all')">All Tasks</button>
<button onclick="filterTasks('done')">Completed</button>
<button onclick="filterTasks('todo')">Pending</button>
<button onclick="clearTasks()">Clear All</button>

</div>

<div class="main">

<div class="header">
<h1>My Dashboard</h1>
<button onclick="toggleTheme()">🌙</button>
</div>

<div class="task-input">
<input id="taskInput" placeholder="Enter a new task...">
<button onclick="addTask()">Add Task</button>
</div>

<input id="search" placeholder="Search tasks..." onkeyup="searchTask()">

<div class="task-board" id="taskBoard"></div>

<div class="progress">
<div class="bar" id="progressBar"></div>
</div>

</div>

<script>

let board=document.getElementById("taskBoard")

function addTask()
{
let text=document.getElementById("taskInput").value
if(text==="") return

let div=document.createElement("div")
div.className="task"

div.innerHTML=`
<p onclick="toggleTask(this)">${text}</p>
<button onclick="editTask(this)">Edit</button>
<button onclick="deleteTask(this)">Delete</button>
`

board.appendChild(div)

document.getElementById("taskInput").value=""

saveTasks()
updateProgress()
}

function toggleTask(el)
{
el.classList.toggle("completed")
confetti()
saveTasks()
updateProgress()
}

function deleteTask(btn)
{
btn.parentElement.remove()
saveTasks()
updateProgress()
}

function editTask(btn)
{
let p=btn.parentElement.querySelector("p")
let newText=prompt("Edit task",p.innerText)
if(newText) p.innerText=newText
saveTasks()
}

function searchTask()
{
let input=document.getElementById("search").value.toLowerCase()

document.querySelectorAll(".task").forEach(task=>{
task.style.display=task.innerText.toLowerCase().includes(input)?"block":"none"
})
}

function filterTasks(type)
{
document.querySelectorAll(".task").forEach(task=>{

let done=task.querySelector("p").classList.contains("completed")

if(type==="all") task.style.display="block"
else if(type==="done") task.style.display=done?"block":"none"
else task.style.display=!done?"block":"none"

})
}

function clearTasks()
{
if(confirm("Delete all tasks?"))
{
board.innerHTML=""
saveTasks()
updateProgress()
}
}

function updateProgress()
{
let total=document.querySelectorAll(".task").length
let done=document.querySelectorAll(".completed").length

let percent= total? done/total*100 :0

document.getElementById("progressBar").style.width=percent+"%"
}

function toggleTheme()
{
document.body.classList.toggle("dark")
}

function saveTasks()
{
localStorage.setItem("tasks",board.innerHTML)
}

window.onload=function()
{
let data=localStorage.getItem("tasks")
if(data) board.innerHTML=data
updateProgress()
}

function confetti()
{
for(let i=0;i<15;i++)
{
let c=document.createElement("div")
c.style.position="fixed"
c.style.width="6px"
c.style.height="6px"
c.style.background="hsl("+Math.random()*360+"deg,100%,50%)"
c.style.left=Math.random()*100+"vw"
c.style.top="0"
document.body.appendChild(c)

let fall=setInterval(()=>{
c.style.top=parseInt(c.style.top)+5+"px"
if(parseInt(c.style.top)>window.innerHeight)
{
c.remove()
clearInterval(fall)
}
},20)
}
}

</script>

</body>
</html>

```

## OUTPUT
<img width="1918" height="1028" alt="image" src="https://github.com/user-attachments/assets/0d625452-e0a3-4ba2-b0a8-785481651259" />

<img width="1918" height="1028" alt="image" src="https://github.com/user-attachments/assets/b0160ea4-12f0-4ac3-b846-1f142b765228" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
