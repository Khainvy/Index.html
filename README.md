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
        <span class="hidden sm:inline">⚡ Edisi Pengayaan Terintegrasi & Komprehensif: Persiapan SNBT 2026 & Ujian SMA</span>
        <span class="mx-auto sm:mx-0">🎉 Penjelasan Lebih Detail, Intuitive & Langkah Penyelesaian Transparan</span>
        <div class="hidden md:flex gap-4 text-[11px] font-semibold text-purple-300">
            <span>v4.0 Mega Edition</span>
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
                    <input type="text" id="global-search" oninput="handleGlobalSearch(this.value)" placeholder="Cari konsep (misal: Eksponen, Newton, Stoikiometri, Hereditas)..." class="w-full bg-slate-900/90 border border-slate-700/80 rounded-2xl pl-10 pr-4 py-2 text-xs text-slate-200 focus:outline-none focus:border-purple-500 transition">
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
                <span>Hak Cipta &copy; 2026. Seluruh Materi Terverifikasi Akademik Terperinci.</span>
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

        // Database Super Engine (Penjelasan Lebih Detail, Jelas, & Sangat Lengkap)
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
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Eksponen adalah bentuk perkalian berulang dari suatu bilangan dengan dirinya sendiri (contoh: aⁿ artinya a dikalikan sebanyak n kali). Bentuk akar merupakan bentuk lain untuk menyatakan bilangan berpangkat pecahan. Sedangkan Logaritma adalah operasi kebalikan (invers) dari eksponensial. Jika aⁿ = b, maka ᵃlog b = n.<br><br><strong>Mengapa Ini Penting?</strong> Logaritma digunakan dalam kehidupan nyata untuk mengukur tingkat keasaman (pH), skala magnitudo gempa bumi (Richter), serta intensitas bunyi (Desibel).<br><br><strong>Sifat-Sifat Kunci yang Wajib Dikuasai:</strong><br>1. aᵐ · aⁿ = aᵐ⁺ⁿ<br>2. aᵐ / aⁿ = aᵐ⁻ⁿ<br>3. (aᵐ)ⁿ = aᵐ·ⁿ<br>4. ᵃlog(b·c) = ᵃlog b + ᵃlog c<br>5. ᵃlog(b/c) = ᵃlog b - ᵃlog c<br>6. ᵃlog bⁿ = n · ᵃlog b',
                        visual: 'ᵃlog(b·c) = ᵃlog b + ᵃlog c | ᵃlog(b/c) = ᵃlog b - ᵃlog c | ᵃlog bⁿ = n · ᵃlog b',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Jika Anda bertemu soal persamaan eksponen bentuk a^(f(x)) = a^(g(x)), langkah pertamanya adalah samakan dahulu bilangan pokoknya (alas a). Setelah bilangan pokok sama, Anda cukup menyamakan pangkatnya: f(x) = g(x).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Jika diketahui ᵃlog b + ᵃlog b² = 12, tentukan nilai dari ᵃlog(a·b).<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Sederhanakan suku kedua menggunakan sifat pangkat logaritma (ᵃlog bⁿ = n · ᵃlog b).<br>&nbsp;&nbsp;&nbsp;ᵃlog b + 2 · ᵃlog b = 12<br><strong>Langkah 2:</strong> Gabungkan suku yang sejenis.<br>&nbsp;&nbsp;&nbsp;(1 + 2) · ᵃlog b = 12<br>&nbsp;&nbsp;&nbsp;3 · ᵃlog b = 12<br>&nbsp;&nbsp;&nbsp;ᵃlog b = 12 / 3 = 4.<br><strong>Langkah 3:</strong> Hitung nilai ᵃlog(a·b) dengan menggunakan sifat penjumlahan logaritma (ᵃlog(a·b) = ᵃlog a + ᵃlog b). Ingat bahwa ᵃlog a = 1.<br>&nbsp;&nbsp;&nbsp;ᵃlog(a·b) = ᵃlog a + ᵃlog b = 1 + 4 = 5.<br><br><strong>Jawaban Akhir:</strong> 5.'
                    },
                    {
                        title: '2. Persamaan Kuadrat & Fungsi Kuadrat (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Persamaan kuadrat adalah persamaan polimomial berderajat dua dengan bentuk umum ax² + bx + c = 0 (dengan a ≠ 0). Grafik dari fungsi kuadrat y = ax² + bx + c berbentuk kurva parabola.<br><br><strong>Analisis Karakteristik Kurva:</strong><br>1. <strong>Arah Terbuka:</strong> Jika a > 0, kurva terbuka ke atas (memiliki titik puncak minimum). Jika a < 0, kurva terbuka ke bawah (memiliki titik puncak maksimum).<br>2. <strong>Diskriminan (D = b² - 4ac):</strong> Memprediksi jumlah titik potong kurva dengan sumbu-X.<br>&nbsp;&nbsp;&nbsp;• D > 0: Memotong sumbu-X di dua titik berbeda (memiliki 2 akar real berbeda).<br>&nbsp;&nbsp;&nbsp;• D = 0: Menyinggung sumbu-X di satu titik (memiliki 2 akar real kembar/sama).<br>&nbsp;&nbsp;&nbsp;• D < 0: Tidak memotong sumbu-X (akar imajiner / tidak real).',
                        visual: 'Akar Vieta: x₁ + x₂ = -b/a | x₁·x₂ = c/a | Puncak Parabola: (-b / 2a , -D / 4a)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Gunakan Rumus Vieta tanpa perlu mencari nilai akar satu per satu! Jika ditanya penjumlahan akar (x₁ + x₂), gunakan -b/a. Jika ditanya perkalian akar (x₁ · x₂), gunakan c/a.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Persamaan kuadrat x² - (k + 2)x + 16 = 0 memiliki dua akar kembar positif. Tentukan nilai k yang memenuhi!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Syarat akar kembar adalah Diskriminan D = 0.<br>&nbsp;&nbsp;&nbsp;D = b² - 4ac = 0<br>&nbsp;&nbsp;&nbsp; (-(k + 2))² - 4(1)(16) = 0<br>&nbsp;&nbsp;&nbsp;(k + 2)² - 64 = 0  ⇒  (k + 2)² = 64<br>&nbsp;&nbsp;&nbsp;k + 2 = √64  ⇒  k + 2 = ±8.<br>&nbsp;&nbsp;&nbsp;Maka k₁ = 8 - 2 = 6, atau k₂ = -8 - 2 = -10.<br><strong>Langkah 2:</strong> Terapkan syarat bahwa akar-akarnya harus POSITIF.<br>&nbsp;&nbsp;&nbsp;Menurut Vieta, x₁ + x₂ = -b/a = (k + 2). Agar kedua akar positif, maka x₁ + x₂ > 0.<br>&nbsp;&nbsp;&nbsp;• Jika k = 6  ⇒  x₁ + x₂ = 6 + 2 = 8 > 0 (Memenuhi syarat).<br>&nbsp;&nbsp;&nbsp;• Jika k = -10 ⇒ x₁ + x₂ = -10 + 2 = -8 < 0 (Ditolak).<br><br><strong>Jawaban Akhir:</strong> Nilai k yang memenuhi adalah 6.'
                    },
                    {
                        title: '3. Sistem Persamaan & Pertidaksamaan Linear (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Sistem Persamaan Linear Tiga Variabel (SPLTV) terdiri atas 3 persamaan berpangkat satu yang saling terkait. Pemodelan ini digunakan untuk memecahkan masalah optimasi (program linear), seperti menentukan keuntungan maksimum produksi toko dengan batasan bahan baku baku.<br><br><strong>Langkah Umum Optimasi Program Linear:</strong><br>1. Buat pemodelan matematika berupa pertidaksamaan dari masalah verbal.<br>2. Gambar garis batas pertidaksamaan pada koordinat Cartesius.<br>3. Tentukan Daerah Himpunan Penyelesaian (DHP) yang memenuhi seluruh kendala.<br>4. Uji titik-titik pojok DHP ke dalam fungsi objektif z = ax + by.',
                        visual: 'Fungsi Objektif: Z = ax + by | Garis Selidik: ax + by = k',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Untuk menguji arah daerah arsiran pertidaksamaan linear ax + by ≤ c, pilihlah titik acuan termudah yaitu (0,0). Jika substitusi (0,0) bernilai BENAR, maka arsirlah daerah yang memuat titik (0,0).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Tentukan nilai maksimum dari fungsi sasaran f(x, y) = 3x + 4y pada daerah penyelesaian yang dibatasi oleh kendala: x + y ≤ 5, x ≥ 0, dan y ≥ 0.<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Tentukan titik potong garis x + y = 5 terhadap sumbu koordinat.<br>&nbsp;&nbsp;&nbsp;• Saat x = 0, y = 5 ⇒ Titik (0,5)<br>&nbsp;&nbsp;&nbsp;• Saat y = 0, x = 5 ⇒ Titik (5,0)<br><strong>Langkah 2:</strong> Kumpulkan seluruh titik pojok dari daerah himpunan penyelesaian (DHP), yaitu: (0,0), (5,0), dan (0,5).<br><strong>Langkah 3:</strong> Substitusikan titik pojok ke fungsi sasaran f(x,y) = 3x + 4y:<br>&nbsp;&nbsp;&nbsp;• f(0,0) = 3(0) + 4(0) = 0<br>&nbsp;&nbsp;&nbsp;• f(5,0) = 3(5) + 4(0) = 15<br>&nbsp;&nbsp;&nbsp;• f(0,5) = 3(0) + 4(5) = 20 (Nilai Terbesar)<br><br><strong>Jawaban Akhir:</strong> Nilai maksimumnya adalah 20.'
                    },
                    {
                        title: '4. Matriks & Operasi Matriks (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Matriks adalah susunan bilangan berbentuk persegi panjang yang diatur berdasarkan baris dan kolom. Operasi perkalian matriks A × B hanya dapat dilakukan jika **jumlah kolom matriks A sama dengan jumlah baris matriks B**.<br><br><strong>Sifat-Sifat Penting Matriks:</strong><br>1. Perkalian matriks **TIDAK bersifat komutatif**: A × B ≠ B × A.<br>2. Determinan perkalian: det(A · B) = det(A) · det(B).<br>3. Determinan invers: det(A⁻¹) = 1 / det(A).<br>4. Invers perkalian: (A · B)⁻¹ = B⁻¹ · A⁻¹.',
                        visual: 'Invers Matriks 2x2: A⁻¹ = (1 / det A) · [[d, -b], [-c, a]] | det A = ad - bc',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Jika Anda diminta mencari determinan dari invers matriks det(A⁻¹), Anda TIDAK PERLU menghitung bentuk matriks inversnya terlebih dahulu! Cukup hitung determinan awal det(A), lalu balik nilainya menjadi 1 / det(A).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Jika matriks A = [[2, 1], [4, 3]], tentukan nilai determinan dari matriks A⁻¹.<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Hitung determinan matriks A secara langsung.<br>&nbsp;&nbsp;&nbsp;det(A) = ad - bc = (2)(3) - (1)(4) = 6 - 4 = 2.<br><strong>Langkah 2:</strong> Terapkan sifat determinan invers det(A⁻¹) = 1 / det(A).<br>&nbsp;&nbsp;&nbsp;det(A⁻¹) = 1 / 2.<br><br><strong>Jawaban Akhir:</strong> 1/2.'
                    },
                    {
                        title: '5. Vektor pada Ruang Dimensi Dua & Tiga (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Vektor adalah besaran yang memiliki besar (panjang/magnitudo) dan arah. Dalam ruang dimensi 3, vektor dinyatakann dalam komponen i, j, dan k.<br><br><strong>Perkalian Skalar (Dot Product):</strong><br>Perkalian titik antara dua vektor u dan v didefinisikan sebagai:<br>u · v = |u| |v| cos θ = uₓvₓ + uᵧvᵧ + u_z v_z.<br><br><strong>Dua Vektor Tegak Lurus (Saling Ortogonal):</strong><br>Jika vektor u tegak lurus v, maka sudut θ = 90° (di mana cos 90° = 0). Sehingga perkalian skalarnya **selalu sama dengan NOL (u · v = 0)**.',
                        visual: 'u · v = |u||v| cos θ | Panjang Vektor |u| = √(x² + y² + z²)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Ingat kata kunci ortogonal! Ketika soal menyatakan dua vektor "saling tegak lurus", langsung tuliskan persamaan u · v = 0 untuk mencari variabel yang tidak diketahui.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Diketahui vektor u = (a, 2, 1) dan v = (3, -2, 4). Jika u dan v saling tegak lurus, hitunglah nilai a!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Karena u ⊥ v, maka hasil perkalian titik u · v = 0.<br><strong>Langkah 2:</strong> Kalikan komponen-komponen yang bersesuaian.<br>&nbsp;&nbsp;&nbsp;(a × 3) + (2 × -2) + (1 × 4) = 0<br>&nbsp;&nbsp;&nbsp;3a - 4 + 4 = 0<br>&nbsp;&nbsp;&nbsp;3a = 0  ⇒  a = 0.<br><br><strong>Jawaban Akhir:</strong> a = 0.'
                    },
                    {
                        title: '6. Trigonometri Analitis & Rumus Sudut (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Trigonometri mempelajari hubungan antara panjang sisi dan sudut pada segitiga. Rumus sudut ganda dan penjumlahan sudut memungkinkan kita menghitung nilai trigonometri sudut non-istimewa (seperti 75° atau 15°) tanpa kalkulator.<br><br><strong>Identitas & Rumus Penting:</strong><br>1. sin(A ± B) = sin A cos B ± cos A sin B<br>2. cos(A ± B) = cos A cos B ∓ sin A sin B<br>3. sin(2A) = 2 sin A cos A<br>4. cos(2A) = cos²A - sin²A = 2cos²A - 1 = 1 - 2sin²A',
                        visual: 'sin²θ + cos²θ = 1 | tan θ = sin θ / cos θ | cos(2A) = 1 - 2sin²A',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Untuk menghitung sudut tidak istimewa seperti 75°, ubahlah menjadi penjumlahan dua sudut istimewa yang Anda hafal, yaitu 75° = 45° + 30°.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Hitung nilai eksak dari sin(75°)!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Uraikan 75° menjadi (45° + 30°).<br><strong>Langkah 2:</strong> Gunakan rumus sin(A + B) = sin A cos B + cos A sin B.<br>&nbsp;&nbsp;&nbsp;sin(75°) = sin(45° + 30°)<br>&nbsp;&nbsp;&nbsp;= sin 45° · cos 30° + cos 45° · sin 30°<br><strong>Langkah 3:</strong> Substitusikan nilai sudut istimewa:<br>&nbsp;&nbsp;&nbsp;= (½ √2) · (½ √3) + (½ √2) · (½)<br>&nbsp;&nbsp;&nbsp;= ¼ √6 + ¼ √2 = ¼ (√6 + √2).<br><br><strong>Jawaban Akhir:</strong> ¼ (√6 + √2).'
                    },
                    {
                        title: '7. Barisan & Deret Aritmetika dan Geometri (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Barisan Aritmetika:</strong> Barisan bilangan di mana selisih antara dua suku berurutan (beda = b) selalu tetap.<br>• <strong>Barisan Geometri:</strong> Barisan bilangan di mana perbandingan antara dua suku berurutan (rasio = r) selalu tetap.<br>• <strong>Deret Geometri Tak Hingga Konvergen:</strong> Deret geometri yang menjumlahkan suku tak hingga banyaknya, namun nilainya mendekati suatu bilangan tetap. Syarat konvergen adalah rasio **-1 < r < 1**.',
                        visual: 'Aritmetika: Un = a + (n-1)b | Geometri: Un = a · rⁿ⁻¹ | Deret Tak Hingga: S_∞ = a / (1 - r)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Rumus Deret Tak Hingga S_∞ = a / (1 - r) sering dijuluki rumus **"A-BAH"** (a dibagi 1 minus r) untuk mempermudah ingatan visual Anda!',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Sebuah bola dijatuhkan dari ketinggian 12 meter dan memantul kembali dengan ketinggian 2/3 dari tinggi sebelumnya secara terus menerus. Tentukan total panjang lintasan bola sampai berhenti!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Lintasan bola terdiri dari **lintasan turun** dan **lintasan naik**.<br><strong>Langkah 2:</strong> Gunakan rumus praktis pemantulan bola: Total Panjang = h × ((p + q) / (q - p)), di mana r = p/q = 2/3 dan h = 12.<br>&nbsp;&nbsp;&nbsp;Total Panjang = 12 × ((2 + 3) / (3 - 2))<br>&nbsp;&nbsp;&nbsp;= 12 × (5 / 1) = 60 meter.<br><br><strong>Jawaban Akhir:</strong> 60 meter.'
                    },
                    {
                        title: '8. Limit Fungsi Aljabar & Trigonometri (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Limit menjelaskan perilaku suatu fungsi ketika variabel inputnya mendekati suatu titik tertentu. Jika hasil substitusi langsung menghasilkan bentuk tak tentu (seperti 0/0 atau ∞/∞), kita harus menyederhanakannya dengan faktorisasi, mengalikan sekawan, atau menggunakan aturan L\'Hopital.<br><br><strong>Aturan L\'Hopital:</strong><br>Jika lim(x→c) f(x)/g(x) = 0/0, maka lim(x→c) f(x)/g(x) = lim(x→c) f\'(x)/g\'(x) (menurunkan pembilang dan penyebut secara terpisah).',
                        visual: 'lim(x→0) sin(ax) / bx = a / b | lim(x→0) tan(ax) / bx = a / b | L\'Hopital: f\'(x) / g\'(x)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Untuk limit trigonometri mendekati 0, Anda dapat menghapus fungsi sin dan tan, lalu langsung mengambil koefisien variabelnya! Contoh: lim(x→0) sin(3x) / tan(5x) = 3/5.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Hitunglah nilai dari lim(x→2) (x² - 4) / (x - 2).<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Substitusi langsung x = 2 ⇒ (2² - 4)/(2 - 2) = 0/0 (Bentuk Tak Tentu).<br><strong>Langkah 2 (Aturan L\'Hopital):</strong> Turunkan pembilang dan penyebut terhadap x.<br>&nbsp;&nbsp;&nbsp;• Turunan pembilang (x² - 4) adalah 2x.<br>&nbsp;&nbsp;&nbsp;• Turunan penyebut (x - 2) adalah 1.<br><strong>Langkah 3:</strong> Hitung limit hasil turunan tersebut:<br>&nbsp;&nbsp;&nbsp;lim(x→2) (2x / 1) = 2(2) = 4.<br><br><strong>Jawaban Akhir:</strong> 4.'
                    },
                    {
                        title: '9. Turunan Fungsi (Diferensial) & Aplikasi (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Turunan f\'(x) mengukur laju perubahan instan dari fungsi f(x). Aplikasi turunan sangat luas, mulai dari menentukan kemiringan garis singgung kurva, menentukan interval fungsi naik/turun, hingga mencari nilai maksimum/minimum (titik stasioner).<br><br><strong>Kriteria Penting:</strong><br>1. Titik Stasioner terjadi saat **f\'(x) = 0**.<br>2. Fungsi Naik saat **f\'(x) > 0**.<br>3. Fungsi Turun saat **f\'(x) < 0**.',
                        visual: 'Aturan Perkalian: (u·v)\' = u\'v + uv\' | Aturan Pembagian: (u/v)\' = (u\'v - uv\') / v²',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Dalam soal aplikasi ekonomi (mencari keuntungan maksimum), tentukan fungsi Keuntungan L(x) = Pendapatan - Biaya. Keuntungan maksimum selalu tercapai saat turunan pertamanya L\'(x) = 0.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Tentukan nilai x yang membuat fungsi f(x) = x³ - 3x² - 9x + 5 mencapai nilai stasioner!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Cari turunan pertama fungsi f\'(x).<br>&nbsp;&nbsp;&nbsp;f\'(x) = 3x² - 6x - 9.<br><strong>Langkah 2:</strong> Syarat stasioner adalah f\'(x) = 0.<br>&nbsp;&nbsp;&nbsp;3x² - 6x - 9 = 0<br><strong>Langkah 3:</strong> Bagilah kedua ruas dengan 3 untuk mempermudah faktorisasi.<br>&nbsp;&nbsp;&nbsp;x² - 2x - 3 = 0  ⇒  (x - 3)(x + 1) = 0.<br>&nbsp;&nbsp;&nbsp;Sehingga x = 3 atau x = -1.<br><br><strong>Jawaban Akhir:</strong> Nilai x stasioner adalah x = 3 dan x = -1.'
                    },
                    {
                        title: '10. Integral Tentu & Tak Tentu (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Integral adalah operasi kebalikan dari turunan (antiturunan). Integral tak tentu menghasilkan fungsi baru yang memuat konstanta +C, sedangkan integral tentu memuat batas atas dan batas bawah yang menghasilkan nilai numerik pasti (digunakan untuk menghitung luas daerah di bawah kurva).<br><br><strong>Rumus Dasar:</strong><br>∫ xⁿ dx = (1 / (n + 1)) xⁿ⁺¹ + C (untuk n ≠ -1).',
                        visual: '∫ xⁿ dx = [1 / (n+1)] xⁿ⁺¹ + C | Integral Parsial: ∫ u dv = u v - ∫ v du',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Jika Anda menemui perkalian dua fungsi yang tidak bisa diselesaikan dengan substitusi biasa, gunakan metode Integral Parsial dengan rumus baku "u v - ∫ v du".',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Hitunglah nilai dari integral tentu ∫₁³ (3x² + 2x) dx!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Cari antiturunan dari (3x² + 2x).<br>&nbsp;&nbsp;&nbsp;∫ (3x² + 2x) dx = x³ + x².<br><strong>Langkah 2:</strong> Evaluasi menggunakan batas atas (3) dan batas bawah (1).<br>&nbsp;&nbsp;&nbsp;[x³ + x²]₁³ = (3³ + 3²) - (1³ + 1²)<br>&nbsp;&nbsp;&nbsp;= (27 + 9) - (1 + 1) = 36 - 2 = 34.<br><br><strong>Jawaban Akhir:</strong> 34.'
                    }
                ],
                'fis': [
                    {
                        title: '1. Besaran, Satuan, Pengukuran & Vektor (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Pengukuran merupakan proses membandingkan suatu besaran dengan besaran standar (satuan SI). Alat ukur panjang memiliki tingkat ketelitian berbeda: Mistar (1 mm), Jangka Sorong (0,1 mm), dan Mikrometer Sekrup (0,01 mm).<br><br><strong>Aturan Angka Penting (AP):</strong><br>1. Semua angka bukan nol adalah angka penting.<br>2. Angka nol di antara angka bukan nol adalah angka penting (contoh: 105 memiliki 3 AP).<br>3. Hasil perkalian/pembagian AP harus mengikuti jumlah angka penting **paling sedikit** dari bilangan yang dioperasikan.',
                        visual: 'Jangka Sorong (0,1 mm) | Mikrometer Sekrup (0,01 mm) | Resultan R = √(F₁² + F₂² + 2F₁F₂ cos θ)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Cara membaca mikrometer sekrup: Angka di skala utama (mm) ditambah dengan (angka skala nonius yang berhimpit × 0,01 mm).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Suatu pengukuran dengan mikrometer sekrup menunjukkan skala utama 4,5 mm dan garis nonius ke-25 berhimpit lurus. Berapakah tebal benda tersebut?<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Skala Utama (SU) = 4,5 mm.<br><strong>Langkah 2:</strong> Skala Nonius (SN) = 25 × 0,01 mm = 0,25 mm.<br><strong>Langkah 3:</strong> Jumlahkan kedua skala:<br>&nbsp;&nbsp;&nbsp;Tebal = SU + SN = 4,5 mm + 0,25 mm = 4,75 mm.<br><br><strong>Jawaban Akhir:</strong> 4,75 mm.'
                    },
                    {
                        title: '2. Kinematika Gerak Lurus & Parabola (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>GLB:</strong> Gerak dengan kecepatan konstan (percepatan a = 0).<br>• <strong>GLBB:</strong> Gerak dengan percepatan konstan.<br>• <strong>Gerak Parabola:</strong> Perpaduan dua gerak independen, yaitu **GLB pada sumbu horizontal (X)** dan **GLBB pada sumbu vertikal (Y)** karena pengaruh gravitasi.',
                        visual: 'GLBB: vₜ = v₀ + a·t | s = v₀t + ½at² | vₜ² = v₀² + 2as',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Pada titik tertinggi gerak parabola, kecepatan arah vertikal (v_y) selalu sama dengan NOL! Namun kecepatan arah horizontal (v_x) tetap ada dan bernilai v₀ cos θ.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Sebuah batu dilempar vertikal ke atas dengan kecepatan awal 20 m/s. Jika percepatan gravitasi g = 10 m/s², hitunglah ketinggian maksimum yang dicapai batu tersebut!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Di titik tertinggi, kecepatan akhir vₜ = 0 m/s.<br><strong>Langkah 2:</strong> Gunakan rumus GLBB diperlambat vₜ² = v₀² - 2gh.<br>&nbsp;&nbsp;&nbsp;0 = (20)² - 2(10)h<br>&nbsp;&nbsp;&nbsp;0 = 400 - 20h<br>&nbsp;&nbsp;&nbsp;20h = 400  ⇒  h = 20 meter.<br><br><strong>Jawaban Akhir:</strong> 20 meter.'
                    },
                    {
                        title: '3. Dinamika Gerak & Hukum Newton (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Dinamika mempelajari penyebab gerak benda, yaitu Gaya (F).<br>1. <strong>Hukum I Newton (Inersia):</strong> ΣF = 0 (Benda cenderung mempertahankan posisinya).<br>2. <strong>Hukum II Newton:</strong> ΣF = m · a (Percepatan berbanding lurus dengan gaya dan berbanding terbalik dengan massa).<br>3. <strong>Hukum III Newton (Aksi-Reaksi):</strong> F_aksi = -F_reaksi (Sama besar, berlawanan arah, bekerja pada dua benda berbeda).',
                        visual: 'ΣF = m · a | Gaya Gesek: f_g = μ · N | Gaya Normal Bidang Miring: N = m·g cos θ',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Ketika menganalisis benda pada bidang miring licin bernilai sudut θ, gaya pendorong searah kemiringan bidang adalah selalu **m · g · sin θ**.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Sebuah balok bermassa 4 kg ditarik gaya horizontal sebesar 20 N di atas lantai licin. Hitung percepatan balok tersebut!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Karena lantai licin, gaya gesek f_g = 0.<br><strong>Langkah 2:</strong> Terapkan Hukum II Newton ΣF = m · a.<br>&nbsp;&nbsp;&nbsp;20 = 4 · a  ⇒  a = 20 / 4 = 5 m/s².<br><br><strong>Jawaban Akhir:</strong> 5 m/s².'
                    },
                    {
                        title: '4. Usaha, Energi & Hukum Kekekalan Energi (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Usaha (W) terjadi ketika gaya yang bekerja berhasil memindahkan posisi benda (W = F · s cos θ). Energi tidak dapat diciptakan atau dimusnahkan, melainkan hanya berubah bentuk (Hukum Kekekalan Energi Mekanik).<br><br><strong>Bentuk Energi Mekanik:</strong><br>1. **Energi Kinetik (EK):** Energi karena gerak (EK = ½ m v²).<br>2. **Energi Potensial (EP):** Energi karena posisi/ketinggian (EP = m g h).',
                        visual: 'EM = EP + EK | W = ΔEK = ½m(v₂² - v₁²) | W = F · s cos θ',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Pada gerak jatuh bebas tanpa gesekan udara, pengurangan Energi Potensial sebanding dengan pertambahan Energi Kinetik (ΔEP = ΔEK).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Benda bermassa 2 kg jatuh bebas dari ketinggian 10 m (g = 10 m/s²). Hitung energi kinetik benda saat berada pada ketinggian 2 m dari tanah!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Terapkan Hukum Kekekalan Energi Mekanik (EM₁ = EM₂).<br>&nbsp;&nbsp;&nbsp;EP₁ + EK₁ = EP₂ + EK₂<br><strong>Langkah 2:</strong> Karena jatuh bebas dari keadaan diam, maka EK₁ = 0.<br>&nbsp;&nbsp;&nbsp;m·g·h₁ + 0 = m·g·h₂ + EK₂<br>&nbsp;&nbsp;&nbsp;(2)(10)(10) = (2)(10)(2) + EK₂<br>&nbsp;&nbsp;&nbsp;200 = 40 + EK₂  ⇒  EK₂ = 200 - 40 = 160 Joule.<br><br><strong>Jawaban Akhir:</strong> 160 Joule.'
                    },
                    {
                        title: '5. Momentum, Impuls & Tumbukan (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Momentum (p = m · v) menggambarkan tingkat kesukaran untuk menghentikan benda yang bergerak. Impuls (I = F · Δt) adalah perubahan momentum (I = Δp).<br><br><strong>Jenis-Jenis Tumbukan:</strong><br>1. <strong>Lenting Sempurna (e = 1):</strong> Berlaku kekekalan momentum & kekekalan energi kinetik.<br>2. <strong>Lenting Sebagian (0 < e < 1):</strong> Energi kinetik berkurang.<br>3. <strong>Tidak Lenting Sama Sekali (e = 0):</strong> Kedua benda **menempel dan bergerak bersama** setelah tumbukan (v₁\' = v₂\' = v\').',
                        visual: 'I = F · Δt = m(v₂ - v₁) | Tumbukan e=0: m₁v₁ + m₂v₂ = (m₁ + m₂)v\'',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Ingat kata kunci "setelah bertumbukan benda menyatu"! Ini menandakan tumbukan tidak lenting sama sekali (e = 0). Langsung gunakan rumus gabungan massa (m₁ + m₂) v\'.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Mobil A (massa 1000 kg, kecepatan 20 m/s) menabrak mobil B (massa 1000 kg yang sedang berhenti) dari belakang, lalu keduanya menyatu. Berapakah kecepatan kedua mobil setelah benturan?<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Gunakan Hukum Kekekalan Momentum untuk tumbukan menyatu (e=0).<br>&nbsp;&nbsp;&nbsp;m_A · v_A + m_B · v_B = (m_A + m_B) v\'<br><strong>Langkah 2:</strong> Substitusikan data (v_B = 0 karena berhenti):<br>&nbsp;&nbsp;&nbsp;(1000 × 20) + (1000 × 0) = (1000 + 1000) v\'<br>&nbsp;&nbsp;&nbsp;20000 = 2000 v\'  ⇒  v\' = 20000 / 2000 = 10 m/s.<br><br><strong>Jawaban Akhir:</strong> 10 m/s.'
                    },
                    {
                        title: '6. Gelombang Bunyi & Gelombang Cahaya (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Efek Doppler:</strong> Perubahan frekuensi bunyi yang didengar oleh pengamat akibat adanya gerak relatif antara sumber bunyi dan pengamat.<br>• <strong>Aturan Tanda Efek Doppler:</strong><br>&nbsp;&nbsp;- Pendengar **Mendekat** (+), Pendengar **Menjauh** (-)<br>&nbsp;&nbsp;- Sumber **Mendekat** (-), Sumber **Menjauh** (+)',
                        visual: 'Efek Doppler: f_p = [(v ± v_p) / (v ± v_s)] · f_s | Interferensi: d sin θ = n λ',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Jembatan keledai Efek Doppler: **"Pendengar mendekat bernilai Positif (+), Sumber mendekat bernilai Negatif (-)"**.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Ambulans bergerak dengan kecepatan 20 m/s mendekati seorang pengamat yang berdiri diam di pinggir jalan sambil membunyikan sirine berfrekuensi 640 Hz. Jika cepat rambat bunyi di udara 340 m/s, hitung frekuensi yang didengar pengamat!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Tentukan komponen:<br>&nbsp;&nbsp;&nbsp;• v = 340 m/s, v_p = 0 (Pengamat diam)<br>&nbsp;&nbsp;&nbsp;• v_s = -20 m/s (Sumber mendekat, tanda minus)<br>&nbsp;&nbsp;&nbsp;• f_s = 640 Hz<br><strong>Langkah 2:</strong> Substitusi ke rumus Efek Doppler:<br>&nbsp;&nbsp;&nbsp;f_p = [(340 + 0) / (340 - 20)] × 640<br>&nbsp;&nbsp;&nbsp;f_p = (340 / 320) × 640 = 340 × 2 = 680 Hz.<br><br><strong>Jawaban Akhir:</strong> 680 Hz.'
                    },
                    {
                        title: '7. Termodinamika & Mesin Heat (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Termodinamika mempelajari perubahan energi panas (kalor) menjadi usaha mekanik. Mesin Carnot adalah mesin kalor ideal yang bekerja dengan efisiensi tertinggi.<br><br><strong>Syarat Suhu Mutlak:</strong><br>Dalam seluruh perhitungan termodinamika, satuan suhu **WAJIB diubah ke Kelvin (K)** dengan menambah angka **273** (K = °C + 273).',
                        visual: 'Q = ΔU + W | Efisiensi Carnot: η = (1 - T₂ / T₁) × 100%',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Ingat bahwa T₁ adalah suhu reservoir panas (suhu lebih tinggi) dan T₂ adalah suhu reservoir dingin (suhu lebih rendah).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Sebuah mesin Carnot bekerja di antara suhu tinggi 327°C dan suhu rendah 27°C. Hitunglah efisiensi mesin Carnot tersebut!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Konversikan suhu dari Celsius ke Kelvin.<br>&nbsp;&nbsp;&nbsp;• T₁ = 327 + 273 = 600 K<br>&nbsp;&nbsp;&nbsp;• T₂ = 27 + 273 = 300 K<br><strong>Langkah 2:</strong> Hitung efisiensi (η):<br>&nbsp;&nbsp;&nbsp;η = (1 - T₂ / T₁) × 100%<br>&nbsp;&nbsp;&nbsp;η = (1 - 300 / 600) × 100% = (1 - 0.5) × 100% = 50%.<br><br><strong>Jawaban Akhir:</strong> 50%.'
                    },
                    {
                        title: '8. Listrik Statis & Listrik Dinamis (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Gaya Coulomb (Listrik Statis):</strong> Gaya tarik-menarik atau tolak-menolak antara dua muatan listrik (F = k · |q₁ q₂| / r²).<br>• <strong>Hukum Ohm (Listrik Dinamis):</strong> V = I · R.<br>• <strong>Hukum Kirchhoff II:</strong> Dalam suatu rangkaian tertutup (loop), jumlah aljabar GGL (E) dan beda potensial (I·R) sama dengan nol (ΣE + Σ(I·R) = 0).',
                        visual: 'F = k · |q₁q₂| / r² | V = I · R | Seri: R_total = R₁ + R₂ | Paralel: 1/R_total = 1/R₁ + 1/R₂',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Gaya Coulomb berbanding terbalik dengan kuadrat jarak (1/r²). Jika jarak antar muatan dijauhkan menjadi 2 kali lipat, maka gayanya menjadi (½)² = ¼ kali semula.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Dua muatan q₁ = +2 μC dan q₂ = +4 μC terpisah sejauh 3 cm di udara (k = 9×10⁹ N m²/C²). Hitung gaya Coulomb antara kedua muatan tersebut!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Ubah satuan ke standar SI:<br>&nbsp;&nbsp;&nbsp;• q₁ = 2 × 10⁻⁶ C, q₂ = 4 × 10⁻⁶ C<br>&nbsp;&nbsp;&nbsp;• r = 3 cm = 3 × 10⁻² m<br><strong>Langkah 2:</strong> Substitusikan ke rumus Hukum Coulomb:<br>&nbsp;&nbsp;&nbsp;F = (9×10⁹ × 2×10⁻⁶ × 4×10⁻⁶) / (3×10⁻²)²<br>&nbsp;&nbsp;&nbsp;F = (72 × 10⁻³) / (9 × 10⁻⁴)<br>&nbsp;&nbsp;&nbsp;F = 8 × 10¹ = 80 Newton.<br><br><strong>Jawaban Akhir:</strong> 80 N.'
                    },
                    {
                        title: '9. Medan Magnetik & Induksi Elektromagnetik (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Arus listrik yang mengalir pada kawat akan menghasilkan medan magnet di sekitarnya. Sebaliknya, perubahan fluks magnetik yang menembus kumparan akan menghasilkan arus listrik induksi (Hukum Faraday).<br><br><strong>Transformator (Trafo) Ideal:</strong><br>Alat untuk mengubah tegangan AC. Berlaku hubungan: **Vₚ / Vₛ = Nₚ / Nₛ = Iₛ / Iₚ**.',
                        visual: 'Gaya Lorentz: F = B · I · L sin θ | Trafo Ideal: Vₚ / Vₛ = Nₚ / Nₛ = Iₛ / Iₚ',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Pada trafo ideal, hubungan Tegangan (V) dan Lilitan (N) berbanding LURUS, namun berbanding TERBALIK dengan Arus Listrik (I).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Sebuah transformator step-up ideal memiliki jumlah lilitan primer 500 dan lilitan sekunder 1000. Jika tegangan pada kumparan primer adalah 110 Volt, hitung tegangan pada kumparan sekunder!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Gunakan rumus perbandingan trafo Vₚ / Vₛ = Nₚ / Nₛ.<br><strong>Langkah 2:</strong> Substitusikan angka:<br>&nbsp;&nbsp;&nbsp;110 / Vₛ = 500 / 1000<br>&nbsp;&nbsp;&nbsp;110 / Vₛ = 1 / 2  ⇒  Vₛ = 110 × 2 = 220 Volt.<br><br><strong>Jawaban Akhir:</strong> 220 Volt.'
                    },
                    {
                        title: '10. Fisika Modern & Relativitas (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Fisika Modern berkembang sejak munculnya Teori Relativitas Einstein dan Kuantum Cahaya. Cahaya memiliki sifat ganda (dualisme gelombang-partikel): dapat berperilaku sebagai gelombang sekaligus sebagai partikel energi (foton).<br><br><strong>Persamaan Kuantum Planck:</strong><br>Energi satu foton adalah **E = h · f** (h = konstanta Planck = 6,63 × 10⁻³⁴ J·s).',
                        visual: 'E = h · f = h · (c / λ) | Relativitas Massa: m = m₀ / √(1 - v²/c²)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Efek fotolistrik membuktikan bahwa cahaya berperilaku sebagai partikel (foton), di mana elektron hanya dapat keluar dari logam jika frekuensi cahaya lebih besar dari frekuensi ambang logam.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Hitung energi dari satu foton cahaya yang memiliki frekuensi 10¹⁵ Hz! (Gunakan h = 6,63 × 10⁻³⁴ J·s).<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Terapkan rumus energi foton E = h · f.<br><strong>Langkah 2:</strong> Substitusikan angka:<br>&nbsp;&nbsp;&nbsp;E = (6,63 × 10⁻³⁴ J·s) × (10¹⁵ s⁻¹)<br>&nbsp;&nbsp;&nbsp;E = 6,63 × 10⁻¹⁹ Joule.<br><br><strong>Jawaban Akhir:</strong> 6,63 × 10⁻¹⁹ Joule.'
                    }
                ],
                'kim': [
                    {
                        title: '1. Struktur Atom & Tabel Periodik Unsur (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Atom terdiri dari inti atom (proton & neutron) yang dikelilingi oleh elektron pada kulitnya. Posisi elektron ditentukan oleh 4 bilangan kuantum:<br>1. <strong>n (Utama):</strong> Menunjukkan nomor kulit (1, 2, 3, ...).<br>2. <strong>l (Azimut):</strong> Menunjukkan subkulit (s=0, p=1, d=2, f=3).<br>3. <strong>m (Magnetik):</strong> Menunjukkan orbital (-l sampai +l).<br>4. <strong>s (Spin):</strong> Arah putaran elektron (+½ atau -½).',
                        visual: 'Konfigurasi Kulit: 1s² 2s² 2p⁶ 3s² 3p⁶ 4s² 3d¹⁰ | Bilangan Kuantum s (+½ panah atas, -½ bawah)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Sifat periodik jari-jari atom semakin BESAR dari atas ke bawah dan semakin KECIL dari kiri ke kanan dalam tabel periodik.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Tentukan 4 bilangan kuantum elektron terakhir dari unsur ₁₁Na (Nomor atom = 11)!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Tuliskan konfigurasi elektron ₁₁Na: 1s² 2s² 2p⁶ 3s¹.<br><strong>Langkah 2:</strong> Elektron terakhir berada di subkulit 3s¹.<br>&nbsp;&nbsp;&nbsp;• n = 3 (Kulit ke-3)<br>&nbsp;&nbsp;&nbsp;• l = 0 (Subkulit s)<br>&nbsp;&nbsp;&nbsp;• m = 0 (Orbital s hanya ada 1 kotak = 0)<br>&nbsp;&nbsp;&nbsp;• s = +½ (Satu elektron mengarah ke atas).<br><br><strong>Jawaban Akhir:</strong> n=3, l=0, m=0, s=+½.'
                    },
                    {
                        title: '2. Ikatan Kimia & Bentuk Molekul (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Atom berikatan untuk mencapai kestabilan (konfigurasi oktet = 8 elektron valensi).<br>• <strong>Ikatan Ionik:</strong> Serah terima elektron (antara logam + non-logam).<br>• <strong>Ikatan Kovalen:</strong> Pemakaian bersama pasangan elektron (antara non-logam + non-logam).<br>• <strong>Bentuk Molekul (VSEPR):</strong> Ditentukan oleh jumlah Pasangan Elektron Ikatan (PEI) dan Pasangan Elektron Bebas (PEB).',
                        visual: 'AX₂ (Linear) | AX₃ (Trigonal Planar) | AX₄ (Tetrahedral) | AX₃E (Piramida Trigonal)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Jika suatu molekul memiliki Pasangan Elektron Bebas (PEB > 0) pada atom pusatnya, molekul tersebut hampir selalu bersifat POLAR (seperti H₂O atau NH₃).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Tentukan bentuk molekul dari CH₄ menurut teori VSEPR! (Nomor atom C = 6, H = 1).<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Elektron valensi atom pusat C = 4.<br><strong>Langkah 2:</strong> C mengikat 4 atom H, sehingga Pasangan Elektron Ikatan (PEI) = 4.<br><strong>Langkah 3:</strong> Pasangan Elektron Bebas PEB = (4 - 4) / 2 = 0.<br><strong>Langkah 4:</strong> Tipe molekulnya adalah AX₄, yang memiliki bentuk geometri Tetrahedral.<br><br><strong>Jawaban Akhir:</strong> Tetrahedral.'
                    },
                    {
                        title: '3. Stoikiometri & Hukum Dasar Kimia (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Stoikiometri adalah hitungan kimia berbasis Mol.<br>• <strong>1 Mol:</strong> Mengandung 6,02 × 10²³ zat (Bilangan Avogadro).<br>• <strong>Massa (gram):</strong> m = mol × Mr.<br>• <strong>Volume Gas STP (0°C, 1 atm):</strong> V = mol × 22,4 Liter.<br>• <strong>Pereaksi Pembatas:</strong> Reaktan yang habis bereaksi terlebih dahulu.',
                        visual: 'n = m / Mr | n = V / 22.4 (STP) | Molaritas M = n / V (Liter)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Untuk menentukan Pereaksi Pembatas, bagilah jumlah mol masing-masing reaktan dengan koefisien reaksinya. Nilai hasil bagi yang TERKECIL adalah pereaksi pembatasnya!',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Berapakah massa dari 0,5 mol H₂SO₄? (Diketahui Ar H=1, S=32, O=16).<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Hitung Massa Molar (Mr) H₂SO₄.<br>&nbsp;&nbsp;&nbsp;Mr = (2 × Ar H) + (1 × Ar S) + (4 × Ar O)<br>&nbsp;&nbsp;&nbsp;Mr = (2 × 1) + 32 + (4 × 16) = 2 + 32 + 64 = 98 g/mol.<br><strong>Langkah 2:</strong> Hitung massa = mol × Mr.<br>&nbsp;&nbsp;&nbsp;Massa = 0,5 mol × 98 g/mol = 49 gram.<br><br><strong>Jawaban Akhir:</strong> 49 gram.'
                    },
                    {
                        title: '4. Termokimia & Perubahan Entalpi (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Termokimia mempelajari perubahan kalor (Q) dalam reaksi kimia.<br>1. <strong>Reaksi Eksoterm:</strong> Reaksi yang melepaskan kalor ke lingkungan (ΔH bernilai **NEGATIF**). Suhu sistem naik.<br>2. <strong>Reaksi Endoterm:</strong> Reaksi yang menyerap kalor dari lingkungan (ΔH bernilai **POSITIF**). Suhu sistem turun.<br><br><strong>Hukum Hess:</strong> Perubahan entalpi reaksi hanya tergantung pada keadaan awal dan akhir, bukan pada tahapan reaksi.',
                        visual: 'Eksoterm (ΔH < 0, Lepas Kalor) | Endoterm (ΔH > 0, Serap Kalor) | Q = m · c · ΔT',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Jika reaksi kimia dibalik, maka nilai ΔH berubah tanda (positif menjadi negatif atau sebaliknya). Jika koefisien dikali n, maka ΔH juga dikali n.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Jika pembakaran 1 mol C(s) melepaskan kalor sebesar 393,5 kJ, tuliskan persamaan termokimianya!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> "Melepaskan kalor" menandakan reaksi Eksoterm, sehingga ΔH = -393,5 kJ/mol.<br><strong>Langkah 2:</strong> Tuliskan persamaan reaksi pembakaran sempurna karbon:<br>&nbsp;&nbsp;&nbsp;C(s) + O₂(g) → CO₂(g)   ΔH = -393,5 kJ/mol.<br><br><strong>Jawaban Akhir:</strong> C(s) + O₂(g) → CO₂(g) ΔH = -393,5 kJ/mol.'
                    },
                    {
                        title: '5. Laju Reaksi & Teori Tumbukan (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Laju reaksi adalah berkurangnya konsentrasi reaktan atau bertambahnya konsentrasi produk per satuan waktu.<br><br><strong>Faktor Mempercepat Laju Reaksi:</strong><br>1. <strong>Konsentrasi:</strong> Partikel semakin rapat, frekuensi tumbukan meningkat.<br>2. <strong>Luas Permukaan:</strong> Bidang sentuh makin luas.<br>3. <strong>Suhu:</strong> Energi kinetik molekul meningkat.<br>4. <strong>Katalis:</strong> Menurunkan **Energi Aktivasi (Ea)**.',
                        visual: 'Persamaan Laju: v = k [A]ˣ [B]ʸ | Kenaikan Suhu: v₂ = v₁ · (Δv)^[(T₂ - T₁) / ΔT]',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Rumus cepat kenaikan suhu: Setiap kenaikan suhu ΔT, laju menjadi n kali lipat. Gunakan rumus v₂ = v₁ × n^((T₂-T₁)/ΔT).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Suatu reaksi berlangsung 8 kali lebih cepat jika suhu dinaikkan dari 20°C ke 50°C. Jika setiap kenaikan 10°C laju reaksi menjadi n kali lipat, hitung nilai n tersebut!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Selisih suhu ΔT = 50 - 20 = 30°C. Jumlah kenaikan = 30 / 10 = 3 kali.<br><strong>Langkah 2:</strong> Kelipatan laju = n³ = 8.<br><strong>Langkah 3:</strong> n = ∛8 = 2.<br><br><strong>Jawaban Akhir:</strong> n = 2 (Laju menjadi 2 kali lipat setiap kenaikan 10°C).'
                    },
                    {
                        title: '6. Kesetimbangan Kimia & Le Chatelier (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Kesetimbangan dinamis terjadi ketika laju reaksi maju sama dengan laju reaksi balik. Hanya wujud **Gas (g) dan Larutan (aq)** yang dimasukkan ke dalam perhitungan konstanta kesetimbangan Kc.<br><br><strong>Azas Le Chatelier (Arah Pergeseran):</strong><br>• <strong>Konsentrasi:</strong> Ditambah → bergeser *menjauhi* arah zat tersebut.<br>• <strong>Tekanan/Volume:</strong> Tekanan diperbesar (volume diperkecil) → bergeser ke arah koefisien gas yang *lebih kecil*.',
                        visual: 'Kc = [Produk]ⁿ / [Reaktan]ᵐ | Kp = P_produkⁿ / P_reaktanᵐ',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Ingat kata kunci wujud! Zat berwujud padat murni (s) dan cair murni (l) DIABAIKAN (nilainya dianggap 1) dalam rumus Kc dan Kp.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Pada reaksi kesetimbangan: N₂(g) + 3H₂(g) ⇌ 2NH₃(g) ΔH = -92 kJ. Ke arah manakah kesetimbangan bergeser jika suhu dinaikkan?<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Reaksi pembentukan NH₃ (ke kanan) bersifat Eksoterm (ΔH = -92 kJ). Reaksi sebaliknya (ke kiri) bersifat Endoterm.<br><strong>Langkah 2:</strong> Kenaikan suhu selalu menggeser kesetimbangan ke arah reaksi **ENDOTERM** (menyerap panas).<br><strong>Langkah 3:</strong> Maka kesetimbangan akan bergeser ke arah Kiri (ke arah reaktan N₂ dan H₂).<br><br><strong>Jawaban Akhir:</strong> Bergeser ke arah Kiri.'
                    },
                    {
                        title: '7. Larutan Asam Basa & Garam (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Asam:</strong> Donor proton H⁺ (pH < 7).<br>• <strong>Basa:</strong> Akseptor proton H⁺ / menghasilkan OH⁻ (pH > 7).<br>• <strong>Hidrolisis Garam:</strong> Reaksi antara ion garam dengan air.<br>&nbsp;&nbsp;- Garam dari (Asam Kuat + Basa Lemah) bersifat **ASAM** (pH < 7).<br>&nbsp;&nbsp;- Garam dari (Asam Lemah + Basa Kuat) bersifat **BASA** (pH > 7).',
                        visual: 'pH = -log[H⁺] | Asam Lemah: [H⁺] = √(Ka · M) | pH + pOH = 14',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Garam yang terbentuk dari Asam Kuat + Basa Kuat (seperti NaCl) TIDAK mengalami hidrolisis dan memiliki pH Netral = 7.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Hitung pH dari larutan asam kuat HCl 0,001 M!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> HCl adalah asam kuat valensi 1, sehingga [H⁺] = Molaritas = 0,001 M = 10⁻³ M.<br><strong>Langkah 2:</strong> pH = -log[H⁺] = -log(10⁻³) = 3.<br><br><strong>Jawaban Akhir:</strong> pH = 3.'
                    },
                    {
                        title: '8. Larutan Penyangga (Buffer) & Ksp (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Larutan Penyangga (Buffer) adalah larutan yang mampu mempertahankan pH dari penambahan sedikit asam, basa, atau pengenceran. Buffer terbuat dari campuran **Asam Lemah + Basa Konjugasinya** atau **Basa Lemah + Asam Konjugasinya**.<br><br><strong>Hasil Kali Kelarutan (Ksp):</strong> Batas kelarutan maksimum zat terlarut dalam air sebelum membentuk endapan.',
                        visual: 'Buffer Asam: [H⁺] = Ka · (mol asam lemah / mol basa konjugasi)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Ciri khas soal larutan buffer adalah menyisakan komponen LEMAH setelah reaksi selesai.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Campuran 100 mL CH₃COOH 0,1 M (Ka = 10⁻⁵) dengan 50 mL CH₃COONa 0,1 M membentuk larutan buffer. Hitung pH larutan tersebut!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Hitung mol masing-masing komponen:<br>&nbsp;&nbsp;&nbsp;• mol CH₃COOH (Asam Lemah) = 100 mL × 0,1 M = 10 mmol.<br>&nbsp;&nbsp;&nbsp;• mol CH₃COONa (Basa Konjugasi) = 50 mL × 0,1 M = 5 mmol.<br><strong>Langkah 2:</strong> Substitusikan ke rumus buffer asam:<br>&nbsp;&nbsp;&nbsp;[H⁺] = Ka × (mol asam / mol basa konjugasi)<br>&nbsp;&nbsp;&nbsp;[H⁺] = 10⁻⁵ × (10 / 5) = 2 × 10⁻⁵ M.<br><strong>Langkah 3:</strong> pH = -log(2 × 10⁻⁵) = 5 - log 2.<br><br><strong>Jawaban Akhir:</strong> pH = 5 - log 2.'
                    },
                    {
                        title: '9. Elektrokimia: Sel Volta & Elektrolisis (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Sel Volta:</strong> Reaksi kimia spontan menghasilkan energi listrik (Contoh: Baterai, Aki). Singkatan KRAP: **K**atoda **R**eduksi (**A**noda **P**ositif).<br>• <strong>Sel Elektrolisis:</strong> Energi listrik digunakan untuk menjalankan reaksi kimia tidak spontan.<br><br><strong>Potensial Sel Standar:</strong> E°sel = E°katoda - E°anoda.',
                        visual: 'E°sel = E°katoda - E°anoda | Hukum Faraday I: w = (e · i · t) / 96500',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Logam yang memiliki potensial E° lebih POSITIF selalu bertindak sebagai **KATODA** (tempat terjadinya reduksi).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Diketahui E° Zn²⁺/Zn = -0,76 V dan E° Cu²⁺/Cu = +0,34 V. Hitunglah E°sel dari sel Volta tersebut!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Tentukan Katoda dan Anoda:<br>&nbsp;&nbsp;&nbsp;• Cu²⁺/Cu memiliki E° lebih positif (+0,34 V) ⇒ Katoda.<br>&nbsp;&nbsp;&nbsp;• Zn²⁺/Zn memiliki E° lebih negatif (-0,76 V) ⇒ Anoda.<br><strong>Langkah 2:</strong> Hitung E°sel = E°katoda - E°anoda:<br>&nbsp;&nbsp;&nbsp;E°sel = (+0,34 V) - (-0,76 V) = +1,10 Volt.<br><br><strong>Jawaban Akhir:</strong> +1,10 Volt.'
                    },
                    {
                        title: '10. Kimia Karbon & Senyawa Makromolekul (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Kimia Karbon mempelajari senyawa turunan alkana berdasarkan gugus fungsinya:<br>1. **Alkohol (-OH)** vs **Eter (-O-)** [Isomer Fungsi]<br>2. **Aldehid (-CHO)** vs **Keton (-CO-)** [Isomer Fungsi]<br>3. **Asam Karboksilat (-COOH)** vs **Ester (-COO-)** [Isomer Fungsi]',
                        visual: 'Aldehid (+ Fehling/Tollens merah bata) vs Keton (- Tidak bereaksi)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Untuk membedakan Aldehid dan Keton di laboratorium, gunakan pereaksi Fehling atau Tollens. Aldehid menghasilkan endapan merah bata (Fehling) atau cermin perak (Tollens), sedangkan Keton tidak bereaksi.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Senyawa C₃H₆O bereaksi positif membentuk cermin perak dengan pereaksi Tollens. Tentukan nama IUPAC senyawa tersebut!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Rumus C₃H₆O mengikuti C_n H_2n O (Aldehid atau Keton).<br><strong>Langkah 2:</strong> Karena bereaksi positif dengan Tollens, senyawa tersebut pasti golongan **ALDEHID**.<br><strong>Langkah 3:</strong> Aldehid dengan 3 atom karbon memiliki nama IUPAC Propanal.<br><br><strong>Jawaban Akhir:</strong> Propanal.'
                    }
                ],
                'bio': [
                    {
                        title: '1. Ruang Lingkup Biologi & Keanekaragaman Hayati (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Biologi mengkaji struktur kehidupan dari tingkat molekul, sel, jaringan, organ, sistem organ, individu, populasi, komunitas, ekosistem, hingga bioma.<br><br><strong>3 Tingkat Keanekaragaman Hayati:</strong><br>1. <strong>Tingkat Gen:</strong> Variasi dalam satu spesies (Contoh: Mawar merah, putih, kuning).<br>2. <strong>Tingkat Jenis (Spesies):</strong> Variasi antar spesies berbeda dalam satu famili (Contoh: Kucing, Harimau, Singa).<br>3. <strong>Tingkat Ekosistem:</strong> Interaksi biota dengan lingkungannya (Contoh: Ekosistem pantai, hutan hujan).',
                        visual: 'Tingkat Gen (Satu spesies) → Tingkat Jenis (Beda spesies) → Tingkat Ekosistem',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Penulisan Binomial Nomenklatur harus dicetak miring: Kata pertama Kapital (Genus), kata kedua huruf kecil (Spesies). Contoh: *Oryza sativa*.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Keanekaragaman warna kelopak bunga wijayakusuma tergolong keanekaragaman tingkat...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Perbedaan warna pada kelopak bunga wijayakusuma disebabkan oleh kombinasi genetik yang bervariasi dalam satu spesies yang sama, sehingga tergolong keanekaragaman **tingkat GEN**.<br><br><strong>Jawaban Akhir:</strong> Tingkat Gen.'
                    },
                    {
                        title: '2. Virus & Monera (Bakteri) (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Virus:</strong> Agen infeksius aseluler (bukan sel) yang hanya terdiri atas materi genetik (DNA atau RNA) yang dibungkus selubung protein (kapsid). Virus hanya bereproduksi di dalam sel hidup.<br>• <strong>Bakteri (Monera):</strong> Organisme prokariotik uniseluler (tidak memiliki membran inti sel).',
                        visual: 'Daur Litik (Sel inang hancur/lisis) vs Daur Lisogenik (DNA virus menyatu jadi profag)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Perbedaan Bakteri Gram Positif dan Negatif: Gram Positif menyerap warna kristal violet (**UNGU**) karena dinding peptidoglikannya tebal.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Bakteri *Rhizobium leguminosarum* sangat menguntungkan tanaman kacang-kacangan karena mampu...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Bakteri *Rhizobium* hidup bersimbiosis di bintil akar legum untuk **mengikat (fiksasi) nitrogen bebas (N₂)** dari udara menjadi senyawa nitrat yang dapat diserap tanaman sebagai nutrisi.<br><br><strong>Jawaban Akhir:</strong> Mengikat nitrogen bebas dari udara.'
                    },
                    {
                        title: '3. Ekologi, Jaring Makanan & Daur Biogeokimia (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Ekologi mempelajari interaksi organisme dengan lingkungannya. Aliran energi bersifat searah melalui rantai makanan, sedangkan materi mengalami siklus berulang (Siklus Biogeokimia: Nitrogen, Karbon, Air, Fosfor).<br><br><strong>Hukum 10% Energi:</strong> Hanya sekitar 10% energi yang berhasil ditransfer dari satu tingkat trofik ke tingkat trofik di atasnya.',
                        visual: 'Siklus N₂: Fiksasi N₂ → Nitrifikasi (Nitrit & Nitrat) → Asimilasi → Denitrifikasi',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Bakteri *Nitrosomonas* dan *Nitrosococcus* berperan mengubah Amonia menjadi Nitrit (Nitritasi).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Proses pengubahan amonia menjadi nitrit oleh bakteri nitrifikasi dinamakan...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Tahap pengubahan amonia (NH₃) menjadi nitrit (NO₂⁻) disebuat **Nitritasi**, yang merupakan bagian awal dari proses besar Nitrifikasi.<br><br><strong>Jawaban Akhir:</strong> Nitritasi.'
                    },
                    {
                        title: '4. Biologi Sel & Transpor Membran (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Sel adalah unit struktural dan fungsional terkecil kehidupan.<br>• <strong>Transpor Pasif:</strong> Tidak memerlukan energi ATP (Difusi & Osmosis).<br>• <strong>Transpor Aktif:</strong> Memerlukan energi ATP untuk melawan gradien konsentrasi (Pompa Na-K, Endositosis, Eksositosis).<br><br><strong>Osmosis:</strong> Perpindahan pelarut (air) dari larutan hipotonis (encer) ke larutan hipertonis (pekat) melalui membran semipermeabel.',
                        visual: 'Sel Tumbuhan di Hipotonis → TURGID | Sel Hewan di Hipotonis → LISIS (Pecah)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Sel tumbuhan tidak akan pecah saat dimasukkan ke dalam air murni (hipotonis) karena memiliki **Dinding Sel** yang kuat.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Organel sel yang dijuluki "Powerhouse of Cell" karena berfungsi menghasilkan energi ATP melalui respirasi seluler adalah...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Organel yang bertanggung jawab merombak glukosa dan O₂ menjadi ATP melalui siklus Krebs dan transpor elektron adalah **Mitokondria**.<br><br><strong>Jawaban Akhir:</strong> Mitokondria.'
                    },
                    {
                        title: '5. Jaringan Tumbuhan & Hewan (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Jaringan Tumbuhan:</strong> Meristem (aktif membelah), Epidermis (pelindung), Parenkim (dasar/penyimpan), Xilem (transpor air & mineral dari akar ke daun), Floem (transpor hasil fotosintesis dari daun ke seluruh tubuh).<br>• <strong>Jaringan Hewan:</strong> Epitel, Jaringan Ikat, Otot (Polos, Lurik, Jantung), dan Saraf.',
                        visual: 'Xilem (Air & Mineral) | Floem (Hasil Fotosintesis)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Pembuluh Xilem tersusun atas sel-sel mati berdinding lignin tebal, sedangkan Floem tersusun atas sel-sel hidup.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Jaringan tumbuhan yang berfungsi mengangkut air dan garam mineral dari tanah ke daun adalah...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Jaringan pengangkut yang bertugas membawa air dan mineral tanah menuju daun untuk fotosintesis adalah **Xilem**.<br><br><strong>Jawaban Akhir:</strong> Xilem.'
                    },
                    {
                        title: '6. Sistem Organ Manusia I: Saraf & Hormon (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Sistem Koordinasi mengatur aktivitas tubuh melalui impuls listrik (Sistem Saraf) dan zat kimia darah (Sistem Hormon / Endokrin).<br><br><strong>Mekanisme Gerak Refleks:</strong><br>Reseptor → Saraf Sensorik → Sumsum Tulang Belakang (Neuron Konektor) → Saraf Motorik → Efektor (Otot).',
                        visual: 'Impuls Saraf: Dendrit → Badan Sel → Akson → Sinapsis (Neurotransmiter)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Gerak refleks TIDAK melibatkan otak secara langsung, melainkan diproses cepat di Sumsum Tulang Belakang.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Hormon yang dihasilkan oleh kelenjar pankreas untuk menurunkan kadar gula darah dengan menguubah glukosa menjadi glikogen adalah...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Kelenjar pankreas memproduksi hormon **Insulin** yang bertugas menurunkan gula darah. Sebaliknya, hormon **Glukagon** bertugas menaikkan gula darah.<br><br><strong>Jawaban Akhir:</strong> Insulin.'
                    },
                    {
                        title: '7. Sistem Organ Manusia II: Sirkulasi & Ekskresi (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Sistem Ekskresi Ginjal (Tahap Pembentukan Urine):</strong><br>1. <strong>Filtrasi (Glomerulus):</strong> Menyaring darah → Urine Primer.<br>2. <strong>Reabsorpsi (Tubulus Kontortus Proksimal):</strong> Menyerap kembali glukosa & asam amino → Urine Sekunder.<br>3. <strong>Augmentasi (Tubulus Kontortus Distal):</strong> Penambahan zat sisa → Urine Sesungguhnya.',
                        visual: 'Filtrasi (Glomerulus) → Reabsorpsi (TKP) → Augmentasi (TKD) → Tubulus Kolektivus',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Jika urine seseorang mengandung **Glukosa** (penyakit Diabetes Mellitus), kerusakan terjadi pada tahap **Reabsorpsi di Tubulus Kontortus Proksimal (TKP)**.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Di bagian manakah proses penyaringan darah (filtrasi) terjadi di dalam nefron ginjal?<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Proses filtrasi plasma darah terjadi pada kapiler **Glomerulus** menghasilkan urine primer.<br><br><strong>Jawaban Akhir:</strong> Glomerulus.'
                    },
                    {
                        title: '8. Enzim & Metabolisme Sel (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Metabolisme mencakup Anabolisme (penyusunan, contoh: Fotosintesis) dan Katabolisme (pembongkaran, contoh: Respirasi Aerob). Enzim bekerja sebagai biokatalisator organik yang mempercepat reaksi dengan menurunkan Energi Aktivasi.<br><br><strong>Tahapan Respirasi Aerob (1 Glukosa):</strong><br>1. Glikolisis (Sitoplasma) → 2 ATP, 2 NADH, 2 Asam Piruvat.<br>2. Dekarboksilasi Oksidatif (Matriks Mitokondria) → 2 Acetyl-CoA, 2 CO₂.<br>3. Siklus Krebs (Matriks Mitokondria) → 2 ATP, 6 NADH, 2 FADH₂.<br>4. Transpor Elektron (Krista Mitokondria) → **34 ATP**.',
                        visual: 'Glikolisis (2 ATP) → Dekarboksilasi → Siklus Krebs (2 ATP) → Transpor Elektron (34 ATP)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Tahap yang menghasilkan ATP TERBANYAK dalam respirasi aerob adalah tahap **Transpor Elektron** (sekitar 34 ATP).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Di bagian sel manakah tahap Glikolisis berlangsung?<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Glikolisis merupakan pemecahan glukosa menjadi asam piruvat yang terjadi di luar mitokondria, yaitu di **Sitoplasma (Sitosol)**.<br><br><strong>Jawaban Akhir:</strong> Sitoplasma.'
                    },
                    {
                        title: '9. Genetika & Sintesis Protein (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> DNA mengandung kode genetik yang diwariskan. Sintesis protein terjadi melalui 2 tahap utama:<br>1. <strong>Transkripsi (di Nukleus):</strong> DNA murni mencetak mRNA (dRNA).<br>2. <strong>Translasi (di Ribosom):</strong> tRNA membawa asam amino sesuai kodon mRNA untuk merangkai rantai polipeptida (protein).<br><br><strong>Pasangan Basa Nitrogen:</strong> Adenin (A) berpasangan dengan Timin (T) [pada RNA diganti Urasil (U)], Guanin (G) berpasangan dengan Sitosin (C).',
                        visual: 'DNA -> Transkripsi (Nukleus) -> mRNA -> Translasi (Ribosom) -> Protein',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Pada persilangan Dihibrid heterozigot sempurna (AaBb × AaBb), rasio fenotipe keturunannya selalu **9 : 3 : 3 : 1**.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Jika urutan basa nitrogen rantai antisense DNA adalah 5\'-TAC GGC-3\', tentukan urutan mRNA hasil transkripsinya!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Transkripsi mRNA dicetak komplementer terhadap rantai DNA antisense.<br><strong>Langkah 2:</strong> Pasangan basa: T→A, A→U (pada RNA), C→G, G→C.<br>&nbsp;&nbsp;&nbsp;• T → A<br>&nbsp;&nbsp;&nbsp;• A → U<br>&nbsp;&nbsp;&nbsp;• C → G<br>&nbsp;&nbsp;&nbsp;• G → C<br>&nbsp;&nbsp;&nbsp;• G → C<br>&nbsp;&nbsp;&nbsp;• C → G<br>&nbsp;&nbsp;&nbsp;Maka rantai mRNA adalah 3\'-AUG CCG-5\'.<br><br><strong>Jawaban Akhir:</strong> AUG CCG.'
                    },
                    {
                        title: '10. Bioteknologi & Evolusi (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Bioteknologi memanfaat organisme hidup untuk menghasilkan produk bermanfaat (Bioteknologi Konvensional menggunakan fermentasi; Bioteknologi Modern menggunakan rekayasa genetik & DNA rekombinan).<br><br><strong>Hukum Hardy-Weinberg (Frekuensi Gen Populasi):</strong><br>p + q = 1, dan p² + 2pq + q² = 1 (p = allele dominan, q = allele resesif, 2pq = individu carrier/heterozigot).',
                        visual: 'Hardy-Weinberg: p + q = 1 | p² + 2pq + q² = 1',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Dalam perhitungan populasi, mulailah dengan mencari nilai **q²** (persentase fenotipe resesif / penderita) terlebih dahulu, lalu tarik akar untuk mendapatkan nilai q.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Dalam populasi 10.000 orang terdapat 16 orang menderita albino (resesif q²). Hitunglah jumlah orang yang tergolong pembawa/carrier (2pq)!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> q² = 16 / 10.000 = 0,0016.<br><strong>Langkah 2:</strong> q = √0,0016 = 0,04.<br><strong>Langkah 3:</strong> p = 1 - q = 1 - 0,04 = 0,96.<br><strong>Langkah 4:</strong> Frekuensi carrier (2pq) = 2 × (0,96) × (0,04) = 0,0768.<br><strong>Langkah 5:</strong> Jumlah orang carrier = 0,0768 × 10.000 = 768 orang.<br><br><strong>Jawaban Akhir:</strong> 768 orang.'
                    }
                ],
                'eko': [
                    {
                        title: '1. Masalah Ekonomi, Kelangkaan & Biaya Peluang (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Masalah inti ekonomi timbul karena kebutuhan manusia bersifat tidak terbatas, sedangkan sumber daya/alat pemuas kebutuhan terbatas (Kelangkaan).<br><br><strong>Biaya Peluang (Opportunity Cost):</strong> Nilai barang atau kesempatan terbaik yang **dikorbankan/dilepaskan** karena memilih alternatif keputusan lain.',
                        visual: 'Biaya Peluang = Nilai Kesempatan Terbaik yang Ditinggalkan (Bukan dijumlahkan)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Biaya peluang TIDAK dijumlahkan! Pilihlah satu nilai tertinggi di antara pilihan-pilihan yang dibatalkan.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Anisa memiliki pilihan setelah lulus SMA: Kuliah (biaya Rp 5 jt/bln), Bekerja sebagai Staf Administrasi (gaji Rp 3,5 jt/bln), atau Menjadi Wirausaha (potensi Rp 4,5 jt/bln). Jika Anisa memilih kuliah, berapakah biaya peluangnya?<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Anisa melepaskan dua kesempatan kerja. Nilai kesempatan terbesar yang ditinggalkan adalah menjadi Wirausaha sebesar **Rp 4.500.000/bulan**.<br><br><strong>Jawaban Akhir:</strong> Rp 4.500.000 / bulan.'
                    },
                    {
                        title: '2. Keseimbangan Pasar & Elastisitas (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Harga Keseimbangan (Ekuilibrium):</strong> Terjadi saat jumlah permintaan sama dengan jumlah penawaran (**Qd = Qs** atau **Pd = Ps**).<br>• <strong>Elastisitas Harga Permintaan (Ed):</strong> Mengukur derajat kepekaan perubahan jumlah barang yang diminta akibat perubahan harga (Ed = %ΔQ / %ΔP).',
                        visual: 'Ekuilibrium: Qd = Qs | Ed > 1 (Elastis) | Ed < 1 (Inelastis) | Ed = 1 (Unitari)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Barang kebutuhan pokok (seperti beras atau garam) memiliki permintaan yang bersifat **Inelastis (Ed < 1)** karena konsumen tetap membelinya meskipun harga naik.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Diketahui fungsi permintaan Qd = 100 - 2P dan fungsi penawaran Qs = -20 + 4P. Tentukan harga keseimbangan pasar (P)!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Terapkan syarat keseimbangan Qd = Qs.<br>&nbsp;&nbsp;&nbsp;100 - 2P = -20 + 4P<br><strong>Langkah 2:</strong> Pindahkan variabel P ke ruas kanan:<br>&nbsp;&nbsp;&nbsp;100 + 20 = 4P + 2P<br>&nbsp;&nbsp;&nbsp;120 = 6P  ⇒  P = 120 / 6 = 20.<br><br><strong>Jawaban Akhir:</strong> P = 20.'
                    },
                    {
                        title: '3. Pendapatan Nasional & PDB (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Produk Domestik Bruto (PDB/GDP) menghitung total nilai barang dan jasa akhir yang dihasilkan di dalam batas wilayah suatu negara selama satu periode.<br><br><strong>Pendekatan Pengeluaran PDB:</strong><br>Y = C + I + G + (X - M)<br>(C=Konsumsi Rumah Tangga, I=Investasi, G=Pengeluaran Pemerintah, X=Ekspor, M=Impor).',
                        visual: 'PDB Pengeluaran: Y = C + I + G + (X - M) | GNP = GDP + Pendapatan Neto Luar Negeri',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Ekspor Neto adalah (X - M). Jika Ekspor > Impor, negara mengalami surplus perdagangan.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Jika C = 300, I = 150, G = 200, X = 100, dan M = 80 (dalam triliun rupiah), hitunglah PDB negara tersebut!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Y = C + I + G + (X - M)<br>Y = 300 + 150 + 200 + (100 - 80)<br>Y = 650 + 20 = 670 triliun rupiah.<br><br><strong>Jawaban Akhir:</strong> Rp 670 Triliun.'
                    },
                    {
                        title: '4. APBN, APBD & Kebijakan Fiskal (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Kebijakan Fiskal diatur oleh Pemerintah melalui penetapan pajak dan belanja negara (APBN) untuk menstabilkan perekonomian.<br>• <strong>Kebijakan Fiskal Ekspansif (Saat Resesi):</strong> Menurunkan Pajak (T) & Meningkatkan Belanja Negara (G).<br>• <strong>Kebijakan Fiskal Kontraktif (Saat Inflasi Tinggi):</strong> Menaikkan Pajak (T) & Menekan Belanja Negara (G).',
                        visual: 'Atasi Inflasi → Naikkan Pajak & Potong Belanja | Atasi Resesi → Turunkan Pajak & Naikkan Belanja',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Ingat bahwa Kebijakan Fiskal berhubungan dengan **PAJAK & BELANJA NEGARA**, sedangkan Kebijakan Moneter berhubungan dengan **SUKU BUNGA & UANG BEREDAR**.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Instrumen kebijakan fiskal yang paling tepat diterapkan pemerintah saat terjadi lonjakan inflasi adalah...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Untuk mengatasi inflasi, pemerintah menerapkan Kebijakan Fiskal Kontraktif dengan **menaikkan tarif pajak** dan **mengurangi belanja pemerintah** guna menurunkan daya beli masyarakat.<br><br><strong>Jawaban Akhir:</strong> Menaikkan pajak dan mengurangi belanja negara.'
                    },
                    {
                        title: '5. Kebijakan Moneter & Perbankan (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Kebijakan Moneter dijalankan oleh Bank Sentral (Bank Indonesia) untuk mengendalikan jumlah uang yang beredar (JUB).<br><br><strong>4 Instrumen Utama Moneter:</strong><br>1. <strong>Operasi Pasar Terbuka:</strong> Jual/Beli Sertifikat BI (SBI).<br>2. <strong>Politik Diskonto:</strong> Naik/Turun suku bunga bank umum.<br>3. <strong>Giro Wajib Minimum (GWM):</strong> Cadangan kas minimum bank.<br>4. <strong>Kredit Selektif:</strong> Pengetatan syarat pinjaman.',
                        visual: 'Atasi Inflasi (Tight Money Policy): Naikkan Suku Bunga & Jual SBI',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Jika Bank Indonesia MENAIKKAN suku bunga diskonto, masyarakat berbondong-bondong menabung sehingga Jumlah Uang Beredar (JUB) berkurang.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Dampak dari kebijakan Bank Indonesia menaikkan tingkat suku bunga diskonto adalah...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Kenaikan suku bunga akan menarik masyarakat untuk menyimpan uang di bank dan mengurangi pinjaman, sehingga **jumlah uang yang beredar berkurang dan inflasi dapat ditekan**.<br><br><strong>Jawaban Akhir:</strong> Jumlah uang beredar berkurang.'
                    },
                    {
                        title: '6. Akuntansi: Persamaan Dasar & Jurnal Umum (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Akuntansi adalah sistem informasi pengukur transaksi keuangan.<br><br><strong>Persamaan Dasar Akuntansi:</strong><br>Aset (Harta) = Liabilitas (Utang) + Ekuitas (Modal)<br><br><strong>Aturan Debet-Kredit (Aturan Saldo Normal):</strong><br>• **Aset & Beban:** Bertambah di **DEBET**, berkurang di KREDIT.<br>• **Utang, Modal, & Pendapatan:** Bertambah di **KREDIT**, berkurang di DEBET.',
                        visual: 'Aset & Beban (Naik = Debet) | Utang, Modal, Pendapatan (Naik = Kredit)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Kata kunci "dibeli peralatan secara kredit" berarti Aset Peralatan bertambah di DEBET, dan Utang Usaha bertambah di KREDIT.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Perusahaan membeli komputer senilai Rp 8.000.000 secara kredit. Tuliskan analisis jurnal umumnya!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Peralatan (Komputer) bertambah → Debet Rp 8.000.000.<br><strong>Langkah 2:</strong> Membeli secara kredit menyebabkan Utang Usaha bertambah → Kredit Rp 8.000.000.<br><br><strong>Jawaban Akhir:</strong> Peralatan (D) Rp 8.000.000; Utang Usaha (K) Rp 8.000.000.'
                    },
                    {
                        title: '7. Akuntansi: Jurnal Penyesuaian & Laporan Keuangan (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Ayat Jurnal Penyesuaian (AJP) dibuat pada akhir periode akuntansi untuk memperbarui saldo akun agar mencerminkan kondisi sebenarnya.<br><br><strong>Penyesuaian Perlengkapan:</strong><br>AJP Perlengkapan dicatat berdasarkan **NILAI YANG SUDAH TERPAKAI**.<br>Beban Perlengkapan (D) / Perlengkapan (K).',
                        visual: 'AJP Perlengkapan = Sebesar yang TERPAKAI | AJP Sewa Dibayar di Muka = Sebesar yang KADALUARSA',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Jangan terkecoh! Untuk Perlengkapan, AJP mencatat besarnya nilai yang *terpakai* (Perlengkapan Awal - Sisa Akhir).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Awal tahun saldo perlengkapan Rp 5.000.000. Pada akhir tahun tersisa perlengkapan Rp 1.500.000. Buatlah jurnal penyesuaiannya!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br><strong>Langkah 1:</strong> Hitung nilai perlengkapan yang terpakai = 5.000.000 - 1.500.000 = Rp 3.500.000.<br><strong>Langkah 2:</strong> Catat AJP:<br>&nbsp;&nbsp;&nbsp;Beban Perlengkapan (D) Rp 3.500.000<br>&nbsp;&nbsp;&nbsp;Perlengkapan (K) Rp 3.500.000.<br><br><strong>Jawaban Akhir:</strong> Beban Perlengkapan (D) Rp 3.500.000; Perlengkapan (K) Rp 3.500.000.'
                    }
                ],
                'sos': [
                    {
                        title: '1. Sosiologi Sebagai Ilmu & Interaksi Sosial (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Sosiologi adalah ilmu kategoris yang mempelajari struktur dan proses sosial masyarakat.<br><br><strong>Ciri Ciri Sosiologi:</strong><br>1. <strong>Empiris:</strong> Berdasarkan fakta dan observasi di lapangan.<br>2. <strong>Teoritis:</strong> Menyusun abstraksi dari hasil observasi.<br>3. <strong>Kumulatif:</strong> Memperbaiki dan memperluas teori lama.<br>4. <strong>Non-Etis:</strong> Tidak menilai baik atau buruknya suatu fakta sosial, melainkan menjelaskan alasannya.',
                        visual: 'Ciri Sosiologi: Empiris, Teoritis, Kumulatif, Non-Etis',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Ciri **Non-Etis** berarti sosiologi tidak bertindak sebagai hakim moral, melainkan menganalisis fakta secara obyektif.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Sosiolog meneliti fenomena kemacetan lalu lintas tanpa menyalahkan pengguna jalan. Ciri sosiologi yang ditunjukkan adalah...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Sikap peneliti yang tidak memberikan penilaian moral baik/buruk terhadap subjek penelitian mencerminkan ciri **Non-Etis**.<br><br><strong>Jawaban Akhir:</strong> Non-Etis.'
                    },
                    {
                        title: '2. Nilai & Norma Sosial (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Nilai sosial adalah anggapan tentang apa yang baik dan buruk dalam masyarakat. Norma adalah aturan bersanksi yang menjaga nilai tersebut.<br><br><strong>4 Tingkatan Norma Berdasarkan Sanksinya:</strong><br>1. <strong>Cara (Usage):</strong> Sanksi sangat ringan (teguran).<br>2. <strong>Kebiasaan (Folkways):</strong> Perilaku berulang (ejekan).<br>3. <strong>Tata Kelakuan (Mores):</strong> Pengatur moralitas (pengucilan).<br>4. <strong>Adat Istiadat (Custom):</strong> Aturan adat kuat (sanksi adat berat).',
                        visual: 'Sanksi Ringan → Cara → Kebiasaan → Tata Kelakuan → Adat Istiadat → Sanksi Berat',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Contoh pelanggaran *Usage* adalah bersendawa saat makan; contoh pelanggaran *Custom* adalah melanggar aturan pernikahan sesuku adat.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Seseorang yang berpakaian tidak rapi saat menghadiri acara resmi akan ditegur. Hal ini tergolong pelanggaran norma...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Teguran ringan atas ketidakselarasan perilaku tergolong pelanggaran norma **Cara (Usage)**.<br><br><strong>Jawaban Akhir:</strong> Cara (Usage).'
                    },
                    {
                        title: '3. Stratifikasi & Diferensiasi Sosial (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Stratifikasi Sosial:</strong> Pengelompokan masyarakat secara vertikal (bertingkat/hierarki) berdasarkan kekayaan, kekuasaan, pendidikan, atau keturunan.<br>• <strong>Diferensiasi Sosial:</strong> Pengelompokan masyarakat secara horizontal (sejajar/sederajat) berdasarkan ras, suku, agama, gender, dan profesi.',
                        visual: 'Stratifikasi (Vertikal / Hirarki) vs Diferensiasi (Horizontal / Kesetaraan)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Keberagaman Suku Bangsa dan Agama bersifat **Diferensiasi Sosial** karena tidak ada agama atau suku yang derajatnya secara sosiologis lebih tinggi dari yang lain.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Keberagaman profesi masyarakat kota seperti dokter, guru, dan pengusaha tergolong ke dalam struktur...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Pengelompokan profesi secara sosiologis memandangnya sebagai keragaman fungsional yang sejajar, sehingga tergolong **Diferensiasi Sosial**.<br><br><strong>Jawaban Akhir:</strong> Diferensiasi Sosial.'
                    },
                    {
                        title: '4. Konflik Sosial & Resolusi Konflik (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Konflik sosial timbul karena perbedaan kepentingan, kebudayaan, atau perubahan sosial yang cepat.<br><br><strong>Bentuk-Bentuk Akomodasi Resolusi Konflik:</strong><br>1. <strong>Mediasi:</strong> Pihak ketiga netral bertindak sebagai penasihat (keputusan tidak mengikat).<br>2. <strong>Arbitrase:</strong> Pihak ketiga berwenang mengambil keputusan yang **mengikat** kedua pihak.<br>3. <strong>Konsiliasi:</strong> Mempertemukan keinginan pihak berkonflik.<br>4. <strong>Ajudikasi:</strong> Penyelesaian melalui **jalur pengadilan**.',
                        visual: 'Mediasi (Penasihat) | Arbitrase (Keputusan Mengikat) | Ajudikasi (Pengadilan)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Kata kunci Ajudikasi adalah kata "Pengadilan" atau "Hukum Positif".',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Sengketa lahan sengketa antar warga diselesaikan di Pengadilan Negeri. Bentuk akomodasi konflik tersebut adalah...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Penyelesaian konflik lembaga peradilan resmi merupakan bentuk **Ajudikasi**.<br><br><strong>Jawaban Akhir:</strong> Ajudikasi.'
                    },
                    {
                        title: '5. Perubahan Sosial & Modernisasi (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Perubahan sosial adalah pergeseran struktur dan pola perilaku masyarakat dari waktu ke waktu.<br><br><strong>Teori-Teori Utama:</strong><br>1. <strong>Teori Siklus:</strong> Perubahan berulang seperti roda berputar (peradaban lahir, berkembang, runtuh, lalu terulang).<br>2. <strong>Teori Linier (Evolusi):</strong> Perubahan bergerak maju ke arah modernisasi yang lebih kompleks.',
                        visual: 'Teori Siklus (Roda Berputar) vs Teori Linier (Garis Lurus Berkelanjutan)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Tren fashion baju vintage yang kembali populer masa kini adalah contoh dari **Teori Siklus**.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Fenomena perkembangan teknologi digital dari era HP analog ke Smartphone modern sesuai dengan konsep...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Perkembangan teknologi yang berjalan maju berkesinambungan menuju bentuk yang lebih sempurna tergolong **Teori Linier / Evolusi**.<br><br><strong>Jawaban Akhir:</strong> Teori Linier.'
                    }
                ],
                'geo': [
                    {
                        title: '1. Pengetahuan Dasar Geografi & 10 Konsep Geografi (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Geografi mengkaji persamaan dan perbedaan fenomena geosfer dengan sudut pandang keruangan.<br><br><strong>4 Prinsip Dasar Geografi:</strong><br>1. <strong>Distribusi (Persebaran):</strong> Fenomena tidak merata.<br>2. <strong>Interelasi (Keterkaitan):</strong> Hubungan sebab-akibat antar fenomena.<br>3. <strong>Deskripsi (Penggambaran):</strong> Penjelasan melalui Peta/Tabel.<br>4. <strong>Korologi:</strong> Gabungan komprehensif ketiga prinsip.',
                        visual: 'Prinsip Korologi = Distribusi + Interelasi + Deskripsi secara Komprehensif',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Konsep Diferensiasi Area membandingkan keunikan dua wilayah berbeda (contoh: Pegunungan penghasil sayur vs Pantai penghasil ikan).',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Banjir di Jakarta disebabkan oleh kerusakan hutan di Bogor. Prinsip geografi yang sesuai adalah...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Fenomena ini menunjukkan hubungan keterkaitan sebab-akibat antara kondisi alih fungsi lahan Bogor dengan banjir Jakarta, sehingga sesuai dengan **Prinsip Interelasi**.<br><br><strong>Jawaban Akhir:</strong> Prinsip Interelasi.'
                    },
                    {
                        title: '2. Dinamika Litosfer & Tenaga Pembentuk Bumi (Kelas 10 / Fase E)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Litosfer adalah lapisan batuan pembentuk kulit bumi.<br>• <strong>Tenaga Endogen (Dari Dalam Bumi):</strong> Tektonisme, Vulkanisme, dan Seisme (Gempa).<br>• <strong>Tenaga Eksogen (Dari Luar Bumi):</strong> Pelapukan, Erosi, Sedimentasi, dan Mass Wasting.<br><br><strong>Siklus Batuan:</strong> Magma → Batuan Beku → Batuan Sedimen → Batuan Metamorf (Malihan).',
                        visual: 'Batuan Beku → Batuan Sedimen → Batuan Metamorf (Mengalami Suhu & Tekanan Tinggi)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Batu Marmer berasal dari perubahan (metamorfosis) Batu Kapur/Gamping akibat pengaruh suhu dan tekanan tinggi.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Batu kapur yang mengalami kontak dengan suhu dan tekanan tinggi di dalam bumi akan berubah menjadi batu...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Batu kapur (sedimen) yang mengalami perubahan akibat suhu dan tekanan tinggi bertransformasi menjadi **Batu Marmer (Metamorf)**.<br><br><strong>Jawaban Akhir:</strong> Batu Marmer.'
                    },
                    {
                        title: '3. Dinamika Atmosfer & Iklim (Kelas 11 / Fase F)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong> Atmosfer adalah selubung udara bumi.<br><br><strong>5 Lapisan Atmosfer:</strong><br>1. <strong>Troposfer:</strong> Tempat terjadinya cuaca (Awan, Hujan, Angin).<br>2. <strong>Stratosfer:</strong> Tempat lapisan Ozon (O₃) yang menyerap sinar UV.<br>3. <strong>Mesosfer:</strong> Lapisan pembakar meteoroid.<br>4. <strong>Termosfer/Ionosfer:</strong> Pemantul gelombang radio.<br>5. <strong>Eksosfer:</strong> Angkasa luar.',
                        visual: 'Troposfer (Cuaca) → Stratosfer (Ozon) → Mesosfer (Meteor) → Termosfer (Radio)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Fenomena cuaca harian manusia HANYA berlangsung di lapisan paling bawah, yaitu **Troposfer**.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Di lapisan atmosfer manakah tempat terjadinya hujan dan pembentukan awan?<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Seluruh dinamika iklim dan cuaca terjadi pada lapisan terdekat dengan permukaan bumi, yaitu **Troposfer**.<br><br><strong>Jawaban Akhir:</strong> Troposfer.'
                    },
                    {
                        title: '4. Penginderaan Jauh & Sistem Informasi Geografis (Kelas 12 / Fase F Lanjut)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Penginderaan Jauh (PJ):</strong> Seni memperoleh data spasial tanpa kontak langsung dengan objek menggunakan sensor satelit/pesawat.<br>• <strong>SIG (Sistem Informasi Geografis):</strong> Sistem komputerisasi penyimpan, pengolah, dan penganalisis data geografis.',
                        visual: 'Overlay SIG: Peta Kemiringan Lahan + Peta Curah Hujan → Peta Rawan Longsor',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Teknik *Overlay* (tumpang susun peta) merupakan keunggulan utama analisis SIG untuk penentuan lokasi pembangunan.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Objek lapangan sepak bola pada foto udara mudah dikenali dari bentuknya yang persegi panjang dan tekstur yang halus. Unsur interpretasi yang digunakan adalah...<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Pengenalan lapangan sepak bola didasarkan pada ciri spasial **Bentuk** (persegi panjang) dan **Tekstur** (permukaan rumput halus).<br><br><strong>Jawaban Akhir:</strong> Bentuk dan Tekstur.'
                    }
                ],
                'lit': [
                    {
                        title: '1. Bahasa Indonesia: Ide Pokok & Simpulan Teks (SNBT)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Ide Pokok (Gagasan Utama):</strong> Inti pembicaraan dari seluruh isi paragraf.<br>• <strong>Paragraf Deduktif:</strong> Ide pokok terletak di **Awal Paragraf**.<br>• <strong>Paragraf Induktif:</strong> Ide pokok terletak di **Akhir Paragraf** (ditandai kata hubung: *oleh karena itu, dengan demikian, maka dari itu*).',
                        visual: 'Deduktif (Awal Paragraf) | Induktif (Akhir Paragraf)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Bacalah kalimat pertama dan kalimat terakhir paragraf terlebih dahulu untuk menentukan jenis paragraf secara instan!',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>Bacalah paragraf berikut: "Pendidikan karakter sangat krusial bagi remaja. Karakter yang kuat membentuk kepribadian yang jujur dan berintegritas. Oleh karena itu, sekolah wajib mengintegrasikan nilai moral dalam pembelajaran." Tentukan kalimat utamanya!<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>Kalimat utama berada di awal paragraf (Deduktif): "Pendidikan karakter sangat krusial bagi remaja."<br><br><strong>Jawaban Akhir:</strong> Pendidikan karakter sangat krusial bagi remaja.'
                    },
                    {
                        title: '2. English Comprehension: Main Idea & Author\'s Attitude (SNBT)',
                        kurikulum: 'K13 & Merdeka',
                        summary: '<strong>Pengertian & Konsep Dasar:</strong><br>• <strong>Main Idea:</strong> The primary point or argument that the author wants to convey.<br>• <strong>Author\'s Tone/Attitude:</strong> The emotional stance or feeling expressed by the author toward the topic (e.g., *Critical, Objective, Optimistic, Pessimistic, Neutral*).',
                        visual: 'Tone Types: Objective (Factual) | Critical (Disapproving) | Optimistic (Positive)',
                        tips: '<strong>Langkah Cepat Cerdas:</strong> Pay attention to adjectives and adverbs used in the text. Positive adjectives indicate an optimistic tone; critical adjectives indicate disapproval.',
                        contohSoal: '<strong>Contoh Soal HOTS UTBK:</strong><br>What is the author\'s attitude in a passage stating: "Renewable energy technologies are revolutionary and offer an unparalleled solution for saving Earth"?<br><br><strong>Langkah Penyelesaian Terperinci:</strong><br>The words "revolutionary" and "unparalleled solution" express strong positive enthusiasm and support toward the topic. Therefore, the tone is **Optimistic / Supportive**.<br><br><strong>Jawaban Akhir:</strong> Optimistic / Supportive.'
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
                            pertanyaan: 'Diketahui persamaan kuadrat x² - (k + 2)x + 16 = 0 memiliki dua akar real positif yang sama (kembar). Nilai k yang memenuhi adalah...',
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
                            <span>Nihiluxxy Super Learning Edition • Penjelasan Lebih Dalam & Jelas</span>
                        </div>
                        <h1 class="text-3xl sm:text-5xl font-black text-white tracking-tight mb-4 leading-tight">
                            Kuasai Seluruh Konsep SMA & Taklukkan <span class="bg-clip-text text-transparent gradient-accent">UTBK SNBT 2026</span>.
                        </h1>
                        <p class="text-slate-300 text-xs sm:text-sm mb-8 leading-relaxed">
                            Akses modul pembelajaran SMA (Kelas 10–12) dengan penjelasan intuitif yang mudah dimengerti, rumus visual, tips instan, serta pembahasan soal HOTS langkah demi langkah.
                        </p>
                        <div class="flex flex-wrap gap-4">
                            <button onclick="switchView('materi')" class="gradient-accent text-white font-extrabold px-6 py-3.5 rounded-2xl shadow-lg shadow-purple-500/25 hover:opacity-95 transition flex items-center gap-2 text-xs sm:text-sm">
                                <i data-lucide="book-open" class="w-4 h-4"></i> Pelajari Modul Terperinci
                            </button>
                            <button onclick="switchView('utbk')" class="bg-slate-800/90 border border-slate-700 text-white font-extrabold px-6 py-3.5 rounded-2xl hover:bg-slate-800 transition flex items-center gap-2 text-xs sm:text-sm">
                                <i data-lucide="target" class="w-4 h-4 text-amber-400"></i> Uji Simulasi UTBK/TKA
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Stats Counters -->
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-12">
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 text-center">
                        <span class="text-2xl font-black text-purple-400 font-mono">8+</span>
                        <span class="text-xs text-slate-400 block mt-1 font-semibold">Mata Pelajaran SMA</span>
                    </div>
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 text-center">
                        <span class="text-2xl font-black text-emerald-400 font-mono">100%</span>
                        <span class="text-xs text-slate-400 block mt-1 font-semibold">Standar K13 & Merdeka</span>
                    </div>
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 text-center">
                        <span class="text-2xl font-black text-amber-400 font-mono">HOTS</span>
                        <span class="text-xs text-slate-400 block mt-1 font-semibold">Langkah Penyelesaian Akurat</span>
                    </div>
                    <div class="glass-card p-5 rounded-2xl border border-slate-800 text-center">
                        <span class="text-2xl font-black text-cyan-400 font-mono">2026</span>
                        <span class="text-xs text-slate-400 block mt-1 font-semibold">Silabus Terbaru Terintegrasi</span>
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
                    <p class="text-slate-400 text-xs sm:text-sm mt-1">Penjelasan mendalam, analogi intuitif, rumus visual, tips cepat, dan pembahasan HOTS langkah demi langkah.</p>
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
                                    <span class="text-[10px] text-slate-500 font-medium">Sub-materi HOTS Lengkap</span>
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
                                    <span class="text-xs text-slate-500 font-mono">Modul Terperinci #${idx + 1}</span>
                                </div>
                                <h3 class="text-lg font-extrabold text-white mb-3 leading-snug">${mat.title}</h3>
                                <div class="text-slate-300 text-xs sm:text-sm mb-4 leading-relaxed">${mat.summary}</div>
                                
                                <div class="bg-slate-950 p-4 rounded-xl font-mono text-xs text-purple-300 mb-4 border border-slate-800/80 text-center overflow-x-auto">
                                    ${mat.visual}
                                </div>

                                <div class="bg-amber-500/10 border-l-4 border-amber-500 p-4 rounded-r-xl text-xs text-amber-200 mb-4 leading-relaxed">
                                    ${mat.tips}
                                </div>

                                <div class="bg-slate-950/80 border border-slate-800 p-4 rounded-xl text-xs text-slate-300 leading-relaxed">
                                    <span class="text-emerald-400 font-extrabold block mb-2 text-xs">📝 Contoh Soal & Pembahasan HOTS UTBK:</span>
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
