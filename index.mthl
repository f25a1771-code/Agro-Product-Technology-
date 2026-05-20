<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculus in Agro-Product Tech: Enzymatic Hydrolysis</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body class="bg-gray-50 text-gray-800 font-sans min-h-screen pb-12">

    <header class="bg-emerald-700 text-white py-8 px-4 shadow-md text-center">
        <h1 class="text-3xl font-bold tracking-tight">Derivatives in Agro-Product Technology</h1>
        <p class="text-emerald-100 mt-2 text-lg">Optimizing Sugar Yield from Malaysian Oil Palm Biomass via Enzymatic Hydrolysis</p>
    </header>

    <main class="max-w-5xl mx-auto px-4 mt-8 grid grid-cols-1 md:grid-cols-3 gap-8">
        
        <div class="md:col-span-1 space-y-6">
            <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                <h2 class="text-xl font-bold text-emerald-800 mb-3">The Bioscience Problem</h2>
                <p class="text-sm text-gray-600 leading-relaxed mb-4">
                    In Malaysia, utilizing Oil Palm Empty Fruit Bunch (EFB) biomass is a massive industry priority. 
                    During <strong>enzymatic hydrolysis</strong>, cellulase enzymes break down EFB cellulose into reducing sugars (glucose). 
                    As substrate limits are reached and enzyme inhibition occurs, the rate of sugar production slows down.
                </p>
                <div class="text-xs text-gray-500 bg-gray-50 p-2 rounded border border-gray-200">
                    <strong>Data Reference Scenario:</strong> Inspired by parameters typical in MPOB (Malaysian Palm Oil Board) and local bioreactor optimization studies for EFB bioconversion.
                </div>
            </div>

            <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                <h2 class="text-xl font-bold text-emerald-800 mb-3">The Mathematical Model</h2>
                <p class="text-xs text-gray-500 mb-4">Let $x$ be the time in hours ($0 \le x \le 24$), and $f(x)$ be the reducing sugar concentration in g/L.</p>
                
                <div class="bg-emerald-50 p-3 rounded-lg mb-4 text-center">
                    <span class="block text-xs font-semibold text-emerald-700 uppercase tracking-wider">Sugar Concentration Function $f(x)$</span>
                    <span class="text-base font-mono text-emerald-900">$f(x) = -0.05x^2 + 2.4x + 2$</span>
                </div>

                <div class="bg-amber-50 p-3 rounded-lg text-center">
                    <span class="block text-xs font-semibold text-amber-700 uppercase tracking-wider">Rate of Change Function $f'(x)$</span>
                    <span class="text-base font-mono text-amber-900">$f'(x) = -0.1x + 2.4$</span>
                    <p class="text-[11px] text-amber-800 mt-1 italic">Calculated using the Power Rule: $\frac{d}{dx}[x^n] = nx^{n-1}$</p>
                </div>
            </div>
        </div>

        <div class="md:col-span-2 space-y-6">
            <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                <h2 class="text-xl font-bold text-gray-800 mb-1">Hydrolysis Progression Curve</h2>
                <p class="text-xs text-gray-500 mb-4">Instruction: Click on any data point on the chart line to analyze the derivative at that hour.</p>
                
                <div class="relative h-80 w-full">
                    <canvas id="hydrolysisChart"></canvas>
                </div>
            </div>

            <div id="interactivePanel" class="bg-slate-800 text-white p-6 rounded-xl shadow-md transition-all duration-300 transform scale-100">
                <div id="placeholderText" class="text-center py-4 text-slate-400 text-sm">
                    ✨ Click a data point on the graph above to run derivative analysis at that specific processing hour.
                </div>
                <div id="analysisResult" class="hidden space-y-4">
                    <div class="flex justify-between items-center border-b border-slate-700 pb-2">
                        <h3 class="text-lg font-bold text-amber-400">Calculus Analysis at Hour <span id="outHour">0</span></h3>
                        <span class="bg-emerald-600 text-xs px-2 py-1 rounded font-semibold">f'(x) Active</span>
                    </div>
                    <div class="grid grid-cols-2 gap-4">
                        <div class="bg-slate-700/50 p-3 rounded">
                            <span class="block text-xs text-slate-400">Sugar Concentration $f(x)$</span>
                            <span class="text-xl font-mono font-bold text-white"><span id="outConc">0.00</span> g/L</span>
                        </div>
                        <div class="bg-slate-700/50 p-3 rounded border border-amber-500/30">
                            <span class="block text-xs text-amber-400 font-medium">Instantaneous Rate $f'(x)$</span>
                            <span class="text-xl font-mono font-bold text-amber-400"><span id="outRate">0.00</span> g/L/hr</span>
                        </div>
                    </div>
                    <div class="bg-slate-900 p-3 rounded text-sm border-l-4 border-emerald-500">
                        <span class="block text-xs font-bold uppercase tracking-wider text-emerald-400 mb-1">Layman Explanation</span>
                        <p id="outExplain" class="text-slate-300 leading-relaxed"></p>
                    </div>
                </div>
            </div>
        </div>

    </main>

    <script>
        // Generate dataset based on f(x) = -0.05x^2 + 2.4x + 2
        const labels = [];
        const dataConc = [];
        
        for (let x = 0; x <= 24; x++) {
            labels.push(x);
            let fx = -0.05 * Math.pow(x, 2) + (2.4 * x) + 2;
