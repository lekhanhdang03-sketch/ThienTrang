<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Chúc Nguyễn Đặng Thiên Trang 20/10 💖</title>
<style>
body {
  margin: 0;
  font-family: "Comic Sans MS", cursive, sans-serif;
  text-align: center;
  color: #333;
  background: #fff0f5;
  overflow-x: hidden;
}

/* Intro */
#intro {
  position: fixed;
  top:0; left:0; width:100%; height:100%;
  background: linear-gradient(135deg, #ff0000, #000000);
  color: white;
  display: flex; flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index:10;
}
#intro h1 {
  font-size: 2.5rem;
  color: yellow;
  text-shadow: 2px 2px 5px black;
  animation: pulse 1s infinite alternate;
}
#intro p { font-size:1.2rem; margin-top:1rem; }
.intro-btn {
  margin:1rem;
  padding:0.8rem 1.5rem;
  border:none;
  background: yellow;
  color:red;
  font-size:1rem;
  cursor:pointer;
  border-radius:20px;
  transition:0.3s;
}
.intro-btn:hover { background: #fff59d; }
@keyframes pulse { from{opacity:0.5;} to{opacity:1;} }

/* Flash bùng nổ */
#flash {
  position: fixed;
  top:0; left:0; width:100%; height:100%;
  background: white;
  opacity:0;
  z-index:15;
  pointer-events:none;
}

/* Hearts */
.heart {
  position: fixed;
  font-size: 2rem;
  color: pink;
  animation: fly 5s linear forwards;
}
@keyframes fly {
  0% { transform: translateY(0) scale(1); opacity:1; }
  100% { transform: translateY(-800px) scale(2); opacity:0; }
}

/* Main Chúc */
#main {
  position: relative; /* để nút tiếp theo góc phải */
  display:none;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  min-height:100vh;
  padding:20px;
  border-radius:20px;
  margin:10px;
  box-shadow:0 0 20px rgba(255,192,203,0.5);
}
#main h2 { font-size:2rem; margin-bottom:20px; color:#ff4081; }
#main p { font-size:1.2rem; line-height:1.6; max-width:90%; color:#555; }

#nextBtn {
  position: absolute;
  top: 20px;
  right: 20px;
  padding: 10px 20px;
  border: none;
  background: #ff1493;
  color: white;
  font-size: 1.2rem;
  border-radius: 20px;
  cursor: pointer;
  box-shadow: 0 5px 15px rgba(255,20,147,0.5);
  transition: 0.3s;
}
#nextBtn:hover {
  background: #ff69b4;
  transform: scale(1.05);
}

