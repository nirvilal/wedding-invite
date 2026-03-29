<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Nirvi & Vidhant</title>

<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Playfair+Display:wght@400;600&family=Cormorant+Garamond:wght@300;400&display=swap" rel="stylesheet">

<style>

body {
  margin: 0;
  font-family: 'Cormorant Garamond', serif;
  background: linear-gradient(#f7e7d3, #f3d6a4);
  color: #5a3e2b;
  text-align: center;
}

/* ===== ENVELOPE ===== */
.envelope-container {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.envelope {
  width: 300px;
  height: 190px;
  background: linear-gradient(#f3d6a4, #e0b76a);
  border-radius: 6px;
  position: relative;
  cursor: pointer;
  box-shadow: 0 25px 50px rgba(0,0,0,0.2);
}

.flap {
  width: 100%;
  height: 100%;
  background: linear-gradient(#e0b76a, #c9972b);
  position: absolute;
  top: 0;
  transform-origin: top;
  transition: transform 1s ease;
}

.open .flap {
  transform: rotateX(180deg);
}

/* ===== MAIN CARD ===== */
.card {
  max-width: 700px;
  margin: 100px auto;
  background: #fffaf3;
  padding: 60px 40px;
  border-radius: 12px;
  box-shadow: 0 20px 60px rgba(0,0,0,0.15);
  position: relative;
  border: 1px solid rgba(200,150,60,0.3);
}

/* INNER BORDER */
.card::before {
  content: "";
  position: absolute;
  inset: 15px;
  border: 1px solid rgba(200,150,60,0.4);
  border-radius: 8px;
}

/* FLORALS */
.floral-top {
  position: absolute;
  top: 0;
  right: 0;
  width: 180px;
  opacity: 0.5;
}

.floral-bottom {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 180px;
  opacity: 0.5;
  transform: rotate(180deg);
}

/* WAX SEAL */
.seal {
  position: absolute;
  top: -35px;
  left: 50%;
  transform: translateX(-50%);
  width: 70px;
  height: 70px;
  background: radial-gradient(circle at 30% 30%, #f2d27a, #c9972b);
  border-radius: 50%;
  box-shadow: 0 5px 15px rgba(0,0,0,0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Playfair Display';
  color: white;
  font-size: 26px;
}

/* TEXT */
h1 {
  font-family: 'Great Vibes', cursive;
  font-size: 56px;
  margin: 15px 0;
}

h2 {
  font-family: 'Playfair Display', serif;
  font-size: 28px;
  margin-top: 30px;
}

p {
  font-size: 18px;
  line-height: 1.7;
}

/* BUTTON */
.btn {
  margin-top: 30px;
  padding: 14px 34px;
  background: linear-gradient(#c9972b, #a87c1f);
  color: white;
  border-radius: 30px;
  text-decoration: none;
  display: inline-block;
  box-shadow: 0 5px 20px rgba(0,0,0,0.2);
}

/* COUNTDOWN */
#countdown {
  margin-top: 15px;
  font-size: 20px;
}

/* FADE */
.fade {
  animation: fadeUp 1.2s ease;
}

@keyframes fadeUp {
  from {opacity:0; transform:translateY(40px);}
  to {opacity:1; transform:translateY(0);}
}

.hidden { display:none; }

</style>
</head>

<body>

<!-- ENVELOPE -->
<div class="envelope-container" id="envelopePage">
  <h2>You’re Invited</h2>
  <div class="envelope" onclick="openEnvelope()">
    <div class="flap"></div>
  </div>
  <p>Tap to Open</p>
</div>

<!-- INVITATION -->
<div id="mainContent" class="hidden">

<div class="card fade">

  <!-- FLORALS -->
  <img class="floral-top" src="https://i.imgur.com/6XbKQ8D.png">
  <img class="floral-bottom" src="https://i.imgur.com/6XbKQ8D.png">

  <!-- SEAL -->
  <div class="seal">N</div>

  <h2>You’re Invited</h2>

  <p>With the blessings of</p>
  <p>Late Shantilal Devchand and Late Jaswantiben Shantilal</p>

  <p>Together with</p>
  <p><b>Ranjit Lal & Veena Lal</b></p>

  <p>We have the pleasure of inviting you  
  to celebrate the wedding festivities  
  of our beloved daughter</p>

  <h1>Nirvi</h1>
  <p>with</p>
  <h1>Vidhant</h1>

  <p>Son of Late Krishna Nambiar  
  and Charlotte Nambiar</p>

</div>

<div class="card fade">
  <h2>Grah Shantak & Haldi</h2>
  <p>4th December 2026</p>
</div>

<div class="card fade">
  <h2>Wedding Ceremony</h2>
  <p>5th December 2026</p>
</div>

<div class="card fade">
  <h2>Reception</h2>
  <p>6th December 2026</p>
</div>

<div class="card fade">
  <h2>Countdown to our forever</h2>
  <div id="countdown"></div>
</div>

<div class="card fade">
  <h2>RSVP</h2>
  <a class="btn" href="YOUR_GOOGLE_FORM_LINK" target="_blank">RSVP Now</a>
</div>

</div>

<script>
function openEnvelope() {
  document.querySelector('.envelope').classList.add('open');
  setTimeout(() => {
    document.getElementById('envelopePage').style.display = 'none';
    document.getElementById('mainContent').classList.remove('hidden');
  }, 900);
}

/* Countdown */
var countDownDate = new Date("Dec 5, 2026 00:00:00").getTime();

setInterval(function() {
  var now = new Date().getTime();
  var d = countDownDate - now;

  var days = Math.floor(d / (1000*60*60*24));
  var h = Math.floor((d%(1000*60*60*24))/(1000*60*60));
  var m = Math.floor((d%(1000*60*60))/(1000*60));
  var s = Math.floor((d%(1000*60))/1000);

  document.getElementById("countdown").innerHTML =
  days + " days " + h + " hrs " + m + " min " + s + " sec";

}, 1000);
</script>

</body>
</html>
