<html>
<head>
    <style>
        body { background: #000; color: #00FF41; font-family: 'Courier New', monospace; margin: 0; overflow: hidden; }
        canvas { position: absolute; top:0; left:0; z-index: 1; }
        #overlay { position: relative; z-index: 2; padding: 20px; }
        #logs { font-size: 14px; text-shadow: 0 0 5px #0f0; }
        .red-flash { animation: flash 0.5s infinite; color: red; font-weight: bold; }
        @keyframes flash { 50% { opacity: 0; } }
    </style>
</head>
<body>

    <canvas id="matrix"></canvas>
    <div id="overlay">
        <h1>[ SYSTEM_OVERRIDE_INITIATED ]</h1>
        <div id="logs"></div>
    </div>

    <script>
        // 1. Matrix Background
        const c = document.getElementById("matrix");
        const ctx = c.getContext("2d");
        c.height = window.innerHeight; c.width = window.innerWidth;
        const drops = Array(Math.floor(c.width/20)).fill(1);
        setInterval(() => {
            ctx.fillStyle = "rgba(0,0,0,0.05)"; ctx.fillRect(0,0,c.width,c.height);
            ctx.fillStyle = "#0f0";
            drops.map((y, i) => {
                ctx.fillText(String.fromCharCode(65+Math.random()*20), i*20, y*20);
                drops[i] = y*20 > c.height ? 0 : y + 1;
            });
        }, 33);

        // 2. Hacker Logs & Features
        const logBox = document.getElementById('logs');
        const tasks = [
            "SCANNING NETWORK_PERIMETER...",
            "DEVICE ID DETECTED: " + navigator.platform,
            "IP ADDRESS TRACED: 192.168.1.105",
            "CRACKING WHATSAPP_SESSION_TOKENS...",
            "ACCESSING: " + window.location.hostname,
            "<span class='red-flash'>!!! WARNING: PASSWORD BREACH !!!</span>",
            "PASSWORD FOUND: Admin@2026",
            "UPLOADING GALLERY_FILES...",
            "SUCCESS: FULL SYSTEM CONTROL ACQUIRED"
        ];

        let i = 0;
        let int = setInterval(() => {
            if(i < tasks.length) {
                logBox.innerHTML += "> " + tasks[i] + "<br>";
                i++;
            } else {
                clearInterval(int);
                setTimeout(() => { 
                    alert("PRANK HACKED! Relax sweetie, this is just a test!");
                    window.location.href = "https://github.com/u-s-h"; 
                }, 2000);
            }
        }, 1200);
    </script>
</body>
</html>
