---
layout: default
title: Swimming Event
permalink: /swimming
---
<img width="750" alt="Skislope" 
src="https://github.com/Code-Demons/miniproject/assets/40652645/33f16454-fa1a-4e86-ab14-fb253ee790cc">
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    canvas {
      border: 1px solid #000;
      display: block;
      margin: 20px auto;
    }
  </style>
  <title>Olympic Race Simulation</title>
</head>
<body>

<canvas id="raceCanvas" width="800" height="280"></canvas>
<button onclick="startRace()">Start Race</button>
<button onclick="resetRace()">Reset Race</button>

<script>
  const canvas = document.getElementById('raceCanvas');
  const ctx = canvas.getContext('2d');

  const raceDurationInSeconds = 10; // Adjust the duration as needed

  // Runner objects with different speeds
  const runners = [
    { name: 'Bubble', speed: 2, color: 'red', position: 0, lane: 1 },
    { name: 'Insertion', speed: 3, color: 'blue', position: 0, lane: 2 },
    { name: 'Merge', speed: 4, color: 'green', position: 0, lane: 3 },
    { name: 'Quick', speed: 5, color: 'yellow', position: 0, lane: 4 },
    // Add more runners as needed
  ];

  // Background image
  const backgroundImage = new Image();
  backgroundImage.src = 'https://github.com/Code-Demons/miniproject/assets/40652645/33f16454-fa1a-4e86-ab14-fb253ee790cc';

  function drawBackground() {
    ctx.drawImage(backgroundImage, 0, 0, canvas.width, canvas.height);
  }

  function drawRunner(runner) {
    ctx.fillStyle = runner.color;
    ctx.fillRect(runner.position, 35*runner.lane + 5, 20, 20);
  }

  function update(timestamp) {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawBackground();

    for (const runner of runners) {
      runner.position += runner.speed;
      drawRunner(runner);

      if (runner.position > canvas.width - 20) {
        alert(`${runner.name} has won the race!`);
        resetRace();
        return;
      }
    }
    requestAnimationFrame(update);
  }

  function startRace() {
    update();
  }

  function resetRace() {
    for (const runner of runners) {
      runner.position = 0;
    }
    cancelAnimationFrame(update);
    // Clear the canvas after resetting
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawBackground();
  }

  // Start the race
  //update();
</script>

</body>
</html>