/* Message động nổi bật */
#message {
  position: fixed;
  top:50%; left:50%;
  transform: translate(-50%,-50%);
  font-size:3rem;
  color: #ff1493;
  text-shadow: 2px 2px 10px #ff69b4, 0 0 20px #ff69b4;
  display:none;
  z-index:20;
  animation: bounce 0.6s infinite alternate, glow 1s infinite alternate;
}
@keyframes bounce {
  from { transform: translate(-50%, -50%) scale(1); }
  to { transform: translate(-50%, -50%) scale(1.2); }
}
@keyframes glow {
  from { text-shadow: 2px 2px 10px #ff69b4, 0 0 20px #ff69b4; }
  to { text-shadow: 4px 4px 15px #ff1493, 0 0 30px #ff1493; }
}

/* Câu hỏi */
#question-section {
  margin-top:30px;
}
#question { font-size:1.4rem; margin:20px 0; }
.choice-btn {
  margin:10px;
  padding:10px 20px;
  border:none;
  background: #ff79a8;
  color:white;
  font-size:1.1rem;
  border-radius:15px;
  cursor:pointer;
  transition:0.3s;
}
.choice-btn:hover { background:#ff4081; }
</style>
</head>
<body>

<div id="flash"></div> <!-- Flash bùng nổ -->

<!-- Intro -->
<div id="intro">
  <h1>⚠️ CẢNH BÁO 🔞 ⚠️</h1>
  <p>Bạn có muốn tiếp tục không?</p>
  <div>
    <button class="intro-btn" onclick="showMain()">Yes</button>
    <button class="intro-btn" onclick="showMain()">OK</button>
  </div>
</div>

<!-- Main Chúc + Nút -->
<div id="main">
  <br>
  <h2>💐 Chúc mừng ngày 20/10 💐</h2>
  <p>Gửi đến Nguyễn Đặng Thiên Trang — chiếc l đáng yêu nhất!<br>
  Chúc chị bé ngày 20/10 thật xinh đẹp, hạnh phúc và luôn mỉm cười, chị cười xinh vãi ò😭😁<br>
  Mong mọi điều tốt đẹp nhất sẽ đến với chị,<br>
  và luôn có một người bên cạnh quan tâm, thương chị mỗi ngày.<br>
  Bạn nhỏ này tuy hơi “phiền”, nhưng thương chị thiệt lòng lắm đó 💖<br>
  <b>Yêu chị 3000 🌹</b></p>
  <button id="nextBtn" onclick="showQuestion()">➡️ Tiếp theo</button>
</div>

<!-- Message động -->
<div id="message">Hehe, biết ngay mà! Em cũng yêu chị bé lắm 💖</div>

<!-- Nhạc -->
<audio id="bgMusic" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_dae0cbe3d9.mp3?filename=romantic-background-music-110734.mp3" loop></audio>

<script>
const intro = document.getElementById("intro");
const main = document.getElementById("main");
const nextBtn = document.getElementById("nextBtn");
const message = document.getElementById("message");
const music = document.getElementById("bgMusic");
const flash = document.getElementById("flash");

function showMain(){
  intro.style.display="none";
  flashEffect();
  setTimeout(()=>{
    main.style.display="flex";
    music.play().catch(()=>{});
    createHearts(60);
  },300);
}

function flashEffect(){
  flash.style.opacity = 1;
  for(let i=0;i<100;i++){
    const heart = document.createElement("div");
    heart.className="heart";
    heart.innerText="💖";
    heart.style.left=Math.random()*window.innerWidth+"px";
    heart.style.top=Math.random()*window.innerHeight+"px";
    heart.style.fontSize=(Math.random()*40+20)+"px";
    document.body.appendChild(heart);
    setTimeout(()=>heart.remove(),800);
  }
  setTimeout(()=>{ flash.style.opacity=0; },300);
}

function showQuestion(){
  main.innerHTML = `
    <div id="question-section">
      <div id="question">Chị bé có muốn cùng em vui vẻ lâu ơi là lâu nữa không? 💕</div>
      <div>
        <button class="choice-btn" onclick="showLoveMessage()">Có</button>
        <button class="choice-btn" id="noBtn" onclick="moveNo()">Không</button>
        <button class="choice-btn" onclick="showLoveMessage()">Ok</button>
        <button class="choice-btn" onclick="showLoveMessage()">Yes</button>
      </div>
    </div>
  `;
}

function createHearts(count){
  for(let i=0;i<count;i++){
    const heart = document.createElement("div");
    heart.className="heart";
    heart.innerText="💖";
    heart.style.left=Math.random()*window.innerWidth+"px";
    heart.style.top=Math.random()*window.innerHeight+"px";
    heart.style.fontSize=Math.random()*30+10+"px";
    document.body.appendChild(heart);
    setTimeout(()=>heart.remove(),5000);
  }
}

// Nút Không chạy trốn
function moveNo(){
  const x=Math.random()*(window.innerWidth-100);
  const y=Math.random()*(window.innerHeight-50);
  const btn = document.getElementById("noBtn");
  btn.style.position="fixed";
  btn.style.left=x+"px";
  btn.style.top=y+"px";
}

// Hiển thị message nổi bật + tim thưa
function showLoveMessage(){
  main.style.display="none";
  message.style.display="block";
  startInfiniteHearts(2); // mỗi lần 2 trái tim
}

// Tim bay thưa
function startInfiniteHearts(count=2){
  setInterval(()=>{
    for(let i=0;i<count;i++){
      const heart = document.createElement("div");
      heart.className="heart";
      heart.innerText="💖";
      heart.style.left=Math.random()*window.innerWidth+"px";
      heart.style.top=window.innerHeight+"px";
      heart.style.fontSize=(Math.random()*30+10)+"px";
      document.body.appendChild(heart);
      setTimeout(()=>heart.remove(),5000);
    }
  },800);
}
</script>
</body>
</html>
