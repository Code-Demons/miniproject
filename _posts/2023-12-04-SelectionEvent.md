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
        video {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: -1; /* Place the video behind other elements */
            display: none; /* Initially hidden */
            transition: opacity 0.5s; /* Add transition effect */
        }
        .container {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr; /* Adjusted to have three columns */
            grid-gap: 20px;
            z-index: 1;
        }
        .event {
            position: relative;
            text-align: center;
            color: white; /* Set text color for better visibility */
            transition: transform 0.3s, border 0.3s; /* Adjusted transition */
        }
        .event img {
            width: 100%;
            height: 250px;
            object-fit: cover;
            transition: transform 0.3s, border 0.3s, opacity 0.5s; /* Added opacity transition */
            border: 5px solid transparent; /* Set initial transparent border */
            box-sizing: border-box; /* Include border in width/height calculations */
            opacity: 1; /* Set initial opacity */
        }
        .event:not(:hover) img {
            opacity: 0.7; /* Lower opacity for non-hovered images */
        }
        .event img:hover {
            border: 5px solid #ffcc00; /* Yellow border on hover */
            transform: scale(1.1); /* Increase scale on hover */
            opacity: 1; /* Set full opacity on hover */
        }
        .event .video-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            opacity: 0;
        }
        .event:hover .video-container {
            opacity: 1;
        }
        .event:hover video {
            display: block; /* Show the video on hover */
        }
        .event video {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
    </style>
</head>

<body>
    <video autoplay muted loop>
        <source src="https://github.com/Code-Demons/miniproject/assets/40652645/16d8a489-e778-4a76-ae93-39e9224b52ae" type="video/mp4">
    </video>
    <div class="container">
        <div class="event">
            <h2>Track Event</h2>
            <a href="/miniproject/track">
                <img alt="Trackfield" src="https://github.com/Code-Demons/miniproject/assets/40652645/131c0df0-1723-4bd6-81ba-41cec8aa1a57">
                <div class="video-container">
                    <video autoplay muted loop>
                        <source src="https://github.com/Code-Demons/miniproject/assets/40652645/16d8a489-e778-4a76-ae93-39e9224b52ae" type="video/mp4">
                    </video>
                </div>
            </a>
        </div>
        <div class="event">
            <h2>Swimming Event</h2>
            <a href="/miniproject/swimming">
                <img alt="Swimming" src="https://github.com/Code-Demons/miniproject/assets/40652645/33f16454-fa1a-4e86-ab14-fb253ee790cc">
                <div class="video-container">
                    <video autoplay muted loop>
                        <source src="https://github.com/Code-Demons/miniproject/assets/40652645/c444655e-d2b3-459a-bc93-9fe9b16d0d89" type="video/mp4">
                    </video>
                </div>
            </a>
        </div>
        <div class="event">
            <h2>Ski Event</h2>
            <a href="/miniproject/ski">
                <img alt="Skislope" src="https://github.com/Code-Demons/miniproject/assets/40652645/37a3fadc-9af0-48e6-b529-23b60c2b5064">
                <div class="video-container">
                    <video autoplay muted loop>
                        <source src="https://github.com/Code-Demons/miniproject/assets/40652645/050809a8-582c-4a25-a24e-7ce457b76ead" type="video/mp4">
                    </video>
                </div>
            </a>
        </div>
    </div>
</body>


<!-- https://github.com/Code-Demons/miniproject/assets/40652645/c444655e-d2b3-459a-bc93-9fe9b16d0d89 -->