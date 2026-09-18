<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CARTEC - Tecnologia Automotiva Avançada | Mobilidade Autónoma</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Chart.js CDN for visual statistics -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;1,400&family=Orbitron:wght@600;800;900&display=swap" rel="stylesheet">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['"Plus Jakarta Sans"', 'sans-serif'],
                        tech: ['Orbitron', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            50: '#f0f7ff',
                            100: '#e0effe',
                            400: '#38bdf8',
                            500: '#0284c7',
                            600: '#026aa2',
                            700: '#035485',
                            800: '#074268',
                            900: '#0c2e4a',
                            dark: '#050a15',
                            card: '#0d1527'
                        },
                        danger: '#ef4444',
                        accent: '#10b981',
                        warning: '#f59e0b'
                    }
                }
            }
        }
    </script>

    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #040812;
            color: #f1f5f9;
            overflow-x: hidden;
        }

        .font-tech {
            font-family: 'Orbitron', sans-serif;
        }

        .glass-panel {
            background: rgba(13, 21, 39, 0.85);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(56, 189, 248, 0.12);
        }

        .glass-panel-hover {
            transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
        }

        .glass-panel-hover:hover {
            border-color: rgba(56, 189, 248, 0.4);
            transform: translateY(-4px);
            box-shadow: 0 16px 35px -10px rgba(14, 165, 233, 0.2);
        }

        .gradient-text {
            background: linear-gradient(135deg, #38bdf8 0%, #00a8ff 40%, #818cf8 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .gradient-text-danger {
            background: linear-gradient(135deg, #f87171 0%, #ef4444 50%, #dc2626 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .gradient-text-success {
            background: linear-gradient(135deg, #34d399 0%, #10b981 50%, #059669 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .custom-slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 22px;
            height: 22px;
            border-radius: 50%;
            background: #38bdf8;
            cursor: pointer;
            box-shadow: 0 0 12px rgba(56, 189, 248, 0.9);
        }

        .nav-link {
            position: relative;
            transition: color 0.3s ease;
        }

        .nav-link.active {
            color: #38bdf8;
            font-weight: 700;
        }

        .nav-link.active::after {
            content: '';
            position: absolute;
            bottom: -6px;
            left: 0;
            width: 100%;
            height: 2px;
            background: #38bdf8;
            border-radius: 2px;
            box-shadow: 0 0 10px #38bdf8;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
            animation: fadeIn 0.4s cubic-bezier(0.16, 1, 0.3, 1);
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes pulseGlow {
            0%, 100% { filter: drop-shadow(0 0 6px rgba(56, 189, 248, 0.4)); }
            50% { filter: drop-shadow(0 0 18px rgba(56, 189, 248, 0.8)); }
        }

        .logo-glow {
            animation: pulseGlow 4s infinite ease-in-out;
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #040812;
        }
        ::-webkit-scrollbar-thumb {
            background: #1e293b;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #0284c7;
        }
    </style>
</head>
<body class="min-h-screen flex flex-col justify-between selection:bg-sky-500 selection:text-white">

    <!-- Header / Navigation -->
    <header class="sticky top-0 z-50 glass-panel border-b border-slate-800/80">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-24">
                
                <!-- CARTEC Official Logo SVG Integration -->
                <div class="flex items-center space-x-3 cursor-pointer group" onclick="switchTab('inicio')">
                    <div class="w-12 h-12 flex items-center justify-center logo-glow">
                        <svg viewBox="0 0 120 120" class="w-full h-full">
                            <defs>
                                <linearGradient id="logoGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                                    <stop offset="0%" stop-color="#0284c7" />
                                    <stop offset="50%" stop-color="#38bdf8" />
                                    <stop offset="100%" stop-color="#0284c7" />
                                </linearGradient>
                            </defs>
                            <circle cx="60" cy="60" r="48" fill="none" stroke="url(#logoGrad)" stroke-width="7" opacity="0.9"/>
                            <circle cx="60" cy="60" r="38" fill="none" stroke="#0f172a" stroke-width="4"/>
                            
                            <path d="M 25,62 C 30,55 42,48 58,48 C 72,48 85,55 92,58 L 102,52 L 95,65" fill="none" stroke="#38bdf8" stroke-width="3.5" stroke-linecap="round"/>
                            <path d="M 22,66 L 38,66 C 42,66 45,72 50,72 C 55,72 58,66 75,66 C 80,66 83,72 88,72 C 92,72 95,66 98,66" fill="none" stroke="#38bdf8" stroke-width="3" stroke-linecap="round"/>
                            
                            <circle cx="38" cy="66" r="2.5" fill="#38bdf8"/>
                            <circle cx="75" cy="66" r="2.5" fill="#38bdf8"/>
                            <path d="M 50,55 L 68,55 L 78,60" fill="none" stroke="#00a8ff" stroke-width="2.5"/>
                            <circle cx="68" cy="55" r="2" fill="#00a8ff"/>
                            
                            <polygon points="92,48 108,52 96,62" fill="#38bdf8"/>
                        </svg>
                    </div>
                    
                    <div class="flex flex-col">
                        <span class="font-tech text-2xl font-black tracking-wider text-white flex items-center">
                            CAR<span class="text-sky-400">TEC</span>
                        </span>
                        <span class="text-[9px] uppercase font-extrabold tracking-widest text-slate-300">
                            TECNOLOGIA AUTOMOTIVA AVANÇADA
                        </span>
                    </div>
                </div>

                <!-- Desktop Navigation Menu -->
                <nav class="hidden md:flex items-center space-x-7 text-xs font-semibold">
                    <button onclick="switchTab('inicio')" id="nav-inicio" class="nav-link active text-slate-300 hover:text-white py-2">
                        <i class="fa-solid fa-house mr-1.5 text-sky-400"></i>Início
                    </button>
                    <button onclick="switchTab('modulo1')" id="nav-modulo1" class="nav-link text-slate-300 hover:text-white py-2">
                        <i class="fa-solid fa-triangle-exclamation mr-1.5 text-red-400"></i>Módulo 01: O Problema
                    </button>
                    <button onclick="switchTab('modulo2')" id="nav-modulo2" class="nav-link text-slate-300 hover:text-white py-2">
                        <i class="fa-solid fa-microchip mr-1.5 text-sky-400"></i>Módulo 02: A Solução
                    </button>
                    <button onclick="switchTab('estado')" id="nav-estado" class="nav-link text-slate-300 hover:text-white py-2">
                        <i class="fa-solid fa-bars-progress mr-1.5 text-emerald-400"></i>Estado do Projeto
                    </button>
                    <button onclick="switchTab('parcerias')" id="nav-parcerias" class="nav-link text-slate-300 hover:text-white py-2">
                        <i class="fa-solid fa-handshake mr-1.5 text-indigo-400"></i>Parcerias & Investimento
                    </button>
                </nav>

                <!-- Action Button -->
                <div class="hidden lg:flex items-center space-x-3">
                    <button onclick="switchTab('contacto')" class="px-4 py-2.5 rounded-xl bg-gradient-to-r from-sky-500 to-brand-600 text-white font-bold text-xs tracking-wide hover:shadow-lg hover:shadow-sky-500/25 border border-sky-400/30 transition">
                        <i class="fa-solid fa-envelope mr-1.5"></i>Contactar Autor
                    </button>
                </div>

                <!-- Mobile Menu Button -->
                <div class="md:hidden flex items-center">
                    <button id="mobile-menu-btn" onclick="toggleMobileMenu()" class="text-slate-300 hover:text-white p-2">
                        <i class="fa-solid fa-bars text-2xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Navigation Drawer -->
        <div id="mobile-menu" class="hidden md:hidden glass-panel border-b border-slate-800 px-4 pt-2 pb-6 space-y-3">
            <button onclick="switchTab('inicio')" class="block w-full text-left py-2.5 px-3 rounded-lg hover:bg-slate-800/60 text-slate-200 text-sm font-semibold">
                <i class="fa-solid fa-house mr-2 text-sky-400"></i>Início
            </button>
            <button onclick="switchTab('modulo1')" class="block w-full text-left py-2.5 px-3 rounded-lg hover:bg-slate-800/60 text-slate-200 text-sm font-semibold">
                <i class="fa-solid fa-triangle-exclamation mr-2 text-red-400"></i>Módulo 01: O Problema Global
            </button>
            <button onclick="switchTab('modulo2')" class="block w-full text-left py-2.5 px-3 rounded-lg hover:bg-slate-800/60 text-slate-200 text-sm font-semibold">
                <i class="fa-solid fa-microchip mr-2 text-sky-400"></i>Módulo 02: A Solução Proposta
            </button>
            <button onclick="switchTab('estado')" class="block w-full text-left py-2.5 px-3 rounded-lg hover:bg-slate-800/60 text-slate-200 text-sm font-semibold">
                <i class="fa-solid fa-bars-progress mr-2 text-emerald-400"></i>Estado do Projeto
            </button>
            <button onclick="switchTab('parcerias')" class="block w-full text-left py-2.5 px-3 rounded-lg hover:bg-slate-800/60 text-slate-200 text-sm font-semibold">
                <i class="fa-solid fa-handshake mr-2 text-indigo-400"></i>Parcerias & Investimento
            </button>
            <button onclick="switchTab('contacto')" class="block w-full text-left py-2.5 px-3 rounded-lg hover:bg-slate-800/60 text-slate-200 text-sm font-semibold">
                <i class="fa-solid fa-envelope mr-2 text-sky-400"></i>Contacto Directo
            </button>
        </div>
    </header>

    <!-- Notification Toast Container -->
    <div id="toast-container" class="fixed top-28 right-5 z-50 flex flex-col space-y-3 max-w-sm pointer-events-none"></div>

    <!-- Main Content Dynamic Container -->
    <main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">

        <!-- ========================================================================= -->
        <!-- TAB 1: INÍCIO & VISÃO GERAL DO PROJETO CARTEC -->
        <!-- ========================================================================= -->
        <section id="tab-inicio" class="tab-content active space-y-16">
            
            <!-- Hero Banner -->
            <div class="relative rounded-3xl overflow-hidden glass-panel p-8 sm:p-12 lg:p-16 border border-sky-500/20">
                <div class="absolute -top-32 -right-32 w-96 h-96 bg-sky-500/10 rounded-full blur-3xl pointer-events-none"></div>
                <div class="absolute -bottom-32 -left-32 w-96 h-96 bg-indigo-500/10 rounded-full blur-3xl pointer-events-none"></div>

                <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center relative z-10">
                    <div class="lg:col-span-7 space-y-6">
                        <div class="inline-flex items-center space-x-2 px-3.5 py-1.5 rounded-full bg-sky-500/10 border border-sky-500/30 text-sky-400 text-xs font-semibold tracking-wide">
                            <span class="w-2 h-2 rounded-full bg-sky-400 animate-ping"></span>
                            <span>Proposta de Projeto • Mobilidade Autónoma & Emergência</span>
                        </div>

                        <h1 class="text-3xl sm:text-5xl font-extrabold tracking-tight text-white leading-tight">
                            Projeto CARTEC: <span class="gradient-text">Autocarro Autónomo de Emergência</span>
                        </h1>

                        <p class="text-slate-300 text-base sm:text-lg leading-relaxed">
                            Um sistema abrangente de <strong>Segurança Ativa e Passiva</strong> com Inteligência Artificial, resposta ultrarrápida (&lt;10ms) e supressão imediata de incêndios. Desenvolvido para erradicar falhas humanas, proteger vidas no transporte coletivo e prevenir elevadas perdas patrimoniais.
                        </p>

                        <!-- Project Author Badge -->
                        <div class="flex items-center space-x-4 p-3.5 rounded-2xl bg-slate-900/80 border border-slate-800 w-fit">
                            <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-sky-500 to-indigo-600 flex items-center justify-center text-white font-bold text-lg">
                                <i class="fa-solid fa-user-gear"></i>
                            </div>
                            <div>
                                <p class="text-[10px] uppercase font-bold text-sky-400 tracking-widest">Autor & Investigador Principal</p>
                                <p class="text-sm font-extrabold text-white">Adilson Lourenço da Costa Santa-Rosa</p>
                                <p class="text-[11px] text-slate-400">Santa-Rosa CORP</p>
                            </div>
                        </div>

                        <div class="flex flex-wrap gap-4 pt-2">
                            <button onclick="switchTab('modulo2')" class="px-6 py-3.5 rounded-xl bg-gradient-to-r from-sky-500 to-indigo-600 text-white font-bold text-sm hover:shadow-lg hover:shadow-sky-500/30 transition border border-sky-400/30">
                                Explorar A Solução <i class="fa-solid fa-microchip ml-2"></i>
                            </button>
                            <button onclick="switchTab('modulo1')" class="px-6 py-3.5 rounded-xl bg-slate-800/90 hover:bg-slate-800 text-slate-200 font-semibold text-sm border border-slate-700 transition">
                                <i class="fa-solid fa-triangle-exclamation mr-2 text-red-400"></i>Análise de Sinistralidade
                            </button>
                        </div>

                        <!-- Key Performance Indicators -->
                        <div class="grid grid-cols-3 gap-4 pt-6 border-t border-slate-800/80">
                            <div>
                                <p class="text-2xl font-black text-sky-400 font-tech">&lt; 10 ms</p>
                                <p class="text-xs text-slate-400">Resposta das ECUs</p>
                            </div>
                            <div>
                                <p class="text-2xl font-black text-emerald-400 font-tech">360°</p>
                                <p class="text-xs text-slate-400">Perceção LIDAR & Radar</p>
                            </div>
                            <div>
                                <p class="text-2xl font-black text-indigo-400 font-tech">100%</p>
                                <p class="text-xs text-slate-400">Supressão Térmica Ativa</p>
                            </div>
                        </div>
                    </div>

                    <!-- Visual Tech Card Showcase -->
                    <div class="lg:col-span-5">
                        <div class="relative rounded-2xl p-6 glass-panel border border-sky-500/30 shadow-2xl space-y-6">
                            <!-- Visual Banner Image -->
                            <div class="relative h-64 rounded-xl overflow-hidden bg-slate-950 border border-slate-800 group">
                                <img src="https://images.unsplash.com/photo-1570125909232-eb263c188f7e?auto=format&fit=crop&w=800&q=80" 
                                     alt="Autocarro Autónomo de Emergência CARTEC" 
                                     class="w-full h-full object-cover group-hover:scale-105 transition duration-700 opacity-80"
                                     onerror="this.src='https://images.unsplash.com/photo-1544620347-c4fd4a3d5957?auto=format&fit=crop&w=800&q=80'">
                                <div class="absolute inset-0 bg-gradient-to-t from-slate-950 via-slate-950/30 to-transparent"></div>
                                <div class="absolute top-3 right-3 px-3 py-1 rounded-full bg-sky-500/20 backdrop-blur-md border border-sky-400/40 text-sky-300 text-[10px] font-mono font-bold">
                                    CONCEITO CARTEC
                                </div>
                                <div class="absolute bottom-3 left-3 right-3 flex justify-between items-center text-xs">
                                    <span class="px-2.5 py-1 rounded bg-slate-900/90 text-sky-400 font-mono border border-sky-500/40 flex items-center">
                                        <i class="fa-solid fa-shield-halved mr-1.5 text-emerald-400"></i> Sistema Ativo AI
                                    </span>
                                    <span class="text-slate-300 font-mono text-[11px]">Santa-Rosa CORP</span>
                                </div>
                            </div>

                            <div class="space-y-3">
                                <div class="flex items-center justify-between text-xs font-semibold text-slate-400">
                                    <span>ARQUITETURA DE SEGURANÇA</span>
                                    <span class="text-sky-400 font-tech">CARTEC 360</span>
                                </div>
                                <div class="space-y-2">
                                    <div class="flex items-center justify-between text-xs p-2.5 rounded-lg bg-slate-900/80 border border-slate-800">
                                        <span c
