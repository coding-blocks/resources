---
layout: post
title:  "IEEE Techweek Game Workshop"
categories: [Workshop]
tags: c++ DTU Workshop
image: dtu_ieee_pokemon.jpg
---

Codes from IEEE-DTU Techweek Workshop on Game Development.

### **Javascript Practice Code**
```js
<html>
    <head>
        <title>JS Practice</title>
    </head>

    <body>
        <script src="game.js"></script>
        <script>
            var a = 10;
            var b = "Hello";

            console.log(a);
            console.log(b);
            document.write("Hello DTU");

            //name = prompt("Enter your name");
            //console.log("Hey"+name);

            //alert("Game over");

            a = [1,2,3,"One","Two",3.5];

            for(i=0;i<a.length;i++){
              console.log(a[i]);
            }

            fly();
            //fun();
            sit();

            bird = {
                'x': 10,
                'y':20,
                'color': "gray",
                'speed':100,

                'jump' : function(){
                    console.log("Bird is jumping");
                }

            };

            function fly(){

                console.log("Bird is flying");
            }
            console.log(x);

            function sit(){
                console.log("Bird is sitting");
            }
            var fun = function(){
                console.log("Having fun!");
            }

            ///Objects
            //JSON - Javascript Object Notation
            //JSON is collection of key value pairs
            //key can be a string, value can be antyihing






        </script>
    </body>
</html>

```
### **Starting with the Game - The Game Loop**
![GameLoop](http://i.imgur.com/GJjFroX.png)

### **Pokemon Game - Code**
The game has two files one for HTML,CSS and another one for JS.



index.html

```html
<html>
  <head>
      <title>DTU's Pokemon Game</title>
      <style>
        #mycanvas{
            border:15px solid orange;
            background-image: url("assets/background2.png");
            background-size: cover;
        }

      </style>

  </head>
  <body>

    <canvas width="800" height="600" id="mycanvas"></canvas>

    <script src="game.js"></script>

  </body>
</html>

```


### **JavaScript Code**
Keep both files in same folder


```js
//Game JS File
function loadImages(){
  playerImage = new Image;
  playerImage.src = "assets/pika.png";

  enemyImage = new Image;
  enemyImage.src = "assets/gengar.png";

  ballImage = new Image;
  ballImage.src = "assets/ball.png";
}

function init(){


  canvas = document.getElementById('mycanvas');
  console.log(canvas);
  pen  = canvas.getContext('2d');
  W = canvas.width;
  H = canvas.height;
  GAME_OVER = false;

  enemy = {
    x: 280,
    y:230,
    w:100,
    h:100,
    speed:4,
  };

  player = {
    x:10,
    y: H/2,
    w:100,
    h:100,
    speed:0
  }
  goal = {
    x:W-100,
    y:H/2,
    w:100,
    h:100
  }

  canvas.addEventListener('mousedown',function(){
    player.speed = 10;
  });
  canvas.addEventListener('mouseup',function(){
    player.speed = 0;
  });



}
function isColliding(r1,r2){

  var firstCond = Math.abs(r1.x-r2.x)<=r1.w;
  var secondCond = Math.abs(r2.y - r1.y)<=r1.h;
  return firstCond&&secondCond;

}
function draw(){
    pen.clearRect(0,0,W,H);

    pen.fillStyle = "blue";
    pen.drawImage(enemyImage,enemy.x, enemy.y,enemy.w,enemy.h);

    pen.fillStyle = "red";
    pen.drawImage(ballImage,goal.x,goal.y,goal.w,goal.h);

    pen.fillStyle = "green";
    pen.drawImage(playerImage,player.x,player.y,player.w,player.h);

}

function update(){
  enemy.y = enemy.y + enemy.speed;

  if(enemy.y>=H-enemy.h || enemy.y<=0){
    enemy.speed = -1*enemy.speed;
  }
  if(isColliding(player,enemy)){
    alert("Game Over");
    GAME_OVER = true;
  }
  if(isColliding(player,goal)){
    alert("Level-1 Complete");
    GAME_OVER = true;
  }

  player.x += player.speed;
}

function loop(){
  console.log("In Game Loop");
  draw();
  update();
  if(GAME_OVER==false){
    window.requestAnimationFrame(loop);
  }
}

loadImages();
init();
loop();

```

### **Download Files**
All Codes and Assets can be downloaded from [Github Repository](https://github.com/prateek27/Workshops) as well.

### **Learn from Coding Blocks Tutorials**
To learn more subscribe us on [Youtube](http://cb.lk/yt) 

### **Upcoming Bootcamps(Aug-Sept)** 
- Game Development in JavaScript
- Terminal Game Development in C 
- Python Chatbots and Automation Bootcamp
- Competitive Coding Bootcamp

For more details follow (Coding Blocks)(http://cb.lk) us on [Facebook](http://facebook.com/codingblocksindia) or check events section on website.
