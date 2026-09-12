<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>micro1 AI Interview Master Sheet & Ultimate Pro Simulator</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
        }
    </script>
    <style>
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-6px); }
        }
        .animate-float { animation: float 3s ease-in-out infinite; }
        
        /* Flashcard 3D Flip Styles */
        .perspective-1000 { perspective: 1000px; }
        .transform-style-3d { transform-style: preserve-3d; }
        .backface-hidden { backface-visibility: hidden; }
        .rotate-y-180 { transform: rotateY(180deg); }
    </style>
</head>
<body id="bodyRoot" class="bg-[#f0f2ff] dark:bg-slate-950 text-slate-800 dark:text-slate-100 min-h-screen font-sans selection:bg-indigo-500 selection:text-white transition-colors duration-300">

    <!-- Top Navigation / Status Bar -->
    <header class="sticky top-0 z-50 bg-white/95 dark:bg-slate-900/95 backdrop-blur-md border-b border-indigo-100 dark:border-slate-800 px-4 py-3 flex items-center justify-between shadow-sm">
        <div class="flex items-center gap-2">
            <div class="w-2.5 h-2.5 rounded-full bg-indigo-600 animate-ping"></div>
            <span class="font-extrabold tracking-tight text-indigo-900 dark:text-indigo-400 text-sm md:text-base">micro1. Ultimate Pro</span>
        </div>
        <div class="flex items-center gap-2 md:gap-3 text-xs md:text-sm">
            <div class="bg-indigo-50 dark:bg-slate-800 border border-indigo-200 dark:border-slate-700 px-3 py-1 rounded-full flex items-center gap-1.5 text-indigo-900 dark:text-indigo-300 font-medium">
                <span>⏱️ Timer:</span>
                <span id="masterTimer" class="font-mono text-indigo-600 dark:text-indigo-400 font-bold">55:00</span>
                <button onclick="toggleMasterTimer()" id="timerToggleBtn" class="ml-1 text-[10px] bg-indigo-200 dark:bg-slate-700 px-1.5 py-0.5 rounded text-indigo-900 dark:text-slate-200">⏸️</button>
            </div>
            <button onclick="toggleDarkMode()" class="bg-indigo-100 dark:bg-slate-800 hover:bg-indigo-200 dark:hover:bg-slate-700 text-indigo-900 dark:text-indigo-300 px-2.5 py-1.5 rounded-lg transition font-medium" title="Toggle Theme">🌓</button>
            <button onclick="switchTab('dashboard')" class="bg-indigo-100 dark:bg-slate-800 hover:bg-indigo-200 dark:hover:bg-slate-700 text-indigo-900 dark:text-indigo-300 px-3 py-1.5 rounded-lg transition font-medium">Dashboard</button>
            <button onclick="switchTab('bookmarks')" class="bg-amber-100 dark:bg-amber-950/50 hover:bg-amber-200 text-amber-900 dark:text-amber-300 px-3 py-1.5 rounded-lg transition font-medium border border-amber-200 dark:border-amber-800">⭐ Saved (<span id="bookmarkCount">0</span>)</button>
        </div>
    </header>

    <main class="max-w-4xl mx-auto p-4 md:p-8 space-y-8">

        <!-- DASHBOARD TAB -->
        <div id="tab-dashboard" class="space-y-6">
            <div class="bg-white dark:bg-slate-900 border border-indigo-100 dark:border-slate-800 p-6 md:p-10 rounded-2xl shadow-xl shadow-indigo-100/50 dark:shadow-none space-y-6 relative overflow-hidden">
                <div class="space-y-3">
                    <h1 class="text-3xl md:text-4xl font-black tracking-tight text-indigo-950 dark:text-white">micro1<span class="text-indigo-600">.</span> Assessment Hub</h1>
                    <p class="text-slate-600 dark:text-slate-300 text-sm md:text-base leading-relaxed max-w-2xl">
                        Please note that this interview will take <strong>~55 minutes</strong> with each question having a limited time for a response. You will answer by speaking or typing. Ensure you're in a quiet spot with a stable internet connection. Once complete, a <strong>25-minute coding exercise</strong> will follow.
                    </p>
                </div>

                <!-- Topics Container -->
                <div class="bg-[#f5f7ff] dark:bg-slate-800/60 border border-indigo-100 dark:border-slate-700 p-5 rounded-xl space-y-3">
                    <p class="text-xs font-bold text-indigo-900 dark:text-indigo-300 uppercase tracking-wide">Interview Core Topics:</p>
                    <div class="flex flex-wrap gap-2">
                        <span class="bg-indigo-100 dark:bg-indigo-950/60 text-indigo-800 dark:text-indigo-300 text-xs px-3 py-1.5 rounded-lg font-medium">React + JavaScript Engineering</span>
                        <span class="bg-indigo-100 dark:bg-indigo-950/60 text-indigo-800 dark:text-indigo-300 text-xs px-3 py-1.5 rounded-lg font-medium">Tailwind CSS + Responsive Layouts</span>
                        <span class="bg-indigo-100 dark:bg-indigo-950/60 text-indigo-800 dark:text-indigo-300 text-xs px-3 py-1.5 rounded-lg font-medium">Frontend Performance Optimization</span>
                        <span class="bg-indigo-100 dark:bg-indigo-950/60 text-indigo-800 dark:text-indigo-300 text-xs px-3 py-1.5 rounded-lg font-medium">State Management & Hooks</span>
                    </div>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 pt-4 border-t border-indigo-50 dark:border-slate-800">
                    <button onclick="switchTab('qa')" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold p-4 rounded-xl text-left transition shadow-md shadow-indigo-200 dark:shadow-none group">
                        <div class="text-xl mb-1">🃏</div>
                        <h3 class="text-sm">Flashcards & Q&A Bank</h3>
                    </button>
                    <button onclick="switchTab('mock')" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold p-4 rounded-xl text-left transition shadow-md shadow-indigo-200 dark:shadow-none group">
                        <div class="text-xl mb-1">🤖</div>
                        <h3 class="text-sm">Interactive Mock Simulator</h3>
                    </button>
                    <button onclick="switchTab('coding')" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold p-4 rounded-xl text-left transition shadow-md shadow-indigo-200 dark:shadow-none group">
                        <div class="text-xl mb-1">💻</div>
                        <h3 class="text-sm">25-Min Coding Arena</h3>
                    </button>
                </div>
            </div>
        </div>

        <!-- Q&A PREP & FLASHCARD TAB -->
        <div id="tab-qa" class="hidden space-y-6">
            <div class="flex flex-wrap items-center justify-between border-b border-indigo-100 dark:border-slate-800 pb-4 gap-4">
                <div>
                    <h2 class="text-2xl font-black text-indigo-950 dark:text-white">Interactive Flashcard Q&A Bank</h2>
                    <p class="text-xs text-slate-500 dark:text-slate-400">Search topics or click cards to flip answers!</p>
                </div>
                <div class="flex items-center gap-2">
                    <button onclick="toggleViewMode()" id="viewModeBtn" class="bg-indigo-100 dark:bg-slate-800 hover:bg-indigo-200 dark:hover:bg-slate-700 text-xs text-indigo-900 dark:text-indigo-300 px-3 py-2 rounded-lg font-medium transition">Switch to List View</button>
                    <button onclick="switchTab('dashboard')" class="text-xs bg-slate-200 dark:bg-slate-800 hover:bg-slate-300 dark:hover:bg-slate-700 text-slate-800 dark:text-slate-200 px-3 py-2 rounded-lg font-medium transition">Back</button>
                </div>
            </div>

            <!-- Search Bar -->
            <div class="relative">
                <input type="text" id="searchQuery" oninput="filterFlashcards()" placeholder="🔍 Search questions or topics (e.g. React, Tailwind, Hooks)..." class="w-full bg-white dark:bg-slate-900 border border-indigo-200 dark:border-slate-800 rounded-xl px-4 py-3 text-sm text-indigo-950 dark:text-white focus:outline-none focus:border-indigo-600 shadow-sm">
            </div>

            <!-- Flashcard Container -->
            <div id="flashcardContainer" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <!-- Dynamically populated via JS -->
            </div>
        </div>

        <!-- BOOKMARKS TAB -->
        <div id="tab-bookmarks" class="hidden space-y-6">
            <div class="flex items-center justify-between border-b border-indigo-100 dark:border-slate-800 pb-4">
                <h2 class="text-2xl font-black text-indigo-950 dark:text-white">Saved Bookmarked Questions</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-200 dark:bg-slate-800 hover:bg-slate-300 dark:hover:bg-slate-700 text-slate-800 dark:text-slate-200 px-3 py-2 rounded-lg font-medium transition">Back</button>
            </div>
            <div id="bookmarksList" class="space-y-4">
                <!-- Populated via JS -->
            </div>
        </div>

        <!-- MOCK SIMULATOR TAB -->
        <div id="tab-mock" class="hidden space-y-6">
            <div class="flex flex-wrap items-center justify-between border-b border-indigo-100 dark:border-slate-800 pb-4 gap-4">
                <div class="flex items-center gap-3">
                    <h2 class="text-2xl font-black text-indigo-950 dark:text-white">AI Mock Simulator</h2>
                    <button onclick="shuffleMockQuestions()" class="bg-indigo-100 dark:bg-slate-800 hover:bg-indigo-200 dark:hover:bg-slate-700 text-indigo-900 dark:text-indigo-300 text-xs px-3 py-1.5 rounded-lg font-medium transition">🔀 Shuffle</button>
                </div>
                <div class="flex items-center gap-3">
                    <div class="bg-white dark:bg-slate-900 border border-indigo-200 dark:border-slate-800 px-3 py-1 rounded-lg text-xs font-mono text-indigo-900 dark:text-indigo-300 shadow-sm">
                        ⏱️ Question Time: <span id="questionTimer" class="text-indigo-600 dark:text-indigo-400 font-bold">00:00</span>
                    </div>
                    <button onclick="switchTab('dashboard')" class="text-xs bg-slate-200 dark:bg-slate-800 hover:bg-slate-300 dark:hover:bg-slate-700 text-slate-800 dark:text-slate-200 px-3 py-2 rounded-lg font-medium transition">Back</button>
                </div>
            </div>

            <!-- Progress Bar -->
            <div class="w-full bg-indigo-100 dark:bg-slate-800 rounded-full h-2.5 overflow-hidden">
                <div id="mockProgressBar" class="bg-indigo-600 h-2.5 rounded-full transition-all duration-300" style="width: 20%"></div>
            </div>

            <div class="bg-white dark:bg-slate-900 border border-indigo-100 dark:border-slate-800 p-6 rounded-2xl space-y-6 shadow-xl relative overflow-hidden">
                <div class="flex items-start gap-4 bg-[#f5f7ff] dark:bg-slate-800/60 p-5 rounded-xl border border-indigo-100 dark:border-slate-700">
                    <div class="w-10 h-10 rounded-full bg-indigo-100 dark:bg-indigo-950 border border-indigo-200 dark:border-slate-700 flex items-center justify-center shrink-0 text-lg">🤖</div>
                    <div class="space-y-2 flex-1">
                        <div class="flex items-center justify-between">
                            <span class="text-xs text-indigo-600 dark:text-indigo-400 font-mono font-bold">Question <span id="currentQNum">1</span> of <span id="totalQCount">5</span></span>
                            <button onclick="bookmarkCurrentMock()" id="mockBookmarkBtn" class="text-xs text-slate-500 dark:text-slate-400 hover:text-amber-600 font-medium transition">⭐ Save Question</button>
                        </div>
                        <p id="aiQuestionText" class="text-indigo-950 dark:text-white text-base md:text-lg font-semibold">Can you explain the key differences between let, const, and var in JavaScript?</p>
                    </div>
                </div>

                <div class="space-y-2">
                    <label class="text-xs font-bold text-slate-600 dark:text-slate-300">Your Practice Answer:</label>
                    <textarea id="userAnswerInput" rows="4" class="w-full bg-[#f9fafd] dark:bg-slate-950 border border-indigo-200 dark:border-slate-800 rounded-xl p-4 text-slate-800 dark:text-slate-200 focus:outline-none focus:border-indigo-600 transition text-sm" placeholder="Type your response here..."></textarea>
                </div>

                <!-- Self Confidence Rating -->
                <div class="flex flex-wrap items-center justify-between gap-2 bg-indigo-50/50 dark:bg-slate-800/40 p-3 rounded-xl border border-indigo-100 dark:border-slate-800">
                    <span class="text-xs font-bold text-indigo-900 dark:text-indigo-300">Rate your confidence:</span>
                    <div class="flex gap-2">
                        <button onclick="setConfidence(1)" class="conf-btn px-3 py-1 rounded-lg text-xs bg-white dark:bg-slate-900 border border-indigo-200 dark:border-slate-700 hover:bg-indigo-600 hover:text-white transition" data-score="1">😕 Need Work</button>
                        <button onclick="setConfidence(2)" class="conf-btn px-3 py-1 rounded-lg text-xs bg-white dark:bg-slate-900 border border-indigo-200 dark:border-slate-700 hover:bg-indigo-600 hover:text-white transition" data-score="2">🙂 Good</button>
                        <button onclick="setConfidence(3)" class="conf-btn px-3 py-1 rounded-lg text-xs bg-white dark:bg-slate-900 border border-indigo-200 dark:border-slate-700 hover:bg-indigo-600 hover:text-white transition" data-score="3">🔥 Mastered</button>
                    </div>
                </div>

                <div class="flex flex-wrap items-center justify-between gap-4">
                    <div class="flex items-center gap-2">
                        <button onclick="playAISpeech()" class="bg-slate-100 dark:bg-slate-800 hover:bg-slate-200 dark:hover:bg-slate-700 text-slate-700 dark:text-slate-300 px-4 py-2 rounded-xl text-xs font-semibold transition border border-slate-300 dark:border-slate-700">🔊 Listen</button>
                        <button onclick="showAIHint()" class="bg-amber-100 dark:bg-amber-950/50 hover:bg-amber-200 text-amber-900 dark:text-amber-300 px-4 py-2 rounded-xl text-xs font-semibold transition border border-amber-300 dark:border-amber-800">💡 Pro Hint</button>
                    </div>
                    <div class="flex items-center gap-2">
                        <button onclick="exportNotes()" class="bg-cyan-100 dark:bg-cyan-950/50 hover:bg-cyan-200 text-cyan-900 dark:text-cyan-300 px-4 py-2 rounded-xl text-xs font-semibold transition border border-cyan-300 dark:border-cyan-800">📥 Export .txt</button>
                        <button onclick="nextMockQuestion()" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold px-6 py-2.5 rounded-xl text-sm transition shadow-md shadow-indigo-200 dark:shadow-none">Next Question ➔</button>
                    </div>
                </div>

                <div id="hintBox" class="hidden bg-amber-50 dark:bg-amber-950/40 border border-amber-200 dark:border-amber-800 p-4 rounded-xl text-amber-900 dark:text-amber-200 text-xs space-y-1">
                    <span class="font-bold">Pro Tip:</span> Talk about block scope and hoisting clearly.
                </div>
            </div>
        </div>

        <!-- CODING ARENA TAB -->
        <div id="tab-coding" class="hidden space-y-6">
            <div class="flex items-center justify-between border-b border-indigo-100 dark:border-slate-800 pb-4">
                <h2 class="text-2xl font-black text-indigo-950 dark:text-white">25-Minute Coding Exercise Arena</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-200 dark:bg-slate-800 hover:bg-slate-300 dark:hover:bg-slate-700 text-slate-800 dark:text-slate-200 px-3 py-2 rounded-lg font-medium transition">Back</button>
            </div>

            <!-- Coding Exercise 1 -->
            <div class="bg-white dark:bg-slate-900 border border-indigo-100 dark:border-slate-800 p-6 rounded-2xl space-y-4 shadow-xl">
                <div class="flex items-center justify-between">
                    <h3 class="font-bold text-indigo-900 dark:text-indigo-300">Pattern 1: Data Fetching Table/List</h3>
                    <button onclick="copySnippet('code1', this)" class="text-xs bg-indigo-50 dark:bg-slate-800 hover:bg-indigo-100 dark:hover:bg-slate-700 border border-indigo-200 dark:border-slate-700 px-3 py-1.5 rounded-lg transition text-indigo-900 dark:text-indigo-300 font-medium">📋 Copy Code</button>
                </div>
                <pre class="bg-slate-900 text-emerald-400 p-4 rounded-xl overflow-x-auto text-xs font-mono border border-slate-800"><code id="code1">import { useState, useEffect } from 'react';

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

            <!-- Coding Exercise 2 -->
            <div class="bg-white dark:bg-slate-900 border border-indigo-100 dark:border-slate-800 p-6 rounded-2xl space-y-4 shadow-xl">
                <div class="flex items-center justify-between">
                    <h3 class="font-bold text-indigo-900 dark:text-indigo-300">Pattern 2: Debounced Search Input</h3>
                    <button onclick="copySnippet('code2', this)" class="text-xs bg-indigo-50 dark:bg-slate-800 hover:bg-indigo-100 dark:hover:bg-slate-700 border border-indigo-200 dark:border-slate-700 px-3 py-1.5 rounded-lg transition text-indigo-900 dark:text-indigo-300 font-medium">📋 Copy Code</button>
                </div>
                <pre class="bg-slate-900 text-emerald-400 p-4 rounded-xl overflow-x-auto text-xs font-mono border border-slate-800"><code id="code2">import { useState, useEffect } from 'react';

