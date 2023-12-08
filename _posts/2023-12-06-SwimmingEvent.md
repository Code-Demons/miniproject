---
layout: default
title: Swimming Event
permalink: /swimming
---

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

<div id="stats"></div>


<script>
  const canvas = document.getElementById('raceCanvas');
  const ctx = canvas.getContext('2d');

  // Runner objects with different speeds
  const runners = [
    { name: 'Bubble Sort', speed: 16, color: 'red', position: 0, lane: 1, done: false },
    { name: 'Insertion Sort', speed: 8, color: 'blue', position: 0, lane: 2, done: false },
    { name: 'Merge Sort', speed: 3, color: 'green', position: 0, lane: 3, done: false },
    { name: 'Quick Sort', speed: 3, color: 'yellow', position: 0, lane: 4, done: false },
    // Add more runners as needed
  ];

  // define stats element
  const statsElement = document.getElementById('stats');

  // Background image
  const backgroundImage = new Image();
  backgroundImage.src = 'https://github.com/Code-Demons/miniproject/assets/40652645/33f16454-fa1a-4e86-ab14-fb253ee790cc';

  function drawBackground() {
    ctx.drawImage(backgroundImage, -60, 0, canvas.width + 120, canvas.height);
  }

  function drawRunner(runner) {
    ctx.fillStyle = runner.color;
    ctx.fillRect(runner.position, 35*runner.lane + 5, 20, 20);
  }


  function updateStats() {
    let statsHTML = '<h3>Runner Stats</h3>';
    for (const runner of runners) {
      statsHTML += `<p>${runner.name} Speed: ${runner.speed}</p>`;
    }
    statsElement.innerHTML = statsHTML;
  }

  function update(timestamp) {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawBackground();

    for (const runner of runners) {
      if (runner.done == false){
        runner.position += runner.speed/3;     
      }
      if (runner.position >= canvas.width - 20) {
        runner.done = true
      }
      drawRunner(runner);
    }
    requestAnimationFrame(update);
    updateStats();
  }

  function startRace() {
    for (const runner of runners) {
      runner.done = false
    }
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
    updateStats();
  }

  // Start the race
  //update();
</script>

</body>
</html>

<!-- Bubble Sort Swimming Animation https://github.com/Code-Demons/miniproject/assets/40652645/4f043398-2031-464d-aefc-0ffc0ea0f689 -->
