<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: #f5f5f5; /* Soft gray background */
    }

    .header {
      text-align: center;
      background-color: #fff;
      padding: 20px;
    }

    .images {
      position: relative;
      height: 20em;
      margin: 0 auto;
      overflow: hidden;
      width: 20em;
    }

    #rabbit,
    #love-rabbit,
    #jumping-rabbit {
      position: absolute;
      top: 0;
      left: 0;
      width: 300px;
      height: 300px;
    }

    #rabbit {
      z-index: 1;
    }

    #love-rabbit {
      z-index: 2;
    }

    #jumping-rabbit {
      display: none;
      z-index: 3;
    }

    /* Soft pastel button styles */
    button {
      background-color: #ffd1dc; /* Light pink */
      border: none;
      color: #fff;
      padding: 10px 20px;
      text-align: center;
      text-decoration: none;
      display: inline-block;
      font-size: 20px;
      cursor: pointer;
      border-radius: 5px;
      margin: 5px;
    }

    #yes {
      background-color: #ffb6c1; /* Darker pink */
      z-index: 4;
    }

    #no {
      background-color: #ffb6c1; /* Darker pink */
      z-index: 5;
    }

    h1 {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      font-weight: bold;
      font-size: 36px;
      color: #333;
      margin: 0;
    }

    .buttons-container {
      text-align: center;
      margin-top: 20px;
    }

    #love-message {
      display: none;
      text-align: center;
      margin-top: 15px;
    }
  </style>
  <script>
    var counter = 0;

    function showLoveMessage() {
      var loveMessage = document.getElementById("love-message");
      var jumpingRabbit = document.getElementById("jumping-rabbit");

      // Show the love message and jumping rabbit gif
      loveMessage.style.display = "block";
      jumpingRabbit.style.display = "block";

      // Optional: You can add additional logic or animations here if needed
    }

    function showJumpingRabbit() {
      var jumpingRabbit = document.getElementById("jumping-rabbit");
      jumpingRabbit.style.display = "block";

      // Optional: You can add additional logic or animations here if needed
    }

    function hideJumpingRabbit() {
      var jumpingRabbit = document.getElementById("jumping-rabbit");
      jumpingRabbit.style.display = "none";

      // Optional: You can add additional logic or animations here if needed
    }

    function hideHappyRabbit() {
      var loveRabbit = document.getElementById("love-rabbit");
      loveRabbit.style.display = "none";
    }

    function hideAngryRabbit() {
      var angryRabbit = document.getElementById("rabbit");
      angryRabbit.style.display = "none";
    }

    function yes() {
      var loveMessage = document.getElementById("love-message");
      var jumpingRabbit = document.getElementById("jumping-rabbit");
      var header = document.querySelector(".header");
      var buttonsContainer = document.querySelector(".buttons-container");
      var loveRabbit = document.getElementById("love-rabbit");
      var angryRabbit = document.getElementById("rabbit");

      // Show the updated love message with red color and a soft palette font
      loveMessage.innerHTML = '<p style="font-size: 24px; color: #ff6666; font-weight: bold; font-family: \'Palatino Linotype\', Palatino, serif; margin-top: 15px;">Thank You and I Love You!</p>';

      // Show the love message and jumping rabbit gif
      showLoveMessage();
      showJumpingRabbit();

      // Hide the header and buttons
      header.style.display = "none";
      buttonsContainer.style.display = "none";

      // Hide the happy rabbit and angry rabbit after a delay
      setTimeout(function() {
        hideHappyRabbit();
        hideAngryRabbit();
      }, 1000); // You can adjust the delay time if needed

      // You can add additional logic or animations here if needed
    }

    function randomizeNoButton() {
      var noButton = document.getElementById("no");
      var yesButton = document.getElementById("yes");

      // Randomize the "No" button's position with a larger offset
      var offset = 200;
      var screenWidth = window.innerWidth - noButton.clientWidth - offset;
      var screenHeight = window.innerHeight - noButton.clientHeight - offset;

      var randomX, randomY;

      randomX = Math.floor(Math.random() * screenWidth) + offset;
      randomY = Math.floor(Math.random() * screenHeight) + offset;

      noButton.lastX = randomX;
      noButton.lastY = randomY;

      noButton.style.left = randomX + "px";
      noButton.style.top = randomY + "px";

      // Hide the "Yes" button
      yesButton.style.display = "none";

      // Show the "No" button
      noButton.style.display = "inline-block";
    }

    function no() {
      var yesButton = document.getElementById("yes");
      var noButton = document.getElementById("no");
      var rabbit = document.getElementById("rabbit");
      var loveRabbit = document.getElementById("love-rabbit");
      var jumpingRabbit = document.getElementById("jumping-rabbit");
      var loveMessage = document.getElementById("love-message");
      yesButton.style.width = (parseInt(yesButton.style.width) + 10) + "px";
      yesButton.style.height = (parseInt(yesButton.style.height) + 10) + "px";
      yesButton.style.fontSize = (parseInt(yesButton.style.fontSize) + 2) + "px";
      counter++;

      if (counter == 20) {
        noButton.style.display = "none";
      } else {
        // Randomize the "No" button's position
        randomizeNoButton();

        // Make the "No" button and its text smaller
        var currentSize = parseInt(noButton.style.fontSize) || 20;
        noButton.style.fontSize = (currentSize - 2) + "px";
        noButton.style.width = (parseInt(noButton.style.width) - 5) + "px";
        noButton.style.height = (parseInt(noButton.style.height) - 5) + "px";
      }

      // Hide the happy rabbit after a delay
      hideHappyRabbit();

      // After 1 second, show the happy rabbit and the "Yes" button again
      setTimeout(function() {
        showHappyRabbit();
        yesButton.style.display = "inline-block";
      }, 1000);
    }

    function showHappyRabbit() {
      var loveRabbit = document.getElementById("love-rabbit");
      loveRabbit.style.display = "block";
    }

    function showAngryRabbit() {
      var angryRabbit = document.getElementById("rabbit");
      angryRabbit.style.display = "block";
    }
  </script>
</head>

<body>
  <div class="header">
    <h1>Would you like to be my girlfriend?</h1>
  </div>
  <div class="images">
    <img id="rabbit" src="https://media0.giphy.com/media/4HbyyMq80B29CBCNUs/giphy.gif" alt="An angry rabbit" loading="lazy">
    <img id="love-rabbit" src="https://media2.giphy.com/media/0xhvPJez78AMJMXuCQ/giphy.gif?cid=ecf05e47totrdpsj6acvjl2t3w5or5je9az796zkyu8nd333&ep=v1_gifs_related&rid=giphy.gif&ct=g" loading="lazy">
    <img id="jumping-rabbit" src="https://media0.giphy.com/media/UpYJwrbEnhimG8l4Ks/giphy.gif" alt="A jumping rabbit" style="display: none;" loading="lazy">
  </div>
  <div id="love-message" style="display: none; text-align: center; margin-top: 15px;">
    <p style="font-size: 24px; color: #ff6666; font-weight: bold; font-family: 'Palatino Linotype', Palatino, serif;">Thank You and I Love You!</p>
  </div>
  <div class="buttons-container">
    <button id="yes" onclick="yes()">Yes</button>
    <button id="no" onclick="no()">No</button>
  </div>
</body>

</html>
