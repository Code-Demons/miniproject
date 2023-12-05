---
layout: default
title: Event Selection Test
permalink: /eventselectiontest
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
            grid-template-columns: 1fr 1fr;
            grid-gap: 20px;
            z-index: 1; /* Ensure content appears above the video */
        }
        .event {
            position: relative;
            text-align: center;
            color: white; /* Set text color for better visibility */
            transition: transform 0.3s, border 0.3s; /* Adjusted transition */
        }
        .event img {
            width: 100%;
            height: 300px;
            object-fit: cover;
            transition: transform 0.3s, border 0.3s; /* Adjusted transition */
            border: 5px solid transparent; /* Set initial transparent border */
            box-sizing: border-box; /* Include border in width/height calculations */
        }
        .event img:hover {
            border: 5px solid #ffcc00; /* Yellow border on hover */
            transform: scale(1.1); /* Increase scale on hover */
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
                <img alt="Trackfield" src="https://github.com/Code-Demons/miniproject/assets/111464993/b8eb1715-c85b-401d-893c-b11a8f25024a">
                <div class="video-container">
                    <video autoplay muted loop>
                        <source src="https://github.com/Code-Demons/miniproject/assets/40652645/16d8a489-e778-4a76-ae93-39e9224b52ae" type="video/mp4">
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