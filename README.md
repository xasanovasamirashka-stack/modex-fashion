<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>ModeX — Luxury Fashion Store</title>

  <!-- Bootstrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <!-- Bootstrap Icons -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.css" rel="stylesheet">
  <!-- AOS -->
  <link href="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.css" rel="stylesheet">

  <style>
    :root{
      --bg:#0b0b0b;
      --panel:#0f0f10;
      --muted:#bdb7a9;
      --gold:#c79b38;
      --white:#f6f6f6;
      --glass: rgba(255,255,255,0.03);
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: Inter, "Segoe UI", Roboto, Arial, sans-serif;
      background: linear-gradient(180deg,#060606 0%, #0b0b0b 100%);
      color:var(--white);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      scroll-behavior:smooth;
    }

    /* NAV */
    .navbar {
      background: linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-bottom:1px solid rgba(255,255,255,0.03);
      padding:.6rem 0;
      position:sticky;
      top:0;
      z-index:1100;
    }
    .navbar-brand { font-weight:800; letter-spacing:1px; color:var(--white) !important; }
    .nav-link { color:var(--muted) !important; }
    .nav-link:hover { color:var(--white) !important; }

    .search-input {
      background: rgba(255,255,255,0.02);
      color: var(--white);
      border: 1px solid rgba(255,255,255,0.04);
      border-radius: 28px;
      padding-left: 14px;
      padding-right: 34px;
      height:40px;
    }

    /* HERO */
    .hero { padding-top:4.8rem; padding-bottom:2.5rem; }
    .hero .carousel-item{
      min-height:420px;
      border-radius:14px;
      overflow:hidden;
      background-size:cover;
      background-position:center;
      box-shadow: 0 18px 46px rgba(0,0,0,0.7);
    }
    .hero-caption{
      position:absolute; left:6%; top:18%; max-width:46%;
      background: linear-gradient(90deg, rgba(6,6,6,0.65), rgba(6,6,6,0.28));
      padding:22px; border-radius:10px;
    }
    .hero-caption h2{ font-size:2.4rem; margin-bottom:8px; }
    .hero-caption p{ color:var(--muted); margin-bottom:12px; }

    /* product cards */
    .card-prod{
      border-radius:12px;
      background: linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));
      border:1px solid rgba(255,255,255,0.03);
      overflow:hidden;
      transition: transform .25s ease, box-shadow .25s ease;
    }
    .card-prod:hover{ transform: translateY(-8px); box-shadow: 0 16px 40px rgba(0,0,0,0.6); }
    .img-wrap{ height:300px; overflow:hidden; }
    .img-wrap img{ width:100%; height:100%; object-fit:cover; transition: transform .5s ease; }
    .card-prod:hover .img-wrap img{ transform:scale(1.05); }

    .price { color:var(--gold); font-weight:700; }
    .muted { color:var(--muted); }

    .panel { background:var(--glass); border-radius:10px; padding:14px; border:1px solid rgba(255,255,255,0.03); }

    .overlay { position:absolute; inset:0; display:flex; align-items:center; justify-content:center; background:linear-gradient(180deg, rgba(0,0,0,0.02), rgba(0,0,0,0.35)); opacity:0; transition:opacity .2s ease; }
    .card-prod:hover .overlay { opacity:1; }

    /* floating chat */
    #chatBtn {
      position:fixed; right:18px; bottom:18px; z-index:1200;
      background:var(--gold); color:#000; border:none; width:56px; height:56px; border-radius:50%;
      display:flex; align-items:center; justify-content:center; box-shadow: 0 10px 30px rgba(0,0,0,0.45);
    }

    /* back to top */
    #toTop {
      position: fixed; right:18px; bottom:88px; z-index:1200;
      background:linear-gradient(90deg,var(--gold),#d4af37); color:#000; border:none; border-radius:50%;
      width:52px; height:52px; display:none; align-items:center; justify-content:center; box-shadow: 0 8px 18px rgba(0,0,0,0.45);
    }

    footer{ border-top:1px solid rgba(255,255,255,0.03); padding:26px 0; margin-top:32px; color:var(--muted); }

    @media (max-width:767px){
      .img-wrap { height:220px; }
      .hero-caption{ max-width:86%; left:5%; top:14%; }
      .search-input{ width:160px !important; }
    }
  </style>
