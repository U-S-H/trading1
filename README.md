<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Trading Hub LLC - Official</title>
    <script src="https://unpkg.com/lightweight-charts/dist/lightweight-charts.standalone.production.js"></script>
    <style>
        body { font-family: sans-serif; background: #121212; color: white; padding: 20px; text-align: center; }
        .section { background: #1e1e1e; padding: 15px; border-radius: 10px; margin: 10px auto; max-width: 500px; }
        input, select { display: block; width: 90%; margin: 10px auto; padding: 10px; border-radius: 5px; border: none; }
        button { padding: 10px 20px; cursor: pointer; border-radius: 5px; border: none; background: #007bff; color: white; }
        #admin-section { display: none; border: 2px solid #ffcc00; padding: 15px; }
    </style>
</head>
<body>

    <h1 id="logo" style="cursor: pointer;">Trading Hub LLC</h1>

    <div id="chart-container" style="height: 300px; width: 100%; max-width: 600px; margin: auto; background: #1e1e1e;"></div>

    <div class="section">
        <h3>Deposit Funds</h3>
        <select id="method"><option>EasyPaisa: 03379827882</option><option>JazzCash/SadaPay: 03705519562</option></select>
        <input type="number" id="amount" placeholder="Amount">
        <input type="text" id="tid" placeholder="TID Number">
        <input type="file" id="proof" accept="image/*">
        <button onclick="submitDeposit()">Submit Deposit</button>
    </div>

    <div id="admin-section" class="section">
        <h3>Admin Panel</h3>
        <div id="requests-list"></div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
        import { getFirestore, collection, addDoc, onSnapshot, doc, updateDoc } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";

        const firebaseConfig = {
            apiKey: "AIzaSyCsgXPW-h2NzAHMrDBIL_HjlU8wSpcgzvI",
            authDomain: "course-3cc77.firebaseapp.com",
            projectId: "course-3cc77",
            storageBucket: "course-3cc77.firebasestorage.app",
            messagingSenderId: "136140432667",
            appId: "1:136140432667:web:9f543dc3db8683944ddfbe"
        };

        const app = initializeApp(firebaseConfig);
        const db = getFirestore();

        // Chart Init
        const chart = LightweightCharts.createChart(document.getElementById('chart-container'), { width: 500, height: 300 });
        const lineSeries = chart.addAreaSeries();
        lineSeries.setData([{ time: '2026-06-21', value: 50000 }]);

        // Deposit Logic
        window.submitDeposit = async () => {
            const file = document.getElementById('proof').files[0];
            const reader = new FileReader();
            reader.onload = async (e) => {
                await addDoc(collection(db, "deposits"), {
                    amount: document.getElementById('amount').value,
                    tid: document.getElementById('tid').value,
                    proof: e.target.result,
                    status: "Pending"
                });
                alert("Deposit submitted!");
            };
            reader.readAsDataURL(file);
        };

        // Admin Secret Logic
        document.getElementById("logo").addEventListener("click", () => {
            if (prompt("Enter Secret Key:") === "5426224") {
                document.getElementById("admin-section").style.display = "block";
                loadAdminRequests();
            }
        });

        function loadAdminRequests() {
            onSnapshot(collection(db, "deposits"), (snapshot) => {
                let html = "";
                snapshot.forEach((d) => {
                    if(d.data().status === "Pending") {
                        html += `<div><p>TID: ${d.data().tid} | $${d.data().amount}</p>
                        <button onclick="approve('${d.id}')">Approve</button></div>`;
                    }
                });
                document.getElementById('requests-list').innerHTML = html;
            });
        }

        window.approve = async (id) => {
            await updateDoc(doc(db, "deposits", id), { status: "Approved" });
            alert("Approved!");
        };
    </script>
</body>
</html>
