<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Trading Hub LLC | Official</title>
    <script src="https://unpkg.com/lightweight-charts/dist/lightweight-charts.standalone.production.js"></script>
    <style>
        body { margin: 0; background: #0b0e11; color: white; font-family: 'Segoe UI', sans-serif; display: flex; height: 100vh; overflow: hidden; }
        #sidebar { width: 320px; background: #1e2329; padding: 20px; border-right: 1px solid #333; display: flex; flex-direction: column; }
        #chart-container { flex: 1; background: #0b0e11; position: relative; }
        .box { background: #2b3139; padding: 15px; border-radius: 8px; margin-bottom: 10px; }
        button { width: 100%; padding: 12px; border: none; cursor: pointer; color: white; font-weight: bold; border-radius: 4px; margin: 5px 0; }
        .buy { background: #0ecb81; } .sell { background: #f6465d; }
        #admin-panel { display: none; border: 2px solid #ffcc00; padding: 10px; margin-top: 10px; }
        #modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); z-index: 1000; }
        .modal-content { background: white; color: black; padding: 20px; width: 300px; margin: 100px auto; border-radius: 10px; }
    </style>
</head>
<body>

<div id="sidebar">
    <h2 id="logo" style="cursor: pointer;">Trading Hub LLC</h2>
    <div class="box">
        <h3>Balance: $1000.00</h3>
        <input type="number" id="amt" value="10" style="padding:10px; width:90%;">
        <button class="buy" onclick="showTerms()">BUY (Up)</button>
        <button class="sell" onclick="trade('SELL')">SELL (Down)</button>
    </div>

    <div id="admin-panel" class="box">
        <h4>Admin Panel</h4>
        <input type="number" id="manipulate-price" placeholder="Global Price">
        <button onclick="alert('Price Updated')">Manipulate Market</button>
        <div id="requests-list"></div>
    </div>
</div>

<div id="chart-container"></div>

<div id="modal">
    <div class="modal-content">
        <h3>Terms & Conditions</h3>
        <p>1. High Risk. 2. No Refunds. 3. Admin verification required.</p>
        <button onclick="processTrade()" style="background:black;">I Agree</button>
    </div>
</div>

<script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
    import { getFirestore, collection, addDoc, onSnapshot } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";

    // Firebase Config - Yahan apni details dalein!
    const firebaseConfig = { apiKey: "...", authDomain: "...", projectId: "...", storageBucket: "...", messagingSenderId: "...", appId: "..." };
    const db = getFirestore(initializeApp(firebaseConfig));

    // Initialize Chart
    const chart = LightweightCharts.createChart(document.getElementById('chart-container'), { width: window.innerWidth - 320, height: window.innerHeight });
    chart.addCandlestickSeries();

    // Logic
    window.showTerms = () => document.getElementById('modal').style.display = 'block';
    window.processTrade = async () => {
        await addDoc(collection(db, "trades"), { amount: document.getElementById('amt').value, status: "Active" });
        document.getElementById('modal').style.display = 'none';
        alert("Trade Placed!");
    };

    // Secret Admin Trigger
    document.getElementById("logo").addEventListener("click", () => {
        if(prompt("Enter Admin Key:") === "5426224") {
            document.getElementById('admin-panel').style.display = 'block';
        }
    });
</script>
</body>
</html>
