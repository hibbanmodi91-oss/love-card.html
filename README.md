<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For Hifza 💗</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&family=Great+Vibes&display=swap" rel="stylesheet">

<style>
  body {
    margin: 0;
    height: 100vh;
    overflow: hidden;
    background: linear-gradient(135deg, #ffb6c1, #ff69b4);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Poppins', sans-serif;
  }

  .blur {
    filter: blur(8px);
    pointer-events: none;
  }

  .lock-screen {
    position: absolute;
    background: white;
    padding: 30px;
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 12px 35px rgba(0,0,0,0.25);
    z-index: 5;
  }

  .lock-screen h2 { color: #ff4d6d; }

  .lock-screen input {
    padding: 10px;
    width: 200px;
    border-radius: 10px;
    border: 1px solid #ccc;
    text-align: center;
    font-size: 16px;
  }

  .lock-screen button {
    margin-top: 12px;
    padding: 8px 18px;
    border: none;
    background: #ff4d6d;
    color: white;
    border-radius: 20px;
    cursor: pointer;
  }

  .envelope {
    width: 280px;
    height: 180px;
    background: #ff4d6d;
    position: relative;
    border-radius: 10px;
    cursor: pointer;
    display: none;
    z-index: 4;
  }

  .envelope .flap {
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 0;
    border-left: 140px solid transparent;
    border-right: 140px solid transparent;
    border-bottom: 90px solid #ff7a8a;
    transform-origin: top;
    transition: transform 1s ease;
  }

  .envelope.open .flap {
    transform: rotateX(180deg);
  }

  .open-text {
    position: absolute;
    bottom: 12px;
    width: 100%;
    text-align: center;
    color: white;
    font-weight: 600;
  }

  .countdown {
    position: absolute;
    font-size: 48px;
    color: white;
    font-weight: bold;
    display: none;
    z-index: 6;
  }

  .card {
    background: white;
    width: 360px;
    padding: 26px;
    border-radius: 22px;
    text-align: center;
    box-shadow: 0 14px 40px rgba(0,0,0,0.25);
    display: none;
    animation: openLetter 1.2s ease;
    z-index: 3;
  }

  @keyframes openLetter {
    from { transform: scaleY(0); opacity: 0; }
    to { transform: scaleY(1); opacity: 1; }
  }

  .from-name { font-size: 14px; color: #777; }
  .heart-main { font-size: 42px; animation: beat 1s infinite; }

  @keyframes beat {
    0%,100% { transform: scale(1); }
    50% { transform: scale(1.25); }
  }

  .to-name {
    font-family: 'Great Vibes', cursive;
    font-size: 42px;
    color: #ff4d6d;
    min-height: 50px;
  }

  p {
    color: #444;
    font-size: 15px;
    line-height: 1.65;
    text-align: left;
  }

  .reveal-btn {
    margin-top: 14px;
    padding: 8px 18px;
    border: none;
    background: #ff4d6d;
    color: white;
    border-radius: 20px;
    cursor: pointer;
  }

  .secret {
    display: none;
    margin-top: 14px;
    font-weight: 600;
    color: #ff4d6d;
    text-align: center;
  }

  .shayari {
    margin-top: 10px;
    font-style: italic;
    color: #666;
  }

  .falling-heart {
    position: absolute;
    top: -40px;
    animation: fall linear infinite;
  }

  @keyframes fall {
    to { transform: translateY(110vh) rotate(360deg); }
  }
</style>
</head>

<body>

<div class="lock-screen" id="lockScreen">
  <h2>🔒 Enter the date</h2>
  <input type="text" id="password" placeholder="DD/MM/YYYY">
  <br>
  <button onclick="checkPassword()">Unlock 💗</button>
</div>

<div class="envelope" id="envelope" onclick="openEnvelope()">
  <div class="flap"></div>
  <div class="open-text">Tap to open 💌</div>
</div>

<div class="countdown" id="countdown"></div>

<audio id="bgMusic" loop>
  <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_2c2c7a1e63.mp3">
</audio>

<div class="card" id="card" onclick="playMusic()">
  <div class="from-name">From Hibbaan</div>
  <div class="heart-main">💗</div>
  <div class="to-name" id="typingName"></div>

  <p>
    This isn’t just a message — it’s a quiet truth I’ve carried in my heart for a long time.
    Some feelings don’t need noise or drama; they grow silently, becoming deeper with time.
    That’s how my feelings for you feel — calm, honest, and real.
    <br><br>
    Your voice has a softness that brings peace. It’s the kind of voice that makes moments
    feel lighter and conversations feel meaningful. And your kindness — it shows in the
    smallest things you do, in the way you care, and in the way you understand others.
    <br><br>
    Your eyes… they shine like diamonds — rare, pure, and beautiful in a way words can’t
    fully explain. There’s depth in them, a quiet magic that stays with me long after.
    <br><br>
    I don’t know what the future holds, and I don’t want to rush anything.
    I just want you to know that my feelings are genuine, respectful, and true —
    something I value deeply and hold with care.
  </p>

  <button class="reveal-btn" onclick="revealMsg(event)">Tap for a secret 💌</button>

  <div class="secret" id="secretMsg">
    I love you 💓 as deep as Osian — endless, calm, and timeless.
    <div class="shayari">
      “Some love grows silently,<br>
      some hearts connect deeply,<br>
      and some feelings stay forever.”
    </div>
  </div>
</div>

<script>
  function checkPassword() {
    if (password.value === "11/4/2011") {
      lockScreen.style.display = "none";
      envelope.style.display = "block";
    } else {
      alert("Wrong password 💔");
    }
  }

  function openEnvelope() {
    envelope.classList.add("open");
    setTimeout(startCountdown, 1000);
  }

  function startCountdown() {
    envelope.style.display = "none";
    let count = 3;
    countdown.style.display = "block";
    countdown.innerText = count;

    const timer = setInterval(() => {
      count--;
      if (count === 0) {
        clearInterval(timer);
        countdown.style.display = "none";
        card.style.display = "block";
        typeName();
      } else {
        countdown.innerText = count;
      }
    }, 1000);
  }

  function playMusic() {
    bgMusic.play();
  }

  function revealMsg(e) {
    e.stopPropagation();
    secretMsg.style.display = "block";
  }

  const nameText = "Hifza";
  let i = 0;
  function typeName() {
    if (i < nameText.length) {
      typingName.innerHTML += nameText.charAt(i);
      i++;
      setTimeout(typeName, 180);
    }
  }

  function createHeart() {
    const heart = document.createElement("div");
    heart.className = "falling-heart";
    heart.innerHTML = "💗";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = (16 + Math.random() * 14) + "px";
    heart.style.animationDuration = (3 + Math.random() * 4) + "s";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 7000);
  }

  setInterval(createHeart, 350);
</script>

</body>
</html>
