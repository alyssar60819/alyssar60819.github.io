# alyssar60819.github.io

<script>

function setup() {
  createCanvas(400, 400);
}

// Current Scene
var currentScene = 0;
// Time bar movement
var timeBarX = 0;
// Winning and losing components
var numCorrect = 5;
// Random placement
// Variables to randomly place cloud
var placementX = Math.round(Math.random(0, 7));
var placementY = Math.round(Math.random(0, 5));

var play=function() {
  background(255, 255, 255);
  // Random color generator
  var Red = 50+Math.random(205);
  var Blue = 50+Math.random(205);
  var Green = 50+Math.random(205);
  // Scoring
  var scoreSize = 40;
  // Random space generator
  var newX = [24, 74, 124, 174, 224, 274, 324, 374];
  var newY = [75, 135, 195, 255, 315, 375];
  // New x-positions
  var X0 = Math.round(Math.random(0, 7));
  var X1 = Math.round(Math.random(-1, 6));
  var X2 = Math.round(Math.random(-2, 5));
  var X3 = Math.round(Math.random(-3, 4));
  var X4 = Math.round(Math.random(-4, 3));
  var X5 = Math.round(Math.random(-5, 2));
  var X6 = Math.round(Math.random(-6, 1));
  var X7 = Math.round(Math.random(-7, 0));
  // New y-positions
  var Y0 = Math.round(Math.random(0, 5));
  var Y1 = Math.round(Math.random(-1, 4));
  var Y2 = Math.round(Math.random(-2, 3));
  var Y3 = Math.round(Math.random(-3, 2));
  var Y4 = Math.round(Math.random(-4, 1));
  var Y5 = Math.round(Math.random(-5, 0));
  draw= function() {
    // Time Bar
    noStroke();
    fill(Red, Blue, Green);
    rect(timeBarX, 0, 400, 50);
    stroke(255, 255, 255);
    strokeWeight(20);
    line(timeBarX-20, -20, timeBarX+70, 60);
    line(timeBarX+50, -20, timeBarX+140, 60);
    line(timeBarX+120, -20, timeBarX+210, 60);
    line(timeBarX+190, -20, timeBarX+280, 60);
    line(timeBarX+260, -20, timeBarX+350, 60);
    line(timeBarX+330, -20, timeBarX+420, 60);
    noStroke();
    fill(255, 255, 255);
    rect(timeBarX-400, 0, 400, 50);
    stroke(Red, Blue, Green);
    strokeWeight(2);
    line(0, 50, 400, 50);
    line(timeBarX, 0, timeBarX+400, 0);
    if(timeBarX<400) {
      timeBarX+=0.125;
    }
    // Circle generator
    for(var x=0; x<400; x+=50) {
      for(var y=45; y<400; y+=60) {
        fill(Red, Blue, Green);
        noStroke();
        ellipse(x+24, y+30, 40, 40);
      }
    }
    // Score display
    fill(255, 255, 255);
    rect(3, 7, scoreSize, 40, 5);
    fill(Red, Blue, Green);
    textSize(40);
    text(numCorrect, 12, 40);
    if(numCorrect>9 || numCorrect<0 && numCorrect>-10) {
      scoreSize = 40;
    }
    if(numCorrect<-0 && numCorrect>-10) {
      scoreSize = 60;
    }
    if(numCorrect<=-10) {
      scoreSize = 80;
    }
    // Placing Imposter
    noStroke();
    fill(Red-20, Blue-20, Green-20);
    ellipse(newX[placementX], newY[placementY], 40, 40);
    // Finding Imposter
    mouseClicked = function() {
      if(mouseX>newX[placementX]-25 && mouseX<newX[placementX]+25 && mouseY>newY[placementY]-25 && mouseY<newY[placementY]+25) {
        numCorrect+=1;
        play();
        if(placementX===0) {
          placementX+=X0;
        }
        if(placementX===1) {
          placementX+=X1;
        }
        if(placementX===2) {
          placementX+=X2;
        }
        if(placementX===3) {
          placementX+=X3;
        }
        if(placementX===4) {
          placementX+=X4;
        }
        if(placementX===5) {
          placementX+=X5;
        }
        if(placementX===6) {
          placementX+=X6;
        }
        if(placementY===0) {
          placementY+=Y0;
        }
        if(placementY===1) {
          placementY+=Y1;
        }
        if(placementY===2) {
          placementY+=Y2;
        }
        if(placementY===3) {
          placementY+=Y3;
        }
        if(placementY===4) {
          placementY+=Y4;
        }
        if(placementY===5) {
          placementY+=Y5;
        }
      }
        else {
          numCorrect-=5;
        }
    };
  };
};

// Growing components
var circle = 300;
// Variables for color changing background
var backgroundColor1 = 255;
var backgroundColor2 = 0;
var backgroundColor3 = 0;
draw= function() {
  // Commands for color changing background
  background(backgroundColor1, backgroundColor2, backgroundColor3);
  if(backgroundColor1>250 && backgroundColor2<255) {
    backgroundColor2+=2;
    backgroundColor3-=2;
  }
  if(backgroundColor2>250 && backgroundColor3<255) {
    backgroundColor3+=2;
    backgroundColor1-=2;
  }
  if(backgroundColor3>250 && backgroundColor1<255) {
    backgroundColor1+=2;
    backgroundColor2-=2;
  }
  // Start button
  noStroke();
  fill(255, 255, 255);
  ellipse(200, 200, circle, circle);
  fill(backgroundColor1, backgroundColor2, backgroundColor3);
  triangle(125, 100, 325, 200, 125, 300);
  if(mouseX>100 && mouseX<400 && mouseY>100 && mouseY<400) {
    circle=315;
  }
    else {
      circle=300;
    }
  mousePressed = function() {
    if(mouseX>100 && mouseX<400 && mouseY>100 && mouseY<400 && currentScene===0) {
      play();
      currentScene+=1;
    }
  };
};
<script/>
                                                            
                                              
                                                           
