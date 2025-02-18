<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🎉 ¡Feliz Cumpleaños! 🎂</title>
    <style>
        body {
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            font-family: 'Arial', sans-serif;
            text-align: center;
            color: #fff;
            overflow: hidden;
        }
        h1 {
            font-size: 3rem;
            margin-top: 20vh;
            animation: fadeIn 2s ease-in-out;
        }
        .message {
            font-size: 1.5rem;
            margin: 20px;
            opacity: 0;
            animation: fadeIn 3s ease-in-out 1s forwards;
        }
        .balloons {
            position: absolute;
            width: 100%;
            height: 100vh;
            pointer-events: none;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>
    <h1>🎉 ¡Feliz Cumpleaños! 🎂</h1>
    <p class="message">Espero que tengas un día increíble, lleno de amor y felicidad. 🎈💖</p>
    <canvas class="balloons"></canvas>
    <script>
        const canvas = document.querySelector('.balloons');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        
        const balloons = [];
        for (let i = 0; i < 30; i++) {
            balloons.push({
                x: Math.random() * canvas.width,
                y: canvas.height + Math.random() * 100,
                r: Math.random() * 20 + 10,
                speed: Math.random() * 2 + 1,
                color: `hsl(${Math.random() * 360}, 100%, 75%)`
            });
        }
        
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            balloons.forEach(b => {
                ctx.beginPath();
                ctx.arc(b.x, b.y, b.r, 0, Math.PI * 2);
                ctx.fillStyle = b.color;
                ctx.fill();
                b.y -= b.speed;
                if (b.y < -20) b.y = canvas.height + 20;
            });
            requestAnimationFrame(animate);
        }
        animate();
    </script>
</body>
</html>
