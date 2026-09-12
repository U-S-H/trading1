<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>micro1 Senior Frontend Interview Prep</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-900 text-slate-100 min-h-screen p-4 md:p-8 font-sans">

    <div class="max-w-5xl mx-auto space-y-10">
        
        <!-- Header -->
        <header class="border-b border-slate-700 pb-6 text-center space-y-4">
            <div>
                <h1 class="text-3xl md:text-4xl font-extrabold text-blue-400">micro1 AI Interview Master Sheet</h1>
                <p class="text-slate-400 mt-2 text-lg">~55 Min Q&A + 25 Min Live Coding Preparation</p>
            </div>

            <!-- Interview Timer Widget -->
            <div class="inline-flex items-center gap-3 bg-slate-800 border border-slate-700 px-4 py-2 rounded-xl text-sm shadow-md">
                <span class="text-emerald-400 font-semibold flex items-center gap-1.5">
                    <span class="w-2.5 h-2.5 rounded-full bg-emerald-500 animate-pulse"></span> Timer:
                </span>
                <span id="interviewTimer" class="font-mono text-amber-300 font-bold tracking-wider">55:00</span>
                <button onclick="toggleTimer()" id="timerBtn" class="text-xs bg-slate-700 hover:bg-slate-600 px-2.5 py-1 rounded text-slate-200 transition">Start</button>
            </div>

            <!-- Quick-Jump Navigation Bar -->
            <nav class="flex flex-wrap justify-center gap-2 pt-2">
                <a href="#react-section" class="text-xs bg-slate-800 hover:bg-slate-700 text-blue-300 border border-slate-700 px-3 py-1.5 rounded-lg transition">React & JS</a>
                <a href="#tailwind-section" class="text-xs bg-slate-800 hover:bg-slate-700 text-blue-300 border border-slate-700 px-3 py-1.5 rounded-lg transition">Tailwind CSS</a>
                <a href="#figma-section" class="text-xs bg-slate-800 hover:bg-slate-700 text-blue-300 border border-slate-700 px-3 py-1.5 rounded-lg transition">Figma UI</a>
                <a href="#perf-section" class="text-xs bg-slate-800 hover:bg-slate-700 text-blue-300 border border-slate-700 px-3 py-1.5 rounded-lg transition">Performance</a>
                <a href="#a11y-section" class="text-xs bg-slate-800 hover:bg-slate-700 text-blue-300 border border-slate-700 px-3 py-1.5 rounded-lg transition">A11y</a>
                <a href="#coding-section" class="text-xs bg-slate-800 hover:bg-slate-700 text-emerald-300 border border-slate-700 px-3 py-1.5 rounded-lg transition">Live Coding Patterns</a>
            </nav>
        </header>

        <!-- SECTION 1: THEORY & Q&A (Based on Image Topics) -->
        <section class="space-y-6">
            <h2 class="text-2xl font-bold text-emerald-400 border-l-4 border-emerald-400 pl-3">Part 1: Interview Q&A (Verbal/Typing)</h2>

            <!-- Topic 1 -->
            <div id="react-section" class="bg-slate-800 p-5 rounded-xl border border-slate-700 space-y-4 shadow-lg scroll-mt-6">
                <h3 class="text-xl font-semibold text-amber-300">1. React + JavaScript Frontend Engineering</h3>
                
                <div class="border-b border-slate-700 pb-3">
                    <p class="font-medium text-slate-200">Q: Can you explain the difference between let, const, and var in JavaScript?</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer:</span> `var` is function-scoped and hoisted with an undefined value. `let` and `const` are block-scoped. `let` allows reassignment, while `const` prevents reassignment of the variable reference[span_1](start_span)[span_1](end_span).</p>
                </div>
                <div class="border-b border-slate-700 pb-3">
                    <p class="font-medium text-slate-200">Q: How does the useEffect hook handle component lifecycles?</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer:</span> It acts as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` combined. The dependency array dictates when it runs, and the return function acts as the cleanup mechanism[span_2](start_span)[span_2](end_span).</p>
                </div>
                <div>
                    <p class="font-medium text-slate-200">Q: What is Prop Drilling and how do you avoid it?</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer:</span> Prop drilling is passing data through multiple nested components that don't need it. I avoid it by using React Context API or state management libraries like Redux or Zustand[span_3](start_span)[span_3](end_span).</p>
                </div>
            </div>

            <!-- Topic 2 -->
            <div id="tailwind-section" class="bg-slate-800 p-5 rounded-xl border border-slate-700 space-y-4 shadow-lg scroll-mt-6">
                <h3 class="text-xl font-semibold text-amber-300">2. Tailwind CSS + Responsive UI / Design Systems</h3>
                
                <div class="border-b border-slate-700 pb-3">
                    <p class="font-medium text-slate-200">Q: How does Tailwind handle responsive design differently than traditional CSS?</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer:</span> Tailwind uses a mobile-first approach with utility variants like `sm:`, `md:`, and `lg:`. Instead of writing separate media queries, you apply these prefixes directly to classes in the HTML[span_4](start_span)[span_4](end_span).</p>
                </div>
                <div>
                    <p class="font-medium text-slate-200">Q: How would you build a reusable button component using Tailwind?</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer:</span> I would create a React component that accepts props for variants (primary, secondary) and conditionally joins Tailwind classes using a utility like `clsx` or `tailwind-merge` to prevent class conflicts[span_5](start_span)[span_5](end_span).</p>
                </div>
            </div>

            <!-- Topic 3 -->
            <div id="figma-section" class="bg-slate-800 p-5 rounded-xl border border-slate-700 space-y-4 shadow-lg scroll-mt-6">
                <h3 class="text-xl font-semibold text-amber-300">3. Pixel-perfect UI Implementation & Designer Collaboration</h3>
                
                <div>
                    <p class="font-medium text-slate-200">Q: A designer gives you a Figma file with a specific design system. How do you implement it in Tailwind?</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer:</span> I extract the exact colors, typography, and spacing scales from Figma and configure them in the `tailwind.config.js` file. This extends Tailwind's default theme to match the designer's tokens exactly, ensuring pixel-perfect consistency across the app[span_6](start_span)[span_6](end_span).</p>
                </div>
            </div>

            <!-- Topic 4 -->
            <div id="perf-section" class="bg-slate-800 p-5 rounded-xl border border-slate-700 space-y-4 shadow-lg scroll-mt-6">
                <h3 class="text-xl font-semibold text-amber-300">4. Frontend Performance Optimization</h3>
                
                <div class="border-b border-slate-700 pb-3">
                    <p class="font-medium text-slate-200">Q: How do you identify and fix performance bottlenecks in a React app?</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer:</span> I use React DevTools Profiler to find components that re-render too often. I fix them by wrapping components in `React.memo`, moving state down the tree, or using `useMemo` and `useCallback` for expensive operations[span_7](start_span)[span_7](end_span).</p>
                </div>
                <div>
                    <p class="font-medium text-slate-200">Q: What strategies do you use for optimizing initial load time?</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer:</span> Implementing code splitting with `React.lazy`, compressing images (using WebP format), lazy-loading off-screen images, and ensuring Tailwind is configured to purge unused CSS for a smaller bundle size[span_8](start_span)[span_8](end_span).</p>
                </div>
            </div>

            <!-- Topic 5 -->
            <div id="a11y-section" class="bg-slate-800 p-5 rounded-xl border border-slate-700 space-y-4 shadow-lg scroll-mt-6">
                <h3 class="text-xl font-semibold text-amber-300">5. Accessibility (a11y) & Usability Standards</h3>
                
                <div>
                    <p class="font-medium text-slate-200">Q: Why is semantic HTML important, and how do you test for accessibility?</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer:</span> Semantic HTML (like using `&lt;button&gt;` instead of a clickable `&lt;div&gt;`) ensures screen readers understand the page structure. I test using automated tools like Lighthouse or axe-core, check color contrast ratios, and verify that all interactive elements are reachable via keyboard (Tab navigation)[span_9](start_span)[span_9](end_span).</p>
                </div>
            </div>

            <!-- Topic 6 -->
            <div class="bg-slate-800 p-5 rounded-xl border border-slate-700 space-y-4 shadow-lg">
                <h3 class="text-xl font-semibold text-amber-300">6. Custom Questions (Experience Based)</h3>
                
                <div>
                    <p class="font-medium text-slate-200">Q: Tell me about a complex web application you've built from scratch.</p>
                    <p class="text-slate-400 text-sm mt-1"><span class="text-emerald-400 font-semibold">Answer Strategy:</span> (Be ready to talk about a recent project. Mention how you handled custom front-end architecture, user authentication, or integrating AI APIs for client projects at Prime Solutions, and the tech stack you chose like Firebase, HTML, CSS, JS)[span_10](start_span)[span_10](end_span).</p>
                </div>
            </div>
        </section>

        <!-- SECTION 2: 25-MINUTE CODING EXERCISE PREP -->
        <section id="coding-section" class="space-y-6 pt-4 scroll-mt-6">
            <h2 class="text-2xl font-bold text-blue-400 border-l-4 border-blue-400 pl-3">Part 2: 25-Minute Coding Exercise Patterns</h2>
            <p class="text-slate-400 mb-4">You will likely be asked to build a functional component, fetch data, and style it with Tailwind. Here are the core patterns to memorize[span_11](start_span)[span_11](end_span). Use the copy buttons to instantly copy code blocks.</p>

            <!-- Coding Snippet 1 -->
            <div class="bg-slate-800 p-5 rounded-xl border border-slate-700 space-y-3">
                <div class="flex items-center justify-between">
                    <h3 class="text-lg font-semibold text-emerald-300">Pattern 1: Data Fetching Table/List (Crucial)</h3>
                    <button onclick="copyCode(this)" class="text-xs bg-slate-700 hover:bg-slate-600 text-slate-200 px-3 py-1.5 rounded-lg transition flex items-center gap-1">
                        📋 Copy Code
                    </button>
                </div>
                <pre class="bg-slate-900 p-4 rounded-lg overflow-x-auto text-xs text-blue-100"><code class="code-block">import { useState, useEffect } from 'react';

export default function DataFetcher() {
  const [data, setData] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/posts?_limit=5');
        if (!response.ok) throw new Error('Network response was not ok');
        const result = await response.json();
        setData(result);
      } catch (err) {
        setError(err.message);
      } finally {
        setLoading(false);
      }
    };
    fetchData();
  }, []);

  if (loading) return &lt;div className="text-center p-4"&gt;Loading...&lt;/div&gt;;
  if (error) return &lt;div className="text-red-500 p-4"&gt;Error: {error}&lt;/div&gt;;

  return (
    &lt;div className="max-w-2xl mx-auto p-4"&gt;
      &lt;h2 className="text-2xl font-bold mb-4"&gt;Latest Posts&lt;/h2&gt;
      &lt;div className="space-y-4"&gt;
        {data.map(item => (
          &lt;div key={item.id} className="p-4 bg-slate-800 rounded-lg shadow-md border border-slate-700"&gt;
            &lt;h3 className="font-semibold text-lg text-emerald-400"&gt;{item.title}&lt;/h3&gt;
            &lt;p className="text-slate-300 mt-2"&gt;{item.body}&lt;/p&gt;
          &lt;/div&gt;
        ))}
      &lt;/div&gt;
    &lt;/div&gt;
  );
}</code></pre>
            </div>

            <!-- Coding Snippet 2 -->
            <div class="bg-slate-800 p-5 rounded-xl border border-slate-700 space-y-3">
                <div class="flex items-center justify-between">
                    <h3 class="text-lg font-semibold text-emerald-300">Pattern 2: Dynamic Form & State Management</h3>
                    <button onclick="copyCode(this)" class="text-xs bg-slate-700 hover:bg-slate-600 text-slate-200 px-3 py-1.5 rounded-lg transition flex items-center gap-1">
                        📋 Copy Code
                    </button>
                </div>
                <pre class="bg-slate-900 p-4 rounded-lg overflow-x-auto text-xs text-blue-100"><code class="code-block">import { useState } from 'react';

export default function ContactForm() {
  const [formData, setFormData] = useState({ name: '', email: '' });

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log('Submitted:', formData);
    // Add logic here
  };

  return (
    &lt;form onSubmit={handleSubmit} className="flex flex-col gap-4 max-w-sm mx-auto p-6 bg-slate-800 rounded-xl"&gt;
      &lt;div&gt;
        &lt;label htmlFor="name" className="block text-sm font-medium text-slate-300 mb-1"&gt;Name&lt;/label&gt;
        &lt;input 
          id="name"
          type="text" 
          className="w-full p-2 rounded bg-slate-900 border border-slate-600 text-white focus:outline-none focus:border-emerald-500"
          value={formData.name}
          onChange={(e) => setFormData({...formData, name: e.target.value})}
          required
        /&gt;
      &lt;/div&gt;
      
      &lt;div&gt;
        &lt;label htmlFor="email" className="block text-sm font-medium text-slate-300 mb-1"&gt;Email&lt;/label&gt;
        &lt;input 
          id="email"
          type="email" 
          className="w-full p-2 rounded bg-slate-900 border border-slate-600 text-white focus:outline-none focus:border-emerald-500"
          value={formData.email}
          onChange={(e) => setFormData({...formData, email: e.target.value})}
          required
        /&gt;
      &lt;/div&gt;

      &lt;button type="submit" className="mt-2 bg-emerald-500 hover:bg-emerald-600 text-slate-900 font-bold py-2 px-4 rounded transition-colors"&gt;
        Submit
      &lt;/button&gt;
    &lt;/form&gt;
  );
}</code></pre>
            </div>
        </section>

        <!-- Footer -->
        <footer class="text-center text-xs text-slate-500 pt-6 border-t border-slate-800 pb-10">
            Good Luck! Focus on writing clean code and explaining your thought process out loud[span_12](start_span)[span_12](end_span).
        </footer>

    </div>

    <!-- Scripts for Timer and Copy Functionality -->
    <script>
        // Copy Code Functionality
        function copyCode(button) {
            const preElement = button.closest('div.space-y-3').querySelector('code.code-block');
            const codeText = preElement.innerText;
            
            navigator.clipboard.writeText(codeText).then(() => {
                const originalText = button.innerHTML;
                button.innerHTML = "✅ Copied!";
                button.classList.add("bg-emerald-600", "text-white");
                setTimeout(() => {
                    button.innerHTML = originalText;
                    button.classList.remove("bg-emerald-600", "text-white");
                }, 2000);
            }).catch(err => {
                console.error('Failed to copy: ', err);
            });
        }

        // Timer Functionality
        let timerInterval;
        let timeLeft = 55 * 60; // 55 minutes in seconds
        let timerRunning = false;

        function toggleTimer() {
            const timerDisplay = document.getElementById('interviewTimer');
            const timerBtn = document.getElementById('timerBtn');

            if (!timerRunning) {
                timerRunning = true;
                timerBtn.innerText = "Pause";
                timerBtn.classList.replace('bg-slate-700', 'bg-amber-600');

                timerInterval = setInterval(() => {
                    if (timeLeft > 0) {
                        timeLeft--;
                        let minutes = Math.floor(timeLeft / 60);
                        let seconds = timeLeft % 60;
                        timerDisplay.innerText = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
                    } else {
                        clearInterval(timerInterval);
                        timerDisplay.innerText = "Time's Up!";
                        timerBtn.innerText = "Done";
                        timerRunning = false;
                    }
                }, 1000);
            } else {
                timerRunning = false;
                clearInterval(timerInterval);
                timerBtn.innerText = "Resume";
                timerBtn.classList.replace('bg-amber-600', 'bg-slate-700');
            }
        }
    </script>
</body>
</html>
