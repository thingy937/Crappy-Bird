<html>
<style>
    body {
    background: #36393f;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  canvas {
    border: 8px solid black;
  }
</style>
<div class="" style="width:100;height:100;background-color:#03b1fc;background-image:linear-gradient(#03b1fc, #0339fc);">
<p>&nbsp;</p>
<p align="center">
<canvas width="400" height="400" id="game"></canvas>
</p>

<script>

var bird = {
  x: 30,
  y: 100
};

this.addEventListener('keypress', event => {
  if (event.keyCode == 38) {
    bird.y = bird.y + 1;
  }
})

var c = document.getElementById("game");
var ctx = c.getContext("2d");
ctx.fillRect(bird.x, bird.y, 50, 50);
</script> 

<p align="center">
<button style="background-color:#0339fc" onclick="location.href='https://thingy937.github.io/'"><img src="https://raw.githubusercontent.com/thingy937/Snake-game-/master/home_circle_icon_137496.png" width="50" height="50"></button>
</p>
<p>&nbsp;</p>
</div>
