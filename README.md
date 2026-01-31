# Scam
Princess
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Be My Valentine 💖</title>
<style>
  /* Full screen setup */
  body {
    height: 100vh;
    margin: 0;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(135deg, #ff9a9e, #fad0c4);
    font-family: 'Comic Sans MS', cursive, sans-serif;
    position: relative;
  }

  /* Central container */
  .container {
    text-align: center;
    background: white;
    padding: 50px;
    border-radius: 20px;
    box-shadow: 0 15px 40px rgba(0,0,0,0.3);
    z-index: 10;
    position: relative;
    overflow: hidden;
  }

  h1 {
    color: #ff2e63;
    font-size: 40px;
    margin-bottom: 30px;
    text-shadow: 2px 2px 5px rgba(255,0,100,0.5);
  }

  button {
    padding: 15px 30px;
    font-size: 20px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    margin: 15px;
    transition: transform 0.2s, background 0.3s;
  }

  #yes {
    background-color: #ff2e63;
    color: white;
  }

  #yes:hover {
    transform: scale(1.1);
    box-shadow: 0 5px 15px rgba(255,46,99,0.6);
  }

  #no {
    background-color: #444;
    color: white;
    position: absolute;
    animation: shake 0.5s infinite;
  }

  @keyframes shake {
    0% { transform: translateX(0); }
    25% { transform: translateX(-4px); }
    50% { transform: translateX(4px); }
    75% { transform: translateX(-4px); }
    100% { transform: translateX(0); }
  }

  #message {
    font-size: 32px;
    color: #ff2e63;
    margin-top: 20px;
    display: none;
  }

  /* Floating hearts */
  .heart {
    position: fixed;
    bottom: -20px;
    font-size: 24px;
    animation: floatUp 5s linear infinite;
    opacity: 0.9;
  }

  @keyframes floatUp {
    0% { transform: translateY(0) scale(1); opacity: 1; }
    100% { transform: translateY(-100vh) scale(1.5); opacity: 0; }
  }

  /* Confetti */
  .confetti {
    position: fixed;
    width: 10px;
    height: 10px;
    background-color: red;
    opacity: 0.8;
    pointer-events: none;
    z-index: 5;
    border-radius: 50%;
    animation: fall 4s linear forwards;
  }

  @keyframes fall {
    0% { transform: translateY(0) rotate(0deg); }
    100% { transform: translateY(100vh) rotate(360deg); }
  }

  /* Typing effect */
  .typing {
    border-right: .15em solid #ff2e63;
    white-space: nowrap;
    overflow: hidden;
    font-size: 30px;
    color: #ff2e63;
    margin-top: 20px;
  }

</style>
</head>

<body>

<div class="container" id="box">
  <h1>Will you be my Valentine? 💖</h1>
  <button id="yes">Yes</button>
  <button id="no">No</button>
  <div id="message" class="typing"></div>
</div>

<!-- Sound Effects -->
<audio id="applause">
  <source src="https://www.soundjay.com/human/sounds/applause-8.mp3" type="audio/mpeg">
</audio>
<audio id="romantic">
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<script>
  const noBtn = document.getElementById("no");
  const yesBtn = document.getElementById("yes");
  const message = document.getElementById("message");
  const applause = document.getElementById("applause");
  const romantic = document.getElementById("romantic");

  // Move the No button
  function moveNoButton() {
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 50);
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
  }
  noBtn.addEventListener("mouseover", moveNoButton);
  noBtn.addEventListener("click", moveNoButton);
  noBtn.addEventListener("touchstart", moveNoButton);

  // Typing effect for message
  function typeMessage(text, element, speed = 100) {
    let i = 0;
    element.innerHTML = "";
    element.style.display = "block";
    const interval = setInterval(() => {
      element.innerHTML += text[i];
      i++;
      if(i >= text.length) clearInterval(interval);
    }, speed);
  }

  yesBtn.addEventListener("click", () => {
    yesBtn.style.display = "none";
    noBtn.style.display = "none";
    typeMessage("🎉 Congratulations Tasmia, you are my Valentine 💘", message);
    applause.play();
    romantic.play();
    createConfetti();
  });

  // Floating hearts generator
  setInterval(() => {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.innerHTML = "❤️";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (3 + Math.random() * 3) + "s";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 6000);
  }, 300);

  // Confetti generator
  function createConfetti() {
    for(let i=0;i<150;i++){
      const confetti = document.createElement("div");
      confetti.className = "confetti";
      confetti.style.left = Math.random() * window.innerWidth + "px";
      confetti.style.backgroundColor = `hsl(${Math.random()*360},70%,60%)`;
      confetti.style.animationDuration = (2 + Math.random()*3) + "s";
      document.body.appendChild(confetti);
      setTimeout(() => confetti.remove(), 5000);
    }
  }

</script>
</body>
</html>
