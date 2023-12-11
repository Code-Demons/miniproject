---
layout: default
title: Swimming Event
permalink: /swimming
---

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
   #results {
     margin-top: 20px;
   }
 </style>
 <title>Olympic Race Simulation</title>
</head>
<body>

<canvas id="raceCanvas" width="800" height="280"></canvas>
<input type="number" id="fibNumber" placeholder="Enter Fibonacci Number">
<button onclick="runFibonacciRace()">Run Fibonacci Race</button>
<button onclick="resetRace()">Reset Race</button>

<div id="results"></div>

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

  const resultsElement = document.getElementById('results');

  const backgroundImage = new Image();
  backgroundImage.src = 'https://github.com/Code-Demons/miniproject/assets/40652645/33f16454-fa1a-4e86-ab14-fb253ee790cc';

  function drawBackground() {
    ctx.drawImage(backgroundImage, -60, 0, canvas.width + 120, canvas.height);
  }

  function drawRunner(runner) {
    ctx.fillStyle = runner.color;
    ctx.fillRect(runner.position, 35 * runner.lane + 5, 20, 20);
  }

  function update() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawBackground();

    let allRunnersDone = true;
    for (const runner of runners) {
      if (!runner.done) {
        runner.position += runner.speed;
        if (runner.position > canvas.width - 20) {
          runner.position = canvas.width - 20;
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
    let results = [];

    for (let i = 0; i < runners.length; i++) {
      const response = await fetch(endpoints[i]);
      const data = await response.json();
      const timeTaken = data.timeTaken;
      maxTime = Math.max(maxTime, timeTaken);
      results.push({ name: runners[i].name, result: data.result, timeTaken: timeTaken });
    }

    for (let i = 0; i < runners.length; i++) {
      runners[i].speed = calculateSpeed(results[i].timeTaken, maxTime);
    }

    displayResults(results);
    startRace();
  }

  function displayResults(results) {
    let resultsHTML = '<h3>Results</h3>';
    results.forEach(result => {
      resultsHTML += `<p><strong>${result.name}:</strong> Result: ${result.result}, Time: ${result.timeTaken} ns</p>`;
    });
    resultsElement.innerHTML = resultsHTML;
  }

  function calculateSpeed(timeTaken, maxTime) {
    const speedFactor = 0.0005; // Adjust for desired speed
    const minSpeed = 0.5; // Minimum speed to ensure all runners move
    return Math.max(minSpeed, (maxTime - timeTaken) * speedFactor);
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
  }

  update();
</script>

</body>
</html>
