---
layout: default
title: Event Selection
permalink: /eventselection
---
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Selection</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
        }
        .container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            grid-gap: 20px;
        }
        .event {
            width: 100%;
            max-width: 500px;
            margin: 0 auto;
            text-align: center;
        }
        .event img {
            width: 100%;
            height: 300px; /* Set a fixed height for both images */
            object-fit: cover;
        }
        .event img:hover {
            border: 5px solid #ffcc00; /* Yellow border on hover */
            transform: scale(1.05); /* Slightly increase size on hover */
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="event">
            <h2>Track Event</h2>
            <a href="/miniproject/track">
                <img alt="Trackfield" src="https://github.com/Code-Demons/miniproject/assets/111464993/b8eb1715-c85b-401d-893c-b11a8f25024a">
            </a>
        </div>
        <div class="event">
            <h2>Ski Event</h2>
            <a href="/miniproject/ski">
                <img alt="Skislope" src="https://github.com/Code-Demons/miniproject/assets/40652645/37a3fadc-9af0-48e6-b529-23b60c2b5064">
            </a>
        </div>
    </div>
</body>