</head>
<body>

  <!-- NAVBAR -->
  <nav class="navbar navbar-expand-lg">
    <div class="container">
      <a class="navbar-brand" href="#">Mode<span style="color:var(--gold); margin-left:6px;">X</span></a>
      <button class="navbar-toggler btn btn-outline-light" type="button" data-bs-toggle="collapse" data-bs-target="#navMenu">
        <i class="bi bi-list"></i>
      </button>

      <div class="collapse navbar-collapse" id="navMenu">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0 align-items-lg-center">
          <li class="nav-item"><a class="nav-link" href="#home">Главная</a></li>
          <li class="nav-item"><a class="nav-link" href="#catalog">Каталог</a></li>
          <li class="nav-item"><a class="nav-link" href="#collections">Коллекции</a></li>
          <li class="nav-item"><a class="nav-link" href="#about">О бренде</a></li>
          <li class="nav-item"><a class="nav-link" href="#contacts">Контакты</a></li>
        </ul>

        <div class="d-flex align-items-center gap-2">
          <div style="position:relative;">
            <input id="searchInput" class="search-input" placeholder="Поиск (пальто, платье, сумка)..." style="width:320px;">
            <i class="bi bi-search" style="position:absolute; right:12px; top:10px; color:var(--muted)"></i>
          </div>
          <button class="btn btn-outline-light" data-bs-toggle="modal" data-bs-target="#profileModal"><i class="bi bi-person"></i></button>
          <button class="btn btn-outline-light position-relative" id="openCart" data-bs-toggle="modal" data-bs-target="#cartModal" aria-label="Открыть корзину">
            <i class="bi bi-bag"></i>
            <span id="cartBadge" class="position-absolute top-0 start-100 translate-middle badge rounded-pill" style="background:var(--gold); color:#000; display:none; font-weight:700;">0</span>
          </button>
        </div>
      </div>
    </div>
  </nav>

  <!-- HERO -->
  <main class="container hero" id="home">
    <div id="heroCarousel" class="carousel slide" data-bs-ride="carousel" data-bs-interval="5200" data-aos="fade-up">
      <div class="carousel-inner">
        <div class="carousel-item active" style="background-image:linear-gradient(180deg, rgba(0,0,0,0.32), rgba(0,0,0,0.45)), url('https://images.unsplash.com/photo-1520975922203-b5e9a0cddb19?auto=format&fit=crop&w=1600&q=80');">
          <div class="hero-caption">
            <span class="badge" style="background:var(--gold); color:#000; padding:6px 10px; border-radius:8px;">Новая коллекция</span>
            <h2>AW 2025 — ModeX Luxury</h2>
            <p class="muted">Премиальные ткани, идеальная посадка — коллекция уже доступна.</p>
            <div class="mt-3">
              <a href="#catalog" class="btn btn-outline-light me-2">Купить</a>
              <button class="btn" style="background:var(--gold); color:#000" onclick="document.getElementById('catalog').scrollIntoView({behavior:'smooth'})">Посмотреть коллекцию</button>
            </div>
          </div>
        </div>

        <div class="carousel-item" style="background-image:linear-gradient(180deg, rgba(0,0,0,0.32), rgba(0,0,0,0.45)), url('https://images.unsplash.com/photo-1495121605193-b116b5b9c5a8?auto=format&fit=crop&w=1600&q=80');">
          <div class="hero-caption">
            <span class="badge" style="background:#7b3cff; color:#fff; padding:6px 10px; border-radius:8px;">Эксклюзив</span>
            <h2>ModeX Atelier</h2>
            <p class="muted">Индивидуальная примерка и ограниченные тиражи — закажите сейчас.</p>
            <div class="mt-3">
              <button class="btn btn-outline-light me-2" data-bs-toggle="modal" data-bs-target="#subscribeModal">Записаться</button>
              <a href="#about" class="btn btn-outline-light">О бренде</a>
            </div>
          </div>
        </div>
      </div>

      <button class="carousel-control-prev" type="button" data-bs-target="#heroCarousel" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#heroCarousel" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
      </button>
    </div>
  </main>

  <!-- CATALOG -->
  <section id="catalog" class="container py-4" data-aos="fade-up">
    <div class="d-flex justify-content-between align-items-center mb-3">
      <h3 style="margin:0">Каталог</h3>
      <div class="muted">Мужская и женская мода — лучшие предложения</div>
    </div>

    <div class="row g-4" id="productGrid">
      <!-- Product 1 (women) -->
      <div class="col-sm-6 col-md-4 col-lg-3 prod-col" data-type="women" data-name="Шерстяное пальто">
        <div class="card-prod position-relative" data-id="coat1">
          <div class="img-wrap"><img src="https://cdn.pixabay.com/photo/2016/11/29/03/09/woman-1867007_1280.jpg" alt="Шерстяное пальто"></div>
          <div class="p-3">
            <div class="d-flex justify-content-between">
              <div>
                <h6 class="mb-1">Шерстяное пальто</h6>
                <div class="muted" style="font-size:.9rem">Женская верхняя одежда</div>
              </div>
              <div class="text-end">
                <div class="price">149 $</div>
                <div class="muted" style="font-size:.8rem">рейтинг <strong style="color:var(--gold)">4.8</strong></div>
              </div>
            </div>
            <div class="d-flex gap-2 mt-3">
              <button class="btn btn-outline-light w-50 quick" data-name="Шерстяное пальто" data-price="149" data-img="https://cdn.pixabay.com/photo/2016/11/29/03/09/woman-1867007_1280.jpg">Быстрый просмотр</button>
              <button class="btn" style="background:var(--gold); color:#000;" onclick="addToCart('coat1','Шерстяное пальто',149,'https://cdn.pixabay.com/photo/2016/11/29/03/09/woman-1867007_1280.jpg')">В корзину</button>
            </div>
          </div>
          <div class="overlay"></div>
        </div>
      </div>

      <!-- Product 2 (men) -->
      <div class="col-sm-6 col-md-4 col-lg-3 prod-col" data-type="men" data-name="Классическое пальто">
        <div class="card-prod position-relative" data-id="coat2">
          <div class="img-wrap"><img src="https://cdn.pixabay.com/photo/2016/03/27/22/16/man-1281568_1280.jpg" alt="Классическое пальто"></div>
          <div class="p-3">
            <div class="d-flex justify-content-between">
              <div>
                <h6 class="mb-1">Классическое пальто</h6>
                <div class="muted" style="font-size:.9rem">Мужская верхняя одежда</div>
              </div>
              <div class="text-end">
                <div class="price">169 $</div>
                <div class="muted" style="font-size:.8rem">рейтинг <strong style="color:var(--gold)">4.7</strong></div>
              </div>
            </div>
            <div class="d-flex gap-2 mt-3">
              <button class="btn btn-outline-light w-50 quick" data-name="Классическое пальто" data-price="169" data-img="https://cdn.pixabay.com/photo/2016/03/27/22/16/man-1281568_1280.jpg">Быстрый просмотр</button>
              <button class="btn" style="background:var(--gold); color:#000;" onclick="addToCart('coat2','Классическое пальто',169,'https://cdn.pixabay.com/photo/2016/03/27/22/16/man-1281568_1280.jpg')">В корзину</button>
            </div>
          </div>
          <div class="overlay"></div>
        </div>
      </div>

      <!-- Product 3 (women) -->
      <div class="col-sm-6 col-md-4 col-lg-3 prod-col" data-type="women" data-name="Вечернее платье">
        <div class="card-prod position-relative" data-id="dress1">
          <div class="img-wrap"><img src="https://images.unsplash.com/photo-1556906781-9a412961c28d?auto=format&fit=crop&w=1200&q=80" alt="Вечернее платье"></div>
          <div class="p-3">
            <div class="d-flex justify-content-between">
              <div>
                <h6 class="mb-1">Вечернее платье</h6>
                <div class="muted" style="font-size:.9rem">Платье — женская</div>
              </div>
              <div class="text-end">
                <div class="price">199 $</div>
                <div class="muted" style="font-size:.8rem">рейтинг <strong style="color:var(--gold)">4.9</strong></div>
              </div>
            </div>
            <div class="d-flex gap-2 mt-3">
              <button class="btn btn-outline-light w-50 quick" data-name="Вечернее платье" data-price="199" data-img="https://images.unsplash.com/photo-1556906781-9a412961c28d?auto=format&fit=crop&w=1200&q=80">Быстрый просмотр</button>
              <button class="btn" style="background:var(--gold); color:#000;" onclick="addToCart('dress1','Вечернее платье',199,'https://images.unsplash.com/photo-1556906781-9a412961c28d?auto=format&fit=crop&w=1200&q=80')">В корзину</button>
            </div>
          </div>
          <div class="overlay"></div>
        </div>
      </div>

      <!-- Product 4 (accessory) -->
      <div class="col-sm-6 col-md-4 col-lg-3 prod-col" data-type="accessory" data-name="Кожаная сумка">
        <div class="card-prod position-relative" data-id="bag1">
          <div class="img-wrap"><img src="https://cdn.pixabay.com/photo/2016/11/29/10/07/handbag-1868600_1280.jpg" alt="Кожаная сумка"></div>
          <div class="p-3">
            <div class="d-flex justify-content-between">
              <div>
                <h6 class="mb-1">Кожаная сумка</h6>
                <div class="muted" style="font-size:.9rem">Аксессуар</div>
              </div>
              <div class="text-end">
                <div class="price">129 $</div>
                <div class="muted" style="font-size:.8rem">рейтинг <strong style="color:var(--gold)">4.6</strong></div>
              </div>
            </div>
            <div class="d-flex gap-2 mt-3">
              <button class="btn btn-outline-light w-50 quick" data-name="Кожаная сумка" data-price="129" data-img="https://cdn.pixabay.com/photo/2016/11/29/10/07/handbag-1868600_1280.jpg">Быстрый просмотр</button>
              <button class="btn" style="background:var(--gold); color:#000;" onclick="addToCart('bag1','Кожаная сумка',129,'https://cdn.pixabay.com/photo/2016/11/29/10/07/handbag-1868600_1280.jpg')">В корзину</button>
            </div>
          </div>
          <div class="overlay"></div>
        </div>
      </div>

      <!-- more products (you can duplicate / edit) -->
      <div class="col-sm-6 col-md-4 col-lg-3 prod-col" data-type="men" data-name="Рубашка премиум">
        <div class="card-prod position-relative" data-id="shirt1">
          <div class="img-wrap"><img src="https://cdn.pixabay.com/photo/2016/03/27/22/22/tie-1281578_1280.jpg" alt="Рубашка"></div>
          <div class="p-3">
            <div class="d-flex justify-content-between">
              <div><h6 class="mb-1">Рубашка премиум</h6><div class="muted" style="font-size:.9rem">Мужская</div></div>
              <div class="text-end"><div class="price">79 $</div><div class="muted" style="font-size:.8rem">рейтинг <strong style="color:var(--gold)">4.5</strong></div></div>
            </div>
            <div class="d-flex gap-2 mt-3">
              <button class="btn btn-outline-light w-50 quick" data-name="Рубашка премиум" data-price="79" data-img="https://cdn.pixabay.com/photo/2016/03/27/22/22/tie-1281578_1280.jpg">Быстрый просмотр</button>
              <button class="btn" style="background:var(--gold); color:#000;" onclick="addToCart('shirt1','Рубашка премиум',79,'https://cdn.pixabay.com/photo/2016/03/27/22/22/tie-1281578_1280.jpg')">В корзину</button>
            </div>
          </div>
          <div class="overlay"></div>
        </div>
      </div>

      <div class="col-sm-6 col-md-4 col-lg-3 prod-col" data-type="women" data-name="Блейзер">
        <div class="card-prod position-relative" data-id="blazer1">
          <div class="img-wrap"><img src="https://cdn.pixabay.com/photo/2015/11/07/11/02/woman-1031166_1280.jpg" alt="Блейзер"></div>
          <div class="p-3">
            <div class="d-flex justify-content-between">
              <div><h6 class="mb-1">Блейзер</h6><div class="muted" style="font-size:.9rem">Жакет</div></div>
              <div class="text-end"><div class="price">129 $</div><div class="muted" style="font-size:.8rem">рейтинг <strong style="color:var(--gold)">4.7</strong></div></div>
            </div>
            <div class="d-flex gap-2 mt-3">
              <button class="btn btn-outline-light w-50 quick" data-name="Блейзер" data-price="129" data-img="https://cdn.pixabay.com/photo/2015/11/07/11/02/woman-1031166_1280.jpg">Быстрый просмотр</button>
              <button class="btn" style="background:var(--gold); color:#000;" onclick="addToCart('blazer1','Блейзер',129,'https://cdn.pixabay.com/photo/2015/11/07/11/02/woman-1031166_1280.jpg')">В корзину</button>
            </div>
          </div>
          <div class="overlay"></div>
        </div>
      </div>

    </div>
  </section>

  <!-- COLLECTIONS -->
  <section id="collections" class="container py-4" data-aos="fade-up">
    <div class="section-title">
      <h3>Коллекции</h3>
      <div class="muted">Сезонные подборки ModeX</div>
    </div>

    <div id="colCarousel" class="carousel slide" data-bs-ride="carousel" data-bs-interval="6000">
      <div class="carousel-inner">
        <div class="carousel-item active">
          <div style="background-image:linear-gradient(180deg,rgba(0,0,0,0.25),rgba(0,0,0,0.45)), url('https://images.unsplash.com/photo-1495121605193-b116b5b9c5a8?auto=format&fit=crop&w=1600&q=80'); height:260px; border-radius:12px; background-size:cover; background-position:center; box-shadow: 0 12px 30px rgba(0,0,0,0.6); display:flex; align-items:center;">
            <div style="padding:28px; margin-left:28px;">
              <h4 style="color:var(--gold)">Atelier — лимитированная серия</h4>
              <p class="muted" style="max-width:520px;">Ручная отделка, премиальные ткани, индивидуальный пошив.</p>
              <a href="#catalog" class="btn btn-outline-light">Смотреть</a>
            </div>
          </div>
        </div>

        <div class="carousel-item">
          <div style="background-image:linear-gradient(180deg,rgba(0,0,0,0.25),rgba(0,0,0,0.45)), url('https://images.unsplash.com/photo-1514996937319-344454492b37?auto=format&fit=crop&w=1600&q=80'); height:260px; border-radius:12px; background-size:cover; background-position:center; box-shadow: 0 12px 30px rgba(0,0,0,0.6); display:flex; align-items:center;">
            <div style="padding:28px; margin-left:28px;">
              <h4 style="color:var(--gold)">Urban Luxury</h4>
              <p class="muted" style="max-width:520px;">Функциональные силуэты для города и вечера.</p>
              <a href="#catalog" class="btn btn-outline-light">Купить</a>
            </div>
          </div>
        </div>
      </div>

      <button class="carousel-control-prev" type="button" data-bs-target="#colCarousel" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#colCarousel" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
      </button>
    </div>
  </section>

  <!-- REVIEWS -->
  <section id="reviews" class="container py-4" data-aos="fade-up">
    <div class="section-title">
      <h3>Отзывы</h3>
      <div class="muted">Что говорят наши покупатели</div>
    </div>

    <div id="revCarousel" class="carousel slide" data-bs-ride="carousel">
      <div class="carousel-inner">
        <div class="carousel-item active">
          <div class="panel p-3 d-flex gap-3 align-items-center">
            <img src="https://images.unsplash.com/photo-1545996124-1b12f6c5a5e5?auto=format&fit=crop&w=200&q=60" alt="user" style="width:80px;height:80px;border-radius:50%;object-fit:cover;">
            <div>
              <strong>Анна</strong> <div class="muted">Москва</div>
              <p class="muted mb-0">Качество превосходное, пальто теплее, чем я ожидала. Спасибо ModeX!</p>
            </div>
          </div>
        </div>

        <div class="carousel-item">
          <div class="panel p-3 d-flex gap-3 align-items-center">
            <img src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?auto=format&fit=crop&w=200&q=60" alt="user" style="width:80px;height:80px;border-radius:50%;object-fit:cover;">
            <div>
              <strong>Елена</strong> <div class="muted">Санкт-Петербург</div>
              <p class="muted mb-0">Быстрая доставка и отличная упаковка. Блейзер сел идеально.</p>
            </div>
          </div>
        </div>
      </div>

      <button class="carousel-control-prev" type="button" data-bs-target="#revCarousel" data-bs-slide="prev"><span class="carousel-control-prev-icon"></span></button>
      <button class="carousel-control-next" type="button" data-bs-target="#revCarousel" data-bs-slide="next"><span class="carousel-control-next-icon"></span></button>
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about" class="container py-4" data-aos="fade-up">
    <div class="row align-items-center g-4">
      <div class="col-md-6"><img src="https://images.unsplash.com/photo-1520975922203-b5e9a0cddb19?auto=format&fit=crop&w=1200&q=80" alt="about" style="width:100%; border-radius:12px; box-shadow: 0 12px 30px rgba(0,0,0,0.5);"></div>
      <div class="col-md-6">
        <h3 style="color:var(--gold)">О бренде ModeX</h3>
        <p class="muted">ModeX — премиальный fashion-магазин, где сочетаются классика и современный дизайн. Мы работаем с лучшими материалами и помогаем подобрать образ для любого события.</p>
        <ul class="muted">
          <li>Ограниченные тиражи</li>
          <li>Персональный сервис</li>
          <li>Гарантия качества</li>
        </ul>
        <div class="mt-3">
          <a class="btn btn-outline-light me-2" href="#collections">Коллекции</a>
          <button class="btn" style="background:var(--gold); color:#000" data-bs-toggle="modal" data-bs-target="#subscribeModal">Получить оффер</button>
        </div>
      </div>
    </div>
  </section>

  <!-- CONTACTS -->
  <section id="contacts" class="container py-4" data-aos="fade-up">
    <div class="row g-3">
      <div class="col-md-5">
        <div class="panel">
          <p class="mb-1"><strong>Email:</strong> contact@modex.ru</p>
          <p class="mb-1"><strong>Телефон:</strong> +998 90 123 45 67</p>
          <p class="mb-0"><strong>Адрес:</strong> ул. Мода, 7, Tashkent</p>
        </div>
      </div>
      <div class="col-md-7">
        <div class="panel">
          <form id="contactForm">
            <div class="row g-2">
              <div class="col-md-6"><input id="cf-name" class="form-control bg-dark text-white" placeholder="Ваше имя" required></div>
              <div class="col-md-6"><input id="cf-email" class="form-control bg-dark text-white" placeholder="Email" required></div>
              <div class="col-12"><textarea id="cf-msg" class="form-control bg-dark text-white" rows="3" placeholder="Сообщение"></textarea></div>
              <div class="col-12 text-end"><button class="btn" style="background:var(--gold); color:#000">Отправить</button></div>
            </div>
            <div id="cf-res" class="muted mt-2" style="display:none"></div>
          </form>
        </div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="container">
      <div class="row align-items-center">
        <div class="col-md-6"><strong>ModeX</strong> — Luxury Fashion</div>
        <div class="col-md-6 text-md-end muted">© 2025 ModeX. Все права защищены. &nbsp; <small>Instagram · Telegram · Pinterest</small></div>
      </div>
    </div>
  </footer>

  <!-- Floating chat & toTop -->
  <button id="chatBtn" title="Чат поддержки" aria-label="Чат">
    <i class="bi bi-chat-dots-fill" style="font-size:1.25rem"></i>
  </button>
  <button id="toTop" title="Наверх" aria-label="Наверх"><i class="bi bi-arrow-up" style="font-size:1.1rem"></i></button>

  <!-- QUICK VIEW MODAL -->
  <div class="modal fade" id="quickModal" tabindex="-1" aria-hidden="true">
    <div class="modal-dialog modal-lg modal-dialog-centered">
      <div class="modal-content" style="background:linear-gradient(180deg,#0f0f0f,#090909); border:none; color:var(--white)">
        <div class="modal-header border-0"><h5 id="qTitle" class="modal-title">Товар</h5><button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div>
        <div class="modal-body">
          <div class="row g-3">
            <div class="col-md-6"><img id="qImg" src="" alt="" style="width:100%; border-radius:8px; object-fit:cover;"></div>
            <div class="col-md-6">
              <p id="qDesc" class="muted"></p>
              <div class="mb-3"><strong id="qPrice" style="color:var(--gold); font-size:1.3rem"></strong></div>
              <div class="d-flex gap-2">
                <button class="btn" style="background:var(--gold); color:#000" id="qAdd">В корзину</button>
                <button class="btn btn-outline-light" data-bs-dismiss="modal">Закрыть</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- CART MODAL -->
  <div class="modal fade" id="cartModal" tabindex="-1" aria-hidden="true">
    <div class="modal-dialog modal-lg modal-dialog-centered">
      <div class="modal-content" style="background:linear-gradient(180deg,#0f0f0f,#090909); border:none; color:var(--white)">
        <div class="modal-header border-0"><h5 class="modal-title">Корзина</h5><button type="button" class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div>
        <div class="modal-body">
          <div id="cartItems" class="mb-3"></div>
          <div class="d-flex justify-content-between align-items-center">
            <div class="muted">Доставка рассчитывается при оформлении</div>
            <div><strong>Итого: </strong><span id="cartTotal">0</span> $</div>
          </div>
        </div>
        <div class="modal-footer border-0">
          <button class="btn btn-outline-light" data-bs-dismiss="modal">Продолжить покупки</button>
          <button class="btn" style="background:var(--gold); color:#000" id="checkoutBtn">Оформить заказ</button>
        </div>
      </div>
    </div>
  </div>

  <!-- SUBSCRIBE MODAL -->
  <div class="modal fade" id="subscribeModal" tabindex="-1" aria-hidden="true">
    <div class="modal-dialog modal-md modal-dialog-centered">
      <div class="modal-content" style="background:linear-gradient(180deg,#0f0f0f,#090909); border:none; color:var(--white)">
        <div class="modal-header border-0"><h5 class="modal-title">Записаться</h5><button class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div>
        <div class="modal-body">
          <form id="subForm">
            <div class="mb-2"><input id="subName" class="form-control bg-dark text-white" placeholder="Ваше имя" required></div>
            <div class="mb-2"><input id="subEmail" class="form-control bg-dark text-white" placeholder="Email" required></div>
            <div class="text-end"><button class="btn" style="background:var(--gold); color:#000">Отправить</button></div>
          </form>
        </div>
      </div>
    </div>
  </div>

  <!-- CHAT PANEL (simple) -->
  <div class="offcanvas offcanvas-end text-white" tabindex="-1" id="chatPanel">
    <div class="offcanvas-header" style="border-bottom:1px solid rgba(255,255,255,0.03);">
      <h5 class="offcanvas-title">Поддержка ModeX</h5>
      <button type="button" class="btn-close btn-close-white" data-bs-dismiss="offcanvas" aria-label="Закрыть"></button>
    </div>
    <div class="offcanvas-body d-flex flex-column" style="background:linear-gradient(180deg,#0d0d0d,#080808);">
      <div id="chatMessages" style="flex:1; overflow:auto; padding:10px;">
        <div class="mb-2"><small class="muted">Чат поддержки (демо)</small></div>
        <div class="mb-2"><div class="panel p-2" style="display:inline-block;">Здравствуйте! Чем можем помочь?</div></div>
      </div>
      <form id="chatForm" class="d-flex gap-2 mt-2">
        <input id="chatInput" class="form-control bg-dark text-white" placeholder="Напишите сообщение..." />
        <button class="btn" style="background:var(--gold); color:#000">Отправить</button>
      </form>
    </div>
  </div>

  <!-- PROFILE modal (demo) -->
  <div class="modal fade" id="profileModal" tabindex="-1" aria-hidden="true">
    <div class="modal-dialog modal-sm modal-dialog-centered">
      <div class="modal-content" style="background:linear-gradient(180deg,#0f0f0f,#090909); border:none; color:var(--white)">
        <div class="modal-header border-0"><h5 class="modal-title">Войти</h5><button class="btn-close btn-close-white" data-bs-dismiss="modal"></button></div>
        <div class="modal-body">
          <form id="loginForm">
            <div class="mb-2"><input class="form-control bg-dark text-white" id="loginEmail" placeholder="Email"></div>
            <div class="mb-2"><input class="form-control bg-dark text-white" id="loginPass" placeholder="Пароль" type="password"></div>
            <div class="text-end"><button class="btn" style="background:var(--gold); color:#000">Войти</button></div>
          </form>
        </div>
      </div>
    </div>
  </div>

  <!-- SCRIPTS -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.js"></script>

  <script>
    AOS.init({ once:true, duration:700 });

    // ----- CART with localStorage -----
    const CART_KEY = 'modex_cart_v1';
    let cart = JSON.parse(localStorage.getItem(CART_KEY) || '{}');

    const cartBadge = document.getElementById('cartBadge');
    const cartItemsEl = document.getElementById('cartItems');
    const cartTotalEl = document.getElementById('cartTotal');

    function saveCart(){ localStorage.setItem(CART_KEY, JSON.stringify(cart)); updateCartUI(); }

    function updateCartUI(){
      const keys = Object.keys(cart);
      if(keys.length === 0){
        cartItemsEl.innerHTML = '<p class="muted">Ваша корзина пуста.</p>';
        cartBadge.style.display = 'none';
        cartTotalEl.innerText = '0';
        return;
      }
      let total = 0, qty = 0;
      cartItemsEl.innerHTML = '';
      keys.forEach(k=>{
        const it = cart[k];
        total += it.price * it.qty;
        qty += it.qty;
        const row = document.createElement('div');
        row.className = 'd-flex align-items-center mb-3';
        row.innerHTML = `
          <img src="${it.img}" alt="${it.name}" style="width:84px;height:84px;object-fit:cover;border-radius:8px;margin-right:12px;">
          <div class="flex-grow-1">
            <strong>${it.name}</strong><br>
            <span class="muted">${it.price}$ × ${it.qty}</span>
          </div>
          <div>
            <button class="btn btn-sm btn-outline-light me-1 dec" data-id="${it.id}">−</button>
            <button class="btn btn-sm btn-outline-light me-1 inc" data-id="${it.id}">+</button>
            <button class="btn btn-sm btn-outline-danger rm" data-id="${it.id}">✕</button>
          </div>
        `;
        cartItemsEl.appendChild(row);
      });
      cartBadge.style.display = 'inline-block';
      cartBadge.innerText = qty;
      cartTotalEl.innerText = total.toFixed(2);

      // events
      document.querySelectorAll('.inc').forEach(b => b.onclick = e => { const id=e.currentTarget.dataset.id; cart[id].qty++; saveCart(); });
      document.querySelectorAll('.dec').forEach(b => b.onclick = e => { const id=e.currentTarget.dataset.id; if(cart[id].qty>1) cart[id].qty--; else delete cart[id]; saveCart(); });
      document.querySelectorAll('.rm').forEach(b => b.onclick = e => { const id=e.currentTarget.dataset.id; delete cart[id]; saveCart(); });
    }

    function addToCart(id,name,price,img){
      if(cart[id]) cart[id].qty++; else cart[id] = { id, name, price, img, qty:1 };
      saveCart();
      // feedback
      cartBadge.classList.add('animate__animated','animate__pulse');
      setTimeout(()=> cartBadge.classList.remove('animate__animated','animate__pulse'),600);
    }

    // Bind inline add buttons already use addToCart()

    // Quick view handlers
    document.querySelectorAll('.quick').forEach(btn=>{
      btn.addEventListener('click', ()=>{
        const name = btn.dataset.name;
        const price = btn.dataset.price;
        const img = btn.dataset.img;
        document.getElementById('qTitle').innerText = name;
        document.getElementById('qImg').src = img;
        document.getElementById('qDesc').innerText = 'Короткое описание товара и материалы.';
        document.getElementById('qPrice').innerText = price + ' $';
        document.getElementById('qAdd').onclick = ()=> { addToCart('q_'+Date.now(), name, parseFloat(price)||0, img); const m = bootstrap.Modal.getInstance(document.getElementById('quickModal')); if(m) m.hide(); };
        const modal = new bootstrap.Modal(document.getElementById('quickModal'));
        modal.show();
      });
    });

    // Open cart updates UI
    document.getElementById('openCart').addEventListener('click', updateCartUI);

    // Checkout demo
    document.getElementById('checkoutBtn').addEventListener('click', ()=>{
      if(Object.keys(cart).length === 0){ alert('Корзина пуста. Добавьте товары.'); return; }
      const name = prompt('Введите ваше имя для оформления заказа:');
      if(!name) return;
      alert('Спасибо, '+name+'! Ваш заказ принят. С вами свяжутся в ближайшее время.');
      // clear cart
      Object.keys(cart).forEach(k=> delete cart[k]); saveCart();
      const cm = bootstrap.Modal.getInstance(document.getElementById('cartModal')); if(cm) cm.hide();
    });

    // Search filter
    document.getElementById('searchInput').addEventListener('input', function(){
      const q = this.value.trim().toLowerCase();
      document.querySelectorAll('.prod-col').forEach(col=>{
        const name = (col.dataset.name || '').toLowerCase();
        col.style.display = (q === '' || name.includes(q)) ? '' : 'none';
      });
      AOS.refresh();
    });

    // Subscribe form
    document.getElementById('subForm').addEventListener('submit', function(e){
      e.preventDefault(); alert('Записано! Мы свяжемся с вами.'); const sm = bootstrap.Modal.getInstance(document.getElementById('subscribeModal')); if(sm) sm.hide(); this.reset();
    });

    // Contact form
    document.getElementById('contactForm').addEventListener('submit', function(e){
      e.preventDefault(); document.getElementById('cf-res').style.display='block'; document.getElementById('cf-res').innerText='Спасибо! Мы ответим в течение 24 часов.'; setTimeout(()=>{ document.getElementById('cf-res').style.display='none'; this.reset(); },2000);
    });

    // Chat panel
    const chatBtn = document.getElementById('chatBtn');
    chatBtn.addEventListener('click', ()=> {
      const off = new bootstrap.Offcanvas(document.getElementById('chatPanel'));
      off.show();
    });
    document.getElementById('chatForm').addEventListener('submit', function(e){
      e.preventDefault();
      const msg = document.getElementById('chatInput').value.trim();
      if(!msg) return;
      const box = document.createElement('div'); box.className = 'd-flex mb-2'; box.innerHTML = `<div class="ms-auto panel p-2" style="max-width:70%;">${msg}</div>`;
      document.getElementById('chatMessages').appendChild(box);
      document.getElementById('chatInput').value='';
      setTimeout(()=> {
        const reply = document.createElement('div'); reply.className='d-flex mb-2'; reply.innerHTML = `<div class="panel p-2">Спасибо! Мы получили ваше сообщение и скоро ответим.</div>`;
        document.getElementById('chatMessages').appendChild(reply);
        document.getElementById('chatMessages').scrollTop = document.getElementById('chatMessages').scrollHeight;
      }, 800);
    });

    // Back to top
    const toTop = document.getElementById('toTop');
    window.addEventListener('scroll', ()=> { toTop.style.display = window.scrollY > 600 ? 'flex' : 'none'; });
    toTop.addEventListener('click', ()=> window.scrollTo({top:0, behavior:'smooth'}));

    // Initialize
    updateCartUI();
  </script>
</body>
</html>
