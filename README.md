<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Surprise</title>
<style>
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        text-align: center;
        background-color: #ffccf9;
    }
    section {
        display: none;
        padding: 50px;
    }
    section.active {
        display: block;
    }
    h1 {
        font-size: 3em;
        color: #ff3d68;
    }
    button {
        background-color: #ff3d68;
        color: white;
        padding: 15px 30px;
        border: none;
        border-radius: 8px;
        cursor: pointer;
        font-size: 1.2em;
    }
    button:hover {
        background-color: #ff6289;
    }
</style>
</head>
<body>

<!-- Page 1 -->
<section id="page1" class="active">
    <h1>🎉 Happy Birthday! 🎉</h1>
    <p>Click below for your surprise!</p>
    <button onclick="startMusicAndNext()">Next 🎵</button>
</section>

<!-- Page 2 -->
<section id="page2">
    <h1>🎂 Wishing you a wonderful year ahead! 🎂</h1>
    <p>Enjoy the music and celebration! 🎶</p>
    <img src="https://source.unsplash.com/400x300/?birthday,cake" alt="Birthday Cake">
</section>

<!-- Music -->
<audio id="bg-music" src="Blue – Yung Kai _ English Song Ringtone Download - MobCup.Com.Co.mp3"></audio>

<!-- Confetti -->
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
<script>
function showPage(pageId) {
    document.querySelectorAll('section').forEach(sec => sec.classList.remove('active'));
    document.getElementById(pageId).classList.add('active');
    launchConfetti();
}

function launchConfetti() {
    let duration = 3 * 1000;
    let end = Date.now() + duration;

    (function frame() {
        confetti({
            particleCount: 6,
            angle: 60,
            spread: 55,
            origin: { x: 0 }
        });
        confetti({
            particleCount: 6,
            angle: 120,
            spread: 55,
            origin: { x: 1 }
        });

        if (Date.now() < end) {
            requestAnimationFrame(frame);
        }
    }());
}

function startMusicAndNext() {
    let music = document.getElementById("bg-music");
    music.volume = 1.0;
    music.play();
    showPage('page2');
}
</script>

</body>
</html>
