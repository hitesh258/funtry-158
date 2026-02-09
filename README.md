# funtry-158
Valentine try
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: #fff0f3;
            font-family: 'Comic Sans MS', cursive, sans-serif;
            overflow: hidden;
        }

        .card {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            text-align: center;
            z-index: 10;
            max-width: 400px;
        }

        h1 { color: #ff4d6d; margin-bottom: 20px; }

        .btn-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
            align-items: center;
        }

        button {
            padding: 12px 25px;
            font-size: 1.1rem;
            border: none;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        #yesBtn { background-color: #ff4d6d; color: white; }

        #noBtn {
            background-color: #ffb3c1;
            color: white;
            position: relative;
        }

        img { width: 180px; margin-bottom: 10px; border-radius: 10px; }

        /* Floating Hearts Animation */
        .heart {
            position: absolute;
            color: #ff758f;
            font-size: 1.5rem;
            animation: float 4s linear infinite;
            opacity: 0;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="card" id="content">
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpwaHpxZ3M3ZzZ4Nzh4bmh4eGZ4eGZ4eGZ4eGZ4eGZ4eGZ4JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1n/c76IJLufpNUMo/giphy.gif">
        <h1>Will you be my Valentine?</h1>
        <div class="btn-container">
            <button id="yesBtn" onclick="accepted()">Yes</button>
            <button id="noBtn" onmouseover="dodge()">No</button>
        </div>
    </div>

    <script>
        let yesScale = 1;
        const noMessages = ["Wait...", "Think about it!", "Are you sure?", "Please?", "Don't click this!"];

        function dodge() {
            const noBtn = document.getElementById('noBtn');
            const yesBtn = document.getElementById('yesBtn');

            // Move the No button
            const x = Math.random() * (window.innerWidth - 100);
            const y = Math.random() * (window.innerHeight - 50);
            noBtn.style.position = 'fixed';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';

            // Grow the Yes button
            yesScale += 0.3;
            yesBtn.style.transform = scale(${yesScale});

            // Change No button text
            noBtn.innerText = noMessages[Math.floor(Math.random() * noMessages.length)];
        }

        function accepted() {
            document.getElementById('content').innerHTML = `
                <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExNmtuYmx4Z2Y5bXF4eGZ4eGZ4eGZ4eGZ4eGZ4eGZ4eGZ4JmVwPXYxX2ludGVybmFsX2dpZl9ieV9pZCZjdD1n/l0HlIDueXKHuLTuZq/giphy.gif">
                <h1>I knew you'd say Yes! ❤️</h1>
                <p>Can't wait for Feb 14th!</p>
            `;
            createHearts();
        }

        function createHearts() {
            for(let i=0; i<30; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.className = 'heart';
                    heart.innerHTML = '❤️';
                    heart.style.left = Math.random() * 100 + 'vw';
                    heart.style.animationDuration = (Math.random() * 2 + 2) + 's';
                    document.body.appendChild(heart);
                }, i * 100);
            }
        }
    </script>
</body>
</html>
