<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Trading Hub LLC - Official</title>
    <script src="https://unpkg.com/lightweight-charts/dist/lightweight-charts.standalone.production.js"></script>
    <style>
        body { margin: 0; font-family: sans-serif; background: url('https://images.unsplash.com/photo-1642543348745-03b1237ef390?q=80&w=2070&auto=format&fit=crop') no-repeat center center fixed; background-size: cover; color: white; text-align: center; }
        .box { background: rgba(30, 30, 30, 0.9); padding: 20px; border-radius: 15px; margin: 20px auto; max-width: 450px; backdrop-filter: blur(10px); }
        input, select { display: block; width: 90%; margin: 10px auto; padding: 12px; border-radius: 8px; border: none; }
        button { padding: 12px 25px; margin: 5px; cursor: pointer; border-radius: 8px; border: none; background: #007bff; color: white; font-weight: bold; }
        #modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); z-index: 1000; }
        .modal-content { background: white; color: black; padding: 20px; width: 80%; max-width: 400px; margin: 100px auto; border-radius: 10px; }
        #admin-panel { display: none; border: 2px solid #ffcc00; }
    </style>
</head>
<body>

    <h1 id="logo" style="cursor: pointer; padding-top: 20px;">Trading Hub LLC</h1>
    
    <div class="box" id="chart-container" style="height: 250px;"></div>

    <div class="box">
        <h3>Deposit/Withdraw</h3>
        <select id="method"><option>EasyPaisa: 03379827882</option><option>JazzCash/SadaPay: 03705519562</option></select>
        <input type="number" id="amt" placeholder="Amount">
        <input type="text" id="tid" placeholder="TID/Account No">
        <input type="file" id="proof" accept="image/*">
        <button onclick="showTerms()">Submit Deposit</button>
    </div>

    <div id="admin-panel" class="box">
        <h3>Admin Panel</h3>
        <div id="requests-list"></div>
    </div>

    <div id="modal">
        <div class="modal-content">
            <h2>Terms & Conditions</h2>
            <p>1. Trading involves risk. 2. No liability for losses. 3. Deposits are verified manually.</p>
            <button onclick="processDeposit()">I Agree & Submit</button>
            <button onclick="document.getElementById('modal').style.display='none'" style="background:red;">Close</button>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-app.js";
        import { getFirestore, collection, addDoc, onSnapshot, doc, updateDoc } from "https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore.js";

        // CONFIG: Replace with your details!
        const firebaseConfig = { apiKey: "AIzaSyCsgXPW-h2NzAHMrDBIL_HjlU8wSpcgzvI", authDomain: "course-3cc77.firebaseapp.com", projectId: "course-3cc77", storageBucket: "course-3cc77.firebasestorage.app", messagingSenderId: "136140432667", appId: "1:136140432667:web:9f543dc3db8683944ddfbe" };
        const db = getFirestore(initializeApp(firebaseConfig));

        // Chart
        const chart = LightweightCharts.createChart(document.getElementById('chart-container'), { width: 400, height: 250 });
        chart.addAreaSeries().setData([{ time: '2026-06-21', value: 50000 }]);

        // Logic
        window.showTerms = () => document.getElementById('modal').style.display = 'block';

        window.processDeposit = async () => {
            const file = document.getElementById('proof').files[0];
            const reader = new FileReader();
            reader.onload = async (e) => {
                await addDoc(collection(db, "deposits"), { amount: document.getElementById('amt').value, tid: document.getElementById('tid').value, proof: e.target.result, status: "Pending" });
                alert("Submitted for review!");
                document.getElementById('modal').style.display = 'none';
            };
            file ? reader.readAsDataURL(file) : alert("Upload Proof!");
        };

        document.getElementById("logo").addEventListener("click", () => {
            if (prompt("Admin Key:") === "5426224") {
                document.getElementById("admin-panel").style.display = "block";
                onSnapshot(collection(db, "deposits"), (snap) => {
                    let h = "";
                    snap.forEach(d => { if(d.data().status === "Pending") h += `<p>${d.data().tid}: $${d.data().amount} <button onclick="approve('${d.id}')">Approve</button></p>`; });
                    document.getElementById('requests-list').innerHTML = h;
                });
            }
        });

        window.approve = async (id) => { await updateDoc(doc(db, "deposits", id), { status: "Approved" }); alert("Done!"); };
    </script>
</body>
</html>
