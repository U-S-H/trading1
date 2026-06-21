<html lang="ur" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>Pro Trading Terminal</title>
    <style>
        body { margin: 0; background: #0b0e11; color: white; font-family: sans-serif; display: flex; flex-direction: column; height: 100vh; }
        .nav { background: #1e2329; padding: 15px; display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid #333; }
        .grid { display: grid; grid-template-columns: 250px 1fr 300px; flex: 1; overflow: hidden; }
        .sidebar { background: #131722; padding: 15px; border-left: 1px solid #333; }
        .chart { background: #000; display: flex; align-items: center; justify-content: center; }
        .controls { background: #1e2329; padding: 20px; border-right: 1px solid #333; }
        .btn { width: 100%; padding: 15px; border: none; cursor: pointer; color: white; font-weight: bold; margin-top: 10px; border-radius: 4px; }
        .buy { background: #00c087; } .sell { background: #ff5252; }
        #admin-panel { display: none; margin-top: 20px; padding: 10px; border: 1px dashed red; }
    </style>
</head>
<body>

<div class="nav">
    <h2 onclick="triggerAdmin()" style="cursor:pointer;">TRADING PRO</h2>
    <div id="balance-display">Balance: $0.00</div>
</div>

<div class="grid">
    <div class="sidebar">
        <h3>History</h3>
        <div id="history-log"></div>
    </div>
    <div class="chart" id="chart-area"></div>
    <div class="controls">
        <input type="number" id="amt" placeholder="Amount ($)" style="width:90%; padding:10px;">
        <button class="btn buy" onclick="placeTrade('BUY')">BUY / UP</button>
        <button class="btn sell" onclick="placeTrade('SELL')">SELL / DOWN</button>
        <hr>
        <button class="btn" onclick="walletAction('DEPOSIT')" style="background:#4a90e2;">Deposit</button>
        <button class="btn" onclick="walletAction('WITHDRAW')" style="background:#f39c12;">Withdraw</button>
        
        <div id="admin-panel">
            <h3>Admin System</h3>
            <div id="admin-requests"></div>
        </div>
    </div>
</div>

<script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
    import { getFirestore, doc, onSnapshot, addDoc, collection } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";

    const config = {
        apiKey: "AIzaSyCsgXPW-h2NzAHMrDBIL_HjlU8wSpcgzvI",
        projectId: "course-3cc77",
        storageBucket: "course-3cc77.firebasestorage.app",
        messagingSenderId: "136140432667",
        appId: "1:136140432667:web:9f543dc3db8683944ddfbe"
    };

    const db = getFirestore(initializeApp(config));
    const uid = "test_user_id";

    // 1. Balance Update
    onSnapshot(doc(db, "users", uid), (doc) => {
        document.getElementById("balance-display").innerText = "Balance: $" + doc.data().balance.toFixed(2);
    });

    // 2. Trade Logic
    window.placeTrade = async (type) => {
        const amt = document.getElementById('amt').value;
        await addDoc(collection(db, "trades"), { uid, type, amount: parseFloat(amt), status: 'OPEN', time: new Date() });
        alert(type + " Trade Placed!");
    };

    // 3. Wallet Actions
    window.walletAction = async (type) => {
        const amt = prompt("Amount:");
        await addDoc(collection(db, "requests"), { uid, type, amount: parseFloat(amt), status: 'PENDING' });
        alert("Request Sent!");
    };

    // 4. Admin
    let t = 0;
    window.triggerAdmin = () => {
        t++;
        if(t === 5) {
            if(prompt("Key:") === "5426224") document.getElementById("admin-panel").style.display = "block";
            t = 0;
        }
    };
</script>

<script src="https://s3.tradingview.com/tv.js"></script>
<script>new TradingView.widget({"container_id": "chart-area", "symbol": "BINANCE:BTCUSDT", "theme": "dark", "autosize": true});</script>

</body>
</html>
