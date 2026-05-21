<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Smash or Pass</title>
<style>
body {
margin: 0;
background: #0f0f0f;
font-family: Arial;
color: white;
overflow: hidden;
}
.container {
display: flex;
flex-direction: column;
align-items: center;
padding-top: 20px;
}
.card {
width: 320px;
height: 420px;
border-radius: 20px;
overflow: hidden;
background: #222;
}
.card img {
width: 100%;
height: 100%;
object-fit: cover;
}
.buttons {
position: fixed;
bottom: 20px;
display: flex;
gap: 20px;
}
button {
padding: 12px 18px;
border: none;
border-radius: 10px;
font-size: 16px;
cursor: pointer;
}
#smash {
background: #4dff88;
}
#pass {
background: #ff4d4d;
color: white;
}
.popup {
position: fixed;
top: 40%;
font-size: 50px;
font-weight: bold;
display: none;
}
</style>
</head>
<body>
<div class="container">
<div class="card">
<img id="img" src="" />
</div>
</div>
<div class="popup" id="popup"></div>
<div class="buttons">
<button id="pass">Pass 👎</button>
<button id="smash">Smash 🔥</button>
</div>
<script>
// =====================
// IMAGES
// =====================
let images = [
"IMG_2583.jpeg",
"IMG_2584.jpeg",
"IMG_2585.jpeg",
"IMG_2586.jpeg",
"IMG_2587.jpeg",
"IMG_2588.jpeg",
"IMG_2589.jpeg",
"IMG_2590.jpeg",
"IMG_2591.jpeg",
"IMG_2592.jpeg"
];
let index = 0;
const img = document.getElementById("img");
const popup = document.getElementById("popup");
// =====================
// GET CORRECT GITHUB PAGES PATH
// =====================
function getBasePath() {
const pathParts = window.location.pathname.split("/");
return "/" + pathParts[1] + "/";
}
// =====================
// LOAD IMAGE (FIXED)
// =====================
function load() {
if (index >= images.length) {
popup.innerText = "DONE";
popup.style.display = "block";
return;
}
img.src = getBasePath() + images[index];
}
// =====================
// NEXT IMAGE
// =====================
function next(text, color) {
popup.innerText = text;
popup.style.color = color;
popup.style.display = "block";
setTimeout(() => {
popup.style.display = "none";
}, 500);
index++;
load();
}
// =====================
// BUTTONS
// =====================
document.getElementById("smash").onclick = () => next("SMASH 🔥", "lime");
document.getElementById("pass").onclick = () => next("PASS 👎", "red");
// =====================
load();
</script>
</body>
</html>