<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Sorry Sejal Didi</title>

<style>
body{
  margin:0;
  height:100vh;
  font-family:'Segoe UI',sans-serif;
  background:linear-gradient(135deg,#ff9a9e,#fad0c4);
  display:flex;
  align-items:center;
  justify-content:center;
  overflow:hidden;
}

.card{
  background:rgba(255,255,255,0.95);
  padding:40px;
  border-radius:20px;
  text-align:center;
  max-width:460px;
  box-shadow:0 10px 30px rgba(0,0,0,0.25);
  z-index:2;
}

h1{color:#e63946;}

p{font-size:18px;line-height:1.6;color:#333;}

.quote{font-style:italic;color:#555;}

.buttons{margin-top:25px;position:relative;height:60px;}

button{
  padding:12px 25px;
  font-size:16px;
  border:none;
  border-radius:30px;
  cursor:pointer;
  position:absolute;
}

.yes{background:#ff4d6d;color:#fff;left:90px;}
.no{background:#adb5bd;color:#fff;left:240px;}

.heart{
  position:fixed;
  font-size:22px;
  animation:fall linear forwards;
  z-index:1;
}

@keyframes fall{
  to{transform:translateY(110vh);opacity:0;}
}

/* 🎀 Rakhi */
.rakhi{
  position:fixed;
  top:-40px;
  font-size:30px;
  animation:rakhiFall 6s linear infinite;
  opacity:0.9;
}

@keyframes rakhiFall{
  to{transform:translateY(110vh) rotate(360deg);}
}

/* 💌 Popup */
.popup{
  position:fixed;
  top:0;left:0;
  width:100%;height:100%;
  background:rgba(0,0,0,0.5);
  display:flex;
  align-items:center;
  justify-content:center;
  z-index:5;
}

.popup-content{
  background:white;
  padding:30px;
  border-radius:20px;
  text-align:center;
  max-width:350px;
}
</style>
</head>

<body>

<!-- 🎵 Music -->
<audio id="bgMusic" autoplay loop>
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_2b3b9f43c3.mp3">
</audio>

<div class="card">
  <h1>Sorry Sejal Didi 💖</h1>

  <p>
    I’m really sorry didi…<br>
    Please forgive me.<br>
    Love you always 💕
  </p>

  <p class="quote">
    “A sister’s love is a lifelong blessing.” 🌸
  </p>

  <p><strong>Will you forgive me?</strong></p>

  <div class="buttons">
    <button class="yes" onclick="yesClicked()">Yes</button>
    <button class="no" id="noBtn" onmouseover="moveNo()">No</button>
  </div>
</div>

<script>
// autoplay fix
document.body.addEventListener('click',()=>{
  document.getElementById("bgMusic").play();
},{once:true});

function moveNo(){
  const b=document.getElementById("noBtn");
  b.style.left=Math.random()*280+"px";
  b.style.top=Math.random()*30+"px";
}

function yesClicked(){
  spellText("LOVE YOU SEJAL");
  startRakhi();
  setTimeout(showPopup,3000);
}

function spellText(text){
  const letters=text.split("");
  const startX=window.innerWidth/2-(letters.length*25);

  letters.forEach((l,i)=>{
    if(l===" ") return;
    for(let j=0;j<15;j++){
      const h=document.createElement("div");
      h.className="heart";
      h.innerHTML="❤️";
      h.style.left=startX+i*35+Math.random()*15+"px";
      h.style.top="-20px";
      h.style.animationDuration=2+Math.random()*2+"s";
      document.body.appendChild(h);
      setTimeout(()=>h.remove(),5000);
    }
  });
}

function startRakhi(){
  for(let i=0;i<8;i++){
    const r=document.createElement("div");
    r.className="rakhi";
    r.innerHTML="🎀";
    r.style.left=Math.random()*100+"vw";
    r.style.animationDuration=5+Math.random()*3+"s";
    document.body.appendChild(r);
  }
}

function showPopup(){
  const pop=document.createElement("div");
  pop.className="popup";
  pop.innerHTML=`
    <div class="popup-content">
      <h2>💖 Thank you Sejal Didi 💖</h2>
      <p>
        I knew you’d forgive me.<br>
        You are the best sister ever 🫶<br><br>
        Love you always 🌸
      </p>
    </div>`;
  document.body.appendChild(pop);
}
</script>

</body>
</html>