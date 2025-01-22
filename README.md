<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: #00627a;
            color: #333;
            text-align: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            position: relative;
            overflow: hidden; /* Hide overflowing confetti */
        }

        /* Confetti effect */
.confetti {
    position: absolute;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    pointer-events: none;
    opacity: 0;
    animation: fall 4s cubic-bezier(0.42, 0, 0.58, 1) infinite, move 3s linear infinite;
    z-index: -2;
}

@keyframes fall {
    0% {
        transform: translateY(-10px);
        opacity: 1;
    }
    100% {
        transform: translateY(100vh);
        opacity: 0;
    }
}

@keyframes move {
    0% { transform: translateX(0); }
    50% { transform: translateX(50px); }
    100% { transform: translateX(-50px); }
        }

        @keyframes fall {
            0% {
                transform: translateY(-10px);
                opacity: 1;
            }
            100% {
                transform: translateY(100vh);
                opacity: 0;
            }
        }

        @keyframes move {
            0% {
                transform: translateX(0);
            }
            50% {
                transform: translateX(50px);
            }
            100% {
                transform: translateX(-50px);
            }
        }

        /* Add background images around the edges */
        .background-images {
            position: absolute;
            top: 0;
            left: 20%;
            width: 60%;
            height: 100%;  /* Full height for vertical centering */
            z-index: -1;
            pointer-events: none;
        }

        .background-images img {
            position: absolute;
            width: 200px;
            opacity: 0; /* Initially hidden for transition */
            border-radius: 15px;
            border: 5px solid #41f2ff;
            padding: 5px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            transform: rotate(calc(45deg * (Math.random() > 0.5 ? 1 : -1)));
            animation: fadeInSlide 2s ease-out forwards;
        }

        .background-images img.top-left {
            top: 5%;
            left: -20%;
            animation-delay: 0.2s;
        }

        .background-images img.top-right {
            top: 10%;
            right: -20%;
            animation-delay: 0.4s;
        }

        .background-images img.bottom-left {
            bottom: 12%;
            left: -20%;
            animation-delay: 0.6s;
        }

        .background-images img.bottom-right {
            bottom: 10%;
            right: -20%;
            animation-delay: 0.8s;
        }

.background-images img.left-center {
    top: 35%; /* 50% - 15% */
    left: 0;
    transform: translateY(-50%);
    animation-delay: 1s;
}

.background-images img.right-center {
    top: 35%; /* 50% - 15% */
    right: 0;
    transform: translateY(-50%);
    animation-delay: 1.2s;
}


        .card {
            background: rgb(255, 255, 255);
            border-radius: 15px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            padding: 20px;
            max-width: 400px;
            text-align: center;
            z-index: 1;
        }

        .card h1 {
            font-size: 2.5em;
            color: #e639dd;
        }

        .card p {
            font-size: 1.2em;
            margin: 20px 0;
        }

        .buttons {
            margin-top: 20px;
        }

        .buttons button {
            border: none;
            padding: 10px 20px;
            margin: 0 10px;
            border-radius: 5px;
            font-size: 1em;
            color: white;
            cursor: pointer;
            background: #6a0572;
            transition: background 0.3s, transform 0.2s;
        }

        .buttons button:hover {
            background: #8d1e9e;
            transform: scale(1.05);
        }

        .buttons button.no {
            background: #c82a2a;
        }

        .buttons button.no:hover {
            background: #ff4040;
        }

        #message {
            margin-top: 20px;
            font-size: 1.3em;
            color: #4caf50;
            display: none;
        }

        #picture {
            margin-top: 20px;
            display: none;
        }

        #picture img {
            max-width: 100%;
            border-radius: 10px;
        }

        #black-screen {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: black;
            z-index: 10;
            justify-content: center;
            align-items: center;
        }

        #black-screen img {
            max-width: 90%;
            max-height: 90%;
            border-radius: 15px;
            border: 5px solid white;
        }

        /* Animation for fade-in with sliding effect */
        @keyframes fadeInSlide {
            0% {
                transform: translateX(100%);
                opacity: 0;
            }
            50% {
                opacity: 1;
            }
            100% {
                transform: translateX(0);
                opacity: 1;
            }
        }
    </style>
