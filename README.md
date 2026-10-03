[index.html](https://github.com/user-attachments/files/33010586/index.html)
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LUMIÈRE | Joyería Fina</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600;700&family=Montserrat:wght@300;400;500&display=swap" rel="stylesheet">
    <!-- Font Awesome para iconos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        /* Reset y estilos base */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            background-color: #faf8f5;
            color: #2e2e2e;
            line-height: 1.6;
            overflow-x: hidden;
        }

        h1, h2, h3, h4 {
            font-family: 'Cormorant Garamond', serif;
            font-weight: 600;
            letter-spacing: 1px;
        }

        a {
            text-decoration: none;
            color: inherit;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* HEADER */
        header {
            background-color: #fff;
            box-shadow: 0 2px 15px rgba(0, 0, 0, 0.03);
            position: sticky;
            top: 0;
            z-index: 100;
            padding: 15px 0;
        }

        .header-flex {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2rem;
            font-weight: 700;
            letter-spacing: 4px;
            color: #b89b7b;
            text-transform: uppercase;
        }

        .logo span {
            color: #2e2e2e;
            font-weight: 400;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        nav ul li a {
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            font-weight: 400;
            color: #4a4a4a;
            transition: color 0.3s;
            padding-bottom: 5px;
            border-bottom: 1px solid transparent;
        }

        nav ul li a:hover,
        nav ul li a.active {
            color: #b89b7b;
            border-bottom-color: #b89b7b;
        }

        .header-icons {
            display: flex;
            gap: 1.5rem;
            font-size: 1.2rem;
            color: #4a4a4a;
        }

        .header-icons i {
            cursor: pointer;
            transition: color 0.3s;
        }

        .header-icons i:hover {
            color: #b89b7b;
        }

        .menu-toggle {
            display: none;
            font-size: 1.8rem;
            cursor: pointer;
            color: #2e2e2e;
        }

        /* SLIDER / BANNER */
        .hero-slider {
            position: relative;
            width: 100%;
            height: 85vh;
            min-height: 500px;
            overflow: hidden;
            background-color: #f2ede8;
        }

        .slide {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0;
            transition: opacity 1s ease-in-out;
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            z-index: 1;
        }

        .slide.active {
            opacity: 1;
            z-index: 2;
        }

        .slide::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.3);
            z-index: 1;
        }

        .slide-content {
            position: relative;
            z-index: 2;
            color: #fff;
            max-width: 800px;
            padding: 0 20px;
        }

        .slide-content h1 {
            font-size: 4.5rem;
            font-weight: 700;
            letter-spacing: 3px;
            text-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
            margin-bottom: 15px;
        }

        .slide-content p {
            font-size: 1.2rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            margin-bottom: 30px;
            font-weight: 300;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        .btn {
            display: inline-block;
            padding: 14px 42px;
            background-color: #b89b7b;
            color: #fff;
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 3px;
            font-weight: 500;
            border: none;
            transition: background 0.3s, transform 0.3s;
            cursor: pointer;
            border-radius: 0;
            box-shadow: 0 6px 20px rgba(184, 155, 123, 0.4);
        }

        .btn:hover {
            background-color: #9e8468;
            transform: translateY(-2px);
        }

        /* Controles del slider */
        .slider-controls {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 10;
            display: flex;
            gap: 15px;
        }

        .dot {
            width: 12px;
            height: 12px;
            background-color: rgba(255, 255, 255, 0.5);
            border-radius: 50%;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
        }

        .dot.active {
            background-color: #b89b7b;
            transform: scale(1.3);
        }

        .arrow {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            z-index: 10;
            background: rgba(255, 255, 255, 0.3);
            color: #fff;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            cursor: pointer;
            transition: background 0.3s, color 0.3s;
            backdrop-filter: blur(4px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .arrow:hover {
            background: #b89b7b;
            color: #fff;
        }

        .arrow-left { left: 30px; }
        .arrow-right { right: 30px; }

        /* ESTILOS COMPARTIDOS DE SECCIONES */
        .section {
            padding: 80px 0;
        }

        .section-alt {
            background-color: #f2ede8;
        }

        .section-title {
            text-align: center;
            font-size: 3rem;
            margin-bottom: 20px;
            color: #2e2e2e;
            font-weight: 600;
            letter-spacing: 2px;
        }

        .section-subtitle {
            text-align: center;
            font-size: 1rem;
            color: #7a7a7a;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-bottom: 50px;
            font-weight: 300;
        }

        /* SECCIÓN SOBRE NOSOTROS */
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }

        .about-img {
            width: 100%;
            height: 500px;
            background-size: cover;
            background-position: center;
            border-radius: 12px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }

        .about-text h2 {
            font-size: 2.8rem;
            margin-bottom: 20px;
            color: #2e2e2e;
        }

        .about-text p {
            color: #5a5a5a;
            margin-bottom: 18px;
            font-size: 1rem;
            line-height: 1.8;
        }

        .about-features {
            display: flex;
            gap: 30px;
            margin-top: 30px;
            flex-wrap: wrap;
        }

        .about-feature {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .about-feature i {
            font-size: 1.8rem;
            color: #b89b7b;
        }

        .about-feature span {
            font-size: 0.9rem;
            font-weight: 500;
            letter-spacing: 1px;
            text-transform: uppercase;
        }

        /* SECCIÓN COLECCIONES */
        .collections-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 30px;
        }

        .collection-card {
            background: #fff;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .collection-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }

        .collection-img {
            width: 100%;
            height: 280px;
            background-size: cover;
            background-position: center;
            transition: transform 0.5s;
        }

        .collection-card:hover .collection-img {
            transform: scale(1.03);
        }

        .collection-info {
            padding: 25px 20px 30px;
            text-align: center;
        }

        .collection-info h3 {
            font-size: 1.8rem;
            margin-bottom: 8px;
            color: #2e2e2e;
        }

        .collection-info p {
            color: #7a7a7a;
            font-size: 0.9rem;
            margin-bottom: 18px;
            letter-spacing: 1px;
        }

        .collection-info .btn-small {
            padding: 10px 30px;
            font-size: 0.8rem;
            background-color: transparent;
            color: #b89b7b;
            border: 1px solid #b89b7b;
            box-shadow: none;
            letter-spacing: 2px;
        }

        .collection-info .btn-small:hover {
            background-color: #b89b7b;
            color: #fff;
            transform: translateY(-2px);
        }

        /* SECCIÓN PRODUCTOS DESTACADOS */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 30px;
        }

        .product-card {
            background: #fff;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s, box-shadow 0.3s;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }

        .product-badge {
            position: absolute;
            top: 15px;
            left: 15px;
            background-color: #b89b7b;
            color: #fff;
            font-size: 0.7rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            padding: 5px 12px;
            z-index: 2;
            font-weight: 500;
        }

        .product-img {
            width: 100%;
            height: 260px;
            background-size: cover;
            background-position: center;
            transition: transform 0.5s;
        }

        .product-card:hover .product-img {
            transform: scale(1.05);
        }

        .product-info {
            padding: 20px;
            text-align: center;
        }

        .product-info h4 {
            font-size: 1.4rem;
            margin-bottom: 8px;
            color: #2e2e2e;
        }

        .product-price {
            color: #b89b7b;
            font-size: 1.1rem;
            font-weight: 500;
            letter-spacing: 1px;
            margin-bottom: 15px;
        }

        .product-info .btn-small {
            padding: 10px 25px;
            font-size: 0.75rem;
            background-color: transparent;
            color: #b89b7b;
            border: 1px solid #b89b7b;
            box-shadow: none;
            letter-spacing: 2px;
        }

        .product-info .btn-small:hover {
            background-color: #b89b7b;
            color: #fff;
            transform: translateY(-2px);
        }

        /* SECCIÓN TESTIMONIOS */
        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .testimonial-card {
            background: #fff;
            padding: 40px 30px;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            text-align: center;
            position: relative;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .testimonial-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }

        .testimonial-card .quote-icon {
            font-size: 2.5rem;
            color: #b89b7b;
            opacity: 0.4;
            margin-bottom: 15px;
        }

        .testimonial-card p {
            color: #5a5a5a;
            font-style: italic;
            font-size: 0.95rem;
            line-height: 1.8;
            margin-bottom: 20px;
        }

        .testimonial-stars {
            color: #b89b7b;
            margin-bottom: 15px;
            font-size: 1rem;
        }

        .testimonial-author {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.3rem;
            font-weight: 600;
            color: #2e2e2e;
        }

        .testimonial-role {
            font-size: 0.8rem;
            color: #7a7a7a;
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        /* SECCIÓN NEWSLETTER */
        .newsletter {
            background-color: #1f1f1f;
            padding: 70px 0;
            text-align: center;
        }

        .newsletter h2 {
            font-size: 2.8rem;
            color: #fff;
            margin-bottom: 15px;
            letter-spacing: 2px;
        }

        .newsletter p {
            color: #b0b0b0;
            margin-bottom: 30px;
            font-size: 1rem;
            letter-spacing: 1px;
        }

        .newsletter-form {
            display: flex;
            justify-content: center;
            gap: 10px;
            max-width: 550px;
            margin: 0 auto;
            flex-wrap: wrap;
        }

        .newsletter-form input {
            flex: 1;
            min-width: 250px;
            padding: 14px 20px;
            border: 1px solid #3a3a3a;
            background-color: #2a2a2a;
            color: #fff;
            font-family: 'Montserrat', sans-serif;
            font-size: 0.9rem;
            letter-spacing: 1px;
            outline: none;
            transition: border-color 0.3s;
        }

        .newsletter-form input:focus {
            border-color: #b89b7b;
        }

        .newsletter-form input::placeholder {
            color: #888;
        }

        /* FOOTER */
        footer {
            background-color: #1f1f1f;
            color: #b0b0b0;
            padding: 50px 0 25px;
            border-top: 1px solid #2e2e2e;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }

        .footer-col h4 {
            color: #b89b7b;
            font-size: 1.3rem;
            margin-bottom: 20px;
            letter-spacing: 2px;
        }

        .footer-col p, .footer-col a {
            font-size: 0.9rem;
            color: #b0b0b0;
            line-height: 1.8;
            display: block;
            margin-bottom: 8px;
            transition: color 0.3s;
        }

        .footer-col a:hover {
            color: #b89b7b;
        }

        .social-icons {
            display: flex;
            gap: 15px;
            margin-top: 15px;
        }

        .social-icons a {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: #2e2e2e;
            color: #b0b0b0;
            font-size: 1.1rem;
            transition: background 0.3s, color 0.3s;
        }

        .social-icons a:hover {
            background-color: #b89b7b;
            color: #fff;
        }

        .copyright {
            text-align: center;
            padding-top: 25px;
            border-top: 1px solid #2e2e2e;
            font-size: 0.8rem;
            letter-spacing: 1px;
        }

        /* RESPONSIVE */
        @media (max-width: 992px) {
            .slide-content h1 { font-size: 3.5rem; }

            .about-grid {
                grid-template-columns: 1fr;
                gap: 40px;
            }

            .about-img { height: 400px; }

            .about-text h2 { font-size: 2.3rem; }
        }

        @media (max-width: 768px) {
            .header-flex { flex-wrap: wrap; }

            nav {
                display: none;
                width: 100%;
                order: 3;
                margin-top: 15px;
                padding-top: 15px;
                border-top: 1px solid #eee;
            }

            nav.active { display: block; }

            nav ul {
                flex-direction: column;
                gap: 1rem;
                align-items: center;
            }

            .menu-toggle { display: block; }

            .header-icons {
                margin-left: auto;
                margin-right: 20px;
            }

            .hero-slider {
                height: 70vh;
                min-height: 400px;
            }

            .slide-content h1 { font-size: 2.8rem; }
            .slide-content p { font-size: 1rem; }

            .arrow { width: 40px; height: 40px; font-size: 1.2rem; }
            .arrow-left { left: 15px; }
            .arrow-right { right: 15px; }

            .section { padding: 60px 0; }
            .section-title { font-size: 2.4rem; }

            .about-features { gap: 20px; }

            .newsletter h2 { font-size: 2.2rem; }
        }

        @media (max-width: 480px) {
            .logo { font-size: 1.5rem; letter-spacing: 2px; }

            .header-icons { gap: 1rem; font-size: 1rem; }

            .hero-slider { height: 60vh; min-height: 350px; }

            .slide-content h1 { font-size: 2.2rem; }
            .slide-content p { font-size: 0.8rem; letter-spacing: 1px; }

            .btn { padding: 12px 28px; font-size: 0.8rem; letter-spacing: 2px; }

            .section-title { font-size: 2rem; }
            .section-subtitle { font-size: 0.8rem; letter-spacing: 2px; }

            .about-img { height: 280px; }
            .about-text h2 { font-size: 1.9rem; }

            .collection-info h3 { font-size: 1.5rem; }
            .product-info h4 { font-size: 1.2rem; }

            .newsletter h2 { font-size: 1.8rem; }
            .newsletter-form input { min-width: 100%; }

            .footer-grid {
                grid-template-columns: 1fr;
                gap: 30px;
                text-align: center;
            }

            .social-icons { justify-content: center; }
        }
    </style>
</head>
<body>

    <!-- HEADER -->
    <header>
        <div class="container header-flex">
            <div class="logo">LUMI<span>ÈRE</span></div>
            <div class="menu-toggle" id="menuToggle">
                <i class="fas fa-bars"></i>
            </div>
            <nav id="mainNav">
                <ul>
                    <li><a href="#" class="active">Inicio</a></li>
                    <li><a href="#nosotros">Nosotros</a></li>
                    <li><a href="#colecciones">Colecciones</a></li>
                    <li><a href="#productos">Productos</a></li>
                    <li><a href="#testimonios">Testimonios</a></li>
                    <li><a href="#contacto">Contacto</a></li>
                </ul>
            </nav>
            <div class="header-icons">
                <i class="fas fa-search"></i>
                <i class="far fa-heart"></i>
                <i class="fas fa-shopping-bag"></i>
            </div>
        </div>
    </header>

    <!-- SLIDER PRINCIPAL -->
    <section class="hero-slider">
        <div class="slide active" style="background-image: url('https://images.unsplash.com/photo-1599643478518-a784e5dc4c8f?q=80&w=1974&auto=format&fit=crop');">
            <div class="slide-content">
                <h1>Elegancia Eterna</h1>
                <p>Descubre la nueva colección de alta joyería</p>
                <a href="#colecciones" class="btn">Explorar</a>
            </div>
        </div>
        <div class="slide" style="background-image: url('https://images.unsplash.com/photo-1611591437281-460bfbe1220a?q=80&w=2070&auto=format&fit=crop');">
            <div class="slide-content">
                <h1>Brillo Natural</h1>
                <p>Piezas únicas en oro y diamantes</p>
                <a href="#productos" class="btn">Ver colección</a>
            </div>
        </div>
        <div class="slide" style="background-image: url('https://images.unsplash.com/photo-1602173574767-37ac01994b2a?q=80&w=2070&auto=format&fit=crop');">
            <div class="slide-content">
                <h1>Amor en Cada Detalle</h1>
                <p>Anillos de compromiso que cuentan historias</p>
                <a href="#colecciones" class="btn">Descubrir</a>
            </div>
        </div>

        <div class="arrow arrow-left" id="prevSlide">
            <i class="fas fa-chevron-left"></i>
        </div>
        <div class="arrow arrow-right" id="nextSlide">
            <i class="fas fa-chevron-right"></i>
        </div>

        <div class="slider-controls" id="sliderDots">
            <div class="dot active" data-index="0"></div>
            <div class="dot" data-index="1"></div>
            <div class="dot" data-index="2"></div>
        </div>
    </section>

    <!-- SECCIÓN SOBRE NOSOTROS -->
    <section class="section" id="nosotros">
        <div class="container">
            <h2 class="section-title">Sobre Nosotros</h2>
            <p class="section-subtitle">Tradición y artesanía desde 1998</p>

            <div class="about-grid">
                <div class="about-img" style="background-image: url('https://images.unsplash.com/photo-1573408301185-9146fe634ad0?q=80&w=2069&auto=format&fit=crop');"></div>
                <div class="about-text">
                    <h2>Arte en cada pieza</h2>
                    <p>En LUMIÈRE creemos que cada joya cuenta una historia. Desde hace más de dos décadas, nuestros maestros orfebres combinan técnicas tradicionales con diseños contemporáneos para crear piezas únicas que trascienden generaciones.</p>
                    <p>Trabajamos exclusivamente con oro de 18 quilates, platino y diamantes certificados, garantizando la más alta calidad en cada creación. Nuestro compromiso es ofrecerte joyas que celebren los momentos más importantes de tu vida.</p>

                    <div class="about-features">
                        <div class="about-feature">
                            <i class="fas fa-gem"></i>
                            <span>Materiales Premium</span>
                        </div>
                        <div class="about-feature">
                            <i class="fas fa-award"></i>
                            <span>Certificación</span>
                        </div>
                        <div class="about-feature">
                            <i class="fas fa-hand-holding-heart"></i>
                            <span>Hecho a mano</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- SECCIÓN COLECCIONES -->
    <section class="section section-alt" id="colecciones">
        <div class="container">
            <h2 class="section-title">Colecciones Destacadas</h2>
            <p class="section-subtitle">Piezas únicas para momentos inolvidables</p>

            <div class="collections-grid">
                <div class="collection-card">
                    <div class="collection-img" style="background-image: url('https://images.unsplash.com/photo-1605100804763-247f67b3557e?q=80&w=2070&auto=format&fit=crop');"></div>
                    <div class="collection-info">
                        <h3>Anillos Solitarios</h3>
                        <p>Diamantes con corte brillante</p>
                        <a href="#" class="btn btn-small">Ver más</a>
                    </div>
                </div>
                <div class="collection-card">
                    <div class="collection-img" style="background-image: url('https://images.unsplash.com/photo-1599643478518-a784e5dc4c8f?q=80&w=1974&auto=format&fit=crop');"></div>
                    <div class="collection-info">
                        <h3>Collares de Oro</h3>
                        <p>Diseños atemporales en oro 18k</p>
                        <a href="#" class="btn btn-small">Ver más</a>
                    </div>
                </div>
                <div class="collection-card">
                    <div class="collection-img" style="background-image: url('https://images.unsplash.com/photo-1535632066927-ab7c9ab60908?q=80&w=2070&auto=format&fit=crop');"></div>
                    <div class="collection-info">
                        <h3>Aretes de Lujo</h3>
                        <p>Elegancia para cada ocasión</p>
                        <a href="#" class="btn btn-small">Ver más</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- SECCIÓN PRODUCTOS DESTACADOS -->
    <section class="section" id="productos">
        <div class="container">
            <h2 class="section-title">Productos Destacados</h2>
            <p class="section-subtitle">Selección exclusiva de nuestra tienda</p>

            <div class="products-grid">
                <div class="product-card">
                    <div class="product-badge">Nuevo</div>
                    <div class="product-img" style="background-image: url('https://images.unsplash.com/photo-1611591437281-460bfbe1220a?q=80&w=2070&auto=format&fit=crop');"></div>
                    <div class="product-info">
                        <h4>Anillo Aurora</h4>
                        <div class="product-price">$2,450</div>
                        <a href="#" class="btn btn-small">Añadir al carrito</a>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-badge">Oferta</div>
                    <div class="product-img" style="background-image: url('https://images.unsplash.com/photo-1515562141207-7a88fb7ce338?q=80&w=2070&auto=format&fit=crop');"></div>
                    <div class="product-info">
                        <h4>Collar Estrella</h4>
                        <div class="product-price">$1,890</div>
                        <a href="#" class="btn btn-small">Añadir al carrito</a>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-badge">Exclusivo</div>
                    <div class="product-img" style="background-image: url('https://images.unsplash.com/photo-1631982690223-8aa4be0a2497?q=80&w=2070&auto=format&fit=crop');"></div>
                    <div class="product-info">
                        <h4>Aretes Luna</h4>
                        <div class="product-price">$3,200</div>
                        <a href="#" class="btn btn-small">Añadir al carrito</a>
                    </div>
                </div>
                <div class="product-card">
                    <div class="product-img" style="background-image: url('https://images.unsplash.com/photo-1603561596112-0a132b757442?q=80&w=2070&auto=format&fit=crop');"></div>
                    <div class="product-info">
                        <h4>Pulsera Serena</h4>
                        <div class="product-price">$1,560</div>
                        <a href="#" class="btn btn-small">Añadir al carrito</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- SECCIÓN TESTIMONIOS -->
    <section class="section section-alt" id="testimonios">
        <div class="container">
            <h2 class="section-title">Lo Que Dicen Nuestros Clientes</h2>
            <p class="section-subtitle">Historias reales, momentos inolvidables</p>

            <div class="testimonials-grid">
                <div class="testimonial-card">
                    <div class="quote-icon"><i class="fas fa-quote-left"></i></div>
                    <div class="testimonial-stars">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p>"Compré el anillo de compromiso para mi ahora esposa y quedó fascinada. La calidad del diamante y el acabado son simplemente espectaculares. Un servicio impecable."</p>
                    <div class="testimonial-author">Carlos Mendoza</div>
                    <div class="testimonial-role">Cliente desde 2020</div>
                </div>
                <div class="testimonial-card">
                    <div class="quote-icon"><i class="fas fa-quote-left"></i></div>
                    <div class="testimonial-stars">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p>"LUMIÈRE es mi tienda de confianza. He comprado varias piezas y siempre superan mis expectativas. El diseño es elegante y atemporal, perfecto para cualquier ocasión."</p>
                    <div class="testimonial-author">María Fernández</div>
                    <div class="testimonial-role">Cliente frecuente</div>
                </div>
                <div class="testimonial-card">
                    <div class="quote-icon"><i class="fas fa-quote-left"></i></div>
                    <div class="testimonial-stars">
                        <i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i><i class="fas fa-star"></i>
                    </div>
                    <p>"Regalé un collar a mi madre por su cumpleaños y quedó encantada. La presentación, el empaque y la atención al detalle hicieron toda la diferencia. 100% recomendados."</p>
                    <div class="testimonial-author">Ana Gutiérrez</div>
                    <div
