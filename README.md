<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday Kesiya! 🎉</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      text-align: center;
      color: #fff;
      overflow: hidden;
      padding: 20px;
    }
    h1, h2 { margin: 10px 0; }
    .game, .question, .wish, .message {
      background: rgba(255, 255, 255, 0.2);
      padding: 20px;
      border-radius: 20px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.2);
      margin-top: 20px;
      max-width: 400px;
      width: 100%;
      z-index: 2;
      position: relative;
    }
    button {
      padding: 10px 20px;
      background: #ff6b6b;
      border: none;
      color: white;
      font-size: 18px;
      border-radius: 10px;
      cursor: pointer;
      transition: transform 0.2s;
    }
    button:hover {
      transform: scale(1.1);
      background: #ff4757;
    }
    input {
      padding: 10px;
      border-radius: 10px;
      border: none;
      text-align: center;
      font-size: 16px;
      margin-top: 10px;
      width: 80%;
    }
    .hidden { display: none; }
    .wish {
      font-size: 2rem;
      animation: glow 2s infinite alternate;
      margin-top: 20px;
    }
    .message {
      margin-top: 20px;
      font-size: 1.2rem;
      line-height: 1.6;
      background: rgba(0,0,0,0.2);
      padding: 15px;
      border-radius: 10px;
    }
    @keyframes glow {
      0% { text-shadow: 0 0 10px #fff, 0 0 20px #ff6b6b; }
      100% { text-shadow: 0 0 20px #ff6b6b, 0 0 30px #ff9a9e; }
    }
    .confetti {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      overflow: hidden;
      z-index: 1;
    }
    /* Floating balloons and hearts */
    .floating {
      position: absolute;
      bottom: -100px;
      font-size: 2rem;
      animation: floatUp 8s linear infinite;
      opacity: 0.8;
    }
    @keyframes floatUp {
      0% { transform: translateY(0); opacity: 1; }
      100% { transform: translateY(-120vh); opacity: 0; }
    }
  </style>
</head>
<body>
  <div id="background-decor"></div>
  <h1>Hi Kesiya! 🎀</h1>
  <h2>Answer these 3 questions to unlock your surprise! 🎁</h2>

  <div class="question" id="q1">
    <h2>Question 1: Who is your favorite person? ❤️</h2>
    <input type="text" id="answer1" placeholder="Type the name...">
    <br><br>
    <button onclick="checkAnswer1()">Submit</button>
  </div>

  <div class="question hidden" id="q2">
    <h2>Question 2: I Love You ❤️, do you? (Yes or No)</h2>
    <input type="text" id="answer2" placeholder="Yes or No">
    <br><br>
    <button onclick="checkAnswer2()">Submit</button>
  </div>

  <div class="question hidden" id="q3">
    <h2>Question 3: What comes after 15?</h2>
    <input type="text" id="answer3" placeholder="Type the number...">
    <br><br>
    <button onclick="checkAnswer3()">Submit</button>
  </div>

  <div class="wish hidden" id="wish">
    🎉 Happy Birthday Kesiya! 🎂<br>
    You have turned <b>16</b> today! ❤️
  </div>

  <div class="message hidden" id="message">
    Kesiya, I’m the luckiest person in this world to have someone like you in my life.<br>
    You’re not just my girlfriend—you’re my happiness, my peace, and my favorite reason to smile.<br>
    Every moment I spend with you feels like magic, and I wouldn’t trade you for anything.<br>
    Thank you for loving me the way you do.<br>
    I promise to always cherish you, support you, and make you feel special, not just today but every day.<br>
    Happy Birthday, my love. ❤️
  </div>

  <canvas class="confetti hidden" id="confettiCanvas"></canvas>

  <script>
    function checkAnswer1() {
      const answer1 = document.getElementById('answer1').value.trim().toLowerCase();
      if (answer1 === "sherjeev") {
        document.getElementById('q1').classList.add('hidden');
        document.getElementById('q2').classList.remove('hidden');
      } else {
        alert("Hint: It's the most handsome guy you know 😉");
      }
    }
    function checkAnswer2() {
      const answer2 = document.getElementById('answer2').value.trim().toLowerCase();
      if (answer2 === "yes") {
        document.getElementById('q2').classList.add('hidden');
        document.getElementById('q3').classList.remove('hidden');
      } else {
        alert("Awww! Try saying YES ❤️");
      }
    }
    function checkAnswer3() {
      const answer3 = document.getElementById('answer3').value.trim();
      if (answer3 === "16") {
        document.getElementById('q3').classList.add('hidden');
        document.getElementById('wish').classList.remove('hidden');
        document.getElementById('message').classList.remove('hidden');
        startConfetti();
      } else {
        alert("Hint: It's after 15! 🤭");
      }
    }
    // Confetti Animation
    const confettiCanvas = document.getElementById('confettiCanvas');
    const ctx = confettiCanvas.getContext('2d');
    let confettiParticles = [];
    function startConfetti() {
      confettiCanvas.classList.remove('hidden');
      confettiCanvas.width = window.innerWidth;
      confettiCanvas.height = window.innerHeight;
      for (let i = 0; i < 150; i++) {
        confettiParticles.push({
          x: Math.random() * confettiCanvas.width,
          y: Math.random() * confettiCanvas.height - confettiCanvas.height,
          color: `hsl(${Math.random() * 360}, 100%, 50%)`,
          size: Math.random() * 5 + 5,
          speed: Math.random() * 3 + 2
        });
      }
      requestAnimationFrame(updateConfetti);
    }
    function updateConfetti() {
      ctx.clearRect(0, 0, confettiCanvas.width, confettiCanvas.height);
      for (let i = 0; i < confettiParticles.length; i++) {
        let p = confettiParticles[i];
        ctx.fillStyle = p.color;
        ctx.fillRect(p.x, p.y, p.size, p.size);
        p.y += p.speed;
        if (p.y > confettiCanvas.height) {
          p.y = -10;
        }
      }
      requestAnimationFrame(updateConfetti);
    }
    window.addEventListener('resize', () => {
      confettiCanvas.width = window.innerWidth;
      confettiCanvas.height = window.innerHeight;
    });

    // Floating balloons and hearts
    const background = document.getElementById('background-decor');
    function createFloating() {
      const elem = document.createElement('div');
      elem.classList.add('floating');
      elem.style.left = Math.random() * 100 + 'vw';
      elem.style.animationDuration = (6 + Math.random() * 4) + 's';
      elem.textContent = Math.random() > 0.5 ? '🎈' : '❤️';
      background.appendChild(elem);
      setTimeout(() => elem.remove(), 10000);
    }
    setInterval(createFloating, 1000);
  </script>
</body>
</html>
