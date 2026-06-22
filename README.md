<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BetMatrix - Live Premium Casino Lobby</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        .custom-scrollbar::-webkit-scrollbar { width: 4px; height: 4px; }
        .custom-scrollbar::-webkit-scrollbar-track { background: #0b0d13; }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: #1f2330; border-radius: 4px; }
        body { background-color: #0b0d13; color: #e2e8f0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }
        .game-card-shadow { box-shadow: 0 4px 15px rgba(0,0,0,0.4); }
        .hot-badge { background: linear-gradient(135deg, #ff4500, #ff8c00); }
    </style>
</head>
<body class="custom-scrollbar min-h-screen flex flex-col justify-between pb-14">

    <nav class="bg-[#121620] border-b border-gray-800/80 px-4 h-14 flex items-center justify-between sticky top-0 z-40">
        <div class="flex items-center space-x-3">
            <div onclick="switchLobbyTab('profile')" class="w-8 h-8 rounded-full bg-yellow-500/10 flex items-center justify-center border border-yellow-500/30 cursor-pointer">
                <i class="fa-solid fa-crown text-xs text-yellow-400"></i>
            </div>
            <span class="text-xs font-black tracking-widest text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-amber-500">BETMATRIX</span>
        </div>

        <div onclick="openWalletModal()" class="flex flex-col items-center justify-center cursor-pointer group bg-gray-900/60 px-3 py-1 rounded-xl border border-gray-800">
            <div class="flex items-center space-x-1.5">
                <span id="lobbyWalletBalanceDisplay" class="font-mono font-black text-xs text-emerald-400">PKR 0.00</span>
                <i class="fa-solid fa-chevron-down text-[9px] text-gray-500 group-hover:text-emerald-400 transition"></i>
            </div>
            <span id="lobbyWalletLabelDisplay" class="text-[8px] text-gray-400 font-bold uppercase tracking-wide">Main Account</span>
        </div>

        <button onclick="openCashierModal('deposit')" class="w-8 h-8 rounded-lg bg-emerald-500 text-black flex items-center justify-center shadow-lg active:scale-95 transition">
            <i class="fa-solid fa-plus text-xs font-black"></i>
        </button>
    </nav>

    <div class="w-full max-w-md mx-auto flex-grow flex flex-col px-3 pt-3">
        
        <div id="lobbyTabSheetGames" class="flex-grow flex flex-col space-y-4">
            <div class="flex items-center space-x-2 bg-[#121620] p-1.5 rounded-xl border border-gray-800/60">
                <div class="flex-1 h-9 bg-gray-900 rounded-lg flex items-center px-3 space-x-2 border border-gray-800">
                    <i class="fa-solid fa-magnifying-glass text-xs text-gray-500"></i>
                    <input type="text" placeholder="Search hot games..." class="bg-transparent text-xs text-white outline-none w-full placeholder-gray-600">
                </div>
            </div>

            <div class="flex items-center space-x-3 text-xs font-bold text-gray-400 border-b border-gray-900 pb-1 px-1">
                <button class="text-yellow-400 border-b-2 border-yellow-400 pb-1 flex items-center space-x-1"><i class="fa-solid fa-fire-flame-curved text-[10px]"></i> <span>Hot</span></button>
                <button class="hover:text-white pb-1 flex items-center space-x-1"><i class="fa-solid fa-clock text-[10px]"></i> <span>Recent</span></button>
                <button class="hover:text-white pb-1 flex items-center space-x-1"><i class="fa-solid fa-star text-[10px]"></i> <span>Favorites</span></button>
            </div>

            <div class="grid grid-cols-3 gap-2.5" id="casinoGamesGridArea">
                </div>
        </div>

        <div id="lobbyTabSheetRewards" class="hidden flex-grow space-y-3">
            <div class="bg-gradient-to-br from-amber-600 to-yellow-700 p-4 rounded-2xl border border-yellow-400/20 shadow-xl relative overflow-hidden">
                <h3 class="font-black text-base text-white">Daily Multiplier Wheel</h3>
                <p class="text-xs text-amber-100/80 mt-1">Get up to x10 random index odds on Crash stakes today.</p>
                <button onclick="openCashierModal('deposit')" class="mt-4 px-3 py-1.5 bg-black text-yellow-400 rounded-lg font-black text-xs uppercase tracking-wider">Claim Multiplier</button>
            </div>
        </div>

        <div id="lobbyTabSheetHistory" class="hidden flex-grow space-y-3">
            <div class="bg-[#121620] border border-gray-800 rounded-xl p-4 text-center text-xs text-gray-500">
                <i class="fa-solid fa-dice text-xl text-gray-700 mb-2 block"></i>
                No active bets or round instances found on this session index.
            </div>
        </div>

        <div id="lobbyTabSheetProfile" class="hidden flex-grow space-y-3">
            <div class="bg-[#121620] border border-gray-800 rounded-2xl p-4 flex items-center space-x-3 text-xs">
                <div class="w-10 h-10 rounded-full bg-yellow-400 text-black font-black flex items-center justify-center text-sm">MN</div>
                <div>
                    <h4 class="font-bold text-white">Muhammad Nazim</h4>
                    <p class="text-[10px] text-gray-500 font-mono mt-0.5">UID: 121542844</p>
                </div>
            </div>
        </div>
    </div>

    <div class="fixed bottom-0 left-0 right-0 h-14 bg-[#121620] border-t border-gray-800/80 flex items-center justify-around z-30 max-w-md mx-auto px-4 shadow-2xl">
        <button id="navBtnGames" onclick="switchLobbyTab('games')" class="flex flex-col items-center justify-center text-yellow-400 transition"><i class="fa-solid fa-gamepad text-base"></i></button>
        <button id="navBtnHistory" onclick="switchLobbyTab('history')" class="flex flex-col items-center justify-center text-gray-500 hover:text-gray-300 transition"><i class="fa-solid fa-receipt text-base"></i></button>
        <button id="navBtnRewards" onclick="switchLobbyTab('rewards')" class="flex flex-col items-center justify-center text-gray-500 hover:text-gray-300 transition"><i class="fa-solid fa-clover text-base"></i></button>
        <button id="navBtnProfile" onclick="switchLobbyTab('profile')" class="flex flex-col items-center justify-center text-gray-500 hover:text-gray-300 transition"><i class="fa-solid fa-user-shield text-base"></i></button>
    </div>

    <div id="walletSwitcherLayout" class="fixed inset-0 bg-black/80 z-50 hidden flex items-end justify-center backdrop-blur-xs">
        <div class="bg-[#121620] w-full max-w-md rounded-t-3xl border-t border-gray-800 p-5 space-y-4 shadow-2xl">
            <div class="flex justify-between items-center">
                <h3 class="text-sm font-black text-white uppercase tracking-wider">Account Wallets</h3>
                <button onclick="closeWalletModal()" class="w-7 h-7 rounded-full bg-gray-800 text-gray-400 text-xs flex items-center justify-center">✕</button>
            </div>
            <div class="space-y-2">
                <div onclick="updatePlatformWalletMode('DEMO')" class="p-3 bg-gray-900 border border-gray-800 rounded-xl flex items-center justify-between cursor-pointer hover:bg-gray-800 transition">
                    <div class="flex items-center space-x-3">
                        <div class="w-6 h-6 bg-amber-500/10 rounded border border-amber-500/20 text-amber-500 font-mono font-bold text-xs flex items-center justify-center">Ð</div>
                        <div><p class="text-[11px] font-bold text-gray-400">Demo Bet Chips</p><p id="modalDemoWalletDisplay" class="text-xs font-mono font-black text-white mt-0.5">Ð0.00</p></div>
                    </div>
                    <i id="walletCheckIconDemo" class="fa-solid fa-circle-check text-yellow-400 text-xs hidden"></i>
                </div>
                <div onclick="updatePlatformWalletMode('PKR')" class="p-3 bg-gray-900 border border-gray-800 rounded-xl flex items-center justify-between cursor-pointer hover:bg-gray-800 transition">
                    <div class="flex items-center space-x-3">
                        <div class="w-6 h-5 bg-emerald-700 rounded text-[9px] font-bold text-white flex items-center justify-center">PK</div>
                        <div><p class="text-[11px] font-bold text-gray-300">Real PKR Wallet</p><p id="modalPkrWalletDisplay" class="text-xs font-mono font-black text-white mt-0.5">PKR 0.00</p></div>
                    </div>
                    <i id="walletCheckIconPkr" class="fa-solid fa-circle-check text-yellow-400 text-xs hidden"></i>
                </div>
            </div>
        </div>
    </div>

    <div id="cashierGateLayout" class="fixed inset-0 bg-black/80 z-50 hidden flex items-end justify-center backdrop-blur-xs">
        <div class="bg-[#121620] w-full max-w-md rounded-t-3xl border-t border-gray-800 p-5 space-y-4 shadow-2xl">
            <div class="flex justify-between items-center">
                <h3 id="cashierModalHeaderTitle" class="text-sm font-black text-white uppercase tracking-wider">Cashier Gateway</h3>
                <button onclick="closeCashierModal()" class="w-7 h-7 rounded-full bg-gray-800 text-gray-400 text-xs flex items-center justify-center">✕</button>
            </div>
            <div class="flex bg-gray-900 rounded-xl p-1 text-xs border border-gray-800">
                <button id="cashierToggleBtnDeposit" onclick="switchCashierTabMode('deposit')" class="flex-1 py-1.5 font-bold rounded-lg text-center transition">Deposit</button>
                <button id="cashierToggleBtnWithdraw" onclick="switchCashierTabMode('withdraw')" class="flex-1 py-1.5 font-bold rounded-lg text-center transition">Withdraw</button>
            </div>
            <div id="cashierInjectedContentPanel" class="space-y-4 pt-1"></div>
        </div>
    </div>

    <div id="gamePlayScreenOverlay" class="fixed inset-0 bg-black z-50 hidden flex flex-col justify-between p-4">
        <div class="flex justify-between items-center border-b border-gray-900 pb-3">
            <div class="flex items-center space-x-2">
                <span id="activeRunningGameIcon" class="text-xl">🚀</span>
                <h2 id="activeRunningGameTitle" class="text-sm font-black text-white">Aviator Run</h2>
            </div>
            <button onclick="exitActiveGameSession()" class="px-3 py-1 bg-gray-900 border border-gray-800 rounded-lg text-xs font-bold text-red-400">Exit Studio</button>
        </div>
        <div class="flex-grow flex flex-col justify-center items-center text-center space-y-6">
            <div class="w-32 h-32 rounded-full border-4 border-yellow-500/20 border-t-yellow-400 animate-spin flex items-center justify-center relative shadow-2xl shadow-yellow-500/10">
                <span id="gameLiveMultiplierToken" class="text-xl font-mono font-black text-white">1.00x</span>
            </div>
            <div>
                <p class="text-xs text-gray-400 font-medium">Staked Risk Investment Pool</p>
                <p id="gameStakedAmountLabel" class="text-sm font-mono font-bold text-yellow-400 mt-1">PKR 280</p>
            </div>
        </div>
        <button onclick="triggerCashoutSequence()" class="w-full h-12 rounded-xl bg-gradient-to-r from-amber-500 to-yellow-500 text-black font-black uppercase tracking-wider shadow-lg active:scale-95 transition">Take Win Profit Payout</button>
    </div>

    <script>
        // DATA ARRAY MATCHING YOUR LOBBY REPLICAS
        const CASINO_CATALOG_DATA = [
            { id: 'aviator', label: 'Aviator', provider: 'Spribe', type: '🚀', bg: 'from-rose-900 to-red-950', baseMultiplier: 2.5 },
            { id: 'sicbo', label: 'SicBo', provider: 'JILI', type: '🎲', bg: 'from-emerald-900 to-teal-950', baseMultiplier: 1.9 },
            { id: 'towerrush', label: 'Tower Rush', provider: 'GALAXSYS', type: '🏰', bg: 'from-blue-900 to-indigo-950', baseMultiplier: 3.0 },
            { id: 'icefishing', label: 'Ice Fishing', provider: 'Evolution', type: '🎣', bg: 'from-cyan-900 to-sky-950', baseMultiplier: 2.1 },
            { id: 'fortunegems2', label: 'FORTUNE GEMS2', provider: 'JILI', type: '🔱', bg: 'from-amber-900 to-orange-950', baseMultiplier: 4.5 },
            { id: 'aviatrix', label: 'Aviatrix', provider: 'aviatrix', type: '🛩️', bg: 'from-purple-900 to-fuchsia-950', baseMultiplier: 2.8 },
            { id: 'moneycoming', label: 'MoneyComing', provider: 'JILI', type: '💵', bg: 'from-green-900 to-emerald-950', baseMultiplier: 5.0 },
            { id: 'vortex', label: 'Vortex', provider: 'Turbo', type: '🌀', bg: 'from-indigo-900 to-purple-950', baseMultiplier: 1.8 },
            { id: 'chickenroad2', label: 'Chicken Road2', provider: 'IN OUT', type: '🐥', bg: 'from-orange-900 to-yellow-950', baseMultiplier: 3.2 },
            { id: 'cricket', label: 'Cricket', provider: '9W', type: '🏏', bg: 'from-teal-900 to-green-950', baseMultiplier: 2.0 },
            { id: 'fortunegems3', label: 'FORTUNE GEMS3', provider: 'JILI', type: '👑', bg: 'from-yellow-950 to-amber-950', baseMultiplier: 6.0 },
            { id: 'speedroulette', label: 'Speed Roulette', provider: 'Evolution', type: '🎡', bg: 'from-stone-900 to-neutral-950', baseMultiplier: 2.2 }
        ];

        let casinoStateEngine = {
            activeEnvironment: 'DEMO',
            balances: { DEMO: 58766.67, PKR: 0.00 },
            activeGameIndex: null,
            multiplierSimulationTimer: null,
            simulatedOdds: 1.00
        };

        window.addEventListener('DOMContentLoaded', () => {
            renderLobbyDynamicGridMatrix();
            syncLobbyApplicationState();
            switchLobbyTab('games');
        });

        function renderLobbyDynamicGridMatrix() {
            const gridContainer = document.getElementById('casinoGamesGridArea');
            if(!gridContainer) return;
            gridContainer.innerHTML = '';

            CASINO_CATALOG_DATA.forEach((gameItem, indexRef) => {
                const card = document.createElement('div');
                card.onclick = () => { launchGameSessionInstance(indexRef); };
                card.className = `bg-gradient-to-b ${gameItem.bg} rounded-2xl p-2.5 flex flex-col justify-between h-36 border border-gray-800 relative cursor-pointer active:scale-95 transition game-card-shadow overflow-hidden group`;
                
                card.innerHTML = `
                    <div class="absolute top-1 left-1 px-1.5 py-0.5 rounded text-[7px] font-black uppercase text-white hot-badge tracking-wider shadow z-10 flex items-center space-x-0.5">
                        <i class="fa-solid fa-fire text-[6px]"></i><span>HOT</span>
                    </div>
                    <div class="absolute -right-2 -top-2 text-4xl opacity-15 group-hover:scale-125 transition duration-500">${gameItem.type}</div>
                    <div class="flex-grow flex items-center justify-center text-3xl my-2">${gameItem.type}</div>
                    <div class="space-y-0.5">
                        <h4 class="text-[10px] font-black text-white tracking-wide truncate uppercase">${gameItem.label}</h4>
                        <p class="text-[8px] text-gray-400 font-bold tracking-tight truncate">${gameItem.provider}</p>
                    </div>
                `;
                gridContainer.appendChild(card);
            });
        }

        function syncLobbyApplicationState() {
            const outputPrefix = casinoStateEngine.activeEnvironment === 'DEMO' ? 'Ð ' : 'PKR ';
            document.getElementById('lobbyWalletBalanceDisplay').innerText = outputPrefix + casinoStateEngine.balances[casinoStateEngine.activeEnvironment].toFixed(2);
            document.getElementById('lobbyWalletLabelDisplay').innerText = casinoStateEngine.activeEnvironment === 'DEMO' ? 'Demo Account' : 'Real Casino Wallet';
            
            document.getElementById('modalDemoWalletDisplay').innerText = "Ð " + casinoStateEngine.balances.DEMO.toFixed(2);
            document.getElementById('modalPkrWalletDisplay').innerText = "PKR " + casinoStateEngine.balances.PKR.toFixed(2);
        }

        function switchLobbyTab(tabToken) {
            const tabs = ['games', 'rewards', 'history', 'profile'];
            tabs.forEach(item => {
                const sheet = document.getElementById(`lobbyTabSheet${item.charAt(0).toUpperCase() + item.slice(1)}`);
                const button = document.getElementById(`navBtn${item.charAt(0).toUpperCase() + item.slice(1)}`);
                if(sheet) sheet.classList.add('hidden');
                if(button) button.className = "flex flex-col items-center justify-center text-gray-500 hover:text-gray-300 transition";
            });

            document.getElementById(`lobbyTabSheet${tabToken.charAt(0).toUpperCase() + tabToken.slice(1)}`).classList.remove('hidden');
            document.getElementById(`navBtn${tabToken.charAt(0).toUpperCase() + tabToken.slice(1)}`).className = "flex flex-col items-center justify-center text-yellow-400 transition";
        }

        function openWalletModal() {
            document.getElementById('walletSwitcherLayout').classList.remove('hidden');
            if(casinoStateEngine.activeEnvironment === 'DEMO') {
                document.getElementById('walletCheckIconDemo').classList.remove('hidden');
                document.getElementById('walletCheckIconPkr').classList.add('hidden');
            } else {
                document.getElementById('walletCheckIconDemo').classList.add('hidden');
                document.getElementById('walletCheckIconPkr').classList.remove('hidden');
            }
        }
        function closeWalletModal() { document.getElementById('walletSwitcherLayout').classList.add('hidden'); }

        function updatePlatformWalletMode(envToken) {
            casinoStateEngine.activeEnvironment = envToken;
            syncLobbyApplicationState();
            closeWalletModal();
        }

        function openCashierModal(mode = 'deposit') {
            document.getElementById('cashierGateLayout').classList.remove('hidden');
            switchCashierTabMode(mode);
        }
        function closeCashierModal() { document.getElementById('cashierGateLayout').classList.add('hidden'); }

        function switchCashierTabMode(modeToken) {
            const depBtn = document.getElementById('cashierToggleBtnDeposit');
            const witBtn = document.getElementById('cashierToggleBtnWithdraw');
            const panel = document.getElementById('cashierInjectedContentPanel');

            if(modeToken === 'deposit') {
                depBtn.className = "flex-1 py-1.5 font-bold rounded-lg text-center bg-gray-800 text-emerald-400";
                witBtn.className = "flex-1 py-1.5 font-bold rounded-lg text-center text-gray-500";
                panel.innerHTML = `
                    <div class="space-y-3 text-xs">
                        <div class="p-3 bg-gray-950 border border-emerald-500/20 rounded-xl flex items-center justify-between"><span class="font-bold">EasyPaisa Gateway</span><i class="fa-solid fa-shield text-emerald-400"></i></div>
                        <input type="number" id="cashierDepositInput" value="1000" class="w-full h-10 bg-gray-900 border border-gray-800 rounded-lg px-3 font-mono text-white outline-none">
                        <button onclick="executeCashierTransaction('DEPOSIT')" class="w-full h-10 bg-emerald-500 text-black font-black uppercase tracking-wider rounded-lg">Load Chips Account</button>
                    </div>`;
            } else {
                depBtn.className = "flex-1 py-1.5 font-bold rounded-lg text-center text-gray-500";
                witBtn.className = "flex-1 py-1.5 font-bold rounded-lg text-center bg-gray-800 text-red-400";
                            panel.innerHTML = `
                    <div class="space-y-3 text-xs">
                        <div class="p-3 bg-gray-950 border border-red-500/20 rounded-xl flex items-center justify-between"><span class="font-bold">EasyPaisa Payout System</span><i class="fa-solid fa-building-columns text-red-400"></i></div>
                        <input type="number" id="cashierWithdrawInput" value="500" class="w-full h-10 bg-gray-900 border border-gray-800 rounded-lg px-3 font-mono text-white outline-none">
                        <button onclick="executeCashierTransaction('WITHDRAW')" class="w-full h-10 bg-red-500 text-black font-black uppercase tracking-wider rounded-lg">Request Payout</button>
                    </div>`;
            }
        }

        function executeCashierTransaction(typeToken) {
            if(casinoStateEngine.activeEnvironment === 'DEMO') {
                alert("Demo balance cannot be deposited or withdrawn. Please switch to your Real PKR Account.");
                closeCashierModal();
                return;
            }

            if(typeToken === 'DEPOSIT') {
                const amount = parseFloat(document.getElementById('cashierDepositInput').value);
                if(isNaN(amount) || amount <= 0) return alert("Please enter a valid amount.");
                casinoStateEngine.balances.PKR += amount;
                alert(`Successfully deposited PKR ${amount.toFixed(2)} via EasyPaisa.`);
            } else {
                const amount = parseFloat(document.getElementById('cashierWithdrawInput').value);
                if(isNaN(amount) || amount <= 0) return alert("Please enter a valid amount.");
                if(amount > casinoStateEngine.balances.PKR) return alert("Insufficient balance in your Real Wallet.");
                casinoStateEngine.balances.PKR -= amount;
                alert(`Withdrawal request of PKR ${amount.toFixed(2)} has been submitted successfully.`);
            }
            syncLobbyApplicationState();
            closeCashierModal();
        }

        function launchGameSessionInstance(indexRef) {
            const gameData = CASINO_CATALOG_DATA[indexRef];
            casinoStateEngine.activeGameIndex = indexRef;
            casinoStateEngine.simulatedOdds = 1.00;

            const baseCurrency = casinoStateEngine.activeEnvironment === 'DEMO' ? 'Ð' : 'PKR';
            const stakeValue = casinoStateEngine.activeEnvironment === 'DEMO' ? 500 : 280;

            if(casinoStateEngine.balances[casinoStateEngine.activeEnvironment] < stakeValue) {
                return alert("Insufficient funds to start this risk pool instance.");
            }

            // Deduct entry stake pool
            casinoStateEngine.balances[casinoStateEngine.activeEnvironment] -= stakeValue;
            syncLobbyApplicationState();

            // Set UI labels
            document.getElementById('activeRunningGameIcon').innerText = gameData.type;
            document.getElementById('activeRunningGameTitle').innerText = gameData.label;
            document.getElementById('gameStakedAmountLabel').innerText = `${baseCurrency} ${stakeValue}`;
            document.getElementById('gameLiveMultiplierToken').innerText = "1.00x";
            
            document.getElementById('gamePlayScreenOverlay').classList.remove('hidden');

            // Start multiplier engine ticker
            casinoStateEngine.multiplierSimulationTimer = setInterval(() => {
                casinoStateEngine.simulatedOdds += 0.04 + (Math.random() * 0.05);
                document.getElementById('gameLiveMultiplierToken').innerText = casinoStateEngine.simulatedOdds.toFixed(2) + "x";
                
                // Random crash ceiling simulation
                if(casinoStateEngine.simulatedOdds > gameData.baseMultiplier * (1 + Math.random())) {
                    clearInterval(casinoStateEngine.multiplierSimulationTimer);
                    alert("💥 Instance Crushed! Stake pool dissolved.");
                    exitActiveGameSession();
                }
            }, 150);
        }

        function triggerCashoutSequence() {
            if(!casinoStateEngine.multiplierSimulationTimer) return;
            clearInterval(casinoStateEngine.multiplierSimulationTimer);
            casinoStateEngine.multiplierSimulationTimer = null;

            const stakeValue = casinoStateEngine.activeEnvironment === 'DEMO' ? 500 : 280;
            const absoluteWinnings = stakeValue * casinoStateEngine.simulatedOdds;
            
            casinoStateEngine.balances[casinoStateEngine.activeEnvironment] += absoluteWinnings;
            const baseCurrency = casinoStateEngine.activeEnvironment === 'DEMO' ? 'Ð' : 'PKR';
            
            alert(`🎉 Cashout Success! Settled payout: ${baseCurrency} ${absoluteWinnings.toFixed(2)} at ${casinoStateEngine.simulatedOdds.toFixed(2)}x`);
            syncLobbyApplicationState();
            exitActiveGameSession();
        }

        function exitActiveGameSession() {
            if(casinoStateEngine.multiplierSimulationTimer) {
                clearInterval(casinoStateEngine.multiplierSimulationTimer);
                casinoStateEngine.multiplierSimulationTimer = null;
            }
            document.getElementById('gamePlayScreenOverlay').classList.add('hidden');
            casinoStateEngine.activeGameIndex = null;
        }
    </script>
</body>
</html>
