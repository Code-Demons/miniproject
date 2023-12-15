---
layout: default
title: Billy Bubble
permalink: /bubbleathlete
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Billy Bubble</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }
        #container {
            display: flex;
            justify-content: flex-start;
            align-items: flex-start;
        }
        #image {
            width: 300px; /* Adjust the width as needed */
            height: auto;
            margin-right: 20px;
        }
        #attributes {
            width: 50%; /* Adjust the width as needed */
            padding: 20px;
            box-sizing: border-box;
        }
        #continueButton {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div id="container">
    <img id="image" src="https://github.com/Code-Demons/miniproject/assets/40652645/4049e8b1-4b24-4c6f-a080-24504607145d" alt="Billy Bubble">
    <div id="attributes">
        <h1>Attributes for Billy Bubble</h1>
        <ul>
            <li>Speed: Fast- Bubble sort is known to be one of the fastest sorting algorithms for shorter datasets, however on longer datasets it struggles because of simplistic nature of the sort just comparing two adjacent objects and seeing which one is greater swaping the numbers one by one.</li>
            <li>Strength: Short Datasets- Struggles on longer datasets because switching two numbers at a time pales in comparison to merge sort breaking down the whole dataset and then combining it back in order.</li>
            <li>Endurance: Weak- Can't do longer races (datasets) as efficiently as other sorting algorithms.</li>
        </ul>
    </div>
</div>

<button id="continueButton" onclick="location.href='/miniproject/eventselection'">Continue</button>

</body>
</html>
