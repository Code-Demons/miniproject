---
layout: default
title: Selection
permalink: /selection
---
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    .athlete-selector {
      display: flex;
      justify-content: space-around;
      margin-top: 50px;
    }
    .athlete-option {
      display: flex;
      flex-direction: column;
      align-items: center;
      position: relative;
      cursor: pointer;
      transition: transform 0.3s ease-in-out;
    }
    .athlete-option:hover {
      transform: scale(1.2);
    }
    .athlete-option img {
      width: 150px;
      height: 225px;
      border-radius: 50%;
    }
    .athlete-option span {
      margin-top: 10px;
      font-weight: bold;
    }
    /* Specific image for Bubble Athlete */
    .athlete-option.bubble:hover img {
      content: url("https://github.com/Code-Demons/miniproject/assets/40652645/213c0a9e-9c56-4484-9d69-3d1cc5984a5a");
    }
    /* Specific image for Merge Athlete */
    .athlete-option.merge:hover img {
      content: url("https://github.com/Code-Demons/miniproject/assets/40652645/adb81563-7fda-47ac-981a-620550ef59e9");
    }
    /* Specific image for Selection Athlete */
    .athlete-option.selection:hover img {
      content: url("https://github.com/Code-Demons/miniproject/assets/40652645/4f671c77-a146-4df5-9100-235d6c833a41");
    }
    .athlete-option.insertion:hover img {
      content: url("https://github.com/Code-Demons/miniproject/assets/40652645/6d08b64d-399b-4a93-98ab-cc179eb4ced5");
    }
    #attribute-section {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      background-color: #f0f0f0;
      padding: 20px;
      display: none;
    }
  </style>
</head>
<body>

  <div class="athlete-selector">
    <!-- Bubble Athlete -->
    <div class="athlete-option bubble" onmouseover="showAttributes('Billy Bubble Attributes')" onmouseout="hideAttributes()">
      <img src="https://github.com/Code-Demons/miniproject/assets/40652645/4049e8b1-4b24-4c6f-a080-24504607145d" alt="Bubble Athlete">
      <span>Billy Bubble</span>
    </div>
    <!-- Merge Athlete -->
    <div class="athlete-option merge" onmouseover="showAttributes('Martin Merge Attributes')" onmouseout="hideAttributes()">
      <img src="https://github.com/Code-Demons/miniproject/assets/40652645/245c81fd-0ccd-4a52-acee-af09a34baaad" alt="Merge Athlete">
      <span>Martin Merge</span>
    </div>
    <!-- Sammy Select Athlete -->
    <div class="athlete-option selection" onmouseover="showAttributes('Sammy Select Attributes')" onmouseout="hideAttributes()">
      <img src="https://github.com/Code-Demons/miniproject/assets/40652645/bb500c0a-102e-42db-99c8-b70deb62305b" alt="Selection Athlete">
      <span>Sammy Select</span>
    </div>
    <!-- Issac Insert Athlete -->
    <div class="athlete-option insertion" onmouseover="showAttributes('Issac Insert Attributes')" onmouseout="hideAttributes()">
      <img src="https://github.com/Code-Demons/miniproject/assets/40652645/78f15b09-37f0-441b-b230-3d3663347a38" alt="Insertion Athlete">
      <span>Issac Insert</span>
    </div>
  </div>
  
  <div id="attribute-section"></div>

  <script>
    function showAttributes(attributes) {
      document.getElementById("attribute-section").innerHTML = attributes;
      document.getElementById("attribute-section").style.display = "block";
    }

    function hideAttributes() {
      document.getElementById("attribute-section").style.display = "none";
    }
  </script>

</body>
</html>



<!-- Insertion Sort Athlete
https://github.com/Code-Demons/miniproject/assets/40652645/78f15b09-37f0-441b-b230-3d3663347a38 Not Selected

https://github.com/Code-Demons/miniproject/assets/40652645/6d08b64d-399b-4a93-98ab-cc179eb4ced5 Selected-->