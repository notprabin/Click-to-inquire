<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Chocolate Day 🍫</title>

<style>
body{
margin:0;
background:maroon;
color:#000;
font-family:Arial;
overflow:hidden;
text-align:center;
}

/* screens */
.screen{
position:absolute;
width:100%;
height:100%;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
z-index:3;
}

.hidden{display:none;}

button{
background:pink;
border:none;
padding:12px 25px;
margin:10px;
border-radius:8px;
font-size:18px;
cursor:pointer;
}

#name{
font-size:32px;
font-weight:bold;
animation:pulse 1.5s infinite;
}

/* pulse effect */
@keyframes pulse{
0%{transform:scale(1);}
50%{transform:scale(1.15);}
100%{transform:scale(1);}
}

/* floating items */
.float{
position:absolute;
font-size:26px;
animation:up 4s linear;
}

.sparkle{
position:absolute;
font-size:14px;
animation:spark 2s linear;
}

.fire{
position:absolute;
font-size:30px;
animation:boom 1.5s ease-out;
}

.chocoPop{
position:absolute;
font-size:70px;
top:30%;
left:50%;
transform:translateX(-50%);
animation:pop 1.5s ease-out;
z-index:10;
}

/* permanent chocolates */
.bg{
position:fixed;
font-size:28px;
opacity:.35;
z-index:0;
}

/* animations */
@keyframes up{
from{transform:translateY(0);opacity:1;}
to{transform:translateY(-120vh);opacity:0;}
}

@keyframes spark{
from{opacity:1;transform:scale(1);}
to{opacity:0;transform:scale(2);}
}

@keyframes boom{
from{opacity:1;transform:scale(.2);}
to{opacity:0;transform:scale(2);}
}

@keyframes pop{
from{transform:translateX(-50%) scale(.2);}
to{transform:translateX(-50%) scale(1.2);}
}
</style>
</head>

<body>

<audio id="music" loop>
<source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3">
</audio>

<script>
// permanent chocolate background
for(let i=0;i<40;i++){
let b=document.createElement("div");
b.className="bg";
b.innerText="🍫";
b.style.left=Math.random()*100+"vw";
b.style.top=Math.random()*100+"vh";
document.body.appendChild(b);
}
</script>

<!-- PAGE 1 -->
<div id="s1" class="screen">
<h1>Happy Chocolate Day 🍫</h1>
<h2 id="name">Jenika 💖</h2>
<button onclick="start()">YES</button>
</div>

<!-- PAGE 2 -->
<div id="s2" class="screen hidden">
<h1>Jenika my love, do you want chocolate? 🍫❤️</h1>
<button id="yes" onclick="yes()">YES</button>
<button id="no" onclick="no()">NO</button>
<p id="msg"></p>
</div>

<!-- PAGE 3 -->
<div id="s3" class="screen hidden">
<h1>I have asked your Sister Sushila to give it to you Enjoy My Love 😄</h1>
<h2>Enjoy 💗💗</h2>
<h3>Lots of love, even though we’re far ❤️</h3>
</div>

<script>
const music = document.getElementById("music");
const s1 = document.getElementById("s1");
const s2 = document.getElementById("s2");
const s3 = document.getElementById("s3");
const yesBtn = document.getElementById("yes");
const noBtn = document.getElementById("no");
const msg = document.getElementById("msg");

let yesClicks = 0;
let yesScale = 1;
let noScale = 1;

function start(){
music.play();
s1.classList.add("hidden");
s2.classList.remove("hidden");
}

function yes(){
yesClicks++;

yesScale -= 0.2;
if(yesScale < 0.4) yesScale = 0.4;

yesBtn.style.transform = `
scale(${yesScale})
translate(${Math.random()*700 - 350}px, ${Math.random()*700 - 350}px)
`;

noScale += 0.25;
noBtn.style.transform = `scale(${noScale})`;

msg.innerText = "Are you sure? 😳🍫";

if(yesClicks >= 3){
setTimeout(()=>{
s2.classList.add("hidden");
s3.classList.remove("hidden");
fireworks();
chocoPop();
},500);
}
}

function no(){
msg.innerText="Come on… just one chocolate? 🥺🍫";
}

/* floating hearts */
setInterval(()=>{
let h=document.createElement("div");
h.className="float";
h.innerText="❤️";
h.style.left=Math.random()*100+"vw";
h.style.top="100vh";
document.body.appendChild(h);
setTimeout(()=>h.remove(),4000);
},700);

/* floating chocolates */
setInterval(()=>{
let c=document.createElement("div");
c.className="float";
c.innerText="🍫";
c.style.left=Math.random()*100+"vw";
c.style.top="100vh";
document.body.appendChild(c);
setTimeout(()=>c.remove(),4000);
},900);

/* sparkles */
setInterval(()=>{
let s=document.createElement("div");
s.className="sparkle";
s.innerText="✨";
s.style.left=Math.random()*100+"vw";
s.style.top=Math.random()*100+"vh";
document.body.appendChild(s);
setTimeout(()=>s.remove(),2000);
},500);

/* fireworks */
function fireworks(){
for(let i=0;i<20;i++){
let f=document.createElement("div");
f.className="fire";
f.innerText="🎆";
f.style.left=Math.random()*100+"vw";
f.style.top=Math.random()*100+"vh";
document.body.appendChild(f);
setTimeout(()=>f.remove(),1500);
}
}

/* chocolate pop */
function chocoPop(){
let c=document.createElement("div");
c.className="chocoPop";
c.innerText="🍫";
document.body.appendChild(c);
setTimeout(()=>c.remove(),2000);
}
</script>

</body>
</html>
