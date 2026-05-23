<html>
<head>
    <style>
        body { background: #000; color: #00FF41; font-family: 'Courier New', monospace; margin: 0; overflow: hidden; text-align: center; }
        canvas { position: absolute; top: 0; left: 0; z-index: 1; }
        #shock-screen { position: fixed; top:0; left:0; width: 100%; height: 100%; background: red; color: white; display: flex; align-items: center; justify-content: center; font-size: 30px; font-weight: bold; z-index: 999; animation: flash 0.3s infinite; }
        @keyframes flash { 0% { opacity: 1; } 50% { opacity: 0.3; } 100% { opacity: 1; } }
        #content { position: relative; z-index: 2; padding: 20px; }
        .hidden { display: none !important; }
        #logs { text-align: left; background: rgba(0,0,0,0.8); padding: 10px; height: 200px; overflow-y: hidden; border: 1px solid #0f0; }
        #success { display: none; font-size: 40px; color: #0f0; margin-top: 100px; }
    </style>
</head>
<body>

    <div id="shock-screen">!!! DANGER: SYSTEM COMPROMISED !!!</div>

    <div id="content">
        <h1>SYSTEM OVERRIDE INITIATED</h1>
        <div id="logs"></div>
    </div>

    <div id="success">✔ DATA EXFILTRATED SUCCESSFULLY</div>

    <canvas id="matrix"></canvas>

    <script>
        // Matrix Rain
        const c = document.getElementById("matrix");
        const ctx = c.getContext("2d");
        c.height = window.innerHeight; c.width = window.innerWidth;
        const drops = Array(Math.floor(c.width/20)).fill(1);
        function draw() {
            ctx.fillStyle = "rgba(0,0,0,0.05)"; ctx.fillRect(0,0,c.width,c.height);
            ctx.fillStyle = "#0f0";
            drops.map((y, i) => {
                ctx.fillText(String.fromCharCode(65+Math.random()*20), i*20, y*20);
                drops[i] = y*20 > c.height ? 0 : y + 1;
            });
        }
        setInterval(draw, 33);

        // Logic
        setTimeout(() => { document.getElementById('shock-screen').classList.add('hidden'); }, 3000);
        
        const logs = document.getElementById('logs');
        const msgs = ["Connecting to remote host...", "Bypassing WPA2 security...", "Extracting WhatsApp DB...", "Stealing Browser Cookies...", "Uploading data to server...", "Target Hacked."];
        let i = 0;
        let int = setInterval(() => {
            if(i < msgs.length) { logs.innerHTML += "> " + msgs[i] + "<br>"; i++; }
            else { 
                clearInterval(int); 
                document.getElementById('content').classList.add('hidden');
                document.getElementById('success').style.display = 'block';
            }
        }, 1000);
    </script>
</body>
</html>
