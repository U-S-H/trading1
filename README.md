<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>micro1 AI Interview Master Sheet & Pro Simulator</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-8px); }
        }
        .animate-float { animation: float 3s ease-in-out infinite; }
        .glow-effect { box-shadow: 0 0 25px rgba(16, 185, 129, 0.2); }
        
        /* Flashcard 3D Flip Styles */
        .perspective-1000 { perspective: 1000px; }
        .transform-style-3d { transform-style: preserve-3d; }
        .backface-hidden { backface-visibility: hidden; }
        .rotate-y-180 { transform: rotateY(180deg); }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen font-sans selection:bg-emerald-500 selection:text-slate-950">

    <!-- Top Navigation / Status Bar -->
    <header class="sticky top-0 z-50 bg-slate-900/90 backdrop-blur-md border-b border-slate-800 px-4 py-3 flex items-center justify-between">
        <div class="flex items-center gap-3">
            <div class="w-3 h-3 rounded-full bg-emerald-500 animate-ping"></div>
            <span class="font-bold tracking-wider text-emerald-400 text-sm md:text-base">micro1 AI Interview Hub Pro</span>
        </div>
        <div class="flex items-center gap-2 md:gap-3 text-xs md:text-sm">
            <div class="bg-slate-800 border border-slate-700 px-3 py-1 rounded-full flex items-center gap-2">
                <span class="text-slate-400">Timer:</span>
                <span id="masterTimer" class="font-mono text-amber-400 font-bold">55:00</span>
            </div>
            <button onclick="switchTab('dashboard')" class="bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition text-slate-200">Dashboard</button>
            <button onclick="switchTab('bookmarks')" class="bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition text-amber-300">⭐ Saved (<span id="bookmarkCount">0</span>)</button>
        </div>
    </header>

    <main class="max-w-5xl mx-auto p-4 md:p-8 space-y-8">

        <!-- DASHBOARD TAB -->
        <div id="tab-dashboard" class="space-y-8">
            <!-- Hero Banner -->
            <div class="bg-gradient-to-r from-slate-900 via-slate-800 to-slate-900 border border-slate-700/60 p-6 md:p-8 rounded-2xl relative overflow-hidden glow-effect space-y-6">
                <div class="absolute -right-10 -bottom-10 w-48 h-48 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
                
                <div class="flex flex-col md:flex-row items-center justify-between gap-6">
                    <div class="space-y-3 text-center md:text-left">
                        <span class="bg-emerald-500/10 text-emerald-400 text-xs px-3 py-1 rounded-full border border-emerald-500/20 font-medium">micro1 Assessment Guidelines</span>
                        <h1 class="text-3xl md:text-4xl font-extrabold tracking-tight text-white">~55 Minutes Q&A + <span class="text-emerald-400">25-Min Coding</span></h1>
                        <p class="text-slate-400 max-w-xl text-sm md:text-base">Advanced prep hub loaded with Flashcards, Live Timers, Bookmarks, and Confetti celebration mode!</p>
                    </div>
                    <div class="relative w-28 h-28 flex items-center justify-center bg-slate-950 rounded-full border-2 border-emerald-500/40 animate-float shadow-lg shadow-emerald-950">
                        <div class="absolute inset-0 rounded-full bg-emerald-500/5 animate-pulse"></div>
                        <span class="text-3xl">🚀</span>
                    </div>
                </div>

                <!-- Action Launch Cards -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 pt-4 border-t border-slate-700/50">
                    <button onclick="switchTab('qa')" class="bg-slate-800/80 hover:bg-slate-800 border border-slate-700 p-4 rounded-xl text-left transition hover:border-emerald-500/50 group">
                        <div class="text-2xl mb-2 group-hover:scale-110 transition-transform">🃏</div>
                        <h3 class="font-bold text-emerald-300">Flashcards & Q&A Bank</h3>
                        <p class="text-xs text-slate-400 mt-1">Flip cards to reveal answers and bookmark tricky questions.</p>
                    </button>
                    <button onclick="switchTab('mock')" class="bg-slate-800/80 hover:bg-slate-800 border border-slate-700 p-4 rounded-xl text-left transition hover:border-emerald-500/50 group">
                        <div class="text-2xl mb-2 group-hover:scale-110 transition-transform">🤖</div>
                        <h3 class="font-bold text-emerald-300">Interactive Mock Simulator</h3>
                        <p class="text-xs text-slate-400 mt-1">Per-question stopwatch, shuffle mode, and export answers to .txt.</p>
                    </button>
                    <button onclick="switchTab('coding')" class="bg-slate-800/80 hover:bg-slate-800 border border-slate-700 p-4 rounded-xl text-left transition hover:border-emerald-500/50 group">
                        <div class="text-2xl mb-2 group-hover:scale-110 transition-transform">💻</div>
                        <h3 class="font-bold text-emerald-300">25-Min Coding Arena</h3>
                        <p class="text-xs text-slate-400 mt-1">Data-fetching patterns and component templates.</p>
                    </button>
                </div>
            </div>
        </div>

        <!-- Q&A PREP & FLASHCARD TAB -->
        <div id="tab-qa" class="hidden space-y-6">
            <div class="flex flex-wrap items-center justify-between border-b border-slate-800 pb-4 gap-4">
                <div>
                    <h2 class="text-2xl font-bold text-emerald-400">Interactive Flashcard Q&A Bank</h2>
                    <p class="text-xs text-slate-400">Click any card to flip it and reveal the answer!</p>
                </div>
                <div class="flex items-center gap-2">
                    <button onclick="toggleViewMode()" id="viewModeBtn" class="bg-slate-800 hover:bg-slate-700 text-xs text-amber-300 px-3 py-1.5 rounded-lg border border-slate-700 transition">Switch to List View</button>
                    <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
                </div>
            </div>

            <!-- Flashcard Container -->
            <div id="flashcardContainer" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Dynamically populated via JS -->
            </div>
        </div>

        <!-- BOOKMARKS TAB -->
        <div id="tab-bookmarks" class="hidden space-y-6">
            <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                <h2 class="text-2xl font-bold text-amber-400">Saved Bookmarked Questions</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
            </div>
            <div id="bookmarksList" class="space-y-4">
                <!-- Populated via JS -->
            </div>
        </div>

        <!-- MOCK SIMULATOR TAB -->
        <div id="tab-mock" class="hidden space-y-6">
            <div class="flex flex-wrap items-center justify-between border-b border-slate-800 pb-4 gap-4">
                <div class="flex items-center gap-3">
                    <h2 class="text-2xl font-bold text-emerald-400">AI Mock Simulator</h2>
                    <button onclick="shuffleMockQuestions()" class="bg-slate-800 hover:bg-slate-700 text-xs px-3 py-1.5 rounded-lg border border-slate-700 text-amber-300 transition">🔀 Shuffle Questions</button>
                </div>
                <div class="flex items-center gap-3">
                    <div class="bg-slate-900 border border-slate-700 px-3 py-1 rounded-lg text-xs font-mono">
                        ⏱️ Question Time: <span id="questionTimer" class="text-amber-400 font-bold">00:00</span>
                    </div>
                    <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
                </div>
            </div>

            <div class="bg-slate-900 border border-slate-800 p-6 rounded-2xl space-y-6 shadow-xl relative overflow-hidden">
                <div class="flex items-start gap-4 bg-slate-950 p-5 rounded-xl border border-slate-800">
                    <div class="w-10 h-10 rounded-full bg-emerald-500/20 border border-emerald-500/40 flex items-center justify-center shrink-0 text-lg">🤖</div>
                    <div class="space-y-2 flex-1">
                        <div class="flex items-center justify-between">
                            <span class="text-xs text-emerald-400 font-mono">Question <span id="currentQNum">1</span> of <span id="totalQCount">3</span></span>
                            <button onclick="bookmarkCurrentMock()" id="mockBookmarkBtn" class="text-xs text-slate-400 hover:text-amber-300 transition">⭐ Save Question</button>
                        </div>
                        <p id="aiQuestionText" class="text-slate-200 text-base md:text-lg font-medium">Can you explain the key differences between let, const, and var in JavaScript?</p>
                    </div>
                </div>

                <div class="space-y-3">
                    <label class="text-xs font-medium text-slate-400">Your Practice Answer:</label>
                    <textarea id="userAnswerInput" rows="4" class="w-full bg-slate-950 border border-slate-800 rounded-xl p-4 text-slate-100 focus:outline-none focus:border-emerald-500 transition text-sm" placeholder="Type your response here..."></textarea>
                </div>

                <div class="flex flex-wrap items-center justify-between gap-4">
                    <div class="flex items-center gap-2">
                        <button onclick="playAISpeech()" class="bg-slate-800 hover:bg-slate-700 text-slate-200 px-4 py-2 rounded-xl text-xs font-semibold transition border border-slate-700">🔊 Listen</button>
                        <button onclick="showAIHint()" class="bg-slate-800 hover:bg-slate-700 text-amber-300 px-4 py-2 rounded-xl text-xs font-semibold transition border border-slate-700">💡 Pro Hint</button>
                    </div>
                    <div class="flex items-center gap-2">
                        <button onclick="exportNotes()" class="bg-slate-800 hover:bg-slate-700 text-cyan-300 px-4 py-2 rounded-xl text-xs font-semibold transition border border-slate-700">📥 Export .txt</button>
                        <button onclick="nextMockQuestion()" class="bg-emerald-500 hover:bg-emerald-600 text-slate-950 font-bold px-6 py-2.5 rounded-xl text-sm transition">Next Question ➔</button>
                    </div>
                </div>

                <div id="hintBox" class="hidden bg-amber-500/10 border border-amber-500/30 p-4 rounded-xl text-amber-200 text-xs space-y-1">
                    <span class="font-bold">Pro Tip:</span> Talk about block scope and hoisting clearly.
                </div>
            </div>
        </div>

        <!-- CODING ARENA TAB -->
        <div id="tab-coding" class="hidden space-y-6">
            <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                <h2 class="text-2xl font-bold text-emerald-400">25-Minute Coding Exercise Arena</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
            </div>

            <div class="bg-slate-900 border border-slate-800 p-6 rounded-2xl space-y-4">
                <div class="flex items-center justify-between">
                    <h3 class="font-semibold text-emerald-300">Pattern 1: Data Fetching Table/List (Crucial)</h3>
                    <button onclick="copySnippet('code1', this)" class="text-xs bg-slate-800 hover:bg-slate-700 border border-slate-700 px-3 py-1.5 rounded-lg transition text-slate-200">📋 Copy Code</button>
                </div>
                <pre class="bg-slate-950 p-4 rounded-xl overflow-x-auto text-xs text-emerald-400 font-mono border border-slate-800"><code id="code1">import { useState, useEffect } from 'react';

