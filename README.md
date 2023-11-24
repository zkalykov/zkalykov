- 👋 Hi, I’m @zkalykov
- 👀 I’m interested in programming
- 🌱 I’m currently learning idk what ) 
- 📫 How to reach me : instagram @zhkalykov

<p style="text-align:center; display: flex; justify-content: center; align-items: center;">
  <img align="left" src="https://github-readme-stats.vercel.app/api/top-langs?username=zkalykov&show_icons=true&locale=en&layout=compact&theme=dark" alt="zkalykov" height="200" style="border: none;"/>

  <img align="center" src="https://github-readme-streak-stats.herokuapp.com/?user=zkalykov&theme=dark" alt="zkalykov" height="200" style="border: none;"/>
</p>

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: black;
    }
    canvas {
      display: block;
    }
  </style>
</head>
<body>
  <canvas id="ballCanvas"></canvas>

  <script>
    const canvas = document.getElementById('ballCanvas');
    const ctx = canvas.getContext('2d');
    let borderHits = 0; // Counter for border hits

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const ball = {
      x: canvas.width / 2,
      y: canvas.height / 2,
      radius: 20,
      color: getRandomColor(),
      speed: 5,
      dx: getRandomSpeed(),
      dy: getRandomSpeed()
    };

    function getRandomColor() {
      const letters = '0123456789ABCDEF';
      let color = '#';
      for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
    }

    function getRandomSpeed() {
      return (Math.random() - 1) * 2; // Random number between -1 and 1
    }

    function drawBall() {
      ctx.beginPath();
      ctx.arc(ball.x, ball.y, ball.radius, 0, Math.PI * 2);
      ctx.fillStyle = ball.color;
      ctx.fill();
      ctx.closePath();
    }

    function update() {
      ball.x += ball.dx * ball.speed;
      ball.y += ball.dy * ball.speed;

      if (ball.x - ball.radius < 0 || ball.x + ball.radius > canvas.width) {
        ball.dx = -ball.dx;
        ball.color = getRandomColor();
        borderHits++;
      }

      if (ball.y - ball.radius < 0 || ball.y + ball.radius > canvas.height) {
        ball.dy = -ball.dy;
        ball.color = getRandomColor();
        borderHits++;
      }
    }

    function draw() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      drawBall();
      ctx.fillStyle = 'white';
      ctx.font = '20px Arial';
      ctx.fillText('Border Hits: ' + borderHits, 10, 30);
    }

    function animate() {
      update();
      draw();
      requestAnimationFrame(animate);
    }

    animate();
  </script>
</body>
</html>
