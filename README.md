<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>micro1 AI Interview Master Sheet & Simulator</title>
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
    <header class="sticky top-0 z-50 bg-slate-900/90 backdrop-blur-md border-b border-slate-800 px-4 py-3 flex items-center justify-between">
        <div class="flex items-center gap-3">
            <div class="w-3 h-3 rounded-full bg-emerald-500 animate-ping"></div>
            <span class="font-bold tracking-wider text-emerald-400 text-sm md:text-base">micro1 AI Interview Hub</span>
        </div>
        <div class="flex items-center gap-3 text-xs md:text-sm">
            <div class="bg-slate-800 border border-slate-700 px-3 py-1 rounded-full flex items-center gap-2">
                <span class="text-slate-400">Interview Timer:</span>
                <span id="masterTimer" class="font-mono text-amber-400 font-bold">55:00</span>
            </div>
            <button onclick="switchTab('dashboard')" class="bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition text-slate-200">Dashboard</button>
        </div>
    </header>

    <main class="max-w-5xl mx-auto p-4 md:p-8 space-y-8">

        <!-- DASHBOARD TAB -->
        <div id="tab-dashboard" class="space-y-8">
            <!-- Hero Banner based on micro1 exact instructions -->
            <div class="bg-gradient-to-r from-slate-900 via-slate-800 to-slate-900 border border-slate-700/60 p-6 md:p-8 rounded-2xl relative overflow-hidden glow-effect space-y-6">
                <div class="absolute -right-10 -bottom-10 w-48 h-48 bg-emerald-500/10 rounded-full blur-3xl pointer-events-none"></div>
                
                <div class="flex flex-col md:flex-row items-center justify-between gap-6">
                    <div class="space-y-3 text-center md:text-left">
                        <span class="bg-emerald-500/10 text-emerald-400 text-xs px-3 py-1 rounded-full border border-emerald-500/20 font-medium">micro1 Assessment Guidelines</span>
                        <h1 class="text-3xl md:text-4xl font-extrabold tracking-tight text-white">~55 Minutes Q&A + <span class="text-emerald-400">25-Min Coding</span></h1>
                        <p class="text-slate-400 max-w-xl text-sm md:text-base">This interview takes ~55 minutes with limited time per question. Answer by speaking or typing. Ensure a quiet spot and stable internet[span_2](start_span)[span_2](end_span). Recorded and available in your profile link[span_3](start_span)[span_3](end_span). Followed by a 25-minute coding exercise[span_4](start_span)[span_4](end_span).</p>
                    </div>
                    <div class="relative w-28 h-28 flex items-center justify-center bg-slate-950 rounded-full border-2 border-emerald-500/40 animate-float shadow-lg shadow-emerald-950">
                        <div class="absolute inset-0 rounded-full bg-emerald-500/5 animate-pulse"></div>
                        <span class="text-3xl">🎙️</span>
                    </div>
                </div>

                <!-- Action Launch Cards -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 pt-4 border-t border-slate-700/50">
                    <button onclick="switchTab('qa')" class="bg-slate-800/80 hover:bg-slate-800 border border-slate-700 p-4 rounded-xl text-left transition hover:border-emerald-500/50 group">
                        <div class="text-2xl mb-2 group-hover:scale-110 transition-transform">📋</div>
                        <h3 class="font-bold text-emerald-300">All Topics Q&A Prep</h3>
                        <p class="text-xs text-slate-400 mt-1">Review exact questions and structured answers for all 6 topics.</p>
                    </button>
                    <button onclick="switchTab('mock')" class="bg-slate-800/80 hover:bg-slate-800 border border-slate-700 p-4 rounded-xl text-left transition hover:border-emerald-500/50 group">
                        <div class="text-2xl mb-2 group-hover:scale-110 transition-transform">🤖</div>
                        <h3 class="font-bold text-emerald-300">Interactive Mock Simulator</h3>
                        <p class="text-xs text-slate-400 mt-1">Practice with speech/text simulator and custom interview timer.</p>
                    </button>
                    <button onclick="switchTab('coding')" class="bg-slate-800/80 hover:bg-slate-800 border border-slate-700 p-4 rounded-xl text-left transition hover:border-emerald-500/50 group">
                        <div class="text-2xl mb-2 group-hover:scale-110 transition-transform">💻</div>
                        <h3 class="font-bold text-emerald-300">25-Min Coding Arena</h3>
                        <p class="text-xs text-slate-400 mt-1">Data-fetching patterns and dynamic form state handling code templates.</p>
                    </button>
                </div>
            </div>

            <!-- Topics List from Screenshot -->
            <div class="space-y-4">
                <h2 class="text-xl font-bold text-slate-200 border-l-4 border-emerald-400 pl-3">You will be interviewed on these topics[span_5](start_span)[span_5](end_span):</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-1">
                        <span class="text-xs text-emerald-400 font-mono">Topic 1</span>
                        <h3 class="font-semibold text-amber-300">React + JavaScript Frontend Engineering[span_6](start_span)[span_6](end_span)</h3>
                    </div>
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-1">
                        <span class="text-xs text-emerald-400 font-mono">Topic 2</span>
                        <h3 class="font-semibold text-amber-300">Tailwind CSS + Responsive UI / Design Systems[span_7](start_span)[span_7](end_span)</h3>
                    </div>
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-1">
                        <span class="text-xs text-emerald-400 font-mono">Topic 3</span>
                        <h3 class="font-semibold text-amber-300">Pixel-perfect UI Implementation & Designer Collaboration[span_8](start_span)[span_8](end_span)</h3>
                    </div>
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-1">
                        <span class="text-xs text-emerald-400 font-mono">Topic 4</span>
                        <h3 class="font-semibold text-amber-300">Frontend Performance Optimization[span_9](start_span)[span_9](end_span)</h3>
                    </div>
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-1">
                        <span class="text-xs text-emerald-400 font-mono">Topic 5</span>
                        <h3 class="font-semibold text-amber-300">Accessibility (a11y) & Usability Standards[span_10](start_span)[span_10](end_span)</h3>
                    </div>
                    <div class="bg-slate-900 border border-slate-800 p-4 rounded-xl space-y-1">
                        <span class="text-xs text-emerald-400 font-mono">Topic 6</span>
                        <h3 class="font-semibold text-amber-300">Custom questions defined for the job[span_11](start_span)[span_11](end_span)</h3>
                    </div>
                </div>
            </div>
        </div>

        <!-- Q&A PREP TAB -->
        <div id="tab-qa" class="hidden space-y-6">
            <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                <h2 class="text-2xl font-bold text-emerald-400">Comprehensive Interview Q&A Bank</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
            </div>

            <div class="space-y-6">
                <!-- Topic 1 -->
                <div class="bg-slate-900 p-5 rounded-xl border border-slate-800 space-y-3">
                    <h3 class="text-lg font-bold text-amber-300">1. React + JavaScript Frontend Engineering</h3>
                    <div class="border-t border-slate-800 pt-3 space-y-2">
                        <p class="font-medium text-slate-200 text-sm">Q: Difference between let, const, and var?</p>
                        <p class="text-slate-400 text-xs"><span class="text-emerald-400 font-semibold">Answer:</span> <code class="bg-slate-950 px-1 rounded text-amber-200">var</code> is function-scoped and hoisted with undefined. <code class="bg-slate-950 px-1 rounded text-amber-200">let</code> and <code class="bg-slate-950 px-1 rounded text-amber-200">const</code> are block-scoped. <code class="bg-slate-950 px-1 rounded text-amber-200">let</code> allows reassignment, whereas <code class="bg-slate-950 px-1 rounded text-amber-200">const</code> does not.</p>
                    </div>
                    <div class="border-t border-slate-800 pt-3 space-y-2">
                        <p class="font-medium text-slate-200 text-sm">Q: How does useEffect handle component lifecycles?</p>
                        <p class="text-slate-400 text-xs"><span class="text-emerald-400 font-semibold">Answer:</span> Combines componentDidMount, componentDidUpdate, and componentWillUnmount based on the dependency array.</p>
                    </div>
                </div>

                <!-- Topic 2 -->
                <div class="bg-slate-900 p-5 rounded-xl border border-slate-800 space-y-3">
                    <h3 class="text-lg font-bold text-amber-300">2. Tailwind CSS + Responsive UI / Design Systems</h3>
                    <div class="border-t border-slate-800 pt-3 space-y-2">
                        <p class="font-medium text-slate-200 text-sm">Q: How does Tailwind handle responsive design?</p>
                        <p class="text-slate-400 text-xs"><span class="text-emerald-400 font-semibold">Answer:</span> Uses a mobile-first philosophy with breakpoint prefixes like <code class="bg-slate-950 px-1 rounded text-amber-200">sm:</code>, <code class="bg-slate-950 px-1 rounded text-amber-200">md:</code>, and <code class="bg-slate-950 px-1 rounded text-amber-200">lg:</code>.</p>
                    </div>
                </div>

                <!-- Topic 3 -->
                <div class="bg-slate-900 p-5 rounded-xl border border-slate-800 space-y-3">
                    <h3 class="text-lg font-bold text-amber-300">3. Pixel-perfect UI Implementation & Designer Collaboration</h3>
                    <div class="border-t border-slate-800 pt-3 space-y-2">
                        <p class="font-medium text-slate-200 text-sm">Q: How do you translate a Figma design into Tailwind components?</p>
                        <p class="text-slate-400 text-xs"><span class="text-emerald-400 font-semibold">Answer:</span> Extract exact tokens (colors, typography, spacing) and configure theme extensions in <code class="bg-slate-950 px-1 rounded text-amber-200">tailwind.config.js</code>.</p>
                    </div>
                </div>

                <!-- Topic 4 -->
                <div class="bg-slate-900 p-5 rounded-xl border border-slate-800 space-y-3">
                    <h3 class="text-lg font-bold text-amber-300">4. Frontend Performance Optimization</h3>
                    <div class="border-t border-slate-800 pt-3 space-y-2">
                        <p class="font-medium text-slate-200 text-sm">Q: How do you resolve performance bottlenecks in React?</p>
                        <p class="text-slate-400 text-xs"><span class="text-emerald-400 font-semibold">Answer:</span> Profile using React DevTools, eliminate unnecessary re-renders with <code class="bg-slate-950 px-1 rounded text-amber-200">React.memo</code>, <code class="bg-slate-950 px-1 rounded text-amber-200">useMemo</code>, and code-split with <code class="bg-slate-950 px-1 rounded text-amber-200">React.lazy</code>.</p>
                    </div>
                </div>

                <!-- Topic 5 -->
                <div class="bg-slate-900 p-5 rounded-xl border border-slate-800 space-y-3">
                    <h3 class="text-lg font-bold text-amber-300">5. Accessibility (a11y) & Usability Standards</h3>
                    <div class="border-t border-slate-800 pt-3 space-y-2">
                        <p class="font-medium text-slate-200 text-sm">Q: Why is semantic HTML critical for accessibility?</p>
                        <p class="text-slate-400 text-xs"><span class="text-emerald-400 font-semibold">Answer:</span> Screen readers rely on tags like <code class="bg-slate-950 px-1 rounded text-amber-200">&lt;button&gt;</code> and <code class="bg-slate-950 px-1 rounded text-amber-200">&lt;nav&gt;</code> to interpret structural hierarchy properly.</p>
                    </div>
                </div>

                <!-- Topic 6 -->
                <div class="bg-slate-900 p-5 rounded-xl border border-slate-800 space-y-3">
                    <h3 class="text-lg font-bold text-amber-300">6. Custom Questions Defined for the Job</h3>
                    <div class="border-t border-slate-800 pt-3 space-y-2">
                        <p class="font-medium text-slate-200 text-sm">Q: Tell me about a custom web app built from scratch.</p>
                        <p class="text-slate-400 text-xs"><span class="text-emerald-400 font-semibold">Answer Strategy:</span> Detail architectural choices, custom component layouts, clean state management, and deployment pipelines.</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- INTERACTIVE MOCK SIMULATOR TAB -->
        <div id="tab-mock" class="hidden space-y-6">
            <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                <h2 class="text-2xl font-bold text-emerald-400">AI Mock Interview Simulator</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
            </div>

            <div class="bg-slate-900 border border-slate-800 p-6 rounded-2xl space-y-6 shadow-xl">
                <div class="flex items-start gap-4 bg-slate-950 p-5 rounded-xl border border-slate-800">
                    <div class="w-10 h-10 rounded-full bg-emerald-500/20 border border-emerald-500/40 flex items-center justify-center shrink-0 text-lg">🤖</div>
                    <div class="space-y-2">
                        <span class="text-xs text-emerald-400 font-mono">Question <span id="currentQNum">1</span> of 5</span>
                        <p id="aiQuestionText" class="text-slate-200 text-base md:text-lg font-medium">Can you explain the key differences between let, const, and var in JavaScript?</p>
                    </div>
                </div>

                <div class="space-y-3">
                    <label class="text-xs font-medium text-slate-400">Your Practice Answer (Type or speak):</label>
                    <textarea id="userAnswerInput" rows="4" class="w-full bg-slate-950 border border-slate-800 rounded-xl p-4 text-slate-100 focus:outline-none focus:border-emerald-500 transition text-sm" placeholder="Type your response here..."></textarea>
                </div>

                <div class="flex flex-wrap items-center justify-between gap-4">
                    <div class="flex items-center gap-2">
                        <button onclick="playAISpeech()" class="bg-slate-800 hover:bg-slate-700 text-slate-200 px-4 py-2 rounded-xl text-xs font-semibold transition border border-slate-700">🔊 Listen</button>
                        <button onclick="showAIHint()" class="bg-slate-800 hover:bg-slate-700 text-amber-300 px-4 py-2 rounded-xl text-xs font-semibold transition border border-slate-700">💡 Pro Hint</button>
                    </div>
                    <button onclick="nextMockQuestion()" class="bg-emerald-500 hover:bg-emerald-600 text-slate-950 font-bold px-6 py-2.5 rounded-xl text-sm transition">Next Question ➔</button>
                </div>

                <div id="hintBox" class="hidden bg-amber-500/10 border border-amber-500/30 p-4 rounded-xl text-amber-200 text-xs space-y-1">
                    <span class="font-bold">Pro Tip:</span> Talk about block scope and hoisting clearly.
                </div>
            </div>
        </div>

        <!-- 25-MIN CODING EXERCISE ARENA TAB -->
        <div id="tab-coding" class="hidden space-y-6">
            <div class="flex items-center justify-between border-b border-slate-800 pb-4">
                <h2 class="text-2xl font-bold text-emerald-400">25-Minute Coding Exercise Arena</h2>
                <button onclick="switchTab('dashboard')" class="text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">Back</button>
            </div>

            <p class="text-xs text-slate-400">Right after the ~55 min Q&A portion, there is a 25-minute coding exercise[span_12](start_span)[span_12](end_span). Memorize and practice these core patterns:</p>

            <div class="space-y-6">
                <!-- Code Snippet 1 -->
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

                <!-- Code Snippet 2 -->
                <div class="bg-slate-900 border border-slate-800 p-6 rounded-2xl space-y-4">
                    <div class="flex items-center justify-between">
                        <h3 class="font-semibold text-emerald-300">Pattern 2: Dynamic Form & State Handling</h3>
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

    <!-- Script Logic -->
    <script>
        function switchTab(tabId) {
            ['dashboard', 'qa', 'mock', 'coding'].forEach(id => {
                document.getElementById('tab-' + id).classList.add('hidden');
            });
            document.getElementById('tab-' + tabId).classList.remove('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        let totalSeconds = 55 * 60;
        setInterval(() => {
            if (totalSeconds > 0) {
                totalSeconds--;
                let mins = Math.floor(totalSeconds / 60);
                let secs = totalSeconds % 60;
                document.getElementById('masterTimer').innerText = `${mins.toString().padStart(2, '0')}:${secs.toString().padStart(2, '0')}`;
            }
        }, 1000);

        const mockQuestions = [
            { q: "Can you explain the key differences between let, const, and var in JavaScript?", hint: "Mention function vs block scope and hoisting." },
            { q: "How does the useEffect hook handle component lifecycles in React?", hint: "Discuss how dependency array maps to mount/update phases." },
            { q: "How does Tailwind CSS handle responsive design differently than standard CSS?", hint: "Mention mobile-first utility prefixes like sm: and md:." },
            { q: "What strategies do you use for optimizing initial load performance in a React app?", hint: "Talk about code splitting with React.lazy and asset optimization." },
            { q: "Why is semantic HTML important for accessibility standards?", hint: "Discuss screen reader compatibility." }
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
                alert('Speech synthesis not supported.');
            }
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
    </script>
</body>
</html>
