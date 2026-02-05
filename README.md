<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>For You 💗</title>

  <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

  <style>
    body {
      margin: 0;
      font-family: 'Pacifico', cursive;
      background: #ffd6e8;
      color: #5a2a3c;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 20px;
    }

    .container {
      max-width: 800px;
      width: 100%;
      background: #fff0f6;
      padding: 30px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    }

    h1 {
      text-align: center;
    }

    ol {
      font-size: 1.1rem;
      line-height: 1.8;
    }

    .center {
      text-align: center;
      margin-top: 30px;
    }

    button {
      font-family: 'Pacifico', cursive;
      background: #ff8fb1;
      border: none;
      padding: 15px 25px;
      font-size: 1.1rem;
      border-radius: 30px;
      cursor: pointer;
      color: white;
    }

    button:hover {
      background: #ff6f9c;
    }

    .hearts-bg {
      position: fixed;
      inset: 0;
      overflow: hidden;
      z-index: -1;
    }

    .heart {
      position: absolute;
      color: #ff8fb1;
      font-size: 24px;
      animation: float 6s infinite ease-in;
    }

    @keyframes float {
      from { transform: translateY(100vh); opacity: 1; }
      to { transform: translateY(-10vh); opacity: 0; }
    }

    .btn-group {
      position: relative;
      display: flex;
      gap: 20px;
      justify-content: center;
      margin-top: 40px;
    }

    #noBtn {
      position: relative;
    }
  </style>
</head>

<body>
  <div class="container" id="content"></div>

  <script>
    let accepted = false;
    const content = document.getElementById('content');
    const params = new URLSearchParams(window.location.search);

    if (!params.get('valentine')) {
      content.innerHTML = `
        <h1>Reasons why I love you:</h1>
        <ol>
          <li>You're amazing</li>
          <li>You're affectionate</li>
          <li>Your eyes</li>
          <li>Your smile</li>
          <li>You love so deeply</li>
          <li>You don't have fragile masculinity</li>
          <li>You're compassionate</li>
          <li>Your height</li>
          <li>You're not afraid to compromise</li>
          <li>You know how to communicate</li>
          <li>You know how to use your words</li>
          <li>You're soft spoken</li>
          <li>You don't hate me</li>
          <li>You understand me</li>
          <li>You know how to handle me</li>
          <li>You love me loudly</li>
          <li>You know how to make things better</li>
          <li>You give me peace in every way</li>
          <li>You make my day better every single day</li>
          <li>I love you because I love you.</li>
        </ol>
        <p class="center">Baby, I love you forever and a day, always remember that.</p>
        <div class="center">
          <button onclick="openValentine()">Click here if you love me 💗</button>
        </div>
      `;
    } else if (!accepted) {
      content.innerHTML = `
        <h1>Will you be my Valentine? 💘</h1>
        <div class="btn-group">
          <button onclick="yesClicked()">Yes 💕</button>
          <button id="noBtn">No 🙄</button>
        </div>
      `;

      const bg = document.createElement('div');
      bg.className = 'hearts-bg';
      document.body.appendChild(bg);

      for (let i = 0; i < 30; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart';
        heart.textContent = '💗';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDelay = Math.random() * 6 + 's';
        bg.appendChild(heart);
      }

      const noBtn = document.getElementById('noBtn');
      noBtn.addEventListener('mouseenter', () => {
        const x = Math.random() * 200 - 100;
        const y = Math.random() * 120 - 60;
        noBtn.style.transform = `translate(${x}px, ${y}px)`;
      });
    }

    function openValentine() {
      window.open(window.location.pathname + '?valentine=true', '_blank');
    }

    function yesClicked() {
      accepted = true;

      confetti({
        particleCount: 200,
        spread: 120,
        origin: { y: 0.6 },
        colors: ['#ff8fb1', '#ffb3c6', '#ffd6e8']
      });

      document.getElementById('content').innerHTML = `
        <h1 style="text-align:center; font-size:3rem;">
          YEEEY I LOVE YOU, FOREVER AND A DAY 💖
        </h1>
      `;
    }
  </script>
</body>
</html>
