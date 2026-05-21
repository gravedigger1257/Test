<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Smash or Pass</title>

  <style>
    body {
      margin: 0;
      padding: 0;
      background: #111;
      color: white;
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .container {
      text-align: center;
      width: 90%;
      max-width: 500px;
    }

    h1 {
      font-size: 42px;
      margin-bottom: 10px;
    }

    .instructions {
      color: #bbb;
      margin-bottom: 20px;
    }

    .image-box {
      width: 100%;
      height: 500px;
      background: #222;
      border-radius: 20px;
      overflow: hidden;
      margin-bottom: 20px;
    }

    .image-box img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .buttons {
      display: flex;
      justify-content: center;
      gap: 20px;
    }

    button {
      border: none;
      padding: 15px 30px;
      font-size: 20px;
      border-radius: 12px;
      cursor: pointer;
      color: white;
      font-weight: bold;
    }

    .smash {
      background: red;
    }

    .pass {
      background: blue;
    }

    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 60px;
      font-weight: bold;
      z-index: 999;
    }

    .hidden {
      display: none;
    }
  </style>
</head>

<body>

  <div class="container">
    <h1>Smash or Pass</h1>

    <p class="instructions">
      Press Smash or Pass for each photo
    </p>

    <div class="image-box">
      <img id="personImage" src="" alt="Random Person">
    </div>

    <div class="buttons">
      <button id="smashBtn" class="smash">SMASH</button>
      <button id="passBtn" class="pass">PASS</button>
    </div>
  </div>

  <div id="overlay" class="overlay hidden">
    <h2 id="overlayText"></h2>
  </div>

  <script>
    const images = [
      "IMG_2534.jpeg",
      "IMG_2549.png",
      "IMG_2550.jpeg",
      "IMG_2551.jpeg",
      "IMG_2552.jpeg",
      "IMG_2553.jpeg",
      "IMG_2554.jpeg",
      "IMG_2555.jpeg",
      "IMG_2556.jpeg",
      "IMG_2557.jpeg"
    ];

    const personImage = document.getElementById("personImage");
    const overlay = document.getElementById("overlay");
    const overlayText = document.getElementById("overlayText");

    function randomImage() {
      const randomIndex = Math.floor(Math.random() * images.length);
      personImage.src = images[randomIndex];
    }

    function showOverlay(text, color) {
      overlay.style.background = color;
      overlayText.textContent = text;
      overlay.classList.remove("hidden");

      setTimeout(() => {
        overlay.classList.add("hidden");
        randomImage();
      }, 1000);
    }

    document.getElementById("smashBtn").addEventListener("click", () => {
      showOverlay("SMASHED", "rgba(255,0,0,0.9)");
    });

    document.getElementById("passBtn").addEventListener("click", () => {
      showOverlay("PASS", "rgba(0,0,255,0.9)");
    });

    randomImage();
  </script>

</body>
</html>
