---
layout: default
title: Sammy Select
permalink: /selectionathlete
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sammy Select</title>
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
    <img id="image" src="https://github.com/Code-Demons/miniproject/assets/40652645/ce479d7a-0c77-4b9e-8f99-453e365403ac" alt="Sammy Select">
    <div id="attributes">
        <h1>Attributes for Sammy Select</h1>
        <ul>
            <li><b>Speed:</b> Fast- Selection sort is one of the fastest sorting algorithms due to its extremely simplsitic nature. It works by just finding the smallest element and moving it to the front then going through it agian and finding the second smallest element and moving it to the second and so forth.</li>
            <li><b>Strength:</b> Arrays with fewer than 20 elements- Due to its simple nature on arrays longer than 20 elements it struggles and is more and more slower the longer the dataset is. </li>
            <li><b>Endurance:</b> Weak- When the data is shorter selection sort works the best due to the fact it reads the array faster the shorter it is so its able to find the next shortest element easier.</li>
        </ul>
    </div>
</div>

<button id="continueButton" onclick="location.href='/miniproject/eventselection'">Continue</button>

</body>
</html>