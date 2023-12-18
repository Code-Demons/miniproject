---
layout: default
title: Issac Insert
permalink: /insertathlete
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Issac Insert</title>
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
    <img id="image" src="https://github.com/Code-Demons/miniproject/assets/40652645/78f15b09-37f0-441b-b230-3d3663347a38" alt="Issac Insert">
    <div id="attributes">
        <h1>Attributes for Issac Insert</h1>
        <ul>
           <li><b>Speed:</b> with a speed of O(n^2) the speed of insertion sort is comparable to other sorting algorithms like it. </li>
            <li><b>Strength:</b> Partially completed arrays. Insertion Sort is preferred for fewer elements. It becomes fast when data is already sorted or nearly sorted because it skips the sorted values. Additionally, Insertion sort has less space complexity. Insertion sort only takes O(1) auxiliary space complexity. It sorts the entire array just by using an extra variable.</li>
            <li><b>Endurance:</b> Insertion sort is efficient for small data values. Large numbers and large data sets slow this algorithm down as it analyzes each element in an array several times each.</li>
        </ul>
    </div>
</div>

<button id="continueButton" onclick="location.href='/miniproject/eventselection'">Continue</button>

</body>
</html>