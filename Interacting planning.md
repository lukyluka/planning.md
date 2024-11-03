
The two objects are a circle and a circle.

I will describe that the objects are touching when the distance between the center of the circle and the closest edge of the rectangle is less than or equal to the 
circle's radius, and the circle is within the rectangle's horizontal and vertical bounds.

When the objects touch, they will bounce off each other by reversing their directions. I will swap the dx and dy variables for each object to make them move in opposite directions. 

let circle1X, circle1Y, circle1DX, circle1DY, circleRadius1;
let circle2X, circle2Y, circle2DX, circle2DY, circleRadius2;

function setup() {
  createCanvas(400, 400);

  // Initialize first circle
  circle1X = 100;
  circle1Y = 100;
  circleRadius1 = 30;
  circle1DX = 3;
  circle1DY = 2;

  // Initialize second circle
  circle2X = 300;
  circle2Y = 200;
  circleRadius2 = 30;
  circle2DX = 2;
  circle2DY = 3;
}

function draw() {
  background(220);

  // Draw the two circles
  ellipse(circle1X, circle1Y, circleRadius1 * 2);
  ellipse(circle2X, circle2Y, circleRadius2 * 2);

  // Move the first circle
  circle1X += circle1DX;
  circle1Y += circle1DY;

  // Move the second circle
  circle2X += circle2DX;
  circle2Y += circle2DY;

  // Bounce off walls (circle 1)
  if (circle1X - circleRadius1 < 0 || circle1X + circleRadius1 > width) {
    circle1DX *= -1;
  }
  if (circle1Y - circleRadius1 < 0 || circle1Y + circleRadius1 > height) {
    circle1DY *= -1;
  }

  // Bounce off walls (circle 2)
  if (circle2X - circleRadius2 < 0 || circle2X + circleRadius2 > width) {
    circle2DX *= -1;
  }
  if (circle2Y - circleRadius2 < 0 || circle2Y + circleRadius2 > height) {
    circle2DY *= -1;
  }

  // Check for collision between the two circles
  let distance = dist(circle1X, circle1Y, circle2X, circle2Y);
  if (distance < circleRadius1 + circleRadius2) {
    // Reverse directions upon collision
    circle1DX *= -1;
    circle1DY *= -1;
    circle2DX *= -1;
    circle2DY *= -1;
  }
}

// Reset positions when a key is pressed
function keyPressed() {
  circle1X = 100;
  circle1Y = 100;
  circle2X = 300;
  circle2Y = 200;
}

