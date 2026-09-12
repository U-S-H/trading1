<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>micro1 AI Interview Pro Simulator</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-8px); }
        }
        .animate-float { animation: float 3s ease-in-out infinite; }
        .glow-effect { box-shadow: 0 0 25px rgba(16, 185, 129, 0.2); }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen font-sans selection:bg-emerald-500 selection:text-slate-950">

    <!-- Top Navigation / Status Bar -->
    <header class="sticky top-0 z-50 bg-slate-900/80 backdrop-blur-md border-b border-slate-800 px-4 py-3 flex items-center justify-between">
        <div class="flex items-center gap-3">
            <div class="w-3 h-3 rounded-full bg-emerald-500 animate-ping"></div>
            <span class="font-bold tracking-wider text-emerald-400 text-sm md:text-base">micro1 AI Simulator v2.0</span>
        </div>
        <div class="flex items-center gap-4 text-xs md:text-sm">
            <div class="bg-slate-800 border border-slate-700 px-3 py-1 rounded-full flex items-center gap-2">
                <span class="text-slate-400">Timer:</span>
                <span id="masterTimer" class="font-mono text-amber-400 font-bold">55:00</span>
            </div>
            <button onclick="switchTab('dashboard')" class="bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition text-slate-200">Dashboard</button>
        </div>
    </header>

    <main class="max-w-5xl mx-auto p-4 md:p-8 space-y-8">

        <!-- DASHBOARD TAB -->
        <div id="tab-dashboard" class="space-y-8 animate-fadeIn">
            <!-- Hero Banner with AI Avatar Feel -->
            <div class="bg-gradient-to-r from-slate-900 via-slate-800 to-slate-900 border border-slate-700/60 p-6 md:p-8 rounded-2xl relative overflow-hidden glow-effect space-y-6">
                <div class="absolute -right-10 -bottom-10 w-48 h-48 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
                
                <div class="flex flex-col md:flex-row items-center justify-between gap-6">
                    <div class="space-y-3 text-center md:text-left">
                        <span class="bg-emerald-500/10 text-emerald-400 text-xs px-3 py-1 rounded-full border border-emerald-500/20 font-medium">Ready for Interview</span>
                        <h1 class="text-3xl md:text-5xl font-extrabold tracking-tight text-white">Ace Your <span class="text-emerald-400">micro1</span> Assessment</h1>
                        <p class="text-slate-400 max-w-xl text-sm md:text-base">~55 Minutes Q&A + 25 Minutes Live Coding Exercise. Practice interactively with real-time feedback simulator!</p>
                    </div>
                    <!-- AI Hologram Circle -->
                    <div class="relative w-28 h-28 flex items-center justify-center bg-slate-950 rounded-full border-2 border-emerald-500/40 animate-float shadow-lg shadow-emerald-950">
                        <div class="absolute inset-0 rounded-full bg-emerald-500/5 animate-pulse"></div>
                        <span class="text-3xl">🤖</span>
                    </div>
                </div>

                <!-- Quick Action Launch Cards -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 pt-4 border-t border-slate-700/50">
                    <button onclick="switchTab('mock')" class="bg-slate-800/80 hover:bg-slate-800 border border-slate-700 p-4 rounded-xl text-left transition hover:border-emerald-500/50 group">
                        <div class="text-2xl mb-2 group-hover:scale-110 transition-transform">🎯</div>
                        <h3 class="font-bold text-emerald-300">Mock Interview Q&A</h3>
                        <p class="text-xs text-slate-400 mt-1">Simulate AI interviewer questions with voice/text prompts.</p>
                    </button>
                    <button onclick="switchTab('quiz')" class="bg-slate-800/80 hover:bg-slate-800 border border-slate-700 p-4 rounded-xl text-left transition hover:border-emerald-500/50 group">
                        <div class="text-2xl mb-2 group-hover:scale-110 transition-transform">⚡</div>
                        <h3 class="font-bold text-emerald-300">Interactive Quiz Test</h3>
                        <p class="text-xs text-slate-400 mt-1">Test your React, Tailwind & JS core knowledge instantly.</p>
                    </button>
                    <button onclick="switchTab('coding')" class="bg-slate-800/80 hover:bg-slate-800 border border-slate-700 p-4 rounded-xl text-left transition hover:border-emerald-500/50 group">
                        <div class="text-2xl mb-2 group-hover:scale-110 transition-transform">💻</div>
                        <h3 class="font-bold text-emerald-300">Live Coding Arena</h3>
                        <p class="text-xs text-slate-400 mt-1">Practice 25-minute data-fetching & form patterns.</p>
                    </button>
                </div>
            </div>

            <!-- Syllabus Overview Grid -->
            <div class="space-y-4">
                <h2 class="text-xl font-bold text-slate-200 border-l-4 border-emerald-400 pl-3">Interview Focus Topics</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-2 hover:border-slate-700 transition">
                        <h3 class="font-semibold text-amber-300 flex items-center gap-2"><span>⚛️</span> React + JavaScript Frontend Engineering</h3>
                        <p class="text-xs text-slate-400">Hooks lifecycle, state management, closures, and ES6+ features.</p>
                    </div>
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-2 hover:border-slate-700 transition">
                        <h3 class="font-semibold text-amber-300 flex items-center gap-2"><span>🎨</span> Tailwind CSS & Responsive Design</h3>
                        <p class="text-xs text-slate-400">Mobile-first styling, design systems tokens, and reusable components.</p>
                    </div>
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-2 hover:border-slate-700 transition">
                        <h3 class="font-semibold text-amber-300 flex items-center gap-2"><span>🚀</span> Performance & Optimization</h3>
                        <p class="text-xs text-slate-400">React DevTools profiling, code splitting, memoization, and bundle reduction.</p>
                    </div>
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-2 hover:border-slate-700 transition">
                        <h3 class="font-semibold text-amber-300 flex items-center gap-2"><span>♿</span> Accessibility (a11y) & Standards</h3>
                        <p class="text-xs text-slate-400">Semantic HTML, ARIA attributes, keyboard navigation, and Lighthouse audits.</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- MOCK INTERVIEW TAB -->
        <div id="tab-mock" class="hidden space-y-6 animate-fadeIn">
            <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                <h2 class="text-2xl font-bold text-emerald-400">AI Mock Interview Simulator</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
            </div>

            <div class="bg-slate-900 border border-slate-800 p-6 rounded-2xl space-y-6 shadow-xl">
                <!-- AI Question Display Box -->
                <div class="flex items-start gap-4 bg-slate-950 p-5 rounded-xl border border-slate-800">
                    <div class="w-10 h-10 rounded-full bg-emerald-500/20 border border-emerald-500/40 flex items-center justify-center shrink-0 text-lg">🤖</div>
                    <div class="space-y-2">
                        <span class="text-xs text-emerald-400 font-mono">Question <span id="currentQNum">1</span> of 5</span>
                        <p id="aiQuestionText" class="text-slate-200 text-base md:text-lg font-medium">Can you explain the key differences between let, const, and var in JavaScript?</p>
                    </div>
                </div>

                <!-- Answer Input Area -->
                <div class="space-y-3">
                    <label class="text-xs font-medium text-slate-400">Your Answer (Type or speak practice):</label>
                    <textarea id="userAnswerInput" rows="4" class="w-full bg-slate-950 border border-slate-800 rounded-xl p-4 text-slate-100 focus:outline-none focus:border-emerald-500 transition text-sm" placeholder="Type your structured answer here..."></textarea>
                </div>

                <!-- Action Controls -->
                <div class="flex flex-wrap items-center justify-between gap-4">
                    <div class="flex items-center gap-2">
                        <button onclick="playAISpeech()" class="bg-slate-800 hover:bg-slate-700 text-slate-200 px-4 py-2 rounded-xl text-xs font-semibold transition flex items-center gap-2 border border-slate-700">
                            🔊 Listen to Question
                        </button>
                        <button onclick="showAIHint()" class="bg-slate-800 hover:bg-slate-700 text-amber-300 px-4 py-2 rounded-xl text-xs font-semibold transition flex items-center gap-2 border border-slate-700">
                            💡 Show Pro Hint
                        </button>
                    </div>
                    <button onclick="nextMockQuestion()" class="bg-emerald-500 hover:bg-emerald-600 text-slate-950 font-bold px-6 py-2.5 rounded-xl text-sm transition shadow-lg shadow-emerald-500/20">
                        Next Question ➔
                    </button>
                </div>

                <!-- Hint Box (Hidden by default) -->
                <div id="hintBox" class="hidden bg-amber-500/10 border border-amber-500/30 p-4 rounded-xl text-amber-200 text-xs space-y-1">
                    <span class="font-bold">Pro Tip:</span> Mention function scope vs block scope, hoisting behavior, and reassignment rules clearly.
                </div>
            </div>
        </div>

        <!-- INTERACTIVE QUIZ TEST TAB -->
        <div id="tab-quiz" class="hidden space-y-6 animate-fadeIn">
            <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                <h2 class="text-2xl font-bold text-emerald-400">Interactive Knowledge Test</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
            </div>

            <div class="bg-slate-900 border border-slate-800 p-6 rounded-2xl space-y-6 shadow-xl">
                <div class="flex justify-between items-center text-xs text-slate-400">
                    <span>Quiz Progress: <span id="quizProg">1 / 4</span></span>
                    <span>Score: <span id="quizScore" class="text-emerald-400 font-bold">0</span></span>
                </div>

                <div class="space-y-4">
                    <h3 id="quizQuestion" class="text-lg font-semibold text-slate-200">What does the dependency array in useEffect control?</h3>
                    <div id="quizOptions" class="grid grid-cols-1 gap-3">
                        <!-- Options generated dynamically -->
                    </div>
                </div>

                <div id="quizFeedback" class="hidden p-4 rounded-xl text-sm font-medium"></div>
            </div>
        </div>

        <!-- LIVE CODING ARENA TAB -->
        <div id="tab-coding" class="hidden space-y-6 animate-fadeIn">
            <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                <h2 class="text-2xl font-bold text-emerald-400">Live Coding Exercise Arena</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
            </div>

            <div class="space-y-6">
                <!-- Snippet 1 -->
                <div class="bg-slate-900 border border-slate-800 p-6 rounded-2xl space-y-4 shadow-xl">
                    <div class="flex items-center justify-between">
                        <h3 class="font-semibold text-emerald-300">Pattern 1: Data Fetching & State Handling</h3>
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

                <!-- Snippet 2 -->
                <div class="bg-slate-900 border border-slate-800 p-6 rounded-2xl space-y-4 shadow-xl">
                    <div class="flex items-center justify-between">
                        <h3 class="font-semibold text-emerald-300">Pattern 2: Dynamic Form Control</h3>
                        <button onclick="copySnippet('code2', this)" class="text-xs bg-slate-800 hover:bg-slate-700 border border-slate-700 px-3 py-1.5 rounded-lg transition text-slate-200">📋 Copy Code</button>
                    </div>
                    <pre class="bg-slate-950 p-4 rounded-xl overflow-x-auto text-xs text-emerald-400 font-mono border border-slate-800"><code id="code2">import { useState } from 'react';

