<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Happy Birthday My Love 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
:root{
  --rose:#ff6f91;
  --pink:#ffe6ef;
  --deep:#b8325a;
  --text:#5a2a35;
}

/* BASIC RESET */
body, html{
  margin:0; padding:0;
  height:100%;
  font-family:"Segoe UI", system-ui, sans-serif;
  overflow-x:hidden;
  background:linear-gradient(135deg,#ffeef4,#ffd1dc);
  color:var(--text);
}

/* CONTAINER FOR PAGES */
.page{
  width:100%;
  height:100vh;
  position:absolute;
  top:0;
  left:0;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  padding:30px;
  text-align:center;
  transition:opacity 1s, transform 1s;
  opacity:0;
  pointer-events:none;
}

/* VISIBLE PAGE */
.page.active{
  opacity:1;
  pointer-events:auto;
}

/* CARD */
.card{
  width:340px;
  height:460px;
  perspective:1400px;
  cursor:pointer;
  margin-bottom:20px;
}

.card-inner{
  width:100%;
  height:100%;
  position:relative;
  transform-style:preserve-3d;
  transition:transform 1.2s;
}

.card.open .card-inner{
  transform:rotateY(180deg);
}

.face{
  position:absolute;
  inset:0;
  border-radius:26px;
  backface-visibility:hidden;
  box-shadow:0 30px 70px rgba(0,0,0,.25);
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  padding:32px;
  background:var(--pink);
}

.front{
  background:linear-gradient(180deg,#fff,#ffe9f1);
}

.front h1{
  font-weight:600;
}

.front span{
  margin-top:10px;
  font-size:14px;
  opacity:.7;
}

.back{
  transform:rotateY(180deg);
}

.back h2{
  color:var(--rose);
  font-size:22px;
}

.back p{
  margin-top:10px;
  line-height:1.8;
}

/* BUTTONS */
.btn{
  margin-top:20px;
  padding:10px 20px;
  border:none;
  border-radius:25px;
  background:#fff;
  font-size:14px;
  cursor:pointer;
  box-shadow:0 10px 25px rgba(0,0,0,.15);
  transition:.3s;
}

.btn:hover{
  transform:translateY(-3px);
}

/* ANIMATIONS */
.heart{
  position:absolute;
  font-size:18px;
  animation:float 8s linear forwards;
  opacity:.8;
}

@keyframes float{
  from{transform:translateY(110vh);}
  to{transform:translateY(-150px);}
}
</style>
</head>

<body>

<!-- PAGE 1: CARD -->
<div class="page active" id="page1">
  <div class="card" onclick="toggleCard()">
    <div class="card-inner">
      <div class="face front">
        <h1>Happy Birthday 🎂</h1>
        <span>Tap to open 💕</span>
      </div>
      <div class="face back">
        <h2>Debashis 💖</h2>
        <p>You are my smile, my peace, my everything.</p>
        <button class="btn" onclick="goToPage(2)">Our Story →</button>
      </div>
    </div>
  </div>
</div>

<!-- PAGE 2: Our Story -->
<div class="page" id="page2">
  <h2>Our Story 📖</h2>
  <p>From the moment we met, every day became brighter.</p>
  <p>We laughed, we dreamed, we grew together 💕</p>
  <button class="btn" onclick="goToPage(3)">Why I Love You →</button>
</div>

<!-- PAGE 3: Why I Love You -->
<div class="page" id="page3">
  <h2>Why I Love You 💖</h2>
  <p>💗 Your smile lights up my world</p>
  <p>💗 Your hug feels like home</p>
  <p>💗 Your heart is pure magic</p>
  <button class="btn" onclick="goToPage(4)">Birthday Wishes →</button>
</div>

<!-- PAGE 4: Wishes -->
<div class="page" id="page4">
  <h2>Happy Birthday My Love 🎉</h2>
  <p>May this year bring you endless joy, laughter, and love.</p>
  <p>You are my forever and always 🥰</p>
  <button class="btn" onclick="goToPage(1)">Back to Start</button>
</div>

<script>
const hearts=["💗","💖","💕","💞"];

// Card toggle hearts
function toggleCard(){
  document.querySelector(".card").classList.toggle("open");
  for(let i=0;i<10;i++) spawnHeart();
}

function spawnHeart(){
  const h=document.createElement("div");
  h.className="heart";
  h.innerText=hearts[Math.floor(Math.random()*hearts.length)];
  h.style.left=Math.random()*100+"vw";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),8000);
}

// Page navigation
function goToPage(n){
  document.querySelectorAll(".page").forEach(p=>{
    p.classList.remove("active");
  });
  document.getElementById("page"+n).classList.add("active");
}

// Continuous hearts
setInterval(spawnHeart,1500);
</script>

</body>
</html>