</head>
<body>
    <!-- Confetti Container -->
    <div id="confetti-container"></div>

    <!-- Background images -->
    <div class="background-images">
        <img src="top_left.jpeg" alt="Top Left Image" class="top-left">
        <img src="top_right.jpg" alt="Top Right Image" class="top-right">
        <img src="middle_left.jpg" alt="Middle Left Image" class="bottom-left">
        <img src="middle_right.jpg" alt="Middle Right Image" class="bottom-right">
        <img src="bottom_left.jpg" alt="Bottom Left Image" class="left-center">
        <img src="botton_right.jpg" alt="Bottom Right Image" class="right-center">
    </div>

    <div class="card">
        <h1>Valentine's Day</h1>
        <p>You bring so much joy into my life and so many good memories. You make me the happiest man on this planet each day, and you’re a really special person to me, so I would like to ask, would you be my Valentine this year?</p>
        <div class="buttons">
            <button onclick="showMessage()">Yes!</button>
            <button id="noButton" class="no" onclick="showRejection()">No :(</button>
        </div>
        <div id="message"></div>
        <div id="picture">
            <img src="" alt="Special Image" id="specialImage">
        </div>
    </div>

    <div id="black-screen">
        <img src="sadcat.gif" alt="Sad Cat">
    </div>

    <!-- Add the audio element for playing the MP3 -->
    <audio id="sadAudio" src="sad.mp3" preload="auto"></audio>

    <script>
        let confettiInterval;

        function getRandomColor() {
            // Random color generator
            const colors = ['#ff6b6b', '#ffb84d', '#f0e130', '#4b8b3b', '#c6b3e8', '#ff6bbf', '#ff66b3'];
            return colors[Math.floor(Math.random() * colors.length)];
        }

        function createConfetti() {
            const container = document.getElementById('confetti-container');
            const confetti = document.createElement('div');
            confetti.classList.add('confetti');
            
            // Randomize the confetti's size, color, and animation timing
            const size = Math.random() * 10 + 5; // Confetti size
            const leftPosition = Math.random() * window.innerWidth; // Horizontal position (full width)
            const topPosition = Math.random() * window.innerHeight; // Vertical position (full height)
            const animationDelay = Math.random() * 2 + 's'; // Random animation delay
            const color = getRandomColor(); // Random color

            confetti.style.width = `${size}px`;
            confetti.style.height = `${size}px`;
            confetti.style.left = `${leftPosition}px`;
            confetti.style.top = `${topPosition}px`; // Position across the whole height
            confetti.style.animationDelay = animationDelay;
            confetti.style.backgroundColor = color; // Assign random color

            container.appendChild(confetti);

            // Remove confetti after it falls to avoid memory leaks
            setTimeout(() => {
                confetti.remove();
            }, 4000); // Remove confetti after 4 seconds
        }

        function startConfetti() {
            confettiInterval = setInterval(createConfetti, 100); // Create confetti every 100ms
        }

        function stopConfetti() {
            clearInterval(confettiInterval); // Stop the confetti after some time or condition
        }

        function showMessage() {
            const messageDiv = document.getElementById('message');
            messageDiv.style.display = 'block';
            messageDiv.innerHTML = "YAY! I LOVE YOU SO MUCH CARIÑO💙";

            const pictureDiv = document.getElementById('picture');
            const img = document.getElementById('specialImage');
            img.src = "https://i.imgur.com/3i6t5Xs.gif";
            img.alt = "Cute kitten GIF";
            pictureDiv.style.display = 'block';

            const noButton = document.getElementById('noButton');
            noButton.disabled = true;
            noButton.classList.add('disabled');

            // Start confetti
            startConfetti();
        }

        function showRejection() {
            const messageDiv = document.getElementById('message');
            messageDiv.style.display = 'block';
            messageDiv.innerHTML = "Okay, maybe next time... 😢";
            
            // Show sad cat gif and hide black screen
            const blackScreen = document.getElementById('black-screen');
            blackScreen.style.display = 'flex';

            // Reset background and picture
            const pictureDiv = document.getElementById('picture');
            pictureDiv.style.display = 'none';

            // Stop confetti
            stopConfetti();

            // Play audio after pressing "No"
            const audio = document.getElementById('sadAudio');
            audio.play();
        }
    </script>
    <script>
    const music = document.getElementById('background-music');

    function stopMusic() {
        music.pause();
        music.currentTime = 0; // Reset to the beginning
    }
</script>
</body>
</html>
