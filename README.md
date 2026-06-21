<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EliteTrade Pro | Dashboard</title>
    <style>
        :root { --bg: #0f172a; --card: #1e293b; --text: #f8fafc; --green: #22c55e; --red: #ef4444; }
        body { background: var(--bg); color: var(--text); font-family: sans-serif; margin: 0; padding: 20px; }
        .grid-layout { display: grid; grid-template-columns: 300px 1fr; gap: 20px; }
        .card { background: var(--card); padding: 20px; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.3); }
        .price-up { color: var(--green); }
        .price-down { color: var(--red); }
        .btn { width: 100%; padding: 12px; margin-top: 10px; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; transition: 0.3s; }
        .buy-btn { background: var(--green); color: white; }
        .sell-btn { background: var(--red); color: white; }
        .btn:hover { opacity: 0.8; }
        #history-list { list-style: none; padding: 0; font-size: 0.9em; height: 300px; overflow-y: auto; }
        li { padding: 8px; border-bottom: 1px solid #334155; }
    </style>
</head>
<body>

<div class="grid-layout">
    <aside class="card">
        <h2 id="admin-trigger" style="cursor: pointer;">EliteTrade</h2>
        <p>Wallet Balance</p>
        <h1 id="balance-display">$1000.00</h1>
        <h3>Recent Trades</h3>
        <ul id="history-list"></ul>
    </aside>
    
    <main>
        <div id="market-grid" style="display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 15px;">
            <!-- Live Data Load Hoga -->
        </div>
    </main>
</div>

<script>
    let balance = parseFloat(localStorage.getItem('balance')) || 1000.00;
    let history = JSON.parse(localStorage.getItem('history')) || [];

    function updateUI() {
        document.getElementById('balance-display').innerText = `$${balance.toFixed(2)}`;
        localStorage.setItem('balance', balance);
        const list = document.getElementById('history-list');
        list.innerHTML = history.slice().reverse().map(item => `<li>${item}</li>`).join('');
    }

    async function fetchMarkets() {
        try {
            const res = await fetch('https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&per_page=8');
            const data = await res.json();
            const grid = document.getElementById('market-grid');
            grid.innerHTML = data.map(coin => `
                <div class="card">
                    <h3>${coin.name}</h3>
                    <p>Price: <strong>$${coin.current_price.toLocaleString()}</strong></p>
                    <button class="btn buy-btn" onclick="trade('${coin.symbol}', ${coin.current_price}, 'buy')">Buy</button>
                    <button class="btn sell-btn" onclick="trade('${coin.symbol}', ${coin.current_price}, 'sell')">Sell</button>
                </div>
            `).join('');
        } catch (e) { console.error("Error loading markets", e); }
    }

    function trade(symbol, price, type) {
        if (type === 'buy') {
            if (balance >= price) {
                balance -= price;
                history.push(`Bought ${symbol.toUpperCase()} @ $${price}`);
            } else { alert("Insufficient funds, sweetie!"); return; }
        } else {
            balance += price;
            history.push(`Sold ${symbol.toUpperCase()} @ $${price}`);
        }
        localStorage.setItem('history', JSON.stringify(history));
        updateUI();
    }

    // Secret Key Trigger
    document.getElementById('admin-trigger').addEventListener('dblclick', () => {
        alert("Admin Mode: System Status Operational");
    });

    updateUI();
    fetchMarkets();
    setInterval(fetchMarkets, 30000); // 30 sec auto-refresh
</script>
</body>
</html>
