<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
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
</head>
<body onload="startGame()">
<p align="center">
<canvas width="400" height="400" id="game"></canvas>
</p>
<script>

var myGamePiece;

function startGame() {
    myGamePiece = new component(30, 30, "black", 80, 75);
    myGameArea.start();
}

var myGameArea = {
    canvas : document.createElement("canvas"),
    start : function() {
        this.canvas.width = 400;
        this.canvas.height = 400;
        this.context = this.canvas.getContext("2d");
        document.body.insertBefore(this.canvas, document.body.childNodes[0]);
        this.interval = setInterval(updateGameArea, 20);        
    },
    stop : function() {
        clearInterval(this.interval);
    },    
    clear : function() {
        this.context.clearRect(0, 0, this.canvas.width, this.canvas.height);
    }
}

function component(width, height, color, x, y, type) {
    this.type = type;
    this.width = width;
    this.height = height;
    this.x = x;
    this.y = y;    
    this.speedX = 0;
    this.speedY = 0;    
    this.gravity = 0.05;
    this.gravitySpeed = 0;
    this.update = function() {
        ctx = myGameArea.context;
        ctx.fillStyle = color;
        ctx.fillRect(this.x, this.y, this.width, this.height);
    }
    this.newPos = function() {
        this.gravitySpeed += this.gravity;
        this.x += this.speedX;
        this.y += this.speedY + this.gravitySpeed;        
    }
}

function updateGameArea() {
    myGameArea.clear();
    myGamePiece.newPos();
    myGamePiece.update();
}

</script>
</body>
</html>
