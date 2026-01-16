# fire-links
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>My Links</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    height: 100vh;
    overflow: hidden;
    color: white;
}

/* FULLSCREEN VIDEO BACKGROUND */
.video-bg {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -2;
    overflow: hidden;
}

.video-bg video {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

/* Dark overlay */
.overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.3);
    z-index: -1;
}

/* Content */
.card {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
}

h1 {
    font-size: 42px;
    margin-bottom: 20px;
}

.link {
    width: 220px;
    padding: 14px;
    margin: 10px;
    border-radius: 12px;
    text-decoration: none;
    color: white;
    font-size: 20px;
    transition: transform 0.2s;
}

.link:hover {
    transform: scale(1.05);
}

.steam {
    background: #171a21;
}

.discord {
    background: #5865F2;
}

/* Volume Slider */
.volume-container {
    margin-top: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
    color: black;
}

.volume-container input[type=range] {
    width: 200px;
}
</style>
</head>
<body>

<!-- BACKGROUND VIDEO -->
<div class="video-bg">
    <video autoplay muted loop playsinline>
        <source src="background.mp4" type="video/mp4">
        Your browser does not support HTML5 video.
    </video>
</div>

<div class="overlay"></div>

<!-- CONTENT -->
<div class="card">
    <h1>My Links</h1>

    <!-- CHANGE THESE LINKS ONLY -->
    <a class="link steam"
       href="https://steamcommunity.com/profiles/76561198904313693/"
       target="_blank">
        Steam
    </a>

    <a class="link discord"
       href="https://discord.com/users/698124165932384336"
       target="_blank">
        Discord
    </a>

    <!-- BACKGROUND MUSIC -->
    <audio id="bgMusic" loop muted>
        <source src="mySong.mp3" type="audio/mpeg">
        Your browser does not support audio playback.
    </audio>

    <!-- VOLUME SLIDER -->
    <div class="volume-container">
        <label for="volumeSlider">Volume</label>
        <input type="range" id="volumeSlider" min="0" max="100" value="100">
    </div>
</div>

<!-- Auto-play + Volume Control Script -->
<script>
window.addEventListener('load', () => {
    const music = document.getElementById('bgMusic');
    const volumeSlider = document.getElementById('volumeSlider');

    // Start music (muted to bypass autoplay restrictions)
    music.play().catch(() => {
        console.log("Autoplay blocked, will start muted");
        music.muted = true;
        music.play();
    });

    // Volume slider control
    volumeSlider.addEventListener('input', () => {
        music.volume = volumeSlider.value / 100; // 0-1
        if(music.muted && volumeSlider.value > 0) {
            music.muted = false; // unmute when slider > 0
        } else if(volumeSlider.value == 0) {
            music.muted = true; // mute if slider at 0
        }
    });
});
</script>

</body>
</html>
