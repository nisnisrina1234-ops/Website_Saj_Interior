<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Saj Interior</title>
  <style>
    /* Reset dan styling dasar */
    * {
      box-sizing: border-box;
    }
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f5f5f5;
      color: #333;
    }
    header {
      background-color: #2c3e50;
      color: white;
      padding: 1rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: sticky;
      top: 0;
      z-index: 100;
      flex-wrap: wrap;
    }
    header h1 {
      margin: 0;
      font-weight: 700;
      font-size: 1.5rem;
    }
    nav {
      display: flex;
      align-items: center;
      gap: 1rem;
      flex-wrap: wrap;
    }
    nav a {
      color: white;
      text-decoration: none;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 0.3rem;
      font-size: 1rem;
    }
    nav a:hover {
      text-decoration: underline;
    }
    .icon {
      width: 18px;
      height: 18px;
      fill: white;
      display: inline-block;
      vertical-align: middle;
    }
    .cart-icon {
      position: relative;
      cursor: pointer;
      font-size: 1.5rem;
      margin-left: 1rem;
    }
    .cart-count {
      position: absolute;
      top: -8px;
      right: -10px;
      background: red;
      color: white;
      font-size: 0.75rem;
      padding: 2px 6px;
      border-radius: 50%;
      font-weight: bold;
    }
    /* Mobile menu button */
    #mobileMenuButton {
      display: none;
      background: transparent;
      border: none;
      color: white;
      font-size: 1.8rem;
      cursor: pointer;
      margin-left: 1rem;
    }
    /* Mobile Navigation */
    #mobileMenu {
      display: none;
      background: white;
      width: 100%;
      margin-top: 0.5rem;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgb(0 0 0 / 0.15);
    }
    #mobileMenu button {
      width: 100%;
      text-align: left;
      padding: 0.75rem 1rem;
      border: none;
      background: white;
      color: #333;
      font-size: 1rem;
      cursor: pointer;
      border-bottom: 1px solid #eee;
      transition: background-color 0.2s ease;
    }
    #mobileMenu button:hover {
      background-color: #ffecb3; /* amber-50 */
    }
    #mobileMenu button:last-child {
      border-bottom: none;
    }
    /* Main Content */
    main.container {
      max-width: 1200px;
      margin: 2rem auto;
      padding: 0 1rem;
    }
    .page {
      display: none;
    }
    .page.active {
      display: block;
    }
    h2 {
      margin-top: 0;
      margin-bottom: 1rem;
      color: #2c3e50;
      font-size: 2.5rem;
      font-weight: 700;
      text-align: center;
    }
    /* Hero Section */
    .hero-section {
      display: grid;
      grid-template-columns: 1fr;
      gap: 2rem;
      align-items: center;
    }
    @media(min-width: 768px) {
      .hero-section {
        grid-template-columns: 1fr 1fr;
      }
    }
    .hero-section h2 {
      font-size: 2.5rem;
      margin-bottom: 1rem;
      color: #4a4a4a;
    }
    .hero-section p {
      font-size: 1.125rem;
      color: #666;
      margin-bottom: 1.5rem;
    }
    .hero-section button {
      background-color: #ffb300; /* amber-600 */
      color: white;
      padding: 0.75rem 2rem;
      border: none;
      border-radius: 12px;
      font-weight: 600;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    .hero-section button:hover {
      background-color: #ffa000; /* amber-700 */
    }
    .hero-section img {
      width: 100%;
      border-radius: 24px;
      object-fit: cover;
    }
    /* Sections styling */
    section {
      margin-bottom: 3rem;
    }
    /* Grid for catalog and featured */
    .grid {
      display: grid;
      gap: 1.5rem;
    }
    .grid-cols-1 {
      grid-template-columns: 1fr;
    }
    @media(min-width: 768px) {
      .md\\:grid-cols-2 {
        grid-template-columns: repeat(2, 1fr);
      }
      .md\\:grid-cols-3 {
        grid-template-columns: repeat(3, 1fr);
      }
    }
    /* Product card */
    .product-card {
      background: white;
      border-radius: 16px;
      box-shadow: 0 4px 12px rgb(0 0 0 / 0.1);
      overflow: hidden;
      display: flex;
      flex-direction: column;
      transition: box-shadow 0.3s ease;
    }
    .product-card:hover {
      box-shadow: 0 8px 24px rgb(0 0 0 / 0.15);
    }
    .product-card img {
      width: 100%;
      height: 200px;
      object-fit: cover;
    }
    .product-card .p-4 {
      padding: 1rem;
      flex-grow: 1;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    .product-card h4 {
      margin: 0 0 0.5rem 0;
      font-weight: 600;
      font-size: 1.25rem;
      color: #333;
    }
    .product-card p {
      flex-grow: 1;
      color: #666;
      margin-bottom: 1rem;
    }
    .product-card button {
      background-color: #ffb300;
      color: white;
      border: none;
      padding: 0.5rem 0;
      border-radius: 12px;
      font-weight: 600;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    .product-card button:hover {
      background-color: #ffa000;
    }
    /* Featured section */
    #featured .grid {
      grid-template-columns: 1fr;
      gap: 2rem;
      align-items: center;
    }
    @media(min-width: 768px) {
      #featured .grid {
        grid-template-columns: 1fr 1fr;
      }
    }
    #featured img {
      width: 100%;
      border-radius: 24px;
      object-fit: cover;
    }
    #featured h3 {
      font-size: 1.75rem;
      margin-bottom: 1rem;
      color: #444;
    }
    #featured p {
      color: #555;
      margin-bottom: 1.5rem;
      line-height: 1.5;
    }
    #featured button {
      background-color: #ffb300;
      color: white;
      padding: 0.75rem 2rem;
      border: none;
      border-radius: 12px;
      font-weight: 600;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    #featured button:hover {
      background-color: #ffa000;
    }
    /* Contact form */
    form input, form textarea {
      width: 100%;
      padding: 0.75rem;
      border: 1px solid #ccc;
      border-radius: 12px;
      font-size: 1rem;
      margin-bottom: 1rem;
      resize: vertical;
    }
    form button {
      background-color: #ffb300;
      color: white;
      border: none;
      padding: 0.75rem 2rem;
      border-radius: 12px;
      font-weight: 600;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    form button:hover {
      background-color: #ffa000;
    }
    /* Contact info */
    #contact div p {
      margin-bottom: 1rem;
      color: #555;
      font-size: 1rem;
    }
    /* Maps */
    #maps iframe {
      border-radius: 24px;
      box-shadow: 0 4px 12px rgb(0 0 0 / 0.1);
      width: 100%;
      height: 450px;
      border: none;
    }
    /* Cart */
    #cartItems > div {
      background: white;
      padding: 1rem;
      border-radius: 12px;
      box-shadow: 0 2px 8px rgb(0 0 0 / 0.1);
    }
    #cartItems h4 {
      margin: 0 0 0.5rem 0;
      font-weight: 600;
      font-size: 1.25rem;
    }
    #cartItems p {
      margin: 0.25rem 0;
      color: #555;
    }
    #cartItems button {
      margin-top: 0.5rem;
      background: none;
      border: none;
      color: #d32f2f;
      cursor: pointer;
      font-weight: 600;
    }
    /* Footer */
    footer {
      background-color: #2c3e50;
      color: white;
      padding: 2rem 1rem;
      text-align: center;
      font-size: 0.9rem;
    }
    /* WhatsApp floating button */
    .whatsapp-float {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background-color: #25d366;
      color: white;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 28px;
      text-decoration: none;
      box-shadow: 0 2px 8px rgb(0 0 0 / 0.3);
      z-index: 1000;
    }
    /* Responsive */
    @media(max-width: 768px) {
      #mobileMenuButton {
        display: inline-block;
      }
      nav a:not(.cart-icon) {
        display: none;
      }
      #mobileMenu {
        display: none;
      }
      #mobileMenu.show {
        display: block;
      }
    }
  </style>
  <!-- FontAwesome for WhatsApp icon -->
  <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