export default function DataFetcher() {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts?_limit=3')
      .then(res => res.json())
      .then(data => { setData(data); setLoading(false); });
  }, []);

  if (loading) return &lt;div className="p-4 text-center"&gt;Loading...&lt;/div&gt;;

  return (
    &lt;div className="p-4 space-y-3"&gt;
      {data.map(item => (
        &lt;div key={item.id} className="p-3 bg-slate-800 rounded-lg border border-slate-700"&gt;
          &lt;h4 className="font-bold text-amber-300"&gt;{item.title}&lt;/h4&gt;
        &lt;/div&gt;
      ))}
    &lt;/div&gt;
  );
}</code></pre>
            </div>
        </div>

    </main>

    <!-- Confetti Container -->
    <div id="confettiContainer" class="fixed inset-0 pointer-events-none z-50 overflow-hidden hidden"></div>

    <!-- Script Logic -->
    <script>
        function switchTab(tabId) {
            ['dashboard', 'qa', 'bookmarks', 'mock', 'coding'].forEach(id => {
                document.getElementById('tab-' + id).classList.add('hidden');
            });
            document.getElementById('tab-' + tabId).classList.remove('hidden');
            if (tabId === 'bookmarks') renderBookmarks();
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Master Timer
        let totalSeconds = 55 * 60;
        setInterval(() => {
            if (totalSeconds > 0) {
                totalSeconds--;
                let mins = Math.floor(totalSeconds / 60);
                let secs = totalSeconds % 60;
                document.getElementById('masterTimer').innerText = `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
            }
        }, 1000);

        // Question Stopwatch Timer
        let qSeconds = 0;
        let qTimerInterval = setInterval(() => {
            qSeconds++;
            let mins = Math.floor(qSeconds / 60);
            let secs = qSeconds % 60;
            document.getElementById('questionTimer').innerText = `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
        }, 1000);

        // Q&A Database & Flashcards
        let questionsBank = [
            { id: 1, topic: "React + JS", q: "Difference between let, const, and var?", a: "var is function-scoped and hoisted. let and const are block-scoped.", hint: "Mention block scope and hoisting." },
            { id: 2, topic: "Tailwind CSS", q: "How does Tailwind handle responsive design?", a: "Uses a mobile-first philosophy with prefixes like sm: and md:.", hint: "Mention mobile-first utility prefixes." },
            { id: 3, topic: "React Hooks", q: "How does useEffect handle component lifecycles?", a: "Dependency array maps to mount/update phases.", hint: "Discuss dependency array behavior." },
            { id: 4, topic: "Performance", q: "What is code splitting in React?", a: "Loading parts of the app lazily using React.lazy and Suspense to reduce initial bundle size.", hint: "Mention React.lazy and Suspense." }
        ];

        let mockQuestions = [...questionsBank];
        let currentQIndex = 0;
        let isListView = false;
        let userNotesHistory = [];

        // Bookmarks system using LocalStorage
        function getBookmarks() {
            return JSON.parse(localStorage.getItem('micro1_bookmarks') || '[]');
        }

        function updateBookmarkCount() {
            document.getElementById('bookmarkCount').innerText = getBookmarks().length;
        }

        function toggleBookmark(id) {
            let bookmarks = getBookmarks();
            if (bookmarks.includes(id)) {
                bookmarks = bookmarks.filter(b => b !== id);
            } else {
                bookmarks.push(id);
            }
            localStorage.setItem('micro1_bookmarks', JSON.stringify(bookmarks));
            updateBookmarkCount();
            renderFlashcards();
        }

        function bookmarkCurrentMock() {
            const currentItem = mockQuestions[currentQIndex];
            toggleBookmark(currentItem.id);
            alert("Question bookmarked successfully, sweetie!");
        }

        function renderBookmarks() {
            const container = document.getElementById('bookmarksList');
            const bookmarks = getBookmarks();
            const savedItems = questionsBank.filter(q => bookmarks.includes(q.id));

            if (savedItems.length === 0) {
                container.innerHTML = `<p class="text-slate-400 text-sm">No bookmarked questions yet. Click '⭐ Save' on questions to save them here!</p>`;
                return;
            }

            container.innerHTML = savedItems.map(item => `
                <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-2">
                    <span class="text-xs text-amber-400 font-mono">${item.topic}</span>
                    <h3 class="font-bold text-slate-100 text-sm">${item.q}</h3>
                    <p class="text-xs text-slate-400"><span class="text-emerald-400 font-semibold">Answer:</span> ${item.a}</p>
                </div>
            `).join('');
        }

        // Render Flashcards / List View
        function renderFlashcards() {
            const container = document.getElementById('flashcardContainer');
            const bookmarks = getBookmarks();

            if (isListView) {
                container.innerHTML = questionsBank.map(item => `
                    <div class="bg-slate-900 border border-slate-800 p-5 rounded-xl space-y-3">
                        <div class="flex items-center justify-between">
                            <span class="text-xs text-emerald-400 font-mono">${item.topic}</span>
                            <button onclick="toggleBookmark(${item.id})" class="text-xs text-amber-300">${bookmarks.includes(item.id) ? '⭐ Saved' : '☆ Save'}</button>
                        </div>
                        <h3 class="font-bold text-slate-200 text-sm">Q: ${item.q}</h3>
                        <p class="text-xs text-slate-400"><span class="text-emerald-400 font-semibold">Ans:</span> ${item.a}</p>
                    </div>
                `).join('');
            } else {
                container.innerHTML = questionsBank.map(item => `
                    <div class="h-56 perspective-1000 cursor-pointer group" onclick="this.querySelector('.transform-style-3d').classList.toggle('rotate-y-180')">
                        <div class="relative w-full h-full duration-500 transform-style-3d bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-xl flex flex-col justify-between">
                            <!-- Front Side -->
                            <div class="absolute inset-0 p-6 backface-hidden flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs text-emerald-400 font-mono">${item.topic}</span>
                                    <span class="text-xs text-slate-500">🔄 Click to Flip</span>
                                </div>
                                <h3 class="font-bold text-slate-100 text-base md:text-lg">${item.q}</h3>
                                <p class="text-xs text-slate-500 text-right">Card #${item.id}</p>
                            </div>
                            <!-- Back Side -->
                            <div class="absolute inset-0 p-6 backface-hidden rotate-y-180 bg-slate-880 bg-slate-900 border border-emerald-500/30 rounded-2xl flex flex-col justify-between">
                                <span class="text-xs text-amber-400 font-mono">Answer Key</span>
                                <p class="text-xs md:text-sm text-slate-300">${item.a}</p>
                                <p class="text-xs text-emerald-400 text-right">Flip back ↩</p>
                            </div>
                        </div>
                    </div>
                `).join('');
            }
        }

        function toggleViewMode() {
            isListView = !isListView;
            document.getElementById('viewModeBtn').innerText = isListView ? "Switch to Flashcard View" : "Switch to List View";
            renderFlashcards();
        }

        // Mock Navigation & Shuffle
        function shuffleMockQuestions() {
            mockQuestions = [...questionsBank].sort(() => Math.random() - 0.5);
            currentQIndex = 0;
            qSeconds = 0;
            loadMockQuestion();
            alert("Questions shuffled successfully, sweetie!");
        }

        function loadMockQuestion() {
            document.getElementById('currentQNum').innerText = currentQIndex + 1;
            document.getElementById('totalQCount').innerText = mockQuestions.length;
            document.getElementById('aiQuestionText').innerText = mockQuestions[currentQIndex].q;
            document.getElementById('userAnswerInput').value = '';
            document.getElementById('hintBox').classList.add('hidden');
            qSeconds = 0;
        }

        function nextMockQuestion() {
            const ans = document.getElementById('userAnswerInput').value;
            userNotesHistory.push({ q: mockQuestions[currentQIndex].q, answer: ans });

            currentQIndex++;
            if (currentQIndex >= mockQuestions.length) {
                triggerConfetti();
                alert("Wonderful job sweetie! You completed all mock interview questions!");
                currentQIndex = 0;
            }
            loadMockQuestion();
        }

        function showAIHint() {
            const hintBox = document.getElementById('hintBox');
            hintBox.innerText = "Pro Tip: " + mockQuestions[currentQIndex].hint;
            hintBox.classList.remove('hidden');
        }

        function playAISpeech() {
            if ('speechSynthesis' in window) {
                const text = document.getElementById('aiQuestionText').innerText;
                const utterance = new SpeechSynthesisUtterance(text);
                window.speechSynthesis.speak(utterance);
            } else {
                alert('Speech synthesis not supported.');
            }
        }

        // Export Notes to .txt
        function exportNotes() {
            let content = "--- micro1 AI Mock Interview Practice Notes ---\n\n";
            userNotesHistory.forEach((item, index) => {
                content += `Q${index + 1}: ${item.q}\nMy Answer: ${item.answer}\n\n`;
            });
            const blob = new Blob([content], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'micro1_practice_notes.txt';
            a.click();
            URL.revokeObjectURL(url);
        }

        // Confetti Effect
        function triggerConfetti() {
            const container = document.getElementById('confettiContainer');
            container.classList.remove('hidden');
            container.innerHTML = '';

            for (let i = 0; i < 50; i++) {
                const conf = document.createElement('div');
                conf.style.position = 'absolute';
                conf.style.left = Math.random() * 100 + 'vw';
                conf.style.top = '-10px';
                conf.style.width = (Math.random() * 8 + 5) + 'px';
                conf.style.height = (Math.random() * 12 + 6) + 'px';
                conf.style.backgroundColor = ['#10b981', '#f59e0b', '#3b82f6', '#ec4899'][Math.floor(Math.random() * 4)];
                conf.style.opacity = Math.random();
                conf.style.transform = `rotate(${Math.random() * 360}deg)`;
                conf.style.transition = `transform 3s ease-in, top 3s ease-in`;
                container.appendChild(conf);

                setTimeout(() => {
                    conf.style.top = '105vh';
                    conf.style.transform += ` rotate(${Math.random() * 500}deg)`;
                }, 50);
            }

            setTimeout(() => {
                container.classList.add('hidden');
                container.innerHTML = '';
            }, 3500);
        }

        function copySnippet(elementId, btn) {
            const codeText = document.getElementById(elementId).innerText;
            navigator.clipboard.writeText(codeText).then(() => {
                const original = btn.innerText;
                btn.innerText = "✅ Copied!";
                btn.classList.add("bg-emerald-600", "text-white");
                setTimeout(() => {
                    btn.innerText = original;
                    btn.classList.remove("bg-emerald-600", "text-white");
                }, 2000);
            });
        }

        // Initialize counts and render cards on load
        updateBookmarkCount();
        renderFlashcards();
    </script>
</body>
</html>
