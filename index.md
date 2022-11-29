<html>
<head>
</head>
<body>
 <style>
  html, body {
    height: 100%;
    margin: 0;
  }
  body {
    background: white;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  canvas {
    border: 10px solid black;
  }
  </style>
<p align="center">
<canvas id="game" width="400" height="400" style="border:1px solid #000000;">
</canvas>
</p>
</body>
<script>
const canvas = document.getElementById('game');
const context = canvas.getContext('2d');
const grid = 15;
const birdHeight = grid * 5; // 80
const maxBirdY = canvas.height - grid - paddleHeight;

var birdSpeed = 5;

const bird = {
  // start in the middle of the game on the left side
  x: grid * 2,
  y: canvas.height / 2 - birdHeight / 2,
  width: grid,
  height: birdHeight,

  // paddle velocity
  dy: 0
};


// game loop
function loop() {
  requestAnimationFrame(loop);
  context.clearRect(0,0,canvas.width,canvas.height);
 
}

// start the game
requestAnimationFrame(loop);
</script>
