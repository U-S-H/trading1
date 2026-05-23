<html lang="en">
<head>
    <style>
        body { background: #000; color: #00FF41; font-family: 'Courier New', monospace; margin: 0; overflow: hidden; }
        #overlay { padding: 40px; }
        #terminal { height: 70vh; overflow-y: hidden; font-size: 1.2rem; border-right: 2px solid #00FF41; }
        .controls { position: fixed; bottom: 20px; width: 100%; text-align: center; }
        button { background: #000; color: #00FF41; border: 2px solid #00FF41; padding: 15px 30px; cursor: pointer; font-weight: bold; }
        button:hover { background: #00FF41; color: #000; }
        .blink { animation: flash 0.5s infinite; }
        @keyframes flash { 50% { opacity: 0; } }
    </style>
</head>
<body>

<div id="overlay">
    <h1 class="blink">>> SECURE SERVER BREACH IN PROGRESS</h1>
    <div id="terminal"></div>
</div>

<div class="controls">
    <button onclick="runBreach()">INITIALIZE BREACH</button>
</div>

<script>
    const term = document.getElementById('terminal');
    const logs = [
        "INITIALIZING ATTACK VECTOR...",
        "BYPASSING DUAL-FACTOR AUTHENTICATION...",
        "TARGET: FINANCIAL_SERVER_CORE_01",
        "DECRYPTING ENCRYPTED_ACCOUNTS_DATABASE...",
        "FACEBOOK_TOKEN: ACCESS_GRANTED",
        "WHATSAPP_SESSION: SYNCING_MEDIA...",
        "BANKING_CREDENTIALS: FOUND_MATCH_IN_VAULT",
        "UPLOADING DATA TO EXTERNAL_PROXY...",
        "SYSTEM_CONTROL: ADMINISTRATIVE_PRIVILEGES_OBTAINED",
        "!!! WARNING: DATA EXFILTRATION COMPLETE !!!"
    ];

    function runBreach() {
        let i = 0;
        let interval = setInterval(() => {
            if (i < logs.length) {
                term.innerHTML += "> " + logs[i] + "<br>";
                i++;
            } else {
                clearInterval(interval);
                alert("PRANK COMPLETE: Data 'stolen' from target!");
                location.reload();
            }
        }, 800);
    }
</script>
</body>
</html>
