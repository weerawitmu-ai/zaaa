<!DOCTYPE html>
<html lang="th" class="dark scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GAMEX // FUTURISTIC - ศูนย์รวมเกมระดับพรีเมียม</title>

    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome 6 Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Prompt & Rajdhani & Orbitron -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;900&family=Prompt:ital,wght@0,300;0,400;0,600;0,700;1,800&family=Rajdhani:wght@500;600;700&display=swap" rel="stylesheet">

    <style>
        body {
            font-family: 'Prompt', sans-serif;
            background-color: #05060b;
            color: #e2e8f0;
            overflow-x: hidden;
        }

        .font-cyber {
            font-family: 'Orbitron', sans-serif;
        }
        .font-rajdhani {
            font-family: 'Rajdhani', sans-serif;
        }

        /* Animated Futuristic Background Canvas */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1;
            pointer-events: none;
        }

        /* Scanline Overlay Effect */
        .scanline-bg {
            background: linear-gradient(
                rgba(18, 16, 16, 0) 50%, 
                rgba(0, 0, 0, 0.35) 50%
            ), linear-gradient(
                90deg,
                rgba(255, 0, 0, 0.02),
                rgba(0, 255, 0, 0.01),
                rgba(0, 0, 255, 0.02)
            );
            background-size: 100% 4px, 6px 100%;
        }

        /* Neon Glow Utility Effects */
        .glow-cyan {
            text-shadow: 0 0 8px rgba(0, 243, 255, 0.8), 0 0 20px rgba(0, 243, 255, 0.4);
        }
        .glow-pink {
            text-shadow: 0 0 8px rgba(255, 0, 85, 0.8), 0 0 20px rgba(255, 0, 85, 0.4);
        }
        .glow-yellow {
            text-shadow: 0 0 8px rgba(255, 234, 0, 0.8);
        }

        /* Cyberpunk Corner Clips */
        .cyber-clip {
            clip-path: polygon(0 0, calc(100% - 18px) 0, 100% 18px, 100% 100%, 18px 100%, 0 calc(100% - 18px));
        }
        .cyber-clip-badge {
            clip-path: polygon(0 0, 100% 0, calc(100% - 12px) 100%, 0 100%);
        }

        /* Dynamic Glowing Neon Box Animation */
        @keyframes borderPulse {
            0%, 100% {
                box-shadow: 0 0 15px rgba(0, 243, 255, 0.3), inset 0 0 10px rgba(0, 243, 255, 0.1);
                border-color: rgba(0, 243, 255, 0.6);
            }
            50% {
                box-shadow: 0 0 28px rgba(0, 243, 255, 0.7), inset 0 0 20px rgba(0, 243, 255, 0.25);
                border-color: rgba(0, 243, 255, 1);
            }
        }

        .neon-card {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .neon-card:hover {
            transform: translateY(-8px) scale(1.02);
            animation: borderPulse 2s infinite ease-in-out;
        }

        /* Custom Cyber Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #030408;
        }
        ::-webkit-scrollbar-thumb {
            background: #00f3ff;
            border-radius: 4px;
            box-shadow: 0 0 10px #00f3ff;
        }
    </style>
</head>
<body class="scanline-bg min-h-screen flex flex-col justify-between selection:bg-cyan-500 selection:text-black">

    <canvas id="bg-canvas"></canvas>

    <header class="sticky top-0 z-40 bg-slate-950/80 backdrop-blur-md border-b border-cyan-500/30 shadow-[0_4px_25px_rgba(0,243,255,0.15)]">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <!-- Brand Logo -->
            <a href="#" class="flex items-center gap-3 group">
                <div class="w-11 h-11 bg-cyan-500/10 border border-cyan-400 flex items-center justify-center rounded-lg cyber-clip group-hover:scale-110 transition-transform shadow-[0_0_15px_rgba(0,243,255,0.3)]">
                    <i class="fa-solid fa-gamepad text-cyan-400 text-2xl group-hover:rotate-12 transition-transform"></i>
                </div>
                <div>
                    <span class="font-rajdhani font-extrabold text-2xl tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-pink-500 to-amber-400 glow-cyan">
                        GAMEX <span class="text-xs text-cyan-400 block -mt-1 font-mono tracking-widest">// FUTURISTIC</span>
                    </span>
                </div>
            </a>

            <!-- Navigation Links -->
            <nav class="hidden md:flex items-center space-x-8 text-sm font-semibold uppercase tracking-wider">
                <a href="#hero" class="text-cyan-400 hover:text-white hover:drop-shadow-[0_0_10px_#00f3ff] transition-all flex items-center gap-2">
                    <i class="fa-solid fa-house-laptop text-xs"></i> หน้าแรก
                </a>
                <a href="#action-games" class="text-slate-300 hover:text-cyan-400 hover:drop-shadow-[0_0_10px_#00f3ff] transition-all flex items-center gap-2">
                    <i class="fa-solid fa-crosshairs text-xs"></i> เกมแอ็คชั่น
                </a>
                <a href="#categories" class="text-slate-300 hover:text-pink-400 hover:drop-shadow-[0_0_10px_#ff0055] transition-all flex items-center gap-2">
                    <i class="fa-solid fa-layer-group text-xs"></i> หมวดหมู่เกม
                </a>
                <a href="#contact" class="text-slate-300 hover:text-yellow-400 hover:drop-shadow-[0_0_10px_#ffea00] transition-all flex items-center gap-2">
                    <i class="fa-solid fa-headset text-xs"></i> ติดต่อเรา
                </a>
            </nav>

            <!-- Quick Status Badge -->
            <div class="hidden lg:flex items-center gap-3 px-3.5 py-1.5 rounded-full bg-cyan-950/50 border border-cyan-500/40 text-xs font-mono text-cyan-300 shadow-[0_0_12px_rgba(0,243,255,0.2)]">
                <span class="w-2.5 h-2.5 rounded-full bg-cyan-400 animate-ping"></span>
                CYBER CORE: ACTIVE
            </div>
        </div>
    </header>

    <section id="hero" class="relative py-12 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto w-full">
        <div class="relative bg-gradient-to-r from-slate-950/90 via-cyan-950/40 to-slate-950/90 border border-cyan-500/40 rounded-2xl p-8 md:p-12 overflow-hidden shadow-[0_0_50px_rgba(0,243,255,0.2)] cyber-clip backdrop-blur-sm">
            <div class="absolute -right-20 -bottom-20 w-96 h-96 bg-cyan-500/10 rounded-full blur-3xl pointer-events-none"></div>
            <div class="absolute -left-20 -top-20 w-96 h-96 bg-pink-500/10 rounded-full blur-3xl pointer-events-none"></div>

            <div class="relative z-10 max-w-3xl">
                <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-pink-500/20 border border-pink-500/50 text-pink-400 text-xs font-mono uppercase tracking-widest mb-4">
                    <i class="fa-solid fa-bolt text-pink-400 animate-bounce"></i> Cyberpunk Action Showcase 2026
                </div>
                <h1 class="text-4xl sm:text-6xl font-extrabold text-white tracking-tight leading-none mb-6">
                    อาณาจักรเกมแอ็คชั่น <br>
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-pink-500 to-amber-400 glow-cyan">
                        FUTURISTIC CYBERPUNK
                    </span>
                </h1>
                <p class="text-slate-300 text-base sm:text-lg mb-8 font-light leading-relaxed">
                    ค้นพบสุดยอด 6 เกมแอ็คชั่นระดับตำนานที่ถูกคัดสรรมาเป็นอย่างดี พร้อมภาพปกประจำเกมอย่างเป็นทางการ และรับชมวิดีโอตัวอย่างเกม (Trailer) ระดับความละเอียดสูงได้ทันทีในหน้าเดียว!
                </p>
                <div class="flex flex-wrap gap-4">
                    <a href="#action-games" class="px-6 py-3.5 bg-gradient-to-r from-cyan-500 to-blue-600 hover:from-cyan-400 hover:to-blue-500 text-black font-bold uppercase tracking-wider rounded cyber-clip transition-all shadow-[0_0_25px_rgba(0,243,255,0.5)] flex items-center gap-2">
                        <i class="fa-solid fa-play"></i> สำรวจเกมแอ็คชั่น
                    </a>
                    <a href="#contact" class="px-6 py-3.5 bg-slate-900/80 hover:bg-slate-800/80 border border-amber-500/50 text-amber-300 font-bold uppercase tracking-wider rounded cyber-clip transition-all flex items-center gap-2">
                        <i class="fa-solid fa-id-card"></i> ติดต่อเราที่นี้
                    </a>
                </div>
            </div>
        </div>
    </section>

    <section id="action-games" class="py-12 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto w-full">
        <!-- Section Header -->
        <div class="flex flex-col md:flex-row md:items-end justify-between mb-10 pb-4 border-b border-cyan-500/20 gap-4">
            <div>
                <div class="text-xs font-mono text-cyan-400 tracking-widest uppercase mb-1">
                    <i class="fa-solid fa-shield-halved"></i> Action Game Collection
                </div>
                <h2 class="text-3xl sm:text-4xl font-extrabold text-white tracking-wide flex items-center gap-3">
                    <span class="w-3 h-8 bg-cyan-400 inline-block rounded-sm shadow-[0_0_10px_#00f3ff]"></span>
                    เกมแอ็คชั่นแนะนำ <span class="text-cyan-400 font-mono text-xl">(Showcase)</span>
                </h2>
            </div>
            
            <!-- Live Search Input -->
            <div class="relative w-full md:w-72">
                <input type="text" id="game-search" oninput="handleSearch()" placeholder="ค้นหาชื่อเกม..." class="w-full bg-slate-900/90 border border-cyan-500/40 rounded-lg px-4 py-2 text-sm text-white focus:outline-none focus:border-cyan-400 focus:ring-1 focus:ring-cyan-400 transition-all pl-10">
                <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-3 text-cyan-400 text-sm"></i>
            </div>
        </div>

        <!-- Action Games Grid -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8" id="action-games-grid">
            <!-- Dynamic Cards Loaded via JavaScript -->
        </div>
    </section>

    <section id="categories" class="py-12 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto w-full">
        <div class="bg-slate-950/70 border border-pink-500/30 rounded-2xl p-6 sm:p-8 backdrop-blur-md shadow-[0_0_30px_rgba(255,0,85,0.1)]">
            <div class="flex flex-col md:flex-row md:items-center justify-between mb-8 gap-4">
                <div>
                    <span class="text-xs font-mono text-pink-400 tracking-widest uppercase block mb-1">
                        <i class="fa-solid fa-filter"></i> Category Filter System
                    </span>
                    <h2 class="text-2xl sm:text-3xl font-extrabold text-white">
                        เลือกหมวดหมู่เกม <span class="text-pink-400 font-mono text-lg">(Game Types)</span>
                    </h2>
                </div>
                
                <!-- Category Filter Buttons -->
                <div class="flex flex-wrap gap-2" id="category-tabs">
                    <button onclick="filterCategory('all', this)" class="cat-btn active px-4 py-2 text-xs font-bold uppercase tracking-wider rounded border border-cyan-400 bg-cyan-500 text-black transition-all shadow-[0_0_12px_rgba(0,243,255,0.4)]">
                        ทั้งหมด
                    </button>
                    <button onclick="filterCategory('open-world', this)" class="cat-btn px-4 py-2 text-xs font-bold uppercase tracking-wider rounded border border-slate-800 bg-slate-900 text-slate-300 hover:border-cyan-400 hover:text-cyan-400 transition-all">
                        Open World
                    </button>
                    <button onclick="filterCategory('battle-royale', this)" class="cat-btn px-4 py-2 text-xs font-bold uppercase tracking-wider rounded border border-slate-800 bg-slate-900 text-slate-300 hover:border-cyan-400 hover:text-cyan-400 transition-all">
                        Battle Royale
                    </button>
                    <button onclick="filterCategory('sci-fi', this)" class="cat-btn px-4 py-2 text-xs font-bold uppercase tracking-wider rounded border border-slate-800 bg-slate-900 text-slate-300 hover:border-cyan-400 hover:text-cyan-400 transition-all">
                        Sci-Fi Ninja
                    </button>
                    <button onclick="filterCategory('rpg-horror', this)" class="cat-btn px-4 py-2 text-xs font-bold uppercase tracking-wider rounded border border-slate-800 bg-slate-900 text-slate-300 hover:border-cyan-400 hover:text-cyan-400 transition-all">
                        Gothic Horror
                    </button>
                </div>
            </div>

            <!-- Dynamic Category Game Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6" id="category-games-grid">
                <!-- Loaded dynamically -->
            </div>
        </div>
    </section>

    <section id="contact" class="py-12 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto w-full relative">
        <div class="relative bg-gradient-to-b from-slate-900 via-slate-950 to-black border-2 border-amber-400/50 rounded-2xl p-6 sm:p-10 shadow-[0_0_35px_rgba(255,234,0,0.15)] overflow-hidden">
            
            <!-- Mandatory Badge Top-Left -->
            <div class="absolute top-0 left-0 bg-gradient-to-r from-amber-400 via-yellow-400 to-amber-500 text-black px-6 py-2.5 rounded-br-2xl font-extrabold text-sm uppercase tracking-widest flex items-center gap-2 shadow-[0_4px_15px_rgba(255,234,0,0.4)] z-20">
                <i class="fa-solid fa-location-dot text-black animate-bounce"></i> ติดต่อเราที่นี้
            </div>

            <div class="mt-8 pt-4 grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
                <div>
                    <span class="text-xs font-mono text-amber-400 uppercase tracking-widest block mb-1">
                        Get In Touch // 24/7 Channel
                    </span>
                    <h2 class="text-3xl font-extrabold text-white mb-4">
                        ข้อมูลการติดต่อผู้ดูแล <span class="text-amber-400 glow-yellow">(Contact Info)</span>
                    </h2>
                    <p class="text-slate-300 text-sm mb-6 leading-relaxed font-light">
                        หากคุณต้องการสอบถามข้อมูลเพิ่มเติม ข้อเสนอแนะเกี่ยวกับเกม หรือติดต่อทีมงานผู้ดูแลเว็บไซต์ สามารถติดต่อเราได้ตามช่องทางโซเชียลมีเดียด้านล่างนี้
                    </p>

                    <!-- Contact Details Cards Grid -->
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                        <!-- Facebook Card -->
                        <div class="p-4 bg-slate-900/90 border border-blue-500/40 rounded-xl flex items-center justify-between hover:border-blue-400 hover:shadow-[0_0_15px_rgba(59,130,246,0.3)] transition-all">
                            <div class="flex items-center gap-3.5">
                                <div class="w-11 h-11 rounded-lg bg-blue-600/20 text-blue-400 border border-blue-500/40 flex items-center justify-center text-xl shrink-0">
                                    <i class="fa-brands fa-facebook-f"></i>
                                </div>
                                <div>
                                    <div class="text-[10px] text-slate-400 uppercase font-mono">Facebook</div>
                                    <div class="font-bold text-white text-sm">Pig Fry</div>
                                </div>
                            </div>
                            <button onclick="copyToClipboard('Pig Fry', 'Facebook')" class="text-xs px-2.5 py-1 bg-slate-800 hover:bg-blue-600 text-slate-300 hover:text-white rounded font-mono transition-colors">
                                <i class="fa-regular fa-copy"></i>
                            </button>
                        </div>

                        <!-- Instagram Card -->
                        <div class="p-4 bg-slate-900/90 border border-pink-500/40 rounded-xl flex items-center justify-between hover:border-pink-400 hover:shadow-[0_0_15px_rgba(236,72,153,0.3)] transition-all">
                            <div class="flex items-center gap-3.5">
                                <div class="w-11 h-11 rounded-lg bg-pink-600/20 text-pink-400 border border-pink-500/40 flex items-center justify-center text-xl shrink-0">
                                    <i class="fa-brands fa-instagram"></i>
                                </div>
                                <div>
                                    <div class="text-[10px] text-slate-400 uppercase font-mono">Instagram (IG)</div>
                                    <div class="font-bold text-white text-sm">zanis_7415</div>
                                </div>
                            </div>
                            <button onclick="copyToClipboard('zanis_7415', 'Instagram')" class="text-xs px-2.5 py-1 bg-slate-800 hover:bg-pink-600 text-slate-300 hover:text-white rounded font-mono transition-colors">
                                <i class="fa-regular fa-copy"></i>
                            </button>
                        </div>

                        <!-- Line Card -->
                        <div class="p-4 bg-slate-900/90 border border-emerald-500/40 rounded-xl flex items-center justify-between hover:border-emerald-400 hover:shadow-[0_0_15px_rgba(16,185,129,0.3)] transition-all">
                            <div class="flex items-center gap-3.5">
                                <div class="w-11 h-11 rounded-lg bg-emerald-600/20 text-emerald-400 border border-emerald-500/40 flex items-center justify-center text-xl shrink-0">
                                    <i class="fa-brands fa-line"></i>
                                </div>
                                <div>
                                    <div class="text-[10px] text-slate-400 uppercase font-mono">Line ID</div>
                                    <div class="font-bold text-white text-sm">พี่บ่าวเกย์</div>
                                </div>
                            </div>
                            <button onclick="copyToClipboard('พี่บ่าวเกย์', 'Line')" class="text-xs px-2.5 py-1 bg-slate-800 hover:bg-emerald-600 text-slate-300 hover:text-white rounded font-mono transition-colors">
                                <i class="fa-regular fa-copy"></i>
                            </button>
                        </div>

                        <!-- Phone Card -->
                        <div class="p-4 bg-slate-900/90 border border-amber-500/40 rounded-xl flex items-center justify-between hover:border-amber-400 hover:shadow-[0_0_15px_rgba(245,158,11,0.3)] transition-all">
                            <div class="flex items-center gap-3.5">
                                <div class="w-11 h-11 rounded-lg bg-amber-600/20 text-amber-400 border border-amber-500/40 flex items-center justify-center text-xl shrink-0">
                                    <i class="fa-solid fa-phone-flip"></i>
                                </div>
                                <div>
                                    <div class="text-[10px] text-slate-400 uppercase font-mono">เบอร์โทรศัพท์</div>
                                    <div class="font-bold text-amber-300 font-mono text-sm">0948683913</div>
                                </div>
                            </div>
                            <button onclick="copyToClipboard('0948683913', 'เบอร์โทรศัพท์')" class="text-xs px-2.5 py-1 bg-slate-800 hover:bg-amber-500 hover:text-black text-slate-300 rounded font-mono transition-colors">
                                <i class="fa-regular fa-copy"></i>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Quick Message Form -->
                <div class="bg-slate-950/90 p-6 rounded-xl border border-amber-400/20 shadow-inner flex flex-col justify-between h-full">
                    <div>
                        <div class="flex items-center justify-between mb-4 pb-2 border-b border-slate-800">
                            <h3 class="text-base font-bold text-white flex items-center gap-2">
                                <i class="fa-solid fa-envelope-open-text text-amber-400"></i> ส่งข้อความด่วน
                            </h3>
                            <span class="text-[11px] font-mono text-amber-400/80">TERMINAL v2.6</span>
                        </div>
                        <div class="space-y-3">
                            <input type="text" id="sender-name" placeholder="ชื่อ หรือ อีเมลของคุณ..." class="w-full bg-slate-900 border border-slate-800 rounded p-3 text-sm text-white focus:outline-none focus:border-amber-400 transition-colors">
                            <textarea id="sender-message" rows="3" placeholder="ข้อความที่ต้องการส่ง..." class="w-full bg-slate-900 border border-slate-800 rounded p-3 text-sm text-white focus:outline-none focus:border-amber-400 transition-colors resize-none"></textarea>
                        </div>
                    </div>
                    <button onclick="sendMessage()" class="mt-4 w-full py-3 bg-amber-400 hover:bg-yellow-300 text-black font-extrabold uppercase rounded text-xs tracking-wider transition-all shadow-[0_0_20px_rgba(255,234,0,0.3)] flex items-center justify-center gap-2">
                        <i class="fa-solid fa-paper-plane"></i> ส่งข้อความทันที
                    </button>
                    <div id="toast-msg" class="text-xs text-center font-mono mt-3 text-emerald-400 hidden"></div>
                </div>
            </div>
        </div>
    </section>

    <footer class="mt-16 bg-slate-950 border-t border-cyan-500/30 py-8 px-4 sm:px-6 lg:px-8 w-full">
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row items-center justify-between gap-6 text-center md:text-left">
            <div>
                <div class="text-lg font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 via-pink-500 to-amber-400 mb-1 font-rajdhani">
                    GAMEX FUTURISTIC SHOWCASE
                </div>
                <!-- Mandatory Student Credits -->
                <p class="text-sm font-semibold text-slate-200">
                    จัดทำโดย นายวีระวิทย์ มูลลักษณ์ ชั้นมัธยมศึกษาปีที่ 5/3 โรงเรียนมัธยมนาคนาวาอุปถัมภ์
                </p>
            </div>
            <div class="text-xs text-slate-400 font-mono flex flex-col md:items-end gap-1">
                <div>© 2026 ALL RIGHTS RESERVED. CYBERPUNK EDITION</div>
                <div class="text-cyan-400"><i class="fa-solid fa-code text-pink-400"></i> NAKNAVA DIGITAL MEDIA LAB</div>
            </div>
        </div>
    </footer>

    <div id="game-modal" class="fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/80 backdrop-blur-md hidden transition-all duration-300 opacity-0">
        <div class="relative bg-slate-900 border-2 border-cyan-400 rounded-2xl max-w-4xl w-full overflow-hidden shadow-[0_0_60px_rgba(0,243,255,0.3)] cyber-clip">
            
            <!-- Modal Header -->
            <div class="bg-slate-950 px-6 py-4 border-b border-cyan-500/30 flex items-center justify-between">
                <div class="flex items-center gap-3">
                    <span class="w-3 h-3 rounded-full bg-cyan-400 animate-ping"></span>
                    <h3 id="modal-title" class="text-xl font-extrabold text-white tracking-wide">
                        GAME TITLE
                    </h3>
                </div>
                <button onclick="closeModal()" class="w-9 h-9 bg-slate-800 hover:bg-pink-600 text-slate-300 hover:text-white rounded-lg flex items-center justify-center transition-colors">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <!-- Modal Content Body -->
            <div class="p-6 max-h-[80vh] overflow-y-auto space-y-6">
                <!-- Video Container -->
                <div class="relative w-full aspect-video rounded-xl overflow-hidden border border-cyan-500/40 bg-black shadow-lg">
                    <iframe id="modal-video" class="w-full h-full" src="" title="Game Trailer" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                </div>

                <!-- Details Grid -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <div class="md:col-span-2 space-y-3">
                        <div class="text-xs font-mono text-cyan-400 uppercase tracking-widest flex items-center gap-2">
                            <i class="fa-solid fa-circle-info"></i> รายละเอียดเกม (Game Overview)
                        </div>
                        <p id="modal-description" class="text-slate-300 text-sm leading-relaxed font-light">
                            คำอธิบายเกม...
                        </p>
                    </div>

                    <div class="bg-slate-950 p-4 rounded-xl border border-slate-800 space-y-3 font-mono text-xs">
                        <div class="text-slate-400 uppercase font-bold text-xs border-b border-slate-800 pb-1.5 flex items-center justify-between">
                            <span>ข้อมูลเกม</span>
                            <i class="fa-solid fa-database text-cyan-400"></i>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-400">หมวดหมู่:</span>
                            <span id="modal-category" class="text-cyan-400 font-bold">Action</span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-400">คะแนนรีวิว:</span>
                            <span id="modal-rating" class="text-yellow-400 font-bold">9.8 / 10</span>
                        </div>
                        <div class="flex justify-between">
                            <span class="text-slate-400">รองรับระบบ:</span>
                            <span class="text-slate-200">PC / Console / Mobile</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Modal Footer -->
            <div class="bg-slate-950 px-6 py-3 border-t border-slate-800 flex justify-end">
                <button onclick="closeModal()" class="px-5 py-2 bg-slate-800 hover:bg-slate-700 text-slate-300 text-xs font-bold uppercase rounded">
                    ปิดหน้าต่าง
                </button>
            </div>
        </div>
    </div>

    <script>
        // Game Database with exact official image artworks corresponding to the prompt
        const gameDatabase = [
            {
                id: 'bloodborne',
                title: 'Bloodborne',
                categoryKey: 'rpg-horror',
                categoryName: 'Action / Gothic Horror',
                description: 'เกมแอ็คชั่น RPG สไตล์ Gothic Horror สุดท้าทาย ออกล่าอสูรกายและไขความลับอันมืดมนในเมือง Yharnam ที่สาปสูญ',
                poster: 'https://image.api.playstation.com/vulcan/img/rnd/202010/2614/NVmnBXze9ElHzU6SmykrJLIV.png',
                videoUrl: 'https://www.youtube.com/embed/StzwspHQ544',
                rating: '9.8 / 10',
                badgeColor: 'border-pink-500 text-pink-400'
            },
            {
                id: 'warframe',
                title: 'Warframe',
                categoryKey: 'sci-fi',
                categoryName: 'Action / Sci-Fi Ninja',
                description: 'เกมแอ็คชั่น Sci-Fi นินจาอวกาศ เล่นฟรี ต่อสู้แบบร่วมมือกัน ยิงและฟันด้วยความเร็วสูง พัฒนาชุดเกราะ Warframe สุดล้ำยุค',
                poster: 'https://m.media-amazon.com/images/M/MV5BNzQxMzYwOTQtMzU4Ni00YzdkLWIzNGMtYTJmY2JmMTFmZGViXkEyXkFqcGc@._V1_FMjpg_UX1000_.jpg',
                videoUrl: 'https://www.youtube.com/embed/4sP3RtN9TeU',
                rating: '9.6 / 10',
                badgeColor: 'border-purple-400 text-purple-400'
            },
            {
                id: 'pubg',
                title: 'PUBG Mobile',
                categoryKey: 'battle-royale',
                categoryName: 'Action / Battle Royale',
                description: 'เกมแอ็คชั่นแบทเทิลรอยัลยอดฮิต กระโดดร่มลงสู่เกาะร้าง รวบรวมอาวุธยุทโธปกรณ์ และต่อสู้เอาชีวิตรอดเพื่อเป็นผู้ชนะคนสุดท้าย',
                poster: 'https://static0.xdaimages.com/wordpress/wp-content/uploads/2018/06/pubg.jpg?w=1200&h=675&fit=crop',
                videoUrl: 'https://www.youtube.com/embed/3XrB1UMYC-U',
                rating: '9.3 / 10',
                badgeColor: 'border-cyan-400 text-cyan-400'
            },
            {
                id: 'farcry3',
                title: 'Far Cry 3',
                categoryKey: 'open-world',
                categoryName: 'Action / Open World',
                description: 'เกมแอ็คชั่นโอเพ่นเวิลด์ในเกาะเขตร้อน ชายชื่อ Jason Brody ต้องเอาชีวิตรอดจากแก๊งโจรสลัดสุดคลั่ง นำโดย Vaas Montenegro',
                poster: 'https://cdn2.unrealengine.com/Diesel/productv2/far-cry-3/deluxe-edition/FC3-dlx-2560x1440-4fa7f35072ee54993b47cf163c2f4f0fd7b1759a.jpg',
                videoUrl: 'https://www.youtube.com/embed/GN563Yxar-o',
                rating: '9.5 / 10',
                badgeColor: 'border-yellow-400 text-yellow-400'
            },
            {
                id: 'gow',
                title: 'God of War Ragnarök',
                categoryKey: 'open-world',
                categoryName: 'Action / Epic Adventure',
                description: 'การผจญภัยครั้งยิ่งใหญ่ของ Kratos และ Atreus ในดินแดนเทพนอร์ส ต่อสู้เผชิญหน้ากับโชคชะตาและสงครามแร็กนาร็อก',
                poster: 'https://cdn1.epicgames.com/spt-assets/edaff839f0734d16bc89d2ddb1dc9339/steel-magnolia-15owu.jpg',
                videoUrl: 'https://www.youtube.com/embed/tO1qXLasEA8',
                rating: '9.9 / 10',
                badgeColor: 'border-amber-400 text-amber-400'
            },
            {
                id: 'justcause3',
                title: 'Just Cause 3',
                categoryKey: 'open-world',
                categoryName: 'Action / Open World',
                description: 'เกมแอ็คชั่นโอเพ่นเวิลด์จอมระเบิด Rico Rodriguez พร้อมเกราะปีกผาดโผนและตะขอเกี่ยว ออกปลดปล่อยเกาะ Medici จากเผด็จการ',
                poster: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSuETVz5ZFzoLD8E7gXVaPtY7fXSMIXeHnTEkK8UiCZcKFLmlVsslCP5scw&s=10',
                videoUrl: 'https://www.youtube.com/embed/0ND5dYIFkd0',
                rating: '9.2 / 10',
                badgeColor: 'border-red-400 text-red-400'
            }
        ];

        function buildGameCard(game) {
            return `
                <div class="group relative bg-slate-900/90 border border-slate-800 hover:border-cyan-400 rounded-xl overflow-hidden neon-card cyber-clip flex flex-col justify-between">
                    <div>
                        <!-- Cover Image with Fallback handling -->
                        <div class="relative aspect-video overflow-hidden bg-slate-950">
                            <img src="${game.poster}" 
                                 alt="${game.title}" 
                                 onerror="this.onerror=null; this.src='https://placehold.co/800x450/090d16/00f3ff?text=${encodeURIComponent(game.title)}';" 
                                 class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500 opacity-90 group-hover:opacity-100">
                            
                            <div class="absolute inset-0 bg-gradient-to-t from-slate-950 via-transparent to-transparent"></div>
                            
                            <!-- Rating Tag -->
                            <div class="absolute top-3 right-3 px-2.5 py-1 bg-slate-950/90 border ${game.badgeColor} text-xs font-mono font-bold rounded backdrop-blur-md shadow-md">
                                <i class="fa-solid fa-star text-yellow-400 mr-1"></i>${game.rating}
                            </div>
                        </div>

                        <!-- Card Information Body -->
                        <div class="p-5">
                            <span class="text-[10px] font-mono uppercase tracking-widest text-cyan-400 block mb-1">
                                ${game.categoryName}
                            </span>
                            <h3 class="text-xl font-extrabold text-white mb-2 group-hover:text-cyan-300 transition-colors">
                                ${game.title}
                            </h3>
                            <p class="text-slate-400 text-xs leading-relaxed line-clamp-3 font-light">
                                ${game.description}
                            </p>
                        </div>
                    </div>

                    <!-- Trigger Trailer Button -->
                    <div class="p-5 pt-0">
                        <button onclick="openModal('${game.id}')" class="w-full py-2.5 bg-slate-800/90 hover:bg-cyan-500 hover:text-black border border-cyan-500/40 text-cyan-300 text-xs font-bold uppercase tracking-wider rounded transition-all flex items-center justify-center gap-2 shadow-[0_0_15px_rgba(0,243,255,0.2)]">
                            <i class="fa-solid fa-circle-play text-sm"></i> ดูตัวอย่าง & รายละเอียด
                        </button>
                    </div>
                </div>
            `;
        }

        function renderActionGames(list = gameDatabase) {
            const actionGrid = document.getElementById('action-games-grid');
            if (list.length === 0) {
                actionGrid.innerHTML = `
                    <div class="col-span-full text-center py-12 text-slate-500 font-mono">
                        <i class="fa-solid fa-ban text-3xl mb-2 text-pink-500 block"></i>
                        ไม่พบเกมที่ค้นหา... กรุณาลองใช้คำค้นหาอื่น
                    </div>
                `;
                return;
            }
            actionGrid.innerHTML = list.map(game => buildGameCard(game)).join('');
        }

        function handleSearch() {
            const query = document.getElementById('game-search').value.toLowerCase().trim();
            const filtered = gameDatabase.filter(game => 
                game.title.toLowerCase().includes(query) || 
                game.description.toLowerCase().includes(query) ||
                game.categoryName.toLowerCase().includes(query)
            );
            renderActionGames(filtered);
        }

        function filterCategory(categoryKey, btn) {
            const categoryGrid = document.getElementById('category-games-grid');
            
            // Tab styling active toggle
            const buttons = document.querySelectorAll('.cat-btn');
            buttons.forEach(b => {
                b.classList.remove('bg-cyan-500', 'text-black', 'border-cyan-400', 'shadow-[0_0_12px_rgba(0,243,255,0.4)]');
                b.classList.add('bg-slate-900', 'text-slate-300', 'border-slate-800');
            });
            btn.classList.remove('bg-slate-900', 'text-slate-300', 'border-slate-800');
            btn.classList.add('bg-cyan-500', 'text-black', 'border-cyan-400', 'shadow-[0_0_12px_rgba(0,243,255,0.4)]');

            let filtered = gameDatabase;
            if (categoryKey !== 'all') {
                filtered = gameDatabase.filter(g => g.categoryKey === categoryKey);
            }

            categoryGrid.innerHTML = filtered.map(game => buildGameCard(game)).join('');
        }

        function openModal(gameId) {
            const game = gameDatabase.find(g => g.id === gameId);
            if (!game) return;

            document.getElementById('modal-title').innerText = game.title;
            document.getElementById('modal-description').innerText = game.description;
            document.getElementById('modal-category').innerText = game.categoryName;
            document.getElementById('modal-rating').innerText = game.rating;
            
            // Embed Youtube with Autoplay enabled
            const modalVideo = document.getElementById('modal-video');
            modalVideo.src = `${game.videoUrl}?autoplay=1`;

            const modal = document.getElementById('game-modal');
            modal.classList.remove('hidden');
            setTimeout(() => {
                modal.classList.remove('opacity-0');
            }, 10);
        }

        function closeModal() {
            const modal = document.getElementById('game-modal');
            const modalVideo = document.getElementById('modal-video');
            modal.classList.add('opacity-0');
            setTimeout(() => {
                modalVideo.src = ''; // Stop sound
                modal.classList.add('hidden');
            }, 300);
        }

        function copyToClipboard(text, typeName) {
            const tempInput = document.createElement('input');
            tempInput.value = text;
            document.body.appendChild(tempInput);
            tempInput.select();
            document.execCommand('copy');
            document.body.removeChild(tempInput);

            showToast(`คัดลอก ${typeName} (${text}) เรียบร้อยแล้ว!`);
        }

        function sendMessage() {
            const name = document.getElementById('sender-name').value.trim();
            const msg = document.getElementById('sender-message').value.trim();
            if(!name || !msg) {
                showToast('กรุณากรอกชื่อและข้อความให้ครบถ้วน', true);
                return;
            }
            document.getElementById('sender-name').value = '';
            document.getElementById('sender-message').value = '';
            showToast('ส่งข้อความถึงทีมงานเรียบร้อยแล้ว ขอบคุณครับ!');
        }

        function showToast(message, isError = false) {
            const toast = document.getElementById('toast-msg');
            toast.innerText = message;
            toast.className = `text-xs text-center font-mono mt-3 ${isError ? 'text-pink-400' : 'text-emerald-400'} block animate-pulse`;
            setTimeout(() => {
                toast.className = 'text-xs text-center font-mono mt-3 hidden';
            }, 3000);
        }

        function initCyberCanvas() {
            const canvas = document.getElementById('bg-canvas');
            const ctx = canvas.getContext('2d');

            let width = canvas.width = window.innerWidth;
            let height = canvas.height = window.innerHeight;

            window.addEventListener('resize', () => {
                width = canvas.width = window.innerWidth;
                height = canvas.height = window.innerHeight;
            });

            // Particles Array
            const particles = [];
            const particleCount = 45;

            for (let i = 0; i < particleCount; i++) {
                particles.push({
                    x: Math.random() * width,
                    y: Math.random() * height,
                    size: Math.random() * 2 + 1,
                    speedX: (Math.random() - 0.5) * 0.8,
                    speedY: (Math.random() - 0.5) * 0.8,
                    color: Math.random() > 0.5 ? 'rgba(0, 243, 255, ' : 'rgba(255, 0, 85, '
                });
            }

            function draw() {
                ctx.clearRect(0, 0, width, height);

                // Draw perspective grid line effect
                ctx.strokeStyle = 'rgba(0, 243, 255, 0.04)';
                ctx.lineWidth = 1;

                const gridSpacing = 50;
                for (let x = 0; x < width; x += gridSpacing) {
                    ctx.beginPath();
                    ctx.moveTo(x, 0);
                    ctx.lineTo(x, height);
                    ctx.stroke();
                }
                for (let y = 0; y < height; y += gridSpacing) {
                    ctx.beginPath();
                    ctx.moveTo(0, y);
                    ctx.lineTo(width, y);
                    ctx.stroke();
                }

                // Render moving glowing particles
                particles.forEach(p => {
                    p.x += p.speedX;
                    p.y += p.speedY;

                    if (p.x < 0) p.x = width;
                    if (p.x > width) p.x = 0;
                    if (p.y < 0) p.y = height;
                    if (p.y > height) p.y = 0;

                    ctx.fillStyle = p.color + '0.6)';
                    ctx.beginPath();
                    ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                    ctx.fill();
                });

                requestAnimationFrame(draw);
            }

            draw();
        }

        // On Page Load Event Listener
        window.onload = function() {
            initCyberCanvas();
            renderActionGames();
            filterCategory('all', document.querySelector('.cat-btn'));
        };
    </script>
</body>
</html>
