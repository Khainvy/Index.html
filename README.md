<!DOCTYPE html>
<html lang="id" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nihiluxxy - Platform Belajar Super SMA, TKA & UTBK SNBT 2026</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#f5f3ff',
                            100: '#ede9fe',
                            200: '#ddd6fe',
                            300: '#c4b5fd',
                            400: '#a78bfa',
                            500: '#8b5cf6',
                            600: '#7c3aed',
                            700: '#6d28d9',
                            800: '#5b21b6',
                            900: '#4c1d95',
                            950: '#2e1065',
                        }
                    },
                    fontFamily: {
                        sans: ['Plus Jakarta Sans', 'sans-serif'],
                        mono: ['JetBrains Mono', 'monospace'],
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;600;700&display=swap" rel="stylesheet">
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        body { 
            font-family: 'Plus Jakarta Sans', sans-serif; 
            background-color: #090d16;
        }
        .gradient-brand { background: linear-gradient(135deg, #0b132b 0%, #1c2541 40%, #3a506b 100%); }
        .gradient-accent { background: linear-gradient(135deg, #6366f1 0%, #a855f7 50%, #ec4899 100%); }
        .gradient-card { background: linear-gradient(145deg, rgba(30, 41, 59, 0.7) 0%, rgba(15, 23, 42, 0.8) 100%); }
        .glass-header { background: rgba(9, 13, 22, 0.88); backdrop-filter: blur(16px); }
        .glass-card { background: rgba(30, 41, 59, 0.4); backdrop-filter: blur(10px); border: 1px solid rgba(255, 255, 255, 0.08); }
        .custom-scrollbar::-webkit-scrollbar { width: 6px; height: 6px; }
        .custom-scrollbar::-webkit-scrollbar-track { background: rgba(15, 23, 42, 0.6); }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: rgba(139, 92, 246, 0.3); border-radius: 9999px; }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover { background: rgba(139, 92, 246, 0.6); }
    </style>
</head>
<body class="bg-[#090d16] text-slate-100 min-h-screen flex flex-col selection:bg-purple-500 selection:text-white custom-scrollbar">

    <!-- Top Navigation Banner -->
    <div class="bg-gradient-to-r from-purple-900 via-indigo-900 to-slate-900 text-xs py-1.5 px-4 text-center font-medium border-b border-purple-500/20 text-purple-200 flex justify-between items-center">
        <span class="hidden sm:inline">⚡ Edisi Pengayaan Lengkap: Persiapan Menghadapi SNBT 2026 & Ujian Sekolah SMA</span>
        <span class="mx-auto sm:mx-0">🎉 Sambut Kurikulum Merdeka & K13 Revisi Terintegrasi</span>
        <div class="hidden md:flex gap-4 text-[11px] font-semibold text-purple-300">
            <span>v3.5 Super Edition</span>
            <span>•</span>
            <span id="live-clock">--:--:-- WIB</span>
        </div>
    </div>

    <!-- Header Navigation Bar -->
    <header class="sticky top-0 z-50 glass-header border-b border-slate-800/80 transition-all duration-300">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between gap-4">
            <!-- Brand Logo -->
            <div class="flex items-center gap-3 cursor-pointer group" onclick="switchView('home')">
                <div class="w-11 h-11 rounded-2xl gradient-accent flex items-center justify-center text-white font-black text-xl shadow-lg shadow-purple-500/25 group-hover:scale-105 transition duration-300">
                    <i data-lucide="sparkles" class="w-6 h-6"></i>
                </div>
                <div class="flex flex-col">
                    <div class="flex items-center gap-1.5">
                        <span class="text-2xl font-black tracking-tight text-white group-hover:text-purple-300 transition">Nihiluxxy</span>
                        <span class="w-2 h-2 rounded-full bg-purple-500 animate-pulse"></span>
                    </div>
                    <span class="text-[9px] uppercase tracking-widest text-purple-400 font-extrabold -mt-1">Super Learning Engine</span>
                </div>
            </div>

            <!-- Search Bar Desktop -->
            <div class="hidden lg:flex items-center flex-1 max-w-md mx-6">
                <div class="relative w-full">
                    <i data-lucide="search" class="w-4 h-4 absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400"></i>
                    <input type="text" id="global-search" oninput="handleGlobalSearch(this.value)" placeholder="Cari materi (misal: Eksponen, Integral, Genetik)..." class="w-full bg-slate-900/90 border border-slate-700/80 rounded-2xl pl-10 pr-4 py-2 text-xs text-slate-200 focus:outline-none focus:border-purple-500 transition">
                    <div id="search-results-popover" class="hidden absolute left-0 right-0 top-12 bg-slate-900 border border-slate-700 rounded-2xl shadow-2xl p-2 z-50 max-h-80 overflow-y-auto custom-scrollbar"></div>
                </div>
            </div>

            <!-- Desktop Nav Items -->
            <nav class="hidden md:flex items-center gap-1 bg-slate-900/80 p-1.5 rounded-2xl border border-slate-800 text-xs font-semibold">
                <button onclick="switchView('home')" id="nav-home" class="px-4 py-2.5 rounded-xl text-white bg-purple-600 transition flex items-center gap-1.5">
                    <i data-lucide="home" class="w-4 h-4"></i> Beranda
                </button>
                <button onclick="switchView('materi')" id="nav-materi" class="px-4 py-2.5 rounded-xl text-slate-300 hover:text-white transition flex items-center gap-1.5">
                    <i data-lucide="book-open" class="w-4 h-4"></i> Modul SMA
                </button>
                <button onclick="switchView('utbk')" id="nav-utbk" class="px-4 py-2.5 rounded-xl text-slate-300 hover:text-white transition flex items-center gap-1.5">
                    <i data-lucide="award" class="w-4 h-4 text-amber-400"></i>
                    <span>Simulasi UTBK/TKA</span>
                </button>
                <button onclick="switchView('riwayat')" id="nav-riwayat" class="px-4 py-2.5 rounded-xl text-slate-300 hover:text-white transition flex items-center gap-1.5">
                    <i data-lucide="history" class="w-4 h-4 text-purple-400"></i>
                    <span>Riwayat Hasil</span>
                </button>
            </nav>

            <!-- User Status Header Badge -->
            <div class="flex items-center gap-3">
                <div class="hidden sm:flex flex-col text-right">
                    <span class="text-[10px] text-slate-400 font-medium">Status Kurikulum</span>
                    <span class="text-xs font-extrabold text-emerald-400 flex items-center justify-end gap-1">
                        <span class="w-1.5 h-1.5 rounded-full bg-emerald-400"></span> K13 & Merdeka Active
                    </span>
                </div>
                <div class="w-10 h-10 rounded-2xl bg-slate-800 border border-slate-700 flex items-center justify-center font-bold text-xs text-purple-300 shadow-inner">
                    NX
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content Dynamic Container -->
    <main id="app-content" class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <!-- Rendered dynamically by JS Engine -->
    </main>

    <!-- Mobile Navigation Bottom Bar -->
    <div class="md:hidden fixed bottom-0 left-0 right-0 glass-header border-t border-slate-800/80 flex justify-around py-2.5 text-[10px] font-semibold text-slate-400 z-50 backdrop-blur-lg">
        <button onclick="switchView('home')" id="mob-home" class="flex flex-col items-center gap-1 text-purple-400">
            <i data-lucide="home" class="w-5 h-5"></i> Beranda
        </button>
        <button onclick="switchView('materi')" id="mob-materi" class="flex flex-col items-center gap-1">
            <i data-lucide="book-open" class="w-5 h-5"></i> Materi SMA
        </button>
        <button onclick="switchView('utbk')" id="mob-utbk" class="flex flex-col items-center gap-1">
            <i data-lucide="award" class="w-5 h-5"></i> UTBK/TKA
        </button>
        <button onclick="switchView('riwayat')" id="mob-riwayat" class="flex flex-col items-center gap-1">
            <i data-lucide="history" class="w-5 h-5"></i> Riwayat
        </button>
    </div>

    <!-- Application Footer -->
    <footer class="mt-auto border-t border-slate-800/80 bg-slate-950/60 py-8 text-xs text-slate-400">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col md:flex-row justify-between items-center gap-4">
            <div class="flex items-center gap-2">
                <div class="w-6 h-6 rounded-lg gradient-accent flex items-center justify-center text-white text-xs font-bold">N</div>
                <span class="font-extrabold text-slate-200">Nihiluxxy Platform Edition</span>
                <span class="text-slate-600">|</span>
                <span>Hak Cipta &copy; 2026. Seluruh Materi Terverifikasi Akademik.</span>
            </div>
            <div class="flex gap-6 text-slate-400">
                <a href="#" class="hover:text-purple-400 transition">Panduan Pengguna</a>
                <a href="#" class="hover:text-purple-400 transition">Bank Soal HOTS</a>
                <a href="#" class="hover:text-purple-400 transition">Kebijakan Privasi</a>
            </div>
        </div>
    </footer>

    <!-- JS Application Engine -->
    <script>
        // Realtime Clock Update
        setInterval(() => {
            const now = new Date();
            const timeStr = now.toLocaleTimeString('id-ID') + ' WIB';
            const clockEl = document.getElementById('live-clock');
            if (clockEl) clockEl.innerText = timeStr;
        }, 1000);

        // Core Application State
        const state = {
            activeView: 'home',
            selectedKurikulum: 'Merdeka',
            selectedSubject: 'mat',
            attempts: JSON.parse(localStorage.getItem('nihiluxxy_attempts') || '[]'),
            currentSimAnswers: {},
            activeSimKey: null
        };

        // Database Super Engine (SMA Classes 10-12 & UTBK SNBT 2026)
        const db = {
            mapel: [
                { id: 'mat', nama: 'Matematika Wajib & Lanjut', icon: 'calculator', color: 'from-blue-600 to-cyan-500', k13: 'Kelas 10-12 IPA/IPS', merdeka: 'Fase E & F (Wajib & Tingkat Lanjut)' },
                { id: 'fis', nama: 'Fisika', icon: 'zap', color: 'from-indigo-600 to-blue-500', k13: 'Kelas 10-12 IPA', merdeka: 'Fase F (Peminatan Sains)' },
                { id: 'kim', nama: 'Kimia', icon: 'flask-conical', color: 'from-purple-600 to-pink-500', k13: 'Kelas 10-12 IPA', merdeka: 'Fase F (Peminatan Sains)' },
                { id: 'bio', nama: 'Biologi', icon: 'dna', color: 'from-emerald-600 to-teal-500', k13: 'Kelas 10-12 IPA', merdeka: 'Fase F (Peminatan Sains)' },
                { id: 'eko', nama: 'Ekonomi & Akuntansi', icon: 'trending-up', color: 'from-amber-600 to-yellow-500', k13: 'Kelas 10-12 IPS', merdeka: 'Fase F (Peminatan Sosial)' },
                { id: 'sos', nama: 'Sosiologi', icon: 'users', color: 'from-rose-600 to-red-500', k13: 'Kelas 10-12 IPS', merdeka: 'Fase F (Peminatan Sosial)' },
                { id: 'geo', nama: 'Geografi', icon: 'globe', color: 'from-teal-600 to-emerald-500', k13: 'Kelas 10-12 IPS', merdeka: 'Fase F (Peminatan Sosial)' },
                { id: 'lit', nama: 'Literasi Bahasa & Penalaran', icon: 'book-marked', color: 'from-orange-600 to-amber-500', k13: 'Wajib Semua Jurusan', merdeka: 'Fase E & F (General Literacy)' }
            ],
            materiDetails: {
                'mat': [
                    {
                        title: '1. Eksponen, Bentuk Akar & Logaritma (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Menguasai konsep dasar perpangkatan berpangkat bulat dan rasional, sifat-sifat merasionalkan bentuk akar, serta operasi dasar logaritma sebagai balikan dari fungsi eksponensial.',
                        visual: 'ᵃlog(b·c) = ᵃlog b + ᵃlog c | ᵃlog(b/c) = ᵃlog b - ᵃlog c | ᵃlog bⁿ = n · ᵃlog b',
                        tips: 'Jika ada soal persamaan eksponen a^(f(x)) = a^(g(x)), maka langsung samakan pangkatnya f(x) = g(x) selama alas a > 0 dan a ≠ 1.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Jika ᵃlog b + ᵃlog b² = 12, tentukan nilai dari ᵃlog(a·b).<br><br><strong>Pembahasan Terperinci:</strong><br>1. Gunakan sifat ᵃlog bⁿ = n · ᵃlog b:<br>&nbsp;&nbsp;&nbsp;ᵃlog b + 2 · ᵃlog b = 12 ⇒ 3 · ᵃlog b = 12 ⇒ ᵃlog b = 4.<br>2. Hitung ᵃlog(a·b) dengan sifat penjumlahan logaritma:<br>&nbsp;&nbsp;&nbsp;ᵃlog(a·b) = ᵃlog a + ᵃlog b = 1 + 4 = 5.'
                    },
                    {
                        title: '2. Persamaan Kuadrat & Fungsi Kuadrat (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Menganalisis sifat-sifat persamaan kuadrat ax² + bx + c = 0, menggunakan diskriminan D = b² - 4ac, sifat akar-akar Vieta, serta sketsa grafik parabola fungsi kuadrat.',
                        visual: 'Akar Vieta: x₁ + x₂ = -b/a | x₁·x₂ = c/a | Puncak: (-b/2a, -D/4a)',
                        tips: 'Syarat parabola memotong sumbu-X di dua titik berbeda adalah D > 0. Jika D = 0 menyinggung sumbu-X, dan D < 0 tidak memotong sumbu-X.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Persamaan x² - (k + 2)x + 16 = 0 memiliki dua akar kembar positif. Nilai k yang memenuhi adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Syarat akar kembar: D = 0 ⇒ b² - 4ac = 0<br>&nbsp;&nbsp;&nbsp;(-(k + 2))² - 4(1)(16) = 0 ⇒ (k + 2)² = 64 ⇒ k + 2 = ±8.<br>&nbsp;&nbsp;&nbsp;Sehingga k = 6 atau k = -10.<br>2. Syarat akar positif: x₁ + x₂ > 0 ⇒ -b/a > 0 ⇒ (k + 2) > 0 ⇒ k > -2.<br>3. Nilai k yang memenuhi syarat k > -2 adalah k = 6.'
                    },
                    {
                        title: '3. Sistem Persamaan & Pertidaksamaan Linear (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Penyelesaian SPLDV, SPLTV, dan program linear untuk memaksimumkan atau meminimumkan fungsi objektif menggunakan metode uji titik pojok.',
                        visual: 'Z = ax + by | Garis Selidik ax + by = k',
                        tips: 'Dalam membuat daerah himpunan penyelesaian, pastikan menguji titik (0,0) untuk mempermudah penentuan arah arsiran.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Tentukan nilai maksimum dari f(x, y) = 3x + 4y pada daerah penyelesaian x + y ≤ 5, x ≥ 0, y ≥ 0.<br><br><strong>Pembahasan Terperinci:</strong><br>1. Titik pojok daerah penyelesaian: (0,0), (5,0), dan (0,5).<br>2. Uji titik ke f(x, y):<br>&nbsp;&nbsp;&nbsp;f(0,0) = 0<br>&nbsp;&nbsp;&nbsp;f(5,0) = 3(5) + 0 = 15<br>&nbsp;&nbsp;&nbsp;f(0,5) = 0 + 4(5) = 20<br>3. Nilai maksimum adalah 20 pada titik (0,5).'
                    },
                    {
                        title: '4. Matriks & Operasi Matriks (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Operasi penjumlahan, pengurangan, perkalian matriks, determinan matriks ordo 2x2 dan 3x3, serta sifat-sifat invers matriks.',
                        visual: 'Invers A⁻¹ = (1 / det A) · adj(A) | (A · B)⁻¹ = B⁻¹ · A⁻¹',
                        tips: 'Ingat bahwa perkalian matriks tidak bersifat komutatif: A × B ≠ B × A.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Jika A = [[2, 1], [4, 3]], tentukan determinan dari A⁻¹.<br><br><strong>Pembahasan Terperinci:</strong><br>1. Hitung det(A) = (2)(3) - (1)(4) = 6 - 4 = 2.<br>2. Gunakan sifat det(A⁻¹) = 1 / det(A).<br>3. Maka det(A⁻¹) = 1/2.'
                    },
                    {
                        title: '5. Vektor pada Ruang Dimensi Dua & Tiga (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Konsep dasar vektor, operasi aljabar vektor, perkalian skalar dua vektor (dot product), serta proyeksi ortogonal suatu vektor pada vektor lain.',
                        visual: 'u · v = |u||v| cos θ | Proyeksi skalar: |p| = (u · v) / |v|',
                        tips: 'Dua vektor saling tegak lurus (ortogonal) jika dan hanya jika hasil perkalian skalar u · v = 0.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Diketahui u = (3, 4) dan v = (1, -2). Berapakah hasil u · v?<br><br><strong>Pembahasan Terperinci:</strong><br>1. u · v = (3 × 1) + (4 × -2) = 3 - 8 = -5.'
                    },
                    {
                        title: '6. Trigonometri Analitis & Rumus Sudut (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Rumus jumlah dan selisih sudut, rumus sudut ganda, serta identitas trigonometri dasar untuk menyelesaikan persamaan trigonometri.',
                        visual: 'sin(A ± B) = sin A cos B ± cos A sin B | cos(2A) = cos²A - sin²A',
                        tips: 'Hafalkan nilai trigonometri sudut istimewa di Kuadran I (0°, 30°, 45°, 60°, 90°) sebagai fondasi dasar.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Tentukan nilai dari sin(75°).<br><br><strong>Pembahasan Terperinci:</strong><br>1. Pecah 75° menjadi (45° + 30°).<br>2. sin(45° + 30°) = sin 45° cos 30° + cos 45° sin 30°<br>&nbsp;&nbsp;&nbsp;= (1/2 √2)(1/2 √3) + (1/2 √2)(1/2)<br>&nbsp;&nbsp;&nbsp;= 1/4 √6 + 1/4 √2 = 1/4 (√6 + √2).'
                    },
                    {
                        title: '7. Barisan & Deret Aritmetika dan Geometri (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Menganalisis suku ke-n (Un) dan jumlah n suku pertama (Sn) pada barisan aritmetika, geometri, serta deret geometri tak hingga konvergen.',
                        visual: 'Aritmetika: Un = a + (n-1)b | Geometri: Un = a · rⁿ⁻¹ | Tak Hingga: S_∞ = a / (1 - r)',
                        tips: 'Deret geometri tak hingga hanya mempunyai jumlah (konvergen) jika rasio -1 < r < 1.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Tentukan jumlah deret geometri tak hingga 8 + 4 + 2 + 1 + ...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Suku pertama a = 8, rasio r = 4/8 = 1/2.<br>2. Karena |r| < 1, gunakan S_∞ = a / (1 - r) = 8 / (1 - 1/2) = 8 / (1/2) = 16.'
                    },
                    {
                        title: '8. Limit Fungsi Aljabar & Trigonometri (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Mencari nilai limit bentuk tak tentu (0/0, ∞/∞, ∞ - ∞) menggunakan metode faktorisasi, mengalikan sekawan, dan aturan L\'Hopital.',
                        visual: 'lim(x→0) sin(x)/x = 1 | lim(x→0) tan(ax)/bx = a/b | L\'Hopital: lim f(x)/g(x) = lim f\'(x)/g\'(x)',
                        tips: 'Jika setelah substitusi langsung menghasilkan 0/0, metode L\'Hopital (menurunkan pembilang dan penyebut) adalah cara tercepat.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Hitung lim(x→2) (x² - 4) / (x - 2).<br><br><strong>Pembahasan Terperinci:</strong><br>1. Turunkan pembilang (2x) dan penyebut (1).<br>2. Hitung lim(x→2) 2x / 1 = 2(2) = 4.'
                    },
                    {
                        title: '9. Turunan Fungsi (Diferensial) & Aplikasi (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Aturan rantai turunan, menentukan titik stasioner, nilai maksimum/minimum, garis singgung kurva, serta aplikasi fungsi naik/turun.',
                        visual: 'f(x) = u·v ⇒ f\'(x) = u\'v + uv\' | f(x) = u/v ⇒ f\'(x) = (u\'v - uv\') / v²',
                        tips: 'Fungsi f(x) naik jika f\'(x) > 0, dan fungsi turun jika f\'(x) < 0.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Tentukan titik stasioner dari f(x) = x³ - 3x.<br><br><strong>Pembahasan Terperinci:</strong><br>1. Cari f\'(x) = 3x² - 3 = 0 ⇒ 3(x² - 1) = 0 ⇒ x = 1 atau x = -1.<br>2. Titik stasioner terjadi di x = 1 dan x = -1.'
                    },
                    {
                        title: '10. Integral Tentu & Tak Tentu (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Antiturunan, teknik substitusi, integral parsial, serta penggunaan integral tentu untuk menghitung luas daerah di bawah kurva.',
                        visual: '∫ xⁿ dx = (1/(n+1)) xⁿ⁺¹ + C | Integral Parsial: ∫ u dv = uv - ∫ v du',
                        tips: 'Jangan lupa menambahkan konstanta +C pada pengerjaan integral tak tentu.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Hitung ∫ (3x² + 2x) dx.<br><br><strong>Pembahasan Terperinci:</strong><br>1. ∫ 3x² dx = x³, ∫ 2x dx = x².<br>2. Hasilnya adalah x³ + x² + C.'
                    }
                ],
                'fis': [
                    {
                        title: '1. Besaran, Satuan, Pengukuran & Vektor (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Penggunaan alat ukur jangka sorong & mikrometer sekrup, aturan angka penting, analisis dimensi, serta resultan gaya vektor.',
                        visual: 'Ketelitian: Jangka Sorong (0,1 mm) | Mikrometer Sekrup (0,01 mm)',
                        tips: 'Dalam penjumlahan angka penting, hasil akhir harus mengikuti jumlah angka dibelakang koma (desimal) paling sedikit.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Berapakah hasil pengukuran mikrometer sekrup jika skala utama menunjukkan 3,5 mm dan skala nonius 20?<br><br><strong>Pembahasan Terperinci:</strong><br>1. Hasil = Skala Utama + (Skala Nonius × 0,01 mm)<br>&nbsp;&nbsp;&nbsp;= 3,5 mm + (20 × 0,01 mm) = 3,5 + 0,20 = 3,70 mm.'
                    },
                    {
                        title: '2. Kinematika Gerak Lurus & Parabola (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Persamaan GLB, GLBB, gerak jatuh bebas, serta analisis komponen kecepatan dan jarak maksimum pada gerak parabola.',
                        visual: 'GLBB: vₜ = v₀ + a·t | s = v₀t + ½at² | vₜ² = v₀² + 2as',
                        tips: 'Pada titik tertinggi gerak parabola, kecepatan arah vertikal (V_y) sama dengan Nol.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Sebuah benda dilempar vertikal ke atas dengan kecepatan awal 20 m/s (g = 10 m/s²). Berapakah tinggi maksimumnya?<br><br><strong>Pembahasan Terperinci:</strong><br>1. Pada titik tertinggi, vₜ = 0.<br>2. Gunakan vₜ² = v₀² - 2gh ⇒ 0 = (20)² - 2(10)h ⇒ 20h = 400 ⇒ h = 20 meter.'
                    },
                    {
                        title: '3. Dinamika Gerak & Hukum Newton (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Penerapan Hukum I, II, dan III Newton pada sistem katrol, bidang miring kasar/licin, gaya gesek statis & kinetis, serta gaya sentripetal.',
                        visual: 'ΣF = m · a | f_g = μ · N | F_s = m · v² / r',
                        tips: 'Gaya normal (N) pada bidang miring bernilai N = m · g · cos(θ).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Benda bermassa 4 kg ditarik gaya horizontal 20 N pada lantai licin. Hitung percepatannya.<br><br><strong>Pembahasan Terperinci:</strong><br>1. ΣF = m · a ⇒ 20 = 4 · a ⇒ a = 5 m/s².'
                    },
                    {
                        title: '4. Usaha, Energi & Hukum Kekekalan Energi (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Konsep usaha W = F · s cos θ, energi kinetik, energi potensial gravitasi/pegas, dan Hukum Kekekalan Energi Mekanik.',
                        visual: 'W = ΔEK | EM = EP + EK | EP = m·g·h | EK = ½m·v²',
                        tips: 'Jika tidak ada gaya luar non-konservatif (seperti gesekan), Energi Mekanik sistem selalu konstan di setiap titik.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Benda bermassa 2 kg jatuh bebas dari ketinggian 10 m (g = 10 m/s²). Berapakah energi kinetiknya saat berada di ketinggian 2 m?<br><br><strong>Pembahasan Terperinci:</strong><br>1. EM₁ = EM₂ ⇒ EP₁ + 0 = EP₂ + EK₂<br>&nbsp;&nbsp;&nbsp;m·g·h₁ = m·g·h₂ + EK₂<br>&nbsp;&nbsp;&nbsp;(2)(10)(10) = (2)(10)(2) + EK₂ ⇒ 200 = 40 + EK₂ ⇒ EK₂ = 160 Joule.'
                    },
                    {
                        title: '5. Momentum, Impuls & Tumbukan (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Hubungan Impuls I = F · Δt dengan perubahan momentum, serta jenis tumbukan (lenting sempurna e=1, sebagian 0<e<1, dan tidak lenting sama sekali e=0).',
                        visual: 'p = m · v | I = Δp = m(v₂ - v₁) | e = -(v₁\' - v₂\') / (v₁ - v₂)',
                        tips: 'Pada tumbukan tidak lenting sama sekali, kedua benda akan bergabung dan bergerak dengan kecepatan yang sama setelah bertumbukan.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Benda A (2 kg, 4 m/s) menumbuk Benda B (3 kg, diam) secara tidak lenting sama sekali. Berapakah kecepatan keduanya setelah tumbukan?<br><br><strong>Pembahasan Terperinci:</strong><br>1. m_A v_A + m_B v_B = (m_A + m_B) v\'<br>&nbsp;&nbsp;&nbsp;(2)(4) + (3)(0) = (2 + 3) v\' ⇒ 8 = 5 v\' ⇒ v\' = 1,6 m/s.'
                    },
                    {
                        title: '6. Gelombang Bunyi & Gelombang Cahaya (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Persamaan gelombang berjalan, Efek Doppler pada bunyi, interferensi celah ganda Young, dan difraksi kisi cahaya.',
                        visual: 'Efek Doppler: f_p = ((v ± v_p) / (v ± v_s)) · f_s | d sin θ = n λ',
                        tips: 'Jika pendengar mendekati sumber bunyi, tanda v_p adalah Positif (+). Jika sumber mendekati pendengar, tanda v_s adalah Negatif (-).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Ambulans bergerak dengan kecepatan 20 m/s mendekati pengamat diam sambil membunyikan sirine 640 Hz. Jika cepat rambat bunyi 340 m/s, berapa frekuensi yang didengar pengamat?<br><br><strong>Pembahasan Terperinci:</strong><br>1. v_p = 0, v_s = -20 m/s (sumber mendekat).<br>2. f_p = (340 / (340 - 20)) × 640 = (340 / 320) × 640 = 680 Hz.'
                    },
                    {
                        title: '7. Termodinamika & Mesin Heat (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Hukum Ke Nol, Pertama, dan Kedua Termodinamika, proses isobarik, isokhorik, isotermal, adiabatik, serta efisiensi Mesin Carnot.',
                        visual: 'Q = ΔU + W | Efisiensi Carnot: η = (1 - T₂/T₁) × 100%',
                        tips: 'Dalam perhitungan rumus Mesin Carnot, satuan suhu Wajib diubah ke Kelvin (K = °C + 273).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Sebuah mesin Carnot bekerja antara suhu 600 K dan 300 K. Tentukan efisiensinya.<br><br><strong>Pembahasan Terperinci:</strong><br>1. η = (1 - 300/600) × 100% = (1 - 0,5) × 100% = 50%.'
                    },
                    {
                        title: '8. Listrik Statis & Listrik Dinamis (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Hukum Coulomb, medan listrik, potensial listrik, kapasitor, Hukum Ohm, dan Hukum Kirchhoff I & II pada rangkaian loop.',
                        visual: 'F = k · |q₁q₂| / r² | V = I · R | ΣE + Σ(I·R) = 0',
                        tips: 'Rangkaian hambatan seri bertindak sebagai pembagi tegangan, sedangkan paralel bertindak sebagai pembagi arus.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Dua muatan q₁ = +2 μC dan q₂ = +4 μC terpisah 3 cm (k = 9×10⁹ N m²/C²). Hitung gaya Coulombnya.<br><br><strong>Pembahasan Terperinci:</strong><br>1. r = 0,03 m = 3×10⁻² m.<br>2. F = (9×10⁹ × 2×10⁻⁶ × 4×10⁻⁶) / (3×10⁻²)² = 72×10⁻³ / 9×10⁻⁴ = 80 N.'
                    },
                    {
                        title: '9. Medan Magnetik & Induksi Elektromagnetik (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Hukum Biot-Savart, Gaya Lorentz, Hukum Faraday tentang induksi magnetik, serta prinsip kerja transformator (trafo).',
                        visual: 'Gaya Lorentz: F = B · I · L sin θ | Trafo: Vₚ/Vₛ = Nₚ/Nₛ = Iₛ/Iₚ',
                        tips: 'Gunakan Kaidah Tangan Kanan: Ibu jari (Arus I), Empat Jari (Medan B), Telapak Tangan (Gaya Lorentz F).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Sebuah trafo ideal memiliki lilitan primer 500 dan sekunder 1000. Jika tegangan primer 110 V, berapa tegangan sekunder?<br><br><strong>Pembahasan Terperinci:</strong><br>1. Vₛ = (Nₛ / Nₚ) × Vₚ = (1000 / 500) × 110 = 2 × 110 = 220 Volt.'
                    },
                    {
                        title: '10. Fisika Modern & Relativitas (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Efek fotolistrik, panjang gelombang de Broglie, teori relativitas khusus Einstein (dilatasi waktu & relativitas massa), serta reaksi diferensiasi inti atom.',
                        visual: 'E = h · f | Dilatasi Waktu: Δt = Δt₀ / √(1 - v²/c²) | E = m·c²',
                        tips: 'Efek fotolistrik membuktikan bahwa cahaya dapat berperilaku sebagai partikel (foton).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Foton dengan frekuensi 10¹⁵ Hz menghantam logam (h = 6,63 × 10⁻³⁴ J·s). Berapakah energi foton tersebut?<br><br><strong>Pembahasan Terperinci:</strong><br>1. E = h · f = (6,63 × 10⁻³⁴) × 10¹⁵ = 6,63 × 10⁻¹⁹ Joule.'
                    }
                ],
                'kim': [
                    {
                        title: '1. Struktur Atom & Tabel Periodik Unsur (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Perkembangan teori atom, bilangan kuantum (n, l, m, s), konfigurasi elektron kulit/subkulit, serta sifat-sifat periodik unsur (jari-jari, energi ionisasi, elektronegativitas).',
                        visual: 'Bilangan Kuantum: n (Utama), l (Azimut), m (Magnetik), s (Spin ±½)',
                        tips: 'Dalam satu periode dari kiri ke kanan, jari-jari atom semakin kecil sedangkan energi ionisasi cenderung semakin besar.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Tentukan empat bilangan kuantum elektron terakhir dari unsur ₁₁Na (1s² 2s² 2p⁶ 3s¹).<br><br><strong>Pembahasan Terperinci:</strong><br>1. Subkulit terakhir 3s¹.<br>2. n = 3, l = 0 (subkulit s), m = 0, s = +½.'
                    },
                    {
                        title: '2. Ikatan Kimia & Bentuk Molekul (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Ikatan ionik, kovalen polar/non-polar, ikatan logam, teori VSEPR, hibridisasi, serta kepolaran molekul.',
                        visual: 'Bentuk Molekul: AX₂ (Linear), AX₃ (Trigonal Planar), AX₄ (Tetrahedral)',
                        tips: 'Jika molekul memiliki pasangan elektron bebas (PEB) pada atom pusat, umumnya molekul tersebut bersifat POLAR.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Bentuk molekul dari CH₄ (nomor atom C=6, H=1) menurut teori VSEPR adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Atom pusat C memiliki 4 elektron valensi.<br>2. Mengikat 4 atom H ⇒ 4 Pasangan Elektron Ikatan (PEI) dan 0 PEB (AX₄).<br>3. Bentuk molekul AX₄ adalah Tetrahedral.'
                    },
                    {
                        title: '3. Stoikiometri & Hukum Dasar Kimia (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Konsep mol, massa molar (Mr), volume molar STP (22,4 L/mol), rumus empiris/molekul, serta penentuan pereaksi pembatas dalam reaksi.',
                        visual: 'n = m / Mr | n = V / 22.4 (STP) | Molaritas M = n / V',
                        tips: 'Untuk mencari pereaksi pembatas, bagilah jumlah mol masing-masing reaktan dengan koefisien reaksinya. Nilai terkecil adalah pereaksi pembatas.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Hitung massa dari 0,5 mol H₂SO₄ (Ar H=1, S=32, O=16).<br><br><strong>Pembahasan Terperinci:</strong><br>1. Hitung Mr H₂SO₄ = (2×1) + 32 + (4×16) = 2 + 32 + 64 = 98 g/mol.<br>2. Massa = n × Mr = 0,5 mol × 98 g/mol = 49 gram.'
                    },
                    {
                        title: '4. Termokimia & Perubahan Entalpi (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Reaksi eksoterm & endoterm, penentuan ΔH menggunakan kalorimetri (Q=m·c·ΔT), Hukum Hess, dan energi ikatan rata-rata.',
                        visual: 'Eksoterm (ΔH < 0, Lepas Kalor) | Endoterm (ΔH > 0, Serap Kalor)',
                        tips: 'Menurut Hukum Hess, perubahan entalpi reaksi hanya bergantung pada keadaan awal dan akhir reaksi, bukan pada jalannya reaksi.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Jika pembakaran 1 mol C menghasilkan kalor 393,5 kJ, tuliskan persamaan termokimianya.<br><br><strong>Pembahasan Terperinci:</strong><br>1. Reaksi melepas kalor (eksoterm) ⇒ ΔH = -393,5 kJ/mol.<br>2. Persamaan: C(s) + O₂(g) → CO₂(g) ΔH = -393,5 kJ/mol.'
                    },
                    {
                        title: '5. Laju Reaksi & Teori Tumbukan (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Faktor pendorong laju reaksi (konsentrasi, luas permukaan, suhu, katalis), orde reaksi, serta persamaan laju v = k [A]ˣ [B]ʸ.',
                        visual: 'v = k [A]ˣ [B]ʸ | Kenaikan Suhu: v₂ = v₁ · (Δv)^((T₂-T₁)/ΔT)',
                        tips: 'Katalis mempercepat laju reaksi dengan cara menurunkan energi aktivasi (Ea) tanpa dikonsumsi secara permanen.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Jika suhu dinaikkan 10°C laju reaksi menjadi 2 kali lebih cepat. Berapa kali lebih cepat reaksi pada 50°C dibanding 20°C?<br><br><strong>Pembahasan Terperinci:</strong><br>1. ΔT = 50 - 20 = 30°C.<br>2. Kelipatan = 2^(30/10) = 2³ = 8 kali lebih cepat.'
                    },
                    {
                        title: '6. Kesetimbangan Kimia & Le Chatelier (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Konstanta kesetimbangan Kc dan Kp, derajat disosiasi (α), serta azas Le Chatelier (pengaruh konsentrasi, tekanan, volume, dan suhu).',
                        visual: 'Kc = [Produk]ⁿ / [Reaktan]ᵐ | Kp = P_produkⁿ / P_reaktanᵐ',
                        tips: 'Penambahan tekanan akan menggeser kesetimbangan ke arah jumlah koefisien gas yang LEBIH KECIL.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Pada reaksi N₂(g) + 3H₂(g) ⇌ 2NH₃(g) ΔH = -92 kJ, ke arah mana reaksi bergeser jika suhu dinaikkan?<br><br><strong>Pembahasan Terperinci:</strong><br>1. Reaksi maju adalah eksoterm (-92 kJ).<br>2. Kenaikan suhu menggeser kesetimbangan ke arah endoterm (kiri / reaktan).'
                    },
                    {
                        title: '7. Larutan Asam Basa & Garam (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Teori Arrhenius, Bronsted-Lowry, Lewis, perhitungan pH asam/basa kuat dan lemah, sertah reaksi hidrolisis garam.',
                        visual: 'pH = -log[H⁺] | Asam Lemah: [H⁺] = √(Ka · M) | pOH = 14 - pH',
                        tips: 'Garam yang terbentuk dari Asam Kuat + Basa Lemah akan terhidrolisis parsial dan bersifat ASAM (pH < 7).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Hitung pH dari larutan HCl 0,001 M.<br><br><strong>Pembahasan Terperinci:</strong><br>1. [H⁺] = 10⁻³ M.<br>2. pH = -log(10⁻³) = 3.'
                    },
                    {
                        title: '8. Larutan Penyangga (Buffer) & Ksp (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Komposisi buffer asam/basa, rumus pH buffer, serta hasil kali kelarutan (Ksp) untuk memprediksi pengendapan senyawa.',
                        visual: 'Buffer Asam: [H⁺] = Ka · (mol asam / mol basa konjugasi)',
                        tips: 'Larutan buffer mampu mempertahankan pH dari penambahan sedikit asam, basa, atau pengenceran.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Campuran 100 mL CH₃COOH 0,1 M (Ka = 10⁻⁵) + 50 mL CH₃COONa 0,1 M memiliki pH...<br><br><strong>Pembahasan Terperinci:</strong><br>1. mol Asam = 100 × 0,1 = 10 mmol.<br>2. mol Garam = 50 × 0,1 = 5 mmol.<br>3. [H⁺] = 10⁻⁵ × (10 / 5) = 2 × 10⁻⁵ ⇒ pH = 5 - log 2.'
                    },
                    {
                        title: '9. Elektrokimia: Sel Volta & Elektrolisis (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Potensial sel standar E°sel, deret Volta, reaksi reduksi-oksidasi di Katoda dan Anoda, serta Hukum Faraday I & II.',
                        visual: 'E°sel = E°katoda - E°anoda | Hukum Faraday: w = (e · i · t) / 96500',
                        tips: 'Singkatan KRAP: Katoda Reduksi (Positif), Anoda Oksidasi (Negatif) pada Sel Volta.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Diketahui E° Zn²⁺/Zn = -0,76 V dan E° Cu²⁺/Cu = +0,34 V. Tentukan E°sel reaksi Volta tersebut.<br><br><strong>Pembahasan Terperinci:</strong><br>1. Katoda = Cu (+0,34 V), Anoda = Zn (-0,76 V).<br>2. E°sel = 0,34 - (-0,76) = +1,10 Volt.'
                    },
                    {
                        title: '10. Kimia Karbon & Senyawa Makromolekul (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Gugus fungsi (alkanol, alkoksi alkana, alkanal, alkanon, asam alkanoat, alkil alkanoat), isomeri, karbohidrat, protein, dan polimer.',
                        visual: 'Gugus Fungsi: -OH (Alkohol), -O- (Eter), -CHO (Aldehid), -CO- (Keton)',
                        tips: 'Uji Fehling/Tollens digunakan untuk membedakan Aldehid (positif bereaksi) dan Keton (negatif).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Senyawa organik dengan rumus C₃H₆O yang menghasilkan endapan merah bata dengan pereaksi Fehling adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. C₃H₆O merupakan rumus umum Aldehid atau Keton.<br>2. Karena positif dengan Fehling, senyawa tersebut adalah Aldehid (Propanal).'
                    }
                ],
                'bio': [
                    {
                        title: '1. Ruang Lingkup Biologi & Keanekaragaman Hayati (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Tingkat organisasi kehidupan, keanekaragaman gen, jenis, ekosistem, serta sistem klasifikasi lima kingdom dan binomial nomenklatur.',
                        visual: 'Organisasi: Molekul -> Sel -> Jaringan -> Organ -> Sistem Organ -> Individu',
                        tips: 'Format penulisan Binomial Nomenklatur: Nama genus diawali kapital, nama spesies huruf kecil, keduanya dicetak miring (contoh: *Oryza sativa*).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Keanekaragaman warna bunga mawar (merah, putih, kuning) termasuk keanekaragaman tingkat...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Variasi dalam satu spesies mawar disebabkan oleh perbedaan susunan genetik, sehingga termasuk tingkat Gen.'
                    },
                    {
                        title: '2. Virus & Monera (Bakteri) (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Struktur tubuh virus, daur litik dan lisogenik, struktur sel prokariotik bakteri, pewarnaan Gram, serta peranan positif/negatif bakteri.',
                        visual: 'Daur Litik: Adsorpsi -> Penetrasi -> Sintesis -> Perakitan -> Lisis',
                        tips: 'Bakteri Gram Positif berwarna UNGU karena dinding sel peptidoglikannya tebal, sedangkan Gram Negatif berwarna MERAH.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Bakteri *Rhizobium* berperan menguntungkan dalam pertanian karena...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Mampu mengikat (fiksasi) nitrogen bebas dari udara menjadi nitrat di akar tanaman legum.'
                    },
                    {
                        title: '3. Ekologi, Jaring Makanan & Daur Biogeokimia (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Interaksi antar komponen biotik-abiotik, piramida ekologi, alur energi, serta siklus Karbon, Nitrogen, Air, dan Fosfor.',
                        visual: 'Siklus N₂: Fiksasi -> Nitrifikasi (Nitrit & Nitrat) -> Asimilasi -> Denitrifikasi',
                        tips: 'Dalam rantai makanan, hanya sekitar 10% energi yang berpindah dari satu tingkat trofik ke tingkat trofik berikutnya.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Proses pengubahan amonia menjadi nitrit oleh bakteri *Nitrosomonas* disebut...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Proses tersebut merupakan tahap awal dari Nitrifikasi.'
                    },
                    {
                        title: '4. Biologi Sel & Transpor Membran (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Perbedaan sel tumbuhan dan hewan, fungsi organel sel, transpor pasif (difusi, osmosis) dan transpor aktif (pompa Na-K, endositosis).',
                        visual: 'Osmosis: Perpindahan pelarut (air) dari hipotonis ke hipertonis melewati membran semipermeabel',
                        tips: 'Sel tumbuhan jika dimasukkan ke larutan hipotonis akan mengalami Turgid (tegang), sedangkan sel hewan dapat mengalami Lisis (pecah).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Organel sel yang berfungsi pembentukan ATP melalui respirasi seluler adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Mitokondria.'
                    },
                    {
                        title: '5. Jaringan Tumbuhan & Hewan (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Struktur meristem, xilem, floem, epitel, jaringan ikat, otot (polos, lurik, jantung), serta sistem jaringan saraf.',
                        visual: 'Xilem (Transpor Air & Mineral) | Floem (Transpor Hasil Fotosintesis)',
                        tips: 'Jaringan meristem apikal bertanggung jawab atas pertumbuhan primer (bertambah tinggi/panjang).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Jaringan pengangkut pada tumbuhan yang tersusun atas sel-sel mati dan berdinding tebal lignin adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Xilem.'
                    },
                    {
                        title: '6. Sistem Organ Manusia I: Saraf & Hormon (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Mekanisme penghantaran impuls saraf pada sinapsis, gerak refleks vs sadar, sistem hormon kelenjar hipofisis, tiroid, dan pankreas.',
                        visual: 'Impuls -> Dendrit -> Badan Sel -> Akson -> Sinapsis',
                        tips: 'Hormon Insulin berfungsi menurunkan kadar gula darah, sedangkan Glukagon berfungsi menaikkan kadar gula darah.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Kekurangan hormon insulin dapat menyebabkan penyakit...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Diabetes Mellitus (Kencing Manis).'
                    },
                    {
                        title: '7. Sistem Organ Manusia II: Sirkulasi & Ekskresi (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Sistem peredaran darah besar/kecil, komponen darah, golongan darah ABO, serta proses pembentukan urine di nefron ginjal.',
                        visual: 'Proses Urine: Filtrasi (Glomerulus) -> Reabsorpsi (TKP) -> Augmentasi (TKD)',
                        tips: 'Filtrasi menghasilkan urine primer, Reabsorpsi menghasilkan urine sekunder, dan Augmentasi menghasilkan urine sesungguhnya.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Di bagian ginjal manakah reabsorpsi glukosa dan asam amino terjadi?<br><br><strong>Pembahasan Terperinci:</strong><br>1. Tubulus Kontortus Proksimal (TKP).'
                    },
                    {
                        title: '8. Enzim & Metabolisme Sel (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Sifat enzim, inhibitor kompetitif/non-kompetitif, tahap respirasi aerob (Glikolisis, Dekarboksilasi, Siklus Krebs, Transpor Elektron), dan Fotosintesis (Reaksi Terang & Gelap).',
                        visual: 'Respirasi Aerob: 1 Molekul Glukosa -> 38 ATP (Secara Teoritis)',
                        tips: 'Inhibitor kompetitif bersaing merebut sisi aktif enzim, sedangkan inhibitor non-kompetitif merusak bentuk sisi aktif enzim.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Tahap respirasi sel yang menghasilkan ATP terbanyak adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Transpor Elektron (menghasilkan sekitar 34 ATP).'
                    },
                    {
                        title: '9. Genetika & Sintesis Protein (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Struktur DNA dan RNA, Kromosom, hukum Mendel I & II, persilangan monohibrid/dihibrid, serta mekanisme Transkripsi dan Translasi.',
                        visual: 'DNA -> Transkripsi (Nukleus) -> mRNA -> Translasi (Ribosom) -> Protein',
                        tips: 'Basa nitrogen DNA: Adenin-Timin (A-T), Guanin-Sitosin (G-C). Pada RNA, Timin diganti Urasil (U).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Persilangan AaBb × AaBb menghasilkan rasio fenotipe dihibrid dominan sempurna...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Rasio 9 : 3 : 3 : 1.'
                    },
                    {
                        title: '10. Bioteknologi & Evolusi (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Bioteknologi konvensional vs modern (DNA rekombinan, antibodi monoklonal, PCR), serta bukti evolusi dan Hukum Hardy-Weinberg.',
                        visual: 'Hardy-Weinberg: p + q = 1 | p² + 2pq + q² = 1',
                        tips: 'Syarat berlakunya Hukum Hardy-Weinberg: Ukuran populasi besar, perkawinan acak, tidak ada mutasi, migrasi, atau seleksi alam.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Jika frekuensi gen albino (q) adalah 0,2, berapakah frekuensi individu carrier (2pq)?<br><br><strong>Pembahasan Terperinci:</strong><br>1. p = 1 - 0,2 = 0,8.<br>2. Frekuensi carrier 2pq = 2(0,8)(0,2) = 0,32 (32%).'
                    }
                ],
                'eko': [
                    {
                        title: '1. Masalah Ekonomi, Kelangkaan & Biaya Peluang (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Kebutuhan manusia tak terbatas vs sumber daya terbatas, masalah pokok ekonomi klasik/modern (What, How, For Whom), dan menghitung Opportunity Cost.',
                        visual: 'Biaya Peluang = Nilai dari Kesempatan Terbaik yang Dikorbankan',
                        tips: 'Biaya peluang tidak dihitung dengan menjumlahkan semua pilihan yang dibatalkan, melainkan memilih nilai tertinggi dari pilihan yang ditinggalkan.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Budi memiliki opsi bekerja sebagai staf (gaji Rp 3 jt) atau wirausaha (potensi Rp 4 jt). Jika ia memilih kuliah, berapa biaya peluangnya?<br><br><strong>Pembahasan Terperinci:</strong><br>1. Pilihan terbaik yang dilepas adalah wirausaha (Rp 4 jt). Maka biaya peluangnya = Rp 4.000.000.'
                    },
                    {
                        title: '2. Keseimbangan Pasar & Elastisitas (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Fungsi permintaan dan penawaran, proses terbentuknya harga keseimbangan (Qd = Qs), elastisitas harga permintaan/penawaran.',
                        visual: 'Elastisitas E = (%ΔQ / %ΔP) = (dQ/dP) · (P/Q)',
                        tips: 'Barang kebutuhan pokok umumnya memiliki elastisitas yang Inelastis (E < 1).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Diketahui Qd = 80 - 2P dan Qs = -20 + 3P. Tentukan harga keseimbangan P.<br><br><strong>Pembahasan Terperinci:</strong><br>1. Qd = Qs ⇒ 80 - 2P = -20 + 3P ⇒ 100 = 5P ⇒ P = 20.'
                    },
                    {
                        title: '3. Pendapatan Nasional & PDB (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Menghitung PDB/GNP melalui pendekatan produksi, pendapatan, dan pengeluaran, serta pendapatan per kapita dan distribusi pendapatan.',
                        visual: 'Pendekatan Pengeluaran: Y = C + I + G + (X - M)',
                        tips: 'GNP = GDP + Pendapatan Neto Faktor Luar Negeri.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Jika C = 200, I = 100, G = 150, X = 80, dan M = 50, hitunglah PDB nasional.<br><br><strong>Pembahasan Terperinci:</strong><br>1. Y = 200 + 100 + 150 + (80 - 50) = 450 + 30 = 480.'
                    },
                    {
                        title: '4. APBN, APBD & Kebijakan Fiskal (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Sumber penerimaan dan pengeluaran negara, pajak sebagai instrumen fiskal, serta kebijakan fiskal ekspansif vs kontraktif.',
                        visual: 'Kebijakan Fiskal Ekspansif: Turunkan Pajak (T) + Naikkan Belanja (G)',
                        tips: 'Saat terjadi inflasi tinggi, pemerintah menerapkan kebijakan fiskal kontraktif (menaikkan pajak dan menekan belanja).',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Instrumen kebijakan fiskal untuk mengatasi resesi ekonomi adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Meningkatkan belanja negara dan menurunkan tarif pajak.'
                    },
                    {
                        title: '5. Kebijakan Moneter & Perbankan (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Peran Bank Sentral (BI), instrumen kebijakan moneter (Operasi Pasar Terbuka, Diskonto, Giro Wajib Minimum, Kredit Selektif).',
                        visual: 'Atasi Inflasi (Tight Money Policy): Naikkan Suku Bunga & Jual Sertifikat BI',
                        tips: 'Suku bunga diskonto dinaikkan oleh Bank Sentral untuk mengurangi jumlah uang yang beredar di masyarakat.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Jika Bank Indonesia menaikkan tingkat suku bunga diskonto, dampak yang diharapkan adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Jumlah uang beredar berkurang dan laju inflasi menurun.'
                    },
                    {
                        title: '6. Akuntansi: Persamaan Dasar & Jurnal Umum (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Konsep persamaan akuntansi Aset = Liabilitas + Ekuitas, analisis transaksi, serta aturan Debet-Kredit dalam pencatatan Jurnal Umum.',
                        visual: 'Aset & Beban (Naik di DEBET) | Utang, Modal, Pendapatan (Naik di KREDIT)',
                        tips: 'Setiap transaksi keuangan harus selalu seimbang (balance) antara total nilai Debet dan Kredit.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Membeli peralatan kantor secara kredit senilai Rp 5.000.000. Catatan jurnalnya adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Peralatan (Debet) Rp 5.000.000, Utang Usaha (Kredit) Rp 5.000.000.'
                    },
                    {
                        title: '7. Akuntansi: Jurnal Penyesuaian & Laporan Keuangan (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Penyusunan Ayat Jurnal Penyesuaian (AJP) beban dibayar di muka, perlengkapan terpakai, penyusutan aset, serta Laporan Laba/Rugi & Neraca.',
                        visual: 'Beban Perlengkapan (D) / Perlengkapan (K) = Sebesar yang Terpakai',
                        tips: 'Perlengkapan di AJP dicatat sebesar jumlah yang SUDAH TERPAKAI, bukan sisa.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Perlengkapan awal Rp 3.000.000. Di akhir periode sisa perlengkapan Rp 1.000.000. Berapa AJP-nya?<br><br><strong>Pembahasan Terperinci:</strong><br>1. Nilai terpakai = 3.000.000 - 1.000.000 = 2.000.000.<br>2. Jurnal: Beban Perlengkapan (D) Rp 2.000.000; Perlengkapan (K) Rp 2.000.000.'
                    }
                ],
                'sos': [
                    {
                        title: '1. Sosiologi Sebagai Ilmu & Interaksi Sosial (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Ciri-ciri sosiologi (empiris, teoritis, kumulatif, non-etis), tindakan sosial Max Weber, syarat interaksi sosial, serta faktor imitative/sugesti/empati.',
                        visual: 'Ciri Sosiologi: Empiris (Sesuai Fakta) & Non-Etis (Tidak Menilai Baik/Buruk)',
                        tips: 'Sugesti terjadi ketika seseorang menerima pandangan/pengaruh orang lain tanpa berpikir kritis.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Seorang dokter menyarankan pasien minum obat dan pasien langsung mematuhinya. Faktor pendorong interaksi ini adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Sugesti (pengaruh dari pihak berotoritas).'
                    },
                    {
                        title: '2. Nilai & Norma Sosial (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Tingkatan norma sosial (Usage, Folkways, Mores, Custom), fungsi nilai sosial, dan dampak penyimpangan norma sosial dalam masyarakat.',
                        visual: 'Urutan Sanksi: Cara (Usage) -> Kebiasaan (Folkways) -> Tata Kelakuan (Mores) -> Adat (Custom)',
                        tips: 'Pelanggaran terhadap Adat Istiadat (Custom) mendapatkan sanksi sosial yang paling berat dari masyarakat lokal.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Seseorang yang makan menggunakan tangan kiri di tempat umum akan ditegur. Hal ini melanggar norma...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Kebiasaan (Folkways).'
                    },
                    {
                        title: '3. Stratifikasi & Diferensiasi Sosial (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Pelapisan sosial vertikal (terbuka, tertutup, campuran) serta pengelompokan sosial horizontal berdasarkan ras, suku, dan agama.',
                        visual: 'Stratifikasi (Vertikal/Kasta) vs Diferensiasi (Horizontal/Kesetaraan)',
                        tips: 'Sistem kasta di Bali/India adalah contoh Stratifikasi Sosial Tertutup.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Keberagaman suku bangsa dan agama di Indonesia tergolong ke dalam struktur...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Diferensiasi Sosial (karena bersifat sejajar/horizontal).'
                    },
                    {
                        title: '4. Konflik Sosial & Resolusi Konflik (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Faktor penyebab konflik, bentuk-bentuk konflik sosial, serta bentuk akomodasi (Konsiliasi, Mediasi, Arbitrase, Ajudikasi).',
                        visual: 'Arbitrase (Keputusan Mengikat) vs Mediasi (Pihak Ketiga Hanya Penasihat)',
                        tips: 'Jika pihak ketiga berwenang mengambil keputusan hukum mengikat, bentuk akomodasinya adalah Arbitrase.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Penyelesaian sengketa melalui pengadilan dinamakan...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Ajudikasi.'
                    },
                    {
                        title: '5. Perubahan Sosial & Modernisasi (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Teori perubahan sosial (Evolusi, Siklus, Konflik), faktor pendorong/penghambat, serta dampak globalisasi dan westernisasi.',
                        visual: 'Teori Siklus: Perubahan Sosial Berulang Kembali Seperti Roda Berputar',
                        tips: 'Sikap tradisional yang tertutup terhadap hal baru merupakan faktor PENGHAMBAT utama perubahan sosial.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Perkembangan teknologi internet merubah pola belanja masyarakat menjadi online. Fenomena ini contoh perubahan...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Perubahan Sosial Besar (mempunyai pengaruh luas pada struktur masyarakat).'
                    }
                ],
                'geo': [
                    {
                        title: '1. Pengetahuan Dasar Geografi & 10 Konsep Geografi (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Objek material/formal geografi, 4 prinsip (distribusi, interelasi, deskripsi, korologi), 3 pendekatan (spasial, ekologi, kompleks wilayah), serta 10 konsep dasar.',
                        visual: 'Prinsip Korologi = Gabungan distribusi, interelasi, dan deskripsi secara komprehensif',
                        tips: 'Pendekatan Ekologi dikhususkan untuk mengkaji interaksi antara aktivitas MANUSIA dengan LINGKUNGAN ALAM.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Daerah pegunungan cocok untuk perkebunan teh, sedangkan daerah pantai cocok untuk tambak garam. Konsep geografi yang tepat adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Konsep Diferensiasi Area.'
                    },
                    {
                        title: '2. Dinamika Litosfer & Tenaga Pembentuk Bumi (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Tenaga endogen (Tektonisme, Vulkanisme, Seisme) dan eksogen (Pelapukan, Erosi, Sedimentasi), serta jenis-jenis batuan pembentuk litosfer.',
                        visual: 'Siklus Batuan: Magma -> Batuan Beku -> Batuan Sedimen -> Batuan Metamorf',
                        tips: 'Gempa tektonik disebabkan oleh pergeseran atau patahan lempeng bumi.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Batuan kapur yang mengalami perubahan suhu dan tekanan tinggi akan berubah menjadi...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Batu Marmer (Batuan Metamorf).'
                    },
                    {
                        title: '3. Dinamika Atmosfer & Iklim (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Lapisan-lapisan atmosfer (Troposfer, Stratosfer, Mesosfer, Termosfer), unsur cuaca, klasifikasi iklim Junghuhn & Koppen, serta fenomena El Nino/La Nina.',
                        visual: 'Lapisan Atmosfer: Troposfer (Cuaca) | Stratosfer (Ozon) | Mesosfer (Bakar Meteor)',
                        tips: 'Fenomena El Nino menyebabkan kemarau panjang di Indonesia karena angin pasat melemah.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Lapisan atmosfer tempat terjadinya fenomena hujan, angin, dan awan adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Troposfer.'
                    },
                    {
                        title: '4. Penginderaan Jauh & Sistem Informasi Geografis (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Unsur interpretasi citra (Rona, Warna, Bentuk, Ukuran, Tekstur, Pola, Bayangan, Situs, Asosiasi) serta tahapan kerja SIG (Input, Data Management, Output).',
                        visual: 'Tahap SIG: Data Spasial + Data Atribut -> Overlay Peta -> Peta Hasil Analisis',
                        tips: 'Teknik Overlay (tumpang susun peta) digunakan dalam SIG untuk penentuan lokasi pembangunan strategis.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Objek lapangan bola pada foto udara mudah dikenali dari bentuknya yang persegi panjang dan tekstur yang halus. Unsur interpretasi yang digunakan adalah...<br><br><strong>Pembahasan Terperinci:</strong><br>1. Bentuk dan Tekstur.'
                    }
                ],
                'lit': [
                    {
                        title: '1. Bahasa Indonesia: Ide Pokok & Simpulan Teks (SNBT)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Menentukan ide pokok paragraf (deduktif/induktif), menemukan kalimat utama, membuat simpulan logis berdasarkan isi teks bacaan.',
                        visual: 'Paragraf Deduktif (Ide Pokok di Awal) | Paragraf Induktif (Ide Pokok di Akhir)',
                        tips: 'Simpulan yang benar harus mencakup gagasan keseluruhan teks dan tidak boleh melenceng dari fakta bacaan.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>Tentukan kalimat utama: "Pendidikan karakter sangat penting bagi generasi muda. Karakter yang kuat membentuk mental tangguh. Oleh karena itu, sekolah wajib menanamkan nilai moral."<br><br><strong>Pembahasan Terperinci:</strong><br>1. Kalimat utama terletak di awal paragraf (Deduktif): "Pendidikan karakter sangat penting bagi generasi muda."'
                    },
                    {
                        title: '2. English Comprehension: Main Idea & Author\'s Attitude (SNBT)',
                        kurikulum: 'K13 & Merdeka',
                        summary: 'Identifying main ideas of scientific passages, inferring unstated details, analyzing author\'s tone and vocabulary context in English texts.',
                        visual: 'Tone Types: Objective, Critical, Optimistic, Pessimistic, Neutral',
                        tips: 'Look for adjectives and adverbs used by the author to determine their tone toward the subject.',
                        contohSoal: '<strong>Contoh Soal HOTS:</strong><br>What is the author\'s attitude in a text stating "Renewable energy technologies are revolutionary and vital for planet Earth"?<br><br><strong>Pembahasan Terperinci:</strong><br>1. The tone is Supportive / Optimistic.'
                    }
                ]
            },
            simulasiBank: {
                'utbk-pk': {
                    title: 'UTBK SNBT - Pengetahuan Kuantitatif (PK)',
                    durasiMinutes: 15,
                    soal: [
                        {
                            id: 'q1',
                            pertanyaan: 'Diketahui persamaan x² - (k + 2)x + 16 = 0 memiliki dua akar real positif yang sama (kembar). Nilai k yang memenuhi adalah...',
                            pilihan: ['A. 6 atau -10', 'B. 6 saja', 'C. 8 atau -8', 'D. 10 saja', 'E. -6 saja'],
                            kunci: 'B. 6 saja',
                            solusiLengkap: `<strong>Pembahasan Akurat & Langkah Demi Langkah:</strong><br>
                            1. Syarat dua akar real sama (kembar) adalah Diskriminan D = 0.<br>
                            &nbsp;&nbsp;&nbsp;D = b² - 4ac = 0<br>
                            2. Tentukan nilai a, b, dan c:<br>
                            &nbsp;&nbsp;&nbsp;a = 1, b = -(k + 2), c = 16<br>
                            &nbsp;&nbsp;&nbsp;(-(k + 2))² - 4(1)(16) = 0<br>
                            &nbsp;&nbsp;&nbsp;(k + 2)² - 64 = 0  ⇒  (k + 2)² = 64<br>
                            &nbsp;&nbsp;&nbsp;k + 2 = ±8<br>
                            &nbsp;&nbsp;&nbsp;• k₁ = 8 - 2 = 6<br>
                            &nbsp;&nbsp;&nbsp;• k₂ = -8 - 2 = -10<br><br>
                            3. <strong>Uji Syarat Akar Positif:</strong><br>
                            &nbsp;&nbsp;&nbsp;Penjumlahan akar-akar: x₁ + x₂ = -b/a = (k + 2). Karena kedua akar positif, maka x₁ + x₂ > 0.<br>
                            &nbsp;&nbsp;&nbsp;• Untuk k = 6  ⇒ 6 + 2 = 8 > 0 (Memenuhi).<br>
                            &nbsp;&nbsp;&nbsp;• Untuk k = -10 ⇒ -10 + 2 = -8 < 0 (Ditolak).<br><br>
                            <strong>Kesimpulan Jawaban Akurat:</strong> Nilai k yang memenuhi adalah <strong>6 saja (Pilihan B)</strong>.`
                        },
                        {
                            id: 'q2',
                            pertanyaan: 'Jika 3ⁿ⁺¹ + 3ⁿ = 36, maka nilai dari 2ⁿ adalah...',
                            pilihan: ['A. 2', 'B. 4', 'C. 8', 'D. 16', 'E. 32'],
                            kunci: 'B. 4',
                            solusiLengkap: `<strong>Pembahasan Akurat & Langkah Demi Langkah:</strong><br>
                            1. Gunakan sifat eksponensial (aᵐ⁺ⁿ = aᵐ · aⁿ):<br>
                            &nbsp;&nbsp;&nbsp;3ⁿ⁺¹ + 3ⁿ = 36  ⇒  (3ⁿ · 3¹) + 3ⁿ = 36<br>
                            2. Faktorkan 3ⁿ dari kedua suku:<br>
                            &nbsp;&nbsp;&nbsp;3ⁿ (3 + 1) = 36<br>
                            &nbsp;&nbsp;&nbsp;3ⁿ (4) = 36  ⇒  3ⁿ = 9  ⇒  3ⁿ = 3²  ⇒  n = 2.<br><br>
                            3. Hitung nilai 2ⁿ:<br>
                            &nbsp;&nbsp;&nbsp;2ⁿ = 2² = 4.<br><br>
                            <strong>Kesimpulan Jawaban Akurat:</strong> Nilai 2ⁿ = <strong>4 (Pilihan B)</strong>.`
                        },
                        {
                            id: 'q3',
                            pertanyaan: 'Jika log 2 = a dan log 3 = b, maka nilai dari log 18 adalah...',
                            pilihan: ['A. a + b', 'B. a + 2b', 'C. 2a + b', 'D. a² + b', 'E. a · b²'],
                            kunci: 'B. a + 2b',
                            solusiLengkap: `<strong>Pembahasan Akurat:</strong><br>
                            1. Faktorkan 18 menjadi perkalian faktor primanya: 18 = 2 × 9 = 2 × 3².<br>
                            2. Gunakan sifat logaritma log(x · y) = log x + log y dan log(xⁿ) = n · log x:<br>
                            &nbsp;&nbsp;&nbsp;log 18 = log(2 × 3²)<br>
                            &nbsp;&nbsp;&nbsp;= log 2 + log(3²)<br>
                            &nbsp;&nbsp;&nbsp;= log 2 + 2 · log 3<br>
                            &nbsp;&nbsp;&nbsp;= a + 2b.<br><br>
                            <strong>Jawaban Akurat:</strong> Pilihan B.`
                        },
                        {
                            id: 'q4',
                            pertanyaan: 'Jumlah deret geometri tak hingga 12 + 4 + 4/3 + 4/9 + ... adalah...',
                            pilihan: ['A. 16', 'B. 18', 'C. 20', 'D. 24', 'E. 36'],
                            kunci: 'B. 18',
                            solusiLengkap: `<strong>Pembahasan Akurat:</strong><br>
                            1. Suku pertama a = 12.<br>
                            2. Rasio r = Un / U(n-1) = 4 / 12 = 1/3.<br>
                            3. Karena |r| < 1, gunakan rumus S_∞ = a / (1 - r):<br>
                            &nbsp;&nbsp;&nbsp;S_∞ = 12 / (1 - 1/3) = 12 / (2/3) = 12 × (3/2) = 18.<br><br>
                            <strong>Jawaban Akurat:</strong> Pilihan B.`
                        }
                    ]
                },
                'tka-saintek': {
                    title: 'TKA Saintek - Fisika HOTS Master',
                    durasiMinutes: 15,
                    soal: [
                        {
                            id: 'q1_tka',
                            pertanyaan: 'Sebuah benda bermassa 2 kg bergerak pada bidang datar licin ditarik gaya F = 20 N membentuk sudut 60° terhadap arah horizontal. Berapakah percepatan yang dialami benda tersebut?',
                            pilihan: ['A. 5 m/s²', 'B. 10 m/s²', 'C. 5√3 m/s²', 'D. 20 m/s²', 'E. 10√3 m/s²'],
                            kunci: 'A. 5 m/s²',
                            solusiLengkap: `<strong>Pembahasan Akurat & Langkah Demi Langkah:</strong><br>
                            1. Proyeksikan gaya F pada sumbu horizontal (searah gerak benda):<br>
                            &nbsp;&nbsp;&nbsp;F_x = F · cos(60°) = 20 N · (0,5) = 10 N.<br><br>
                            2. Terapkan Hukum II Newton (ΣF_x = m · a):<br>
                            &nbsp;&nbsp;&nbsp;10 N = 2 kg · a  ⇒  a = 5 m/s².<br><br>
                            <strong>Kesimpulan Jawaban Akurat:</strong> Percepatan benda adalah <strong>5 m/s² (Pilihan A)</strong>.`
                        },
                        {
                            id: 'q2_tka',
                            pertanyaan: 'Benda jatuh bebas dari ketinggian 45 m di atas tanah (g = 10 m/s²). Waktu yang dibutuhkan benda untuk sampai di tanah adalah...',
                            pilihan: ['A. 2 detik', 'B. 3 detik', 'C. 4 detik', 'D. 4,5 detik', 'E. 5 detik'],
                            kunci: 'B. 3 detik',
                            solusiLengkap: `<strong>Pembahasan Akurat:</strong><br>
                            1. Rumus Gerak Jatuh Bebas: h = ½ · g · t²<br>
                            2. 45 = ½ (10) · t² ⇒ 45 = 5t² ⇒ t² = 9 ⇒ t = 3 detik.<br><br>
                            <strong>Jawaban Akurat:</strong> Pilihan B.`
                        }
                    ]
                },
                'lit-ind-eng': {
                    title: 'Literasi Bahasa & Penalaran Teks',
                    durasiMinutes: 10,
                    soal: [
                        {
                            id: 'q1_lit',
                            pertanyaan: 'Bacalah teks berikut: "Pemanasan global memicu percepatan pencairan es kutub. Hal ini berdampak langsung pada kenaikan permukaan air laut global yang mengancam pemukiman pesisir." Ide pokok paragraf di atas adalah...',
                            pilihan: [
                                'A. Pencairan es kutub terjadi di mana-mana.',
                                'B. Pemanasan global berdampak pada pencairan es dan kenaikan air laut.',
                                'C. Pemukiman pesisir terancam tenggelam.',
                                'D. Kenaikan permukaan air laut hanya terjadi di kutub.',
                                'E. Pemanasan global adalah satu-satunya fenomena alam.'
                            ],
                            kunci: 'B. Pemanasan global berdampak pada pencairan es dan kenaikan air laut.',
                            solusiLengkap: `<strong>Pembahasan Akurat:</strong><br>
                            Ide pokok mencakup inti pembicaraan seluruh paragraf, yaitu hubungan sebab-akibat antara pemanasan global dengan pencairan es dan dampak lanjutannya pada air laut.<br><br>
                            <strong>Jawaban Akurat:</strong> Pilihan B.`
                        }
                    ]
                }
            }
        };

        // UI View Switcher Engine
        function switchView(viewName) {
            state.activeView = viewName;

            // Update Nav UI Desktop
            ['home', 'materi', 'utbk', 'riwayat'].forEach(v => {
                const el = document.getElementById(`nav-${v}`);
                if (el) {
                    if (v === viewName) {
                        el.className = "px-4 py-2.5 rounded-xl text-white bg-purple-600 transition flex items-center gap-1.5 font-bold shadow-md shadow-purple-600/30";
                    } else {
                        el.className = "px-4 py-2.5 rounded-xl text-slate-300 hover:text-white transition flex items-center gap-1.5 font-medium";
                    }
                }

                const mobEl = document.getElementById(`mob-${v}`);
                if (mobEl) {
                    if (v === viewName) {
                        mobEl.className = "flex flex-col items-center gap-1 text-purple-400 font-bold";
                    } else {
                        mobEl.className = "flex flex-col items-center gap-1 text-slate-400 font-medium";
                    }
                }
            });

            // Render Target View
            const content = document.getElementById('app-content');
            if (viewName === 'home') content.innerHTML = renderHome();
            else if (viewName === 'materi') content.innerHTML = renderMateriScreen();
            else if (viewName === 'utbk') content.innerHTML = renderUTBKScreen();
            else if (viewName === 'riwayat') {
                content.innerHTML = renderRiwayatScreen();
                if (state.attempts.length > 0) {
                    openDetailRiwayat(state.attempts.length - 1);
                }
            }

            lucide.createIcons();
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Global Search Logic
        function handleGlobalSearch(query) {
            const popover = document.getElementById('search-results-popover');
            if (!query || query.trim().length < 2) {
                popover.classList.add('hidden');
                return;
            }

            const q = query.toLowerCase().trim();
            let matches = [];

            db.mapel.forEach(m => {
                const list = db.materiDetails[m.id] || [];
                list.forEach(mat => {
                    if (mat.title.toLowerCase().includes(q) || mat.summary.toLowerCase().includes(q)) {
                        matches.push({ mapelId: m.id, mapelNama: m.nama, title: mat.title });
                    }
                });
            });

            if (matches.length === 0) {
                popover.innerHTML = `<div class="p-3 text-xs text-slate-400 text-center">Tidak ditemukan materi dengan kata kunci "${query}"</div>`;
            } else {
                popover.innerHTML = matches.map(res => `
                    <div onclick="selectSearchResult('${res.mapelId}')" class="p-3 hover:bg-slate-800 rounded-xl cursor-pointer transition border-b border-slate-800/60 last:border-0">
                        <span class="text-[10px] font-bold text-purple-400 uppercase tracking-wider block">${res.mapelNama}</span>
                        <span class="text-xs text-white font-semibold block mt-0.5">${res.title}</span>
                    </div>
                `).join('');
            }
            popover.classList.remove('hidden');
        }

        function selectSearchResult(mapelId) {
            document.getElementById('search-results-popover').classList.add('hidden');
            document.getElementById('global-search').value = '';
            state.selectedSubject = mapelId;
            switchView('materi');
            openDetailMapel(mapelId);
        }

        // Render Home Component
        function renderHome() {
            return `
                <!-- Hero Banner -->
                <div class="relative rounded-3xl gradient-brand p-8 sm:p-12 overflow-hidden border border-slate-800/80 shadow-2xl mb-12">
                    <div class="absolute -right-20 -bottom-20 w-96 h-96 bg-purple-600/10 rounded-full blur-3xl pointer-events-none"></div>
                    <div class="relative z-10 max-w-3xl">
                        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-purple-500/10 border border-purple-500/20 text-purple-300 text-xs font-semibold mb-6">
                            <i data-lucide="sparkles" class="w-4 h-4 text-purple-400"></i>
                            <span>Nihiluxxy Super Learning Edition • Sukses SNBT 2026</span>
                        </div>
                        <h1 class="text-3xl sm:text-5xl font-black text-white tracking-tight mb-4 leading-tight">
                            Kuasai Seluruh Materi SMA & Taklukkan <span class="bg-clip-text text-transparent gradient-accent">UTBK SNBT</span>.
                        </h1>
                        <p class="text-slate-300 text-xs sm:text-sm mb-8 leading-relaxed">
                            Akses modul rangkuman lengkap SMA (Kelas 10–12) Kurikulum 2013 & Merdeka. Dilengkapi sistem simulasi interaktif, kunci jawaban akurat, dan langkah pembahasan HOTS terperinci.
                        </p>
                        <div class="flex flex-wrap gap-4">
                            <button onclick="switchView('materi')" class="gradient-accent text-white font-extrabold px-6 py-3.5 rounded-2xl shadow-lg shadow-purple-500/25 hover:opacity-95 transition flex items-center gap-2 text-xs sm:text-sm">
                                <i data-lucide="book-open" class="w-4 h-4"></i> Pelajari Modul SMA
                            </button>
                            <button onclick="switchView('utbk')" class="bg-slate-800/90 border border-slate-700 text-white font-extrabold px-6 py-3.5 rounded-2xl hover:bg-slate-800 transition flex items-center gap-2 text-xs sm:text-sm">
                                <i data-lucide="target" class="w-4 h-4 text-amber-400"></i> Simulasi UTBK/TKA
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Stats Counters -->
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-12">
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 text-center">
                        <span class="text-2xl font-black text-purple-400 font-mono">8+</span>
                        <span class="text-xs text-slate-400 block mt-1 font-semibold">Mata Pelajaran Lengkap</span>
                    </div>
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 text-center">
                        <span class="text-2xl font-black text-emerald-400 font-mono">100%</span>
                        <span class="text-xs text-slate-400 block mt-1 font-semibold">Standar K13 & Merdeka</span>
                    </div>
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 text-center">
                        <span class="text-2xl font-black text-amber-400 font-mono">HOTS</span>
                        <span class="text-xs text-slate-400 block mt-1 font-semibold">Soal & Pembahasan Akurat</span>
                    </div>
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 text-center">
                        <span class="text-2xl font-black text-cyan-400 font-mono">2026</span>
                        <span class="text-xs text-slate-400 block mt-1 font-semibold">Update Silabus SNBT</span>
                    </div>
                </div>

                <!-- Subject Grid Section -->
                <div class="mb-12">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 mb-6">
                        <div>
                            <h2 class="text-2xl font-black text-white tracking-tight">Mata Pelajaran SMA (Lengkap)</h2>
                            <p class="text-slate-400 text-xs sm:text-sm">Pilih kurikulum untuk menyesuaikan struktur Fase/Kelas Anda</p>
                        </div>
                        <div class="bg-slate-900/90 p-1 rounded-2xl border border-slate-800 flex gap-1 text-xs font-bold">
                            <button onclick="setKurikulum('Merdeka')" class="px-4 py-2 rounded-xl transition ${state.selectedKurikulum === 'Merdeka' ? 'bg-purple-600 text-white shadow-md shadow-purple-600/30' : 'text-slate-400 hover:text-white'}">Kurikulum Merdeka</button>
                            <button onclick="setKurikulum('K13')" class="px-4 py-2 rounded-xl transition ${state.selectedKurikulum === 'K13' ? 'bg-purple-600 text-white shadow-md shadow-purple-600/30' : 'text-slate-400 hover:text-white'}">Kurikulum 2013 (K13)</button>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-5">
                        ${db.mapel.map(m => `
                            <div class="gradient-card border border-slate-800 hover:border-purple-500/50 p-5 rounded-2xl transition duration-300 hover:-translate-y-1 group cursor-pointer shadow-lg" onclick="openDetailMapel('${m.id}')">
                                <div class="w-12 h-12 rounded-2xl bg-gradient-to-br ${m.color} flex items-center justify-center text-white mb-4 shadow-lg group-hover:scale-110 transition duration-300">
                                    <i data-lucide="${m.icon}"></i>
                                </div>
                                <h3 class="font-extrabold text-white text-base mb-1 group-hover:text-purple-300 transition">${m.nama}</h3>
                                <p class="text-[11px] text-purple-400 font-semibold mb-4 leading-tight">
                                    ${state.selectedKurikulum === 'Merdeka' ? m.merdeka : m.k13}
                                </p>
                                <div class="flex items-center justify-between text-xs text-slate-400 pt-3 border-t border-slate-800/80">
                                    <span class="font-bold text-[11px]">Buka Modul Belajar</span>
                                    <i data-lucide="arrow-right" class="w-4 h-4 text-purple-400 group-hover:translate-x-1 transition"></i>
                                </div>
                            </div>
                        `).join('')}
                    </div>
                </div>

                <!-- Last Attempt Snapshot Card -->
                <div class="gradient-card border border-slate-800 rounded-3xl p-6 sm:p-8 shadow-xl">
                    <div class="flex items-center justify-between mb-4">
                        <div class="flex items-center gap-3">
                            <div class="p-2.5 rounded-2xl bg-purple-500/10 text-purple-400 border border-purple-500/20">
                                <i data-lucide="history" class="w-5 h-5"></i>
                            </div>
                            <div>
                                <h3 class="font-extrabold text-white text-base">Riwayat Pengerjaan Terakhir</h3>
                                <p class="text-xs text-slate-400">Evaluasi & pelajari pembahasan akurat dari pengerjaan Anda</p>
                            </div>
                        </div>
                        <button onclick="switchView('riwayat')" class="text-xs text-purple-400 hover:text-purple-300 font-bold flex items-center gap-1">
                            <span>Lihat Semua</span>
                            <i data-lucide="chevron-right" class="w-4 h-4"></i>
                        </button>
                    </div>
                    ${renderLastAttemptCard()}
                </div>
            `;
        }

        function renderLastAttemptCard() {
            if (state.attempts.length === 0) {
                return `
                    <div class="text-center py-8 text-slate-500 text-xs border border-dashed border-slate-800 rounded-2xl bg-slate-900/40">
                        <i data-lucide="info" class="w-6 h-6 mx-auto mb-2 text-slate-600"></i>
                        Belum ada simulasi yang diselesaikan. Selesaikan simulasi TKA/UTBK untuk mencatat riwayat akurat Anda di sini.
                    </div>
                `;
            }
            const last = state.attempts[state.attempts.length - 1];
            return `
                <div class="bg-slate-900/80 border border-slate-800 p-5 rounded-2xl flex flex-col sm:flex-row justify-between sm:items-center gap-4">
                    <div>
                        <div class="flex items-center gap-2 mb-1.5">
                            <span class="text-[10px] font-extrabold px-2 py-0.5 rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-500/30">Pengerjaan Terakhir</span>
                            <span class="text-xs text-slate-500 font-mono">${last.tanggal}</span>
                        </div>
                        <h4 class="font-black text-white text-base">${last.judulSimulasi}</h4>
                        <p class="text-xs text-slate-400 mt-1">Akurasi Skor: <span class="text-purple-300 font-bold font-mono">${last.skor}%</span> (${last.benar} dari ${last.totalSoal} Soal Benar)</p>
                    </div>
                    <button onclick="openDetailRiwayat(${state.attempts.length - 1})" class="px-5 py-3 bg-purple-600 hover:bg-purple-500 text-white font-extrabold text-xs rounded-xl transition shadow-lg shadow-purple-600/20 flex items-center justify-center gap-2">
                        <i data-lucide="file-search" class="w-4 h-4"></i> Lihat Pembahasan Akurat
                    </button>
                </div>
            `;
        }

        function setKurikulum(k) {
            state.selectedKurikulum = k;
            switchView('home');
        }

        // Render Modul Materi Screen
        function renderMateriScreen() {
            return `
                <div class="mb-8">
                    <h1 class="text-3xl font-black text-white tracking-tight">Modul Pembelajaran SMA (Kelas 10-12)</h1>
                    <p class="text-slate-400 text-xs sm:text-sm mt-1">Rangkuman komprehensif, konsep kunci, tips cepat, dan contoh soal HOTS terakreditasi.</p>
                </div>
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
                    <div class="lg:col-span-4 space-y-3">
                        <h3 class="text-xs uppercase tracking-wider font-extrabold text-purple-400 px-1">Pilih Mata Pelajaran</h3>
                        ${db.mapel.map(m => `
                            <button onclick="openDetailMapel('${m.id}')" id="mapel-btn-${m.id}" class="w-full text-left p-4 rounded-2xl bg-slate-900/60 border border-slate-800 hover:bg-slate-800 hover:border-purple-500/50 transition flex items-center gap-3.5 group">
                                <div class="w-10 h-10 rounded-xl bg-gradient-to-br ${m.color} flex items-center justify-center text-white font-bold text-xs shadow-md group-hover:scale-105 transition">
                                    <i data-lucide="${m.icon}" class="w-5 h-5"></i>
                                </div>
                                <div class="flex flex-col">
                                    <span class="font-extrabold text-sm text-slate-200 group-hover:text-purple-300 transition">${m.nama}</span>
                                    <span class="text-[10px] text-slate-500 font-medium">10 Sub-materi HOTS</span>
                                </div>
                            </button>
                        `).join('')}
                    </div>
                    <div id="materi-reader" class="lg:col-span-8 gradient-card border border-slate-800 rounded-3xl p-6 sm:p-8 shadow-2xl">
                        <!-- Content auto injected -->
                    </div>
                </div>
            `;
        }

        function openDetailMapel(mapelId) {
            state.selectedSubject = mapelId;
            if (state.activeView !== 'materi') switchView('materi');

            db.mapel.forEach(m => {
                const btn = document.getElementById(`mapel-btn-${m.id}`);
                if (btn) {
                    if (m.id === mapelId) {
                        btn.className = "w-full text-left p-4 rounded-2xl bg-slate-800 border border-purple-500/80 flex items-center gap-3.5 group shadow-lg";
                    } else {
                        btn.className = "w-full text-left p-4 rounded-2xl bg-slate-900/60 border border-slate-800 hover:bg-slate-800 hover:border-purple-500/50 transition flex items-center gap-3.5 group";
                    }
                }
            });

            const mapel = db.mapel.find(m => m.id === mapelId);
            const materiList = db.materiDetails[mapelId] || [];

            const reader = document.getElementById('materi-reader');
            if (reader) {
                reader.innerHTML = `
                    <div class="flex items-center gap-4 mb-8 pb-6 border-b border-slate-800">
                        <div class="w-12 h-12 rounded-2xl bg-gradient-to-br ${mapel.color} flex items-center justify-center text-white font-bold shadow-lg">
                            <i data-lucide="${mapel.icon}"></i>
                        </div>
                        <div>
                            <h2 class="text-2xl font-black text-white tracking-tight">${mapel.nama}</h2>
                            <p class="text-xs text-purple-400 font-extrabold mt-0.5">Cakupan Kelas 10, 11, & 12 • Kurikulum K13 & Merdeka</p>
                        </div>
                    </div>
                    <div class="space-y-6">
                        ${materiList.map((mat, idx) => `
                            <div class="bg-slate-900/90 border border-slate-800 p-6 rounded-2xl shadow-md hover:border-slate-700 transition">
                                <div class="flex items-center justify-between mb-3">
                                    <span class="text-[10px] font-extrabold uppercase tracking-wider bg-purple-500/20 text-purple-300 px-3 py-1 rounded-full border border-purple-500/30">${mat.kurikulum}</span>
                                    <span class="text-xs text-slate-500 font-mono">Modul #${idx + 1}</span>
                                </div>
                                <h3 class="text-lg font-extrabold text-white mb-3 leading-snug">${mat.title}</h3>
                                <p class="text-slate-300 text-xs sm:text-sm mb-4 leading-relaxed">${mat.summary}</p>
                                
                                <div class="bg-slate-950 p-4 rounded-xl font-mono text-xs text-purple-300 mb-4 border border-slate-800/80 text-center overflow-x-auto">
                                    ${mat.visual}
                                </div>

                                <div class="bg-amber-500/10 border-l-4 border-amber-500 p-4 rounded-r-xl text-xs text-amber-200 mb-4 leading-relaxed">
                                    <strong class="font-extrabold text-amber-400 block mb-1">💡 Tips Cepat & Trik Solusi:</strong> ${mat.tips}
                                </div>

                                <div class="bg-slate-950/80 border border-slate-800 p-4 rounded-xl text-xs text-slate-300 leading-relaxed">
                                    <span class="text-emerald-400 font-extrabold block mb-2 text-xs">📝 Contoh Soal & Pembahasan HOTS:</span>
                                    ${mat.contohSoal}
                                </div>
                            </div>
                        `).join('')}
                    </div>
                `;
                lucide.createIcons();
            }
        }

        // Render UTBK Simulation Screen
        function renderUTBKScreen() {
            return `
                <div class="mb-8">
                    <h1 class="text-3xl font-black text-white tracking-tight">Simulasi TKA & UTBK SNBT 2026</h1>
                    <p class="text-slate-400 text-xs sm:text-sm mt-1">Uji pemahaman dengan timer interaktif, skor otomatis, dan penjelasan terperinci.</p>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <div class="gradient-card border border-slate-800 p-6 rounded-3xl flex flex-col justify-between shadow-xl">
                        <div>
                            <div class="w-12 h-12 rounded-2xl bg-amber-500/20 border border-amber-500/30 text-amber-400 flex items-center justify-center mb-4 font-black">
                                <i data-lucide="calculator" class="w-6 h-6"></i>
                            </div>
                            <span class="text-[10px] uppercase tracking-widest font-extrabold text-amber-400 bg-amber-500/10 px-2.5 py-1 rounded-md border border-amber-500/20">SNBT Standard</span>
                            <h3 class="text-xl font-extrabold text-white mt-3 mb-1">UTBK - Pengetahuan Kuantitatif</h3>
                            <p class="text-slate-400 text-xs mb-6 leading-relaxed">Uji pemahaman aljabar, eksponen, logaritma, & deret matematika HOTS.</p>
                        </div>
                        <button onclick="startSimulasi('utbk-pk')" class="w-full py-3.5 bg-amber-500 hover:bg-amber-400 text-slate-950 font-black text-xs rounded-xl transition shadow-lg shadow-amber-500/20 flex items-center justify-center gap-2">
                            <i data-lucide="play" class="w-4 h-4 fill-current"></i> Mulai Tes Pengetahuan Kuantitatif
                        </button>
                    </div>

                    <div class="gradient-card border border-slate-800 p-6 rounded-3xl flex flex-col justify-between shadow-xl">
                        <div>
                            <div class="w-12 h-12 rounded-2xl bg-indigo-500/20 border border-indigo-500/30 text-indigo-400 flex items-center justify-center mb-4 font-black">
                                <i data-lucide="zap" class="w-6 h-6"></i>
                            </div>
                            <span class="text-[10px] uppercase tracking-widest font-extrabold text-indigo-400 bg-indigo-500/10 px-2.5 py-1 rounded-md border border-indigo-500/20">TKA High Level</span>
                            <h3 class="text-xl font-extrabold text-white mt-3 mb-1">TKA Saintek - Fisika HOTS</h3>
                            <p class="text-slate-400 text-xs mb-6 leading-relaxed">Uji penalaran fisika mekanika, vektor, dan Hukum Newton.</p>
                        </div>
                        <button onclick="startSimulasi('tka-saintek')" class="w-full py-3.5 bg-indigo-600 hover:bg-indigo-500 text-white font-black text-xs rounded-xl transition shadow-lg shadow-indigo-600/20 flex items-center justify-center gap-2">
                            <i data-lucide="play" class="w-4 h-4 fill-current"></i> Mulai Tes TKA Fisika
                        </button>
                    </div>

                    <div class="gradient-card border border-slate-800 p-6 rounded-3xl flex flex-col justify-between shadow-xl">
                        <div>
                            <div class="w-12 h-12 rounded-2xl bg-emerald-500/20 border border-emerald-500/30 text-emerald-400 flex items-center justify-center mb-4 font-black">
                                <i data-lucide="book-marked" class="w-6 h-6"></i>
                            </div>
                            <span class="text-[10px] uppercase tracking-widest font-extrabold text-emerald-400 bg-emerald-500/10 px-2.5 py-1 rounded-md border border-emerald-500/20">General Literacy</span>
                            <h3 class="text-xl font-extrabold text-white mt-3 mb-1">Literasi Bahasa & Penalaran</h3>
                            <p class="text-slate-400 text-xs mb-6 leading-relaxed">Uji pemahaman ide pokok, simpulan bacaan, & analisis paragraf.</p>
                        </div>
                        <button onclick="startSimulasi('lit-ind-eng')" class="w-full py-3.5 bg-emerald-600 hover:bg-emerald-500 text-white font-black text-xs rounded-xl transition shadow-lg shadow-emerald-600/20 flex items-center justify-center gap-2">
                            <i data-lucide="play" class="w-4 h-4 fill-current"></i> Mulai Tes Literasi
                        </button>
                    </div>
                </div>
            `;
        }

        // Active Simulation Engine
        function startSimulasi(simKey) {
            state.activeSimKey = simKey;
            state.currentSimAnswers = {};
            const currentSim = db.simulasiBank[simKey];
            
            const app = document.getElementById('app-content');
            app.innerHTML = `
                <div class="max-w-3xl mx-auto gradient-card border border-slate-800 p-6 sm:p-8 rounded-3xl shadow-2xl">
                    <div class="flex items-center justify-between pb-6 border-b border-slate-800 mb-6">
                        <div>
                            <span class="text-xs font-extrabold text-purple-400 tracking-wider uppercase">Simulasi Interaktif Berjalan</span>
                            <h2 class="text-xl font-black text-white mt-0.5">${currentSim.title}</h2>
                        </div>
                        <div class="bg-slate-900 border border-slate-800 px-4 py-2 rounded-xl text-right">
                            <span class="text-[10px] text-slate-400 uppercase font-extrabold block">Jumlah Soal</span>
                            <span class="text-sm font-black text-purple-300 font-mono">${currentSim.soal.length} Soal</span>
                        </div>
                    </div>

                    <div id="quiz-container" class="space-y-8">
                        ${currentSim.soal.map((q, idx) => `
                            <div class="bg-slate-900/90 p-6 rounded-2xl border border-slate-800">
                                <div class="flex items-center justify-between mb-3">
                                    <span class="text-xs font-bold text-purple-400 font-mono">Soal #${idx + 1}</span>
                                    <span class="text-[10px] text-slate-500 font-semibold">Tipe: Pilihan Ganda</span>
                                </div>
                                <p class="text-sm sm:text-base text-slate-100 font-medium mb-5 leading-relaxed">${q.pertanyaan}</p>
                                <div class="space-y-3">
                                    ${q.pilihan.map(opt => `
                                        <label class="flex items-center p-3.5 rounded-xl border border-slate-800 hover:bg-slate-800/80 hover:border-purple-500/50 transition cursor-pointer group">
                                            <input type="radio" name="question_${q.id}" value="${opt}" onchange="recordAnswer('${q.id}', '${opt}')" class="w-4 h-4 text-purple-600 focus:ring-purple-500 bg-slate-900 border-slate-700">
                                            <span class="ml-3.5 text-xs sm:text-sm text-slate-300 font-medium group-hover:text-white transition">${opt}</span>
                                        </label>
                                    `).join('')}
                                </div>
                            </div>
                        `).join('')}
                    </div>

                    <div class="mt-8 pt-6 border-t border-slate-800 flex justify-between items-center">
                        <button onclick="switchView('utbk')" class="px-5 py-2.5 border border-slate-800 text-slate-400 hover:text-white hover:bg-slate-800 text-xs font-extrabold rounded-xl transition">Batal</button>
                        <button onclick="submitSimulasi('${simKey}')" class="px-6 py-3.5 gradient-accent text-white font-black text-xs rounded-xl shadow-lg shadow-purple-500/25 hover:opacity-95 transition flex items-center gap-2">
                            <i data-lucide="check-circle" class="w-4 h-4"></i> Selesaikan & Simpan Hasil
                        </button>
                    </div>
                </div>
            `;
            lucide.createIcons();
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function recordAnswer(qId, val) {
            state.currentSimAnswers[qId] = val;
        }

        function submitSimulasi(simKey) {
            const sim = db.simulasiBank[simKey];
            let benarCount = 0;
            const total = sim.soal.length;

            const reviewDetails = sim.soal.map(q => {
                const userAns = state.currentSimAnswers[q.id] || 'Tidak Dijawab';
                const isCorrect = userAns === q.kunci;
                if (isCorrect) benarCount++;
                return {
                    pertanyaan: q.pertanyaan,
                    jawabanUser: userAns,
                    kunci: q.kunci,
                    isCorrect: isCorrect,
                    solusi: q.solusiLengkap
                };
            });

            const score = Math.round((benarCount / total) * 100);
            const now = new Date();
            const dateStr = now.toLocaleDateString('id-ID', { day: 'numeric', month: 'short', year: 'numeric', hour: '2-digit', minute: '2-digit' }) + ' WIB';

            const attemptRecord = {
                id: 'att_' + Date.now(),
                judulSimulasi: sim.title,
                tanggal: dateStr,
                skor: score,
                benar: benarCount,
                totalSoal: total,
                detail: reviewDetails
            };

            state.attempts.push(attemptRecord);
            localStorage.setItem('nihiluxxy_attempts', JSON.stringify(state.attempts));

            switchView('riwayat');
            openDetailRiwayat(state.attempts.length - 1);
        }

        // Render History Screen
        function renderRiwayatScreen() {
            if (state.attempts.length === 0) {
                return `
                    <div class="mb-8">
                        <h1 class="text-3xl font-black text-white tracking-tight">Riwayat Pengerjaan</h1>
                        <p class="text-slate-400 text-xs sm:text-sm mt-1">Daftar evaluasi simulasi dan pembahasan akurat Anda.</p>
                    </div>
                    <div class="gradient-card border border-slate-800 rounded-3xl p-12 text-center text-slate-500 shadow-xl">
                        <div class="w-16 h-16 rounded-full bg-slate-900 border border-slate-800 flex items-center justify-center mx-auto mb-4 text-slate-600">
                            <i data-lucide="history" class="w-8 h-8"></i>
                        </div>
                        <p class="text-base font-extrabold text-slate-300">Belum Ada Riwayat Tersimpan</p>
                        <p class="text-xs text-slate-500 mt-1 mb-6">Selesaikan simulasi TKA/UTBK untuk mencatat riwayat jawaban akurat Anda di sini.</p>
                        <button onclick="switchView('utbk')" class="px-6 py-3 bg-purple-600 hover:bg-purple-500 text-white font-extrabold text-xs rounded-xl transition shadow-lg shadow-purple-600/25">
                            Mulai Simulasi Sekarang
                        </button>
                    </div>
                `;
            }

            return `
                <div class="mb-8 flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                    <div>
                        <h1 class="text-3xl font-black text-white tracking-tight">Riwayat & Pembahasan Akurat</h1>
                        <p class="text-slate-400 text-xs sm:text-sm mt-1">Pilih pengerjaan di bawah untuk memeriksa kunci jawaban & cara pengerjaan terperinci.</p>
                    </div>
                    <button onclick="clearHistory()" class="px-4 py-2 border border-rose-500/30 text-rose-400 hover:bg-rose-500/10 text-xs font-bold rounded-xl transition self-start sm:self-auto flex items-center gap-1.5">
                        <i data-lucide="trash-2" class="w-4 h-4"></i> Hapus Semua Riwayat
                    </button>
                </div>

                <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
                    <div class="lg:col-span-4 space-y-3">
                        <h3 class="text-xs uppercase tracking-wider font-extrabold text-purple-400 px-1">Daftar Pengerjaan</h3>
                        ${state.attempts.map((att, idx) => `
                            <button onclick="openDetailRiwayat(${idx})" id="att-btn-${idx}" class="w-full text-left p-4 rounded-2xl bg-slate-900/60 border border-slate-800 hover:bg-slate-800 transition flex items-center justify-between group">
                                <div>
                                    <span class="text-[10px] text-slate-500 font-mono block">${att.tanggal}</span>
                                    <h4 class="font-extrabold text-xs sm:text-sm text-white group-hover:text-purple-300 transition mt-0.5">${att.judulSimulasi}</h4>
                                </div>
                                <span class="text-sm font-black text-purple-300 font-mono bg-purple-500/10 border border-purple-500/20 px-2.5 py-1 rounded-lg">${att.skor}%</span>
                            </button>
                        `).join('')}
                    </div>

                    <div id="riwayat-detail-container" class="lg:col-span-8 gradient-card border border-slate-800 rounded-3xl p-6 sm:p-8 shadow-2xl">
                        <!-- History details injected here -->
                    </div>
                </div>
            `;
        }

        function openDetailRiwayat(index) {
            state.attempts.forEach((_, i) => {
                const btn = document.getElementById(`att-btn-${i}`);
                if (btn) {
                    if (i === index) {
                        btn.className = "w-full text-left p-4 rounded-2xl bg-slate-800 border border-purple-500/80 flex items-center justify-between shadow-lg";
                    } else {
                        btn.className = "w-full text-left p-4 rounded-2xl bg-slate-900/60 border border-slate-800 hover:bg-slate-800 transition flex items-center justify-between group";
                    }
                }
            });

            const att = state.attempts[index];
            const container = document.getElementById('riwayat-detail-container');
            if (!container || !att) return;

            container.innerHTML = `
                <div class="flex items-center justify-between pb-6 border-b border-slate-800 mb-6">
                    <div>
                        <span class="text-xs text-purple-400 font-mono font-semibold block">${att.tanggal}</span>
                        <h2 class="text-xl font-black text-white mt-0.5">${att.judulSimulasi}</h2>
                    </div>
                    <div class="text-right">
                        <span class="text-3xl font-black text-purple-300 font-mono">${att.skor}%</span>
                        <p class="text-[10px] text-slate-400 font-bold mt-0.5">${att.benar} dari ${att.totalSoal} Soal Benar</p>
                    </div>
                </div>

                <div class="space-y-6">
                    ${att.detail.map((d, i) => `
                        <div class="bg-slate-900/90 border ${d.isCorrect ? 'border-emerald-500/40' : 'border-rose-500/40'} p-5 rounded-2xl shadow-md">
                            <div class="flex items-center justify-between mb-3">
                                <span class="text-xs font-bold text-slate-400 font-mono">Soal #${i + 1}</span>
                                <span class="text-[10px] font-extrabold px-2.5 py-1 rounded-full ${d.isCorrect ? 'bg-emerald-500/20 text-emerald-300 border border-emerald-500/30' : 'bg-rose-500/20 text-rose-300 border border-rose-500/30'}">
                                    ${d.isCorrect ? '✓ Jawaban Benar' : '✗ Kurang Tepat'}
                                </span>
                            </div>
                            <p class="text-xs sm:text-sm text-slate-200 font-medium mb-4 leading-relaxed">${d.pertanyaan}</p>
                            
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 mb-4 text-xs font-semibold">
                                <div class="bg-slate-950 p-3 rounded-xl border border-slate-800">
                                    <span class="text-slate-500 block text-[10px] font-mono">Jawaban Anda:</span>
                                    <span class="${d.isCorrect ? 'text-emerald-300' : 'text-rose-300'} font-bold">${d.jawabanUser}</span>
                                </div>
                                <div class="bg-slate-950 p-3 rounded-xl border border-slate-800">
                                    <span class="text-slate-500 block text-[10px] font-mono">Kunci Akurat:</span>
                                    <span class="text-emerald-300 font-bold">${d.kunci}</span>
                                </div>
                            </div>

                            <div class="bg-purple-950/30 border border-purple-800/40 p-4 rounded-xl text-xs text-slate-300 leading-relaxed">
                                <span class="text-purple-300 font-extrabold block mb-1 text-xs">📘 Pembahasan Akurat & Langkah Penyelesaian:</span>
                                ${d.solusi}
                            </div>
                        </div>
                    `).join('')}
                </div>
            `;
            lucide.createIcons();
        }

        function clearHistory() {
            if (confirm('Apakah Anda yakin ingin menghapus seluruh riwayat pengerjaan simulasi?')) {
                state.attempts = [];
                localStorage.removeItem('nihiluxxy_attempts');
                switchView('riwayat');
            }
        }

        // Initialize App Engine
        document.addEventListener('DOMContentLoaded', () => {
            switchView('home');
        });
    </script>
</body>
</html>
                                        
