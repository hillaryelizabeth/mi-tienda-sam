# mi-tienda-sam
Tienda online de fragancias y ropa de cama - Mi Tienda Sam
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Mi Tienda Sam</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@500;600;700&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg: #fffaf7;
      --panel: #fff;
      --soft: #f7efe9;
      --primary: #6f3d2e;
      --primary-dark: #4d261d;
      --accent: #d8b79d;
      --text: #271c1a;
      --muted: #6d5b56;
      --success: #7a9d6f;
      --shadow: 0 18px 35px rgba(98, 54, 44, 0.14);
      --radius: 22px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      font-family: 'Inter', sans-serif;
      background: var(--bg);
      color: var(--text);
      line-height: 1.6;
    }

    img { max-width: 100%; display: block; }
    a { text-decoration: none; color: inherit; }
    button { font: inherit; cursor: pointer; }

    .container {
      width: min(1200px, calc(100% - 32px));
      margin: 0 auto;
    }

    .topbar {
      background: rgba(255,255,255,0.8);
      backdrop-filter: blur(12px);
      position: sticky;
      top: 0;
      z-index: 1000;
      border-bottom: 1px solid rgba(111,61,46,0.08);
    }

    .nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      min-height: 72px;
      gap: 22px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      font-weight: 700;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      font-size: 0.82rem;
    }

    .brand-mark {
      width: 42px;
      height: 42px;
      border-radius: 50%;
      display: grid;
      place-items: center;
      background: linear-gradient(145deg, var(--primary), #b77960);
      color: white;
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.6rem;
      font-weight: 700;
      box-shadow: var(--shadow);
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 24px;
      color: var(--muted);
      font-size: 0.95rem;
    }

    .nav-links a:hover { color: var(--primary); }

    .nav-actions {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 14px 22px;
      border-radius: 999px;
      border: 1px solid transparent;
      transition: 0.25s ease;
      font-weight: 600;
      letter-spacing: 0.02em;
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--primary), #bf7d5e);
      color: white;
      box-shadow: 0 14px 28px rgba(111,61,46,0.28);
    }

    .btn-primary:hover { transform: translateY(-2px); }

    .btn-light {
      background: rgba(255,255,255,0.9);
      border-color: rgba(111,61,46,0.15);
      color: var(--primary-dark);
    }

    .hero {
      padding: 54px 0 30px;
      background:
        radial-gradient(circle at top right, rgba(216,183,157,0.35), transparent 30%),
        linear-gradient(180deg, #fffaf7 0%, #fff2ea 100%);
    }

    .hero-grid {
      display: grid;
      grid-template-columns: 1.08fr 0.92fr;
      gap: 38px;
      align-items: center;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(111,61,46,0.08);
      color: var(--primary);
      padding: 8px 14px;
      border-radius: 999px;
      font-weight: 600;
      font-size: 0.8rem;
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }

    h1, h2, h3 {
      margin: 0;
      font-family: 'Cormorant Garamond', serif;
      line-height: 0.98;
      letter-spacing: -0.02em;
    }

    .hero h1 {
      font-size: clamp(3rem, 5vw, 6rem);
      margin-top: 18px;
      color: var(--primary-dark);
    }

    .hero p {
      font-size: 1.08rem;
      color: var(--muted);
      margin: 18px 0 30px;
      max-width: 600px;
    }

    .hero-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 14px;
      margin-bottom: 30px;
    }

    .stats {
      display: grid;
      grid-template-columns: repeat(3, minmax(110px, 1fr));
      gap: 18px;
      max-width: 520px;
    }

    .stat {
      background: rgba(255,255,255,0.7);
      border: 1px solid rgba(111,61,46,0.08);
      border-radius: 18px;
      padding: 18px 16px;
      box-shadow: 0 10px 25px rgba(42, 25, 23, 0.04);
    }

    .stat strong {
      display: block;
      font-size: 1.6rem;
      color: var(--primary-dark);
      font-family: 'Cormorant Garamond', serif;
    }

    .stat span {
      color: var(--muted);
      font-size: 0.82rem;
    }

    .hero-visual {
      position: relative;
      min-height: 520px;
      display: grid;
      place-items: center;
    }

    .visual-card {
      position: absolute;
      display: grid;
      place-items: center;
      border-radius: 30px;
      overflow: hidden;
      box-shadow: var(--shadow);
      background: #f5e7dd;
      border: 10px solid rgba(255,255,255,0.7);
    }

    .visual-card.main {
      width: min(78%, 480px);
      height: 500px;
      right: 15%;
      top: 10px;
      background:
        linear-gradient(180deg, rgba(0,0,0,0.05), rgba(0,0,0,0.1)),
        url('https://images.unsplash.com/photo-1528740561666-dc2479dc08ab?auto=format&fit=crop&w=900&q=80') center/cover no-repeat;
    }

    .visual-card.small {
      width: 160px;
      height: 200px;
      left: 3%;
      bottom: 40px;
      background:
        linear-gradient(180deg, rgba(0,0,0,0.1), rgba(0,0,0,0.05)),
        url('https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&w=700&q=80') center/cover no-repeat;
    }

    .floating-badge {
      position: absolute;
      background: rgba(255,255,255,0.92);
      border-radius: 18px;
      padding: 16px 18px;
      box-shadow: var(--shadow);
      border: 1px solid rgba(111,61,46,0.07);
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 12px;
      color: var(--primary-dark);
      right: 4%;
      top: 24%;
    }

    .badge-icon {
      width: 42px;
      height: 42px;
      border-radius: 14px;
      display: grid;
      place-items: center;
      background: linear-gradient(135deg, #f9dcc8, #e2bda0);
      color: var(--primary-dark);
      font-size: 1.2rem;
    }

    section {
      padding: 88px 0;
    }

    .section-header {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 18px;
      margin-bottom: 28px;
    }

    .section-header h2 {
      font-size: clamp(2.5rem, 4vw, 4rem);
      color: var(--primary-dark);
    }

    .section-header p {
      color: var(--muted);
      margin: 0;
      max-width: 420px;
    }

    .product-filters {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin-bottom: 22px;
    }

    .filter-btn {
      background: #fff;
      border: 1px solid rgba(111,61,46,0.12);
      color: var(--muted);
      padding: 12px 16px;
      border-radius: 999px;
      font-weight: 600;
      transition: 0.25s ease;
    }

    .filter-btn.active {
      background: var(--primary);
      color: white;
      border-color: var(--primary);
      box-shadow: 0 14px 24px rgba(111,61,46,0.18);
    }

    .products-grid {
      display: grid;
      grid-template-columns: repeat(4, minmax(220px, 1fr));
      gap: 22px;
    }

    .product-card {
      background: var(--panel);
      border-radius: var(--radius);
      overflow: hidden;
      border: 1px solid rgba(111,61,46,0.08);
      box-shadow: 0 12px 24px rgba(25, 18, 17, 0.04);
      transition: 0.35s ease;
    }

    .product-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 18px 32px rgba(25, 18, 17, 0.08);
    }

    .product-image {
      height: 260px;
      background-size: cover;
      background-position: center;
      position: relative;
    }

    .product-tag {
      position: absolute;
      top: 14px;
      left: 14px;
      background: rgba(255,255,255,0.9);
      color: var(--primary);
      padding: 8px 10px;
      border-radius: 999px;
      font-size: 0.72rem;
      font-weight: 700;
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }

    .product-body {
      padding: 18px;
    }

    .product-top {
      display: flex;
      justify-content: space-between;
      gap: 10px;
      align-items: start;
      margin-bottom: 10px;
    }

    .product-name {
      font-size: 1.38rem;
      font-family: 'Cormorant Garamond', serif;
      color: var(--primary-dark);
      font-weight: 700;
    }

    .rating {
      color: #d89a3b;
      font-size: 0.75rem;
      letter-spacing: 0.05em;
    }

    .product-description {
      color: var(--muted);
      font-size: 0.95rem;
      margin: 8px 0 16px;
      min-height: 74px;
    }

    .notes {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 16px;
    }

    .note {
      background: var(--soft);
      color: var(--primary);
      border-radius: 999px;
      font-size: 0.72rem;
      padding: 6px 10px;
      font-weight: 600;
    }

    .product-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 10px;
      margin-top: auto;
    }

    .price {
      font-size: 1.5rem;
      font-weight: 700;
      color: var(--primary-dark);
    }

    .add-cart {
      background: var(--primary);
      color: white;
      border: none;
      border-radius: 12px;
      padding: 10px 14px;
      font-weight: 600;
    }

    .add-cart:hover {
      background: var(--primary-dark);
    }

    .bedroom-section {
      background: linear-gradient(180deg, rgba(233,220,212,0.5), rgba(255,255,255,0.0));
    }

    .bedding-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(240px, 1fr));
      gap: 22px;
      margin-top: 30px;
    }

    .bedding-card {
      background: white;
      border-radius: 26px;
      overflow: hidden;
      border: 1px solid rgba(111,61,46,0.08);
      box-shadow: 0 12px 24px rgba(25,18,17,0.04);
    }

    .bedding-image {
      height: 240px;
      background-size: cover;
      background-position: center;
    }

    .bedding-body {
      padding: 22px;
    }

    .bedding-body h3 {
      font-size: 2.1rem;
      color: var(--primary-dark);
      margin-bottom: 8px;
    }

    .bedding-body p {
      color: var(--muted);
      margin: 0 0 18px;
    }

    .design-swatches {
      display: flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 18px;
      flex-wrap: wrap;
    }

    .swatch {
      width: 22px;
      height: 22px;
      border-radius: 50%;
      border: 2px solid white;
      box-shadow: 0 0 0 1px rgba(39,28,26,0.12);
    }

    .cta {
      background:
        linear-gradient(135deg, rgba(111,61,46,0.96), rgba(143,98,79,0.9)),
        url('https://images.unsplash.com/photo-1515377905703-c4788e51af15?auto=format&fit=crop&w=1200&q=80') center/cover no-repeat;
      border-radius: 32px;
      padding: 48px 42px;
      color: white;
      display: grid;
      grid-template-columns: 1.2fr 0.8fr;
      gap: 26px;
      align-items: center;
      box-shadow: var(--shadow);
    }

    .cta h2 {
      font-size: clamp(2.5rem, 4vw, 4rem);
      color: white;
      margin-bottom: 12px;
    }

    .cta p {
      color: rgba(255,255,255,0.82);
      margin: 0;
      font-size: 1.02rem;
    }

    .cta-actions {
      display: flex;
      justify-content: flex-end;
      flex-wrap: wrap;
      gap: 12px;
    }

    .whatsapp {
      background: #25D366;
      color: white;
      border: none;
      box-shadow: 0 16px 28px rgba(37, 211, 102, 0.22);
    }

    .footer {
      padding: 28px 0 48px;
      color: var(--muted);
      text-align: center;
    }

    .floating-whatsapp {
      position: fixed;
      right: 26px;
      bottom: 26px;
      width: 72px;
      height: 72px;
      border-radius: 50%;
      background: linear-gradient(135deg, #25D366, #1eb95f);
      display: grid;
      place-items: center;
      color: white;
      font-size: 2rem;
      box-shadow: 0 22px 40px rgba(37, 211, 102, 0.3);
      z-index: 1200;
      transition: 0.25s ease;
    }

    .floating-whatsapp:hover {
      transform: translateY(-4px) scale(1.03);
    }

    @media (max-width: 980px) {
      .hero-grid,
      .cta {
        grid-template-columns: 1fr;
      }

      .products-grid {
        grid-template-columns: repeat(2, minmax(220px, 1fr));
      }

      .bedding-grid {
        grid-template-columns: 1fr;
      }

      .cta-actions {
        justify-content: flex-start;
      }
    }

    @media (max-width: 700px) {
      .nav {
        flex-wrap: wrap;
        justify-content: center;
        padding: 16px 0;
      }

      .nav-links {
        flex-wrap: wrap;
        justify-content: center;
      }

      .products-grid {
        grid-template-columns: 1fr;
      }

      .stats {
        grid-template-columns: 1fr;
      }

      .section-header {
        display: block;
      }

      .hero p {
        max-width: none;
      }

      .floating-whatsapp {
        width: 62px;
        height: 62px;
        right: 18px;
        bottom: 18px;
      }
    }
  </style>
</head>
<body>
  <header class="topbar">
    <div class="container nav">
      <div class="brand">
        <div class="brand-mark">S</div>
        <span>Mi Tienda Sam</span>
      </div>

      <nav class="nav-links">
        <a href="#inicio">Inicio</a>
        <a href="#fragancias">Fragancias</a>
        <a href="#ropa">Ropa de cama</a>
        <a href="#nosotros">Nosotros</a>
      </nav>

      <div class="nav-actions">
        <a class="btn btn-light" href="#fragancias">Ver catálogo</a>
      </div>
    </div>
  </header>

  <main id="inicio">
    <section class="hero">
      <div class="container hero-grid">
        <div>
          <span class="eyebrow">perfumes · confort · estilo</span>
          <h1>Fragancias que enamoran y piezas que transforman tu hogar.</h1>
          <p>
            En Mi Tienda Sam encontrarás aromas sofisticados para cada momento y una colección exclusiva de ropa de cama con diseños elegantes, suaves y modernos para hacer de tu descanso una experiencia especial.
          </p>

          <div class="hero-actions">
            <a href="#fragancias" class="btn btn-primary">Explorar fragancias</a>
            <a href="#ropa" class="btn btn-light">Ver ropa de cama</a>
          </div>

          <div class="stats">
            <div class="stat">
              <strong>200+</strong>
              <span>Clientes felices</span>
            </div>
            <div class="stat">
              <strong>4.9/5</strong>
              <span>Calificación</span>
            </div>
            <div class="stat">
              <strong>24h</strong>
              <span>Entrega rápida</span>
            </div>
          </div>
        </div>

        <div class="hero-visual">
          <div class="visual-card main"></div>
          <div class="visual-card small"></div>

          <div class="floating-badge">
            <div class="badge-icon">✦</div>
            <div>
              <div style="font-size:0.8rem; color:var(--muted);">Colección</div>
              <strong>Exclusiva</strong>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="fragancias">
      <div class="container">
        <div class="section-header">
          <div>
            <span class="eyebrow">fragancias</span>
            <h2>Descubre tu aroma favorito</h2>
          </div>
          <p>Perfumes con intensidad, comodidad y personalidad para cada día, ocasión o estilo de vida.</p>
        </div>

        <div class="product-filters">
          <button class="filter-btn active" data-filter="all">Todo</button>
          <button class="filter-btn" data-filter="femenino">Femenino</button>
          <button class="filter-btn" data-filter="masculino">Masculino</button>
          <button class="filter-btn" data-filter="unisex">Unisex</button>
        </div>

        <div id="productGrid" class="products-grid"></div>
      </div>
    </section>

    <section id="ropa" class="bedroom-section">
      <div class="container">
        <div class="section-header">
          <div>
            <span class="eyebrow">ropa de cama</span>
            <h2>Diseños exclusivos para descansar mejor</h2>
          </div>
          <p>Edredones, sábanas y cobijas con acabados suaves, modernos y con estilo para transformar tu dormitorio.</p>
        </div>

        <div class="bedding-grid">
          <article class="bedding-card">
            <div class="bedding-image" style="background-image:url('https://images.unsplash.com/photo-1505693416388-ac5ce068fe85?auto=format&fit=crop&w=900&q=80');"></div>
            <div class="bedding-body">
              <h3>Edredones</h3>
              <p>Texturas suaves y estampados sofisticados para darle un toque elegante a tu habitación.</p>
              <div class="design-swatches">
                <span class="swatch" style="background:#d8c3ab;"></span>
                <span class="swatch" style="background:#9db2af;"></span>
                <span class="swatch" style="background:#bea59b;"></span>
                <span class="swatch" style="background:#d7d1c9;"></span>
              </div>
              <a href="https://wa.me/5215512345678?text=Hola%20Mi%20Tienda%20Sam%2C%20quiero%20ver%20la%20colecci%C3%B3n%20de%20edredones" class="btn btn-primary">Consultar diseño</a>
            </div>
          </article>

          <article class="bedding-card">
            <div class="bedding-image" style="background-image:url('https://images.unsplash.com/photo-1505693416388-ac5ce068fe85?auto=format&fit=crop&w=900&q=80');"></div>
            <div class="bedding-body">
              <h3>Sábanas</h3>
              <p>Hilos suaves, colores cálidos y diseños que combinan máxima comodidad con estilo contemporáneo.</p>
              <div class="design-swatches">
                <span class="swatch" style="background:#f3d8c7;"></span>
                <span class="swatch" style="background:#d0b9a6;"></span>
                <span class="swatch" style="background:#b4a598;"></span>
                <span class="swatch" style="background:#dfe3df;"></span>
              </div>
              <a href="https://wa.me/5215512345678?text=Hola%20Mi%20Tienda%20Sam%2C%20quiero%20ver%20la%20colecci%C3%B3n%20de%20s%C3%A1banas" class="btn btn-primary">Consultar diseño</a>
            </div>
          </article>

          <article class="bedding-card">
            <div class="bedding-image" style="background-image:url('https://images.unsplash.com/photo-1505693416388-ac5ce068fe85?auto=format&fit=crop&w=900&q=80');"></div>
            <div class="bedding-body">
              <h3>Cobijas</h3>
              <p>Prendas ligeras y acogedoras con estampados chic y texturas suaves para cada temporada.</p>
              <div class="design-swatches">
                <span class="swatch" style="background:#d8a18d;"></span>
                <span class="swatch" style="background:#b9c4bf;"></span>
                <span class="swatch" style="background:#e8d8c5;"></span>
                <span class="swatch" style="background:#8c6c5d;"></span>
              </div>
              <a href="https://wa.me/5215512345678?text=Hola%20Mi%20Tienda%20Sam%2C%20quiero%20ver%20la%20colecci%C3%B3n%20de%20cobijas" class="btn btn-primary">Consultar diseño</a>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section id="nosotros">
      <div class="container">
        <div class="cta">
          <div>
            <span class="eyebrow" style="background:rgba(255,255,255,0.15); color:#fff;">Mi Tienda Sam</span>
            <h2>Calidad, estilo y esencia en cada detalle.</h2>
            <p>Somos una tienda pensada para quienes buscan productos bonitos, auténticos y con personalidad. Aquí encuentras aromas inolvidables y piezas para tu hogar con un diseño que habla por sí mismo.</p>
          </div>

          <div class="cta-actions">
            <a href="https://wa.me/5215512345678?text=Hola%20Mi%20Tienda%20Sam%2C%20me%20gustar%C3%ADa%20hacer%20una%20compra" class="btn btn-primary whatsapp">WhatsApp</a>
            <a href="#fragancias" class="btn btn-light">Ver catálogo</a>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer class="footer">
    <div class="container">
      © 2026 Mi Tienda Sam · Todos los derechos reservados
    </div>
  </footer>

  <a class="floating-whatsapp" href="https://wa.me/5215512345678?text=Hola%20Mi%20Tienda%20Sam%2C%20quiero%20consultar%20catalogo" aria-label="WhatsApp">
    WhatsApp
  </a>

  <script>
    const fragrances = [
      {
        name: "Velvet Bloom",
        category: "femenino",
        tag: "Best seller",
        image: "https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&w=900&q=80",
        description: "Un aroma floral con notas de rosa, vainilla y sándalo ideal para un día elegante.",
        notes: ["Rosa", "Vainilla", "Sándalo"],
        price: "$420",
        rating: "★ ★ ★ ★ ★"
      },
      {
        name: "Noir Gold",
        category: "masculino",
        tag: "Premium",
        image: "https://images.unsplash.com/photo-1528740561666-dc2479dc08ab?auto=format&fit=crop&w=900&q=80",
        description: "Dinamismo y sofisticación con musk, ámbar y bergamota para un estilo intenso.",
        notes: ["Ámbar", "Bergamota", "Musk"],
        price: "$460",
        rating: "★ ★ ★ ★ ★"
      },
      {
        name: "Sakura Mist",
        category: "unisex",
        tag: "Fresh",
        image: "https://images.unsplash.com/photo-1594035910387-fea47794261f?auto=format&fit=crop&w=900&q=80",
        description: "Notas frutales y florales ligeras que equilibran frescura con una presencia elegante.",
        notes: ["Sakura", "Manzana", "Lima"],
        price: "$390",
        rating: "★ ★ ★ ★ ☆"
      },
      {
        name: "Amber Silk",
        category: "femenino",
        tag: "Noche",
        image: "https://images.unsplash.com/photo-1523293182086-7651a899d37f?auto=format&fit=crop&w=900&q=80",
        description: "Un perfume cálido y sensual con ámbar, jazmín y vainilla para una presencia memorable.",
        notes: ["Ámbar", "Jazmín", "Vainilla"],
        price: "$480",
        rating: "★ ★ ★ ★ ★"
      },
      {
        name: "Cedar Storm",
        category: "masculino",
        tag: "Nuevo",
        image: "https://images.unsplash.com/photo-1617897903246-719242758050?auto=format&fit=crop&w=900&q=80",
        description: "Notas de cedro, pino y tabaco con profundidad intensa para un estilo audaz.",
        notes: ["Cedro", "Pino", "Tabaco"],
        price: "$470",
        rating: "★ ★ ★ ★ ☆"
      },
      {
        name: "Citrus Muse",
        category: "unisex",
        tag: "Vital",
        image: "https://images.unsplash.com/photo-1523293182086-7651a899d37f?auto=format&fit=crop&w=900&q=80",
        description: "Refrescante y vibrante, con cítricos brillantes y notas verdes para despertar tus sentidos.",
        notes: ["Naranja", "Bambú", "Menta"],
        price: "$350",
        rating: "★ ★ ★ ★ ☆"
      },
      {
        name: "Rose Aura",
        category: "femenino",
        tag: "Clásico",
        image: "https://images.unsplash.com/photo-1528740561666-dc2479dc08ab?auto=format&fit=crop&w=900&q=80",
        description: "Floral chic con rosas, peonía y almizcle para una fragancia femenina y elegante.",
        notes: ["Rosa", "Peonía", "Almizcle"],
        price: "$410",
        rating: "★ ★ ★ ★ ★"
      },
      {
        name: "Midnight Echo",
        category: "unisex",
        tag: "Épico",
        image: "https://images.unsplash.com/photo-1541643600914-78b084683601?auto=format&fit=crop&w=900&q=80",
        description: "Una mezcla intensa de cacao, madera y especias que deja un recuerdo envolvente.",
        notes: ["Cacao", "Madera", "Especias"],
        price: "$500",
        rating: "★ ★ ★ ★ ★"
      }
    ];

    let activeFilter = 'all';

    const productGrid = document.getElementById('productGrid');

    function renderProducts() {
      const filtered = activeFilter === 'all'
        ? fragrances
        : fragrances.filter(item => item.category === activeFilter);

      productGrid.innerHTML = filtered.map(item => `
        <article class="product-card">
          <div class="product-image" style="background-image:url('${item.image}')">
            <span class="product-tag">${item.tag}</span>
          </div>
          <div class="product-body">
            <div class="product-top">
              <div class="product-name">${item.name}</div>
              <div class="rating">${item.rating}</div>
            </div>
            <div class="product-description">${item.description}</div>
            <div class="notes">
              ${item.notes.map(note => `<span class="note">${note}</span>`).join('')}
            </div>
            <div class="product-footer">
              <div class="price">${item.price}</div>
              <button class="add-cart" data-name="${item.name}">Añadir</button>
            </div>
          </div>
        </article>
      `).join('');

      document.querySelectorAll('.add-cart').forEach(btn => {
        btn.addEventListener('click', () => {
          const productName = btn.dataset.name;
          const whatsappLink = `https://wa.me/5215512345678?text=Hola%20Mi%20Tienda%20Sam%2C%20quiero%20comprar%20${encodeURIComponent(productName)}`;
          window.open(whatsappLink, '_blank');
        });
      });
    }

    document.querySelectorAll('.filter-btn').forEach(button => {
      button.addEventListener('click', () => {
        document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
        button.classList.add('active');
        activeFilter = button.dataset.filter;
        renderProducts();
      });
    });

    renderProducts();
  </script>
</body>
</html>