</head>
<body>
  <header>
    <h1>Saj Interior</h1>
    <nav>
      <a href="#home" title="Home" onclick="showPage('home')">
        <svg class="icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M10 20v-6h4v6h5v-8h3L12 3 2 12h3v8z"/>
        </svg>
        Beranda
      </a>
      <a href="#about" title="Tentang Kami" onclick="showPage('about')">
        <svg class="icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
        </svg>
        Tentang Kami
      </a>
      <a href="#catalog" title="Katalog Produk" onclick="showPage('catalog')">
        <svg class="icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M3 13h2v-2H3v2zm0 4h2v-2H3v2zm0-8h2V7H3v2zm4 4h14v-2H7v2zm0 4h14v-2H7v2zm0-10v2h14V7H7z"/>
        </svg>
        Katalog Produk
      </a>
      <a href="#featured" title="Produk Unggulan" onclick="showPage('featured')">
        <svg class="icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"/>
        </svg>
        Produk Unggulan
      </a>
      <a href="#contact" title="Kontak" onclick="showPage('contact')">
        <svg class="icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M21 8V7l-3 2-2-2-3 2-2-2-3 2v1l3-2 2 2 3-2 2 2 3-2zM3 19h18v2H3z"/>
        </svg>
        Kontak
      </a>
      <a href="#maps" title="Maps" onclick="showPage('maps')">
        <svg class="icon" viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zM12 11.5c-1.38 0-2.5-1.12-2.5-2.5S10.62 6.5 12 6.5s2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
        </svg>
        Maps
      </a>
      <span class="cart-icon" id="cartIcon" title="Lihat Keranjang" onclick="showPage('cart')">
        🛒
        <span class="cart-count" id="cartBadge" style="display:none">0</span>
      </span>
      <button id="mobileMenuButton" aria-label="Buka menu mobile">&#9776;</button>
    </nav>

    <!-- Mobile Navigation -->
    <div id="mobileMenu" class="hidden">
      <button onclick="showPage('home')">Beranda</button>
      <button onclick="showPage('about')">Tentang Kami</button>
      <button onclick="showPage('catalog')">Katalog Produk</button>
      <button onclick="showPage('featured')">Produk Unggulan</button>
      <button onclick="showPage('contact')">Kontak</button>
      <button onclick="showPage('maps')">Maps</button>
      <button onclick="showPage('cart')">
        Keranjang <span id="mobileCartBadge" class="bg-amber-600 text-white px-2 py-1 rounded-full text-sm ml-2">0</span>
      </button>
    </div>
  </header>

  <!-- Main Content -->
  <main class="container mx-auto px-4 py-8">
    <!-- Beranda -->
    <section id="home" class="page active">
      <div class="bg-gradient-to-r from-amber-50 to-orange-100 rounded-2xl p-8 mb-12">
        <div class="hero-section grid md:grid-cols-2 gap-8 items-center">
          <div>
            <h2 class="text-4xl md:text-5xl font-bold text-gray-800 mb-4">Bikin Rumah Nyaman dengan SAJ Interior</h2>
            <p class="text-lg text-gray-600 mb-6">Solusi interior terbaik untuk rumah dan kantor modern dengan desain inovatif.</p>
            <button onclick="showPage('catalog')" class="bg-amber-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-amber-700 transition-colors">Lihat Katalog</button>
          </div>
          <div class="rounded-2xl overflow-hidden">
            <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/cc7d0517-ac2d-486c-80fa-48e412d30296.png" alt="Modern living room with spacious sofa, wooden coffee table, large windows overlooking city skyline, and contemporary wall decor in warm lighting." />
          </div>
        </div>
      </div>
    </section>

    <!-- Tentang Kami -->
    <section id="about" class="page">
        <div class="max-w-4xl mx-auto">
            <h2 class="text-4xl font-bold text-center text-gray-800 mb-8">Tentang Kami</h2>
            <div class="grid md:grid-cols-2 gap-12">
                <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/81a9e44f-6f5c-4ce9-b37e-978b5b415bec.png" alt="Interior design team collaborating in a modern showroom with blueprints, fabric samples, design software on laptops, and furniture prototypes." />
                <div>
                    <p class="text-gray-700 mb-6">SAJ Interior adalah perusahaan desain interior terkemuka yang fokus pada menciptakan ruang hidup yang estetis dan fungsional. Dengan tim profesional berpengalaman, kami hadir untuk mewujudkan visi Anda.</p>
                    <h3 class="text-2xl font-semibold mb-4">Visi & Misi</h3>
                    <p class="text-gray-700">Visi: Menjadi pemimpin dalam industri interior dengan inovasi berkelanjutan. Misi: Memberikan pelayanan terbaik dan produk berkualitas untuk kepuasan klien.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Katalog Produk -->
    <section id="catalog" class="page">
        <h2 class="text-4xl font-bold text-center text-gray-800 mb-8">Katalog Produk</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div class="product-card bg-white rounded-xl shadow-md overflow-hidden">
                <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/3f02616d-ffbb-4d58-8796-7a4d6ba8024f.png" alt="Elegant wooden dining table set with upholstered chairs in a bright contemporary dining space with chandelier lighting." />
                <div class="p-4">
                    <h4 class="font-semibold text-lg mb-2">Meja Makan Modern</h4>
                    <p class="text-gray-600 mb-4">Desain elegan dengan bahan kayu berkualitas.</p>
                    <button onclick="addToCart('Meja Makan Modern', 4500000)" class="w-full bg-amber-600 text-white py-2 rounded-lg hover:bg-amber-700">Tambah ke Keranjang</button>
                </div>
            </div>
            <div class="product-card bg-white rounded-xl shadow-md overflow-hidden">
                <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/1928266d-1036-434c-b493-7f1d8787ec6e.png" alt="Cozy gray fabric sofa with plush cushions and wooden legs in a nicely lit living room with plants and magazines." />
                <div class="p-4">
                    <h4 class="font-semibold text-lg mb-2">Sofa Lounge</h4>
                    <p class="text-gray-600 mb-4">Sofa nyaman untuk ruang tamu minimalis.</p>
                    <button onclick="addToCart('Sofa Lounge', 3200000)" class="w-full bg-amber-600 text-white py-2 rounded-lg hover:bg-amber-700">Tambah ke Keranjang</button>
                </div>
            </div>
            <div class="product-card bg-white rounded-xl shadow-md overflow-hidden">
                <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/dffda21c-fd22-4f7e-a756-142b265d7d12.png" alt="Stylish wardrobe with mirrored doors and storage drawers in a bedroom with soft bedding and curtains." />
                <div class="p-4">
                    <h4 class="font-semibold text-lg mb-2">Lemari Pakaian</h4>
                    <p class="text-gray-600 mb-4">Lemari elegan dengan desain modern.</p>
                    <button onclick="addToCart('Lemari Pakaian', 2800000)" class="w-full bg-amber-600 text-white py-2 rounded-lg hover:bg-amber-700">Tambah ke Keranjang</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Produk Unggulan -->
    <section id="featured" class="page">
        <h2 class="text-4xl font-bold text-center text-gray-800 mb-8">Produk Unggulan</h2>
        <div class="grid md:grid-cols-2 gap-12 items-center">
            <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/9b4d60bf-9b89-4598-8187-553e04aef9ad.png" alt="Luxurious bedroom suite with king-size bed, velvet headboard, chandelier, and large windows with city view and soft natural light." />
            <div>
                <h3 class="text-2xl font-semibold mb-4">Kamar Tidur Mewah</h3>
                <p class="text-gray-700 mb-6">Suite kamar tidur lengkap dengan desain premium dan material berkualitas tinggi untuk kenyamanan maksimal.</p>
                <button onclick="addToCart('Kamar Tidur Mewah', 8500000)" class="bg-amber-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-amber-700">Pesan Sekarang</button>
            </div>
        </div>
    </section>

    <!-- Kontak -->
    <section id="contact" class="page">
        <h2 class="text-4xl font-bold text-center text-gray-800 mb-8">Kontak Kami</h2>
        <div class="grid md:grid-cols-2 gap-12">
            <form>
                <div class="mb-4"><input type="text" placeholder="Nama" class="w-full p-3 border rounded"></div>
                <div class="mb-4"><input type="email" placeholder="Email" class="w-full p-3 border rounded"></div>
                <div class="mb-4"><textarea placeholder="Pesan" rows="5" class="w-full p-3 border rounded"></textarea></div>
                <button type="submit" class="bg-amber-600 text-white px-8 py-3 rounded-lg font-semibold hover:bg-amber-700">Kirim Pesan</button>
            </form>
            <div>
                <p class="text-gray-700 mb-4"><i class="fas fa-phone mr-2"></i> 08970688409</p>
                <p class="text-gray-700 mb-4"><i class="fas fa-envelope mr-2"></i> sajinteriorconstruction@gmail.com</p>
                <p class="text-gray-700 mb-4"><i class="fas fa-map-marker-alt mr-2"></i> Jl. Bareng, Barengpulo, Hadipolo, Kec. Jekulo, Kabupaten Kudus, Jawa Tengah 59382</p>
            </div>
        </div>
    </section>

    <!-- Maps -->
    <section id="maps" class="page">
        <h2 class="text-4xl font-bold text-center text-gray-800 mb-8">Lokasi Kami</h2>
        <div class="bg-gray-200 h-64 rounded-2xl flex items-center justify-center">
            <p class="text-gray-600">Peta lokasi SAJ Interior - Jl. Bareng, Barengpulo, Hadipolo, Kec. Jekulo, Kabupaten Kudus, Jawa Tengah 59382</p>
        </div>
        <div class="mt-8">
            <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3960.8935628963824!2d110.90189257585029!3d-6.797102768730307!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e70cf4447624213%3A0x50dccf071f4295c1!2sInterior%20SAJ%20jateng!5e0!3m2!1sid!2sid!4v1711100694401!5m2!1sid!2sid" width="100%" height="450" style="border:0;" allowfullscreen></iframe>
        </div>
    </section>

    <!-- Keranjang -->
    <section id="cart" class="page">
        <h2 class="text-4xl font-bold text-center text-gray-800 mb-8">Keranjang Belanja</h2>
        <div id="cartItems" class="space-y-4">
            <p class="text-gray-600 text-center">Belum ada item di keranjang.</p>
        </div>
    </section>
