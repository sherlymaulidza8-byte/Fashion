
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>AURIC</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --cream: #FAF8F5;
      --dark: #1A1A1A;
      --gold: #C9A84C;
      --gold-light: #E8D5A3;
      --muted: #6B6B6B;
      --border: #E8E4DF;
      --white: #FFFFFF;
      --success: #2D7A4F;
      --danger: #C0392B;
      --card-bg: #FFFFFF;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: var(--cream);
      color: var(--dark);
      min-height: 100vh;
    }

    /* ── NAVBAR ── */
    nav {
      position: sticky; top: 0; z-index: 100;
      background: var(--white);
      border-bottom: 1px solid var(--border);
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 32px; height: 64px;
      box-shadow: 0 1px 8px rgba(0,0,0,0.05);
    }
    .nav-brand {
      font-family: 'Playfair Display', serif;
      font-size: 1.5rem; font-weight: 700;
      color: var(--dark); letter-spacing: 0.04em;
      text-decoration: none;
    }
    .nav-brand span { color: var(--gold); }
    .nav-links { display: flex; gap: 28px; align-items: center; }
    .nav-links a {
      text-decoration: none; font-size: 0.875rem; font-weight: 500;
      color: var(--muted); letter-spacing: 0.02em;
      transition: color .2s;
    }
    .nav-links a:hover, .nav-links a.active { color: var(--dark); }
    .nav-actions { display: flex; gap: 12px; align-items: center; }
    .btn-cart {
      position: relative;
      background: var(--dark); color: var(--white);
      border: none; border-radius: 6px; padding: 8px 16px;
      font-size: 0.8rem; font-weight: 600; cursor: pointer;
      display: flex; align-items: center; gap: 6px;
      transition: background .2s;
    }
    .btn-cart:hover { background: rgb(59, 59, 59)121; }
    .cart-badge {
      position: absolute; top: -6px; right: -6px;
      background: var(--gold); color: var(--white);
      border-radius: 50%; width: 18px; height: 18px;
      font-size: 0.65rem; font-weight: 700;
      display: flex; align-items: center; justify-content: center;
    }
    .btn-history {
      background: transparent; color: var(--dark);
      border: 1.5px solid var(--border); border-radius: 6px;
      padding: 8px 14px; font-size: 0.8rem; font-weight: 500;
      cursor: pointer; transition: all .2s;
    }
    .btn-history:hover { border-color: var(--gold); color: var(--gold); }

    /* ── HERO ── */
    .hero {
      background: linear-gradient(135deg, #1A1A1A 0%, #2C2C2C 60%, #3A3020 100%);
      padding: 80px 32px;
      display: flex; align-items: center; justify-content: space-between;
      gap: 40px; overflow: hidden; position: relative;
    }
    .hero::after {
      content: '';
      position: absolute; right: 0; top: 0; bottom: 0; width: 45%;
      background: url('https://plus.unsplash.com/premium_photo-1664202526559-e21e9c0fb46a?q=80&w=870&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D') center/cover;
      opacity: 0.18;
    }
    .hero-content { z-index: 1; max-width: 520px; }
    .hero-eyebrow {
      font-size: 0.75rem; font-weight: 600; letter-spacing: 0.15em;
      color: var(--gold); text-transform: uppercase; margin-bottom: 16px;
    }
    .hero-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 4vw, 3.2rem); font-weight: 700;
      color: var(--white); line-height: 1.15; margin-bottom: 20px;
    }
    .hero-title em { font-style: normal; color: var(--gold); }
    .hero-sub {
      font-size: 0.95rem; color: #B0A898; line-height: 1.7; margin-bottom: 32px;
    }
    .hero-cta { display: flex; gap: 12px; }
    .btn-primary {
      background: var(--gold); color: var(--white);
      border: none; border-radius: 6px; padding: 13px 28px;
      font-size: 0.875rem; font-weight: 600; cursor: pointer;
      letter-spacing: 0.02em; transition: all .2s;
    }
    .btn-primary:hover { background: #B8922E; transform: translateY(-1px); }
    .btn-outline-white {
      background: transparent; color: var(--white);
      border: 1.5px solid rgba(255,255,255,0.3); border-radius: 6px;
      padding: 13px 28px; font-size: 0.875rem; font-weight: 500;
      cursor: pointer; transition: all .2s;
    }
    .btn-outline-white:hover { border-color: var(--gold); color: var(--gold); }

    /* ── SECTION LAYOUT ── */
    .section { padding: 56px 32px; }
    .section-header {
      display: flex; align-items: flex-end; justify-content: space-between;
      margin-bottom: 32px; padding-bottom: 16px; border-bottom: 1px solid var(--border);
    }
    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.6rem; font-weight: 600; color: var(--dark);
    }
    .section-subtitle { font-size: 0.8rem; color: var(--muted); margin-top: 4px; }
    .view-all {
      font-size: 0.8rem; color: var(--gold); font-weight: 600;
      letter-spacing: 0.05em; cursor: pointer; text-decoration: none;
      border-bottom: 1px solid transparent; transition: border-color .2s;
    }
    .view-all:hover { border-color: var(--gold); }

    /* ── PRODUCT GRID ── */
    .product-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
      gap: 24px;
    }
    .product-card {
      background: var(--white); border-radius: 10px;
      overflow: hidden; transition: transform .25s, box-shadow .25s;
      border: 1px solid var(--border);
    }
    .product-card:hover { transform: translateY(-4px); box-shadow: 0 12px 30px rgba(0,0,0,0.10); }
    .product-img {
      width: 100%; aspect-ratio: 3/4; object-fit: cover;
      background: #F0ECE8; display: block;
    }
    .product-img-placeholder {
      width: 100%; aspect-ratio: 3/4;
      display: flex; align-items: center; justify-content: center;
      font-size: 3rem; background: linear-gradient(135deg, #F5F0EA, #EDE8E0);
    }
    .product-info { padding: 16px; }
    .product-badge {
      display: inline-block; font-size: 0.65rem; font-weight: 700;
      letter-spacing: 0.08em; text-transform: uppercase;
      background: var(--gold-light); color: #7A5C00;
      border-radius: 4px; padding: 2px 8px; margin-bottom: 8px;
    }
    .product-name {
      font-size: 0.9rem; font-weight: 600; margin-bottom: 4px;
      color: var(--dark); line-height: 1.3;
    }
    .product-price {
      font-size: 1rem; font-weight: 700; color: var(--gold);
      margin-bottom: 14px;
    }
    .product-price .original {
      font-size: 0.78rem; font-weight: 400;
      color: var(--muted); text-decoration: line-through; margin-left: 6px;
    }
    .btn-add-cart {
      width: 100%; background: var(--dark); color: var(--white);
      border: none; border-radius: 6px; padding: 10px;
      font-size: 0.82rem; font-weight: 600; cursor: pointer;
      transition: background .2s; letter-spacing: 0.03em;
    }
    .btn-add-cart:hover { background: var(--gold); }

    /* ── MODAL BASE ── */
    .modal-overlay {
      position: fixed; inset: 0; background: rgba(0,0,0,0.5);
      z-index: 200; display: none; align-items: center; justify-content: center;
      padding: 20px;
    }
    .modal-overlay.open { display: flex; }
    .modal {
      background: var(--white); border-radius: 12px;
      width: 100%; max-width: 520px; max-height: 90vh;
      overflow-y: auto; position: relative;
    }
    .modal-header {
      padding: 24px 24px 0;
      display: flex; align-items: center; justify-content: space-between;
      border-bottom: 1px solid var(--border); padding-bottom: 16px;
      position: sticky; top: 0; background: var(--white); z-index: 1;
    }
    .modal-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.2rem; font-weight: 600;
    }
    .modal-close {
      background: none; border: none; font-size: 1.4rem;
      cursor: pointer; color: var(--muted); line-height: 1;
      padding: 4px; transition: color .2s;
    }
    .modal-close:hover { color: var(--dark); }
    .modal-body { padding: 20px 24px 24px; }

    /* ── CART MODAL ── */
    .cart-item {
      display: flex; align-items: center; gap: 14px;
      padding: 14px 0; border-bottom: 1px solid var(--border);
    }
    .cart-item-img {
      width: 60px; height: 60px; object-fit: cover;
      border-radius: 6px; background: #F0ECE8;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.6rem; flex-shrink: 0;
    }
    .cart-item-info { flex: 1; }
    .cart-item-name { font-size: 0.87rem; font-weight: 600; margin-bottom: 2px; }
    .cart-item-price { font-size: 0.8rem; color: var(--gold); font-weight: 600; }
    .cart-qty { display: flex; align-items: center; gap: 8px; margin-top: 8px; }
    .qty-btn {
      width: 26px; height: 26px; border-radius: 4px;
      border: 1.5px solid var(--border); background: var(--white);
      cursor: pointer; font-size: 0.9rem; font-weight: 700;
      display: flex; align-items: center; justify-content: center;
      transition: all .2s;
    }
    .qty-btn:hover { border-color: var(--gold); color: var(--gold); }
    .qty-num { font-size: 0.85rem; font-weight: 600; min-width: 20px; text-align: center; }
    .cart-item-remove {
      background: none; border: none; color: #C0392B;
      cursor: pointer; font-size: 0.75rem; font-weight: 500;
      padding: 0; transition: opacity .2s;
    }
    .cart-item-remove:hover { opacity: 0.7; }
    .cart-empty {
      text-align: center; padding: 40px 0; color: var(--muted);
    }
    .cart-empty-icon { font-size: 3rem; margin-bottom: 12px; }
    .cart-summary {
      margin-top: 20px; padding-top: 16px;
      border-top: 2px solid var(--dark);
    }
    .summary-row {
      display: flex; justify-content: space-between;
      font-size: 0.85rem; margin-bottom: 6px;
    }
    .summary-row.total {
      font-weight: 700; font-size: 1rem; margin-top: 10px;
      padding-top: 10px; border-top: 1px solid var(--border);
    }
    .btn-checkout {
      width: 100%; margin-top: 16px;
      background: var(--gold); color: var(--white);
      border: none; border-radius: 8px; padding: 14px;
      font-size: 0.9rem; font-weight: 700; cursor: pointer;
      transition: background .2s; letter-spacing: 0.03em;
    }
    .btn-checkout:hover { background: #B8922E; }

    /* ── CHECKOUT MODAL ── */
    .form-group { margin-bottom: 16px; }
    .form-label {
      display: block; font-size: 0.78rem; font-weight: 600;
      color: var(--dark); margin-bottom: 6px; letter-spacing: 0.03em;
    }
    .form-input, .form-select {
      width: 100%; padding: 10px 14px; border: 1.5px solid var(--border);
      border-radius: 6px; font-size: 0.875rem; font-family: inherit;
      background: var(--white); color: var(--dark);
      transition: border-color .2s; outline: none;
    }
    .form-input:focus, .form-select:focus { border-color: var(--gold); }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
    .payment-options { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 6px; }
    .payment-opt {
      border: 1.5px solid var(--border); border-radius: 6px;
      padding: 10px 12px; cursor: pointer; transition: all .2s;
      display: flex; align-items: center; gap: 8px;
      font-size: 0.82rem; font-weight: 500;
    }
    .payment-opt.selected { border-color: var(--gold); background: #FFF9F0; color: #7A5C00; }
    .payment-opt:hover { border-color: var(--gold-light); }
    .section-divider {
      font-size: 0.7rem; font-weight: 700; letter-spacing: 0.1em;
      text-transform: uppercase; color: var(--muted);
      margin: 20px 0 12px; display: flex; align-items: center; gap: 8px;
    }
    .section-divider::after {
      content: ''; flex: 1; height: 1px; background: var(--border);
    }

    /* ── ORDER SUCCESS MODAL ── */
    .success-modal { text-align: center; }
    .success-icon {
      width: 72px; height: 72px; background: #E8F5EF;
      border-radius: 50%; display: flex; align-items: center; justify-content: center;
      margin: 0 auto 20px; font-size: 2rem;
    }
    .success-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.5rem; font-weight: 600; margin-bottom: 8px;
    }
    .success-sub { color: var(--muted); font-size: 0.875rem; line-height: 1.6; margin-bottom: 24px; }
    .order-code {
      background: var(--cream); border: 1px solid var(--border);
      border-radius: 8px; padding: 16px; margin-bottom: 20px;
      text-align: left;
    }
    .order-code-label { font-size: 0.7rem; font-weight: 700; color: var(--muted); letter-spacing: 0.1em; margin-bottom: 4px; }
    .order-code-value { font-size: 1rem; font-weight: 700; color: var(--dark); letter-spacing: 0.05em; }
    .order-items-preview { text-align: left; margin-bottom: 20px; }
    .order-item-row {
      display: flex; justify-content: space-between; align-items: center;
      font-size: 0.82rem; padding: 6px 0; border-bottom: 1px solid var(--border);
    }
    .order-item-row:last-child { border-bottom: none; }
    .order-total-row {
      display: flex; justify-content: space-between;
      font-size: 0.9rem; font-weight: 700; padding-top: 10px;
    }
    .success-actions { display: flex; gap: 10px; }
    .btn-secondary {
      flex: 1; background: var(--white); color: var(--dark);
      border: 1.5px solid var(--border); border-radius: 8px;
      padding: 12px; font-size: 0.85rem; font-weight: 600;
      cursor: pointer; transition: all .2s;
    }
    .btn-secondary:hover { border-color: var(--dark); }

    /* ── HISTORY MODAL ── */
    .history-filters {
      display: flex; gap: 8px; margin-bottom: 20px; flex-wrap: wrap;
    }
    .filter-chip {
      padding: 6px 14px; border-radius: 20px; border: 1.5px solid var(--border);
      font-size: 0.78rem; font-weight: 500; cursor: pointer; transition: all .2s;
      background: var(--white);
    }
    .filter-chip.active { background: var(--dark); color: var(--white); border-color: var(--dark); }
    .history-empty {
      text-align: center; padding: 40px 0; color: var(--muted);
    }
    .history-card {
      border: 1px solid var(--border); border-radius: 8px;
      margin-bottom: 14px; overflow: hidden;
    }
    .history-card-header {
      background: var(--cream); padding: 12px 16px;
      display: flex; align-items: center; justify-content: space-between;
    }
    .history-order-id { font-size: 0.75rem; font-weight: 700; color: var(--muted); }
    .history-date { font-size: 0.75rem; color: var(--muted); }
    .history-status {
      font-size: 0.7rem; font-weight: 700; letter-spacing: 0.05em;
      text-transform: uppercase; padding: 3px 10px; border-radius: 20px;
    }
    .status-selesai { background: #E8F5EF; color: var(--success); }
    .status-diproses { background: #FFF3E0; color: #E65100; }
    .status-dikirim { background: #E3F2FD; color: #1565C0; }
    .history-card-body { padding: 14px 16px; }
    .history-items { margin-bottom: 12px; }
    .history-item {
      display: flex; justify-content: space-between;
      font-size: 0.82rem; padding: 4px 0;
      border-bottom: 1px dashed var(--border);
    }
    .history-item:last-child { border-bottom: none; }
    .history-item-name { color: var(--dark); }
    .history-item-sub { font-size: 0.75rem; color: var(--muted); }
    .history-footer {
      display: flex; align-items: center; justify-content: space-between;
      margin-top: 12px; padding-top: 10px; border-top: 1px solid var(--border);
    }
    .history-total { font-size: 0.9rem; font-weight: 700; color: var(--dark); }
    .btn-reorder {
      background: var(--gold-light); color: #7A5C00;
      border: none; border-radius: 6px; padding: 7px 14px;
      font-size: 0.78rem; font-weight: 600; cursor: pointer;
      transition: background .2s;
    }
    .btn-reorder:hover { background: #DFC87E; }

    /* ── BANNER / PROMO ── */
    .promo-banner {
      background: linear-gradient(90deg, var(--dark) 0%, #2C2C2C 100%);
      color: var(--white); text-align: center;
      padding: 14px 32px; font-size: 0.82rem;
      display: flex; align-items: center; justify-content: center; gap: 12px;
    }
    .promo-banner strong { color: var(--gold); }

    /* ── TOAST ── */
    .toast {
      position: fixed; bottom: 24px; right: 24px; z-index: 999;
      background: var(--dark); color: var(--white);
      border-radius: 8px; padding: 14px 20px;
      font-size: 0.85rem; font-weight: 500;
      display: flex; align-items: center; gap: 10px;
      transform: translateY(80px); opacity: 0;
      transition: all .3s ease; pointer-events: none;
      max-width: 300px; box-shadow: 0 8px 24px rgba(0,0,0,0.2);
    }
    .toast.show { transform: translateY(0); opacity: 1; }
    .toast-icon { font-size: 1rem; }

    /* ── KATEGORI TABS ── */
    .category-tabs {
      display: flex; gap: 0; border-bottom: 2px solid var(--border);
      margin-bottom: 28px;
    }
    .category-tab {
      padding: 10px 24px; font-size: 0.85rem; font-weight: 500;
      cursor: pointer; border-bottom: 2px solid transparent;
      margin-bottom: -2px; transition: all .2s; color: var(--muted);
    }
    .category-tab.active { border-color: var(--gold); color: var(--dark); font-weight: 600; }
    .category-tab:hover { color: var(--dark); }

    /* ── FOOTER ── */
    footer {
      background: var(--dark); color: #B0A898;
      padding: 40px 32px 24px;
      display: grid; grid-template-columns: 2fr 1fr 1fr; gap: 40px;
    }
    .footer-brand {
      font-family: 'Playfair Display', serif;
      font-size: 1.3rem; font-weight: 700; color: var(--white);
      margin-bottom: 10px;
    }
    .footer-brand span { color: var(--gold); }
    .footer-tagline { font-size: 0.82rem; line-height: 1.6; }
    .footer-col h4 { color: var(--white); font-size: 0.8rem; font-weight: 700; letter-spacing: 0.08em; text-transform: uppercase; margin-bottom: 14px; }
    .footer-col a { display: block; color: #B0A898; text-decoration: none; font-size: 0.82rem; margin-bottom: 8px; transition: color .2s; }
    .footer-col a:hover { color: var(--gold); }
    .footer-bottom {
      background: var(--dark); border-top: 1px solid #333;
      text-align: center; padding: 16px 32px;
      font-size: 0.75rem; color: #666;
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      nav { padding: 0 16px; }
      .nav-links { display: none; }
      .hero { padding: 48px 20px; }
      .section { padding: 40px 16px; }
      .hero-cta { flex-direction: column; }
      footer { grid-template-columns: 1fr; gap: 28px; padding: 32px 16px 20px; }
      .form-row { grid-template-columns: 1fr; }
      .modal { border-radius: 0; max-height: 100vh; }
    }
  </style>
</head>
<body>

<!-- PROMO BANNER -->
<div class="promo-banner">
  🎁 <span>Gratis ongkir untuk pembelian di atas <strong>Rp 300.000</strong> &nbsp;·&nbsp; Kode: <strong>AURIC2026</strong></span>
</div>

<!-- NAVBAR -->
<nav>
  <a class="nav-brand" href="#"><span>AU</span>RIC</a>
  <div class="nav-links">
    <a href="#" class="active" onclick="showSection('beranda'); return false;">Beranda</a>
    <a href="#" onclick="showSection('wanita'); return false;">Fashion Wanita</a>
    <a href="#" onclick="showSection('pria'); return false;">Fashion Pria</a>
  </div>
  <div class="nav-actions">
    <button class="btn-history" onclick="openHistory()">📋 Riwayat</button>
    <button class="btn-cart" onclick="openCart()">
      🛍 Keranjang
      <span class="cart-badge" id="cartBadge">0</span>
    </button>
  </div>
</nav>

<!-- HERO -->
<section class="hero" id="hero-section">
  <div class="hero-content">
    <p class="hero-eyebrow">Koleksi Terbaru 2026</p>
    <h1 class="hero-title">Tampil <em>Percaya Diri</em> Setiap Hari</h1>
    <p class="hero-sub">Temukan koleksi fashion premium untuk wanita dan pria. Gaya modern dengan kualitas terbaik, harga terjangkau.</p>
    <div class="hero-cta">
      <button class="btn-primary" onclick="showSection('wanita')">Belanja Sekarang</button>
      <button class="btn-outline-white" onclick="showSection('pria')">Koleksi Pria →</button>
    </div>
  </div>
</section>

<!-- MAIN CONTENT -->
<main>

  <!-- BERANDA / SEMUA -->
  <section class="section" id="section-beranda">
    <div class="section-header">
      <div>
        <h2 class="section-title">Produk Unggulan</h2>
        <p class="section-subtitle">Pilihan terlaris minggu ini</p>
      </div>
      <a class="view-all" onclick="showSection('wanita')">Lihat semua →</a>
    </div>
    <div class="product-grid" id="grid-beranda"></div>
  </section>

  <!-- FASHION WANITA -->
  <section class="section" id="section-wanita" style="display:none;">
    <div class="section-header">
      <div>
        <h2 class="section-title">Fashion Wanita</h2>
        <p class="section-subtitle">Koleksi elegan & modern</p>
      </div>
    </div>
    <div class="product-grid" id="grid-wanita"></div>
  </section>

  <!-- FASHION PRIA -->
  <section class="section" id="section-pria" style="display:none;">
    <div class="section-header">
      <div>
        <h2 class="section-title">Fashion Pria</h2>
        <p class="section-subtitle">Koleksi maskulin & stylish</p>
      </div>
    </div>
    <div class="product-grid" id="grid-pria"></div>
  </section>

</main>

<!-- FOOTER -->
<footer>
  <div>
    <div class="footer-brand"><span>AU</span>RIC</div>
    <p class="footer-tagline">Belanja fashion favorit Anda dengan mudah dan aman. Kualitas premium, harga bersahabat.</p>
  </div>
  <div class="footer-col">
    <h4>Belanja</h4>
    <a href="#" onclick="showSection('wanita'); return false;">Fashion Wanita</a>
    <a href="#" onclick="showSection('pria'); return false;">Fashion Pria</a>
    <a href="#" onclick="openHistory(); return false;">Riwayat Pembelian</a>
  </div>
  <div class="footer-col">
    <h4>Bantuan</h4>
    <a href="#">Cara Pemesanan</a>
    <a href="#">Kebijakan Pengembalian</a>
    <a href="#">Hubungi Kami</a>
  </div>
</footer>
<div class="footer-bottom">© 2026 Auric Fashion — Belanja Fashion Favorite Anda.</div>

<!-- ════ CART MODAL ════ -->
<div class="modal-overlay" id="cartModal">
  <div class="modal" style="max-width:480px;">
    <div class="modal-header">
      <h2 class="modal-title">🛍 Keranjang Belanja</h2>
      <button class="modal-close" onclick="closeCart()">×</button>
    </div>
    <div class="modal-body">
      <div id="cartContent"></div>
    </div>
  </div>
</div>

<!-- ════ CHECKOUT MODAL ════ -->
<div class="modal-overlay" id="checkoutModal">
  <div class="modal" style="max-width:520px;">
    <div class="modal-header">
      <h2 class="modal-title">📦 Checkout</h2>
      <button class="modal-close" onclick="closeCheckout()">×</button>
    </div>
    <div class="modal-body">
      <p class="section-divider">Informasi Pengiriman</p>
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">Nama Lengkap</label>
          <input class="form-input" id="ck-name" placeholder="contoh: Andi Pratama" />
        </div>
        <div class="form-group">
          <label class="form-label">No. HP</label>
          <input class="form-input" id="ck-phone" placeholder="08xx-xxxx-xxxx" />
        </div>
      </div>
      <div class="form-group">
        <label class="form-label">Alamat Lengkap</label>
        <input class="form-input" id="ck-address" placeholder="Jl. Contoh No. 1, Kelurahan, Kecamatan" />
      </div>
      <div class="form-row">
        <div class="form-group">
          <label class="form-label">Kota</label>
          <input class="form-input" id="ck-city" placeholder="Medan" />
        </div>
        <div class="form-group">
          <label class="form-label">Kode Pos</label>
          <input class="form-input" id="ck-zip" placeholder="20111" />
        </div>
      </div>

      <p class="section-divider">Pengiriman</p>
      <div class="form-group">
        <select class="form-select" id="ck-shipping">
          <option value="regular">JNE Regular — Rp 20.000 (3-5 hari)</option>
          <option value="express">JNE Express — Rp 35.000 (1-2 hari)</option>
          <option value="same">Kurir Instan — Rp 50.000 (Hari ini)</option>
        </select>
      </div>

      <p class="section-divider">Pembayaran</p>
      <div class="payment-options" id="paymentOptions">
        <div class="payment-opt selected" data-val="transfer" onclick="selectPayment(this)">🏦 Transfer Bank</div>
        <div class="payment-opt" data-val="qris" onclick="selectPayment(this)">📱 QRIS</div>
        <div class="payment-opt" data-val="cod" onclick="selectPayment(this)">💵 COD</div>
        <div class="payment-opt" data-val="ewallet" onclick="selectPayment(this)">💳 E-Wallet</div>
      </div>

      <div id="ck-order-summary" style="margin-top:20px;"></div>

      <button class="btn-checkout" onclick="placeOrder()" style="margin-top:12px;">
        Konfirmasi Pesanan ✓
      </button>
    </div>
  </div>
</div>

<!-- ════ SUCCESS MODAL ════ -->
<div class="modal-overlay" id="successModal">
  <div class="modal" style="max-width:460px;">
    <div class="modal-header">
      <h2 class="modal-title">Pesanan Berhasil</h2>
      <button class="modal-close" onclick="closeSuccess()">×</button>
    </div>
    <div class="modal-body success-modal">
      <div class="success-icon">✅</div>
      <h3 class="success-title">Pemesanan Selesai!</h3>
      <p class="success-sub">Terima kasih telah berbelanja di AURIC Fashion. Pesanan Anda sedang diproses dan akan segera dikirimkan.</p>
      <div class="order-code" id="successOrderCode"></div>
      <div class="order-items-preview" id="successOrderItems"></div>
      <div class="success-actions">
        <button class="btn-secondary" onclick="openHistory(); closeSuccess()">📋 Lihat Riwayat</button>
        <button class="btn-primary" style="flex:1;" onclick="closeSuccess()">Lanjut Belanja</button>
      </div>
    </div>
  </div>
</div>

<!-- ════ HISTORY MODAL ════ -->
<div class="modal-overlay" id="historyModal">
  <div class="modal" style="max-width:560px;">
    <div class="modal-header">
      <h2 class="modal-title">📋 Riwayat Pembelian</h2>
      <button class="modal-close" onclick="closeHistory()">×</button>
    </div>
    <div class="modal-body">
      <div class="history-filters" id="historyFilters">
        <div class="filter-chip active" data-filter="all" onclick="filterHistory('all', this)">Semua</div>
        <div class="filter-chip" data-filter="Selesai" onclick="filterHistory('Selesai', this)">✅ Selesai</div>
        <div class="filter-chip" data-filter="Dikirim" onclick="filterHistory('Dikirim', this)">🚚 Dikirim</div>
        <div class="filter-chip" data-filter="Diproses" onclick="filterHistory('Diproses', this)">⏳ Diproses</div>
      </div>
      <div id="historyContent"></div>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast">
  <span class="toast-icon" id="toastIcon">✓</span>
  <span id="toastMsg">Item ditambahkan</span>
</div>

<script>
// ══════════════════════════════════════
//  DATA PRODUK
// ══════════════════════════════════════
const products = {
  wanita: [
    { id:'w1', name:'Dress Floral Premium', price:189000, original:250000, badge:'Terlaris',
     gambar :'https://images.unsplash.com/photo-1721990336298-90832e791b5a?q=80&w=387&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'w2', name:'Dress flow', price:135000, original:175000, badge:'Diskon 23%', gambar :'https://plus.unsplash.com/premium_photo-1661424159141-70611d4d66a0?q=80&w=774&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'w3', name:'Rok Midi Plisket', price:145000, original:190000, badge:'Baru', gambar:'https://images.unsplash.com/photo-1591948083708-6edc852d7275?q=80&w=870&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'w4', name:'Kemeja blus Oversize Wanita', price:119000, original:150000, badge:'Hot', gambar:'https://images.unsplash.com/photo-1780775589046-adc9c08b58d1?q=80&w=774&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'w5', name:'Celana Cullote', price:129000, original:165000, badge:'Terlaris', gambar:'https://plus.unsplash.com/premium_photo-1689371952452-c88c72464115?q=80&w=774&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'w6', name:'Blezer', price:175000, original:220000, badge:'Diskon 20%', gambar:'https://images.unsplash.com/photo-1571513722275-4b41940f54b8?q=80&w=774&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' }
  ],
  pria: [
    { id:'p1', name:'Kemeja Cowo', price:165000, original:210000, badge:'Terlaris', gambar:'https://images.unsplash.com/photo-1740711152088-88a009e877bb?q=80&w=880&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'p2', name:'Kaos Polo Premium', price:115000, original:145000, badge:'Baru', gambar:'https://plus.unsplash.com/premium_photo-1718913936342-eaafff98834b?q=80&w=872&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'p3', name:'Celana Chino Stretch', price:185000, original:230000, badge:'Hot', gambar:'https://images.unsplash.com/photo-1584865288642-42078afe6942?q=80&w=774&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'p4', name:'Jaket Bomber Casual', price:245000, original:310000, badge:'Diskon 21%', gambar:'https://plus.unsplash.com/premium_photo-1665461701010-3dd2b5a51c9b?q=80&w=764&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'p5', name:'Kemeja Flannel Kotak', price:139000, original:175000, badge:'Terlaris', gambar:'https://images.unsplash.com/photo-1710255067130-17af687f1ff2?q=80&w=774&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
    { id:'p6', name:'Celana Jogger Slim', price:125000, original:160000, badge:'Baru', gambar:'https://images.unsplash.com/photo-1518292309104-b0ee1cfba4cc?q=80&w=870&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D' },
  ]
};

// ══════════════════════════════════════
//  STATE
// ══════════════════════════════════════
let cart = JSON.parse(localStorage.getItem('auric_cart') || '[]');
let history = JSON.parse(localStorage.getItem('auric_history') || '[]');
let selectedPayment = 'transfer';
let lastOrder = null;

function saveCart() { localStorage.setItem('auric_cart', JSON.stringify(cart)); }
function saveHistory() { localStorage.setItem('auric_history', JSON.stringify(history)); }

// ══════════════════════════════════════
//  FORMAT
// ══════════════════════════════════════
function fmtRp(n) { return 'Rp ' + n.toLocaleString('id-ID'); }
function fmtDate(d) {
  return new Date(d).toLocaleDateString('id-ID', { day:'numeric', month:'long', year:'numeric', hour:'2-digit', minute:'2-digit' });
}

// ══════════════════════════════════════
//  RENDER PRODUK
// ══════════════════════════════════════
function renderProducts() {
  const all = [...products.wanita, ...products.pria];
  // Pilih 4 dari masing2 untuk beranda
  const featured = [...products.wanita.slice(0,3), ...products.pria.slice(0,3)];

  renderGrid('grid-beranda', featured);
  renderGrid('grid-wanita', products.wanita);
  renderGrid('grid-pria', products.pria);
}

function renderGrid(id, items) {
  document.getElementById(id).innerHTML = items.map(p => `
    <div class="product-card">
      <img class="product-img" src="${p.gambar}" alt="${p.name}">
      <div class="product-info">
        <span class="product-badge">${p.badge}</span>
        <div class="product-name">${p.name}</div>
        <div class="product-price">
          ${fmtRp(p.price)}
          <span class="original">${fmtRp(p.original)}</span>
        </div>
        <button class="btn-add-cart" onclick="addToCart('${p.id}')">+ Tambah ke Keranjang</button>
      </div>
    </div>
  `).join('');
}

// ══════════════════════════════════════
//  NAVIGASI SEKSI
// ══════════════════════════════════════
function showSection(name) {
  ['beranda','wanita','pria'].forEach(s => {
    document.getElementById('section-'+s).style.display = s===name ? 'block' : 'none';
  });
  document.getElementById('hero-section').style.display = name==='beranda' ? '' : 'none';
  document.querySelectorAll('.nav-links a').forEach((a,i) => {
    a.classList.toggle('active', ['beranda','wanita','pria'][i]===name);
  });
  window.scrollTo({top:0, behavior:'smooth'});
}

// ══════════════════════════════════════
//  CART
// ══════════════════════════════════════
function getProduct(id) {
  return [...products.wanita, ...products.pria].find(p => p.id === id);
}

function addToCart(id) {
  const p = getProduct(id);
  const existing = cart.find(c => c.id === id);
  if (existing) existing.qty++;
  else cart.push({ id, qty: 1 });
  saveCart();
  updateBadge();
  showToast('✓', `${p.name} ditambahkan ke keranjang`);
}

function updateBadge() {
  const total = cart.reduce((s,c) => s+c.qty, 0);
  document.getElementById('cartBadge').textContent = total;
}

function openCart() {
  renderCart();
  document.getElementById('cartModal').classList.add('open');
}
function closeCart() { document.getElementById('cartModal').classList.remove('open'); }

function renderCart() {
  const el = document.getElementById('cartContent');
  if (!cart.length) {
    el.innerHTML = `<div class="cart-empty"><div class="cart-empty-icon">🛍</div><p>Keranjang masih kosong.<br><small>Yuk, mulai belanja!</small></p></div>`;
    return;
  }
  const items = cart.map(c => {
    const p = getProduct(c.id);
    return `
    <div class="cart-item">
      <img class="cart-item-img" src="${p.gambar}" alt="${p.name}">
      <div class="cart-item-info">
        <div class="cart-item-name">${p.name}</div>
        <div class="cart-item-price">${fmtRp(p.price * c.qty)}</div>
        <div class="cart-qty">
          <button class="qty-btn" onclick="changeQty('${c.id}',-1)">−</button>
          <span class="qty-num">${c.qty}</span>
          <button class="qty-btn" onclick="changeQty('${c.id}',1)">+</button>
          <button class="cart-item-remove" onclick="removeFromCart('${c.id}')">Hapus</button>
        </div>
      </div>
    </div>`;
  }).join('');

  const subtotal = cart.reduce((s,c) => s + getProduct(c.id).price * c.qty, 0);
  const shipping = 20000;
  const total = subtotal + shipping;

  el.innerHTML = `
    ${items}
    <div class="cart-summary">
      <div class="summary-row"><span>Subtotal</span><span>${fmtRp(subtotal)}</span></div>
      <div class="summary-row"><span>Ongkos Kirim (est.)</span><span>${fmtRp(shipping)}</span></div>
      <div class="summary-row total"><span>Total</span><span>${fmtRp(total)}</span></div>
    </div>
    <button class="btn-checkout" onclick="openCheckout()">Lanjut ke Checkout →</button>
  `;
}

function changeQty(id, delta) {
  const item = cart.find(c => c.id === id);
  if (!item) return;
  item.qty = Math.max(1, item.qty + delta);
  saveCart(); updateBadge(); renderCart();
}

function removeFromCart(id) {
  cart = cart.filter(c => c.id !== id);
  saveCart(); updateBadge(); renderCart();
}

// ══════════════════════════════════════
//  CHECKOUT
// ══════════════════════════════════════
function openCheckout() {
  closeCart();
  renderCheckoutSummary();
  document.getElementById('checkoutModal').classList.add('open');
}
function closeCheckout() { document.getElementById('checkoutModal').classList.remove('open'); }

function renderCheckoutSummary() {
  const subtotal = cart.reduce((s,c) => s + getProduct(c.id).price * c.qty, 0);
  const shippingEl = document.getElementById('ck-shipping');
  const shippingCost = shippingEl ? [20000,35000,50000][shippingEl.selectedIndex] : 20000;
  const total = subtotal + shippingCost;
  document.getElementById('ck-order-summary').innerHTML = `
    <div style="background:var(--cream);border:1px solid var(--border);border-radius:8px;padding:14px;">
      <div style="font-size:0.7rem;font-weight:700;letter-spacing:0.1em;color:var(--muted);margin-bottom:10px;">RINGKASAN PESANAN</div>
      ${cart.map(c => {
        const p = getProduct(c.id);
        return `<div style="display:flex;justify-content:space-between;font-size:0.82rem;padding:4px 0;border-bottom:1px dashed var(--border);">
          <span>${p.emoji} ${p.name} ×${c.qty}</span>
          <span style="font-weight:600;">${fmtRp(p.price*c.qty)}</span>
        </div>`;
      }).join('')}
      <div style="display:flex;justify-content:space-between;font-size:0.9rem;font-weight:700;margin-top:10px;padding-top:8px;border-top:1px solid var(--border);">
        <span>Total Bayar</span><span style="color:var(--gold);">${fmtRp(total)}</span>
      </div>
    </div>`;
}

function selectPayment(el) {
  document.querySelectorAll('.payment-opt').forEach(o => o.classList.remove('selected'));
  el.classList.add('selected');
  selectedPayment = el.dataset.val;
}

function placeOrder() {
  const name = document.getElementById('ck-name').value.trim();
  const phone = document.getElementById('ck-phone').value.trim();
  const address = document.getElementById('ck-address').value.trim();
  const city = document.getElementById('ck-city').value.trim();

  if (!name || !phone || !address || !city) {
    showToast('⚠️', 'Lengkapi semua data pengiriman'); return;
  }

  const shippingEl = document.getElementById('ck-shipping');
  const shippingCosts = [20000, 35000, 50000];
  const shippingLabels = ['JNE Regular', 'JNE Express', 'Kurir Instan'];
  const shippingCost = shippingCosts[shippingEl.selectedIndex];
  const subtotal = cart.reduce((s,c) => s + getProduct(c.id).price * c.qty, 0);

  const order = {
    id: 'ARC-' + Date.now().toString().slice(-8),
    date: new Date().toISOString(),
    customer: name,
    phone, address, city,
    shipping: shippingLabels[shippingEl.selectedIndex],
    payment: selectedPayment,
    items: cart.map(c => ({ ...getProduct(c.id), qty: c.qty })),
    subtotal,
    shippingCost,
    total: subtotal + shippingCost,
    status: 'Diproses'
  };

  history.unshift(order);
  saveHistory();
  lastOrder = order;

  // Simulate status progression
  setTimeout(() => {
    const o = history.find(h => h.id === order.id);
    if (o) { o.status = 'Dikirim'; saveHistory(); }
  }, 5000);
  setTimeout(() => {
    const o = history.find(h => h.id === order.id);
    if (o) { o.status = 'Selesai'; saveHistory(); }
  }, 10000);

  cart = [];
  saveCart();
  updateBadge();
  closeCheckout();
  showSuccessModal(order);
}

// ══════════════════════════════════════
//  SUCCESS MODAL
// ══════════════════════════════════════
function showSuccessModal(order) {
  const payLabels = { transfer:'Transfer Bank', qris:'QRIS', cod:'COD', ewallet:'E-Wallet' };
  document.getElementById('successOrderCode').innerHTML = `
    <div class="order-code-label">ID PESANAN</div>
    <div class="order-code-value">${order.id}</div>
    <div style="margin-top:8px;font-size:0.78rem;color:var(--muted);">
      ${fmtDate(order.date)} &nbsp;·&nbsp; ${payLabels[order.payment]} &nbsp;·&nbsp; ${order.shipping}
    </div>`;

  document.getElementById('successOrderItems').innerHTML = `
    ${order.items.map(i => `
    <div class="order-item-row">
      <span>${i.emoji} ${i.name} ×${i.qty}</span>
      <span style="font-weight:600;">${fmtRp(i.price * i.qty)}</span>
    </div>`).join('')}
    <div class="order-total-row">
      <span>Total Bayar</span>
      <span style="color:var(--gold);">${fmtRp(order.total)}</span>
    </div>`;

  document.getElementById('successModal').classList.add('open');
}
function closeSuccess() { document.getElementById('successModal').classList.remove('open'); }

// ══════════════════════════════════════
//  HISTORY
// ══════════════════════════════════════
let currentFilter = 'all';

function openHistory() {
  renderHistory();
  document.getElementById('historyModal').classList.add('open');
}
function closeHistory() { document.getElementById('historyModal').classList.remove('open'); }

function filterHistory(filter, el) {
  currentFilter = filter;
  document.querySelectorAll('.filter-chip').forEach(c => c.classList.remove('active'));
  el.classList.add('active');
  renderHistory(false);
}

function renderHistory(resetFilters = true) {
  if (resetFilters) {
    currentFilter = 'all';
    document.querySelectorAll('.filter-chip').forEach(c => c.classList.remove('active'));
    document.querySelector('[data-filter="all"]')?.classList.add('active');
  }

  const el = document.getElementById('historyContent');
  const filtered = currentFilter === 'all' ? history : history.filter(o => o.status === currentFilter);

  if (!filtered.length) {
    el.innerHTML = `<div class="history-empty"><div style="font-size:2.5rem;margin-bottom:12px;">📭</div><p>Belum ada pesanan${currentFilter !== 'all' ? ' dengan status ini' : ''}.</p></div>`;
    return;
  }

  const statusClass = { 'Selesai':'status-selesai', 'Diproses':'status-diproses', 'Dikirim':'status-dikirim' };
  const statusIcon = { 'Selesai':'✅', 'Diproses':'⏳', 'Dikirim':'🚚' };

  el.innerHTML = filtered.map(o => `
    <div class="history-card">
      <div class="history-card-header">
        <div>
          <div class="history-order-id">${o.id}</div>
          <div class="history-date">${fmtDate(o.date)}</div>
        </div>
        <span class="history-status ${statusClass[o.status]}">${statusIcon[o.status]} ${o.status}</span>
      </div>
      <div class="history-card-body">
        <div class="history-items">
          ${o.items.map(i => `
          <div class="history-item">
            <div>
              <div class="history-item-name">${i.emoji} ${i.name}</div>
              <div class="history-item-sub">×${i.qty} &nbsp;·&nbsp; ${fmtRp(i.price)} / pcs</div>
            </div>
            <span style="font-weight:600;">${fmtRp(i.price * i.qty)}</span>
          </div>`).join('')}
        </div>
        <div style="font-size:0.78rem;color:var(--muted);margin-bottom:4px;">
          📍 ${o.address}, ${o.city} &nbsp;·&nbsp; 🚚 ${o.shipping}
        </div>
        <div class="history-footer">
          <div class="history-total">Total: <span style="color:var(--gold);">${fmtRp(o.total)}</span></div>
          <button class="btn-reorder" onclick="reorder('${o.id}')">🔁 Pesan Lagi</button>
        </div>
      </div>
    </div>
  `).join('');
}

function reorder(orderId) {
  const order = history.find(o => o.id === orderId);
  if (!order) return;
  order.items.forEach(item => {
    const existing = cart.find(c => c.id === item.id);
    if (existing) existing.qty += item.qty;
    else cart.push({ id: item.id, qty: item.qty });
  });
  saveCart(); updateBadge();
  closeHistory();
  openCart();
  showToast('🔁', 'Produk ditambahkan ke keranjang');
}

// ══════════════════════════════════════
//  TOAST
// ══════════════════════════════════════
let toastTimer;
function showToast(icon, msg) {
  const t = document.getElementById('toast');
  document.getElementById('toastIcon').textContent = icon;
  document.getElementById('toastMsg').textContent = msg;
  t.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => t.classList.remove('show'), 2800);
}

// ══════════════════════════════════════
//  CLOSE ON OVERLAY CLICK
// ══════════════════════════════════════
['cartModal','checkoutModal','successModal','historyModal'].forEach(id => {
  document.getElementById(id).addEventListener('click', function(e) {
    if (e.target === this) this.classList.remove('open');
  });
});

// Update shipping cost on change
document.getElementById('ck-shipping')?.addEventListener('change', renderCheckoutSummary);

// ══════════════════════════════════════
//  INIT
// ══════════════════════════════════════
renderProducts();
updateBadge();
</script>
</body>
</html>
