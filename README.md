<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SkillOrbit • Cosmic Skill Matching</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="styles.css">
</head>
<body class="tailwind-ready text-slate-100 min-h-screen overflow-x-hidden">
    
    <!-- Navbar -->
    <nav class="bg-slate-950/80 backdrop-blur-lg border-b border-slate-800 sticky top-0 z-50">
        <div class="max-w-screen-2xl mx-auto px-8 py-5 flex items-center justify-between">
            <div class="flex items-center gap-x-3">
                <div class="w-9 h-9 bg-gradient-to-br from-amber-400 to-yellow-300 rounded-2xl flex items-center justify-center text-2xl">☀️</div>
                <h1 class="logo-font text-3xl tracking-[-1px]">SkillOrbit</h1>
            </div>
            
            <div class="flex items-center gap-x-8 text-sm font-medium">
                <a href="#" onclick="navigateTo('home')" class="nav-link flex items-center gap-x-1 hover:text-amber-400" id="nav-home">🌌 Home</a>
                <a href="#" onclick="navigateTo('offer')" class="nav-link flex items-center gap-x-1 hover:text-amber-400" id="nav-offer">🚀 Offer Skill</a>
                <a href="#" onclick="navigateTo('request')" class="nav-link flex items-center gap-x-1 hover:text-amber-400" id="nav-request">🌠 Request Skill</a>
                <a href="#" onclick="navigateTo('matches')" class="nav-link flex items-center gap-x-1 hover:text-amber-400" id="nav-matches">🔭 AI Matches</a>
                
                <div class="flex items-center gap-x-3 pl-6 border-l border-slate-700">
                    <div class="w-8 h-8 bg-emerald-400 rounded-2xl flex items-center justify-center text-white font-bold">RJ</div>
                    <div>
                        <p class="text-sm font-semibold">Ravi J.</p>
                        <p class="text-xs text-emerald-400">Hyderabad • Level 12</p>
                    </div>
                </div>
                
                <button onclick="toggleSound()" id="sound-btn" class="w-9 h-9 bg-slate-800 hover:bg-slate-700 rounded-2xl text-xl flex items-center justify-center">🔊</button>
            </div>
        </div>
    </nav>

    <!-- HOME SECTION -->
    <section id="home-section" class="section">
        <div class="max-w-screen-2xl mx-auto px-8 pt-12">
            <div class="text-center mb-12">
                <h1 class="text-7xl font-semibold logo-font tracking-[-2px] leading-none">
                    Your skills.<br>
                    <span class="bg-gradient-to-r from-amber-400 to-yellow-300 bg-clip-text text-transparent">Orbiting the future.</span>
                </h1>
                <p class="mt-4 text-xl text-slate-400">Offer • Request • AI-match in a living solar system</p>
                
                <div class="flex justify-center gap-x-6 mt-10">
                    <button onclick="runAIMatch()" 
                            class="px-10 py-5 bg-gradient-to-r from-amber-400 to-yellow-300 text-slate-950 font-semibold text-xl rounded-3xl flex items-center gap-x-3 hover:scale-105 shadow-2xl">
                        Launch AI Cosmic Match <span class="text-3xl">🔭</span>
                    </button>
                    <button onclick="showHowItWorks()" 
                            class="px-8 py-5 border border-slate-400/30 hover:border-amber-400 rounded-3xl text-lg">
                        How Solar System Works →
                    </button>
                </div>
            </div>

            <!-- Solar System -->
            <div class="flex justify-center mb-16">
                <div id="solar-system" class="relative w-[620px] h-[620px]">
                    <!-- Sun -->
                    <div id="sun" class="sun" onclick="showSunModal()">
                        🤖
                    </div>
                    
                    <!-- Orbits & Planets -->
                    <div class="orbit orbit-1" style="animation-duration: 18s;">
                        <div class="planet planet-1" onclick="selectPlanet(this)">🌍</div>
                    </div>
                    <div class="orbit orbit-2" style="animation-duration: 28s;">
                        <div class="planet planet-2" onclick="selectPlanet(this)">🪐</div>
                    </div>
                    <div class="orbit orbit-3" style="animation-duration: 42s;">
                        <div class="planet planet-3" onclick="selectPlanet(this)">🌎</div>
                    </div>
                    <div class="orbit orbit-4" style="animation-duration: 55s;">
                        <div class="planet planet-4" onclick="selectPlanet(this)">🌕</div>
                    </div>
                    <div class="orbit orbit-5" style="animation-duration: 72s;">
                        <div class="planet planet-5" onclick="selectPlanet(this)">🪐</div>
                    </div>
                    
                    <svg id="connections" class="absolute top-0 left-0 w-full h-full pointer-events-none"></svg>
                </div>
            </div>
            
            <p class="text-center text-slate-400 text-sm">248 students orbiting right now • Hyderabad</p>
        </div>
    </section>

    <!-- OFFER SECTION -->
    <section id="offer-section" class="section hidden">
        <div class="max-w-2xl mx-auto px-8 pt-12">
            <h2 class="text-5xl font-semibold logo-font">Offer a Skill</h2>
            <p class="text-slate-400 mt-2 mb-10">Share your knowledge. Become someone’s gravitational center.</p>
            
            <div class="bg-slate-900/70 border border-slate-700 rounded-3xl p-10">
                <div class="grid grid-cols-2 gap-6">
                    <div>
                        <label class="block text-sm uppercase tracking-widest mb-2">Skill</label>
                        <select id="offer-skill" class="w-full bg-slate-800 border border-slate-600 rounded-2xl px-6 py-4 text-lg">
                            <option>Coding / Programming</option>
                            <option>UI/UX Design</option>
                            <option>Video Editing</option>
                            <option>Graphic Design</option>
                            <option>Music Production</option>
                            <option>Data Science</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-sm uppercase tracking-widest mb-2">Level</label>
                        <div class="flex gap-2">
                            <button onclick="setOfferLevel(this)" class="level-btn flex-1 py-4 rounded-2xl bg-slate-800">🌱 Beginner</button>
                            <button onclick="setOfferLevel(this)" class="level-btn flex-1 py-4 rounded-2xl bg-slate-800">⭐ Intermediate</button>
                            <button onclick="setOfferLevel(this)" class="level-btn flex-1 py-4 rounded-2xl bg-slate-800">🔥 Expert</button>
                        </div>
                    </div>
                </div>
                
                <textarea id="offer-desc" class="mt-8 w-full h-40 bg-slate-800 border border-slate-600 rounded-3xl px-6 py-6" placeholder="Describe what you can teach..."></textarea>
                
                <button onclick="submitOffer()" class="mt-10 w-full py-6 bg-gradient-to-r from-amber-400 to-yellow-300 text-slate-950 font-semibold text-xl rounded-3xl">
                    LAUNCH INTO ORBIT 🚀
                </button>
            </div>
        </div>
    </section>

    <!-- REQUEST SECTION -->
    <section id="request-section" class="section hidden">
        <div class="max-w-2xl mx-auto px-8 pt-12">
            <h2 class="text-5xl font-semibold logo-font">Request a Skill</h2>
            <p class="text-slate-400 mt-2 mb-10">Tell the universe what you want to learn.</p>
            
            <div class="bg-slate-900/70 border border-slate-700 rounded-3xl p-10">
                <select id="request-skill" class="w-full bg-slate-800 border border-slate-600 rounded-2xl px-6 py-4 text-lg">
                    <option>Coding / Programming</option>
                    <option>UI/UX Design</option>
                    <option>Video Editing</option>
                    <option>Music Production</option>
                    <option>Data Science</option>
                </select>
                
                <textarea id="request-desc" class="mt-8 w-full h-40 bg-slate-800 border border-slate-600 rounded-3xl px-6 py-6" placeholder="Why do you want to learn this?"></textarea>
                
                <button onclick="submitRequest()" class="mt-10 w-full py-6 bg-gradient-to-r from-cyan-400 to-blue-400 text-white font-semibold text-xl rounded-3xl">
                    SEND INTO THE COSMOS 🌠
                </button>
            </div>
        </div>
    </section>

    <!-- MATCHES SECTION -->
    <section id="matches-section" class="section hidden">
        <div class="max-w-screen-2xl mx-auto px-8 pt-12">
            <div class="flex justify-between items-end mb-10">
                <h2 class="text-5xl font-semibold logo-font">Your AI Matches</h2>
                <button onclick="runAIMatch()" class="px-8 py-4 bg-white text-slate-950 font-semibold rounded-3xl flex items-center gap-x-2">
                    Refresh Matches <span class="text-xl">🔄</span>
                </button>
            </div>
            
            <div id="matches-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Populated by JS -->
            </div>
        </div>
    </section>

    <!-- Modals -->
    <div id="planet-modal" class="hidden fixed inset-0 bg-black/80 flex items-center justify-center z-50">
        <div class="modal bg-slate-900 border border-amber-400/30 rounded-3xl p-8 max-w-md w-full">
            <h3 id="modal-title" class="text-3xl font-semibold mb-4"></h3>
            <p id="modal-desc" class="text-slate-300"></p>
            <button onclick="closeModal()" class="mt-8 w-full py-4 bg-slate-800 hover:bg-slate-700 rounded-2xl">Close</button>
        </div>
    </div>

    <div id="sun-modal" class="hidden fixed inset-0 bg-black/80 flex items-center justify-center z-50">
        <div class="modal bg-slate-900 border border-amber-400/30 rounded-3xl p-8 max-w-lg w-full text-center">
            <h2 class="text-4xl mb-4">🤖 AI Match Engine</h2>
            <p class="text-slate-300">The core of SkillOrbit. It analyzes all offers and requests to find perfect gravitational matches.</p>
            <button onclick="closeSunModal()" class="mt-8 px-10 py-4 bg-gradient-to-r from-amber-400 to-yellow-300 text-slate-950 font-semibold rounded-3xl">Got it</button>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>