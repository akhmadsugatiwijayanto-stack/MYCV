<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>Galeri Dokumentasi Kegiatan | Arsip 50 Momen</title>
    <!-- Google Fonts & Font Awesome for Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(145deg, #f8fafc 0%, #eef2f5 100%);
            color: #0a1e2f;
            line-height: 1.5;
            scroll-behavior: smooth;
        }

        /* container utama */
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem 1.5rem 4rem;
        }

        /* Header / hero */
        .hero {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }
        .hero h1 {
            font-size: 2.8rem;
            font-weight: 700;
            background: linear-gradient(135deg, #1e3c5c, #2a5f8a);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            letter-spacing: -0.5px;
            margin-bottom: 0.75rem;
        }
        .hero .badge {
            display: inline-block;
            background: rgba(30,60,92,0.12);
            backdrop-filter: blur(2px);
            padding: 0.3rem 1rem;
            border-radius: 40px;
            font-size: 0.85rem;
            font-weight: 500;
            color: #1e4a76;
            margin-bottom: 1rem;
        }
        .hero p {
            max-width: 650px;
            margin: 0 auto;
            color: #2c4966;
            font-weight: 400;
            font-size: 1.05rem;
        }
        .stats-info {
            margin-top: 1.2rem;
            display: flex;
            justify-content: center;
            gap: 2rem;
            flex-wrap: wrap;
        }
        .stat-card {
            background: white;
            border-radius: 60px;
            padding: 0.4rem 1.2rem;
            box-shadow: 0 2px 8px rgba(0,0,0,0.03);
            font-size: 0.9rem;
            font-weight: 500;
            color: #1f5e8c;
        }
        .stat-card i {
            margin-right: 6px;
            color: #e07c3c;
        }

        /* filter & search */
        .toolbar {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            gap: 1rem;
            margin-bottom: 2rem;
            background: rgba(255,255,255,0.7);
            backdrop-filter: blur(8px);
            padding: 0.8rem 1.5rem;
            border-radius: 60px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.02), 0 1px 1px rgba(0,0,0,0.05);
        }
        .search-box {
            display: flex;
            align-items: center;
            background: white;
            border-radius: 48px;
            padding: 0.3rem 0.8rem;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
            border: 1px solid #e2edf2;
        }
        .search-box i {
            color: #8aaec0;
            font-size: 1rem;
        }
        #searchInput {
            border: none;
            padding: 0.6rem 0.8rem;
            font-size: 0.9rem;
            width: 220px;
            background: transparent;
            outline: none;
            font-family: inherit;
        }
        .filter-group {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }
        .filter-btn {
            background: white;
            border: 1px solid #dce5ec;
            padding: 0.45rem 1.1rem;
            border-radius: 40px;
            font-weight: 500;
            font-size: 0.8rem;
            cursor: pointer;
            transition: all 0.2s;
            color: #2c4c6e;
        }
        .filter-btn.active {
            background: #1e5a7d;
            border-color: #1e5a7d;
            color: white;
            box-shadow: 0 4px 8px rgba(0,80,120,0.2);
        }
        .filter-btn:hover:not(.active) {
            background: #e6f0f5;
            border-color: #bdd4e2;
        }

        /* masonry grid style - rapi dan modern */
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.6rem;
        }

        /* kartu foto */
        .photo-card {
            background: white;
            border-radius: 24px;
            overflow: hidden;
            box-shadow: 0 12px 26px -12px rgba(0, 0, 0, 0.12);
            transition: all 0.3s ease;
            cursor: pointer;
            opacity: 0;
            transform: translateY(18px);
            animation: fadeInUp 0.4s forwards;
            display: flex;
            flex-direction: column;
        }
        .photo-card:hover {
            transform: translateY(-6px);
            box-shadow: 0 22px 32px -14px rgba(0, 0, 0, 0.2);
        }
        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .img-wrapper {
            width: 100%;
            aspect-ratio: 4 / 3;
            overflow: hidden;
            background: #eef3f7;
            position: relative;
        }
        .img-wrapper img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s ease;
            display: block;
        }
        .photo-card:hover .img-wrapper img {
            transform: scale(1.03);
        }
        .card-caption {
            padding: 1rem 1.2rem 1.2rem;
        }
        .card-caption h3 {
            font-size: 1rem;
            font-weight: 600;
            color: #1d3b53;
            margin-bottom: 0.35rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .card-caption p {
            font-size: 0.75rem;
            color: #7196ae;
            display: flex;
            align-items: center;
            gap: 8px;
            margin-top: 6px;
        }
        .photo-number {
            background: #eef2f5;
            border-radius: 50px;
            padding: 0.2rem 0.6rem;
            font-size: 0.7rem;
            font-weight: 500;
        }

        /* modal lightbox */
        .lightbox {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(10, 25, 40, 0.94);
            backdrop-filter: blur(12px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2000;
            visibility: hidden;
            opacity: 0;
            transition: visibility 0.2s, opacity 0.25s;
        }
        .lightbox.active {
            visibility: visible;
            opacity: 1;
        }
        .lb-content {
            max-width: 90vw;
            max-height: 85vh;
            position: relative;
            background: rgba(20,20,30,0.2);
            border-radius: 28px;
            overflow: hidden;
        }
        .lb-content img {
            max-width: 100%;
            max-height: 80vh;
            display: block;
            border-radius: 20px;
            box-shadow: 0 20px 35px rgba(0,0,0,0.3);
        }
        .lb-caption {
            text-align: center;
            color: white;
            margin-top: 1rem;
            font-weight: 500;
            letter-spacing: 0.3px;
        }
        .close-lb {
            position: absolute;
            top: 20px;
            right: 30px;
            font-size: 2rem;
            color: white;
            cursor: pointer;
            background: rgba(0,0,0,0.5);
            width: 44px;
            height: 44px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: 0.2s;
        }
        .close-lb:hover {
            background: #c2410c;
            transform: scale(1.02);
        }
        .nav-lb {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0,0,0,0.6);
            color: white;
            font-size: 1.8rem;
            width: 48px;
            height: 48px;
            border-radius: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: 0.2s;
        }
        .nav-lb.prev {
            left: 20px;
        }
        .nav-lb.next {
            right: 20px;
        }
        .nav-lb:hover {
            background: #e07c3c;
        }
        @media (max-width: 640px) {
            .container { padding: 1rem 1rem 2rem; }
            .hero h1 { font-size: 1.8rem; }
            .toolbar { flex-direction: column; align-items: stretch; border-radius: 28px; }
            .search-box { width: 100%; }
            #searchInput { width: 100%; }
            .filter-group { justify-content: center; }
            .gallery { grid-template-columns: 1fr; gap: 1.2rem; }
        }

        /* empty state */
        .empty-message {
            text-align: center;
            padding: 3rem;
            background: white;
            border-radius: 40px;
            color: #5f7f9a;
            font-weight: 500;
        }

        footer {
            margin-top: 3rem;
            text-align: center;
            font-size: 0.75rem;
            color: #68839b;
            border-top: 1px solid #d4e2ec;
            padding-top: 2rem;
        }
    </style>
</head>
<body>

<div class="container">
    <div class="hero">
        <div class="badge"><i class="fas fa-camera-retro"></i> Arsip Visual</div>
        <h1>Dokumentasi Kegiatan</h1>
        <p>Menangkap setiap momen berharga — dari persiapan hingga puncak acara. 50 foto penuh cerita.</p>
        <div class="stats-info">
            <span class="stat-card"><i class="fas fa-images"></i> Total 50 Foto</span>
            <span class="stat-card"><i class="fas fa-calendar-alt"></i> Kegiatan 2025</span>
        </div>
    </div>

    <div class="toolbar">
        <div class="search-box">
            <i class="fas fa-search"></i>
            <input type="text" id="searchInput" placeholder="Cari deskripsi / nomor foto..." autocomplete="off">
        </div>
        <div class="filter-group" id="filterGroup">
            <button class="filter-btn active" data-filter="all">Semua</button>
            <button class="filter-btn" data-filter="workshop">Workshop</button>
            <button class="filter-btn" data-filter="seremonial">Seremonial</button>
            <button class="filter-btn" data-filter="kebersamaan">Kebersamaan</button>
            <button class="filter-btn" data-filter="dokumentasi">Dokumentasi</button>
        </div>
    </div>

    <div class="gallery" id="galleryContainer">
        <!-- foto2 akan di inject via JS, 50 foto dinamis -->
        <div class="empty-message" style="display: none;" id="emptyMsg">✨ Tidak ada foto yang cocok dengan pencarian atau filter.</div>
    </div>
    <footer>
        <i class="far fa-images"></i> Galeri kegiatan — 50 momen terbaik •  Dokumentasi resmi
    </footer>
</div>

<!-- Lightbox Modal -->
<div id="lightbox" class="lightbox">
    <div class="close-lb" id="closeLbBtn"><i class="fas fa-times"></i></div>
    <div class="nav-lb prev" id="prevBtn"><i class="fas fa-chevron-left"></i></div>
    <div class="nav-lb next" id="nextBtn"><i class="fas fa-chevron-right"></i></div>
    <div class="lb-content">
        <img id="lbImage" src="" alt="lightbox view">
        <div class="lb-caption" id="lbCaption"></div>
    </div>
</div>

<script>
    // ---------------------------------------------------------
    // MEMBUAT 50 DATA FOTO (dummy dengan placeholder berkualitas tinggi dari picsum + variasi)
    // Menggunakan tema kegiatan yang variatif dengan kategori.
    // Supaya elegan dan tidak bergantung file eksternal, 
    // kita gunakan placeholder image dari "picsum.photos" plus ID unik.
    // Tapi agar lebih meyakinkan dan fleksibel, kita buat judul & caption menarik.
    // ---------------------------------------------------------
    const totalPhotos = 50;
    const categories = ['workshop', 'seremonial', 'kebersamaan', 'dokumentasi'];
    const categoryNames = {
        workshop: '🎓 Workshop & Pelatihan',
        seremonial: '🏆 Seremonial & Pembukaan',
        kebersamaan: '🤝 Kebersamaan & Team Building',
        dokumentasi: '📸 Dokumentasi & Behind The Scene'
    };
    
    // Kumpulan judul menarik
    const workshopTitles = [
        "Diskusi Interaktif", "Latihan Teknis", "Presentasi Mentor", "Sesi Tanya Jawab", "Praktik Langsung",
        "Demo Produk", "Studi Kasus", "Role Playing", "Evaluasi Kelompok", "Inovasi Sprint"
    ];
    const seremonialTitles = [
        "Pembukaan Acara", "Sambutan Ketua", "Penyerahan Penghargaan", "Pemotongan Pita", "Doa Bersama",
        "Menyanyikan Lagu Kebangsaan", "Pidato Inspiratif", "Launching Program", "Penandatanganan MoU", "Flasmob Pembukaan"
    ];
    const kebersamaanTitles = [
        "Sesi Ice Breaking", "Foto Keluarga Besar", "Makan Bersama", "Outbound Fun", "Kegiatan Sosial",
        "Lomba Kreatif", "Berkebun Bersama", "City Tour", "Refleksi Malam", "Api Unggun"
    ];
    const dokumentasiTitles = [
        "Behind the Scene", "Sudut Ruangan", "Persiapan Panitia", "Wawancara Peserta", "Peralatan Acara",
        "Momen Candid", "Dekorasi Panggung", "Interaksi Audiens", "Sorotan Kamera", "Panitia Action"
    ];
    
    // helper random dari array
    function getRandomItem(arr) {
        return arr[Math.floor(Math.random() * arr.length)];
    }
    
    // generate caption deskripsi pendek
    function generateDesc(title, cat, idx) {
        let base = `Foto #${idx+1} - ${title}. Momen berharga dari kegiatan yang penuh makna.`;
        if (cat === 'workshop') base += ` Peserta antusias mengikuti sesi.`;
        else if (cat === 'seremonial') base += ` Suasana khidmat dan meriah.`;
        else if (cat === 'kebersamaan') base += ` Kebersamaan yang hangat tercipta.`;
        else base += ` Dokumentasi eksklusif momen tak terlupakan.`;
        return base;
    }
    
    // membuat array foto dengan image dari picsum (unsplash random style) + alternatif tema yang bagus secara visual
    // supaya gambar bervariasi namun tetap foto realistis, kita gunakan "picsum.photos/id/..." 
    // kita pilih ID yang memberikan suasana netral (bisa orang, tempat, dll). Agar tidak terlalu abstrak, gunakan tema tertentu.
    // Lebih baik kita mapping 50 gambar dengan gaya dokumenter / event menggunakan picsum + seed.
    // Tapi karena picsum sering menampilkan landscape / abstract, namun tetap kelihatan profesional.
    // Alternatif: menggunakan placeholder dengan kategori warna, tapi lebih baik beragam.
    // Saya mengkombinasikan gambar acak dari picsum yang memiliki style 'people/event' via id tertentu.
    // Untuk dokumentasi yang lebih mantap, kita set gambar yang 'cocok' menggunakan ID yang menghasilkan foto orang / pertemuan.
    const picsumEventIds = [20, 26, 42, 55, 64, 76, 89, 91, 102, 115, 128, 136, 155, 169, 177, 188, 200, 212, 225, 239, 250, 261, 277, 289, 300, 312, 328, 340, 357, 366, 377, 388, 395, 407, 418, 429, 440, 455, 469, 477, 488, 499, 510, 525, 539, 550, 567, 578, 590, 600];
    // pastikan memiliki 50 id 
    while(picsumEventIds.length < totalPhotos) picsumEventIds.push(42); // fallback
    
    const photoData = [];
    for (let i = 0; i < totalPhotos; i++) {
        // tentukan kategori secara seimbang (masing2 sekitar 12-13)
        let cat;
        if (i < 12) cat = 'workshop';
        else if (i < 24) cat = 'seremonial';
        else if (i < 37) cat = 'kebersamaan';
        else cat = 'dokumentasi';
        
        // pilih judul sesuai kategori
        let title = "";
        if (cat === 'workshop') title = `${getRandomItem(workshopTitles)} (Sesi ${Math.floor(i/3)+1})`;
        else if (cat === 'seremonial') title = getRandomItem(seremonialTitles);
        else if (cat === 'kebersamaan') title = getRandomItem(kebersamaanTitles);
        else title = getRandomItem(dokumentasiTitles);
        
        // tambahkan variasi nomor
        const finalTitle = `${title} — Momen ${i+1}`;
        const description = generateDesc(finalTitle, cat, i);
        // gambar: menggunakan foto dari picsum dengan resolusi 800x600 agar tampil bagus dan responsif
        const imageId = picsumEventIds[i % picsumEventIds.length];
        // menambahkan random seed kecil agar gambar tidak terlalu sama? gunakan id berbeda unik.
        const imageUrl = `https://picsum.photos/id/${imageId}/800/600?grayscale=&seed=kegiatan${i}`;
        // beberapa gambar mungkin akan terlihat tidak event, tapi tetap artistik. alternatif bisa juga unplash? tapi ini legal.
        // Agar lebih meyakinkan secara visual kita juga tambahkan efek overlay? tidak masalah.
        photoData.push({
            id: i,
            title: finalTitle,
            category: cat,
            desc: description,
            imgUrl: imageUrl,
            thumbnail: imageUrl // kita pakai url yang sama, nanti grid menggunakan image yg sama dioptimasi via css
        });
    }
    
    // variabel global untuk state
    let currentFilter = "all";
    let searchKeyword = "";
    let currentLightboxIndex = 0;
    let filteredPhotos = [...photoData];
    
    // DOM elements
    const galleryContainer = document.getElementById('galleryContainer');
    const searchInput = document.getElementById('searchInput');
    const filterBtns = document.querySelectorAll('.filter-btn');
    const emptyMsgDiv = document.getElementById('emptyMsg');
    const lightboxEl = document.getElementById('lightbox');
    const lbImage = document.getElementById('lbImage');
    const lbCaption = document.getElementById('lbCaption');
    const closeLb = document.getElementById('closeLbBtn');
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    
    // fungsi render gallery
    function renderGallery() {
        // filter berdasarkan keyword dan kategori
        let filtered = photoData.filter(photo => {
            const matchCategory = (currentFilter === 'all' || photo.category === currentFilter);
            const matchSearch = searchKeyword.trim() === "" || 
                photo.title.toLowerCase().includes(searchKeyword.toLowerCase()) ||
                photo.desc.toLowerCase().includes(searchKeyword.toLowerCase()) ||
                `foto ${photo.id+1}`.includes(searchKeyword.toLowerCase()) ||
                `#${photo.id+1}`.includes(searchKeyword);
            return matchCategory && matchSearch;
        });
        filteredPhotos = filtered;
        
        if (filtered.length === 0) {
            galleryContainer.innerHTML = '';
            emptyMsgDiv.style.display = 'block';
            galleryContainer.appendChild(emptyMsgDiv);
            return;
        }
        emptyMsgDiv.style.display = 'none';
        
        // generate cards
        galleryContainer.innerHTML = '';
        filtered.forEach((photo, idx) => {
            const card = document.createElement('div');
            card.className = 'photo-card';
            // animasi delay micro
            card.style.animationDelay = `${Math.min(idx * 0.02, 0.2)}s`;
            
            // inner structure
            card.innerHTML = `
                <div class="img-wrapper">
                    <img src="${photo.imgUrl}" alt="${photo.title}" loading="lazy">
                </div>
                <div class="card-caption">
                    <h3>
                        <span>${photo.title.length > 45 ? photo.title.slice(0,42)+'...' : photo.title}</span>
                        <span class="photo-number">#${photo.id+1}</span>
                    </h3>
                    <p><i class="fas fa-tag"></i> ${categoryNames[photo.category] || photo.category} • <i class="far fa-comment"></i> ${photo.desc.slice(0, 70)}${photo.desc.length>70?'…':''}</p>
                </div>
            `;
            // event untuk buka lightbox
            card.addEventListener('click', (e) => {
                // cari index sebenarnya di filteredPhotos
                const realIndex = filteredPhotos.findIndex(p => p.id === photo.id);
                if(realIndex !== -1) openLightbox(realIndex);
            });
            galleryContainer.appendChild(card);
        });
    }
    
    // Lightbox logic
    function openLightbox(index) {
        if (filteredPhotos.length === 0) return;
        currentLightboxIndex = index;
        updateLightboxContent();
        lightboxEl.classList.add('active');
        document.body.style.overflow = 'hidden';
    }
    
    function updateLightboxContent() {
        if (!filteredPhotos.length) return;
        const photo = filteredPhotos[currentLightboxIndex];
        if (photo) {
            lbImage.src = photo.imgUrl;
            lbCaption.innerHTML = `<strong>${photo.title}</strong> &nbsp;| ${photo.desc} <span style="opacity:0.7;">  (${currentLightboxIndex+1}/${filteredPhotos.length})</span>`;
        }
    }
    
    function closeLightbox() {
        lightboxEl.classList.remove('active');
        document.body.style.overflow = '';
    }
    
    function nextPhoto() {
        if (filteredPhotos.length === 0) return;
        currentLightboxIndex = (currentLightboxIndex + 1) % filteredPhotos.length;
        updateLightboxContent();
    }
    
    function prevPhoto() {
        if (filteredPhotos.length === 0) return;
        currentLightboxIndex = (currentLightboxIndex - 1 + filteredPhotos.length) % filteredPhotos.length;
        updateLightboxContent();
    }
    
    // event listener filter & search
    function attachEvents() {
        searchInput.addEventListener('input', (e) => {
            searchKeyword = e.target.value;
            renderGallery();
        });
        
        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                const filterValue = btn.getAttribute('data-filter');
                currentFilter = filterValue;
                filterBtns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                renderGallery();
            });
        });
        
        // lightbox controls
        closeLb.addEventListener('click', closeLightbox);
        prevBtn.addEventListener('click', prevPhoto);
        nextBtn.addEventListener('click', nextPhoto);
        lightboxEl.addEventListener('click', (e) => {
            if (e.target === lightboxEl) closeLightbox();
        });
        document.addEventListener('keydown', (e) => {
            if (!lightboxEl.classList.contains('active')) return;
            if (e.key === 'Escape') closeLightbox();
            if (e.key === 'ArrowRight') nextPhoto();
            if (e.key === 'ArrowLeft') prevPhoto();
        });
    }
    
    // inisialisasi pertama
    function init() {
        attachEvents();
        renderGallery();
        // optional: preload antusias
        console.log(`Galeri siap dengan ${photoData.length} foto unggulan.`);
    }
    
    init();
</script>
</body>
</html>
