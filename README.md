[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/xr2RtvyI)


In today's lab, we used constructors and arrays to draw multiple objects of the same type without creating a function for every object. For this exercise we drew 20 balls, randomly colored, at random speeds, that move along the X axis and bounce off the canvas walls. Link to the code is below.
https://editor.p5js.org/Furi0usGeorgeX/sketches/OwOJ39wIr

Below is the class constructor used to draw every ball.

class ball {
  constructor(x, y, hue) {
    this.x = x;
    this.y = y;
    this.color = "hsla(" + parseInt(hue) + ", 100%, 50%, 1)";
    this.addX = random(1-5);
  }
  move() {
    this.x = this.x + this.addX;
    this.y = this.y;
    let ballIsTooFarLeft = this.x < 0;
    let ballIsTooFarRight = this.x > width;
    if (ballIsTooFarLeft || ballIsTooFarRight) {
      this.addX = -this.addX;
    }
  }
  show() {
    push();
    fill(this.color);
    ellipse(this.x, this.y, 50);
    pop();
  }
  
  Inside setup, the following code determines the amount of balls on screen, and determine what X and Y and color each ball spawns with (all of which are random).
  
   for (let ballsDrawn = 0; ballsDrawn < 20; ballsDrawn++) {
    ballList[ballsDrawn];
    let ballX = random(width);
    let ballY = random(height);
    let ballHue = random(360);
    ballList[ballsDrawn] = new ball(ballX, ballY, ballHue);
