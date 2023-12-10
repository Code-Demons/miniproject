---
layout: default
title: Track Event
permalink: /track
---
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            margin: 0;
            padding: 0;
            background-image: url('https://github.com/Code-Demons/miniproject/assets/40652645/131c0df0-1723-4bd6-81ba-41cec8aa1a57');
            background-size: cover;
            background-position: center;
            height: 100vh;
        }
        canvas {
            position: fixed;
            top: 0;
            left: 0;
            border: 1px solid #000;
            width: 100vw; /* Make the canvas full width of the viewport */
            height: 100vh; /* Make the canvas full height of the viewport */
            z-index: -1; /* Ensure it's behind other elements */
        }
        #controls {
            position: absolute;
            top: 10px;
            left: 10px;
            z-index: 1;
            color: white;
        }
    </style>
    <title>Track Event</title>
</head>

<body>
    <div id="controls">
        <input type="number" id="fibNumber" placeholder="Enter Fibonacci Number">
        <button onclick="runFibonacciRace()">Run Fibonacci Race</button>
        <button onclick="resetRace()">Reset Race</button>
    </div>
    <canvas id="raceCanvas"></canvas>
    <script>
        const canvas = document.getElementById('raceCanvas');
        const ctx = canvas.getContext('2d');
        // Runner objects with different speeds
        const runners = [
            { name: 'For Loop', speed: 0, color: 'red', position: 0, lane: 1, done: false, yPos: 30 },
            { name: 'Recursion', speed: 0, color: 'blue', position: 0, lane: 2, done: false, yPos: 60 },
            { name: 'While Loop', speed: 0, color: 'green', position: 0, lane: 3, done: false, yPos: 90 },
            { name: 'Dynamic Programming', speed: 0, color: 'yellow', position: 0, lane: 4, done: false, yPos: 120 }
        ];
        // Background image
        const backgroundImage = new Image();
        backgroundImage.src = 'https://github.com/Code-Demons/miniproject/assets/40652645/33f16454-fa1a-4e86-ab14-fb253ee790cc';
        function drawBackground() {
            ctx.drawImage(backgroundImage, 0, 0, canvas.width, canvas.height);
        }
        function drawRunner(runner) {
            ctx.fillStyle = runner.color;
            ctx.fillRect(runner.position, runner.yPos, 20, 20);
        }
        function updateStats() {
            for (const runner of runners) {
                const stats = `${runner.name}: ${runner.speed.toFixed(2)} px/ms`;
                const statElement = document.createElement('p');
                statElement.textContent = stats;
                statElement.style.color = runner.color; // Set the color
                statElement.style.position = 'absolute';
                statElement.style.top = `${runner.yPos}px`; // Set the vertical position
                statElement.style.left = '150px'; // Set the horizontal position
                document.body.appendChild(statElement);
            }
        }
        function update() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            drawBackground();
            for (const runner of runners) {
                if (!runner.done) {
                    runner.position += runner.speed / 3;
                }
                if (runner.position >= canvas.width - 20) {
                    runner.done = true;
                }
                drawRunner(runner);
            }
            requestAnimationFrame(update);
            updateStats();
        }
        async function runFibonacciRace() {
            const fibNumber = document.getElementById('fibNumber').value;
            if (!fibNumber) {
                alert('Please enter a Fibonacci number');
                return;
            }
            // Reset the race
            resetRace();
            // Define your backend endpoints
            const endpoints = [
                `http://localhost:8085/fibonacci/forloop/${fibNumber}`,
                `http://localhost:8085/fibonacci/recursion/${fibNumber}`,
                `http://localhost:8085/fibonacci/whileloop/${fibNumber}`,
                `http://localhost:8085/fibonacci/dynamic/${fibNumber}`
            ];
            // Fetch data from each endpoint and update the runners
            for (let i = 0; i < runners.length; i++) {
                const startTime = performance.now();
                const response = await fetch(endpoints[i]);
                const endTime = performance.now();
                const timeTaken = endTime - startTime;
                // Update runner speed based on time taken
                runners[i].speed = calculateSpeed(timeTaken);
            }
            // Start the race
            startRace();
        }
        function calculateSpeed(timeTaken) {
            // Convert time taken to a suitable speed for the animation
            // Smaller time should result in higher speed
            return Math.max(1, 1000 / timeTaken);
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
            cancelAnimationFrame(update);
            // Clear the canvas after resetting
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            drawBackground();
            updateStats();
        }
        // Initialize stats
        updateStats();
    </script>
</body>