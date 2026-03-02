# Assignment-5---Noise

Please enjoy the newest work in my Comet & Dinosaur series
Basically, I combined what I learned before with the starter code from this time, and ended up with this result.


```js
let agents = [];
let count = 100;
let words = ["☄️"];

function setup() {
  createCanvas(600, 400);
  textAlign(CENTER, CENTER);
  

  for (let i = 0; i < count; i++) {
    agents.push({
      x: random(width),
      y: random(height),
      word: random(words),
      
      update() {
        let d = dist(mouseX, mouseY, this.x, this.y);
        if (d < 100) {
          let angle = atan2(this.y - mouseY, this.x - mouseX);
          let speed = map(d, 0, 100, 5, 0);
          textSize(30)
          text("😱", this.x-5, this.y-30)
          this.x += cos(angle) * speed;
          this.y += sin(angle) * speed;
        }
      },

      draw() {
        textSize(40) 
        text(this.word, this.x, this.y); 
      }
    });
  }
}

function draw() {
  background(0);
  fill(255);
  noStroke();

  agents.forEach(a => {
    a.update(); 
    a.draw();   
  });
  
  textSize(80)  
  text("🦖", mouseX, mouseY)
}
```
