<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Smash or Pass</title>
<style>
body{
margin:0;
background:#0f0f0f;
font-family:Arial;
color:white;
overflow:hidden;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
flex-direction:column;
}
.container{
display:flex;
flex-direction:column;
align-items:center;
}
.card{
width:320px;
height:420px;
border-radius:20px;
overflow:hidden;
background:#222;
box-shadow:0 0 20px rgba(0,0,0,0.5);
}
.card img{
width:100%;
height:100%;
object-fit:cover;
}
.buttons{
position:fixed;
bottom:20px;
display:flex;
gap:20px;
}
button{
padding:12px 18px;
border:none;
border-radius:10px;
font-size:16px;
cursor:pointer;
font-weight:bold;
}
#smash{
background:#4dff88;
}
#pass{
background:#ff4d4d;
color:white;
}
.popup{
position:fixed;
top:40%;
font-size:50px;
font-weight:bold;
display:none;
text-shadow:0 0 10px black;
}
</style>
</head>
<body>
<div class="container">
<div class="card">
<img id="img" src="">
</div>
</div>

<div class="popup" id="popup"></div>

<div class="buttons">
<button id="pass">Pass 👎</button>
<button id="smash">Smash 🔥</button>
</div>

<script>
let images=[
"images/IMG_2583.jpeg",
"images/IMG_2584.jpeg",
"images/IMG_2585.jpeg",
"images/IMG_2586.jpeg",
"images/IMG_2587.jpeg",
"images/IMG_2588.jpeg",
"images/IMG_2589.jpeg",
"images/IMG_2590.jpeg",
"images/IMG_2591.jpeg",
"images/IMG_2592.jpeg"
];

let index=0;

const img=document.getElementById("img");
const popup=document.getElementById("popup");

function load(){
if(index>=images.length){
popup.innerText="DONE";
popup.style.color="white";
popup.style.display="block";
document.querySelector(".card").style.display="none";
document.querySelector(".buttons").style.display="none";
return;
}
img.src=images[index];
}

function next(text,color){
popup.innerText=text;
popup.style.color=color;
popup.style.display="block";

setTimeout(()=>{
popup.style.display="none";
},500);

index++;
load();
}

document.getElementById("smash").onclick=()=>next("SMASH 🔥","lime");
document.getElementById("pass").onclick=()=>next("PASS 👎","red");

load();
</script>
</body>
</html>