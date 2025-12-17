<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <title>NIMTECH Blockchain Academy | Gombe State</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Official Blockchain and DLT Academic Programme under NIMTECH Gombe. Research, Policy, and Technical Education.">
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap');
    body { font-family: 'Inter', sans-serif; }
    .glass-effect { background: rgba(255, 255, 255, 0.95); backdrop-filter: blur(10px); }
    /* Keyframe for simple animation for the modal */
    @keyframes fade-in {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    @keyframes zoom-in {
      from { transform: scale(0.9); }
      to { transform: scale(1); }
    }
    .animate-in {
      animation-name: fade-in, zoom-in;
      animation-duration: 0.3s;
      animation-timing-function: ease-out;
    }
    /* Custom utility for link styling on hover */
    .link-citation:hover .source-uri {
        max-width: 500px; /* Expand on hover */
        opacity: 1;
    }
  </style>
</head>

<body class="bg-slate-50 text-slate-900 antialiased">

<!-- Mobile Menu Overlay -->
<div id="mobileMenu" class="fixed inset-0 bg-blue-900 z-[120] hidden flex flex-col p-8 text-white">
    <div class="flex justify-between items-center mb-16">
        <div class="flex items-center gap-3">
            <span class="bg-yellow-500 text-blue-900 px-2 py-1 rounded font-black text-xl italic">N</span>
            <div class="leading-none">
                <h1 class="font-extrabold text-lg tracking-tight">NIMTECH</h1>
                <p class="text-[10px] uppercase tracking-[0.2em] text-blue-300">Blockchain Academy</p>
            </div>
        </div>
        <button onclick="toggleMobileMenu()" class="text-3xl text-white hover:text-yellow-500 transition"><i class="fas fa-times"></i></button>
    </div>
    <nav class="flex flex-col space-y-8 text-2xl font-bold uppercase">
        <a href="#about" onclick="toggleMobileMenu()" class="hover:text-yellow-400 transition py-2 border-b border-white/10">Overview</a>
        <a href="#courses" onclick="toggleMobileMenu()" class="hover:text-yellow-400 transition py-2 border-b border-white/10">Curriculum</a>
        <a href="#policy-drafting" onclick="toggleMobileMenu()" class="hover:text-yellow-400 transition py-2 border-b border-white/10">Policy Lab ✨</a>
        <a href="#glossary" onclick="toggleMobileMenu()" class="hover:text-yellow-400 transition py-2 border-b border-white/10">Glossary ✨</a>
        <a href="#faculty" onclick="toggleMobileMenu()" class="hover:text-yellow-400 transition py-2 border-b border-white/10">Faculty</a>
        <button onclick="toggleLogin(); toggleMobileMenu();" class="mt-8 bg-yellow-500 text-blue-900 font-black py-4 rounded-xl hover:bg-white transition flex items-center justify-center shadow-lg">
            <i class="fas fa-fingerprint mr-3"></i> Student Portal
        </button>
    </nav>
</div>


<!-- Custom Message Modal (Replaces alert()) -->
<div id="messageModal" class="fixed inset-0 bg-slate-900/90 z-[110] hidden flex items-center justify-center p-4">
    <div class="bg-white w-full max-w-md rounded-3xl p-8 shadow-2xl relative animate-in fade-in zoom-in duration-300">
        <button onclick="closeMessageModal()" class="absolute top-6 right-6 text-slate-400 hover:text-red-500"><i class="fas fa-times"></i></button>
        <div class="text-center mb-6">
            <div id="messageIcon" class="inline-flex items-center justify-center w-16 h-16 bg-blue-50 text-blue-900 rounded-full mb-4">
                <i class="fas fa-info-circle text-2xl"></i>
            </div>
            <h2 id="messageTitle" class="text-2xl font-bold">Message Title</h2>
        </div>
        <p id="messageBody" class="text-sm text-slate-600 text-center mb-4"></p>
        <button onclick="closeMessageModal()" class="w-full bg-blue-900 text-white font-bold py-3 rounded-xl hover:shadow-lg transition-all active:scale-95">Close</button>
    </div>
</div>

<!-- Login Modal (From previous code) -->
<div id="loginModal" class="fixed inset-0 bg-slate-900/90 z-[100] hidden flex items-center justify-center p-4">
    <div class="bg-white w-full max-w-md rounded-3xl p-8 shadow-2xl relative animate-in fade-in zoom-in duration-300">
        <button onclick="toggleLogin()" class="absolute top-6 right-6 text-slate-400 hover:text-red-500"><i class="fas fa-times"></i></button>
        <div class="text-center mb-8">
            <div class="inline-flex items-center justify-center w-16 h-16 bg-blue-50 text-blue-900 rounded-full mb-4">
                <i class="fas fa-user-shield text-2xl"></i>
            </div>
            <h2 class="text-2xl font-bold">Secure Access</h2>
            <p class="text-sm text-slate-500">Authorized Personnel & Students Only</p>
        </div>
        <form onsubmit="event.preventDefault(); showCustomMessage('Login Unavailable', 'Login service temporarily undergoing maintenance. Please check back later.');" class="space-y-4">
            <input type="text" placeholder="Institutional ID" class="w-full border border-slate-200 rounded-xl p-4 outline-none focus:ring-2 focus:ring-blue-900 bg-slate-50" required>
            <input type="password" placeholder="Access Key" class="w-full border border-slate-200 rounded-xl p-4 outline-none focus:ring-2 focus:ring-blue-900 bg-slate-50" required>
            <button class="w-full bg-blue-900 text-white font-bold py-4 rounded-xl hover:shadow-lg transition-all active:scale-95">Authenticate</button>
        </form>
    </div>
</div>

<header class="bg-blue-900 text-white sticky top-0 z-50 shadow-xl border-b border-blue-800">
  <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
    <div class="flex items-center gap-3">
        <span class="bg-yellow-500 text-blue-900 px-2 py-1 rounded font-black text-xl italic">N</span>
        <div class="leading-none">
            <h1 class="font-extrabold text-lg tracking-tight">NIMTECH</h1>
            <p class="text-[10px] uppercase tracking-[0.2em] text-blue-300">Blockchain Academy</p>
        </div>
    </div>
    
    <nav class="hidden lg:flex items-center space-x-8 text-[11px] font-bold uppercase tracking-widest">
      <a href="#about" class="hover:text-yellow-400 transition">Overview</a>
      <a href="#courses" class="hover:text-yellow-400 transition">Curriculum</a>
      <a href="#policy-drafting" class="hover:text-yellow-400 transition">Policy Lab ✨</a>
      <a href="#glossary" class="hover:text-yellow-400 transition">Glossary ✨</a>
      <a href="#faculty" class="hover:text-yellow-400 transition">Faculty</a>
      <button onclick="toggleLogin()" class="bg-white/10 border border-white/20 px-6 py-2.5 rounded-full hover:bg-white hover:text-blue-900 transition flex items-center shadow-inner">
        <i class="fas fa-fingerprint mr-2"></i> Student Portal
      </button>
    </nav>

    <!-- Mobile Menu Button - Now functional -->
    <button class="lg:hidden text-2xl" onclick="toggleMobileMenu()"><i class="fas fa-bars"></i></button>
  </div>
</header>

<section class="relative bg-blue-900 text-white py-32 px-6 overflow-hidden border-b-8 border-yellow-500">
    <div class="absolute top-0 left-0 w-full h-full opacity-10 pointer-events-none">
        <svg width="100%" height="100%"><pattern id="grid" width="40" height="40" patternUnits="userSpaceOnUse"><path d="M 40 0 L 0 0 0 40" fill="none" stroke="white" stroke-width="1"/></pattern><rect width="100%" height="100%" fill="url(#grid)" /></svg>
    </div>
    <div class="relative max-w-5xl mx-auto text-center">
        <span class="inline-block bg-blue-800 text-yellow-400 px-4 py-1 rounded-full text-xs font-bold mb-6 border border-blue-700 uppercase tracking-widest">Official Academic Division</span>
        <h2 class="text-5xl md:text-7xl font-extrabold mb-8 tracking-tight">Pioneering <span class="text-transparent bg-clip-text bg-gradient-to-r from-yellow-400 to-white">Blockchain Literacy</span> in Nigeria</h2>
        <p class="text-xl md:text-2xl text-blue-100 mb-12 max-w-3xl mx-auto font-light leading-relaxed italic">"Transforming Nigeria's digital landscape through structured academic research and ethical governance."</p>
        <div class="flex flex-col sm:flex-row justify-center gap-6">
            <a href="#apply" class="bg-yellow-500 text-blue-900 px-12 py-5 rounded-2xl font-black text-lg hover:bg-white transition shadow-2xl uppercase tracking-wider">Start Application</a>
            <a href="#" onclick="showCustomMessage('Prospectus Generation', 'Prospectus PDF is generating... Please check back in 5 minutes.');" class="bg-blue-800/50 backdrop-blur text-white border border-blue-700 px-12 py-5 rounded-2xl font-bold text-lg hover:bg-blue-700 transition flex items-center justify-center">
                <i class="fas fa-cloud-download-alt mr-3"></i> Prospectus 2026
            </a>
        </div>
    </div>
</section>

<section id="about" class="py-24 px-6 bg-white border-b border-slate-100">
    <div class="max-w-7xl mx-auto grid md:grid-cols-3 gap-12">
        <div class="p-10 rounded-3xl bg-slate-50 border border-slate-100 hover:border-blue-200 transition">
            <div class="text-blue-900 text-4xl mb-6"><i class="fas fa-university"></i></div>
            <h3 class="text-xl font-bold mb-4">Academic Integrity</h3>
            <p class="text-slate-500 text-sm leading-relaxed">Our curriculum is built on peer-reviewed research and internationally recognized computer science standards.</p>
        </div>
        <div class="p-10 rounded-3xl bg-slate-50 border border-slate-100 hover:border-blue-200 transition">
            <div class="text-blue-900 text-4xl mb-6"><i class="fas fa-gavel"></i></div>
            <h3 class="text-xl font-bold mb-4">Regulatory Compliance</h3>
            <p class="text-slate-500 text-sm leading-relaxed">Strict adherence to the Nigeria National Blockchain Policy and CBN virtual asset guidelines.</p>
        </div>
        <div class="p-10 rounded-3xl bg-slate-50 border border-slate-100 hover:border-blue-200 transition">
            <div class="text-blue-900 text-4xl mb-6"><i class="fas fa-shield-alt"></i></div>
            <h3 class="text-xl font-bold mb-4">Non-Investment</h3>
            <p class="text-slate-500 text-sm leading-relaxed">A pure education model. We do not engage in trading, brokerage, or financial solicitation.</p>
            </div>
    </div>
</section>

<section id="courses" class="py-24 px-6">
    <div class="max-w-7xl mx-auto">
        <div class="flex items-center gap-4 mb-16">
            <h2 class="text-4xl font-black text-blue-900 uppercase">Curriculum</h2>
            <div class="h-[2px] bg-slate-200 flex-grow"></div>
        </div>
        <div class="grid lg:grid-cols-3 gap-8">
            <div class="bg-white p-2 rounded-[2rem] shadow-sm border border-slate-200 group hover:shadow-2xl transition-all duration-500">
                <div class="bg-slate-900 rounded-[1.8rem] p-8 text-white h-full flex flex-col">
                    <span class="text-yellow-400 font-bold text-[10px] tracking-[0.3em] uppercase mb-4">Module 01</span>
                    <h3 class="text-2xl font-bold mb-4 leading-tight">Blockchain Architecture & Nodes</h3>
                    <p class="text-slate-400 text-sm mb-8 flex-grow">Technical study of P2P networks, cryptography, and hash functions.</p>
                    <div class="border-t border-white/10 pt-6 mt-auto">
                        <span class="text-[10px] font-bold opacity-50 uppercase">Course Duration</span>
                        <p class="font-bold">12 Weeks Intensive</p>
                    </div>
            </div>
            </div>
            <div class="bg-white p-2 rounded-[2rem] shadow-sm border border-slate-200 group hover:shadow-2xl transition-all duration-500">
                <div class="bg-blue-900 rounded-[1.8rem] p-8 text-white h-full flex flex-col">
                    <span class="text-yellow-400 font-bold text-[10px] tracking-[0.3em] uppercase mb-4">Module 02</span>
                    <h3 class="text-2xl font-bold mb-4 leading-tight">Digital Policy & Frameworks</h3>
                    <p class="text-slate-200 text-sm mb-8 flex-grow">Analyzing West African regulatory hurdles and global web3 compliance.</p>
                    <div class="border-t border-white/10 pt-6 mt-auto">
                        <span class="text-[10px] font-bold opacity-50 uppercase">Course Duration</span>
                        <p class="font-bold">8 Weeks Policy Lab</p>
                    </div>
            </div>
            </div>
            <div class="bg-white p-2 rounded-[2rem] shadow-sm border border-slate-200 group hover:shadow-2xl transition-all duration-500">
                <div class="bg-slate-100 rounded-[1.8rem] p-8 text-blue-900 h-full flex flex-col">
                    <span class="text-blue-900 font-bold text-[10px] tracking-[0.3em] uppercase mb-4">Module 03</span>
                    <h3 class="text-2xl font-bold mb-4 leading-tight">Smart Contract Logic (Academic) </h3>
                    <p class="text-slate-500 text-sm mb-8 flex-grow">Mathematical simulation of logic-based execution without mainnet deployment.</p>
                    <div class="border-t border-blue-900/10 pt-6 mt-auto">
                        <span class="text-[10px] font-bold opacity-50 uppercase">Course Duration</span>
                        <p class="font-bold">10 Weeks Lab-Based</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- Policy Drafting Assistant (New LLM Feature) -->
<section id="policy-drafting" class="py-24 px-6 bg-white border-b border-slate-100">
    <div class="max-w-5xl mx-auto">
        <div class="flex items-center gap-4 mb-10">
            <h2 class="text-4xl font-black text-blue-900 uppercase">Policy Drafting Lab ✨</h2>
            <div class="h-[2px] bg-slate-300 flex-grow"></div>
        </div>
        <p class="text-slate-600 mb-8 max-w-2xl">Simulate academic policy creation. Describe a regulatory challenge, and our AI assistant will draft a concise, research-backed policy recommendation.</p>

        <div class="space-y-4">
            <textarea id="policyGoalInput" rows="4" placeholder="e.g., How to regulate decentralized finance (DeFi) protocols to prevent illicit funding and ensure consumer protection without stifling innovation?" class="w-full bg-slate-50 p-4 rounded-xl outline-none focus:ring-2 focus:ring-yellow-500 border border-slate-200 shadow-lg"></textarea>
            
            <button id="draftPolicyButton" onclick="handlePolicyDrafting()" class="w-full bg-yellow-500 text-blue-900 font-black py-4 rounded-xl hover:bg-blue-900 hover:text-white transition-all uppercase tracking-wider active:scale-95 flex items-center justify-center">
                <i class="fas fa-file-alt mr-2"></i> Draft Policy Suggestion
            </button>
        </div>
        
        <!-- Loading Indicator -->
        <div id="policyLoadingIndicator" class="hidden text-center py-8">
            <div class="animate-spin inline-block w-8 h-8 border-4 border-yellow-500 border-t-transparent rounded-full mb-2"></div>
            <p class="text-sm text-slate-500">Simulating Policy Framework...</p>
        </div>

        <!-- Output Area -->
        <div id="policyOutput" class="mt-8 bg-slate-50 p-8 rounded-2xl shadow-inner border border-yellow-300 min-h-[150px] relative">
            <h4 class="text-lg font-bold text-blue-900 mb-2 border-b border-slate-200 pb-2">Policy Recommendation:</h4>
            <p id="policyResultText" class="text-slate-700 italic">Policy recommendations will appear here after drafting. Focus on clarity and regulatory scope.</p>
        </div>
    </div>
</section>

<!-- Interactive Glossary Section (Powered by Gemini API) -->
<section id="glossary" class="py-24 px-6 bg-slate-100 border-b border-slate-200">
    <div class="max-w-5xl mx-auto">
        <div class="flex items-center gap-4 mb-10">
            <h2 class="text-4xl font-black text-blue-900 uppercase">Interactive Glossary ✨</h2>
            <div class="h-[2px] bg-slate-300 flex-grow"></div>
        </div>
        <p class="text-slate-600 mb-8 max-w-2xl">Use our academic assistant to get grounded, concise definitions of any DLT, Cryptography, or Digital Policy term, suitable for institutional research.</p>

        <!-- Stacks vertically on mobile due to flex-col -->
        <div class="flex flex-col sm:flex-row gap-4 mb-8">
            <input id="termInput" type="text" placeholder="e.g., Zero-Knowledge Proof, DeFi, DAO, Fiat Currency" class="w-full sm:w-3/4 bg-white p-4 rounded-xl outline-none focus:ring-2 focus:ring-yellow-500 border border-slate-200 shadow-lg" required>
            <button id="explainButton" onclick="handleExplainTerm()" class="w-full sm:w-1/4 bg-blue-900 text-white font-black py-4 rounded-xl hover:bg-yellow-500 hover:text-blue-900 transition-all uppercase tracking-wider active:scale-95 flex items-center justify-center">
                <i class="fas fa-magic mr-2"></i> Get Explanation
            </button>
        </div>
        
        <!-- Loading Indicator -->
        <div id="loadingIndicator" class="hidden text-center py-8">
            <div class="animate-spin inline-block w-8 h-8 border-4 border-blue-500 border-t-transparent rounded-full mb-2"></div>
            <p class="text-sm text-slate-500">Querying Academic DLT Expert...</p>
        </div>

        <!-- Output Area -->
        <div id="glossaryOutput" class="bg-white p-8 rounded-2xl shadow-xl border border-blue-200 min-h-[150px] relative">
            <h4 class="text-lg font-bold text-blue-900 mb-2 border-b border-slate-100 pb-2">Result:</h4>
            <p id="resultText" class="text-slate-700 italic">Enter a term above to get a grounded explanation.</p>
            <div id="resultSources" class="mt-4 pt-4 border-t border-slate-100 text-xs text-slate-500 hidden">
                <p class="font-bold mb-1">Sources:</p>
                <div id="sourcesList" class="space-y-1"></div>
            </div>
        </div>
    </div>
</section>

<section id="faculty" class="py-24 px-6 bg-blue-900 text-white">
    <div class="max-w-7xl mx-auto text-center">
        <h2 class="text-4xl font-black mb-16 uppercase tracking-widest">Institutional Leadership</h2>
        <div class="grid md:grid-cols-3 gap-12">
            <div class="group">
                <div class="w-32 h-32 mx-auto rounded-full bg-slate-800 mb-6 border-4 border-yellow-500 overflow-hidden grayscale group-hover:grayscale-0 transition duration-500">
                    <img src="https://placehold.co/128x128/1e293b/fff?text=Dr" onerror="this.onerror=null; this.src='https://ui-avatars.com/api/?name=Director&background=1e293b&color=fff';" class="w-full">
                </div>
                <h4 class="font-bold text-xl uppercase tracking-tighter">Academic Director</h4>
                <p class="text-blue-300 text-xs font-bold uppercase mt-2 tracking-widest leading-loose">Board of Studies</p>
            </div>
            <div class="group">
                <div class="w-32 h-32 mx-auto rounded-full bg-slate-800 mb-6 border-4 border-yellow-500 overflow-hidden grayscale group-hover:grayscale-0 transition duration-500">
                    <img src="https://placehold.co/128x128/1e293b/fff?text=Liaison" onerror="this.onerror=null; this.src='https://ui-avatars.com/api/?name=Compliance&background=1e293b&color=fff';" class="w-full">
                </div>
                <h4 class="font-bold text-xl uppercase tracking-tighter">Regulatory Liaison</h4>
                <p class="text-blue-300 text-xs font-bold uppercase mt-2 tracking-widest leading-loose">Policy Division</p>
            </div>
            <div class="group">
                <div class="w-32 h-32 mx-auto rounded-full bg-slate-800 mb-6 border-4 border-yellow-500 overflow-hidden grayscale group-hover:grayscale-0 transition duration-500">
                    <img src="https://placehold.co/128x128/1e293b/fff?text=Eng" onerror="this.onerror=null; this.src='https://ui-avatars.com/api/?name=Research&background=1e293b&color=fff';" class="w-full">
                </div>
                <h4 class="font-bold text-xl uppercase tracking-tighter">Lead Researcher</h4>
                <p class="text-blue-300 text-xs font-bold uppercase mt-2 tracking-widest leading-loose">Systems Engineering</p>
            </div>
        </div>
    </div>
</section>

<section id="apply" class="py-24 px-6">
    <div class="max-w-5xl mx-auto bg-white rounded-[3rem] shadow-2xl overflow-hidden flex flex-col lg:flex-row border border-slate-100">
        <div class="lg:w-1/3 bg-blue-950 p-12 text-white">
            <h2 class="text-3xl font-extrabold mb-6">Enrollment 2026</h2>
            <p class="text-slate-400 text-sm mb-8">Limited seats available for the academic session. All applicants undergo institutional vetting.</p>
            <ul class="space-y-4 text-xs font-bold uppercase tracking-widest">
                <li class="flex items-center"><i class="fas fa-check text-yellow-500 mr-3"></i> ID Verification</li>
                <li class="flex items-center"><i class="fas fa-check text-yellow-500 mr-3"></i> Academic Interview</li>
                <li class="flex items-center"><i class="fas fa-check text-yellow-500 mr-3"></i> Ethics Clearance</li>
            </ul>
        </div>
        <div class="lg:w-2/3 p-12">
            <form onsubmit="event.preventDefault(); showCustomMessage('Application Submission', 'Application received. We will contact your email shortly.', 'success');" class="grid md:grid-cols-2 gap-6">
                <div class="space-y-2">
                    <label class="text-[10px] font-bold text-slate-400 uppercase">First Name</label>
                    <input type="text" class="w-full bg-slate-50 p-4 rounded-xl outline-none focus:ring-2 focus:ring-blue-900 border border-slate-100" placeholder="John" required>
                </div>
                <div class="space-y-2">
                    <label class="text-[10px] font-bold text-slate-400 uppercase">Last Name</label>
                    <input type="text" class="w-full bg-slate-50 p-4 rounded-xl outline-none focus:ring-2 focus:ring-blue-900 border border-slate-100" placeholder="Doe" required>
                </div>
                <div class="md:col-span-2 space-y-2">
                    <label class="text-[10px] font-bold text-slate-400 uppercase">Email Address</label>
                    <input type="email" class="w-full bg-slate-50 p-4 rounded-xl outline-none focus:ring-2 focus:ring-blue-900 border border-slate-100" placeholder="j.doe@institution.edu.ng" required>
                </div>
                <div class="md:col-span-2">
                    <button class="w-full bg-blue-900 text-white font-black py-5 rounded-2xl hover:bg-yellow-500 hover:text-blue-900 transition-all uppercase tracking-widest shadow-xl">Complete Application</button>
                </div>
            </form>
        </div>
    </div>
</section>

<footer class="bg-slate-900 text-slate-500 py-16 px-6">
    <div class="max-w-7xl mx-auto text-center">
        <div class="flex justify-center gap-4 mb-8">
            <a href="#" class="w-12 h-12 bg-white/5 rounded-full flex items-center justify-center hover:bg-white/10 transition"><i class="fab fa-linkedin-in"></i></a>
            <a href="#" class="w-12 h-12 bg-white/5 rounded-full flex items-center justify-center hover:bg-white/10 transition"><i class="fab fa-twitter"></i></a>
        </div>
        <p class="text-[10px] font-bold uppercase tracking-[0.4em] mb-4">Nurain Institute of Management and Technology</p>
        <p class="text-xs max-w-lg mx-auto leading-relaxed">Gombe State, Nigeria. This academy is strictly an educational facility. We do not offer investment advice or crypto-financial brokerage services.</p>
        <div class="mt-8 pt-8 border-t border-white/5 text-[9px] uppercase tracking-widest">
            &copy; 2025 NIMTECH. All Rights Reserved.
        </div>
    </div>
</footer>

<script>
    // --- Mobile Menu Toggle ---
    function toggleMobileMenu() {
        const menu = document.getElementById('mobileMenu');
        menu.classList.toggle('hidden');
    }

    // --- Custom Modal Functions ---
    function showCustomMessage(title, message, type = 'info') {
        const modal = document.getElementById('messageModal');
        const iconDiv = document.getElementById('messageIcon');
        const icon = iconDiv.querySelector('i');

        // Reset icon classes
        icon.className = '';
        iconDiv.className = 'inline-flex items-center justify-center w-16 h-16 rounded-full mb-4';

        if (type === 'success') {
            icon.classList.add('fas', 'fa-check-circle', 'text-2xl');
            iconDiv.classList.add('bg-green-50', 'text-green-600');
        } else if (type === 'error') {
            icon.classList.add('fas', 'fa-exclamation-triangle', 'text-2xl');
            iconDiv.classList.add('bg-red-50', 'text-red-600');
        } else { // info/default
            icon.classList.add('fas', 'fa-info-circle', 'text-2xl');
            iconDiv.classList.add('bg-blue-50', 'text-blue-900');
        }

        document.getElementById('messageTitle').textContent = title;
        document.getElementById('messageBody').textContent = message;
        modal.classList.remove('hidden');
    }

    function closeMessageModal() {
        document.getElementById('messageModal').classList.add('hidden');
    }

    // --- Login Toggle ---
    function toggleLogin() {
        const modal = document.getElementById('loginModal');
        modal.classList.toggle('hidden');
    }

    // --- Gemini API Setup ---
    const apiKey = ""; // API Key will be provided by the runtime environment
    const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;

    // Simple delay function for exponential backoff
    const delay = (ms) => new Promise(resolve => setTimeout(resolve, ms));

    async function fetchWithBackoff(url, options, maxRetries = 3) {
        for (let i = 0; i < maxRetries; i++) {
            try {
                const response = await fetch(url, options);
                if (response.status === 429 && i < maxRetries - 1) {
                    // console.log(`Rate limit hit, retrying in ${Math.pow(2, i)}s...`);
                    await delay(Math.pow(2, i) * 1000 + Math.random() * 1000); // Exponential backoff
                    continue;
                }
                // Check for non-OK status right away
                if (!response.ok) {
                    // Attempt to read the response body for more detail, if available
                    const errorBody = await response.text(); 
                    const errorDetail = errorBody ? `: ${errorBody.substring(0, 100)}...` : '.';
                    throw new Error(`HTTP Error Status ${response.status}${errorDetail}`);
                }
                return response;
            } catch (error) {
                if (i === maxRetries - 1) throw error;
            }
        }
    }

    // --- Gemini API Integration for Policy Drafting (New Feature) ---
    const policyGoalInput = document.getElementById('policyGoalInput');
    const draftPolicyButton = document.getElementById('draftPolicyButton');
    const policyLoadingIndicator = document.getElementById('policyLoadingIndicator');
    const policyResultText = document.getElementById('policyResultText');

    async function handlePolicyDrafting() {
        const goal = policyGoalInput.value.trim();
        if (!goal) {
            showCustomMessage('Input Required', 'Please describe a regulatory challenge or policy objective (e.g., "Preventing NFT fraud") to draft a suggestion.', 'error');
            return;
        }

        // 1. UI: Set Loading State
        draftPolicyButton.disabled = true;
        draftPolicyButton.innerHTML = '<i class="fas fa-sync-alt animate-spin mr-2"></i> Drafting Policy...';
        policyLoadingIndicator.classList.remove('hidden');
        policyResultText.innerHTML = 'Analyzing regulatory goal and drafting framework...';
        
        try {
            const systemPrompt = "You are a senior DLT Policy Analyst specializing in Nigerian and West African regulatory frameworks. Your task is to analyze the user's regulatory goal and provide a structured, concise, and academic policy recommendation. The output must be formatted as a single, numbered list of 3 actionable, high-level regulatory points. Do not include any introductory or concluding text, only the numbered points.";
            const userQuery = `Draft policy recommendations for the following regulatory goal: ${goal}`;

            const payload = {
                contents: [{ parts: [{ text: userQuery }] }],
                // No grounding needed for creative/structured drafting
                systemInstruction: { parts: [{ text: systemPrompt }] },
            };

            const response = await fetchWithBackoff(apiUrl, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(payload)
            });

            const result = await response.json();
            const candidate = result.candidates?.[0];

            let policyDraft = "Failed to generate policy draft. Check API response or system prompt.";

            if (candidate && candidate.content?.parts?.[0]?.text) {
                // Convert Markdown list (e.g., 1., 2., 3.) to HTML list for better formatting
                let markdownText = candidate.content.parts[0].text;
                let htmlList = markdownText.split('\n')
                    .map(line => line.trim())
                    .filter(line => line.match(/^\d+\.\s/))
                    .map(line => line.replace(/^\d+\.\s/, '<li>') + '</li>')
                    .join('');

                policyDraft = `<ol class="list-decimal list-inside space-y-3 pl-4 text-left">${htmlList}</ol>`;

            } else if (result.error && result.error.message) {
                 policyDraft = `<span class="text-red-600 font-bold">API Error:</span> ${result.error.message}.`;
            }

            // 2. UI: Update Result State
            policyResultText.innerHTML = policyDraft;

        } catch (error) {
            console.error('Gemini Policy Drafting Failure:', error);
            
            let userFeedback = "An unknown network error occurred. Check your network status.";
            if (error.message.includes("HTTP Error Status")) {
                 userFeedback = `Service Error: ${error.message.split('.')[0]}.`;
            } else if (error.message.includes("Failed to fetch")) {
                 userFeedback = "Network connection failed or API endpoint unreachable.";
            }

            policyResultText.innerHTML = `<span class="text-red-600 font-bold">Drafting Error:</span> ${userFeedback} <span class="text-sm italic block mt-1">Please check your browser's console (F12) for technical details.</span>`;
        } finally {
            // 3. UI: Reset Button/Loading State
            draftPolicyButton.disabled = false;
            draftPolicyButton.innerHTML = '<i class="fas fa-file-alt mr-2"></i> Draft Policy Suggestion';
            policyLoadingIndicator.classList.add('hidden');
        }
    }


    // --- Existing Gemini API Integration for Glossary ---
    const termInput = document.getElementById('termInput');
    const loadingIndicator = document.getElementById('loadingIndicator');
    const explainButton = document.getElementById('explainButton');
    const resultText = document.getElementById('resultText');
    const resultSources = document.getElementById('resultSources');
    const sourcesList = document.getElementById('sourcesList');

    async function handleExplainTerm() {
        const term = termInput.value.trim();
        if (!term) {
            showCustomMessage('Input Required', 'Please enter a technical term (e.g., "Smart Contract" or "Merkle Tree") to receive an explanation.');
            return;
        }

        // 1. UI: Set Loading State
        explainButton.disabled = true;
        explainButton.innerHTML = '<i class="fas fa-sync-alt animate-spin mr-2"></i> Generating...';
        loadingIndicator.classList.remove('hidden');
        resultText.innerHTML = 'Analyzing term...';
        resultSources.classList.add('hidden');
        sourcesList.innerHTML = '';
        
        try {
            const systemPrompt = "You are the Academic DLT Expert for NIMTECH Blockchain Academy. Provide a concise (max 3 sentences), highly authoritative, and easy-to-understand definition of the following blockchain or computer science term, suitable for institutional research.";
            const userQuery = `Define the term: ${term}`;

            const payload = {
                contents: [{ parts: [{ text: userQuery }] }],
                // Use Google Search for authoritative, real-time grounding
                tools: [{ "google_search": {} }], 
                systemInstruction: { parts: [{ text: systemPrompt }] },
            };

            const response = await fetchWithBackoff(apiUrl, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(payload)
            });

            const result = await response.json();
            const candidate = result.candidates?.[0];

            let explanationText = "Could not generate a clear explanation. The model may have failed to produce content or the response structure was unexpected.";
            let sources = [];

            if (candidate && candidate.content?.parts?.[0]?.text) {
                explanationText = candidate.content.parts[0].text;

                const groundingMetadata = candidate.groundingMetadata;
                if (groundingMetadata && groundingMetadata.groundingAttributions) {
                    sources = groundingMetadata.groundingAttributions
                        .map(attribution => ({
                            uri: attribution.web?.uri,
                            title: attribution.web?.title,
                        }))
                        .filter(source => source.uri && source.title);
                }
            } else if (result.error && result.error.message) {
                 // Explicit error from the API body 
                 explanationText = `API Error: ${result.error.message}. This usually indicates a configuration issue.`;
            }

            // 2. UI: Update Result State
            resultText.textContent = explanationText;

            if (sources.length > 0) {
                sourcesList.innerHTML = sources.map((source, index) => `
                    <div class="flex items-center">
                        <span class="font-semibold text-blue-900 mr-2">(${index + 1})</span>
                        <a href="${source.uri}" target="_blank" rel="noopener noreferrer" class="link-citation text-blue-600 hover:text-blue-800 transition truncate flex-grow">
                            <span class="source-title font-medium">${source.title}</span>
                            <span class="source-uri text-slate-400 ml-2 italic text-xs transition-all duration-300 max-w-0 overflow-hidden inline-block align-middle">${new URL(source.uri).hostname}</span>
                        </a>
                    </div>
                `).join('');
                resultSources.classList.remove('hidden');
            } else {
                sourcesList.innerHTML = '<p>No grounding sources found.</p>';
            }

        } catch (error) {
            console.error('Gemini API Integration Failure:', error);
            
            // Provide specific user feedback based on the error
            let userFeedback = "An unknown network error occurred. Check your network status.";
            if (error.message.includes("429")) {
                 userFeedback = "Rate limit exceeded. Please wait a moment before trying again.";
            } else if (error.message.includes("HTTP Error Status")) {
                 userFeedback = `Service Error: ${error.message.split('.')[0]}.`;
            } else if (error.message.includes("Failed to fetch")) {
                 userFeedback = "Network connection failed or API endpoint unreachable. Check your network.";
            } else if (error.message.includes("configuration issue")) {
                 userFeedback = error.message; // Use the message from the explicit API error check
            }

            resultText.innerHTML = `<span class="text-red-600 font-bold">Error:</span> ${userFeedback} <span class="text-sm italic block mt-1">Please check your browser's console (F12) for technical details.</span>`;
            resultSources.classList.add('hidden');
        } finally {
            // 3. UI: Reset Button/Loading State
            explainButton.disabled = false;
            explainButton.innerHTML = '<i class="fas fa-magic mr-2"></i> Get Explanation';
            loadingIndicator.classList.add('hidden');
        }
    }

    // Allow pressing Enter key in the input field
    termInput.addEventListener('keypress', function(e) {
        if (e.key === 'Enter') {
            e.preventDefault();
            handleExplainTerm();
        }
    });
</script>

</body>
</html>