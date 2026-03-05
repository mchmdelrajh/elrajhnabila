<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday</title>

<style>
body{
margin:0;
font-family:'Segoe UI',sans-serif;
background:linear-gradient(135deg,#ff9a9e,#fad0c4);
text-align:center;
overflow-x:hidden;
color:white;
}

.hero{
padding:80px 20px 40px;
}

.name{
font-size:60px;
font-weight:bold;
text-shadow:0 5px 15px rgba(0,0,0,0.3);
}

.subtitle{
font-size:22px;
margin-top:10px;
}

.countdown{
font-size:28px;
margin-top:20px;
font-weight:bold;
}

button{
margin-top:25px;
background:#ff4b7d;
border:none;
padding:14px 28px;
font-size:16px;
border-radius:30px;
color:white;
cursor:pointer;
box-shadow:0 10px 20px rgba(0,0,0,0.2);
}

.message{
background:white;
color:#333;
margin:40px auto;
max-width:700px;
padding:35px;
border-radius:20px;
box-shadow:0 10px 30px rgba(0,0,0,0.2);
display:none;
}

.gallery{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
gap:15px;
padding:30px;
max-width:900px;
margin:auto;
}

.gallery img{
width:100%;
height:240px;
object-fit:cover;
border-radius:15px;
box-shadow:0 10px 20px rgba(0,0,0,0.25);
transition:0.3s;
}

.gallery img:hover{
transform:scale(1.05);
}

footer{
padding:30px;
font-size:14px;
}

/* sakura */
.sakura{
position:fixed;
top:-10px;
font-size:18px;
animation:fall linear forwards;
}

@keyframes fall{
to{
transform:translateY(110vh) rotate(360deg);
opacity:0;
}
}

/* fireworks canvas */
#fireworks{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
pointer-events:none;
}

</style>
</head>

<body>

<canvas id="fireworks"></canvas>

<audio id="music" loop>
<source src="happybirthday.mp3" type="audio/mpeg">
</audio>

<div class="hero">

<div class="name">INTAN NABILA</div>

<div class="subtitle">Selamat Ulang Tahun 🎉</div>

<div class="countdown" id="countdown"></div>

<button onclick="showMessage()">Buka Pesan ❤️</button>

</div>

<div class="message" id="birthdayMessage">

<h2>Happy Birthday ❤️</h2>

<p>
Hari ini adalah hari spesial karena dunia pernah menghadirkan seseorang yang sangat berarti bagiku.
</p>

<p>
Terima kasih sudah hadir di hidupku, membawa tawa, cerita, dan banyak kenangan indah.
</p>

<p>
Semoga di umurmu yang baru ini kamu selalu diberi kesehatan, kebahagiaan, dan semua impianmu bisa tercapai.
</p>

<p>
Aku harap kita bisa terus membuat banyak kenangan indah bersama.
</p>

<h3>I Love You ❤️</h3>

</div>

<h2>Foto-Foto Kamu 📸</h2>

<div class="gallery">
<img src="foto/IMG_0472.PNG">
<img src="foto/IMG_0739 (1).WEBP">
<img src="foto/image.png">
<img src="foto/image copy.png">
</div>

<footer>
Dibuat dengan sepenuh hati oleh pacar mu (elrajh)❤️
</footer>

<script>

function showMessage(){
 document.getElementById("birthdayMessage").style.display="block";
 document.getElementById("music").play();
}

/* COUNTDOWN */
const targetDate = new Date("March 8, 2026 00:00:00").getTime();

setInterval(function(){

const now = new Date().getTime();
const distance = targetDate - now;

const days = Math.floor(distance / (1000*60*60*24));
const hours = Math.floor((distance%(1000*60*60*24))/(1000*60*60));
const minutes = Math.floor((distance%(1000*60*60))/(1000*60));
const seconds = Math.floor((distance%(1000*60))/1000);

if(distance > 0){
 document.getElementById("countdown").innerHTML =
 "Menuju ulang tahun: " + days+"h " + hours+"j " + minutes+"m " + seconds+"d";
}else{
 document.getElementById("countdown").innerHTML = "Hari ini ulang tahunmu 🎂";
}

},1000);

/* SAKURA */
function createSakura(){

const sakura = document.createElement("div");

sakura.classList.add("sakura");

sakura.innerHTML = "🌸";

sakura.style.left = Math.random()*100 + "vw";

sakura.style.animationDuration = (Math.random()*4 + 4) + "s";

sakura.style.fontSize = (Math.random()*15 + 10) + "px";


document.body.appendChild(sakura);

setTimeout(()=>{

sakura.remove();

},8000);

}

setInterval(createSakura,400);

/* SIMPLE FIREWORKS */
const canvas = document.getElementById("fireworks");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

function firework(){

let x = Math.random()*canvas.width;
let y = Math.random()*canvas.height/2;

for(let i=0;i<50;i++){

ctx.beginPath();
ctx.arc(x + Math.random()*80-40, y + Math.random()*80-40, 2, 0, Math.PI*2);
ctx.fillStyle = "white";
ctx.fill();

}

}

setInterval(firework,800);

</script>

</body>
</html>
