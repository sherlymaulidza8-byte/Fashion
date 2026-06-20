
<html lang="id">
<head>
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Auric — Fashion Shop</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,500;0,9..144,600;1,9..144,400&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#1A1A1A;
    --bg:#FAF8F5;
    --gold:#C9A876;
    --gold-deep:#A8855A;
    --surface:#FFFFFF;
    --line:#E8E3DC;
    --pine:#2D5A4A;
    --pine-bg:#EAF1ED;
    --muted:#8A8378;
  }
  *{margin:0;padding:0;box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    font-family:'Inter',sans-serif;
    background:var(--bg);
    color:var(--ink);
    -webkit-font-smoothing:antialiased;
    overflow-x:hidden;
  }
  h1,h2,h3,.display{font-family:'Fraunces',serif;}
  a{text-decoration:none;color:inherit;}
  button{font-family:inherit;cursor:pointer;border:none;background:none;}
  ::selection{background:var(--gold);color:var(--ink);}

  /* focus visibility */
  button:focus-visible, a:focus-visible, input:focus-visible, select:focus-visible, textarea:focus-visible{
    outline:2px solid var(--gold-deep);
    outline-offset:2px;
  }

  @media (prefers-reduced-motion: reduce){
    *{animation-duration:0.01ms !important; transition-duration:0.01ms !important;}
  }

  /* ===== HEADER ===== */
  header{
    position:sticky; top:0; z-index:50;
    background:rgba(250,248,245,0.92);
    backdrop-filter:blur(10px);
    border-bottom:1px solid var(--line);
  }
  .header-inner{
    max-width:1200px; margin:0 auto;
    display:flex; align-items:center; justify-content:space-between;
    padding:18px 32px;
  }
  .logo{
    font-size:24px; font-weight:600; letter-spacing:0.5px;
    display:flex; align-items:baseline; gap:6px;
  }
  .logo span{color:var(--gold-deep); font-style:italic; font-weight:400;}
  nav{display:flex; gap:36px; align-items:center;}
  .nav-link{
    font-size:14px; font-weight:500; letter-spacing:0.3px;
    color:var(--ink); position:relative; padding:4px 0;
    transition:color .2s;
  }
  .nav-link::after{
    content:''; position:absolute; left:0; bottom:0; height:1px; width:0;
    background:var(--gold-deep); transition:width .25s ease;
  }
  .nav-link:hover::after, .nav-link.active::after{width:100%;}
  .nav-link.active{color:var(--gold-deep);}
  .cart-btn{
    display:flex; align-items:center; gap:8px;
    padding:9px 18px; border:1px solid var(--ink); border-radius:999px;
    font-size:13px; font-weight:500; position:relative;
    transition:background .2s, color .2s;
  }
  .cart-btn:hover{background:var(--ink); color:var(--bg);}
  .cart-count{
    position:absolute; top:-7px; right:-7px;
    background:var(--gold-deep); color:#fff;
    font-size:11px; font-weight:700; width:19px; height:19px;
    border-radius:50%; display:flex; align-items:center; justify-content:center;
  }
  .mobile-toggle{display:none; font-size:22px;}

  @media (max-width:840px){
    nav{
      position:fixed; top:65px; left:0; right:0; bottom:0;
      background:var(--bg); flex-direction:column; justify-content:flex-start;
      padding:32px; gap:28px; transform:translateX(100%);
      transition:transform .3s ease; z-index:60;
    }
    nav.open{transform:translateX(0);}
    .mobile-toggle{display:block;}
    .cart-btn{order:-1; margin-bottom:12px;}
  }

  /* ===== HERO / BANNER ===== */
  .hero{
    max-width:1200px; margin:0 auto;
    padding:64px 32px 56px;
    display:grid; grid-template-columns:1.1fr 0.9fr; gap:64px; align-items:center;
  }
  .hero-eyebrow{
    font-size:12px; letter-spacing:2.5px; text-transform:uppercase;
    color:var(--gold-deep); font-weight:600; margin-bottom:18px;
    display:flex; align-items:center; gap:10px;
  }
  .hero-eyebrow::before{content:''; width:28px; height:1px; background:var(--gold-deep);}
  .hero h1{
    font-size:clamp(40px,6vw,68px); line-height:1.02; font-weight:500;
    letter-spacing:-0.5px; margin-bottom:22px;
  }
  .hero h1 em{font-style:italic; color:var(--gold-deep); font-weight:400;}
  .hero p{font-size:16px; color:var(--muted); max-width:420px; margin-bottom:32px; line-height:1.6;}
  .hero-ctas{display:flex; gap:14px;}
  .btn-primary{
    background:var(--ink); color:var(--bg); padding:15px 30px;
    font-size:13px; font-weight:600; letter-spacing:0.5px; text-transform:uppercase;
    border-radius:2px; transition:background .2s, transform .2s;
  }
  .btn-primary:hover{background:var(--gold-deep); transform:translateY(-1px);}
  .btn-ghost{
    border:1px solid var(--ink); padding:15px 30px;
    font-size:13px; font-weight:600; letter-spacing:0.5px; text-transform:uppercase;
    border-radius:2px; transition:all .2s;
  }
  .btn-ghost:hover{background:var(--ink); color:var(--bg);}
  .hero-visual{
    position:relative; aspect-ratio:4/5; border-radius:4px; overflow:hidden;
    background:linear-gradient(160deg,#EFE9E0,#DCD3C4);
  }
  .hero-visual .frame-label{
    position:absolute; bottom:20px; left:20px; right:20px;
    background:rgba(255,255,255,0.85); backdrop-filter:blur(6px);
    padding:14px 18px; border-radius:2px; font-size:12px;
    display:flex; justify-content:space-between; align-items:center;
  }
  .hero-visual svg{position:absolute; inset:0; width:100%; height:100%;}

  @media (max-width:840px){
    .hero{grid-template-columns:1fr; padding:40px 24px;}
    .hero-visual{order:-1; aspect-ratio:16/10;}
  }

  /* ===== SECTION SHELL ===== */
  .section{max-width:1200px; margin:0 auto; padding:72px 32px;}
  .section-head{
    display:flex; justify-content:space-between; align-items:flex-end;
    margin-bottom:40px; border-bottom:1px solid var(--line); padding-bottom:24px;
  }
  .section-tag{
    font-size:12px; letter-spacing:2px; text-transform:uppercase;
    color:var(--gold-deep); font-weight:600; margin-bottom:10px;
  }
  .section-head h2{font-size:clamp(28px,3.5vw,38px); font-weight:500;}
  .section-sub{font-size:14px; color:var(--muted); max-width:320px; text-align:right;}
  @media (max-width:600px){
    .section-head{flex-direction:column; align-items:flex-start; gap:14px;}
    .section-sub{text-align:left;}
  }

  /* category pill filters */
  .filters{display:flex; gap:10px; flex-wrap:wrap; margin-bottom:32px;}
  .filter-pill{
    padding:8px 18px; border:1px solid var(--line); border-radius:999px;
    font-size:13px; font-weight:500; color:var(--muted); transition:all .2s;
  }
  .filter-pill:hover{border-color:var(--gold-deep); color:var(--ink);}
  .filter-pill.active{background:var(--ink); color:var(--bg); border-color:var(--ink);}

  /* ===== PRODUCT GRID ===== */
  .grid{
    display:grid; grid-template-columns:repeat(4,1fr); gap:28px 24px;
  }
  @media (max-width:980px){.grid{grid-template-columns:repeat(3,1fr);}}
  @media (max-width:700px){.grid{grid-template-columns:repeat(2,1fr); gap:20px 14px;}}

  
  .card-img{
    position:relative; aspect-ratio:3/4; border-radius:3px; overflow:hidden;
    background:#EFEAE2; margin-bottom:14px;
  }
  .card-img svg{width:100%; height:100%; transition:transform .5s ease;}
  .card:hover .card-img svg{transform:scale(1.06);}
  .card-tag{
    position:absolute; top:10px; left:10px; background:var(--surface);
    font-size:10px; letter-spacing:1px; text-transform:uppercase; font-weight:700;
    padding:5px 9px; border-radius:2px; color:var(--gold-deep);
  }
  .card-quick{
    position:absolute; bottom:0; left:0; right:0; padding:12px;
    background:linear-gradient(to top, rgba(0,0,0,0.55), transparent);
    opacity:0; transition:opacity .25s; display:flex; justify-content:flex-end;
  }
  .card:hover .card-quick{opacity:1;}
  .quick-add{
    background:var(--surface); color:var(--ink); font-size:11px; font-weight:600;
    padding:8px 14px; border-radius:999px; letter-spacing:0.3px;
  }
  .quick-add:hover{background:var(--gold-deep); color:#fff;}
  .card-name{font-size:14.5px; font-weight:500; margin-bottom:4px;}
  .card-price{font-size:14px; color:var(--gold-deep); font-weight:600;}

  /* ===== PRODUCT DETAIL ===== */
  .pdp{
    max-width:1200px; margin:0 auto; padding:48px 32px 80px;
    display:grid; grid-template-columns:1fr 1fr; gap:64px;
  }
  @media (max-width:840px){.pdp{grid-template-columns:1fr; gap:36px; padding:32px 24px 60px;}}
  .pdp-gallery-main{
    aspect-ratio:4/5; border-radius:4px; overflow:hidden; background:#EFEAE2; margin-bottom:14px;
  }
  .pdp-gallery-thumbs{display:flex; gap:10px;}
  .pdp-thumb{
    width:72px; height:90px; border-radius:3px; overflow:hidden; background:#EFEAE2;
    border:1.5px solid transparent; cursor:pointer; opacity:0.6; transition:all .2s;
  }
  .pdp-thumb.active{border-color:var(--gold-deep); opacity:1;}

  .breadcrumb{font-size:12px; color:var(--muted); margin-bottom:18px;}
  .breadcrumb a:hover{color:var(--gold-deep);}
  .pdp h1{font-size:clamp(26px,3vw,34px); font-weight:500; margin-bottom:10px; line-height:1.15;}
  .pdp-price{font-size:24px; color:var(--gold-deep); font-weight:700; margin-bottom:20px;}
  .pdp-desc{font-size:14.5px; color:var(--muted); line-height:1.7; margin-bottom:30px; max-width:460px;}

  .option-block{margin-bottom:26px;}
  .option-label{
    font-size:12px; font-weight:600; text-transform:uppercase; letter-spacing:1px;
    margin-bottom:12px; display:flex; justify-content:space-between;
  }
  .option-label .sel-val{color:var(--gold-deep); text-transform:none; font-weight:500; letter-spacing:0;}
  .size-row{display:flex; gap:9px; flex-wrap:wrap;}
  .size-opt{
    width:46px; height:46px; border:1px solid var(--line); border-radius:2px;
    display:flex; align-items:center; justify-content:center; font-size:13px; font-weight:500;
    transition:all .15s;
  }
  .size-opt:hover{border-color:var(--ink);}
  .size-opt.active{background:var(--ink); color:var(--bg); border-color:var(--ink);}

  .color-row{display:flex; gap:12px;}
  .color-opt{
    width:34px; height:34px; border-radius:50%; border:2px solid transparent;
    display:flex; align-items:center; justify-content:center; position:relative; cursor:pointer;
  }
  .color-opt.active{border-color:var(--gold-deep);}
  .color-swatch{width:26px; height:26px; border-radius:50%; border:1px solid rgba(0,0,0,0.1);}

  .qty-row{display:flex; align-items:center; gap:0; width:fit-content; border:1px solid var(--line); border-radius:2px;}
  .qty-btn{width:42px; height:42px; font-size:18px; color:var(--muted); transition:color .15s;}
  .qty-btn:hover{color:var(--ink);}
  .qty-val{width:48px; text-align:center; font-size:15px; font-weight:600; border-left:1px solid var(--line); border-right:1px solid var(--line); height:42px; line-height:42px;}

  .pdp-actions{display:flex; gap:12px; margin-top:34px;}
  .pdp-actions .btn-primary, .pdp-actions .btn-ghost{flex:1; text-align:center;}

  .stock-note{display:flex; align-items:center; gap:8px; font-size:12.5px; color:var(--pine); margin-top:18px;}
  .stock-dot{width:7px; height:7px; border-radius:50%; background:var(--pine);}

  /* ===== CART DRAWER ===== */
  .overlay{
    position:fixed; inset:0; background:rgba(26,26,26,0.4); z-index:90;
    opacity:0; visibility:hidden; transition:opacity .3s; backdrop-filter:blur(2px);
  }
  .overlay.show{opacity:1; visibility:visible;}
  .drawer{
    position:fixed; top:0; right:0; bottom:0; width:420px; max-width:92vw;
    background:var(--bg); z-index:95; transform:translateX(100%);
    transition:transform .35s cubic-bezier(.22,.9,.32,1);
    display:flex; flex-direction:column; box-shadow:-12px 0 40px rgba(0,0,0,0.1);
  }
  .drawer.show{transform:translateX(0);}
  .drawer-head{
    padding:24px 28px; border-bottom:1px solid var(--line);
    display:flex; justify-content:space-between; align-items:center;
  }
  .drawer-head h3{font-size:20px; font-weight:500;}
  .drawer-close{font-size:22px; color:var(--muted); line-height:1;}
  .drawer-body{flex:1; overflow-y:auto; padding:20px 28px;}
  .cart-item{display:flex; gap:14px; padding:16px 0; border-bottom:1px solid var(--line);}
  .cart-item-img{width:70px; height:88px; border-radius:3px; background:#EFEAE2; flex-shrink:0; overflow:hidden;}
  .cart-item-info{flex:1; display:flex; flex-direction:column;}
  .cart-item-name{font-size:14px; font-weight:500;}
  .cart-item-meta{font-size:12px; color:var(--muted); margin:3px 0 8px;}
  .cart-item-row{display:flex; justify-content:space-between; align-items:center; margin-top:auto;}
  .cart-item-qty{display:flex; align-items:center; border:1px solid var(--line); border-radius:2px;}
  .cart-item-qty button{width:26px; height:26px; font-size:14px;}
  .cart-item-qty span{width:28px; text-align:center; font-size:13px; font-weight:600;}
  .cart-item-price{font-size:13.5px; font-weight:600; color:var(--gold-deep);}
  .cart-item-remove{font-size:11px; color:var(--muted); text-decoration:underline; margin-top:6px; align-self:flex-start;}
  .cart-item-remove:hover{color:#b14545;}
  .drawer-foot{padding:24px 28px; border-top:1px solid var(--line);}
  .drawer-total-row{display:flex; justify-content:space-between; font-size:15px; margin-bottom:18px;}
  .drawer-total-row strong{font-size:19px; color:var(--gold-deep);}
  .empty-cart{text-align:center; padding:60px 20px; color:var(--muted);}
  .empty-cart svg{width:64px; height:64px; margin-bottom:16px; opacity:0.4;}

  /* ===== CHECKOUT ===== */
  .checkout-wrap{max-width:1100px; margin:0 auto; padding:48px 32px 90px;}
  .checkout-grid{display:grid; grid-template-columns:1.3fr 1fr; gap:48px; margin-top:32px; align-items:start;}
  @media (max-width:880px){.checkout-grid{grid-template-columns:1fr;}}

  .field-group{margin-bottom:22px;}
  .field-label{font-size:12.5px; font-weight:600; margin-bottom:8px; display:block;}
  .field-input, .field-select, .field-textarea{
    width:100%; border:1px solid var(--line); background:var(--surface); border-radius:3px;
    padding:13px 14px; font-size:14px; font-family:inherit; color:var(--ink);
    transition:border-color .2s;
  }
  .field-input:focus, .field-select:focus, .field-textarea:focus{border-color:var(--gold-deep); outline:none;}
  .field-textarea{resize:vertical; min-height:80px;}
  .field-row{display:grid; grid-template-columns:1fr 1fr 1fr; gap:14px;}
  @media (max-width:560px){.field-row{grid-template-columns:1fr;}}
  .field-error{font-size:12px; color:#b14545; margin-top:6px; display:none;}
  .field-group.error .field-input, .field-group.error .field-select, .field-group.error .field-textarea{border-color:#b14545;}
  .field-group.error .field-error{display:block;}

  .pay-options{display:flex; flex-direction:column; gap:10px;}
  .pay-card{
    border:1px solid var(--line); border-radius:4px; padding:16px 18px; cursor:pointer;
    transition:all .2s;
  }
  .pay-card.active{border-color:var(--gold-deep); background:#FBF7F0;}
  .pay-card-head{display:flex; align-items:center; gap:12px; font-size:14px; font-weight:500;}
  .pay-radio{width:18px; height:18px; border-radius:50%; border:1.5px solid var(--line); flex-shrink:0; position:relative;}
  .pay-card.active .pay-radio{border-color:var(--gold-deep);}
  .pay-card.active .pay-radio::after{
    content:''; position:absolute; inset:3px; border-radius:50%; background:var(--gold-deep);
  }
  .pay-sub{font-size:12px; color:var(--muted); margin-left:30px; margin-top:2px;}
  .pay-banks{display:flex; gap:8px; margin-top:12px; margin-left:30px; flex-wrap:wrap;}
  .bank-chip{
    border:1px solid var(--line); border-radius:2px; padding:8px 12px; font-size:12px; font-weight:600;
    color:var(--muted); transition:all .15s;
  }
  .bank-chip.active{border-color:var(--gold-deep); color:var(--gold-deep); background:#fff;}

  .summary-box{
    background:var(--surface); border:1px solid var(--line); border-radius:6px; padding:26px;
    position:sticky; top:100px;
  }
  .summary-box h3{font-size:17px; font-weight:500; margin-bottom:20px;}
  .summary-item{display:flex; gap:12px; padding:12px 0; border-bottom:1px solid var(--line); font-size:13.5px;}
  .summary-item-img{width:48px; height:60px; border-radius:2px; background:#EFEAE2; flex-shrink:0; overflow:hidden;}
  .summary-item-info{flex:1;}
  .summary-item-name{font-weight:500; margin-bottom:2px;}
  .summary-item-meta{font-size:11.5px; color:var(--muted);}
  .summary-item-price{font-weight:600; font-size:13px; white-space:nowrap;}
  .summary-row{display:flex; justify-content:space-between; font-size:13.5px; padding:10px 0; color:var(--muted);}
  .summary-row.total{
    border-top:1px solid var(--line); margin-top:8px; padding-top:16px;
    font-size:16px; color:var(--ink); font-weight:600;
  }
  .summary-row.total span:last-child{color:var(--gold-deep); font-size:19px;}
  .order-btn{width:100%; margin-top:20px; text-align:center; padding:16px;}
  .secure-note{
    display:flex; align-items:center; gap:7px; justify-content:center;
    font-size:11.5px; color:var(--muted); margin-top:14px;
  }

  /* ===== TOAST ===== */
  .toast{
    position:fixed; bottom:28px; left:50%; transform:translateX(-50%) translateY(20px);
    background:var(--ink); color:var(--bg); padding:14px 26px; border-radius:999px;
    font-size:13.5px; font-weight:500; z-index:200; display:flex; align-items:center; gap:10px;
    opacity:0; transition:opacity .3s, transform .3s; pointer-events:none;
  }
  .toast.show{opacity:1; transform:translateX(-50%) translateY(0);}
  .toast .dot{width:7px; height:7px; border-radius:50%; background:var(--pine);}

  /* ===== SUCCESS PANEL ===== */
  .success-wrap{
    max-width:560px; margin:90px auto; text-align:center; padding:0 24px;
  }
  .success-icon{
    width:74px; height:74px; border-radius:50%; background:var(--pine-bg);
    display:flex; align-items:center; justify-content:center; margin:0 auto 26px;
  }
  .success-wrap h2{font-size:30px; margin-bottom:12px;}
  .success-wrap p{color:var(--muted); font-size:14.5px; margin-bottom:30px; line-height:1.6;}
  .receipt{
    background:var(--surface); border:1px solid var(--line); border-radius:6px;
    padding:24px; text-align:left; margin-bottom:30px;
  }
  .receipt-row{display:flex; justify-content:space-between; font-size:13.5px; padding:8px 0; border-bottom:1px dashed var(--line);}
  .receipt-row:last-child{border-bottom:none;}
  .receipt-row span:first-child{color:var(--muted);}
  .receipt-row span:last-child{font-weight:600;}

  footer{border-top:1px solid var(--line); padding:40px 32px; text-align:center; color:var(--muted); font-size:12.5px; margin-top:40px;}

  .hide{display:none !important;}
  .view{animation:fadeIn .35s ease;}
  @keyframes fadeIn{from{opacity:0; transform:translateY(8px);} to{opacity:1; transform:translateY(0);}}
</style>
</head>
<body>

<header>
  <div class="header-inner">
    <a href="#" class="logo" onclick="goHome(event)">AURIC<span>&nbsp;Fashion</span></a>
    <button class="mobile-toggle" id="mobileToggle" aria-label="Buka menu">☰</button>
    <nav id="mainNav">
      <a href="#" class="nav-link" data-page="home" onclick="navigate(event,'home')">Beranda</a>
      <a href="#" class="nav-link" data-page="wanita" onclick="navigate(event,'wanita')">Fashion Wanita</a>
      <a href="#" class="nav-link" data-page="pria" onclick="navigate(event,'pria')">Fashion Pria</a>
      <button class="cart-btn" onclick="openCart()">
           Keranjang <span class="cart-count hide" id="cartCount">0</span>
      </button>
    </nav>
  </div>
</header>

<main id="app"></main>

<footer>
  © 2026 Auric Fashion —, Dibuat Oleh Sherly, Untuk Belanja Fashion Favorite Anda.
</footer>

<!-- CART DRAWER -->
<div class="overlay" id="overlay" onclick="closeAllOverlays()"></div>
<div class="drawer" id="cartDrawer">
  <div class="drawer-head">
    <h3>Keranjang Anda</h3>
    <button class="drawer-close" onclick="closeCart()">×</button>
  </div>
  <div class="drawer-body" id="cartBody"></div>
  <div class="drawer-foot" id="cartFoot"></div>
</div>

<div class="toast" id="toast"><span class="dot"></span><span id="toastMsg"></span></div>

<script>
/* ============ DATA (referensi struktur tabel Produk) ============ */
const PRODUCTS = [
  // ---- WANITA ----
  
  {id:1, nama:"Dress Linen Midi", 
  kategori:"wanita", sub:"Dress",
  harga:285000,
  gambar:"img/midi.jpg", 
  ukuran:["XS","S","M","L"],
  warna:[["Krem","#E8DCC8"],["Hitam","#222"],["Terracotta","#C77B58"]],
  deskripsi:"Dress midi berbahan linen premium, potongan A-line yang nyaman untuk aktivitas sehari-hari maupun acara santai. Jatuh kain lembut dan breathable.", tag:"Baru"},
  {id:2, nama:"Blouse Satin", kategori:"wanita", sub:"Blouse", harga:175000,
  gambar:"img/blouse-satin.jpg.jpg", ukuran:["S","M","L","XL"], warna:[["Putih","#FAFAFA"],["Dusty Pink","#D9A9A0"],["Navy","#22304A"]], deskripsi:"Blouse satin dengan detail tali leher, cocok dipadukan dengan rok maupun celana formal. Tekstur lembut berkilau halus.", tag:"Favorit"},
  {id:3, nama:"Kemeja Wanita Oversized", kategori:"wanita", sub:"Kemeja", harga:165000,
  gambar:"https://images.unsplash.com/photo-1541101767792-f9b2b1c4f127?q=80&w=600&auto=format&fit=crop](https://images.unsplash.com/photo-1541101767792-f9b2b1c4f127?q=80&w=600&auto=format&fit=crop)",
  ukuran:["S","M","L","XL"], warna:[["Putih","#FAFAFA"],["Biru Muda","#AFC8DC"],["Abu-abu","#A9A9A2"]], deskripsi:"Kemeja oversized dengan bahan katun ringan, desain unisex-fit yang fleksibel untuk gaya kasual maupun semi-formal.", tag:null},
  {id:4, nama:"Rok Plisket Midi", kategori:"wanita", sub:"Rok", harga:195000,
  gambar:"img/rokpris.jpg", ukuran:["S","M","L"], warna:[["Hitam","#222"],["Khaki","#BBA875"],["Maroon","#6E2E33"]], deskripsi:"Rok plisket dengan jatuh kain yang anggun, pinggang elastis untuk kenyamanan ekstra sepanjang hari.", tag:null},
  {id:5, nama:"Celana Kulot Wanita", kategori:"wanita", sub:"Celana", harga:155000,
  gambar:"img/celanakulot.jpg", ukuran:["S","M","L","XL"], warna:[["Hitam","#222"],["Krem","#E8DCC8"],["Navy","#22304A"]], deskripsi:"Celana kulot longgar dengan bahan jatuh, sangat nyaman dipakai untuk aktivitas harian maupun bekerja.", tag:"Diskon"},
  {id:6, nama:"Dress Wrap Floral", kategori:"wanita", sub:"Dress", harga:245000,
  gambar:"img/DressFloral.jpg", ukuran:["XS","S","M","L"], warna:[["Floral Krem","#E3D8C2"],["Floral Navy","#283449"]], deskripsi:"Dress model wrap dengan motif floral lembut, siluet feminin yang flattering untuk berbagai bentuk tubuh.", tag:null},

  // ---- PRIA ----
  {id:7, nama:"Kemeja Casual Pria", kategori:"pria", sub:"Kemeja", harga:150000,
  gambar:"https://images.unsplash.com/photo-1603252109303-2751441dd157?q=80&w=600&auto=format&fit=crop](https://images.unsplash.com/photo-1603252109303-2751441dd157?q=80&w=600&auto=format&fit=crop)", ukuran:["XS","S","M","L","XL","XXL"], warna:[["Hitam","#222"],["Putih","#FAFAFA"],["Navy","#22304A"],["Abu-abu","#8C8A86"]], deskripsi:"Bahan premium, nyaman dipakai sehari-hari. Cutting modern slim-fit dengan jahitan rapi dan material breathable sepanjang hari.", tag:"Favorit"},
  {id:8, nama:"Kaos Polos Premium", kategori:"pria", sub:"Kaos", harga:95000,
  gambar:"img/KaosPolos.jpg", ukuran:["S","M","L","XL","XXL"], warna:[["Hitam","#222"],["Putih","#FAFAFA"],["Abu-abu","#8C8A86"]], deskripsi:"Kaos berbahan cotton combed 30s, tebal namun tetap sejuk dipakai. Pilihan dasar yang wajib ada di lemari.", tag:null},
  {id:9, nama:"Jaket Bomber Pria", kategori:"pria", sub:"Jaket", harga:320000,
  gambar:"https://images.unsplash.com/photo-1551028719-00167b16eac5?q=80&w=600&auto=format&fit=crop](https://images.unsplash.com/photo-1551028719-00167b16eac5?q=80&w=600&auto=format&fit=crop)", ukuran:["M","L","XL","XXL"], warna:[["Hitam","#222"],["Olive","#6B6E4E"]], deskripsi:"Jaket bomber dengan lapisan dalam hangat, ritsleting berkualitas dan saku fungsional untuk gaya urban.", tag:"Baru"},
  {id:10, nama:"Celana Chino Slim", kategori:"pria", sub:"Celana", harga:185000,
  gambar:"img/CelanaSlim.jpg", ukuran:["S","M","L","XL"], warna:[["Khaki","#BBA875"],["Hitam","#222"],["Navy","#22304A"]], deskripsi:"Celana chino slim-fit dengan bahan stretch ringan, nyaman dipakai kerja maupun santai.", tag:null},
  {id:11, nama:"Hoodie Basic Pria", kategori:"pria", sub:"Hoodie", harga:210000,
  gambar:"img/Hoodie.jpg", ukuran:["S","M","L","XL","XXL"], warna:[["Hitam","#222"],["Abu-abu","#8C8A86"],["Maroon","#6E2E33"]], deskripsi:"Hoodie dengan fleece tebal di bagian dalam, hangat dan nyaman untuk cuaca dingin maupun gaya kasual harian.", tag:"Diskon"},
  {id:12, nama:"Sepatu Sneakers Canvas", kategori:"pria", sub:"Sepatu", harga:275000,
  gambar:"https://images.unsplash.com/photo-1549298916-b41d501d3772?q=80&w=600&auto=format&fit=crop](https://images.unsplash.com/photo-1549298916-b41d501d3772?q=80&w=600&auto=format&fit=crop)", ukuran:["39","40","41","42","43","44"], warna:[["Putih","#FAFAFA"],["Hitam","#222"]], deskripsi:"Sneakers canvas dengan sol karet anti-slip, ringan dan cocok dipadukan dengan berbagai outfit kasual.", tag:null},
];

const SHIPPING_COST = 15000;

/* ============ STATE ============ */
let state = {
  page: 'home',
  currentProduct: null,
  selectedSize: null,
  selectedColorIdx: 0,
  qty: 1,
  thumbIdx: 0,
  cart: [], // {productId, size, color, qty}
  filter: 'semua'
};

const fmt = (n) => 'Rp' + n.toLocaleString('id-ID');

/* ============ SVG PLACEHOLDER ART ============ */
function productSVG(p, big=false){
  const palette = ['#EFEAE2','#E3DACB','#D8CDBB'];
  const seed = p.id % 3;
  return `<svg viewBox="0 0 300 380" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid slice">
    <rect width="300" height="380" fill="${palette[seed]}"/>
    <g opacity="0.55">
      <path d="M150 60 C 110 70, 90 110, 95 160 L 80 320 L 220 320 L 205 160 C 210 110, 190 70, 150 60 Z" fill="${p.warna[0][1]}" opacity="0.5"/>
      <circle cx="150" cy="48" r="20" fill="${p.warna[0][1]}" opacity="0.45"/>
    </g>
    <text x="150" y="355" text-anchor="middle" font-family="Inter, sans-serif" font-size="11" letter-spacing="1.5" fill="#8A8378" font-weight="600">${p.sub.toUpperCase()}</text>
  </svg>`;
}

/* ============ ROUTER ============ */
function navigate(e, page){
  if(e) e.preventDefault();
  state.page = page;
  state.filter = 'semua';
  document.getElementById('mainNav').classList.remove('open');
  document.querySelectorAll('.nav-link').forEach(a=>a.classList.toggle('active', a.dataset.page===page));
  window.scrollTo({top:0, behavior:'smooth'});
  render();
}
function goHome(e){ navigate(e,'home'); }
function openProduct(id){
  state.currentProduct = PRODUCTS.find(p=>p.id===id);
  state.selectedSize = null;
  state.selectedColorIdx = 0;
  state.qty = 1;
  state.thumbIdx = 0;
  state.page = 'detail';
  document.querySelectorAll('.nav-link').forEach(a=>a.classList.remove('active'));
  window.scrollTo({top:0, behavior:'smooth'});
  render();
}

document.getElementById('mobileToggle').addEventListener('click', ()=>{
  document.getElementById('mainNav').classList.toggle('open');
});

/* ============ CART LOGIC ============ */
function cartKey(productId, size, color){ return productId+'|'+size+'|'+color; }

function addToCart(product, size, color, qty){
  if(!size){ showToast('Pilih ukuran terlebih dahulu', true); return; }
  const key = cartKey(product.id, size, color);
  const existing = state.cart.find(i=>cartKey(i.productId,i.size,i.color)===key);
  if(existing){ existing.qty += qty; }
  else{ state.cart.push({productId:product.id, size, color, qty}); }
  updateCartCount();
  showToast(`${product.nama} ditambahkan ke keranjang`);
}

function updateCartCount(){
  const count = state.cart.reduce((s,i)=>s+i.qty,0);
  const el = document.getElementById('cartCount');
  el.textContent = count;
  el.classList.toggle('hide', count===0);
}

function cartTotal(){
  return state.cart.reduce((sum,item)=>{
    const p = PRODUCTS.find(pr=>pr.id===item.productId);
    return sum + p.harga*item.qty;
  },0);
}

function changeCartQty(idx, delta){
  state.cart[idx].qty += delta;
  if(state.cart[idx].qty<=0) state.cart.splice(idx,1);
  updateCartCount();
  renderCartDrawer();
}
function removeCartItem(idx){
  state.cart.splice(idx,1);
  updateCartCount();
  renderCartDrawer();
}

function openCart(){
  renderCartDrawer();
  document.getElementById('cartDrawer').classList.add('show');
  document.getElementById('overlay').classList.add('show');
}
function closeCart(){
  document.getElementById('cartDrawer').classList.remove('show');
  document.getElementById('overlay').classList.remove('show');
}
function closeAllOverlays(){ closeCart(); }

function renderCartDrawer(){
  const body = document.getElementById('cartBody');
  const foot = document.getElementById('cartFoot');
  if(state.cart.length===0){
    body.innerHTML = `<div class="empty-cart">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M6 6h15l-1.5 9h-12L6 6Z"/><path d="M6 6L4.5 2H2"/><circle cx="9" cy="20" r="1"/><circle cx="18" cy="20" r="1"/></svg>
      <p>Keranjang Anda masih kosong.</p>
    </div>`;
    foot.innerHTML = `<button class="btn-primary" style="width:100%" onclick="closeCart()">Lanjut Belanja</button>`;
    return;
  }
  body.innerHTML = state.cart.map((item,idx)=>{
    const p = PRODUCTS.find(pr=>pr.id===item.productId);
    return `<div class="cart-item">
      <div class="cart-item-img">${productSVG(p)}</div>
      <div class="cart-item-info">
        <div class="cart-item-name">${p.nama}</div>
        <div class="cart-item-meta">Ukuran ${item.size} · ${item.color}</div>
        <div class="cart-item-row">
          <div class="cart-item-qty">
            <button onclick="changeCartQty(${idx},-1)" aria-label="Kurangi">−</button>
            <span>${item.qty}</span>
            <button onclick="changeCartQty(${idx},1)" aria-label="Tambah">+</button>
          </div>
          <span class="cart-item-price">${fmt(p.harga*item.qty)}</span>
        </div>
        <button class="cart-item-remove" onclick="removeCartItem(${idx})">Hapus</button>
      </div>
    </div>`;
  }).join('');
  foot.innerHTML = `
    <div class="drawer-total-row"><span>Total</span><strong>${fmt(cartTotal())}</strong></div>
    <button class="btn-primary" style="width:100%" onclick="goCheckout()">Checkout</button>
  `;
}

function goCheckout(){
  if(state.cart.length===0){ showToast('Keranjang masih kosong', true); return; }
  closeCart();
  state.page = 'checkout';
  window.scrollTo({top:0,behavior:'smooth'});
  render();
}

/* ============ TOAST ============ */
function showToast(msg, isWarn=false){
  const t = document.getElementById('toast');
  document.getElementById('toastMsg').textContent = msg;
  t.querySelector('.dot').style.background = isWarn ? '#b14545' : 'var(--pine)';
  t.classList.add('show');
  clearTimeout(window._toastTimer);
  window._toastTimer = setTimeout(()=>t.classList.remove('show'), 2400);
}

/* ============ RENDER: HOME ============ */
function renderHome(){
  const featured = PRODUCTS.slice(0,4);
  return `
  <section class="hero view">
    <div>
      <div class="hero-eyebrow">Koleksi Musim Ini</div>
      <h1>Gaya yang<br><em>bercerita</em><br>tentang Anda.</h1>
      <p>Koleksi pakaian wanita dan pria dengan material premium dan potongan yang dirancang untuk kenyamanan sehari-hari.</p>
      <div class="hero-ctas">
        <a class="btn-primary" href="#" onclick="navigate(event,'wanita')">Belanja Wanita</a>
        <a class="btn-ghost" href="#" onclick="navigate(event,'pria')">Belanja Pria</a>
      </div>
    </div>
    
    <div class="hero-visual">
      <svg viewBox="0 0 400 480" xmlns="http://www.w3.org/2000/svg">
        <div class="hero-visual">
    <img src="https://images.unsplash.com/photo-1558769132-cb1aea458c5e?q=80&w=600&auto=format&fit=crop" alt="Hero Image">
      </svg>
      <div class="frame-label">
        <span>AURIC Lookbook</span>
        <span style="color:var(--gold-deep); font-weight:700;">2026</span>
      </div>
    </div>
  </section>

  <section class="section view">
    <div class="section-head">
      <div>
        <div class="section-tag">Pilih Fashion Anda</div>
        <h2>Produk Favorit</h2>
      </div>
      <p class="section-sub">Dipilih langsung dari koleksi wanita dan pria yang paling banyak diminati pelanggan kami.</p>
    </div>
    <div class="grid">
      ${featured.map(p=>productCard(p)).join('')}
    </div>
  </section>

  <section class="section view" style="padding-top:0;">
    <div class="section-head">
      <div>
        <div class="section-tag">Jelajahi</div>
        <h2>Kategori</h2>
      </div>
    </div>
    <div class="grid" style="grid-template-columns:1fr 1fr;">
      ${categoryBanner('wanita','Fashion Wanita','Dress · Blouse · Kemeja · Rok · Celana')}
      ${categoryBanner('pria','Fashion Pria','Kemeja · Kaos · Jaket · Celana · Hoodie · Sepatu')}
    </div>
  </section>
  `;
}
function categoryBanner(key, title, sub){
    // Menentukan link gambar otomatis berdasarkan kategori (key)
    let urlGambar = (key === 'wanita') 
        ? 'https://images.unsplash.com/photo-1595777457583-95e059d581b8?q=80&w=600&auto=format&fit=crop' 
        : 'https://images.unsplash.com/photo-1617137968427-85924c800a22?q=80&w=600&auto=format&fit=crop';

    return `<a href="#" onclick="navigate(event, '${key}')" class="category-card" style="position:relative; display:block; overflow:hidden; border-radius:12px; height:250px;">
        <img src="${urlGambar}" alt="${title}" style="width:100%; height:100%; object-fit:cover; position:absolute; top:0; left:0; z-index:1;">
        <div class="category-overlay" style="position:absolute; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.4); z-index:2;"></div>
        <div style="position:relative; z-index:3; padding:20px; color:#ffffff;">
            <h3 style="font-weight:600; font-size:1.5rem; margin-bottom:5px;">${title}</h3>
            <p style="font-size:0.85rem; opacity:0.8; margin:0;">${sub}</p>
        </div>
    </a>`
  }
  
  function productCard(p){
    // Menggunakan gambar dari data produk, jika tidak ada pakai gambar kosong/default
    let fotoProduk = p.gambar ? p.gambar : 'https://images.unsplash.com/photo-1595777457583-95e059d581b8?q=80&w=600&auto=format&fit=crop';

    return `<div class="card" onclick="openProduct(${p.id})">
        <div class="card-img" style="overflow:hidden; height:350px;">
            <img src="${fotoProduk}" alt="${p.nama}" style="width: 100%; height: 100%; object-fit: cover;">
            ${p.tag ? `<span class="card-tag">${p.tag}</span>` : ''}
            <div class="card-quick">
                <span class="quick-add" onclick="event.stopPropagation(); addToCart(${p.id})">tambah</span>
            </div>
        </div>
        <div class="card-name">${p.nama}</div>
        <div class="card-price">${fmt(p.harga)}</div>
    </div>`;
}



/* ============ RENDER: CATEGORY PAGE ============ */
function productCard(p) {
    return `
    <div class="product-card" onclick="openProduct(${p.id})" style="cursor: pointer; background: #fff; border-radius: 8px; overflow: hidden; box-shadow: 0 2px 5px rgba(0,0,0,0.05); transition: transform 0.2s;">
        <div class="product-img-wrapper" style="height: 320px; overflow: hidden; position: relative;">
            <img src="${p.gambar}" alt="${p.nama}" class="product-img" style="width: 100%; height: 100%; object-fit: cover;">
            ${p.tag ? `<span class="badge" style="position: absolute; top: 10px; left: 10px; background: #b8860b; color: #fff; padding: 4px 8px; font-size: 12px; font-weight: bold; border-radius: 4px;">${p.tag}</span>` : ''}
        </div>
        <div class="product-info" style="padding: 15px; text-align: left;">
            <h3 style="margin: 0 0 8px 0; font-size: 16px; color: #333; font-weight: 500;">${p.nama}</h3>
            <div class="price" style="font-weight: bold; color: #111; font-size: 15px;">${fmt(p.harga)}</div>
        </div>
    </div>`;
}
function renderCategory(kategori){
  const title = kategori==='wanita' ? 'Fashion Wanita' : 'Fashion Pria';
  const subs = [...new Set(PRODUCTS.filter(p=>p.kategori===kategori).map(p=>p.sub))];
  const list = PRODUCTS.filter(p=>p.kategori===kategori && (state.filter==='semua' || p.sub===state.filter));
  return `
  <section class="section view">
    <div class="section-head">
      <div>
        <div class="section-tag">${kategori==='wanita'?'👗':'👔'} Koleksi</div>
        <h2>${title}</h2>
      </div>
      <p class="section-sub">${list.length} produk tersedia dalam kategori ini.</p>
    </div>
    <div class="filters">
      <button class="filter-pill ${state.filter==='semua'?'active':''}" onclick="setFilter('semua')">Semua</button>
      ${subs.map(s=>`<button class="filter-pill ${state.filter===s?'active':''}" onclick="setFilter('${s}')">${s}</button>`).join('')}
    </div>
    <div class="grid">
      ${list.map(p=>productCard(p)).join('')}
    </div>
  </section>`;
}

function setFilter(f){ state.filter = f; render(); }

/* ============ RENDER: PRODUCT DETAIL ============ */
function renderDetail(){
    const p = state.currentProduct;
    const catLabel = p.kategori==='wanita'?'Fashion Wanita':'Fashion Pria';
    return `
    <div class="pdp view">
        <div>
            <div class="pdp-gallery-main" style="height: 400px; overflow: hidden; border-radius: 8px;">
                <img src="${p.gambar ? p.gambar : 'blouse-satin.jpg.jpg'}" alt="${p.nama}" style="width: 100%; height: 100%; object-fit: cover;">
            </div>
        </div>
        <div>
            <div class="breadcrumb">
                <a href="#" onclick="navigate(event, 'home')">Beranda</a> / 
                <a href="#" onclick="navigate(event, '${p.kategori}')">${catLabel}</a> / 
                ${p.nama}
            </div>
            <h1>${p.nama}</h1>
            <div class="pdp-price">${fmt(p.harga)}</div>
            <p class="pdp-desc">${p.deskripsi || 'Deskripsi produk premium.'}</p>
      <div class="option-block">
        <div class="option-label">Pilih Warna <span class="sel-val">${p.warna[state.selectedColorIdx][0]}</span></div>
        <div class="color-row">
          ${p.warna.map((w,i)=>`<button class="color-opt ${i===state.selectedColorIdx?'active':''}" onclick="state.selectedColorIdx=${i}; render()" aria-label="${w[0]}"><span class="color-swatch" style="background:${w[1]}"></span></button>`).join('')}
        </div>
        </div>
  <div class="option-block" style="margin-bottom: 20px;">
                <div class="option-label" style="margin-bottom: 10px;">Pilih Ukuran: <span class="selected-value" style="font-weight: bold; color: #b8860b;">${state.selectedSize || 'Belum dipilih'}</span></div>
                <div class="size-row" style="display: flex; gap: 12px; flex-wrap: wrap;">
                    ${p.ukuran.map(sz => `
                        <button class="size-btn ${state.selectedSize === sz ? 'active' : ''}" onclick="state.selectedSize='${sz}'; render();" style="padding: 8px 16px; min-width: 45px; cursor: pointer; border: 1px solid #ccc; background: #fff; transition: all 0.2s;">${sz}</button>
                    `).join('')}
                </div>
            </div>
      <div class="option-block">
        <div class="option-label">Jumlah Pembelian</div>
        <div class="qty-row">
          <button class="qty-btn" onclick="changeQty(-1)" aria-label="Kurangi jumlah">−</button>
          <span class="qty-val">${state.qty}</span>
          <button class="qty-btn" onclick="changeQty(1)" aria-label="Tambah jumlah">+</button>
        </div>
      </div>

      <div class="stock-note"><span class="stock-dot"></span> Stok tersedia · siap dikirim 1-2 hari kerja</div>

      <div class="pdp-actions">
        <button class="btn-ghost" onclick="handleAddToCart()">Tambah ke Keranjang</button>
        <button class="btn-primary" onclick="handleBuyNow()">Beli Sekarang</button>
      </div>
    </div>
  </div>`;
}
function selectSize(s){ state.selectedSize = s; render(); }
function changeQty(delta){
  state.qty = Math.max(1, state.qty+delta);
  render();
}
function handleAddToCart(){
  const p = state.currentProduct;
  addToCart(p, state.selectedSize, p.warna[state.selectedColorIdx][0], state.qty);
}
function handleBuyNow(){
  const p = state.currentProduct;
  if(!state.selectedSize){ showToast('Pilih ukuran terlebih dahulu', true); return; }
  addToCart(p, state.selectedSize, p.warna[state.selectedColorIdx][0], state.qty);
  goCheckout();
}

/* ============ RENDER: CHECKOUT ============ */
let checkoutPayment = 'transfer';
let checkoutBank = 'BCA';
let checkoutEwallet = 'Dana';

function renderCheckout(){
  const total = cartTotal();
  const grandTotal = total + SHIPPING_COST;
  return `
  <div class="checkout-wrap view">
    <div class="section-head" style="border-bottom:none; margin-bottom:0;">
      <div>
        <div class="section-tag">🏠 Langkah Terakhir</div>
        <h2>Checkout</h2>
      </div>
    </div>

    <div class="checkout-grid">
      <div>
        <h3 style="font-size:16px; font-weight:600; margin:28px 0 18px;">Data Pengiriman</h3>
        <div class="field-group" id="fg-nama">
          <label class="field-label">Nama Penerima</label>
          <input class="field-input" id="inp-nama" placeholder="Masukkan nama lengkap">
          <div class="field-error">Nama penerima wajib diisi.</div>
        </div>
        <div class="field-group" id="fg-hp">
          <label class="field-label">Nomor HP</label>
          <input class="field-input" id="inp-hp" placeholder="08xx-xxxx-xxxx" inputmode="numeric">
          <div class="field-error">Nomor HP wajib diisi dengan benar.</div>
        </div>
        <div class="field-group" id="fg-alamat">
          <label class="field-label">Alamat Lengkap</label>
          <textarea class="field-textarea" id="inp-alamat" placeholder="Nama jalan, nomor rumah, RT/RW, patokan"></textarea>
          <div class="field-error">Alamat lengkap wajib diisi.</div>
        </div>
        <div class="field-row">
          <div class="field-group">
            <label class="field-label">Provinsi</label>
            <select class="field-select" id="inp-provinsi">
              <option>Sumatera Utara</option><option>DKI Jakarta</option><option>Jawa Barat</option><option>Jawa Timur</option><option>Bali</option>
            </select>
          </div>
          <div class="field-group">
            <label class="field-label">Kabupaten/Kota</label>
            <select class="field-select" id="inp-kota">
              <option>Medan</option><option>Deli Serdang</option><option>Binjai</option>
            </select>
          </div>
          <div class="field-group">
            <label class="field-label">Kecamatan</label>
            <select class="field-select" id="inp-kecamatan">
              <option>Medan Baru</option><option>Medan Petisah</option><option>Medan Selayang</option>
            </select>
          </div>
        </div>
        <div class="field-group" style="max-width:200px;">
          <label class="field-label">Kode Pos</label>
          <input class="field-input" id="inp-kodepos" placeholder="20xxx" inputmode="numeric">
        </div>

        <h3 style="font-size:16px; font-weight:600; margin:32px 0 18px;">💳 Metode Pembayaran</h3>
        <div class="pay-options">
          <div class="pay-card ${checkoutPayment==='transfer'?'active':''}" onclick="setPayment('transfer')">
            <div class="pay-card-head"><span class="pay-radio"></span> Transfer Bank</div>
            <div class="pay-sub">Transfer manual, konfirmasi otomatis setelah pembayaran.</div>
            ${checkoutPayment==='transfer' ? `<div class="pay-banks">
              ${['BCA','BRI','BNI','Mandiri'].map(b=>`<button class="bank-chip ${checkoutBank===b?'active':''}" onclick="event.stopPropagation(); setBank('${b}')">${b}</button>`).join('')}
            </div>` : ''}
          </div>
          <div class="pay-card ${checkoutPayment==='ewallet'?'active':''}" onclick="setPayment('ewallet')">
            <div class="pay-card-head"><span class="pay-radio"></span> E-Wallet</div>
            <div class="pay-sub">Bayar instan lewat dompet digital pilihan Anda.</div>
            ${checkoutPayment==='ewallet' ? `<div class="pay-banks">
              ${['Dana','OVO','GoPay','ShopeePay'].map(b=>`<button class="bank-chip ${checkoutEwallet===b?'active':''}" onclick="event.stopPropagation(); setEwallet('${b}')">${b}</button>`).join('')}
            </div>` : ''}
          </div>
          <div class="pay-card ${checkoutPayment==='cod'?'active':''}" onclick="setPayment('cod')">
            <div class="pay-card-head"><span class="pay-radio"></span> COD (Cash On Delivery)</div>
            <div class="pay-sub">Bayar tunai di tempat saat pesanan tiba.</div>
          </div>
        </div>
      </div>

      <div class="summary-box">
        <h3>🧾 Ringkasan Pesanan</h3>
        ${state.cart.map(item=>{
          const p = PRODUCTS.find(pr=>pr.id===item.productId);
          return `<div class="summary-item">
            <div class="summary-item-img">${productSVG(p)}</div>
            <div class="summary-item-info">
              <div class="summary-item-name">${p.nama}</div>
              <div class="summary-item-meta">${item.size} · ${item.color} · ${item.qty}x</div>
            </div>
            <div class="summary-item-price">${fmt(p.harga*item.qty)}</div>
          </div>`;
        }).join('')}
        <div class="summary-row"><span>Subtotal</span><span>${fmt(total)}</span></div>
        <div class="summary-row"><span>Ongkir</span><span>${fmt(SHIPPING_COST)}</span></div>
        <div class="summary-row total"><span>Total Bayar</span><span>${fmt(grandTotal)}</span></div>
        <button class="btn-primary order-btn" onclick="submitOrder()">✅ Pesan Sekarang</button>
        <div class="secure-note">🔒 Transaksi demo — tidak ada data nyata yang dikirim</div>
      </div>
    </div>
  </div>`;
}
function setPayment(p){ checkoutPayment = p; render(); }
function setBank(b){ checkoutBank = b; render(); }
function setEwallet(e){ checkoutEwallet = e; render(); }

function submitOrder(){
  const fields = [
    {id:'nama', el:'inp-nama', check:v=>v.trim().length>1},
    {id:'hp', el:'inp-hp', check:v=>v.trim().length>=8},
    {id:'alamat', el:'inp-alamat', check:v=>v.trim().length>4},
  ];
  let valid = true;
  let values = {};
  fields.forEach(f=>{
    const input = document.getElementById(f.el);
    const v = input.value;
    values[f.id]=v;
    const group = document.getElementById('fg-'+f.id);
    if(!f.check(v)){ group.classList.add('error'); valid=false; }
    else{ group.classList.remove('error'); }
  });
  if(!valid){ showToast('Lengkapi data pengiriman terlebih dahulu', true); return; }

  const orderData = {
    nama: values.nama,
    hp: values.hp,
    alamat: values.alamat,
    metode: checkoutPayment==='transfer' ? `Transfer Bank ${checkoutBank}` : checkoutPayment==='ewallet' ? `E-Wallet ${checkoutEwallet}` : 'COD',
    total: cartTotal()+SHIPPING_COST,
    items: state.cart.length,
    orderId: 'MA' + Date.now().toString().slice(-8)
  };
  state.lastOrder = orderData;
  state.cart = [];
  updateCartCount();
  state.page = 'success';
  window.scrollTo({top:0,behavior:'smooth'});
  render();
}

/* ============ RENDER: SUCCESS ============ */
function renderSuccess(){
  const o = state.lastOrder;
  if(!o){ return renderHome(); }
  return `
  <div class="success-wrap view">
    <div class="success-icon">
      <svg width="34" height="34" viewBox="0 0 24 24" fill="none" stroke="#2D5A4A" stroke-width="2.2"><path d="M20 6L9 17l-5-5"/></svg>
    </div>
    <h2>Pesanan Berhasil Dibuat</h2>
    <p>Terima kasih, ${o.nama}. Pesanan Anda dengan nomor <strong>${o.orderId}</strong> sedang kami proses dan akan segera dikirim ke alamat Anda.</p>
    <div class="receipt">
      <div class="receipt-row"><span>Nomor Pesanan</span><span>${o.orderId}</span></div>
      <div class="receipt-row"><span>Penerima</span><span>${o.nama}</span></div>
      <div class="receipt-row"><span>Nomor HP</span><span>${o.hp}</span></div>
      <div class="receipt-row"><span>Metode Pembayaran</span><span>${o.metode}</span></div>
      <div class="receipt-row"><span>Total Pembayaran</span><span>${fmt(o.total)}</span></div>
    </div>
    <a class="btn-primary" href="#" onclick="navigate(event,'home')">Kembali Berbelanja</a>
  </div>`;
}

/* ============ MASTER RENDER ============ */
function render(){
  const app = document.getElementById('app');
  if(state.page==='home') app.innerHTML = renderHome();
  else if(state.page==='wanita') app.innerHTML = renderCategory('wanita');
  else if(state.page==='pria') app.innerHTML = renderCategory('pria');
  else if(state.page==='detail') app.innerHTML = renderDetail();
  else if(state.page==='checkout') app.innerHTML = renderCheckout();
  else if(state.page==='success') app.innerHTML = renderSuccess();
}

/* init */
document.querySelectorAll('.nav-link').forEach(a=>a.classList.toggle('active', a.dataset.page==='home'));
render();
</script>
</body>
</html>
