<html>
<head>
    <style>
        body { background: #000; color: #0f0; font-family: monospace; padding: 20px; }
        .bar-container { width: 100%; background: #222; margin: 10px 0; }
        .bar { height: 20px; background: #0f0; width: 0%; transition: width 1s; }
    </style>
</head>
<body>
    <h1>SYSTEM BREACH INITIATED...</h1>
    <p>Target: FACEBOOK_SERVER_01</p>
    <div class="bar-container"><div class="bar" id="fb-bar"></div></div>
    
    <p>Target: WHATSAPP_ENCRYPTION_KEY</p>
    <div class="bar-container"><div class="bar" id="wa-bar"></div></div>

    <script>
        function load(id, speed) {
            let width = 0;
            let el = document.getElementById(id);
            let interval = setInterval(() => {
                if (width >= 100) clearInterval(interval);
                else { width++; el.style.width = width + '%'; }
            }, speed);
        }
        load('fb-bar', 100);
        load('wa-bar', 200);
    </script>
</body>
</html>