</main>

<!-- Footer -->
<footer class="bg-gray-800 text-white py-8">
    <div class="container mx-auto px-4 text-center">
        <p>© 2024 SAJ Interior. All Rights Reserved.</p>
    </div>
</footer>

<!-- WhatsApp Button -->
<a href="https://wa.me/6281234567890?text=Halo, saya tertarik dengan SAJ Interior!" class="whatsapp-float" target="_blank" aria-label="Hubungi via WhatsApp">
    <i class="fab fa-whatsapp text-white text-xl"></i>
</a>

<script>
    let cart = JSON.parse(localStorage.getItem('cart')) || [];
    let currentPage = 'home';

    function showPage(pageName) {
        document.querySelectorAll('.page').forEach(p => {
            p.classList.remove('active');
            p.style.display = 'none';
        });
        document.getElementById(pageName).classList.add('active');
        document.getElementById(pageName).style.display = 'block';
        currentPage = pageName;
        toggleMobileMenu(false);
        updateCartDisplay();
    }

    function toggleMobileMenu(show) {
        const menu = document.getElementById('mobileMenu');
        if (show) menu.classList.remove('hidden');
        else menu.classList.add('hidden');
    }

    document.getElementById('mobileMenuButton').addEventListener('click', () => toggleMobileMenu(true));
    document.querySelectorAll('#mobileMenu button').forEach(btn => btn.addEventListener('click', () => toggleMobileMenu(false)));

    function addToCart(name, price) {
        cart.push({ name, price, qty: 1 });
        localStorage.setItem('cart', JSON.stringify(cart));
        updateCartCount();
        showNotification(`${name} ditambahkan ke keranjang!`);
        if (currentPage === 'cart') updateCartDisplay();
    }

    function updateCartCount() {
        const count = cart.reduce((sum, item) => sum + item.qty, 0);
        document.getElementById('cartBadge').textContent = count;
        document.getElementById('mobileCartBadge').textContent = count;
    }

    function updateCartDisplay() {
        const cartDiv = document.getElementById('cartItems');
        cartDiv.innerHTML = '';
        if (cart.length === 0) {
            cartDiv.innerHTML = '<p class="text-gray-600 text-center">Belum ada item di keranjang.</p>';
        } else {
            cart.forEach((item, idx) => {
                cartDiv.innerHTML += `
                    <div class="bg-white p-4 rounded-lg shadow">
                        <h4>${item.name}</h4>
                        <p>Rp ${item.price.toLocaleString()}</p>
                        <p>Qty: ${item.qty}</p>
                        <button onclick="removeFromCart(${idx})" class="text-red-600 mt-2">Hapus</button>
                    </div>
                `;
            });
        }
    }

    function removeFromCart(idx) {
        cart.splice(idx, 1);
        localStorage.setItem('cart', JSON.stringify(cart));
        updateCartCount();
        updateCartDisplay();
    }

    function showNotification(msg) {
        const notif = document.createElement('div');
        notif.className = 'fixed top-20 right-4 bg-green-600 text-white px-6 py-3 rounded-lg shadow-lg z-50';
        notif.textContent = msg;
        document.body.appendChild(notif);
        setTimeout(() => document.body.removeChild(notif), 3000);
    }

    document.addEventListener('DOMContentLoaded', () => {
        updateCartCount();
        updateCartDisplay();
    });
</script>
