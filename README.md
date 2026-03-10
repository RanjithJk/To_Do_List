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

### Index.html:
```
<!DOCTYPE html>
<html>
<head>
<title>Todo App</title>
<link rel="stylesheet" href="style.css">
</head>

<body>

<div class="container">

<h1>Todo Application</h1>

<div class="input-section">
<input type="text" id="taskInput" placeholder="Enter a task">
<button onclick="addTask()">Add</button>
</div>

<div class="filter">
<button onclick="filterTasks('all')">All</button>
<button onclick="filterTasks('completed')">Completed</button>
<button onclick="filterTasks('pending')">Pending</button>
</div>

<ul id="taskList"></ul>

</div>

<script src="script.js"></script>
</body>
</html>
```

### Style.css:
```
body{
font-family: Arial;
background:#f2f2f2;
display:flex;
justify-content:center;
margin-top:50px;
}

.container{
background:white;
padding:20px;
width:350px;
border-radius:10px;
box-shadow:0 0 10px gray;
}

h1{
text-align:center;
}

.input-section{
display:flex;
gap:10px;
}

input{
flex:1;
padding:8px;
}

button{
padding:8px 12px;
cursor:pointer;
}

ul{
list-style:none;
padding:0;
}

li{
display:flex;
justify-content:space-between;
padding:8px;
border-bottom:1px solid #ddd;
}

.completed{
text-decoration:line-through;
color:gray;
}

.filter{
margin-top:10px;
display:flex;
justify-content:space-between;
}
```

### Script.js:
```
let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

function saveTasks(){
localStorage.setItem("tasks", JSON.stringify(tasks));
}

function renderTasks(filter="all"){

const list = document.getElementById("taskList");
list.innerHTML="";

tasks.forEach((task,index)=>{

if(filter==="completed" && !task.completed) return;
if(filter==="pending" && task.completed) return;

let li=document.createElement("li");

li.innerHTML = `
<span class="${task.completed?'completed':''}" onclick="toggleTask(${index})">
${task.text}
</span>

<div>
<button onclick="editTask(${index})">Edit</button>
<button onclick="deleteTask(${index})">Delete</button>
</div>
`;

list.appendChild(li);

});

}

function addTask(){

const input=document.getElementById("taskInput");
const text=input.value.trim();

if(text==="") return;

tasks.push({
text:text,
completed:false
});

input.value="";
saveTasks();
renderTasks();
}

function deleteTask(index){
tasks.splice(index,1);
saveTasks();
renderTasks();
}

function toggleTask(index){
tasks[index].completed=!tasks[index].completed;
saveTasks();
renderTasks();
}

function editTask(index){

let newTask=prompt("Edit task",tasks[index].text);

if(newTask!==null){
tasks[index].text=newTask;
saveTasks();
renderTasks();
}

}

function filterTasks(type){
renderTasks(type);
}

renderTasks();
```


## OUTPUT

<img width="1680" height="749" alt="image" src="https://github.com/user-attachments/assets/5d27b695-5603-4c18-b937-88b7d87cabad" />



## RESULT
The program for creating To-do list using JavaScript is executed successfully.
