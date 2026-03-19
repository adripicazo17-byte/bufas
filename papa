<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Feliz Día del Padre</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: radial-gradient(circle at top, #2b2b4f, #1e1e2f);
      font-family: Arial, sans-serif;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      cursor: pointer;
      text-align: center;
    }

    .hint {
      color: white;
      font-size: 28px;
      margin-bottom: 10px;
      animation: pulse 1.5s infinite;
    }

    .arrow {
      font-size: 40px;
      color: #ffd700;
      animation: bounce 1s infinite;
      margin-bottom: 20px;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }

    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(10px); }
    }

    /* CONTENEDOR SOBRE CENTRADO */
    .envelope-wrapper {
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .envelope {
      width: 150px;
      height: 100px;
      background: #ffcc00;
      position: relative;
      transition: all 0.8s ease;
    }

    .flap {
      width: 0;
      height: 0;
      border-left: 75px solid transparent;
      border-right: 75px solid transparent;
      border-bottom: 50px solid #ffaa00;
      position: absolute;
      top: -50px;
      transform-origin: bottom;
      transition: transform 0.8s;
    }

    .open .flap {
      transform: rotateX(180deg);
    }

    .hide {
      opacity: 0;
      transform: scale(0);
    }

    /* CONTENIDO FINAL */
    .content {
      display: none;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 20px;
      max-width: 900px;
      padding: 20px;
    }

    .show-content {
      display: flex;
    }

    .message {
      font-size: 64px;
      font-weight: 900;
      opacity: 0;
      letter-spacing: 4px;
      text-transform: uppercase;
      background: linear-gradient(90deg, red, yellow, cyan, magenta);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow: 0 0 25px rgba(255,255,255,0.4);
    }

    .show-text {
      opacity: 1;
      animation: glow 2s infinite alternate;
    }

    @keyframes glow {
      from { text-shadow: 0 0 10px #fff; }
      to { text-shadow: 0 0 40px #ff0, 0 0 60px #f0f; }
    }

    .poem {
      color: #f5f5f5;
      font-size: 20px;
      line-height: 1.8;
      opacity: 0;
      white-space: pre-line;
      background: rgba(255,255,255,0.05);
      padding: 20px;
      border-radius: 20px;
      backdrop-filter: blur(5px);
    }

    .show-poem {
      opacity: 1;
      animation: fadeIn 2s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .confetti {
      position: absolute;
      width: 8px;
      height: 8px;
      top: -10px;
      animation: fall linear infinite;
    }

    @keyframes fall {
      to { transform: translateY(100vh) rotate(360deg); }
    }

    .balloon {
      position: absolute;
      bottom: -100px;
      width: 40px;
      height: 60px;
      border-radius: 50%;
      animation: floatUp linear infinite;
    }

    @keyframes floatUp {
      to { transform: translateY(-120vh); }
    }

    .burst {
      position: absolute;
      width: 6px;
      height: 6px;
      border-radius: 50%;
      animation: explode 0.8s ease-out forwards;
    }

    @keyframes explode {
      to {
        transform: translate(var(--x), var(--y)) scale(0);
        opacity: 0;
      }
    }

  </style>
</head>
<body onclick="startAnimation()">

<div class="hint" id="hint">Dame click</div>
<div class="arrow" id="arrow">⬇️</div>

<div class="envelope-wrapper">
  <div class="envelope" id="envelope">
    <div class="flap"></div>
  </div>
</div>

<div class="content" id="content">
  <div class="message" id="message">FELIZ DÍA DEL PADRE, PAPA🎉</div>

  <div class="poem" id="poem">
Jaime en el bar ya monta el sarao,
con esa sonrisa que va “picao”.
Vacila, provoca, le mola el jaleo,
y si se calienta… mejor ni le veo

A veces se enciende, modo agresivo,
salta a la mínima, todo impulsivo.
Pero en el fondo, aunque vaya de duro,
es buen colega… eso es seguro
  </div>
</div>

<audio id="sound" src="https://www.soundjay.com/human/sounds/applause-8.mp3"></audio>

<script>

function playSound() {
  const audio = document.getElementById("sound");
  audio.currentTime = 0;
  audio.play();
}

function startAnimation() {
  playSound();

  const envelope = document.getElementById("envelope");
  envelope.classList.add("open");

  createExplosion();

  setTimeout(() => {
    envelope.classList.add("hide");

    document.getElementById("content").classList.add("show-content");
    document.getElementById("message").classList.add("show-text");
    document.getElementById("poem").classList.add("show-poem");

    document.getElementById("hint").style.display = "none";
    document.getElementById("arrow").style.display = "none";

    createConfetti();
    createBalloons();
  }, 600);
}

function createExplosion() {
  for (let i = 0; i < 40; i++) {
    const p = document.createElement("div");
    p.classList.add("burst");

    p.style.background = getRandomColor();
    p.style.left = "50%";
    p.style.top = "50%";

    const x = (Math.random() - 0.5) * 300 + "px";
    const y = (Math.random() - 0.5) * 300 + "px";

    p.style.setProperty("--x", x);
    p.style.setProperty("--y", y);

    document.body.appendChild(p);

    setTimeout(() => p.remove(), 800);
  }
}

function createConfetti() {
  setInterval(() => {
    const confetti = document.createElement("div");
    confetti.classList.add("confetti");

    confetti.style.left = Math.random() * window.innerWidth + "px";
    confetti.style.background = getRandomColor();
    confetti.style.animationDuration = (Math.random() * 3 + 2) + "s";

    document.body.appendChild(confetti);

    setTimeout(() => confetti.remove(), 5000);
  }, 100);
}

function createBalloons() {
  setInterval(() => {
    const balloon = document.createElement("div");
    balloon.classList.add("balloon");

    balloon.style.left = Math.random() * window.innerWidth + "px";
    balloon.style.background = getRandomColor();
    balloon.style.animationDuration = (Math.random() * 5 + 5) + "s";

    document.body.appendChild(balloon);

    setTimeout(() => balloon.remove(), 10000);
  }, 500);
}

function getRandomColor() {
  const colors = ["#ff4d4d", "#ffd700", "#00ffcc", "#ff66ff", "#66ff66"];
  return colors[Math.floor(Math.random() * colors.length)];
}

</script>

</body>
</html>
