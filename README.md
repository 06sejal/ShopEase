<!doctype html>
<html lang="en">

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>ShopEase — E‑commerce Teaching Example</title>

    <style>
        /* ==========================
       Base / Utility styles
       ========================== */
        :root {
            --primary: #0d6efd;
            /* blue */
            --accent: #ff7a59;
            /* coral */
            --muted: #6b7280;
            /* gray */
            --bg: #f7fafc;
            /* page background */
            --card: #ffffff;
            /* card background */
            --radius: 12px;
            --container: 1200px;
            font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
            color: #111827;
        }

        * {
            box-sizing: border-box
        }

        html,
        body {
            height: 100%
        }

        body {
            margin: 0;
            background: var(--bg);
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            line-height: 1.4;
            font-size: 16px;
        }

        /* Constrain page width and center */
        .container {
            width: 90%;
            max-width: var(--container);
            margin: 0 auto;
        }

        /* ==========================
       NAVBAR
       - Using Flexbox for horizontal layout
       - 'space-between' to push brand and actions apart
       - simple responsive mobile menu
       ========================== */
        header.site-header {
            background: linear-gradient(90deg, rgba(13, 110, 253, 0.08), rgba(255, 122, 89, 0.03));
            position: sticky;
            /* keeps nav at top while scrolling */
            top: 0;
            z-index: 40;
            backdrop-filter: blur(6px);
        }

        .nav {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 16px;
            padding: 14px 0;
        }

        .brand {
            display: flex;
            align-items: center;
            gap: 12px;
            font-weight: 700;
            font-size: 1.1rem
        }

        .brand .logo {
            width: 44px;
            height: 44px;
            border-radius: 8px;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            display: inline-grid;
            place-items: center;
            color: white;
            font-weight: 800;
        }

        /* primary nav links - horizontal in desktop */
        nav.primary {
            display: flex;
            gap: 18px;
            align-items: center
        }

        nav.primary a {
            text-decoration: none;
            color: var(--muted);
            font-weight: 600;
            padding: 8px 10px;
            border-radius: 8px;
        }

        nav.primary a:hover {
            color: var(--primary);
            background: rgba(13, 110, 253, 0.06)
        }

        /* action buttons on the right */
        .nav-actions {
            display: flex;
            gap: 10px;
            align-items: center
        }

        .btn {
            border: 0;
            padding: 9px 14px;
            border-radius: 10px;
            font-weight: 700;
            cursor: pointer;
        }

        .btn-primary {
            background: var(--primary);
            color: white
        }

        .btn-ghost {
            background: transparent;
            border: 1px solid rgba(0, 0, 0, 0.06)
        }

        /* Mobile menu checkbox trick: hide by default on desktop */
        .mobile-toggle {
            display: none
        }

        .mobile-menu {
            display: none
        }

        /* ==========================
       BANNER / HERO
       - Two-column layout using CSS Grid
       - simple text animation using keyframes
       ========================== */
        .hero {
            padding: 48px 0 24px;
        }

        .hero-grid {
            display: grid;
            grid-template-columns: 1fr 460px;
            gap: 28px;
            align-items: center
        }

        .hero-card {
            background: linear-gradient(180deg, rgba(255, 255, 255, 0.9), rgba(255, 255, 255, 0.6));
            padding: 32px;
            border-radius: 16px;
            box-shadow: 0 8px 28px rgba(13, 110, 253, 0.06);
        }

        .eyebrow {
            color: var(--accent);
            font-weight: 700
        }

        h1 {
            font-size: 2rem;
            margin: 8px 0 12px
        }

        p.lead {
            color: var(--muted);
            margin: 0 0 18px
        }

        /* animated highlight under the hero title */
        .title-anim {
            display: inline-block;
            position: relative;
            overflow: hidden;
            padding-bottom: 6px
        }

        .title-anim::after {
            content: '';
            position: absolute;
            left: 0;
            bottom: 0;
            height: 6px;
            background: linear-gradient(90deg, var(--accent), var(--primary));
            width: 100%;
            transform: translateX(-110%);
            animation: slideInUnderline 1s ease-out forwards 0.3s;
        }

        @keyframes slideInUnderline {
            to {
                transform: translateX(0)
            }
        }

        .hero-cta {
            display: flex;
            gap: 12px;
            margin-top: 10px
        }

        /* hero image card */
        .hero-image {
            background: linear-gradient(135deg, #fff 0%, #f9fbff 100%);
            padding: 20px;
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 10px 30px rgba(2, 6, 23, 0.06);
        }

        .product-preview {
            width: 320px;
            height: 320px;
            border-radius: 12px;
            background: linear-gradient(120deg, #fff, #eef3ff);
            display: grid;
            place-items: center;
            font-size: 22px
        }

        .product-preview img
       {
        height: 100%;
        width: 63%;
       }


        /* small responsive icons row inside hero */
        .hero-features {
            display: flex;
            gap: 12px;
            margin-top: 18px;
            flex-wrap: wrap
        }

        .feature-pill {
            background: var(--card);
            padding: 8px 12px;
            border-radius: 999px;
            box-shadow: 0 6px 18px rgba(15, 23, 42, 0.04);
            font-weight: 600
        }

        /* ==========================
       SERVICES (flex-based)
       - Use Flexbox for equal-height cards
       ========================== */
        section.services {
            padding: 36px 0
        }

        .services-grid {
            display: flex;
            gap: 18px;
            flex-wrap: wrap
        }

        .service {
            flex: 1 1 240px;
            background: var(--card);
            padding: 18px;
            border-radius: 12px;
            box-shadow: 0 8px 24px rgba(2, 6, 23, 0.04);
            min-width: 220px
        }

        .service h4 {
            margin: 8px 0
        }

        /* ==========================
       PRODUCTS (CSS Grid)
       - Use CSS Grid to create responsive product gallery
       - Product card demonstrates hover animation using keyframes/transform
       ========================== */
        section.products {
            padding: 36px 0
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 18px
        }

        .product {
            background: var(--card);
            padding: 14px;
            border-radius: 12px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            align-items: start;
            transition: transform .28s ease, box-shadow .28s ease;
        }

        .product:hover {
            transform: translateY(-8px);
            box-shadow: 0 12px 30px rgba(2, 6, 23, 0.08)
        }

        .product img {
            width: 100%;
            height: 100%;
            border-radius: 8px;
            display: block
        }

        .product .title {
            font-weight: 700
        }

        .price {
            color: var(--accent);
            font-weight: 800
        }

        /* subtle loading shimmer for images (teaching: placeholder technique) */
        .img-placeholder {
            height: 160px;
            width: 100%;
            border-radius: 8px;
            background: linear-gradient(90deg, #eef2ff, #f8fafc, #eef2ff);
            animation: shimmer 1.6s infinite
        }

        @keyframes shimmer {
            0% {
                background-position: -200px 0
            }

            100% {
                background-position: 200px 0
            }
        }

        /* ==========================
       TESTIMONIALS (carousel-like using CSS scroll snap)
       - Teach students a simple touch-friendly carousel without JS
       ========================== */
        section.testimonials {
            padding: 36px 0
        }

        .testi-track {
            display: flex;
            gap: 14px;
            overflow: auto;
            padding-bottom: 10px;
            scroll-snap-type: x mandatory
        }

        .testi {
            min-width: 280px;
            flex: 0 0 320px;
            background: var(--card);
            padding: 18px;
            border-radius: 12px;
            scroll-snap-align: center
        }

        .stars {
            color: gold
        }

        /* ==========================
       FOOTER
       ========================== */
        footer.site-footer {
            padding: 28px 0;
            background: linear-gradient(180deg, transparent, rgba(2, 6, 23, 0.02));
            margin-top: 20px
        }

        .footer-grid {
            display: grid;
            grid-template-columns: 1fr 220px;
            gap: 18px;
            align-items: start
        }

        /* ==========================
       Responsive rules
       - Use mobile-first approach: smaller screens use single column stacks
       - Common breakpoints: 900px (tablet), 640px (phone)
       ========================== */
        @media (max-width:900px) {
            .hero-grid {
                grid-template-columns: 1fr;
            }

            .products-grid {
                grid-template-columns: repeat(2, 1fr)
            }

            .footer-grid {
                grid-template-columns: 1fr
            }

            nav.primary {
                display: none
            }

            .mobile-toggle {
                display: block
            }

            .mobile-menu {
                display: block;
                background: transparent;
                padding-top: 8px
            }

            .mobile-menu a {
                display: block;
                padding: 8px 0;
                color: var(--muted);
                text-decoration: none
            }
        }

        @media (max-width:640px) {
            :root {
                font-size: 15px
            }

            .products-grid {
                grid-template-columns: repeat(1, 1fr)
            }

            .service {
                flex: 1 1 100%
            }

            .brand .logo {
                width: 38px;
                height: 38px
            }

            h1 {
                font-size: 1.4rem
            }

            .product img {
                height: auto
            }
        }

        /* Extra small polish: prevent horizontal overflow on body when mobile menu opens */
        html,
        body {
            overflow-x: hidden
        }
    </style>
</head>

<body>
    <header class="site-header">
        <div class="container nav">
            <div class="brand" aria-label="ShopEase brand">
                <div class="logo">S</div>
                <div>
                    <div>ShopEase</div>
                    <div style="font-size:.78rem;color:var(--muted);font-weight:600">Smart shopping, simplified</div>
                </div>
            </div>

            <!-- primary links (hidden on small screens) -->
            <nav class="primary" aria-label="Primary">
                <a href="#home">Home</a>
                <a href="#services">Services</a>
                <a href="#products">Products</a>
                <a href="#testimonials">Testimonials</a>
                <a href="#contact">Contact</a>
            </nav>

            <div class="nav-actions">
                <button class="btn btn-ghost" aria-label="Open search">Search</button>
                <button class="btn btn-primary">Cart (2)</button>

                <!-- mobile toggle: only visible under 900px (see CSS) -->
                <label class="mobile-toggle" for="m">☰</label>
                <input id="m" class="mobile-toggle" type="checkbox" style="display:none" />
            </div>
        </div>

        <!-- mobile menu (simple) - in production you'd use a nicer animation or JS toggle -->
        <div class="container mobile-menu" aria-hidden="false">
            <a href="#home">Home</a>
            <a href="#services">Services</a>
            <a href="#products">Products</a>
            <a href="#testimonials">Testimonials</a>
            <a href="#contact">Contact</a>
        </div>
    </header>

    <!-- ==========================
       HERO / BANNER
       - Grid layout: text and product preview
       - Keyframe underline animation used to draw attention
       ========================== -->
    <main>
        <section class="hero container" id="home">
            <div class="hero-grid">

                <div class="hero-card">
                    <div class="eyebrow">NEW ARRIVAL</div>
                    <h1><span class="title-anim">Comfort meet style —</span> Premium sneakers for everyday</h1>
                    <p class="lead">Lightweight, sustainable materials and crafted to move with you. Perfect for
                        commuting, running, and casual wear.</p>

                    <div class="hero-cta">
                        <button class="btn btn-primary">Shop Now</button>
                        <button class="btn btn-ghost">Learn More</button>
                    </div>

                    <div class="hero-features" aria-hidden="true">
                        <div class="feature-pill">Free shipping</div>
                        <div class="feature-pill">30-day returns</div>
                        <div class="feature-pill">Plant-based foam</div>
                    </div>
                </div>

                <div class="hero-image" aria-hidden="true">
                    <!-- product-preview illustrates the kind of image/visual you'd use -->
                    <div class="product-preview">
                        <img src="./image/ladies.jpg">
                    </div>
                </div>

            </div>
        </section>

        <!-- ==========================
         SERVICES
         - Show how flex creates equal-height columns automatically
         ========================== -->
        <section class="services container" id="services">
            <h3>Why choose ShopEase</h3>
            <div class="services-grid" style="margin-top:14px">
                <article class="service">
                    <h4>Fast delivery</h4>
                    <p style="color:var(--muted)">Most orders ship within 24 hours. Show students how flex items stretch
                        to match heights.</p>
                </article>
                <article class="service">
                    <h4>Quality guarantee</h4>
                    <p style="color:var(--muted)">We inspect every product before shipping. Useful to explain box-shadow
                        and border-radius for cards.</p>
                </article>
                <article class="service">
                    <h4>Customer support</h4>
                    <p style="color:var(--muted)">24/7 support team — teach how to use icons and badges in pills.</p>
                </article>
            </div>
        </section>

        <!-- ==========================
         PRODUCTS (Grid) - real teaching area
         - Explain repeat(), minmax(), and responsive layout choices
         ========================== -->
        <section class="products container" id="products">
            <h3>Popular Products</h3>
            <div class="products-grid" style="margin-top:14px">

                <!-- Product card example: image placeholder, title, price, and add-to-cart button -->
                <article class="product">
                    <div class="img-placeholder" aria-hidden="true">
                        <img src="./image/sneaker2.WEBP">
                    </div>
                    <div class="title">Urban Runner Sneakers</div>
                    <div class="price">₹3,499</div>
                    <div style="margin-top:auto;display:flex;gap:8px;width:100%">
                        <button class="btn btn-primary" style="flex:1">Add</button>
                        <button class="btn btn-ghost">Wishlist</button>
                    </div>
                </article>

                <article class="product">
                    <div class="img-placeholder" aria-hidden="true">
                        <img src="./image/every_day_trainer.jpg">
                    </div>
                    <div class="title">Everyday Trainer</div>
                    <div class="price">₹2,899</div>
                    <div style="margin-top:auto;display:flex;gap:8px;width:100%">
                        <button class="btn btn-primary" style="flex:1">Add</button>
                        <button class="btn btn-ghost">Wishlist</button>
                    </div>
                </article>

                <article class="product">
                    <div class="img-placeholder" aria-hidden="true">
                        <img src="./image/comfy_slips.jpg">
                    </div>
                    <div class="title">Comfy Slip-Ons</div>
                    <div class="price">₹1,999</div>
                    <div style="margin-top:auto;display:flex;gap:8px;width:100%">
                        <button class="btn btn-primary" style="flex:1">Add</button>
                        <button class="btn btn-ghost">Wishlist</button>
                    </div>
                </article>

                <article class="product">
                    <div class="img-placeholder" aria-hidden="true">
                        <img src="./image/nike.jpg">
                    </div>
                    <div class="title">Nike</div>
                    <div class="price">₹4,199</div>
                    <div style="margin-top:auto;display:flex;gap:8px;width:100%">
                        <button class="btn btn-primary" style="flex:1">Add</button>
                        <button class="btn btn-ghost">Wishlist</button>
                    </div>
                </article>

            </div>
        </section>

        <!-- ==========================
         TESTIMONIALS
         - Use scroll-snap to create a touch-friendly carousel without JS
         ========================== -->
        <section class="testimonials container" id="testimonials">
            <h3>What customers say</h3>
            <div class="testi-track" style="margin-top:14px">
                <article class="testi">
                    <div style="font-weight:800">Asha K.</div>
                    <div class="stars">★★★★★</div>
                    <p style="color:var(--muted)">"Fast delivery and the shoes fit perfectly — highly recommend
                        ShopEase!"</p>
                </article>

                <article class="testi">
                    <div style="font-weight:800">Deepak M.</div>
                    <div class="stars">★★★★★</div>
                    <p style="color:var(--muted)">"Super comfy — day-long wear without any pain. Great quality."</p>
                </article>

                <article class="testi">
                    <div style="font-weight:800">Sanya R.</div>
                    <div class="stars">★★★★★</div>
                    <p style="color:var(--muted)">"Excellent customer support and easy returns. Will buy again."</p>
                </article>
            </div>
        </section>

    </main>

    <!-- ==========================
       FOOTER
       - simple two-column grid
       - include contact / social / copyright
       ========================== -->
    <footer class="site-footer">
        <div class="container footer-grid" id="contact">
            <div>
                <h4>ShopEase</h4>
                <p style="color:var(--muted)">123 Market St, City, Country · support@shopease.example</p>
                <p style="color:var(--muted);margin-top:10px">© <span id="year"></span> ShopEase — All rights reserved
                </p>
            </div>

            <div>
                <h5>Follow us</h5>
                <div style="display:flex;gap:8px;margin-top:8px">
                    <div class="btn btn-ghost">Twitter</div>
                    <div class="btn btn-ghost">Instagram</div>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // small script to show current year (teaching: tiny JS for dynamic content)
        document.getElementById('year').textContent = new Date().getFullYear();
    </script>
</body>

</html>
