<html>
<head>
  <title></title>
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
  </style>
</head>
<body>
<p align="center">
<canvas width="400" height="400" id="game"></canvas>
</p>
<script>
const canvas = document.getElementById('game');
const context = canvas.getContext('2d');
const grid = 15;
const birdHeight = grid * 5; // 80
const maxPaddleY = canvas.height - grid - birdHeight;

var birdSpeed = 6;

const bird = {
  // start in the middle of the game on the left side
  x: grid * 2,
  y: canvas.height / 2 - birdHeight / 2,
  width: grid,
  height: birdHeight,

  // paddle velocity
  dy: 0
};

// check for collision between two objects using axis-aligned bounding box (AABB)
// @see https://developer.mozilla.org/en-US/docs/Games/Techniques/2D_collision_detection
function collides(obj1, obj2) {
  return obj1.x < obj2.x + obj2.width &&
         obj1.x + obj1.width > obj2.x &&
         obj1.y < obj2.y + obj2.height &&
         obj1.y + obj1.height > obj2.y;
}

// game loop
function loop() {
  requestAnimationFrame(loop);
  context.clearRect(0,0,canvas.width,canvas.height);

  // move bird by their velocity
  bird.y += birdPaddle.dy;

  // prevent bird from going through walls
  if (leftPaddle.y < grid) {
    leftPaddle.y = grid;
  }
  else if (bird.y > maxBirdY) {
    bird.y = maxBirdY;
  }


  // draw bird
  context.fillStyle = 'black';
  context.fillRect(bird.x, bird.y, bird.width, bird.height);

  // draw walls
  context.fillStyle = 'black';
  context.fillRect(0, 0, canvas.width, grid);
  context.fillRect(0, canvas.height - grid, canvas.width, canvas.height);

  // draw dotted line down the middle
  for (let i = grid; i < canvas.height - grid; i += grid * 2) {
    context.fillRect(canvas.width / 2 - grid / 2, i, grid, grid);
  }
}

// listen to keyboard events to move the paddles
document.addEventListener('keydown', function(e) {


  // w key
  if (e.which === 87) {
    bird.dy = -birdSpeed;
  }
  // a key
  else if (e.which === 83) {
    bird.dy = birdSpeed;
  }
});

// listen to keyboard events to stop the bird if key is released
document.addEventListener('keyup', function(e) {

  if (e.which === 83 || e.which === 87) {
    bird.dy = 0;
  }
});

// start the game
requestAnimationFrame(loop);
</script>
</body>
<p align="center">
<button onclick="location.href='https://thingy937.github.io/'"><img src="https://raw.githubusercontent.com/thingy937/Snake-game-/master/home_circle_icon_137496.png" width="50" height="50"></button>
</p>
</html>
