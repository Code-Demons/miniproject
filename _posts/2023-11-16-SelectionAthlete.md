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
      content: url("https://github.com/Code-Demons/miniproject/assets/40652645/adcf3d8a-8d5a-4605-9dcb-3443fb3f1480");
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
    <div class="athlete-option bubble" onclick="navigateTo('/miniproject/bubbleathlete')" onmouseover="showAttributes('Billy Bubble Attributes')" onmouseout="hideAttributes()">
      <img src="https://github.com/Code-Demons/miniproject/assets/40652645/4049e8b1-4b24-4c6f-a080-24504607145d" alt="Bubble Athlete">
      <span>Billy Bubble</span>
    </div>
    <!-- Merge Athlete -->
    <div class="athlete-option merge" onclick="navigateTo('/miniproject/mergeathlete')" onmouseover="showAttributes('Martin Merge Attributes')" onmouseout="hideAttributes()">
      <img src="https://github.com/Code-Demons/miniproject/assets/40652645/245c81fd-0ccd-4a52-acee-af09a34baaad" alt="Merge Athlete">
      <span>Martin Merge</span>
    </div>
    <!-- Sammy Select Athlete -->
    <div class="athlete-option selection" onclick="navigateTo('/miniproject/selectionathlete')" onmouseover="showAttributes('Sammy Select Attributes')" onmouseout="hideAttributes()">
      <img src="https://github.com/Code-Demons/miniproject/assets/40652645/ce479d7a-0c77-4b9e-8f99-453e365403ac" alt="Selection Athlete">
      <span>Sammy Select</span>
    </div>
    <!-- Issac Insert Athlete -->
    <div class="athlete-option insertion" onclick="navigateTo('/miniproject/insertathlete')" onmouseover="showAttributes('Issac Insert Attributes')" onmouseout="hideAttributes()">
      <img src="https://github.com/Code-Demons/miniproject/assets/40652645/78f15b09-37f0-441b-b230-3d3663347a38" alt="Insertion Athlete">
      <span>Issac Insert</span>
    </div>
  </div>
  
  <div id="attribute-section" onclick="hideFullAttributes()">
    <div id="full-attributes"></div>
  </div>

  <script>
    function showAttributes(attributes) {
      document.getElementById("attribute-section").innerHTML = attributes;
      document.getElementById("attribute-section").style.display = "block";
    }

    function hideAttributes() {
      document.getElementById("attribute-section").style.display = "none";
    }

    function hideFullAttributes() {
      document.getElementById("attribute-section").style.display = "none";

      // Show all athletes
      document.querySelectorAll('.athlete-option').forEach(function(option) {
        option.style.display = 'flex';
      });
    }

    function navigateTo(url) {
      window.location.href = url;
    }
  </script>

</body>
</html>