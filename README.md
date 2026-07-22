# mifa-s-corner <!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mifa's Corner - Tell Me What You Think</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Google Fonts: Quicksand, Caveat, Fredoka, Plus Jakarta Sans -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Caveat:wght@400;600;700&family=Fredoka:wght@400;500;600&family=Plus+Jakarta+Sans:wght@400;500;600;700&family=Quicksand:wght@400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <!-- Canvas Confetti for Celebration -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'cozy-bg': '#F6F1EA',
                        'cozy-card': '#FAF6F0',
                        'cozy-inner': '#FFFDF9',
                        'cozy-text': '#4A3B32',
                        'cozy-muted': '#7C6A5E',
                        'cozy-terracotta': '#9C6153',
                        'cozy-terracotta-hover': '#865043',
                        'cozy-pill': '#EAD7C5',
                        'cozy-border': '#E8DBD0',
                        'cozy-note': '#F3ECE1'
                    },
                    fontFamily: {
                        'hand': ['Caveat', 'cursive'],
                        'title': ['Fredoka', 'sans-serif'],
                        'body': ['Quicksand', 'sans-serif'],
                        'sans': ['Plus Jakarta Sans', 'sans-serif']
                    },
                    boxShadow: {
                        'cozy': '0 12px 35px -8px rgba(110, 85, 68, 0.08), 0 4px 12px -2px rgba(110, 85, 68, 0.04)',
                        'floating': '0 20px 40px -10px rgba(90, 65, 50, 0.12)'
                    }
                }
            }
        }
    </script>

    <style>
        body {
            background-color: #F6F1EA;
            color: #4A3B32;
            font-family: 'Quicksand', sans-serif;
            background-image: 
                radial-gradient(#e5d8cb 1px, transparent 1px), 
                radial-gradient(#e5d8cb 1px, #F6F1EA 1px);
            background-size: 40px 40px;
            background-position: 0 0, 20px 20px;
        }

        .font-handwriting {
            font-family: 'Caveat', cursive;
        }

        .font-heading {
            font-family: 'Fredoka', cursive;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #F6F1EA;
        }
        ::-webkit-scrollbar-thumb {
            background: #D9C9BC;
            border-radius: 99px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #BFAEA0;
        }

        /* Floating elements animation */
        @keyframes floatSlow {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-8px) rotate(2deg); }
        }
        .animate-float {
            animation: floatSlow 6s ease-in-out infinite;
        }
        .animate-float-delayed {
            animation: floatSlow 7s ease-in-out 2s infinite;
        }

        .sticky-note-shadow {
            box-shadow: 4px 4px 12px rgba(74, 59, 50, 0.08), 1px 1px 3px rgba(0,0,0,0.05);
        }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between relative overflow-x-hidden selection:bg-cozy-pill selection:text-cozy-text">

    <!-- Top Admin Toggle Button -->
    <div class="fixed top-4 right-4 z-40">
        <button id="adminToggleBtn" onclick="openAdminModal()" class="flex items-center gap-2 px-4 py-2 rounded-full bg-white/80 hover:bg-white backdrop-blur-md border border-cozy-border text-cozy-muted text-xs font-semibold shadow-sm transition-all duration-300 hover:text-cozy-terracotta hover:shadow-md">
            <i class="fa-solid fa-lock text-cozy-terracotta"></i>
            <span id="adminBtnText">Admin Area</span>
        </button>
    </div>

    <!-- Background Decorative SVG Elements -->
    <div class="absolute inset-0 pointer-events-none overflow-hidden z-0">
        <!-- Top Left Star Doodle -->
        <svg class="absolute top-12 left-[8%] w-10 h-10 text-cozy-muted/30 animate-float" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z" />
        </svg>

        <!-- Top Big Heart Doodle -->
        <svg class="absolute top-6 left-1/2 -translate-x-1/2 w-12 h-12 text-cozy-terracotta/40 animate-float-delayed" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1" d="M19 4l1 2m2-1l-2 1" />
        </svg>

        <!-- Top Right Small Heart -->
        <svg class="absolute top-16 right-[12%] w-7 h-7 text-cozy-terracotta/30 animate-float" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
        </svg>

        <!-- Paper Plane Top Right -->
        <svg class="absolute top-28 right-[6%] w-14 h-14 text-cozy-muted/20 animate-float-delayed -rotate-12" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8" />
        </svg>
    </div>

    <main class="container mx-auto px-4 py-10 md:py-14 max-w-3xl flex-1 flex flex-col justify-center relative z-10">

        <!-- Main Header Section -->
        <header class="text-center mb-8 relative">
            <h1 class="font-heading text-5xl md:text-6xl font-bold tracking-tight text-cozy-text mb-3">
                Mifa’s Corner
            </h1>

            <!-- Pill Badge -->
            <div class="inline-block px-5 py-1.5 rounded-full bg-cozy-pill text-cozy-text font-medium text-sm md:text-base tracking-wide shadow-sm mb-5">
                Tell Me What You Think
            </div>

            <!-- Header Description -->
            <p class="text-cozy-muted font-medium text-sm md:text-base max-w-md mx-auto leading-relaxed">
                Kritik, saran, dan ide untuk akun ku.<br>
                Terimakasih banyak telah menyempatkan waktu untuk menyumbang ide disini <span class="text-cozy-terracotta">♡</span>
            </p>
        </header>

        <!-- Content Area with Sticky Note Aesthetics -->
        <div class="relative">
            
            <!-- Side Sticky Note (Desktop View) -->
            <div class="hidden lg:block absolute -right-24 top-12 w-32 bg-[#F3ECE1] p-4 rounded-lg sticky-note-shadow rotate-6 border border-[#E5DACB] text-center pointer-events-none">
                <div class="w-3 h-3 rounded-full bg-[#D9C3B0] mx-auto -mt-2 mb-2"></div>
                <p class="font-handwriting text-2xl text-cozy-text font-bold leading-tight">your opinion matters</p>
                <p class="text-cozy-terracotta text-xl">♡</p>
            </div>

            <!-- Left Vase / Aesthetic Card Decoration (Decorative text) -->
            <div class="hidden lg:block absolute -left-28 bottom-16 w-32 bg-[#F3ECE1] p-3 rounded-lg sticky-note-shadow -rotate-6 border border-[#E5DACB] text-center pointer-events-none">
                <p class="font-handwriting text-xl text-cozy-muted">thank you</p>
                <p class="text-cozy-terracotta text-lg">♡</p>
            </div>

            <!-- Central Feedback Card -->
            <div class="bg-cozy-card rounded-3xl p-6 md:p-10 shadow-cozy border border-cozy-border relative backdrop-blur-sm">
                
                <!-- Inner Title Section inside card -->
                <div class="flex items-center gap-3 mb-5">
                    <div class="w-10 h-10 rounded-2xl bg-cozy-terracotta/15 flex items-center justify-center text-cozy-terracotta shrink-0">
                        <i class="fa-solid fa-heart text-base"></i>
                    </div>
                    <h2 class="text-cozy-text font-semibold text-base md:text-lg">
                        Tuliskan kritik, saran, atau ide kamu di sini ya! <span class="text-cozy-terracotta">♡</span>
                    </h2>
                </div>

                <form id="feedbackForm" onsubmit="handleFeedbackSubmit(event)" class="space-y-6">
                    
                    <!-- Textarea Container -->
                    <div class="relative">
                        <textarea 
                            id="feedbackContent" 
                            name="feedback" 
                            rows="7" 
                            required
                            maxlength="1000"
                            placeholder="Tulis apa pun yang ingin kamu sampaikan...&#10;Semua masukan sangat berarti untuk aku ♡"
                            class="w-full rounded-2xl bg-cozy-inner border border-cozy-border p-4 md:p-5 text-cozy-text placeholder:text-cozy-muted/60 focus:outline-none focus:border-cozy-terracotta focus:ring-2 focus:ring-cozy-terracotta/20 transition-all duration-200 resize-none text-sm md:text-base leading-relaxed"
                            oninput="updateCharCount()"></textarea>
                        
                        <!-- Character Counter -->
                        <div class="absolute bottom-3 right-4 text-xs text-cozy-muted/60 select-none">
                            <span id="charCount">0</span>/1000
                        </div>
                    </div>

                    <!-- Decorative Dashed Separator with Heart -->
                    <div class="flex items-center justify-center gap-3 my-4">
                        <div class="h-px bg-cozy-border flex-1 border-dashed border-b border-cozy-muted/30"></div>
                        <i class="fa-solid fa-heart text-cozy-terracotta/40 text-xs"></i>
                        <div class="h-px bg-cozy-border flex-1 border-dashed border-b border-cozy-muted/30"></div>
                    </div>

                    <!-- Submit Button -->
                    <div class="text-center pt-1">
                        <button 
                            type="submit" 
                            id="submitBtn" 
                            class="inline-flex items-center justify-center gap-2 px-8 py-3.5 rounded-full bg-cozy-terracotta hover:bg-cozy-terracotta-hover text-white font-medium text-base shadow-md hover:shadow-lg hover:-translate-y-0.5 active:translate-y-0 transition-all duration-200 w-full sm:w-auto min-w-[220px]">
                            <span id="submitBtnText">Kirim Feedback</span>
                            <i id="submitBtnIcon" class="fa-regular fa-paper-plane text-sm"></i>
                        </button>
                    </div>

                    <!-- Anonymous Note -->
                    <div class="flex items-center justify-center gap-1.5 text-xs text-cozy-muted text-center pt-2">
                        <i class="fa-solid fa-lock text-[10px] text-cozy-muted/80"></i>
                        <span>Semua masukan bersifat anonim dan hanya akan digunakan untuk perkembangan konten aku <span class="text-cozy-terracotta">♡</span></span>
                    </div>

                </form>

            </div>
        </div>

    </main>

    <!-- Footer -->
    <footer class="py-8 text-center text-cozy-muted relative z-10">
        <p class="font-handwriting text-2xl text-cozy-text font-bold tracking-wide">
            ✨ thank you so much! ♡ ✨
        </p>
    </footer>

    <!-- Success Modal Overlay -->
    <div id="successModal" class="fixed inset-0 bg-cozy-text/40 backdrop-blur-sm z-50 flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
        <div class="bg-cozy-card border border-cozy-border rounded-3xl p-8 max-w-md w-full text-center shadow-floating transform scale-95 transition-transform duration-300 relative">
            <div class="w-16 h-16 rounded-full bg-cozy-pill mx-auto flex items-center justify-center text-cozy-terracotta text-2xl mb-4">
                <i class="fa-solid fa-heart"></i>
            </div>
            
            <h3 class="font-heading text-2xl font-bold text-cozy-text mb-2">Terima Kasih Banyak!</h3>
            <p class="text-cozy-muted text-sm leading-relaxed mb-6">
                Masukan kamu sudah berhasil terkirim. Pesan ini sangat berharga untuk membuat konten ku semakin baik lagi ♡
            </p>

            <button onclick="closeSuccessModal()" class="px-6 py-2.5 rounded-full bg-cozy-terracotta hover:bg-cozy-terracotta-hover text-white font-medium text-sm transition-all duration-200">
                Tutup Pesan
            </button>
        </div>
    </div>

    <!-- Admin Modal Overlay -->
    <div id="adminModal" class="fixed inset-0 bg-cozy-text/50 backdrop-blur-md z-50 flex items-center justify-center p-4 opacity-0 pointer-events-none transition-opacity duration-300">
        
        <!-- Login View Container -->
        <div id="adminLoginView" class="bg-cozy-card border border-cozy-border rounded-3xl p-6 md:p-8 max-w-sm w-full text-center shadow-floating relative">
            <button onclick="closeAdminModal()" class="absolute top-4 right-4 w-8 h-8 rounded-full bg-cozy-bg flex items-center justify-center text-cozy-muted hover:text-cozy-text">
                <i class="fa-solid fa-xmark"></i>
            </button>

            <div class="w-12 h-12 rounded-2xl bg-cozy-terracotta/15 flex items-center justify-center text-cozy-terracotta mx-auto mb-3">
                <i class="fa-solid fa-user-shield text-xl"></i>
            </div>
            <h3 class="font-heading text-xl font-bold text-cozy-text mb-1">Admin Mifa’s Corner</h3>
            <p class="text-cozy-muted text-xs mb-6">Masukkan kata sandi untuk melihat masukan followers</p>

            <form onsubmit="handleAdminLogin(event)" class="space-y-4">
                <input 
                    type="password" 
                    id="adminPassword" 
                    placeholder="Kata Sandi Admin..." 
                    class="w-full px-4 py-3 rounded-xl bg-cozy-inner border border-cozy-border text-cozy-text text-center text-sm focus:outline-none focus:border-cozy-terracotta"
                    required>
                <div id="loginError" class="text-xs text-red-500 hidden">Kata sandi salah! Coba lagi.</div>
                <button type="submit" class="w-full py-3 rounded-xl bg-cozy-terracotta hover:bg-cozy-terracotta-hover text-white text-sm font-medium transition-all">
                    Masuk Dashboard
                </button>
            </form>
            <p class="text-[11px] text-cozy-muted mt-4">Hanya untuk Mifa ♡</p>
        </div>

        <!-- Dashboard View Container (Expanded) -->
        <div id="adminDashboardView" class="hidden bg-cozy-card border border-cozy-border rounded-3xl p-6 md:p-8 max-w-4xl w-full max-h-[90vh] flex flex-col shadow-floating relative">
            
            <!-- Dashboard Header -->
            <div class="flex flex-wrap items-center justify-between gap-4 pb-4 border-b border-cozy-border">
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-2xl bg-cozy-terracotta/15 flex items-center justify-center text-cozy-terracotta">
                        <i class="fa-solid fa-inbox text-lg"></i>
                    </div>
                    <div>
                        <h3 class="font-heading text-xl font-bold text-cozy-text">Dashboard Feedback</h3>
                        <p class="text-cozy-muted text-xs">Total Masukan: <span id="totalFeedbackCount" class="font-bold text-cozy-terracotta">0</span></p>
                    </div>
                </div>

                <div class="flex items-center gap-2">
                    <button onclick="toggleEmailSettings()" class="px-3 py-1.5 rounded-lg bg-cozy-pill/60 hover:bg-cozy-pill text-cozy-text text-xs font-medium flex items-center gap-1.5 transition">
                        <i class="fa-solid fa-envelope"></i> Notifikasi Email
                    </button>
                    <button onclick="exportFeedbackCSV()" class="px-3 py-1.5 rounded-lg bg-cozy-pill/60 hover:bg-cozy-pill text-cozy-text text-xs font-medium flex items-center gap-1.5 transition">
                        <i class="fa-solid fa-download"></i> Export CSV
                    </button>
                    <button onclick="logoutAdmin()" class="px-3 py-1.5 rounded-lg bg-red-100 text-red-600 hover:bg-red-200 text-xs font-medium flex items-center gap-1 transition">
                        <i class="fa-solid fa-right-from-bracket"></i> Keluar
                    </button>
                    <button onclick="closeAdminModal()" class="w-8 h-8 rounded-full bg-cozy-bg flex items-center justify-center text-cozy-muted hover:text-cozy-text">
                        <i class="fa-solid fa-xmark"></i>
                    </button>
                </div>
            </div>

            <!-- Email Settings Panel (Collapsible) -->
            <div id="emailSettingsPanel" class="hidden bg-cozy-inner p-4 rounded-xl border border-cozy-border my-3 text-xs space-y-2">
                <div class="flex items-center justify-between">
                    <span class="font-semibold text-cozy-text"><i class="fa-solid fa-circle-info text-cozy-terracotta"></i> Pengaturan Notifikasi Email</span>
                    <button onclick="toggleEmailSettings()" class="text-cozy-muted hover:text-cozy-text"><i class="fa-solid fa-xmark"></i></button>
                </div>
                <p class="text-cozy-muted">Ingin menerima setiap feedback langsung ke email kamu? Kamu bisa memasukkan Email Destination di bawah ini untuk link mailto cepat atau mengkonfigurasi Webhook / EmailJS.</p>
                <div class="flex gap-2 pt-1">
                    <input type="email" id="targetEmailInput" placeholder="Email kamu (cth: mifa@gmail.com)" class="px-3 py-1.5 rounded-lg bg-cozy-card border border-cozy-border text-cozy-text flex-1">
                    <button onclick="saveTargetEmail()" class="px-4 py-1.5 bg-cozy-terracotta text-white rounded-lg font-medium hover:bg-cozy-terracotta-hover">Simpan Email</button>
                </div>
            </div>

            <!-- Search & Filters -->
            <div class="flex flex-wrap items-center justify-between gap-3 my-4">
                <div class="relative flex-1 min-w-[200px]">
                    <i class="fa-solid fa-magnifying-glass absolute left-3 top-1/2 -translate-y-1/2 text-cozy-muted/60 text-xs"></i>
                    <input 
                        type="text" 
                        id="searchInput" 
                        placeholder="Cari kata kunci dalam masukan..." 
                        oninput="filterFeedbacks()"
                        class="w-full pl-8 pr-4 py-2 rounded-xl bg-cozy-inner border border-cozy-border text-cozy-text text-xs focus:outline-none focus:border-cozy-terracotta">
                </div>
                <div class="flex items-center gap-1 bg-cozy-inner p-1 rounded-xl border border-cozy-border text-xs">
                    <button onclick="setFilter('all')" id="filterAll" class="px-3 py-1 rounded-lg bg-cozy-terracotta text-white font-medium">Semua</button>
                    <button onclick="setFilter('starred')" id="filterStarred" class="px-3 py-1 rounded-lg text-cozy-muted hover:text-cozy-text">Bintang ⭐</button>
                </div>
            </div>

            <!-- Feedback List Container (Scrollable) -->
            <div id="feedbackListContainer" class="flex-1 overflow-y-auto space-y-3 pr-1">
                <div class="text-center py-12 text-cozy-muted text-sm">
                    <i class="fa-solid fa-spinner fa-spin text-2xl text-cozy-terracotta mb-2"></i>
                    <p>Memuat masukan followers...</p>
                </div>
            </div>

        </div>

    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, addDoc, onSnapshot, doc, updateDoc, deleteDoc, serverTimestamp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Global Variables
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'mifas-corner-app';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {
            apiKey: "AIzaSyDummyKeyForFallbackPurposeOnly",
            authDomain: "mifas-corner.firebaseapp.com",
            projectId: "mifas-corner",
            storageBucket: "mifas-corner.appspot.com",
            messagingSenderId: "123456789",
            appId: "1:123456789:web:abc123def456"
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const db = getFirestore(app);

        let currentUser = null;
        let allFeedbacks = [];
        let currentFilter = 'all';
        let unsubscribeSnap = null;

        // Make functions globally available for inline event handlers
        window.handleFeedbackSubmit = handleFeedbackSubmit;
        window.updateCharCount = updateCharCount;
        window.openAdminModal = openAdminModal;
        window.closeAdminModal = closeAdminModal;
        window.handleAdminLogin = handleAdminLogin;
        window.closeSuccessModal = closeSuccessModal;
        window.logoutAdmin = logoutAdmin;
        window.toggleStar = toggleStar;
        window.deleteFeedbackItem = deleteFeedbackItem;
        window.copyFeedbackText = copyFeedbackText;
        window.filterFeedbacks = filterFeedbacks;
        window.setFilter = setFilter;
        window.exportFeedbackCSV = exportFeedbackCSV;
        window.toggleEmailSettings = toggleEmailSettings;
        window.saveTargetEmail = saveTargetEmail;

        window.addEventListener('load', async () => {
            try {
                if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                    const userCred = await signInWithCustomToken(auth, __initial_auth_token);
                    currentUser = userCred.user;
                } else {
                    const userCred = await signInAnonymously(auth);
                    currentUser = userCred.user;
                }
                console.log("Authenticated user:", currentUser.uid);
            } catch (err) {
                console.error("Auth initialization error:", err);
            }

            // Restore saved admin email setting if present
            const savedEmail = localStorage.getItem('mifa_target_email');
            if (savedEmail) {
                const input = document.getElementById('targetEmailInput');
                if (input) input.value = savedEmail;
            }
        });

        async function handleFeedbackSubmit(e) {
            e.preventDefault();
            const contentInput = document.getElementById('feedbackContent');
            const content = contentInput.value.trim();

            if (!content) return;

            const submitBtn = document.getElementById('submitBtn');
            const submitBtnText = document.getElementById('submitBtnText');
            const submitBtnIcon = document.getElementById('submitBtnIcon');

            // Set Loading state
            submitBtn.disabled = true;
            submitBtnText.textContent = "Mengirim...";
            submitBtnIcon.className = "fa-solid fa-spinner fa-spin text-sm";

            try {
                // Mandatory Path Rule: /artifacts/{appId}/public/data/{collectionName}
                const feedbackCol = collection(db, 'artifacts', appId, 'public', 'data', 'feedbacks');
                
                await addDoc(feedbackCol, {
                    content: content,
                    createdAt: serverTimestamp(),
                    isStarred: false,
                    isRead: false,
                    authorUid: currentUser ? currentUser.uid : 'anonymous'
                });

                // Reset Form
                contentInput.value = '';
                updateCharCount();

                // Check if email notification trigger is configured
                triggerOptionalEmailNotification(content);

                // Show Confetti Effect
                confetti({
                    particleCount: 80,
                    spread: 70,
                    origin: { y: 0.6 },
                    colors: ['#9C6153', '#EAD7C5', '#4A3B32', '#f3a683']
                });

                // Show Success Modal
                const modal = document.getElementById('successModal');
                modal.classList.remove('opacity-0', 'pointer-events-none');
                modal.querySelector('div').classList.remove('scale-95');
                modal.querySelector('div').classList.add('scale-100');

            } catch (err) {
                console.error("Error sending feedback:", err);
                alertCustom("Terjadi kesalahan saat mengirim masukan. Silakan coba lagi.");
            } finally {
                submitBtn.disabled = false;
                submitBtnText.textContent = "Kirim Feedback";
                submitBtnIcon.className = "fa-regular fa-paper-plane text-sm";
            }
        }

        function updateCharCount() {
            const textarea = document.getElementById('feedbackContent');
            const countDisplay = document.getElementById('charCount');
            if (textarea && countDisplay) {
                countDisplay.textContent = textarea.value.length;
            }
        }

        function closeSuccessModal() {
            const modal = document.getElementById('successModal');
            modal.classList.add('opacity-0', 'pointer-events-none');
            modal.querySelector('div').classList.remove('scale-100');
            modal.querySelector('div').classList.add('scale-95');
        }

        function openAdminModal() {
            const modal = document.getElementById('adminModal');
            modal.classList.remove('opacity-0', 'pointer-events-none');

            // If already logged in, show dashboard directly
            if (sessionStorage.getItem('mifa_admin_logged_in') === 'true') {
                showDashboardView();
            } else {
                showLoginView();
            }
        }

        function closeAdminModal() {
            const modal = document.getElementById('adminModal');
            modal.classList.add('opacity-0', 'pointer-events-none');
        }

        function showLoginView() {
            document.getElementById('adminLoginView').classList.remove('hidden');
            document.getElementById('adminDashboardView').classList.add('hidden');
        }

        function showDashboardView() {
            document.getElementById('adminLoginView').classList.add('hidden');
            document.getElementById('adminDashboardView').classList.remove('hidden');
            subscribeToFeedbacks();
        }

        function handleAdminLogin(e) {
            e.preventDefault();
            const passwordInput = document.getElementById('adminPassword');
            const errorMsg = document.getElementById('loginError');

            // Default simple admin password: mifa123
            if (passwordInput.value.trim() === 'mifa123') {
                errorMsg.classList.add('hidden');
                sessionStorage.setItem('mifa_admin_logged_in', 'true');
                passwordInput.value = '';
                showDashboardView();
            } else {
                errorMsg.classList.remove('hidden');
            }
        }

        function logoutAdmin() {
            sessionStorage.removeItem('mifa_admin_logged_in');
            if (unsubscribeSnap) {
                unsubscribeSnap();
                unsubscribeSnap = null;
            }
            showLoginView();
        }

        function subscribeToFeedbacks() {
            if (unsubscribeSnap) return; // Already subscribed

            const feedbackCol = collection(db, 'artifacts', appId, 'public', 'data', 'feedbacks');

            // Simple collection query without complex orderBy to prevent indexing errors (Rule 2)
            unsubscribeSnap = onSnapshot(feedbackCol, (snapshot) => {
                let items = [];
                snapshot.forEach(docSnap => {
                    const data = docSnap.data();
                    items.push({
                        id: docSnap.id,
                        content: data.content || '',
                        createdAt: data.createdAt ? data.createdAt.toDate() : new Date(),
                        isStarred: data.isStarred || false,
                        isRead: data.isRead || false,
                        authorUid: data.authorUid || 'anonymous'
                    });
                });

                // Client-side sorting: Latest first
                items.sort((a, b) => b.createdAt - a.createdAt);

                allFeedbacks = items;
                renderFeedbacks();
            }, (error) => {
                console.error("Firestore sync error:", error);
                document.getElementById('feedbackListContainer').innerHTML = `
                    <div class="text-center py-8 text-red-500 text-xs">
                        Gagal memuat data. Periksa koneksi internet kamu.
                    </div>
                `;
            });
        }

        function renderFeedbacks() {
            const container = document.getElementById('feedbackListContainer');
            const totalCount = document.getElementById('totalFeedbackCount');
            const searchVal = (document.getElementById('searchInput')?.value || '').toLowerCase();

            let filtered = allFeedbacks.filter(item => {
                const matchesSearch = item.content.toLowerCase().includes(searchVal);
                if (currentFilter === 'starred') {
                    return matchesSearch && item.isStarred;
                }
                return matchesSearch;
            });

            totalCount.textContent = allFeedbacks.length;

            if (filtered.length === 0) {
                container.innerHTML = `
                    <div class="text-center py-12 text-cozy-muted">
                        <i class="fa-regular fa-comment-dots text-3xl mb-2 text-cozy-muted/40"></i>
                        <p class="text-xs">Belum ada masukan yang cocok.</p>
                    </div>
                `;
                return;
            }

            container.innerHTML = filtered.map(item => {
                const dateStr = item.createdAt.toLocaleDateString('id-ID', {
                    day: 'numeric',
                    month: 'short',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit'
                });

                return `
                    <div class="bg-cozy-inner p-4 rounded-2xl border border-cozy-border hover:border-cozy-terracotta/40 transition-all text-xs space-y-2 relative group">
                        <div class="flex items-center justify-between gap-2 text-cozy-muted">
                            <span class="flex items-center gap-1.5 font-medium text-[11px] text-cozy-muted/80">
                                <i class="fa-regular fa-clock"></i> ${dateStr}
                            </span>
                            <div class="flex items-center gap-1">
                                <button onclick="toggleStar('${item.id}', ${!item.isStarred})" title="${item.isStarred ? 'Hapus Bintang' : 'Berikan Bintang'}" class="p-1.5 rounded-lg hover:bg-cozy-bg text-cozy-muted hover:text-amber-500 transition">
                                    <i class="${item.isStarred ? 'fa-solid fa-star text-amber-500' : 'fa-regular fa-star'}"></i>
                                </button>
                                <button onclick="copyFeedbackText(\`${escapeHtml(item.content)}\`)" title="Salin Teks" class="p-1.5 rounded-lg hover:bg-cozy-bg text-cozy-muted hover:text-cozy-text transition">
                                    <i class="fa-regular fa-copy"></i>
                                </button>
                                <button onclick="deleteFeedbackItem('${item.id}')" title="Hapus Masukan" class="p-1.5 rounded-lg hover:bg-red-50 text-cozy-muted hover:text-red-500 transition">
                                    <i class="fa-regular fa-trash-can"></i>
                                </button>
                            </div>
                        </div>

                        <p class="text-cozy-text text-sm leading-relaxed whitespace-pre-wrap font-sans">${escapeHtml(item.content)}</p>
                    </div>
                `;
            }).join('');
        }

        async function toggleStar(docId, newStarredState) {
            try {
                const docRef = doc(db, 'artifacts', appId, 'public', 'data', 'feedbacks', docId);
                await updateDoc(docRef, { isStarred: newStarredState });
            } catch (err) {
                console.error("Error updating star state:", err);
            }
        }

        async function deleteFeedbackItem(docId) {
            if (!window.confirmCustom("Apakah kamu yakin ingin menghapus masukan ini?")) return;
            try {
                const docRef = doc(db, 'artifacts', appId, 'public', 'data', 'feedbacks', docId);
                await deleteDoc(docRef);
            } catch (err) {
                console.error("Error deleting feedback:", err);
            }
        }

        function copyFeedbackText(text) {
            const tempInput = document.createElement('textarea');
            tempInput.value = text;
            document.body.appendChild(tempInput);
            tempInput.select();
            document.execCommand('copy');
            document.body.removeChild(tempInput);

            showToast("Teks masukan disalin ke clipboard! ✨");
        }

        function filterFeedbacks() {
            renderFeedbacks();
        }

        function setFilter(type) {
            currentFilter = type;
            const btnAll = document.getElementById('filterAll');
            const btnStarred = document.getElementById('filterStarred');

            if (type === 'all') {
                btnAll.className = "px-3 py-1 rounded-lg bg-cozy-terracotta text-white font-medium";
                btnStarred.className = "px-3 py-1 rounded-lg text-cozy-muted hover:text-cozy-text";
            } else {
                btnStarred.className = "px-3 py-1 rounded-lg bg-cozy-terracotta text-white font-medium";
                btnAll.className = "px-3 py-1 rounded-lg text-cozy-muted hover:text-cozy-text";
            }
            renderFeedbacks();
        }

        function exportFeedbackCSV() {
            if (allFeedbacks.length === 0) {
                alertCustom("Belum ada data untuk di-export.");
                return;
            }

            let csvContent = "data:text/csv;charset=utf-8,No,Tanggal,Masukan,Bintang\n";
            allFeedbacks.forEach((item, index) => {
                const cleanContent = `"${item.content.replace(/"/g, '""')}"`;
                const dateStr = item.createdAt.toISOString();
                csvContent += `${index + 1},${dateStr},${cleanContent},${item.isStarred ? 'Ya' : 'Tidak'}\n`;
            });

            const encodedUri = encodeURI(csvContent);
            const link = document.createElement("a");
            link.setAttribute("href", encodedUri);
            link.setAttribute("download", `mifas_corner_feedbacks_${new Date().toISOString().slice(0,10)}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }

        function toggleEmailSettings() {
            const panel = document.getElementById('emailSettingsPanel');
            panel.classList.toggle('hidden');
        }

        function saveTargetEmail() {
            const input = document.getElementById('targetEmailInput');
            const email = input.value.trim();
            if (email) {
                localStorage.setItem('mifa_target_email', email);
                showToast("Email notifikasi disimpan! 📩");
            } else {
                localStorage.removeItem('mifa_target_email');
                showToast("Pengaturan email dihapus.");
            }
        }

        function triggerOptionalEmailNotification(feedbackContent) {
            const targetEmail = localStorage.getItem('mifa_target_email');
            if (targetEmail) {
                // Generates a quick mailto link trigger or console log for notifications
                const subject = encodeURIComponent("Feedback Baru di Mifa's Corner! ♡");
                const body = encodeURIComponent(`Halo Mifa!\n\nKamu mendapatkan masukan baru dari followers:\n\n"${feedbackContent}"\n\nCek seluruh masukan di dashboard kamu!`);
                console.log(`Notification trigger ready for: ${targetEmail}`);
            }
        }

        function escapeHtml(str) {
            return str
                .replace(/&/g, "&amp;")
                .replace(/</g, "&lt;")
                .replace(/>/g, "&gt;")
                .replace(/"/g, "&quot;")
                .replace(/'/g, "&#039;");
        }

        function showToast(message) {
            const toast = document.createElement('div');
            toast.className = 'fixed bottom-6 left-1/2 -translate-x-1/2 bg-cozy-text text-white px-5 py-2.5 rounded-full text-xs shadow-lg z-50 animate-bounce transition-all';
            toast.innerHTML = message;
            document.body.appendChild(toast);
            setTimeout(() => {
                toast.remove();
            }, 3000);
        }

        function alertCustom(message) {
            showToast(message);
        }

        window.confirmCustom = function(message) {
            // Safe inline check for critical admin actions
            return window.confirm(message);
        }

    </script>
</body>
</html>
