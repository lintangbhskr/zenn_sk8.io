<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ZENNSK8 — Skateshop</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Space+Grotesk:wght@400;500;700&display=swap" rel="stylesheet">
<style>
  :root{
    --asphalt: #191919;
    --concrete: #262625;
    --concrete-2: #302f2d;
    --chalk: #f1efe9;
    --chalk-dim: #b8b5ac;
    --spray: #ff5a1f;
    --deck-tan: #c9a66b;
    --low: #e8493a;
    --ok: #7fae5c;
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  body{
    background:
      radial-gradient(#2c2b28 1px, transparent 1px),
      var(--asphalt);
    background-size: 14px 14px, auto;
    color:var(--chalk);
    font-family:'Space Grotesk', sans-serif;
    line-height:1.5;
  }
  a{color:inherit;}

  /* ---- NAV ---- */
  nav{
    display:flex; justify-content:space-between; align-items:center;
    padding:22px 6vw;
    border-bottom:1px solid #383734;
    background:var(--asphalt);
  }
  .logo{ font-family:'Anton', sans-serif; font-size:22px; letter-spacing:1px; cursor:default; }
  .logo span{color:var(--spray);}
  nav a.contact-link{
    font-size:14px; color:var(--chalk-dim); text-decoration:none;
    border-bottom:1px solid #4a4844; padding-bottom:2px;
  }
  nav a.contact-link:hover{color:var(--chalk); border-color:var(--chalk);}

  /* ---- HERO ---- */
  .hero{ position:relative; padding:14vh 6vw 10vh; overflow:hidden; background:var(--asphalt); }
  .hero .eyebrow{
    display:inline-flex; align-items:center; gap:8px;
    font-size:13px; color:var(--chalk-dim); margin-bottom:18px;
  }
  .hero .eyebrow .dot{ width:7px; height:7px; border-radius:50%; background:var(--spray); }
  .hero h1{
    font-family:'Anton', sans-serif; font-size:clamp(52px, 12vw, 150px);
    line-height:0.85; letter-spacing:1px; transform:skewX(-6deg); display:inline-block;
  }
  .hero h1 .out{ -webkit-text-stroke:2px var(--chalk); color:transparent; display:block;}
  .hero h1 .fill{ color:var(--spray); display:block;}
  .hero p{ max-width:480px; margin-top:28px; color:var(--chalk-dim); font-size:17px; }
  .hero .cta{
    display:inline-block; margin-top:32px; background:var(--spray); color:var(--asphalt);
    font-weight:700; text-decoration:none; padding:14px 26px; border-radius:2px;
  }
  .hero .stripe{
    position:absolute; right:-5%; top:0; bottom:0; width:220px;
    background:repeating-linear-gradient(-6deg, var(--concrete-2) 0 18px, transparent 18px 36px);
    opacity:0.5; pointer-events:none;
  }

  /* ---- MARQUEE ---- */
  .marquee{
    background:var(--spray); color:var(--asphalt);
    overflow:hidden; white-space:nowrap;
    border-top:1px solid #1c1c1c; border-bottom:1px solid #1c1c1c;
  }
  .marquee-track{
    display:inline-flex; gap:36px; padding:11px 0;
    animation:scroll-left 22s linear infinite;
  }
  .marquee-track span{
    font-family:'Anton', sans-serif; font-size:14px; letter-spacing:1px;
  }
  @keyframes scroll-left{ from{ transform:translateX(0); } to{ transform:translateX(-50%); } }
  @media (prefers-reduced-motion: reduce){ .marquee-track{ animation:none; } }

  /* ---- WHY US ---- */
  .why-section{ padding:9vh 6vw; border-bottom:1px solid #383734; }
  .why-grid{ display:grid; grid-template-columns:repeat(3, 1fr); gap:28px; margin-top:8px; }
  .why-item .why-num{ font-family:'Anton', sans-serif; font-size:13px; color:var(--spray); }
  .why-item h3{ font-family:'Anton', sans-serif; font-size:19px; letter-spacing:0.3px; margin:8px 0 8px; }
  .why-item p{ color:var(--chalk-dim); font-size:14px; max-width:320px; }
  @media (max-width:760px){ .why-grid{ grid-template-columns:1fr; } }

  /* ---- STOCK ---- */
  .stock-section{ padding:6vh 6vw 12vh; }
  .stock-head{
    display:flex; justify-content:space-between; align-items:flex-end;
    margin-bottom:24px; flex-wrap:wrap; gap:10px;
    border-bottom:1px solid #383734; padding-bottom:18px;
  }
  .stock-head h2{ font-family:'Anton', sans-serif; font-size:34px; letter-spacing:0.5px; }
  .stock-head p{ color:var(--chalk-dim); font-size:14px; }

  .cat-filters{ display:flex; flex-wrap:wrap; gap:9px; margin-bottom:28px; }
  .cat-chip{
    font-family:'Space Grotesk', sans-serif; font-size:13px; font-weight:500;
    background:var(--concrete); color:var(--chalk-dim); border:1px solid #37362f;
    padding:8px 15px; border-radius:20px; cursor:pointer;
  }
  .cat-chip:hover{ color:var(--chalk); }
  .cat-chip.active{ background:var(--spray); color:var(--asphalt); border-color:var(--spray); font-weight:700; }

  .grid{ display:grid; grid-template-columns:repeat(auto-fill, minmax(230px, 1fr)); gap:20px; }
  .empty-state{ color:var(--chalk-dim); font-size:14px; padding:30px 0; }
  .card{
    background:var(--concrete); border:1px solid #37362f;
    display:flex; flex-direction:column; overflow:hidden;
  }
  .thumb{
    position:relative; height:180px; overflow:hidden; cursor:zoom-in;
    display:flex; align-items:center; justify-content:center;
    background:var(--concrete-2);
  }
  .thumb img{ width:100%; height:100%; object-fit:cover; display:block; }
  .thumb .fallback-label{
    font-family:'Anton', sans-serif; font-size:15px; color:rgba(241,239,233,0.65); letter-spacing:1px;
  }
  .thumb .zoom-hint{
    position:absolute; right:8px; bottom:8px;
    background:rgba(25,25,25,0.72); color:var(--chalk);
    font-size:11px; padding:4px 8px; border-radius:20px;
    display:flex; align-items:center; gap:5px;
    opacity:0; transition:opacity 0.15s ease; pointer-events:none;
  }
  .thumb:hover .zoom-hint{ opacity:1; }

  .card-body{ padding:16px 18px 18px; display:flex; flex-direction:column; gap:10px; flex:1;}
  .card-top{ display:flex; justify-content:space-between; align-items:flex-start; gap:8px;}
  .card-name{ font-weight:700; font-size:16px; }
  .card-cat{ color:var(--chalk-dim); font-size:12.5px; margin-top:2px;}
  .badge{ font-size:11.5px; padding:4px 9px; border-radius:20px; white-space:nowrap; font-weight:500; }
  .badge.ok{ background:rgba(127,174,92,0.15); color:var(--ok); }
  .badge.low{ background:rgba(232,73,58,0.15); color:var(--low); }
  .badge.out{ background:rgba(184,181,172,0.15); color:var(--chalk-dim); }
  .price{ font-family:'Anton', sans-serif; font-size:20px; color:var(--deck-tan); margin-top:auto;}
  .wa-btn{
    display:flex; align-items:center; justify-content:center; gap:8px;
    text-decoration:none; background:var(--spray); color:var(--asphalt);
    font-weight:700; font-size:14px; padding:11px 0; border-radius:2px;
    transition:opacity 0.15s ease;
  }
  .wa-btn:hover{ opacity:0.85; }
  .wa-btn.disabled{ background:#3a3934; color:var(--chalk-dim); pointer-events:none; }

  footer{
    padding:5vh 6vw 6vh; border-top:1px solid #383734;
    display:flex; justify-content:space-between; flex-wrap:wrap; gap:14px;
    color:var(--chalk-dim); font-size:13px;
  }

  @media (max-width:640px){
    .hero{ padding-top:10vh; }
    .stock-head{ flex-direction:column; align-items:flex-start; }
  }

  /* ---- LIGHTBOX ---- */
  .lightbox{
    position:fixed; inset:0; background:rgba(10,10,10,0.92);
    display:none; align-items:center; justify-content:center;
    z-index:200; flex-direction:column;
  }
  .lightbox.open{ display:flex; }
  .lightbox-frame{
    position:relative; width:min(88vw, 640px); height:min(70vh, 640px);
    overflow:hidden; border:1px solid #383734; background:var(--concrete-2);
    display:flex; align-items:center; justify-content:center;
    touch-action:none;
  }
  .lightbox-frame img{
    width:100%; height:100%; object-fit:contain;
    transform:scale(1); transform-origin:50% 50%;
    transition:transform 0.06s ease-out;
    cursor:zoom-in; user-select:none; -webkit-user-drag:none;
  }
  .lightbox-frame img.zoomed{ cursor:grab; }
  .lightbox-frame img.dragging{ cursor:grabbing; transition:none; }
  .lightbox-caption{
    margin-top:16px; text-align:center; color:var(--chalk-dim); font-size:13px; max-width:80vw;
  }
  .lightbox-caption strong{ color:var(--chalk); display:block; font-size:15px; margin-bottom:2px; }
  .lightbox-close{
    position:absolute; top:22px; right:22px;
    background:none; border:1px solid #4a4844; color:var(--chalk);
    width:36px; height:36px; border-radius:50%; font-size:18px; cursor:pointer;
    display:flex; align-items:center; justify-content:center;
  }
  .lightbox-close:hover{ border-color:var(--chalk); }
  .lightbox-zoomlevel{
    position:absolute; left:14px; bottom:14px;
    background:rgba(25,25,25,0.75); color:var(--chalk-dim);
    font-size:11px; padding:4px 9px; border-radius:20px;
  }

  /* ---- ADMIN (hidden route) ---- */
  #admin-view{ display:none; min-height:100vh; padding:6vh 5vw; }
  .admin-shell{ max-width:1040px; margin:0 auto; }
  .admin-head{ display:flex; justify-content:space-between; align-items:center; margin-bottom:28px; flex-wrap:wrap; gap:10px;}
  .admin-head h2{ font-family:'Anton', sans-serif; font-size:26px; letter-spacing:0.5px; }
  .back-link{ font-size:13px; color:var(--chalk-dim); text-decoration:none; border-bottom:1px solid #4a4844; }

  .login-box{
    max-width:340px; margin:14vh auto; text-align:center;
    background:var(--concrete); border:1px solid #37362f; padding:36px 28px;
  }
  .login-box h3{ font-family:'Anton', sans-serif; font-size:20px; margin-bottom:6px;}
  .login-box p{ color:var(--chalk-dim); font-size:13px; margin-bottom:20px;}
  .login-box input{
    width:100%; padding:11px 12px; background:var(--asphalt); border:1px solid #3a3934;
    color:var(--chalk); font-size:15px; margin-bottom:12px; letter-spacing:2px; text-align:center;
  }
  .login-box button, .save-btn, .add-btn{
    width:100%; padding:11px 0; background:var(--spray); color:var(--asphalt);
    border:none; font-weight:700; font-size:14px; cursor:pointer; border-radius:2px;
  }
  .login-err{ color:var(--low); font-size:12.5px; margin-top:10px; min-height:14px; }

  table{ width:100%; border-collapse:collapse; font-size:13.5px; }
  th{ text-align:left; color:var(--chalk-dim); font-weight:500; font-size:12px; padding:8px 10px; border-bottom:1px solid #383734; }
  td{ padding:8px 10px; border-bottom:1px solid #2c2b28; vertical-align:middle; }
  td input{
    background:var(--concrete); border:1px solid #3a3934; color:var(--chalk);
    padding:7px 8px; font-size:13.5px; width:100%; font-family:inherit;
  }
  td input.narrow{ width:75px; }
  td input.wide{ min-width:170px; }
  .thumb-preview{
    width:44px; height:44px; border-radius:4px; object-fit:cover;
    background:var(--concrete-2); display:block; border:1px solid #3a3934;
  }
  .del-btn{
    background:none; border:1px solid #4a3530; color:var(--low);
    padding:6px 10px; font-size:12px; cursor:pointer; border-radius:2px;
  }
  .del-btn:hover{ background:rgba(232,73,58,0.1); }
  .admin-actions{ display:flex; gap:12px; margin-top:22px; flex-wrap:wrap; }
  .admin-actions .save-btn{ width:auto; padding:11px 24px; }
  .admin-actions .add-btn{ width:auto; padding:11px 24px; background:var(--concrete-2); color:var(--chalk); border:1px solid #3a3934; }
  .save-msg{ font-size:12.5px; color:var(--ok); margin-top:10px; min-height:14px; }
  .table-wrap{ overflow-x:auto; }
</style>
</head>
<body>

<!-- ============ STORE VIEW ============ -->
<div id="store-view">
  <nav>
    <div class="logo">ZENN<span>SK8</span></div>
    <a class="contact-link" href="#stock">Lihat stok</a>
  </nav>

  <section class="hero">
    <div class="stripe"></div>
    <div class="eyebrow"><span class="dot"></span> Local skate shop · Balikpapan</div>
    <h1>
      <span class="out">RIDE</span>
      <span class="fill">OR ROT</span>
    </h1>
    <p>ZennSk8 — deck, truck, wheel, dan alat skate lain buat anak-anak lokal yang niat main. Stok asli, harga jelas, tinggal chat WA buat order.</p>
    <a class="cta" href="#stock">Cek Stok Barang ↓</a>
  </section>

  <div class="marquee">
    <div class="marquee-track">
      <span>GRIP IT &amp; RIP IT</span><span>·</span>
      <span>NO SKATE NO LIFE</span><span>·</span>
      <span>LOKAL CREW BALIKPAPAN</span><span>·</span>
      <span>STOK ASLI, HARGA JUJUR</span><span>·</span>
      <span>GRIP IT &amp; RIP IT</span><span>·</span>
      <span>NO SKATE NO LIFE</span><span>·</span>
      <span>LOKAL CREW BALIKPAPAN</span><span>·</span>
      <span>STOK ASLI, HARGA JUJUR</span><span>·</span>
    </div>
  </div>

  <section class="why-section">
    <div class="why-grid">
      <div class="why-item">
        <div class="why-num">01</div>
        <h3>Barang Ori</h3>
        <p>Semua part dan deck yang kami jual asli, bukan KW — dicek dulu sebelum masuk stok.</p>
      </div>
      <div class="why-item">
        <div class="why-num">02</div>
        <h3>Fast Response WA</h3>
        <p>Tanya stok, nego, sampai order tinggal chat — nggak perlu bikin akun atau ribet checkout.</p>
      </div>
      <div class="why-item">
        <div class="why-num">03</div>
        <h3>Dari &amp; Buat Skater Lokal</h3>
        <p>Dijalanin sama yang emang main skate juga, ngerti part apa yang cocok buat gaya main kamu.</p>
      </div>
    </div>
  </section>

  <section class="stock-section" id="stock">
    <div class="stock-head">
      <h2>Stok Barang</h2>
      <p>Klik foto buat lihat &amp; zoom · klik "Order via WA" buat pesan</p>
    </div>
    <div class="cat-filters" id="cat-filters"></div>
    <div class="grid" id="product-grid"></div>
  </section>

  <footer>
    <div>© 2026 ZennSk8. Balikpapan, Indonesia.</div>
    <div>Order &amp; tanya-tanya lewat WhatsApp</div>
  </footer>
</div>

<!-- ============ LIGHTBOX (preview + zoom foto) ============ -->
<div class="lightbox" id="lightbox">
  <div class="lightbox-frame" id="lightbox-frame">
    <button class="lightbox-close" onclick="closeLightbox()">✕</button>
    <span class="lightbox-zoomlevel" id="lightbox-zoomlevel">1.0×</span>
    <img id="lightbox-img" src="" alt="">
  </div>
  <div class="lightbox-caption">
    <strong id="lightbox-name"></strong>
    <span>Klik foto buat zoom · scroll buat perbesar/perkecil · geser saat di-zoom</span>
  </div>
</div>

<!-- ============ ADMIN VIEW (hidden route: buka #admin) ============ -->
<div id="admin-view">
  <div class="admin-shell">

    <div id="login-box" class="login-box">
      <h3>ZENNSK8 · DASHBOARD</h3>
      <p>Masukkan kode admin</p>
      <input type="password" id="admin-code" placeholder="••••••" maxlength="20">
      <button onclick="tryLogin()">Masuk</button>
      <div class="login-err" id="login-err"></div>
    </div>

    <div id="dashboard-box" style="display:none;">
      <div class="admin-head">
        <h2>Kelola Stok Barang</h2>
        <a class="back-link" href="#">← Kembali ke toko</a>
      </div>

      <div class="table-wrap">
        <table>
          <thead>
            <tr>
              <th>Foto</th>
              <th>URL Foto</th>
              <th>Nama Barang</th>
              <th>Kategori</th>
              <th>Harga (Rp)</th>
              <th>Stok</th>
              <th></th>
            </tr>
          </thead>
          <tbody id="admin-table-body"></tbody>
        </table>
      </div>

      <div class="admin-actions">
        <button class="add-btn" onclick="addProduct()">+ Tambah Barang</button>
        <button class="save-btn" onclick="saveProducts()">Simpan Perubahan</button>
      </div>
      <div class="save-msg" id="save-msg"></div>
    </div>

  </div>
</div>

<script>
  // GANTI nomor ini dengan nomor WhatsApp toko kamu (format: 62xxxxxxxxxxx, tanpa + atau 0 di depan)
  const WA_NUMBER = "6281234567890";

  // GANTI kode ini dengan kode rahasia kamu sendiri untuk masuk dashboard
  const ADMIN_CODE = "zenn8125";

  const STORAGE_KEY = "zennsk8:products";

  // Foto di bawah ini pakai layanan foto dummy (Picsum) supaya kelihatan seperti foto asli.
  // Ganti field "image" tiap barang lewat dashboard (#admin) dengan foto produk aslinya nanti.
  const DEFAULT_PRODUCTS = [
    { name: "Deck ZennSk8 8.0\"", cat: "Deck", price: 450000, stock: 6, swatch: "#3a2a1f", image: "https://picsum.photos/seed/zennsk8-deck/600/600" },
    { name: "Trucks Independent 139", cat: "Trucks", price: 380000, stock: 3, swatch: "#4a4a4a", image: "https://picsum.photos/seed/zennsk8-trucks/600/600" },
    { name: "Wheels 52mm 99A", cat: "Wheels", price: 220000, stock: 12, swatch: "#c9a66b", image: "https://picsum.photos/seed/zennsk8-wheels/600/600" },
    { name: "Bearings ABEC 7", cat: "Bearings", price: 95000, stock: 20, swatch: "#5c5c5c", image: "https://picsum.photos/seed/zennsk8-bearings/600/600" },
    { name: "Grip Tape Jessup", cat: "Grip Tape", price: 65000, stock: 0, swatch: "#1c1c1c", image: "https://picsum.photos/seed/zennsk8-griptape/600/600" },
    { name: "Sepatu Skate Vans Style", cat: "Sepatu", price: 520000, stock: 4, swatch: "#7a1f1f", image: "https://picsum.photos/seed/zennsk8-shoes/600/600" },
    { name: "Riser Pad Set", cat: "Aksesoris", price: 35000, stock: 25, swatch: "#3a5a40", image: "https://picsum.photos/seed/zennsk8-riser/600/600" },
    { name: "Skate Tool All-in-One", cat: "Aksesoris", price: 75000, stock: 8, swatch: "#8a5a2a", image: "https://picsum.photos/seed/zennsk8-tool/600/600" },
  ];

  let products = [];
  let authenticated = false;
  let activeCategory = "Semua";

  function formatRupiah(n){ return "Rp" + Number(n || 0).toLocaleString("id-ID"); }

  function stockBadge(stock){
    if(stock === 0) return { text: "Habis", cls: "out" };
    if(stock <= 4) return { text: `Sisa ${stock}`, cls: "low" };
    return { text: `Stok ${stock}`, cls: "ok" };
  }

  async function loadProducts(){
    try{
      const res = await window.storage.get(STORAGE_KEY, true);
      products = res && res.value ? JSON.parse(res.value) : DEFAULT_PRODUCTS;
    }catch(err){
      products = DEFAULT_PRODUCTS;
    }
  }

  async function persistProducts(){
    try{
      await window.storage.set(STORAGE_KEY, JSON.stringify(products), true);
      return true;
    }catch(err){
      return false;
    }
  }

  function renderCatFilters(){
    const wrap = document.getElementById("cat-filters");
    const cats = ["Semua", ...new Set(products.map(p => p.cat))];
    wrap.innerHTML = "";
    cats.forEach(cat => {
      const chip = document.createElement("button");
      chip.className = "cat-chip" + (cat === activeCategory ? " active" : "");
      chip.textContent = cat;
      chip.onclick = () => { activeCategory = cat; renderStore(); };
      wrap.appendChild(chip);
    });
  }

  function renderStore(){
    renderCatFilters();
    const grid = document.getElementById("product-grid");
    grid.innerHTML = "";
    const visible = products
      .map((p, i) => ({ p, i }))
      .filter(({ p }) => activeCategory === "Semua" || p.cat === activeCategory);

    if(visible.length === 0){
      grid.innerHTML = `<div class="empty-state">Belum ada barang di kategori ini.</div>`;
      return;
    }

    visible.forEach(({ p, i }) => {
      const badge = stockBadge(p.stock);
      const msg = encodeURIComponent(`Halo ZennSk8, saya mau order: ${p.name}`);
      const waLink = `https://wa.me/${WA_NUMBER}?text=${msg}`;
      const thumbInner = p.image
        ? `<img src="${p.image}" alt="${p.name}" loading="lazy">`
        : `<span class="fallback-label" style="background:${p.swatch || '#3a3934'}">${p.cat}</span>`;

      const card = document.createElement("div");
      card.className = "card";
      card.innerHTML = `
        <div class="thumb" style="background:${p.swatch || '#3a3934'}" onclick="openLightbox(${i})">
          ${thumbInner}
          <span class="zoom-hint">🔍 Lihat &amp; zoom</span>
        </div>
        <div class="card-body">
          <div class="card-top">
            <div>
              <div class="card-name">${p.name}</div>
              <div class="card-cat">${p.cat}</div>
            </div>
            <span class="badge ${badge.cls}">${badge.text}</span>
          </div>
          <div class="price">${formatRupiah(p.price)}</div>
          <a class="wa-btn ${p.stock === 0 ? "disabled" : ""}" href="${p.stock === 0 ? "#" : waLink}" target="_blank" rel="noopener">
            ${p.stock === 0 ? "Stok Habis" : "Order via WA"}
          </a>
        </div>
      `;
      grid.appendChild(card);
    });
  }

  /* ---------- LIGHTBOX: preview + zoom ---------- */
  let lbScale = 1;
  let lbOriginX = 50, lbOriginY = 50;
  let lbPanX = 0, lbPanY = 0;
  let lbDragging = false, lbLastX = 0, lbLastY = 0;

  function openLightbox(index){
    const p = products[index];
    const img = document.getElementById("lightbox-img");
    img.src = p.image || "https://placehold.co/500x500/262625/b8b5ac?text=Belum+ada+foto";
    document.getElementById("lightbox-name").textContent = p.name;
    resetZoom();
    document.getElementById("lightbox").classList.add("open");
  }

  function closeLightbox(){
    document.getElementById("lightbox").classList.remove("open");
  }

  function resetZoom(){
    lbScale = 1; lbPanX = 0; lbPanY = 0; lbOriginX = 50; lbOriginY = 50;
    applyZoom();
  }

  function applyZoom(){
    const img = document.getElementById("lightbox-img");
    img.style.transformOrigin = `${lbOriginX}% ${lbOriginY}%`;
    img.style.transform = `scale(${lbScale}) translate(${lbPanX}px, ${lbPanY}px)`;
    img.classList.toggle("zoomed", lbScale > 1);
    document.getElementById("lightbox-zoomlevel").textContent = lbScale.toFixed(1) + "×";
  }

  function clamp(v, min, max){ return Math.max(min, Math.min(max, v)); }

  document.getElementById("lightbox-img").addEventListener("click", function(e){
    if(lbDragging) return;
    const rect = this.getBoundingClientRect();
    lbOriginX = ((e.clientX - rect.left) / rect.width) * 100;
    lbOriginY = ((e.clientY - rect.top) / rect.height) * 100;
    lbPanX = 0; lbPanY = 0;
    lbScale = lbScale > 1 ? 1 : 2.4;
    applyZoom();
  });

  document.getElementById("lightbox-frame").addEventListener("wheel", function(e){
    e.preventDefault();
    const img = document.getElementById("lightbox-img");
    const rect = img.getBoundingClientRect();
    lbOriginX = clamp(((e.clientX - rect.left) / rect.width) * 100, 0, 100);
    lbOriginY = clamp(((e.clientY - rect.top) / rect.height) * 100, 0, 100);
    lbScale = clamp(lbScale + (e.deltaY < 0 ? 0.3 : -0.3), 1, 3.5);
    if(lbScale === 1){ lbPanX = 0; lbPanY = 0; }
    applyZoom();
  }, { passive:false });

  const lbImgEl = document.getElementById("lightbox-img");
  lbImgEl.addEventListener("pointerdown", function(e){
    if(lbScale <= 1) return;
    lbDragging = true;
    lbLastX = e.clientX; lbLastY = e.clientY;
    this.classList.add("dragging");
    this.setPointerCapture(e.pointerId);
  });
  lbImgEl.addEventListener("pointermove", function(e){
    if(!lbDragging) return;
    lbPanX += (e.clientX - lbLastX) / lbScale;
    lbPanY += (e.clientY - lbLastY) / lbScale;
    lbLastX = e.clientX; lbLastY = e.clientY;
    applyZoom();
  });
  ["pointerup","pointercancel","pointerleave"].forEach(evt=>{
    lbImgEl.addEventListener(evt, function(){
      lbDragging = false;
      this.classList.remove("dragging");
    });
  });
  lbImgEl.addEventListener("dblclick", resetZoom);

  document.getElementById("lightbox").addEventListener("click", function(e){
    if(e.target === this) closeLightbox();
  });
  document.addEventListener("keydown", function(e){
    if(e.key === "Escape") closeLightbox();
  });

  /* ---------- ADMIN ---------- */
  function renderAdminTable(){
    const body = document.getElementById("admin-table-body");
    body.innerHTML = "";
    products.forEach((p, i) => {
      const tr = document.createElement("tr");
      tr.innerHTML = `
        <td><img class="thumb-preview" id="thumb-prev-${i}" src="${p.image || 'https://placehold.co/80x80/262625/b8b5ac?text=-'}" alt=""></td>
        <td><input class="wide" value="${p.image || ''}" placeholder="https://..." oninput="updateField(${i},'image',this.value); document.getElementById('thumb-prev-${i}').src = this.value || 'https://placehold.co/80x80/262625/b8b5ac?text=-';"></td>
        <td><input value="${p.name}" oninput="updateField(${i},'name',this.value)"></td>
        <td><input value="${p.cat}" oninput="updateField(${i},'cat',this.value)"></td>
        <td><input class="narrow" type="number" value="${p.price}" oninput="updateField(${i},'price',this.value)"></td>
        <td><input class="narrow" type="number" value="${p.stock}" oninput="updateField(${i},'stock',this.value)"></td>
        <td><button class="del-btn" onclick="deleteProduct(${i})">Hapus</button></td>
      `;
      body.appendChild(tr);
    });
  }

  function updateField(index, field, value){
    if(field === "price" || field === "stock"){
      products[index][field] = Number(value) || 0;
    }else{
      products[index][field] = value;
    }
  }

  function addProduct(){
    products.push({ name: "Barang Baru", cat: "Kategori", price: 0, stock: 0, swatch: "#3a3934", image: "" });
    renderAdminTable();
  }

  function deleteProduct(index){
    products.splice(index, 1);
    renderAdminTable();
  }

  async function saveProducts(){
    const ok = await persistProducts();
    const msg = document.getElementById("save-msg");
    msg.textContent = ok ? "Tersimpan. Perubahan langsung tampil di toko." : "Gagal menyimpan, coba lagi.";
    msg.style.color = ok ? "var(--ok)" : "var(--low)";
    if(ok) renderStore();
  }

  function tryLogin(){
    const input = document.getElementById("admin-code").value;
    const err = document.getElementById("login-err");
    if(input === ADMIN_CODE){
      authenticated = true;
      document.getElementById("login-box").style.display = "none";
      document.getElementById("dashboard-box").style.display = "block";
      renderAdminTable();
    }else{
      err.textContent = "Kode salah.";
    }
  }

  function checkRoute(){
    const isAdmin = location.hash === "#admin";
    document.getElementById("store-view").style.display = isAdmin ? "none" : "block";
    document.getElementById("admin-view").style.display = isAdmin ? "block" : "none";
    if(isAdmin && authenticated){
      document.getElementById("login-box").style.display = "none";
      document.getElementById("dashboard-box").style.display = "block";
      renderAdminTable();
    }else if(isAdmin){
      document.getElementById("login-box").style.display = "block";
      document.getElementById("dashboard-box").style.display = "none";
    }
  }

  window.addEventListener("hashchange", checkRoute);

  document.getElementById("admin-code").addEventListener("keydown", (e) => {
    if(e.key === "Enter") tryLogin();
  });

  (async function init(){
    await loadProducts();
    renderStore();
    checkRoute();
  })();
</script>

</body>
</html>
