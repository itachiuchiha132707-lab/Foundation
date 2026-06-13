<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>NayePankh Foundation AI Hub</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>

:root{
--bg:#0f172a;
--card:rgba(255,255,255,0.08);
--text:white;
--accent:#38bdf8;
--secondary:#94a3b8;
}

.light{
--bg:#f8fafc;
--card:white;
--text:#0f172a;
--accent:#0284c7;
--secondary:#475569;
}

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

body{
background:linear-gradient(-45deg,#0f172a,#1e293b,#0ea5e9,#1e293b);
background-size:400% 400%;
animation:gradient 12s ease infinite;
color:var(--text);
transition:0.4s;
overflow-x:hidden;
}

@keyframes gradient{
0%{background-position:0% 50%;}
50%{background-position:100% 50%;}
100%{background-position:0% 50%;}
}

header{
padding:80px 20px;
text-align:center;
}

header h1{
font-size:3rem;
margin-bottom:15px;
}

.highlight{
color:var(--accent);
}

header p{
max-width:700px;
margin:auto;
color:#d1d5db;
}

.container{
width:90%;
max-width:1200px;
margin:auto;
}

.btn{
padding:12px 25px;
border:none;
border-radius:30px;
cursor:pointer;
font-weight:600;
background:var(--accent);
margin:10px;
}

.card{
background:var(--card);
backdrop-filter:blur(15px);
border-radius:20px;
padding:25px;
}

.features{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
gap:20px;
margin:50px 0;
}

.feature{
transition:0.3s;
}

.feature:hover{
transform:translateY(-8px);
}

.stats{
display:grid;
grid-template-columns:repeat(3,1fr);
gap:20px;
margin:50px 0;
text-align:center;
}

.stats h2{
font-size:2.5rem;
color:var(--accent);
}

.chat-section{
margin:60px 0;
}

.chat-box{
height:350px;
overflow-y:auto;
padding:15px;
border-radius:15px;
background:rgba(0,0,0,0.15);
margin-bottom:15px;
}

.message{
padding:12px;
margin:10px 0;
border-radius:12px;
}

.user{
background:var(--accent);
color:black;
text-align:right;
}

.bot{
background:#334155;
}

.input-group{
display:flex;
gap:10px;
}

.input-group input{
flex:1;
padding:14px;
border:none;
border-radius:10px;
}

.input-group button{
padding:14px;
border:none;
border-radius:10px;
cursor:pointer;
}

.quote{
text-align:center;
font-size:1.2rem;
padding:20px;
margin-top:20px;
}

.career{
margin-top:50px;
}

.career input{
width:100%;
padding:15px;
border:none;
border-radius:10px;
margin:15px 0;
}

.output{
margin-top:15px;
padding:15px;
border-radius:10px;
background:rgba(255,255,255,0.05);
}

.toggle{
position:fixed;
right:20px;
top:20px;
z-index:999;
}

footer{
padding:40px;
text-align:center;
margin-top:60px;
}

@media(max-width:768px){
header h1{
font-size:2rem;
}

.stats{
grid-template-columns:1fr;
}
}

</style>
</head>

<body>

<button class="btn toggle" onclick="toggleTheme()">
🌙 Theme
</button>

<header>

<h1>
<span class="highlight">NayePankh Foundation</span><br>
AI Innovation Hub
</h1>

<p>
Empowering students through Artificial Intelligence,
career guidance, learning support and social impact.
</p>

<button class="btn" onclick="personalize()">
Personalize Experience
</button>

<h3 id="welcome"></h3>

</header>

<div class="container">

<div class="stats">

<div class="card">
<h2 id="students">0</h2>
<p>Students Guided</p>
</div>

<div class="card">
<h2 id="queries">0</h2>
<p>AI Queries Solved</p>
</div>

<div class="card">
<h2 id="volunteers">0</h2>
<p>Volunteers Connected</p>
</div>

</div>

<div class="features">

<div class="card feature">
<h3>🤖 AI Mentor</h3>
<p>Personalized learning assistance for every student.</p>
</div>

<div class="card feature">
<h3>📚 Smart Learning</h3>
<p>Adaptive education powered by AI technologies.</p>
</div>

<div class="card feature">
<h3>💡 Innovation Lab</h3>
<p>Explore future technologies and AI applications.</p>
</div>

<div class="card feature">
<h3>🌍 Social Impact</h3>
<p>Measure and improve community impact through data.</p>
</div>

</div>

<div class="chat-section card">

<h2>🤖 NayePankh AI Assistant</h2>

<div class="chat-box" id="chatBox">

<div class="message bot">
Hello! I am your AI Assistant. Ask me anything.
</div>

</div>

<div class="input-group">

<input
type="text"
id="userInput"
placeholder="Type your message..."
>

<button onclick="sendMessage()">Send</button>

<button onclick="startVoice()">🎤</button>

</div>

</div>

<div class="career card">

<h2>🎯 AI Career Guidance</h2>

<input
type="text"
id="careerInput"
placeholder="Example: Software Engineer"
>

<button class="btn" onclick="careerGuide()">
Generate Roadmap
</button>

<div class="output" id="careerOutput"></div>

</div>

<div class="card quote">

<h2>✨ Motivation Generator</h2>

<p id="quoteText">
Click below to generate motivation.
</p>

<button class="btn" onclick="generateQuote()">
Inspire Me
</button>

</div>

</div>

<footer>

<h3>NayePankh Foundation</h3>

<p>
Giving New Wings to Dreams Through Artificial Intelligence
</p>

</footer>

<script>

function personalize(){
let name=prompt("Enter your name");

if(name){
document.getElementById("welcome").innerHTML=
"Welcome "+name+
"! 🚀 Let's learn and grow together.";
}
}

function toggleTheme(){
document.body.classList.toggle("light");
}

let students=0;
let queries=0;
let volunteers=0;

setInterval(()=>{
if(students<5000){
students+=15;
queries+=50;
volunteers+=3;

document.getElementById("students").innerText=students+"+";
document.getElementById("queries").innerText=queries+"+";
document.getElementById("volunteers").innerText=volunteers+"+";
}
},30);

function sendMessage(){

let input=document.getElementById("userInput");
let text=input.value.trim();

if(text==="") return;

let chat=document.getElementById("chatBox");

chat.innerHTML+=
'<div class="message user">'+text+'</div>';

let response="Thank you for your message.";

if(text.toLowerCase().includes("ai")){
response=
"Artificial Intelligence helps us provide smarter learning experiences.";
}

else if(text.toLowerCase().includes("career")){
response=
"Use the Career Guidance section below to get a personalized roadmap.";
}

else if(text.toLowerCase().includes("volunteer")){
response=
"You can volunteer with NayePankh Foundation and create social impact.";
}

else{
response=
"I am here to assist you with education, careers and AI learning.";
}

setTimeout(()=>{

chat.innerHTML+=
'<div class="message bot">'+response+'</div>';

speak(response);

chat.scrollTop=chat.scrollHeight;

},500);

input.value="";
}

function speak(text){

let speech=
new SpeechSynthesisUtterance(text);

speech.lang="en-US";

window.speechSynthesis.speak(speech);
}

function startVoice(){

const recognition=
new(window.SpeechRecognition||
window.webkitSpeechRecognition)();

recognition.lang="en-US";

recognition.start();

recognition.onresult=function(event){

document.getElementById("userInput").value=
event.results[0][0].transcript;

};
}

function careerGuide(){

let career=
document.getElementById("careerInput")
.value.toLowerCase();

let output="";

if(career.includes("software")){

output=`
1. Learn HTML, CSS, JavaScript<br>
2. Learn React & Node.js<br>
3. Learn Databases<br>
4. Build Projects<br>
5. Create Portfolio<br>
6. Apply for Internships
`;

}

else if(career.includes("data")){

output=`
1. Learn Python<br>
2. Learn Statistics<br>
3. Learn Machine Learning<br>
4. Build AI Projects<br>
5. Create Portfolio
`;

}

else{

output=`
Research the field, learn core skills,
build projects and gain practical experience.
`;

}

document.getElementById("careerOutput")
.innerHTML=output;
}

const quotes=[

"Your future is created by what you do today.",
"Dream big and start small.",
"Success comes from consistent effort.",
"Every expert was once a beginner.",
"Education is the passport to the future.",
"Believe in yourself and keep learning."

];

function generateQuote(){

let random=
quotes[Math.floor(Math.random()*quotes.length)];

document.getElementById("quoteText")
.innerText=random;

speak(random);
}

/*
========================================================
OPENAI API INTEGRATION (OPTIONAL)
========================================================

Replace YOUR_API_KEY with your actual API key.

async function askAI(message){

const response = await fetch(
"https://api.openai.com/v1/chat/completions",
{
method:"POST",
headers:{
"Content-Type":"application/json",
"Authorization":"Bearer YOUR_API_KEY"
},
body:JSON.stringify({
model:"gpt-4o-mini",
messages:[
{
role:"user",
content:message
}
]
})
});

const data = await response.json();

return data.choices[0].message.content;

}
*/

</script>

</body>
</html>
