<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nihiluxxy - Platform Belajar SMA, TKA & UTBK SNBT</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Plus Jakarta Sans -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        body { font-family: 'Plus Jakarta Sans', sans-serif; }
        .gradient-brand { background: linear-gradient(135deg, #0F172A 0%, #312E81 50%, #4C1D95 100%); }
        .gradient-accent { background: linear-gradient(135deg, #6366F1 0%, #A855F7 100%); }
        .glass-header { background: rgba(15, 23, 42, 0.85); backdrop-filter: blur(12px); }
    </style>
</head>
<body class="bg-slate-900 text-slate-100 min-h-screen flex flex-col selection:bg-purple-500 selection:text-white">

    <!-- Header Navigation -->
    <header class="sticky top-0 z-50 glass-header border-b border-slate-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between">
            <div class="flex items-center gap-3 cursor-pointer" onclick="switchView('home')">
                <div class="w-10 h-10 rounded-xl gradient-accent flex items-center justify-center text-white font-extrabold text-xl shadow-lg shadow-purple-500/20">
                    <i data-lucide="sparkles" class="w-6 h-6"></i>
                </div>
                <div class="flex flex-col">
                    <span class="text-2xl font-black tracking-tight text-white">Nihiluxxy<span class="text-purple-400">.</span></span>
                    <span class="text-[9px] uppercase tracking-widest text-purple-300 font-bold -mt-1">Future Learning Platform</span>
                </div>
            </div>

            <nav class="hidden md:flex items-center gap-1 bg-slate-800/60 p-1.5 rounded-2xl border border-slate-700/50 text-sm font-semibold">
                <button onclick="switchView('home')" id="nav-home" class="px-4 py-2 rounded-xl text-white bg-purple-600 transition">Beranda</button>
                <button onclick="switchView('materi')" id="nav-materi" class="px-4 py-2 rounded-xl text-slate-300 hover:text-white transition">Materi SMA</button>
                <button onclick="switchView('utbk')" id="nav-utbk" class="px-4 py-2 rounded-xl text-slate-300 hover:text-white transition flex items-center gap-1.5">
                    <span>Simulasi UTBK/TKA</span>
                    <span class="bg-gradient-to-r from-amber-500 to-rose-500 text-white text-[10px] px-2 py-0.5 rounded-full font-bold">SNBT 2026</span>
                </button>
                <button onclick="switchView('riwayat')" id="nav-riwayat" class="px-4 py-2 rounded-xl text-slate-300 hover:text-white transition flex items-center gap-1.5">
                    <i data-lucide="history" class="w-4 h-4 text-purple-400"></i>
                    <span>Riwayat Hasil</span>
                </button>
            </nav>

            <div class="flex items-center gap-3">
                <div class="hidden sm:flex flex-col text-right">
                    <span class="text-xs text-slate-400 font-medium">Siswa Active</span>
                    <span class="text-sm font-bold text-purple-300">SMA Kelas 10 - 12</span>
                </div>
                <div class="w-10 h-10 rounded-xl gradient-accent flex items-center justify-center font-bold text-white shadow-inner">
                    NX
                </div>
            </div>
        </div>
    </header>

    <!-- App Main Content Area -->
    <main id="app-content" class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <!-- Konten diisi secara dinamis melalui JavaScript -->
    </main>

    <!-- Bottom Navigation Bar (Tampilan Mobile) -->
    <div class="md:hidden fixed bottom-0 left-0 right-0 glass-header border-t border-slate-800 flex justify-around py-3 text-xs font-semibold text-slate-400 z-50">
        <button onclick="switchView('home')" class="flex flex-col items-center gap-1 text-purple-400">
            <i data-lucide="home" class="w-5 h-5"></i> Beranda
        </button>
        <button onclick="switchView('materi')" class="flex flex-col items-center gap-1">
            <i data-lucide="book-open" class="w-5 h-5"></i> Materi
        </button>
        <button onclick="switchView('utbk')" class="flex flex-col items-center gap-1">
            <i data-lucide="award" class="w-5 h-5"></i> UTBK/TKA
        </button>
        <button onclick="switchView('riwayat')" class="flex flex-col items-center gap-1">
            <i data-lucide="history" class="w-5 h-5"></i> Riwayat
        </button>
    </div>

    <!-- Application Engine Logic -->
    <script>
        // State Management Application
        const state = {
            activeView: 'home',
            selectedKurikulum: 'Merdeka', // 'Merdeka' | 'K13'
            attempts: JSON.parse(localStorage.getItem('nihiluxxy_attempts') || '[]')
        };

        // Static Database (Kurikulum, Materi, Bank Soal & Pembahasan Akurat)
        const db = {
            mapel: [
                { id: 'mat', nama: 'Matematika Wajib & Lanjut', icon: 'calculator', color: 'from-blue-600 to-cyan-500', k13: 'Kelas 10-12 IPA/IPS', merdeka: 'Fase E & F' },
                { id: 'fis', nama: 'Fisika', icon: 'zap', color: 'from-indigo-600 to-blue-500', k13: 'Kelas 10-12 IPA', merdeka: 'Fase F (Peminatan)' },
                { id: 'kim', nama: 'Kimia', icon: 'flask-conical', color: 'from-purple-600 to-pink-500', k13: 'Kelas 10-12 IPA', merdeka: 'Fase F (Peminatan)' },
                { id: 'bio', nama: 'Biologi', icon: 'dna', color: 'from-emerald-600 to-teal-500', k13: 'Kelas 10-12 IPA', merdeka: 'Fase F (Peminatan)' },
                { id: 'eko', nama: 'Ekonomi & Akuntansi', icon: 'trending-up', color: 'from-amber-600 to-yellow-500', k13: 'Kelas 10-12 IPS', merdeka: 'Fase F (Peminatan)' },
                { id: 'sos', nama: 'Sosiologi', icon: 'users', color: 'from-rose-600 to-red-500', k13: 'Kelas 10-12 IPS', merdeka: 'Fase F (Peminatan)' },
                { id: 'geo', nama: 'Geografi', icon: 'globe', color: 'from-teal-600 to-emerald-500', k13: 'Kelas 10-12 IPS', merdeka: 'Fase F (Peminatan)' },
                { id: 'sej', nama: 'Sejarah Indonesia & Lanjut', icon: 'landmark', color: 'from-orange-600 to-amber-500', k13: 'Wajib & Peminatan', merdeka: 'Fase E & F' }
            ],
            materiDetails: {
                'mat': [
                    { title: 'Limit Fungsi Aljabar & Turunan', kurikulum: 'K13 & Merdeka', summary: 'Memahami nilai pendekatan fungsi saat mendekati titik tertentu serta konsep laju perubahan kuantitas.', visual: 'lim (x→a) f(x) = L', tips: 'Gunakan aturan L\'Hopital (turunan pembilang dan penyebut) jika menemukan bentuk tak tentu (0/0).' },
                    { title: 'Vektor & Geometri Ruang (3D)', kurikulum: 'Kurikulum Merdeka', summary: 'Besaran yang memiliki nilai dan arah. Sangat krusial dalam pemodelan gerak fisika dan proyeksi spasial.', visual: 'a · b = |a||b| cos(θ)', tips: 'Pahami perkalian titik (dot product) untuk menentukan sudut antar dua garis ruang.' }
                ],
                'fis': [
                    { title: 'Termodinamika & Hukum Gas Ideal', kurikulum: 'K13 & Merdeka', summary: 'Studi mengenai hubungan antara kalor, energi dalam, serta usaha yang dilakukan sistem.', visual: 'Q = ΔU + W', tips: 'Perhatikan tanda positif/negatif: Q bernilai (+) jika menerima kalor, W bernilai (+) jika melakukan usaha.' }
                ]
            },
            simulasiBank: {
                'utbk-pk': {
                    title: 'UTBK SNBT - Pengetahuan Kuantitatif (PK)',
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
                            &nbsp;&nbsp;&nbsp;• Untuk k = -10 ⇒ -10 + 2 = -8 < 0 (Ditolak, karena menghasilkan akar-akar negatif).<br><br>
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
                            &nbsp;&nbsp;&nbsp;3ⁿ (4) = 36  ⇒  3ⁿ = 9<br>
                            &nbsp;&nbsp;&nbsp;3ⁿ = 3²  ⇒  n = 2.<br><br>
                            3. Hitung nilai 2ⁿ:<br>
                            &nbsp;&nbsp;&nbsp;2ⁿ = 2² = 4.<br><br>
                            <strong>Kesimpulan Jawaban Akurat:</strong> Nilai 2ⁿ = <strong>4 (Pilihan B)</strong>.`
                        }
                    ]
                },
                'tka-saintek': {
                    title: 'TKA Saintek - Fisika HOTS',
                    soal: [
                        {
                            id: 'q1_tka',
                            pertanyaan: 'Sebuah benda bermassa 2 kg bergerak pada bidang datar licin ditarik gaya F = 20 N membentuk sudut 60° terhadap arah horizontal. Berapakah percepatan yang dialami benda tersebut?',
                            pilihan: ['A. 5 m/s²', 'B. 10 m/s²', 'C. 5√3 m/s²', 'D. 20 m/s²', 'E. 10√3 m/s²'],
                            kunci: 'A. 5 m/s²',
                            solusiLengkap: `<strong>Pembahasan Akurat & Langkah Demi Langkah:</strong><br>
                            1. Proyeksikan gaya F pada sumbu horizontal (searah gerak benda):<br>
                            &nbsp;&nbsp;&nbsp;F_x = F · cos(60°)<br>
                            &nbsp;&nbsp;&nbsp;F_x = 20 N · (0,5) = 10 N.<br><br>
                            2. Terapkan Hukum II Newton pada sumbu horizontal (ΣF_x = m · a):<br>
                            &nbsp;&nbsp;&nbsp;10 N = 2 kg · a<br>
                            &nbsp;&nbsp;&nbsp;a = 10 / 2 = 5 m/s².<br><br>
                            <strong>Kesimpulan Jawaban Akurat:</strong> Percepatan benda adalah <strong>5 m/s² (Pilihan A)</strong>.`
                        }
                    ]
                }
            }
        };

        // Render Home Screen
        function renderHome() {
            return `
                <div class="relative rounded-3xl gradient-brand p-8 sm:p-12 overflow-hidden border border-slate-800 shadow-2xl mb-12">
                    <div class="relative z-10 max-w-3xl">
                        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-purple-500/10 border border-purple-500/20 text-purple-300 text-xs font-semibold mb-6">
                            <i data-lucide="sparkles" class="w-4 h-4 text-purple-400"></i>
                            <span>Nihiluxxy Platform v2.5 - Fitur Kurikulum Lengkap</span>
                        </div>
                        <h1 class="text-3xl sm:text-5xl font-black text-white tracking-tight mb-4 leading-tight">
                            Kuasai Konsep SMA & Taklukkan <span class="bg-clip-text text-transparent gradient-accent">UTBK SNBT</span> Akurat.
                        </h1>
                        <p class="text-slate-300 text-sm sm:text-base mb-8 leading-relaxed">
                            Materi terstruktur untuk Kurikulum 2013 & Kurikulum Merdeka (Kelas 10–12). Dilengkapi pembahasan step-by-step super jelas serta rekam jejak riwayat pengerjaan terakhir yang detail.
                        </p>
                        <div class="flex flex-wrap gap-4">
                            <button onclick="switchView('materi')" class="gradient-accent text-white font-bold px-6 py-3.5 rounded-2xl shadow-lg shadow-purple-500/25 hover:opacity-95 transition flex items-center gap-2 text-sm">
                                <i data-lucide="book-open" class="w-4 h-4"></i> Pelajari Materi SMA
                            </button>
                            <button onclick="switchView('utbk')" class="bg-slate-800/80 border border-slate-700 text-white font-bold px-6 py-3.5 rounded-2xl hover:bg-slate-800 transition flex items-center gap-2 text-sm">
                                <i data-lucide="target" class="w-4 h-4 text-amber-400"></i> Simulasi UTBK/TKA
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Kurikulum Toggle Section -->
                <div class="mb-12">
                    <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 mb-6">
                        <div>
                            <h2 class="text-2xl font-black text-white">Bidang Mata Pelajaran</h2>
                            <p class="text-slate-400 text-xs sm:text-sm">Pilih kurikulum untuk melihat cakupan materi terstandarisasi</p>
                        </div>
                        <div class="bg-slate-800/80 p-1 rounded-2xl border border-slate-700 flex gap-1 text-xs font-bold">
                            <button onclick="setKurikulum('Merdeka')" class="px-4 py-2 rounded-xl transition ${state.selectedKurikulum === 'Merdeka' ? 'bg-purple-600 text-white' : 'text-slate-400 hover:text-white'}">Kurikulum Merdeka</button>
                            <button onclick="setKurikulum('K13')" class="px-4 py-2 rounded-xl transition ${state.selectedKurikulum === 'K13' ? 'bg-purple-600 text-white' : 'text-slate-400 hover:text-white'}">Kurikulum 2013 (K13)</button>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-5">
                        ${db.mapel.map(m => `
                            <div class="bg-slate-800/50 border border-slate-700/60 hover:border-purple-500/50 p-5 rounded-2xl transition-all duration-300 hover:-translate-y-1 group cursor-pointer" onclick="openDetailMapel('${m.id}')">
                                <div class="w-12 h-12 rounded-xl bg-gradient-to-br ${m.color} flex items-center justify-center text-white mb-4 shadow-lg group-hover:scale-110 transition">
                                    <i data-lucide="${m.icon}"></i>
                                </div>
                                <h3 class="font-extrabold text-white text-base mb-1 group-hover:text-purple-300 transition">${m.nama}</h3>
                                <p class="text-xs text-purple-400 font-semibold mb-3">
                                    ${state.selectedKurikulum === 'Merdeka' ? m.merdeka : m.k13}
                                </p>
                                <div class="flex items-center justify-between text-xs text-slate-400 pt-3 border-t border-slate-700/40">
                                    <span>Buka Modul Belajar</span>
                                    <i data-lucide="arrow-right" class="w-4 h-4 text-purple-400"></i>
                                </div>
                            </div>
                        `).join('')}
                    </div>
                </div>

                <!-- Snapshot Riwayat Pengerjaan Terakhir -->
                <div class="bg-slate-800/40 border border-slate-800 rounded-3xl p-6 sm:p-8">
                    <div class="flex items-center justify-between mb-4">
                        <div class="flex items-center gap-3">
                            <div class="p-2.5 rounded-xl bg-purple-500/10 text-purple-400">
                                <i data-lucide="history" class="w-5 h-5"></i>
                            </div>
                            <div>
                                <h3 class="font-bold text-white text-base">Riwayat Pengerjaan Terakhir</h3>
                                <p class="text-xs text-slate-400">Evaluasi & pelajari pembahasan akurat dari pengerjaan Anda</p>
                            </div>
                        </div>
                        <button onclick="switchView('riwayat')" class="text-xs text-purple-400 hover:text-purple-300 font-semibold">Lihat Semua Riwayat</button>
                    </div>
                    ${renderLastAttemptCard()}
                </div>
            `;
        }

        // Render Kartu Riwayat Terakhir
        function renderLastAttemptCard() {
            if (state.attempts.length === 0) {
                return `
                    <div class="text-center py-6 text-slate-500 text-xs border border-dashed border-slate-700/60 rounded-2xl">
                        Belum ada simulasi yang diselesaikan. Selesaikan simulasi TKA/UTBK untuk mencatat riwayat akurat Anda di sini.
                    </div>
                `;
            }
            const last = state.attempts[state.attempts.length - 1];
            return `
                <div class="bg-slate-800/80 border border-slate-700 p-4 rounded-2xl flex flex-col sm:flex-row justify-between sm:items-center gap-4">
                    <div>
                        <div class="flex items-center gap-2 mb-1">
                            <span class="text-xs font-bold px-2 py-0.5 rounded bg-emerald-500/20 text-emerald-300 border border-emerald-500/30">Pengerjaan Terakhir</span>
                            <span class="text-xs text-slate-400">${last.tanggal}</span>
                        </div>
                        <h4 class="font-extrabold text-white text-sm sm:text-base">${last.judulSimulasi}</h4>
                        <p class="text-xs text-slate-400 mt-0.5">Akurasi Skor: <span class="text-purple-300 font-bold">${last.skor}%</span> (${last.benar} dari ${last.totalSoal} Soal Benar)</p>
                    </div>
                    <button onclick="openDetailRiwayat(${state.attempts.length - 1})" class="px-4 py-2 bg-purple-600 hover:bg-purple-500 text-white font-bold text-xs rounded-xl transition flex items-center justify-center gap-1.5">
                        <i data-lucide="file-search" class="w-4 h-4"></i> Lihat Pembahasan Akurat
                    </button>
                </div>
            `;
        }

        function setKurikulum(k) {
            state.selectedKurikulum = k;
            switchView('home');
        }

        // Render Materi Screen
        function renderMateriScreen() {
            return `
                <div class="mb-8">
                    <h1 class="text-3xl font-black text-white">Modul Pembelajaran SMA</h1>
                    <p class="text-slate-400 text-sm mt-1">Sederhana, visual, & ramah pemula untuk Kurikulum 2013 dan Merdeka.</p>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <div class="space-y-3">
                        <h3 class="text-xs uppercase tracking-wider font-bold text-purple-400 px-1">Pilih Bidang Mata Pelajaran</h3>
                        ${db.mapel.map(m => `
                            <button onclick="openDetailMapel('${m.id}')" class="w-full text-left p-4 rounded-2xl bg-slate-800/60 border border-slate-700/60 hover:bg-slate-800 hover:border-purple-500/50 transition flex items-center gap-3">
                                <div class="w-8 h-8 rounded-lg bg-gradient-to-br ${m.color} flex items-center justify-center text-white font-bold text-xs">
                                    <i data-lucide="${m.icon}" class="w-4 h-4"></i>
                                </div>
                                <span class="font-bold text-sm text-slate-200">${m.nama}</span>
                            </button>
                        `).join('')}
                    </div>
                    <div id="materi-reader" class="md:col-span-2 bg-slate-800/40 border border-slate-800 rounded-3xl p-6 sm:p-8">
                        <div class="text-center py-12 text-slate-500">
                            <i data-lucide="book-marked" class="w-12 h-12 mx-auto mb-3 text-slate-600"></i>
                            <p class="text-sm">Pilih salah satu mata pelajaran di sebelah kiri untuk menampilkan materi penjelasan.</p>
                        </div>
                    </div>
                </div>
            `;
        }

        function openDetailMapel(mapelId) {
            if (state.activeView !== 'materi') switchView('materi');
            const mapel = db.mapel.find(m => m.id === mapelId);
            const materiList = db.materiDetails[mapelId] || [
                { title: 'Konsep Dasar & Formula Inti', kurikulum: 'K13 & Merdeka', summary: 'Penjelasan menyeluruh mengenai materi dasar bab ini dengan analogi kehidupan sehari-hari.', visual: 'Rumus Utama: X = a + b(t)', tips: 'Pahami pola dasar sebelum memecahkan variasi soal latihan.' }
            ];

            const reader = document.getElementById('materi-reader');
            if (reader) {
                reader.innerHTML = `
                    <div class="flex items-center gap-3 mb-6 pb-4 border-b border-slate-700/60">
                        <div class="w-10 h-10 rounded-xl bg-gradient-to-br ${mapel.color} flex items-center justify-center text-white font-bold">
                            <i data-lucide="${mapel.icon}"></i>
                        </div>
                        <div>
                            <h2 class="text-xl font-black text-white">${mapel.nama}</h2>
                            <p class="text-xs text-purple-400 font-semibold">Modul Pembelajaran K13 & Kurikulum Merdeka</p>
                        </div>
                    </div>
                    <div class="space-y-6">
                        ${materiList.map(mat => `
                            <div class="bg-slate-900/80 border border-slate-700/80 p-6 rounded-2xl">
                                <div class="flex items-center justify-between mb-3">
                                    <span class="text-[10px] font-extrabold uppercase tracking-wider bg-purple-500/20 text-purple-300 px-2.5 py-1 rounded-full border border-purple-500/30">${mat.kurikulum}</span>
                                    <span class="text-xs text-slate-500">Estimasi: 5 min</span>
                                </div>
                                <h3 class="text-lg font-bold text-white mb-2">${mat.title}</h3>
                                <p class="text-slate-300 text-sm mb-4 leading-relaxed">${mat.summary}</p>
                                
                                <div class="bg-slate-800 p-4 rounded-xl font-mono text-xs text-purple-300 mb-4 border border-slate-700/50 text-center">
                                    ${mat.visual}
                                </div>

                                <div class="bg-amber-500/10 border-l-4 border-amber-500 p-3.5 rounded-r-xl text-xs text-amber-200">
                                    <strong>💡 Tips Cepat Nyantol:</strong> ${mat.tips}
                                </div>
                            </div>
                        `).join('')}
                    </div>
                `;
                lucide.createIcons();
            }
        }

        // Render UTBK Screen
        function renderUTBKScreen() {
            return `
                <div class="mb-8">
                    <h1 class="text-3xl font-black text-white">Simulasi TKA & UTBK SNBT</h1>
                    <p class="text-slate-400 text-sm mt-1">Uji kemampuan dengan sistem jawaban interaktif dan simpan riwayat pembahasan akurat.</p>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="bg-slate-800/50 border border-slate-700/80 p-6 rounded-3xl flex flex-col justify-between">
                        <div>
                            <div class="w-12 h-12 rounded-2xl bg-amber-500/20 border border-amber-500/30 text-amber-400 flex items-center justify-center mb-4 font-black">
                                <i data-lucide="calculator" class="w-6 h-6"></i>
                            </div>
                            <span class="text-[10px] uppercase tracking-widest font-bold text-amber-400 bg-amber-500/10 px-2 py-0.5 rounded-md">SNBT Standard</span>
                            <h3 class="text-xl font-bold text-white mt-2 mb-1">UTBK - Pengetahuan Kuantitatif</h3>
                            <p class="text-slate-400 text-xs mb-6">Uji pemahaman aljabar, eksponen, & logika matematika HOTS.</p>
                        </div>
                        <button onclick="startSimulasi('utbk-pk')" class="w-full py-3 bg-amber-500 hover:bg-amber-400 text-slate-900 font-extrabold text-xs rounded-xl transition flex items-center justify-center gap-2">
                            <i data-lucide="play" class="w-4 h-4"></i> Mulai Tes Pengetahuan Kuantitatif
                        </button>
                    </div>

                    <div class="bg-slate-800/50 border border-slate-700/80 p-6 rounded-3xl flex flex-col justify-between">
                        <div>
                            <div class="w-12 h-12 rounded-2xl bg-indigo-500/20 border border-indigo-500/30 text-indigo-400 flex items-center justify-center mb-4 font-black">
                                <i data-lucide="zap" class="w-6 h-6"></i>
                            </div>
                            <span class="text-[10px] uppercase tracking-widest font-bold text-indigo-400 bg-indigo-500/10 px-2 py-0.5 rounded-md">TKA High Level</span>
                            <h3 class="text-xl font-bold text-white mt-2 mb-1">TKA Saintek - Fisika HOTS</h3>
                            <p class="text-slate-400 text-xs mb-6">Uji penalaran fisika mekanika, gaya Newton, & vektor.</p>
                        </div>
                        <button onclick="startSimulasi('tka-saintek')" class="w-full py-3 bg-indigo-600 hover:bg-indigo-500 text-white font-extrabold text-xs rounded-xl transition flex items-center justify-center gap-2">
                            <i data-lucide="play" class="w-4 h-4"></i> Mulai Tes TKA Fisika
                        </button>
                    </div>
                </div>
            `;
        }

        let simAnswers = {};

        function startSimulasi(simKey) {
            const currentSim = db.simulasiBank[simKey];
            simAnswers = {};
            
            const app = document.getElementById('app-content');
            app.innerHTML = `
                <div class="max-w-3xl mx-auto bg-slate-800/90 border border-slate-700 p-6 sm:p-8 rounded-3xl shadow-2xl">
                    <div class="flex items-center justify-between pb-4 border-b border-slate-700/80 mb-6">
                        <div>
                            <span class="text-xs font-bold text-purple-400">Simulasi Berjalan</span>
                            <h2 class="text-lg font-black text-white">${currentSim.title}</h2>
                        </div>
                    </div>

                    <div id="quiz-container" class="space-y-8">
                        ${currentSim.soal.map((q, idx) => `
                            <div class="bg-slate-900/60 p-5 rounded-2xl border border-slate-800">
                                <span class="text-xs font-bold text-slate-400 mb-2 block">Soal Nomor ${idx + 1}</span>
                                <p class="text-sm sm:text-base text-slate-200 font-medium mb-4 leading-relaxed">${q.pertanyaan}</p>
                                <div class="space-y-2.5">
                                    ${q.pilihan.map(opt => `
                                        <label class="flex items-center p-3 rounded-xl border border-slate-700/60 hover:bg-slate-800 hover:border-purple-500/50 transition cursor-pointer">
                                            <input type="radio" name="question_${q.id}" value="${opt}" onchange="recordAnswer('${q.id}', '${opt}')" class="text-purple-600 focus:ring-purple-500 bg-slate-800 border-slate-600">
                                            <span class="ml-3 text-xs sm:text-sm text-slate-300 font-medium">${opt}</span>
                                        </label>
                                    `).join('')}
                                </div>
                            </div>
                        `).join('')}
                    </div>

                    <div class="mt-8 pt-4 border-t border-slate-700/80 flex justify-between items-center">
                        <button onclick="switchView('utbk')" class="px-4 py-2 border border-slate-700 text-slate-400 hover:text-white text-xs font-bold rounded-xl">Batal</button>
                        <button onclick="submitSimulasi('${simKey}')" class="px-6 py-3 gradient-accent text-white font-black text-xs rounded-xl shadow-lg hover:opacity-95 transition">
                            Selesaikan & Simpan Hasil
                        </button>
                    </div>
                </div>
            `;
            lucide.createIcons();
        }

        function recordAnswer(qId, val) {
            simAnswers[qId] = val;
        }

        function submitSimulasi(simKey) {
            const sim = db.simulasiBank[simKey];
            let benarCount = 0;
            const total = sim.soal.length;

            const reviewDetails = sim.soal.map(q => {
                const userAns = simAnswers[q.id] || 'Tidak Dijawab';
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
            const dateStr = now.toLocaleDateString('id-ID', { day: 'numeric', month: 'short', year: 'numeric', hour: '2-digit', minute: '2-digit' });

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

        // Render Riwayat Screen
        function renderRiwayatScreen() {
            if (state.attempts.length === 0) {
                return `
                    <div class="mb-8">
                        <h1 class="text-3xl font-black text-white">Riwayat Pengerjaan</h1>
                        <p class="text-slate-400 text-sm mt-1">Daftar evaluasi simulasi dan pembahasan akurat Anda.</p>
                    </div>
                    <div class="bg-slate-800/40 border border-slate-800 rounded-3xl p-12 text-center text-slate-500">
                        <i data-lucide="history" class="w-12 h-12 mx-auto mb-3 text-slate-600"></i>
                        <p class="text-sm font-semibold">Belum Ada Riwayat Tersimpan</p>
                        <p class="text-xs text-slate-600 mt-1 mb-4">Selesaikan simulasi TKA/UTBK untuk mencatat riwayat jawaban akurat Anda.</p>
                        <button onclick="switchView('utbk')" class="px-5 py-2.5 bg-purple-600 hover:bg-purple-500 text-white font-bold text-xs rounded-xl transition">
                            Mulai Simulasi Sekarang
                        </button>
                    </div>
                `;
            }

            return `
                <div class="mb-8">
                    <h1 class="text-3xl font-black text-white">Riwayat & Pembahasan Akurat</h1>
                    <p class="text-slate-400 text-sm mt-1">Pilih pengerjaan di bawah untuk memeriksa kunci jawaban & cara pengerjaan terperinci.</p>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <div class="space-y-3">
                        <h3 class="text-xs uppercase tracking-wider font-bold text-purple-400 px-1">Daftar Pengerjaan</h3>
                        ${state.attempts.map((att, idx) => `
                            <button onclick="openDetailRiwayat(${idx})" class="w-full text-left p-4 rounded-2xl bg-slate-800/60 border border-slate-700/60 hover:bg-slate-800 transition flex items-center justify-between">
                                <div>
                                    <span class="text-[10px] text-slate-400 font-mono block">${att.tanggal}</span>
                                    <h4 class="font-bold text-xs sm:text-sm text-white">${att.judulSimulasi}</h4>
                                </div>
                                <span class="text-sm font-black text-purple-300 font-mono">${att.skor}%</span>
                            </button>
                        `).join('')}
                    </div>

                    <div id="riwayat-detail-container" class="md:col-span-2 bg-slate-800/40 border border-slate-800 rounded-3xl p-6 sm:p-8">
                        <!-- Detail riwayat akan dimuat di sini -->
                    </div>
                </div>
            `;
        }

        function openDetailRiwayat(index) {
            if (state.activeView !== 'riwayat') switchView('riwayat');

            const att = state.attempts[index];
            const container = document.getElementById('riwayat-detail-container');
            if (!container) return;

            container.innerHTML = `
                <div class="flex items-center justify-between pb-4 border-b border-slate-700/80 mb-6">
                    <div>
                        <span class="text-xs text-purple-400 font-bold">${att.tanggal}</span>
                        <h2 class="text-xl font-black text-white">${att.judulSimulasi}</h2>
                    </div>
                    <div class="text-right">
                        <span class="text-2xl font-black text-purple-300 font-mono">${att.skor}%</span>
                        <p class="text-[10px] text-slate-400 font-semibold">${att.benar} dari ${att.totalSoal} Soal Benar</p>
                    </div>
                </div>

                <div class="space-y-6">
                    ${att.detail.map((d, i) => `
                        <div class="bg-slate-900/90 border ${d.isCorrect ? 'border-emerald-500/40' : 'border-rose-500/40'} p-5 rounded-2xl">
                            <div class="flex items-center justify-between mb-2">
                                <span class="text-xs font-bold text-slate-400">Soal #${i + 1}</span>
                                <span class="text-xs font-extrabold px-2 py-0.5 rounded ${d.isCorrect ? 'bg-emerald-500/20 text-emerald-300' : 'bg-rose-500/20 text-rose-300'}">
                                    ${d.isCorrect ? '✓ Jawaban Benar' : '✗ Kurang Tepat'}
                                </span>
                            </div>
                            <p class="text-sm text-slate-200 font-medium mb-4">${d.pertanyaan}</p>
                            
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 mb-4 text-xs font-semibold">
                                <div class="bg-slate-800 p-3 rounded-xl border border-slate-700">
                                    <span class="text-slate-500 block text-[10px]">Jawaban Anda:</span>
                                    <span class="${d.isCorrect ? 'text-emerald-300' : 'text-rose-300'}">${d.jawabanUser}</span>
                                </div>
                                <div class="bg-slate-800 p-3 rounded-xl border border-slate-700">
                                    <span class="text-slate-500 block text-[10px]">Kunci Akurat:</span>
                                    <span class="text-emerald-300">${d.kunci}</span>
                                </div>
                            </div>

                            <div class="bg-purple-950/40 border border-purple-800/40 p-4 rounded-xl text-xs text-slate-300 leading-relaxed">
                                <span class="text-purple-300 font-bold block mb-1">📘 Cara & Pembahasan Akurat:</span>
                                ${d.solusi}
                            </div>
                        </div>
                    `).join('')}
                </div>
            `;
            lucide.createIcons();
        }

        // Navigation Controller
        function switchView(viewName) {
            state.activeView = viewName;

            ['home', 'materi', 'utbk', 'riwayat'].forEach(v => {
                const el = document.getElementById(`nav-${v}`);
                if (el) {
                    if (v === viewName) {
                        el.className = "px-4 py-2 rounded-xl text-white bg-purple-600 transition font-bold";
                    } else {
                        el.className = "px-4 py-2 rounded-xl text-slate-300 hover:text-white transition font-semibold";
                    }
                }
            });

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

        document.addEventListener('DOMContentLoaded', () => {
            switchView('home');
        });
    </script>
</body>
</html>