export default function FormHandler() {
  const [form, setForm] = useState({ name: '', email: '' });

  return (
    &lt;form onSubmit={(e) => { e.preventDefault(); alert('Submitted!'); }} className="p-4 space-y-3 max-w-sm"&gt;
      &lt;input 
        type="text" 
        placeholder="Name"
        value={form.name}
        onChange={e => setForm({...form, name: e.target.value})}
        className="w-full p-2 bg-slate-800 rounded border border-slate-700 text-white"
      /&gt;
      &lt;button type="submit" className="bg-emerald-500 text-slate-950 font-bold px-4 py-2 rounded"&gt;Submit&lt;/button&gt;
    &lt;/form&gt;
  );
}</code></pre>
                </div>
            </div>
        </div>

    </main>

    <!-- Interactive JavaScript Logic -->
    <script>
        // Tab Switcher
        function switchTab(tabId) {
            ['dashboard', 'mock', 'quiz', 'coding'].forEach(id => {
                document.getElementById('tab-' + id).classList.add('hidden');
            });
            document.getElementById('tab-' + tabId).classList.remove('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Master Countdown Timer (55 Minutes)
        let totalSeconds = 55 * 60;
        setInterval(() => {
            if (totalSeconds > 0) {
                totalSeconds--;
                let mins = Math.floor(totalSeconds / 60);
                let secs = totalSeconds % 60;
                document.getElementById('masterTimer').innerText = `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
            }
        }, 1000);

        // Mock Q&A Data
        const mockQuestions = [
            { q: "Can you explain the key differences between let, const, and var in JavaScript?", hint: "Mention function vs block scope and hoisting rules." },
            { q: "How does the useEffect hook handle component lifecycles in React?", hint: "Discuss how the dependency array maps to mount, update, and unmount phases." },
            { q: "How does Tailwind CSS handle responsive design differently than standard CSS?", hint: "Mention mobile-first utility prefixes like sm:, md:, and lg:." },
            { q: "What strategies do you use for optimizing initial load performance in a React app?", hint: "Talk about code splitting with React.lazy, WebP images, and asset optimization." },
            { q: "Why is semantic HTML important for accessibility standards?", hint: "Discuss screen reader compatibility and Lighthouse audits." }
        ];
        let currentQIndex = 0;

        function nextMockQuestion() {
            currentQIndex = (currentQIndex + 1) % mockQuestions.length;
            document.getElementById('currentQNum').innerText = currentQIndex + 1;
            document.getElementById('aiQuestionText').innerText = mockQuestions[currentQIndex].q;
            document.getElementById('userAnswerInput').value = '';
            document.getElementById('hintBox').classList.add('hidden');
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
                alert('Speech synthesis not supported on this browser.');
            }
        }

        // Quiz Data
        const quizData = [
            {
                q: "What does the dependency array in useEffect control?",
                options: [
                    "When the component is initially deleted from DOM",
                    "When the effect callback re-runs based on value changes",
                    "The global CSS styling of the application",
                    "None of the above"
                ],
                correct: 1
            },
            {
                q: "Which Tailwind utility defines a responsive medium screen breakpoint?",
                options: ["tab:", "md:", "lg:", "screen-mid:"],
                correct: 1
            },
            {
                q: "How do you prevent prop drilling in large React applications?",
                options: ["Using inline styles", "Using React Context API or state management libraries", "Deleting props entirely", "Using nested divs"],
                correct: 1
            }
        ];
        let currentQuizIndex = 0;
        let score = 0;

        function loadQuiz() {
            if (currentQuizIndex >= quizData.length) {
                document.getElementById('tab-quiz').innerHTML = `
                    <div class="bg-slate-900 border border-slate-800 p-8 rounded-2xl text-center space-y-4">
                        <h2 class="text-2xl font-bold text-emerald-400">🎉 Quiz Completed!</h2>
                        <p class="text-slate-300">Your final score: <span class="text-amber-400 font-bold">${score} / ${quizData.length}</span></p>
                        <button onclick="currentQuizIndex=0; score=0; loadQuiz(); switchTab('dashboard');" class="bg-emerald-500 text-slate-950 font-bold px-6 py-2 rounded-xl">Back to Dashboard</button>
                    </div>
                `;
                return;
            }

            const item = quizData[currentQuizIndex];
            document.getElementById('quizProg').innerText = `${currentQuizIndex + 1} / ${quizData.length}`;
            document.getElementById('quizScore').innerText = score;
            document.getElementById('quizQuestion').innerText = item.q;
            
            const optionsContainer = document.getElementById('quizOptions');
            optionsContainer.innerHTML = '';
            item.options.forEach((opt, idx) => {
                const btn = document.createElement('button');
                btn.className = "w-full text-left p-4 bg-slate-950 hover:bg-slate-800 border border-slate-800 rounded-xl transition text-sm text-slate-200";
                btn.innerText = opt;
                btn.onclick = () => checkQuizAnswer(idx, item.correct);
                optionsContainer.appendChild(btn);
            });
            document.getElementById('quizFeedback').classList.add('hidden');
        }

        function checkQuizAnswer(selected, correct) {
            const feedback = document.getElementById('quizFeedback');
            feedback.classList.remove('hidden');
            if (selected === correct) {
                score++;
                feedback.className = "p-4 rounded-xl text-sm font-medium bg-emerald-500/10 text-emerald-300 border border-emerald-500/30";
                feedback.innerText = "✅ Correct answer! Great job.";
            } else {
                feedback.className = "p-4 rounded-xl text-sm font-medium bg-rose-500/10 text-rose-300 border border-rose-500/30";
                feedback.innerText = "❌ Incorrect. Keep practicing!";
            }
            setTimeout(() => {
                currentQuizIndex++;
                loadQuiz();
            }, 1500);
        }

        // Copy Code Helper
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

        // Initialize Quiz on load
        loadQuiz();
    </script>
</body>
</html>