export default function DebouncedSearch() {
  const [query, setQuery] = useState('');
  const [debouncedQuery, setDebouncedQuery] = useState('');

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedQuery(query);
    }, 500);
    return () => clearTimeout(timer);
  }, [query]);

  return (
    &lt;div className="p-4 space-y-3"&gt;
      &lt;input 
        type="text" 
        value={query} 
        onChange={(e) => setQuery(e.target.value)} 
        placeholder="Search..." 
        className="p-2 border rounded bg-slate-800 text-white w-full"
      /&gt;
      &lt;p className="text-sm text-slate-300"&gt;Searching for: {debouncedQuery}&lt;/p&gt;
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

        // Dark Mode Toggle
        function toggleDarkMode() {
            const html = document.documentElement;
            html.classList.toggle('dark');
        }

        // Master Timer with Pause/Resume
        let totalSeconds = 55 * 60;
        let isTimerRunning = true;
        let masterTimerInterval = setInterval(() => {
            if (isTimerRunning && totalSeconds > 0) {
                totalSeconds--;
                let mins = Math.floor(totalSeconds / 60);
                let secs = totalSeconds % 60;
                document.getElementById('masterTimer').innerText = `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
            }
        }, 1000);

        function toggleMasterTimer() {
            isTimerRunning = !isTimerRunning;
            document.getElementById('timerToggleBtn').innerText = isTimerRunning ? "⏸️" : "▶️";
        }

        // Question Stopwatch Timer
        let qSeconds = 0;
        let qTimerInterval = setInterval(() => {
            qSeconds++;
            let mins = Math.floor(qSeconds / 60);
            let secs = qSeconds % 60;
            document.getElementById('questionTimer').innerText = `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
        }, 1000);

        // Expanded & Detailed Rich Q&A Database
        let questionsBank = [
            { 
                id: 1, 
                topic: "React + JS", 
                q: "Difference between let, const, and var?", 
                a: "Scope: var is function-scoped, while let and const are block-scoped. Hoisting: var hoists with undefined; let and const hoist into Temporal Dead Zone (TDZ) and throw ReferenceError if accessed before declaration. Re-assignment: var allows re-declaration and re-assignment; let allows re-assignment but not re-declaration; const is constant with fixed reference (though nested object properties can mutate).", 
                hint: "Mention block scope, hoisting/TDZ, and re-assignment rules." 
            },
            { 
                id: 2, 
                topic: "Tailwind CSS", 
                q: "How does Tailwind handle responsive design?", 
                a: "Tailwind follows a mobile-first philosophy. It uses predefined screen size prefixes like sm:, md:, lg:, xl:, and 2xl: to apply utility classes dynamically as screen widths increase.", 
                hint: "Mention mobile-first utility prefixes like md: and lg:." 
            },
            { 
                id: 3, 
                topic: "React Hooks", 
                q: "How does useEffect handle component lifecycles?", 
                a: "An empty dependency array [] runs on mount once. Passing specific variables triggers execution on mount and whenever those variables update. Returning a cleanup function from the effect handles unmounting or prior cleanup.", 
                hint: "Discuss dependency array behavior and cleanup functions." 
            },
            { 
                id: 4, 
                topic: "Performance", 
                q: "What is code splitting in React?", 
                a: "Code splitting divides large JavaScript bundles into smaller chunks loaded lazily on demand using React.lazy() and Suspense, drastically improving initial page load speed.", 
                hint: "Mention React.lazy and Suspense." 
            },
            { 
                id: 5, 
                topic: "State Management", 
                q: "When should you use Context API vs Redux?", 
                a: "Context API is ideal for low-frequency global states like themes, user authentication, or localization. Redux or Zustand is better suited for complex, high-frequency global state updates across large applications.", 
                hint: "Compare update frequency and application scale." 
            }
        ];

        let mockQuestions = [...questionsBank];
        let currentQIndex = 0;
        let isListView = false;
        let userNotesHistory = [];
        let currentConfidenceScore = 0;

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

        function setConfidence(score) {
            currentConfidenceScore = score;
            document.querySelectorAll('.conf-btn').forEach(btn => {
                if(parseInt(btn.getAttribute('data-score')) === score) {
                    btn.classList.add('bg-indigo-600', 'text-white');
                } else {
                    btn.classList.remove('bg-indigo-600', 'text-white');
                }
            });
        }

        function renderBookmarks() {
            const container = document.getElementById('bookmarksList');
            const bookmarks = getBookmarks();
            const savedItems = questionsBank.filter(q => bookmarks.includes(q.id));

            if (savedItems.length === 0) {
                container.innerHTML = `<p class="text-slate-500 text-sm">No bookmarked questions yet. Click '⭐ Save' on questions to save them here!</p>`;
                return;
            }

            container.innerHTML = savedItems.map(item => `
                <div class="bg-white dark:bg-slate-900 border border-indigo-100 dark:border-slate-800 p-4 rounded-xl space-y-2 shadow-sm">
                    <span class="text-xs text-indigo-600 dark:text-indigo-400 font-mono font-bold">${item.topic}</span>
                    <h3 class="font-bold text-indigo-950 dark:text-white text-sm">${item.q}</h3>
                    <p class="text-xs text-slate-600 dark:text-slate-300"><span class="text-indigo-600 dark:text-indigo-400 font-semibold">Answer:</span> ${item.a}</p>
                </div>
            `).join('');
        }

        function renderFlashcards(filterText = "") {
            const container = document.getElementById('flashcardContainer');
            const bookmarks = getBookmarks();
            const filtered = questionsBank.filter(item => 
                item.q.toLowerCase().includes(filterText.toLowerCase()) || 
                item.topic.toLowerCase().includes(filterText.toLowerCase()) ||
                item.a.toLowerCase().includes(filterText.toLowerCase())
            );

            if (filtered.length === 0) {
                container.innerHTML = `<p class="text-slate-500 text-sm col-span-2 text-center py-8">No matching questions found, sweetie!</p>`;
                return;
            }

            if (isListView) {
                container.innerHTML = filtered.map(item => `
                    <div class="bg-white dark:bg-slate-900 border border-indigo-100 dark:border-slate-800 p-5 rounded-xl space-y-3 shadow-sm">
                        <div class="flex items-center justify-between">
                            <span class="text-xs text-indigo-600 dark:text-indigo-400 font-mono font-bold">${item.topic}</span>
                            <button onclick="toggleBookmark(${item.id})" class="text-xs text-amber-600 dark:text-amber-400 font-medium">${bookmarks.includes(item.id) ? '⭐ Saved' : '☆ Save'}</button>
                        </div>
                        <h3 class="font-bold text-indigo-950 dark:text-white text-sm">Q: ${item.q}</h3>
                        <p class="text-xs text-slate-600 dark:text-slate-300"><span class="text-indigo-600 dark:text-indigo-400 font-semibold">Ans:</span> ${item.a}</p>
                    </div>
                `).join('');
            } else {
                container.innerHTML = filtered.map(item => `
                    <div class="h-64 perspective-1000 cursor-pointer group" onclick="this.querySelector('.transform-style-3d').classList.toggle('rotate-y-180')">
                        <div class="relative w-full h-full duration-500 transform-style-3d bg-white dark:bg-slate-900 border border-indigo-100 dark:border-slate-800 rounded-2xl p-6 shadow-md flex flex-col justify-between">
                            <!-- Front Side -->
                            <div class="absolute inset-0 p-6 backface-hidden flex flex-col justify-between overflow-y-auto">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs text-indigo-600 dark:text-indigo-400 font-mono font-bold">${item.topic}</span>
                                    <span class="text-xs text-slate-400">🔄 Click to Flip</span>
                                </div>
                                <h3 class="font-bold text-indigo-950 dark:text-white text-base md:text-lg my-auto">${item.q}</h3>
                                <p class="text-xs text-slate-400 text-right">Card #${item.id}</p>
                            </div>
                            <!-- Back Side -->
                            <div class="absolute inset-0 p-6 backface-hidden rotate-y-180 bg-indigo-900 dark:bg-slate-800 border border-indigo-700 dark:border-slate-700 text-white rounded-2xl flex flex-col justify-between overflow-y-auto">
                                <span class="text-xs text-indigo-300 font-mono font-bold">Detailed Answer Key</span>
                                <p class="text-xs md:text-sm text-indigo-100 my-auto">${item.a}</p>
                                <p class="text-xs text-indigo-300 text-right">Flip back ↩</p>
                            </div>
                        </div>
                    </div>
                `).join('');
            }
        }

        function filterFlashcards() {
            const query = document.getElementById('searchQuery').value;
            renderFlashcards(query);
        }

        function toggleViewMode() {
            isListView = !isListView;
            document.getElementById('viewModeBtn').innerText = isListView ? "Switch to Flashcard View" : "Switch to List View";
            filterFlashcards();
        }

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
            currentConfidenceScore = 0;
            document.querySelectorAll('.conf-btn').forEach(btn => btn.classList.remove('bg-indigo-600', 'text-white'));
            
            // Update Progress Bar
            let progress = ((currentQIndex + 1) / mockQuestions.length) * 100;
            document.getElementById('mockProgressBar').style.width = progress + '%';
            qSeconds = 0;
        }

        function nextMockQuestion() {
            const ans = document.getElementById('userAnswerInput').value;
            userNotesHistory.push({ q: mockQuestions[currentQIndex].q, answer: ans, confidence: currentConfidenceScore });

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

        function exportNotes() {
            let content = "--- micro1 AI Mock Interview Practice Notes ---\n\n";
            userNotesHistory.forEach((item, index) => {
                content += `Q${index + 1}: ${item.q}\nMy Answer: ${item.answer}\nConfidence Level: ${item.confidence}/3\n\n`;
            });
            const blob = new Blob([content], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'micro1_practice_notes.txt';
            a.click();
            URL.revokeObjectURL(url);
        }

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
                conf.style.backgroundColor = ['#4f46e5', '#10b981', '#f59e0b', '#ec4899'][Math.floor(Math.random() * 4)];
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
                btn.classList.add("bg-indigo-600", "text-white");
                setTimeout(() => {
                    btn.innerText = original;
                    btn.classList.remove("bg-indigo-600", "text-white");
                }, 2000);
            });
        }

        updateBookmarkCount();
        renderFlashcards();
    </script>
</body>
</html>
