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
<input type="number" id="fibNumber" placeholder="Enter Fibonacci Number">
<button onclick="runFibonacciRace()">Run Fibonacci Race</button>
<button onclick="resetRace()">Reset Race</button>


<div id="stats"></div>


<script>
  let animationFrameId;
  const canvas = document.getElementById('raceCanvas');
  const ctx = canvas.getContext('2d');

  const runners = [
    { name: 'For Loop', speed: 0, color: 'red', position: 0, lane: 1, done: false },
    { name: 'Recursion', speed: 0, color: 'blue', position: 0, lane: 2, done: false },
    { name: 'While Loop', speed: 0, color: 'green', position: 0, lane: 3, done: false },
    { name: 'Dynamic Programming', speed: 0, color: 'yellow', position: 0, lane: 4, done: false }
  ];

  const statsElement = document.getElementById('stats');

  const backgroundImage = new Image();
  backgroundImage.src = 'https://github.com/Code-Demons/miniproject/assets/40652645/33f16454-fa1a-4e86-ab14-fb253ee790cc';

  function drawBackground() {
    ctx.drawImage(backgroundImage, -60, 0, canvas.width + 120, canvas.height);
  }

  function drawRunner(runner) {
    ctx.fillStyle = runner.color;
    ctx.fillRect(runner.position, 35 * runner.lane + 5, 20, 20);
  }

  function updateStats() {
    let statsHTML = '<h3>Runner Stats</h3>';
    for (const runner of runners) {
      statsHTML += `<p>${runner.name} Speed: ${runner.speed}</p>`;
    }
    statsElement.innerHTML = statsHTML;
  }

  function update() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawBackground();

    let allRunnersDone = true;
    for (const runner of runners) {
      if (!runner.done) {
        runner.position += runner.speed;
        if (runner.position > canvas.width - 20) { // 20 is the width of the runner
          runner.position = canvas.width - 20; // Stop the runner at the edge
          runner.done = true;
        } else {
          allRunnersDone = false;
        }
      }
      drawRunner(runner);
    }

    if (!allRunnersDone) {
      animationFrameId = requestAnimationFrame(update);
    }
    updateStats();
  }

  async function runFibonacciRace() {
    const fibNumber = document.getElementById('fibNumber').value;
    if (!fibNumber) {
      alert('Please enter a Fibonacci number');
      return;
    }

    if (animationFrameId) {
      cancelAnimationFrame(animationFrameId);
    }

    resetRace();

    const endpoints = [
      `http://localhost:8085/fibonacci/forloop/${fibNumber}`,
      `http://localhost:8085/fibonacci/recursion/${fibNumber}`,
      `http://localhost:8085/fibonacci/whileloop/${fibNumber}`,
      `http://localhost:8085/fibonacci/dynamic/${fibNumber}`
    ];

    let maxTime = 0;
    for (let i = 0; i < runners.length; i++) {
      const startTime = performance.now();
      const response = await fetch(endpoints[i]);
      const endTime = performance.now();
      const timeTaken = endTime - startTime;
      maxTime = Math.max(maxTime, timeTaken);
    }

    for (let i = 0; i < runners.length; i++) {
      const startTime = performance.now();
      const response = await fetch(endpoints[i]);
      const endTime = performance.now();
      const timeTaken = endTime - startTime;

      runners[i].speed = calculateSpeed(timeTaken, maxTime);
    }

    startRace();
  }

  function calculateSpeed(timeTaken, maxTime) {
    return Math.max(1, maxTime - timeTaken);
  }

  function startRace() {
    for (const runner of runners) {
      runner.done = false;
      runner.position = 0;
    }
    update();
  }

  function resetRace() {
    for (const runner of runners) {
      runner.position = 0;
      runner.done = false;
    }
    if (animationFrameId) {
      cancelAnimationFrame(animationFrameId);
    }
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawBackground();
    updateStats();
  }

  updateStats();
</script>


</body>
</html>
