<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Retro Space Shooter</title>
    <style>
        body {
            margin: 0;
            background: #000;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: 'Courier New', Courier, monospace;
        }
        canvas {
            border: 4px solid #fff;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.2);
            background: #050510;
        }
    </style>
</head>
<body>

<canvas id="gameCanvas" width="800" height="600"></canvas>

<script>
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

// Game State
let score = 0;
let gameOver = false;
const keys = {};

// Player Setup
const player = {
    x: canvas.width / 2 - 20,
    y: canvas.height - 60,
    width: 40,
    height: 40,
    speed: 6,
    color: "#00ffcc"
};

// Arrays for Game Objects
const bullets = [];
const enemies = [];
const particles = [];

// Event Listeners for Controls
window.addEventListener("keydown", (e) => keys[e.key] = true);
window.addEventListener("keyup", (e) => keys[e.key] = false);

// Handle Shooting Rate
let lastShot = 0;
const fireRate = 200; // ms

function spawnEnemy() {
    if (gameOver) return;
    const size = Math.random() * 30 + 20;
    enemies.push({
        x: Math.random() * (canvas.width - size),
        y: -size,
        width: size,
        height: size,
        speed: Math.random() * 2 + 2,
        color: `hsl(${Math.random() * 360}, 80%, 60%)`
    });
    // Random interval for next spawn
    setTimeout(spawnEnemy, Math.random() * 1000 + 600);
}

function createExplosion(x, y, color) {
    for (let i = 0; i < 15; i++) {
        particles.push({
            x: x,
            y: y,
            vx: (Math.random() - 0.5) * 6,
            vy: (Math.random() - 0.5) * 6,
            alpha: 1,
            color: color,
            size: Math.random() * 3 + 1
        });
    }
}

// Main Game Loop
function update() {
    if (gameOver) return;

    // Player Movement
    if ((keys["ArrowLeft"] || keys["a"]) && player.x > 0) player.x -= player.speed;
    if ((keys["ArrowRight"] || keys["d"]) && player.x < canvas.width - player.width) player.x += player.speed;

    // Shooting
    if (keys[" "] || keys["Enter"]) {
        const now = Date.now();
        if (now - lastShot > fireRate) {
            bullets.push({
                x: player.x + player.width / 2 - 3,
                y: player.y,
                width: 6,
                height: 15,
                speed: 8,
                color: "#ff0055"
            });
            lastShot = now;
        }
    }

    // Move Bullets
    for (let i = bullets.length - 1; i >= 0; i--) {
        bullets[i].y -= bullets[i].speed;
        if (bullets[i].y < 0) bullets.splice(i, 1);
    }

    // Move Enemies
    for (let i = enemies.length - 1; i >= 0; i--) {
        enemies[i].y += enemies[i].speed;

        // Check Collision with Player
        if (
            enemies[i].x < player.x + player.width &&
            enemies[i].x + enemies[i].width > player.x &&
            enemies[i].y < player.y + player.height &&
            enemies[i].y + enemies[i].height > player.y
        ) {
            gameOver = true;
            createExplosion(player.x + player.width/2, player.y + player.height/2, player.color);
        }

        // Remove if off-screen
        if (enemies[i].y > canvas.height) {
            enemies.splice(i, 1);
        }
    }

    // Handle Particles
    for (let i = particles.length - 1; i >= 0; i--) {
        particles[i].x += particles[i].vx;
        particles[i].y += particles[i].vy;
        particles[i].alpha -= 0.02;
        if (particles[i].alpha <= 0) particles.splice(i, 1);
    }

    // Bullet & Enemy Collision Detection
    for (let b = bullets.length - 1; b >= 0; b--) {
        for (let e = enemies.length - 1; e >= 0; e--) {
            if (
                bullets[b] &&
                bullets[b].x < enemies[e].x + enemies[e].width &&
                bullets[b].x + bullets[b].width > enemies[e].x &&
                bullets[b].y < enemies[e].y + enemies[e].height &&
                bullets[b].y + bullets[b].height > enemies[e].y
            ) {
                createExplosion(enemies[e].x + enemies[e].width/2, enemies[e].y + enemies[e].height/2, enemies[e].color);
                enemies.splice(e, 1);
                bullets.splice(b, 1);
                score += 10;
                break;
            }
        }
    }
}

function draw() {
    // Clear Canvas
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    if (!gameOver) {
        // Draw Player (Spaceship Triangle)
        ctx.fillStyle = player.color;
        ctx.beginPath();
        ctx.moveTo(player.x + player.width / 2, player.y);
        ctx.lineTo(player.x, player.y + player.height);
        ctx.lineTo(player.x + player.width, player.y + player.height);
        ctx.closePath();
        ctx.fill();
    }

    // Draw Bullets
    bullets.forEach(b => {
        ctx.fillStyle = b.color;
        ctx.fillRect(b.x, b.y, b.width, b.height);
    });

    // Draw Enemies
    enemies.forEach(e => {
        ctx.fillStyle = e.color;
        ctx.fillRect(e.x, e.y, e.width, e.height);
    });

    // Draw Particles
    particles.forEach(p => {
        ctx.save();
        ctx.globalAlpha = p.alpha;
        ctx.fillStyle = p.color;
        ctx.fillRect(p.x, p.y, p.size, p.size);
        ctx.restore();
    });

    // Draw Score
    ctx.fillStyle = "#fff";
    ctx.font = "20px 'Courier New'";
    ctx.fillText(`SCORE: ${score}`, 20, 40);

    // Game Over Screen
    if (gameOver) {
        ctx.fillStyle = "rgba(0, 0, 0, 0.8)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        ctx.fillStyle = "#ff0055";
        ctx.font = "40px 'Courier New'";
        ctx.textAlign = "center";
        ctx.fillText("GAME OVER", canvas.width / 2, canvas.height / 2 - 20);
        
        ctx.fillStyle = "#fff";
        ctx.font = "20px 'Courier New'";
        ctx.fillText(`Final Score: ${score}`, canvas.width / 2, canvas.height / 2 + 20);
        ctx.fillText("Refresh Page to Restart", canvas.width / 2, canvas.height / 2 + 60);
    }
}

// Loop Engine
function loop() {
    update();
    draw();
    requestAnimationFrame(loop);
}

// Start Game
spawnEnemy();
loop();
</script>

</body>
</html>
