<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#1761ad">

<title>مكتبتي | المكتبة الرقمية العربية</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;500;600;700;800&display=swap" rel="stylesheet">

<link rel="stylesheet"
href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">

<style>
:root {
    --primary: #1761ad;
    --primary-light: #4da6ff;
    --background: #f2f7fd;
    --surface: #ffffff;
    --text: #12385d;
    --muted: #718096;
    --border: #e2eaf4;
    --danger: #e5484d;
    --success: #16865c;
    --shadow: 0 4px 16px rgba(18, 56, 93, .08);
    --bottom-height: 72px;
}

* {
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
    scroll-padding-top: 80px;
}

body {
    margin: 0;
    padding: 0 0 calc(var(--bottom-height) + 16px);
    background: var(--background);
    color: var(--text);
    font-family: "Cairo", Tahoma, sans-serif;
    overflow-x: hidden;
    transition: background .25s, color .25s;
}

button, input {
    font: inherit;
}

button {
    cursor: pointer;
}

button:focus-visible,
input:focus-visible {
    outline: 3px solid #70b8ff;
    outline-offset: 2px;
}

img {
    display: block;
    max-width: 100%;
}

/* =========================
   الشريط العلوي
========================= */

.topbar {
    position: sticky;
    top: 0;
    z-index: 100;
    background: var(--primary);
    color: #fff;
    box-shadow: 0 3px 12px #12385d20;
}

.topbar-inner {
    max-width: 1250px;
    min-height: 66px;
    margin: auto;
    padding: 10px 16px;
    display: flex;
    align-items: center;
    gap: 10px;
}

.icon-button {
    width: 42px;
    height: 42px;
    flex: 0 0 42px;
    display: grid;
    place-items: center;
    border: 0;
    border-radius: 13px;
    background: transparent;
    color: inherit;
    font-size: 19px;
}

.icon-button:hover {
    background: #ffffff20;
}

.search-trigger {
    min-width: 0;
    flex: 1;
    height: 43px;
    border: 0;
    border-radius: 25px;
    padding: 0 15px;
    background: #ffffff;
    color: #718096;
    display: flex;
    align-items: center;
    gap: 9px;
    text-align: right;
    overflow: hidden;
}

.search-trigger span {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
}

.brand {
    padding: 0 16px 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    font-size: 27px;
    font-weight: 800;
}

.brand i {
    font-size: 29px;
}

/* =========================
   شريط الصور
========================= */

.hero {
    width: min(1200px, calc(100% - 24px));
    height: clamp(210px, 36vw, 340px);
    position: relative;
    margin: 14px auto 24px;
    overflow: hidden;
    border-radius: 18px;
    background: #18334b;
    box-shadow: var(--shadow);
}

.hero-track {
    display: flex;
    direction: ltr;
    height: 100%;
    transition: transform .45s ease;
}

.hero-slide {
    flex: 0 0 100%;
    min-width: 100%;
    height: 100%;
    position: relative;
    overflow: hidden;
}

.hero-slide img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: brightness(.65);
}

.hero-slide::after {
    content: "";
    position: absolute;
    inset: 0;
    background: linear-gradient(
        90deg,
        transparent,
        rgba(0, 0, 0, .65)
    );
}

.hero-copy {
    position: absolute;
    z-index: 2;
    top: 50%;
    right: clamp(18px, 6vw, 70px);
    transform: translateY(-50%);
    width: min(550px, 78%);
    color: #fff;
}

.hero-copy h1 {
    margin: 0 0 8px;
    font-size: clamp(23px, 4vw, 39px);
    line-height: 1.5;
}

.hero-copy p {
    margin: 0 0 18px;
    font-size: clamp(13px, 2vw, 17px);
    line-height: 1.8;
}

.primary-button {
    min-height: 42px;
    padding: 9px 17px;
    border: 0;
    border-radius: 12px;
    background: var(--primary);
    color: white;
    font-weight: 700;
}

.hero-button {
    background: #fff;
    color: var(--primary);
    border-radius: 25px;
}

.hero-arrow {
    position: absolute;
    z-index: 4;
    top: 50%;
    transform: translateY(-50%);
    width: 38px;
    height: 38px;
    border: 0;
    border-radius: 50%;
    background: #071a2bb8;
    color: white;
}

.hero-prev {
    right: 12px;
}

.hero-next {
    left: 12px;
}

.hero-dots {
    position: absolute;
    z-index: 5;
    bottom: 13px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    direction: ltr;
    gap: 8px;
}

.hero-dot {
    width: 9px;
    height: 9px;
    padding: 0;
    border: 0;
    border-radius: 50%;
    background: #ffffff85;
}

.hero-dot.active {
    background: white;
    transform: scale(1.25);
}

/* =========================
   محتوى الموقع
========================= */

.page-container {
    width: min(1200px, calc(100% - 24px));
    margin: 0 auto 25px;
}

.welcome {
    padding: 18px;
    margin-bottom: 22px;
    border: 1px solid var(--border);
    border-radius: 16px;
    background: var(--surface);
    box-shadow: var(--shadow);
}

.welcome h2 {
    margin: 0;
    font-size: 21px;
}

.welcome p {
    margin: 5px 0 0;
    color: var(--muted);
    font-size: 13px;
    line-height: 1.8;
}

.section {
    margin: 26px 0 34px;
}

.section-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    margin-bottom: 13px;
}

.section-title {
    margin: 0;
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 19px;
}

.section-title i {
    color: var(--primary-light);
}

.link-button {
    padding: 6px;
    border: 0;
    background: transparent;
    color: var(--primary);
    font-size: 13px;
    font-weight: 800;
    white-space: nowrap;
}

/* =========================
   بطاقات الأقسام
========================= */

.categories-grid {
    display: grid;
    grid-template-columns: repeat(5, minmax(0, 1fr));
    gap: 11px;
}

.category-card {
    min-width: 0;
    padding: 10px 7px 8px;
    border: 1px solid var(--border);
    border-radius: 13px;
    background: var(--surface);
    box-shadow: var(--shadow);
    color: var(--text);
    text-align: center;
    transition: transform .2s;
}

.category-card:hover {
    transform: translateY(-3px);
}

.category-icon {
    width: 43px;
    height: 43px;
    margin: 0 auto 8px;
    display: grid;
    place-items: center;
    border-radius: 50%;
    background: var(--primary);
    color: white;
    font-size: 19px;
}

.category-name {
    min-height: 42px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 12px;
    font-weight: 800;
}

.category-cover {
    width: 100%;
    height: 75px;
    margin-top: 7px;
    object-fit: cover;
    border-radius: 8px;
}

/* =========================
   بطاقات الكتب
========================= */

.books-grid {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    gap: 12px;
}

.book-card {
    min-width: 0;
    overflow: hidden;
    border: 1px solid var(--border);
    border-radius: 13px;
    background: var(--surface);
    box-shadow: var(--shadow);
    cursor: pointer;
    transition: transform .2s, box-shadow .2s;
}

.book-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 9px 24px #12385d18;
}

.book-cover-wrap {
    height: 205px;
    position: relative;
    background: #eaf1f8;
}

.book-cover {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.favorite-button {
    position: absolute;
    top: 8px;
    right: 8px;
    width: 32px;
    height: 32px;
    border: 0;
    border-radius: 50%;
    background: #ffffffed;
    color: #b3bac5;
}

.favorite-button.active {
    color: var(--danger);
}

.book-info {
    padding: 10px;
}

.book-title {
    min-height: 44px;
    margin: 0;
    font-size: 13px;
    line-height: 1.7;
    font-weight: 800;
}

.book-author {
    margin: 4px 0 0;
    color: var(--muted);
    font-size: 11px;
    line-height: 1.7;
}

.book-stats {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 5px;
    margin-top: 9px;
    color: var(--muted);
    font-size: 10px;
}

.book-stats span {
    display: flex;
    align-items: center;
    gap: 4px;
}

.empty-state {
    padding: 30px 15px;
    border-radius: 14px;
    background: var(--surface);
    color: var(--muted);
    text-align: center;
    line-height: 1.9;
}

/* =========================
   القائمة الجانبية
========================= */

.sidebar-backdrop {
    position: fixed;
    z-index: 500;
    inset: 0;
    background: rgba(3, 17, 32, .6);
    opacity: 0;
    visibility: hidden;
    transition: opacity .25s, visibility .25s;
}

.sidebar-backdrop.active {
    opacity: 1;
    visibility: visible;
}

.sidebar {
    position: fixed;
    z-index: 501;
    top: 0;
    right: 0;
    bottom: 0;
    width: min(320px, 86vw);
    padding: 18px;
    overflow-y: auto;
    background: var(--surface);
    color: var(--text);
    transform: translateX(105%);
    transition: transform .25s ease;
    box-shadow: var(--shadow);
}

.sidebar.active {
    transform: translateX(0);
}

.sidebar-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    margin-bottom: 18px;
}

.sidebar-header h2 {
    margin: 0;
    font-size: 21px;
}

.sidebar-link {
    width: 100%;
    display: flex;
    align-items: center;
    gap: 12px;
    margin: 6px 0;
    padding: 12px;
    border: 0;
    border-radius: 10px;
    background: var(--background);
    color: var(--text);
    text-align: right;
}

.sidebar-link i {
    width: 20px;
    color: var(--primary);
}

.sidebar-link:hover {
    background: #dcecff;
}

/* =========================
   شريط التنقل السفلي
========================= */

.bottom-nav {
    position: fixed;
    z-index: 200;
    right: 0;
    bottom: 0;
    left: 0;
    min-height: var(--bottom-height);
    display: flex;
    align-items: center;
    justify-content: space-around;
    padding: 5px 4px;
    padding-bottom: max(5px, env(safe-area-inset-bottom));
    border-top: 1px solid var(--border);
    background: var(--surface);
    box-shadow: 0 -4px 18px #12385d0c;
}

.nav-button {
    min-width: 0;
    flex: 1;
    padding: 7px 2px;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    border: 0;
    border-radius: 10px;
    background: transparent;
    color: var(--muted);
    font-size: 10px;
}

.nav-button i {
    font-size: 20px;
}

.nav-button.active {
    color: var(--primary);
    font-weight: 800;
}

/* =========================
   النوافذ المنبثقة
========================= */

.overlay {
    position: fixed;
    z-index: 700;
    inset: 0;
    display: none;
    align-items: center;
    justify-content: center;
    padding: 14px;
    background: #071a2bd9;
}

.overlay.active {
    display: flex;
}

.modal {
    width: min(760px, 100%);
    max-height: 88dvh;
    overflow-y: auto;
    padding: 18px;
    border-radius: 17px;
    background: var(--surface);
    color: var(--text);
    box-shadow: 0 20px 60px #0004;
}

.modal-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    margin-bottom: 16px;
}

.modal-header h2 {
    margin: 0;
    font-size: 19px;
}

.close-button {
    width: 38px;
    height: 38px;
    flex: 0 0 38px;
    border: 0;
    border-radius: 50%;
    background: var(--background);
    color: var(--text);
}

.search-form {
    display: flex;
    gap: 8px;
    margin-bottom: 18px;
}

.search-input {
    min-width: 0;
    flex: 1;
    padding: 11px;
    border: 1px solid var(--border);
    border-radius: 10px;
    background: var(--surface);
    color: var(--text);
}

.results-grid {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 10px;
}

.result-card {
    min-width: 0;
    padding: 7px;
    border: 1px solid var(--border);
    border-radius: 10px;
    background: var(--surface);
    color: var(--text);
    text-align: right;
}

.result-card img {
    width: 100%;
    height: 130px;
    object-fit: cover;
    border-radius: 7px;
}

.result-card strong {
    display: block;
    margin-top: 7px;
    font-size: 12px;
}

.result-card small {
    color: var(--muted);
}

/* تفاصيل الكتاب */

.detail-layout {
    display: grid;
    grid-template-columns: 180px minmax(0, 1fr);
    gap: 20px;
}

.detail-cover {
    width: 100%;
    max-height: 270px;
    object-fit: cover;
    border-radius: 10px;
}

.detail-title {
    margin: 0 0 8px;
    font-size: 21px;
}

.detail-author {
    color: var(--muted);
    font-size: 13px;
}

.detail-description {
    line-height: 2;
    font-size: 14px;
}

.detail-actions {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 18px;
}

.secondary-button {
    min-height: 40px;
    padding: 8px 13px;
    border: 1px solid var(--border);
    border-radius: 10px;
    background: var(--background);
    color: var(--text);
    font-weight: 700;
}

/* قارئ النبذة */

.reader {
    width: min(760px, 100%);
    max-height: 88dvh;
    display: flex;
    flex-direction: column;
    border-radius: 16px;
    overflow: hidden;
    background: var(--surface);
    color: var(--text);
}

.reader-toolbar {
    padding: 12px;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    gap: 8px;
    border-bottom: 1px solid var(--border);
}

.reader-toolbar strong {
    flex: 1;
}

.reader-content {
    overflow-y: auto;
    padding: 22px;
    line-height: 2.1;
    white-space: pre-line;
}

/* التنبيهات */

.toast {
    position: fixed;
    z-index: 1000;
    right: 50%;
    bottom: calc(var(--bottom-height) + 16px);
    transform: translateX(50%);
    width: max-content;
    max-width: 90%;
    padding: 11px 16px;
    border-radius: 11px;
    background: #173653;
    color: #fff;
    box-shadow: var(--shadow);
    font-size: 13px;
    text-align: center;
    opacity: 0;
    visibility: hidden;
    transition: opacity .2s;
}

.toast.show {
    opacity: 1;
    visibility: visible;
}

/* =========================
   الوضع الليلي
========================= */

body.dark {
    --background: #0b1726;
    --surface: #132338;
    --text: #e4efff;
    --muted: #a8b8cc;
    --border: #2a3e55;
    --shadow: 0 5px 18px #0003;
}

body.dark .search-trigger {
    background: #f3f7fc;
    color: #52657a;
}

body.dark .category-icon {
    background: #245b93;
}

body.dark .sidebar-link:hover {
    background: #203a59;
}

/* =========================
   الشاشات المتوسطة
========================= */

@media (min-width: 900px) {
    .topbar-inner {
        min-height: 70px;
    }

    .brand {
        font-size: 30px;
    }
}

@media (max-width: 700px) {
    .topbar-inner {
        gap: 5px;
        padding: 8px 9px;
    }

    .icon-button {
        width: 35px;
        height: 38px;
        flex-basis: 35px;
        font-size: 16px;
    }

    .search-trigger {
        height: 39px;
        padding: 0 10px;
        font-size: 12px;
    }

    .brand {
        padding-bottom: 10px;
        font-size: 24px;
    }

    .hero {
        height: 230px;
        margin-top: 12px;
    }

    .page-container {
        width: calc(100% - 18px);
    }

    .categories-grid {
        grid-template-columns: repeat(5, minmax(0, 1fr));
        gap: 6px;
    }

    .category-card {
        padding: 8px 3px;
    }

    .category-icon {
        width: 35px;
        height: 35px;
        font-size: 15px;
    }

    .category-name {
        font-size: 10px;
        min-height: 38px;
    }

    .category-cover {
        height: 55px;
    }

    .books-grid {
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 8px;
    }

    .book-cover-wrap {
        height: 165px;
    }

    .book-info {
        padding: 7px;
    }

    .book-title {
        font-size: 12px;
        min-height: 41px;
    }

    .book-author {
        font-size: 10px;
    }

    .book-stats {
        font-size: 9px;
    }

    .detail-layout {
        grid-template-columns: 115px minmax(0, 1fr);
        gap: 12px;
    }

    .detail-title {
        font-size: 17px;
    }

    .detail-description {
        font-size: 12px;
    }
}

@media (max-width: 390px) {
    .hero {
        height: 210px;
    }

    .hero-copy {
        width: 75%;
        right: 42px;
    }

    .hero-copy h1 {
        font-size: 22px;
    }

    .hero-copy p {
        font-size: 12px;
    }

    .books-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    .book-cover-wrap {
        height: 205px;
    }

    .results-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    .nav-button {
        font-size: 9px;
    }

    .nav-button i {
        font-size: 18px;
    }
}

@media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
        scroll-behavior: auto !important;
        transition-duration: .01ms !important;
        animation-duration: .01ms !important;
    }
}
</style>
</head>

<body>

<!-- الشريط العلوي -->

<header class="topbar">
    <div class="topbar-inner">

        <button class="icon-button"
                onclick="toggleSidebar()"
                aria-label="فتح القائمة">
            <i class="fa-solid fa-bars"></i>
        </button>

        <button class="search-trigger" onclick="openSearch()">
            <i class="fa-solid fa-magnifying-glass"></i>
            <span>ابحث عن كتاب، مؤلف، أو قسم...</span>
        </button>

        <button class="icon-button"
                id="themeButton"
                onclick="toggleTheme()"
                aria-label="تغيير الوضع">
            <i class="fa-solid fa-moon"></i>
        </button>

        <button class="icon-button"
                onclick="shareSite()"
                aria-label="مشاركة الموقع">
            <i class="fa-solid fa-share-nodes"></i>
        </button>

    </div>

    <div class="brand">
        <i class="fa-solid fa-book-open"></i>
        <span>مكتبتي</span>
    </div>
</header>

<!-- شريط الصور -->

<section class="hero" aria-label="عروض المكتبة">

    <div class="hero-track" id="heroTrack">

        <article class="hero-slide">
            <img
                src="https://images.unsplash.com/photo-1481627834876-b7833e8f5570?auto=format&fit=crop&w=1400&q=80"
                alt="رفوف مكتبة مليئة بالكتب">

            <div class="hero-copy">
                <h1>اقرأ لتتغير حياتك</h1>
                <p>كل كتاب فرصة جديدة لاكتشاف عالم أوسع.</p>
                <button class="primary-button hero-button"
                        onclick="openSearch()">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    ابحث عن كتاب
                </button>
            </div>
        </article>

        <article class="hero-slide">
            <img
                src="https://images.unsplash.com/photo-1507842217343-583bb7270b66?auto=format&fit=crop&w=1400&q=80"
                alt="مكتبة هادئة">

            <div class="hero-copy">
                <h1>المعرفة تبدأ بكتاب</h1>
                <p>اكتشف مجالات جديدة وطوّر مهاراتك.</p>
                <button class="primary-button hero-button"
                        onclick="showSection('all')">
                    <i class="fa-solid fa-book-open"></i>
                    تصفح الكتب
                </button>
            </div>
        </article>

        <article class="hero-slide">
            <img
                src="https://images.unsplash.com/photo-1521587760476-6c12a4b040da?auto=format&fit=crop&w=1400&q=80"
                alt="رفوف الكتب">

            <div class="hero-copy">
                <h1>اختر كتابك التالي</h1>
                <p>من الروايات إلى العلوم والثقافة والدين.</p>
                <button class="primary-button hero-button"
                        onclick="showSection('categories')">
                    <i class="fa-solid fa-layer-group"></i>
                    استكشف الأقسام
                </button>
            </div>
        </article>

    </div>

    <button class="hero-arrow hero-prev"
            onclick="changeSlide(1)"
            aria-label="الصورة التالية">
        <i class="fa-solid fa-chevron-right"></i>
    </button>

    <button class="hero-arrow hero-next"
            onclick="changeSlide(-1)"
            aria-label="الصورة السابقة">
        <i class="fa-solid fa-chevron-left"></i>
    </button>

    <div class="hero-dots" id="heroDots">
        <button class="hero-dot active" onclick="goToSlide(0)" aria-label="الصورة 1"></button>
        <button class="hero-dot" onclick="goToSlide(1)" aria-label="الصورة 2"></button>
        <button class="hero-dot" onclick="goToSlide(2)" aria-label="الصورة 3"></button>
    </div>

</section>

<!-- المحتوى -->

<main class="page-container" id="mainContent">

    <section class="welcome">
        <h2 id="pageTitle">مرحبًا بك في مكتبتي</h2>
        <p id="pageSubtitle">
            اختر كتابًا جديدًا، فقد تكون بداخله فكرة تغيّر يومك.
        </p>
    </section>

    <div id="content"></div>

</main>

<!-- القائمة الجانبية -->

<div class="sidebar-backdrop"
     id="sidebarBackdrop"
     onclick="closeSidebar()"></div>

<aside class="sidebar" id="sidebar">

    <div class="sidebar-header">
        <h2><i class="fa-solid fa-book-open"></i> القائمة</h2>

        <button class="close-button"
                onclick="closeSidebar()"
                aria-label="إغلاق القائمة">
            <i class="fa-solid fa-xmark"></i>
        </button>
    </div>

    <button class="sidebar-link" onclick="navigate('home')">
        <i class="fa-solid fa-house"></i>
        الرئيسية
    </button>

    <button class="sidebar-link" onclick="navigate('all')">
        <i class="fa-solid fa-book"></i>
        جميع الكتب
    </button>

    <button class="sidebar-link" onclick="navigate('categories')">
        <i class="fa-solid fa-layer-group"></i>
        الأقسام
    </button>

    <button class="sidebar-link" onclick="navigate('favorites')">
        <i class="fa-solid fa-heart"></i>
        مكتبتي والمفضلة
    </button>

    <button class="sidebar-link" onclick="navigate('history')">
        <i class="fa-solid fa-clock-rotate-left"></i>
        سجل القراءة
    </button>

    <button class="sidebar-link" onclick="navigate('downloaded')">
        <i class="fa-solid fa-download"></i>
        الكتب المحفوظة
    </button>

    <button class="sidebar-link" onclick="navigate('about')">
        <i class="fa-solid fa-circle-info"></i>
        حول الموقع
    </button>

    <hr style="border:0;border-top:1px solid var(--border);margin:18px 0">

    <button class="sidebar-link" onclick="shareSite()">
        <i class="fa-solid fa-share-nodes"></i>
        مشاركة الموقع
    </button>

</aside>

<!-- نافذة البحث -->

<div class="overlay" id="searchOverlay">
    <div class="modal">

        <div class="modal-header">
            <h2><i class="fa-solid fa-magnifying-glass"></i> البحث عن الكتب</h2>

            <button class="close-button"
                    onclick="closeModal('searchOverlay')"
                    aria-label="إغلاق البحث">
                <i class="fa-solid fa-xmark"></i>
            </button>
        </div>

        <form class="search-form" onsubmit="submitSearch(event)">
            <input class="search-input"
                   id="searchInput"
                   type="search"
                   placeholder="اسم الكتاب أو المؤلف أو القسم..."
                   autocomplete="off">

            <button class="primary-button" type="submit">بحث</button>
        </form>

        <div id="searchResults"></div>

    </div>
</div>

<!-- تفاصيل الكتاب -->

<div class="overlay" id="detailsOverlay">
    <div class="modal">

        <div class="modal-header">
            <h2>تفاصيل الكتاب</h2>

            <button class="close-button"
                    onclick="closeModal('detailsOverlay')"
                    aria-label="إغلاق التفاصيل">
                <i class="fa-solid fa-xmark"></i>
            </button>
        </div>

        <div id="bookDetails"></div>

    </div>
</div>

<!-- قارئ النبذة -->

<div class="overlay" id="readerOverlay">
    <div class="reader">

        <div class="reader-toolbar">
            <strong id="readerTitle">القراءة</strong>

            <button class="secondary-button" onclick="changeFontSize(-1)">A−</button>
            <button class="secondary-button" onclick="changeFontSize(1)">A+</button>

            <button class="secondary-button" onclick="saveBookmark()">
                <i class="fa-solid fa-bookmark"></i>
                حفظ الموضع
            </button>

            <button class="close-button"
                    onclick="closeModal('readerOverlay')"
                    aria-label="إغلاق القراءة">
                <i class="fa-solid fa-xmark"></i>
            </button>
        </div>

        <div class="reader-content"
             id="readerContent"
             tabindex="0"></div>

    </div>
</div>

<!-- شريط التنقل السفلي -->

<nav class="bottom-nav" aria-label="التنقل الرئيسي">

    <button class="nav-button active"
            data-page="home"
            onclick="navigate('home')">
        <i class="fa-solid fa-house"></i>
        <span>الرئيسية</span>
    </button>

    <button class="nav-button"
            data-page="categories"
            onclick="navigate('categories')">
        <i class="fa-solid fa-layer-group"></i>
        <span>الأقسام</span>
    </button>

    <button class="nav-button"
            data-page="favorites"
            onclick="navigate('favorites')">
        <i class="fa-solid fa-book-bookmark"></i>
        <span>مكتبتي</span>
    </button>

    <button class="nav-button"
            data-page="history"
            onclick="navigate('history')">
        <i class="fa-solid fa-clock-rotate-left"></i>
        <span>السجل</span>
    </button>

    <button class="nav-button"
            data-page="about"
            onclick="navigate('about')">
        <i class="fa-solid fa-user"></i>
        <span>الملف الشخصي</span>
    </button>

</nav>

<div class="toast" id="toast" role="status" aria-live="polite"></div>

<!-- القسم الثاني يوضع هنا -->
<!-- القسم الثاني يوضع هنا --><script>
"use strict";

/* ============================
   بيانات الكتب
============================ */

const books = [
    {
        id: 1,
        title: "العادات الذرية",
        author: "جيمس كلير",
        category: "تطوير الذات",
        description: "كتاب يتناول بناء العادات الصغيرة وتحسين السلوك تدريجيًا. المعروض هنا نبذة تعريفية فقط.",
        cover: "https://covers.openlibrary.org/b/isbn/9780735211292-L.jpg",
        likes: 42,
        views: 850,
        downloads: 120
    },
    {
        id: 2,
        title: "الأب الغني والأب الفقير",
        author: "روبرت كيوساكي",
        category: "ثقافية",
        description: "يتناول الكتاب مفاهيم الثقافة المالية والأصول والالتزامات والتخطيط المالي.",
        cover: "https://covers.openlibrary.org/b/isbn/9781612680194-L.jpg",
        likes: 51,
        views: 940,
        downloads: 140
    },
    {
        id: 3,
        title: "مقدمة ابن خلدون",
        author: "عبد الرحمن بن خلدون",
        category: "ثقافية",
        description: "عمل تراثي بارز يناقش التاريخ والعمران والاجتماع البشري.",
        cover: "https://covers.openlibrary.org/b/isbn/9780140449150-L.jpg",
        likes: 33,
        views: 680,
        downloads: 81
    },
    {
        id: 4,
        title: "الأمير",
        author: "نيكولو مكيافيلي",
        category: "قانونية",
        description: "نص كلاسيكي يناقش الحكم والسياسة والسلطة في سياقه التاريخي.",
        cover: "https://covers.openlibrary.org/b/isbn/9780140449150-L.jpg",
        likes: 22,
        views: 490,
        downloads: 53
    },
    {
        id: 5,
        title: "تعلم البرمجة للمبتدئين",
        author: "فريق مكتبتي",
        category: "تقنية",
        description: "مقدمة تعريفية بالمفاهيم الأساسية للبرمجة.",
        cover: "https://images.unsplash.com/photo-1515879218367-8466d910aaa4?auto=format&fit=crop&w=500&q=80",
        likes: 31,
        views: 520,
        downloads: 65
    },
    {
        id: 6,
        title: "مبادئ علم النفس",
        author: "فريق مكتبتي",
        category: "تعليمية",
        description: "نبذة تمهيدية عن موضوعات علم النفس الأساسية.",
        cover: "https://images.unsplash.com/photo-1456513080510-7bf3a84b82f8?auto=format&fit=crop&w=500&q=80",
        likes: 19,
        views: 360,
        downloads: 42
    },
    {
        id: 7,
        title: "رحلة إلى مركز الأرض",
        author: "جول فيرن",
        category: "روايات وقصص",
        description: "رواية مغامرات كلاسيكية عن رحلة استكشافية خيالية إلى باطن الأرض.",
        cover: "https://covers.openlibrary.org/b/isbn/9780140449129-L.jpg",
        likes: 27,
        views: 580,
        downloads: 71
    },
    {
        id: 8,
        title: "حول العالم في 80 يومًا",
        author: "جول فيرن",
        category: "روايات وقصص",
        description: "رواية مغامرات حول رهان للقيام برحلة حول العالم خلال مدة محددة.",
        cover: "https://covers.openlibrary.org/b/isbn/9780140449068-L.jpg",
        likes: 24,
        views: 510,
        downloads: 60
    },
    {
        id: 9,
        title: "مدخل إلى العلوم",
        author: "فريق مكتبتي",
        category: "علمية",
        description: "مقدمة مبسطة إلى التفكير العلمي والملاحظة والاستنتاج.",
        cover: "https://images.unsplash.com/photo-1532094349884-543bc11b234d?auto=format&fit=crop&w=500&q=80",
        likes: 16,
        views: 290,
        downloads: 29
    },
    {
        id: 10,
        title: "مختارات من الحكم",
        author: "مجموعة مؤلفين",
        category: "دينية",
        description: "نبذة تعريفية عن مجموعة من الحكم والمواعظ. يجب إضافة مصدر موثوق للنص الكامل.",
        cover: "https://images.unsplash.com/photo-1609599006353-e629aaabfeae?auto=format&fit=crop&w=500&q=80",
        likes: 39,
        views: 800,
        downloads: 110
    },
    {
        id: 11,
        title: "فكر تصبح غنيًا",
        author: "نابليون هيل",
        category: "تطوير الذات",
        description: "يتناول تحديد الأهداف والتفكير والمثابرة في سبيل تحقيقها.",
        cover: "https://covers.openlibrary.org/b/isbn/9781585424337-L.jpg",
        likes: 36,
        views: 720,
        downloads: 98
    },
    {
        id: 12,
        title: "قوة الآن",
        author: "إيكهارت تول",
        category: "تطوير الذات",
        description: "مقدمة إلى الانتباه للحظة الحالية والتعامل مع الأفكار.",
        cover: "https://covers.openlibrary.org/b/isbn/9781577314806-L.jpg",
        likes: 28,
        views: 610,
        downloads: 76
    }
];

/* ============================
   الأقسام
============================ */

const categoryInfo = [
    {
        name: "كتب شائعة",
        icon: "fa-fire",
        category: null,
        cover: "https://images.unsplash.com/photo-1544947950-fa07a98d237f?auto=format&fit=crop&w=400&q=80"
    },
    {
        name: "دينية",
        icon: "fa-mosque",
        category: "دينية",
        cover: "https://images.unsplash.com/photo-1609599006353-e629aaabfeae?auto=format&fit=crop&w=400&q=80"
    },
    {
        name: "ثقافية",
        icon: "fa-globe",
        category: "ثقافية",
        cover: "https://images.unsplash.com/photo-1524995997946-a1c2e315a42f?auto=format&fit=crop&w=400&q=80"
    },
    {
        name: "روايات وقصص",
        icon: "fa-feather",
        category: "روايات وقصص",
        cover: "https://images.unsplash.com/photo-1512820790803-83ca734da794?auto=format&fit=crop&w=400&q=80"
    },
    {
        name: "تعليمية",
        icon: "fa-graduation-cap",
        category: "تعليمية",
        cover: "https://images.unsplash.com/photo-1503676260728-1c00da094a0b?auto=format&fit=crop&w=400&q=80"
    },
    {
        name: "تطوير الذات",
        icon: "fa-pen",
        category: "تطوير الذات",
        cover: "https://images.unsplash.com/photo-1455390582262-044cdead277a?auto=format&fit=crop&w=400&q=80"
    },
    {
        name: "علمية",
        icon: "fa-flask",
        category: "علمية",
        cover: "https://images.unsplash.com/photo-1532094349884-543bc11b234d?auto=format&fit=crop&w=400&q=80"
    },
    {
        name: "قانونية",
        icon: "fa-scale-balanced",
        category: "قانونية",
        cover: "https://images.unsplash.com/photo-1589829545856-d10d557cf95f?auto=format&fit=crop&w=400&q=80"
    },
    {
        name: "تقنية",
        icon: "fa-laptop-code",
        category: "تقنية",
        cover: "https://images.unsplash.com/photo-1515879218367-8466d910aaa4?auto=format&fit=crop&w=400&q=80"
    }
];

const KEY = {
    favorites: "maktabati_v2_favorites",
    history: "maktabati_v2_history",
    downloads: "maktabati_v2_downloads",
    views: "maktabati_v2_views",
    bookmarks: "maktabati_v2_bookmarks",
    theme: "maktabati_v2_theme"
};

let slideIndex = 0;
let slideTimer = null;
let currentBook = null;
let fontSize = 18;
let toastTimer = null;
let currentPage = "home";

/* ============================
   أدوات مساعدة
============================ */

function readStore(key, fallback) {
    try {
        const value = localStorage.getItem(key);
        return value === null ? fallback : JSON.parse(value);
    } catch {
        return fallback;
    }
}

function writeStore(key, value) {
    try {
        localStorage.setItem(key, JSON.stringify(value));
    } catch {
        notify("تعذر حفظ البيانات في المتصفح.");
    }
}

function escapeHTML(value) {
    return String(value ?? "").replace(/[&<>"']/g, char => ({
        "&": "&amp;",
        "<": "&lt;",
        ">": "&gt;",
        '"': "&quot;",
        "'": "&#39;"
    })[char]);
}

function getBook(id) {
    return books.find(book => book.id === Number(id));
}

function getFavorites() {
    return readStore(KEY.favorites, []);
}

function getDownloads() {
    return readStore(KEY.downloads, []);
}

function getViews(book) {
    const values = readStore(KEY.views, {});
    return Number(values[book.id] ?? book.views);
}

function getLikes(book) {
    const values = readStore("maktabati_v2_likes", {});
    return Number(values[book.id] ?? book.likes);
}

function notify(message) {
    const toast = document.getElementById("toast");

    toast.textContent = message;
    toast.classList.add("show");

    clearTimeout(toastTimer);

    toastTimer = setTimeout(() => {
        toast.classList.remove("show");
    }, 2600);
}

function imageFallback(image) {
    image.onerror = null;
    image.src =
        "https://placehold.co/400x600/eaf1f8/1761ad?text=Maktabati";
}

/* ============================
   بناء بطاقات الكتب
============================ */

function bookCard(book) {
    const favorites = getFavorites();
    const isFavorite = favorites.includes(book.id);

    return `
        <article class="book-card">

            <div class="book-cover-wrap"
                 onclick="openBook(${book.id})">

                <img
                    class="book-cover"
                    src="${escapeHTML(book.cover)}"
                    alt="غلاف ${escapeHTML(book.title)}"
                    loading="lazy"
                    onerror="imageFallback(this)">

                <button
                    class="favorite-button ${isFavorite ? "active" : ""}"
                    onclick="event.stopPropagation(); toggleFavorite(${book.id})"
                    aria-label="إضافة إلى المفضلة">
                    <i class="fa-solid fa-heart"></i>
                </button>

            </div>

            <div class="book-info"
                 onclick="openBook(${book.id})">

                <h3 class="book-title">${escapeHTML(book.title)}</h3>

                <p class="book-author">${escapeHTML(book.author)}</p>

                <div class="book-stats">
                    <span title="مرات القراءة">
                        <i class="fa-solid fa-eye"></i>
                        ${getViews(book)}
                    </span>

                    <span title="الإعجابات">
                        <i class="fa-solid fa-heart"></i>
                        ${getLikes(book)}
                    </span>
                </div>

            </div>
        </article>
    `;
}

function bookGrid(list) {
    if (!list.length) {
        return `
            <div class="empty-state">
                <i class="fa-solid fa-book-open"></i>
                <p>لا توجد كتب في هذه القائمة حاليًا.</p>
            </div>
        `;
    }

    return `
        <div class="books-grid">
            ${list.map(bookCard).join("")}
        </div>
    `;
}

function sectionBlock(title, list, page, icon = "fa-book-open") {
    if (!list.length) return "";

    return `
        <section class="section">

            <div class="section-header">
                <h2 class="section-title">
                    <i class="fa-solid ${icon}"></i>
                    ${escapeHTML(title)}
                </h2>

                <button class="link-button"
                        onclick="navigate('${page}')">
                    عرض الكل ←
                </button>
            </div>

            ${bookGrid(list)}

        </section>
    `;
}

/* ============================
   بطاقات الأقسام
============================ */

function categoryCards() {
    return `
        <section class="section">

            <div class="section-header">
                <h2 class="section-title">
                    <i class="fa-solid fa-layer-group"></i>
                    الأقسام الرئيسية
                </h2>

                <button class="link-button"
                        onclick="navigate('categories')">
                    عرض الكل ←
                </button>
            </div>

            <div class="categories-grid">
                ${categoryInfo.map((item, index) => `
                    <button class="category-card"
                            onclick="navigateCategory(${index})">

                        <span class="category-icon">
                            <i class="fa-solid ${item.icon}"></i>
                        </span>

                        <span class="category-name">
                            ${escapeHTML(item.name)}
                        </span>

                        <img class="category-cover"
                             src="${escapeHTML(item.cover)}"
                             alt=""
                             loading="lazy"
                             onerror="imageFallback(this)">

                    </button>
                `).join("")}
            </div>

        </section>
    `;
}

function navigateCategory(index) {
    const category = categoryInfo[index];

    if (!category) return;

    if (category.category === null) {
        navigate("all");
    } else {
        navigate("category:" + category.category);
    }
}

/* ============================
   عرض الصفحات
============================ */

function renderHome() {
    const popular = [...books]
        .sort((a, b) => getViews(b) - getViews(a))
        .slice(0, 4);

    const religious = books.filter(book => book.category === "دينية");
    const cultural = books.filter(book => book.category === "ثقافية");
    const novels = books.filter(book => book.category === "روايات وقصص");

    document.getElementById("content").innerHTML =
        categoryCards() +
        sectionBlock("كتب شائعة", popular, "all", "fa-fire") +
        sectionBlock("كتب دينية", religious, "category:دينية", "fa-mosque") +
        sectionBlock("كتب ثقافية", cultural, "category:ثقافية", "fa-globe") +
        sectionBlock("روايات وقصص", novels, "category:روايات وقصص", "fa-feather") +
        sectionBlock(
            "تطوير الذات",
            books.filter(book => book.category === "تطوير الذات"),
            "category:تطوير الذات",
            "fa-lightbulb"
        );

    setPageHeading(
        "مرحبًا بك في مكتبتي",
        "اكتشف كتبًا جديدة في مجالات مختلفة."
    );
}

function renderCategories() {
    document.getElementById("content").innerHTML =
        categoryCards();

    setPageHeading(
        "أقسام المكتبة",
        "اختر القسم الذي تريد تصفح كتبه."
    );
}

function renderAllBooks() {
    document.getElementById("content").innerHTML =
        sectionBlock("جميع الكتب", books, "all");

    setPageHeading(
        "جميع الكتب",
        "تصفح الكتب المتاحة في المكتبة."
    );
}

function renderCategory(name) {
    const list = books.filter(book => book.category === name);

    document.getElementById("content").innerHTML =
        sectionBlock(name, list, "all");

    setPageHeading(
        name,
        "الكتب المتوفرة في هذا القسم."
    );
}

function renderFavorites() {
    const ids = getFavorites();
    const list = books.filter(book => ids.includes(book.id));

    document.getElementById("content").innerHTML =
        sectionBlock("كتبي المفضلة", list, "all", "fa-heart");

    setPageHeading(
        "مكتبتي",
        "الكتب التي أضفتها إلى المفضلة."
    );
}

function renderHistory() {
    const ids = readStore(KEY.history, []);
    const list = ids.map(getBook).filter(Boolean);

    document.getElementById("content").innerHTML =
        sectionBlock("سجل القراءة", list, "all", "fa-clock-rotate-left");

    setPageHeading(
        "سجل القراءة",
        "الكتب التي فتحتها مؤخرًا."
    );
}

function renderDownloads() {
    const ids = getDownloads();
    const list = books.filter(book => ids.includes(book.id));

    document.getElementById("content").innerHTML =
        sectionBlock("الكتب المحفوظة", list, "all", "fa-download");

    setPageHeading(
        "الكتب المحفوظة",
        "الكتب التي حفظت بياناتها على جهازك."
    );
}

function renderAbout() {
    document.getElementById("content").innerHTML = `
        <div class="welcome">
            <h2>عن مكتبتي</h2>
            <p>
                مكتبتي واجهة تجريبية لاكتشاف الكتب وتصنيفها
                وحفظ المفضلة وسجل القراءة على الجهاز.
            </p>
            <p>
                القراءة المتاحة في هذه النسخة تعرض نبذة تعريفية،
                وليست النص الكامل للكتب.
            </p>
        </div>
    `;

    setPageHeading("الملف الشخصي", "مرحبًا بك في مكتبتي.");
}

function setPageHeading(title, subtitle) {
    document.getElementById("pageTitle").textContent = title;
    document.getElementById("pageSubtitle").textContent = subtitle;
}

/* ============================
   التنقل
============================ */

function navigate(page) {
    currentPage = page;

    if (page === "home") renderHome();
    else if (page === "all") renderAllBooks();
    else if (page === "categories") renderCategories();
    else if (page === "favorites") renderFavorites();
    else if (page === "history") renderHistory();
    else if (page === "downloaded") renderDownloads();
    else if (page === "about") renderAbout();
    else if (page.startsWith("category:")) {
        renderCategory(page.slice("category:".length));
    }

    document.querySelectorAll(".nav-button").forEach(button => {
        button.classList.toggle(
            "active",
            button.dataset.page === page
        );
    });

    closeSidebar();

    window.scrollTo({
        top: 0,
        behavior: "smooth"
    });
}

/* ============================
   تفاصيل الكتاب
============================ */

function openBook(id) {
    const book = getBook(id);

    if (!book) return;

    const views = readStore(KEY.views, {});
    views[id] = getViews(book) + 1;
    writeStore(KEY.views, views);

    currentBook = book.id;

    const history = readStore(KEY.history, []);
    const updatedHistory = [
        book.id,
        ...history.filter(bookId => bookId !== book.id)
    ].slice(0, 50);

    writeStore(KEY.history, updatedHistory);

    const isFavorite = getFavorites().includes(book.id);

    document.getElementById("bookDetails").innerHTML = `
        <div class="detail-layout">

            <img class="detail-cover"
                 src="${escapeHTML(book.cover)}"
                 alt="غلاف ${escapeHTML(book.title)}"
                 onerror="imageFallback(this)">

            <div>
                <h2 class="detail-title">${escapeHTML(book.title)}</h2>

                <p class="detail-author">
                    المؤلف: ${escapeHTML(book.author)}
                </p>

                <p class="detail-author">
                    القسم: ${escapeHTML(book.category)}
                </p>

                <p class="detail-description">
                    ${escapeHTML(book.description)}
                </p>

                <div class="book-stats">
                    <span><i class="fa-solid fa-eye"></i> ${getViews(book)}</span>
                    <span><i class="fa-solid fa-heart"></i> ${getLikes(book)}</span>
                </div>

                <div class="detail-actions">

                    <button class="primary-button"
                            onclick="readBook(${book.id})">
                        <i class="fa-solid fa-book-open"></i>
                        قراءة النبذة
                    </button>

                    <button class="secondary-button"
                            onclick="toggleFavorite(${book.id})">
                        <i class="fa-solid fa-heart"></i>
                        ${isFavorite ? "إزالة من مكتبتي" : "إضافة إلى مكتبتي"}
                    </button>

                    <button class="secondary-button"
                            onclick="saveBookInfo(${book.id})">
                        <i class="fa-solid fa-download"></i>
                        حفظ معلومات الكتاب
                    </button>

                </div>

                <p class="book-author">
                    ملف PDF الكامل غير متوفر لهذا الكتاب في النسخة التجريبية.
                </p>
            </div>

        </div>
    `;

    closeModal("searchOverlay");
    document.getElementById("detailsOverlay").classList.add("active");
}

function toggleFavorite(id) {
    const book = getBook(id);
    if (!book) return;

    let favorites = getFavorites();
    const likes = readStore("maktabati_v2_likes", {});
    const alreadyFavorite = favorites.includes(id);

    if (alreadyFavorite) {
        favorites = favorites.filter(bookId => bookId !== id);
        likes[id] = Math.max(0, getLikes(book) - 1);
        notify("أُزيل الكتاب من المفضلة.");
    } else {
        favorites.unshift(id);
        likes[id] = getLikes(book) + 1;
        notify("أُضيف الكتاب إلى المفضلة.");
    }

    writeStore(KEY.favorites, favorites);
    writeStore("maktabati_v2_likes", likes);

    if (document.getElementById("detailsOverlay").classList.contains("active")) {
        openBook(id);
    } else {
        navigate(currentPage);
    }
}

/* ============================
   قارئ النبذة
============================ */

function readBook(id) {
    const book = getBook(id);
    if (!book) return;

    currentBook = id;

    document.getElementById("readerTitle").textContent = book.title;

    const content = document.getElementById("readerContent");

    content.textContent =
        book.title + "\n\n" +
        "المؤلف: " + book.author + "\n\n" +
        book.description + "\n\n" +
        "هذه نبذة تعريفية تجريبية وليست النص الكامل للكتاب. " +
        "لإتاحة القراءة الكاملة، أضف نصًا تملك حق نشره أو رابطًا قانونيًا لنسخة متاحة.";

    content.style.fontSize = fontSize + "px";

    const bookmarks = readStore(KEY.bookmarks, {});
    content.scrollTop = bookmarks[id] || 0;

    closeModal("detailsOverlay");
    document.getElementById("readerOverlay").classList.add("active");
}

function changeFontSize(change) {
    fontSize = Math.min(30, Math.max(14, fontSize + change * 2));

    document.getElementById("readerContent").style.fontSize =
        fontSize + "px";
}

function saveBookmark() {
    if (!currentBook) return;

    const bookmarks = readStore(KEY.bookmarks, {});
    bookmarks[currentBook] =
        document.getElementById("readerContent").scrollTop;

    writeStore(KEY.bookmarks, bookmarks);

    notify("تم حفظ موضع القراءة.");
}

/* ============================
   حفظ بطاقة الكتاب
============================ */

function saveBookInfo(id) {
    const book = getBook(id);
    if (!book) return;

    const downloads = getDownloads();

    if (!downloads.includes(id)) {
        downloads.unshift(id);
        writeStore(KEY.downloads, downloads);
    }

    const text =
        "عنوان الكتاب: " + book.title + "\n" +
        "المؤلف: " + book.author + "\n" +
        "القسم: " + book.category + "\n\n" +
        book.description;

    const blob = new Blob(
        [text],
        { type: "text/plain;charset=utf-8" }
    );

    const url = URL.createObjectURL(blob);
    const link = document.createElement("a");

    link.href = url;
    link.download = "معلومات-" + book.id + ".txt";

    document.body.appendChild(link);
    link.click();
    link.remove();

    setTimeout(() => URL.revokeObjectURL(url), 1000);

    notify("تم حفظ معلومات الكتاب، وليس ملف PDF.");
}

/* ============================
   البحث
============================ */

function openSearch() {
    document.getElementById("searchOverlay").classList.add("active");

    displaySearchResults(books);

    setTimeout(() => {
        document.getElementById("searchInput").focus();
    }, 100);
}

function submitSearch(event) {
    event.preventDefault();
    performSearch();
}

function performSearch() {
    const query = document.getElementById("searchInput")
        .value.trim().toLocaleLowerCase("ar");

    const results = books.filter(book => {
        const text = [
            book.title,
            book.author,
            book.category,
            book.description
        ].join(" ").toLocaleLowerCase("ar");

        return text.includes(query);
    });

    displaySearchResults(results, query ? "نتائج البحث" : "جميع الكتب");
}

function displaySearchResults(results, title = "نتائج البحث") {
    const box = document.getElementById("searchResults");

    if (!results.length) {
        box.innerHTML = `
            <div class="empty-state">
                لم نعثر على كتب مطابقة لبحثك.
            </div>
        `;
        return;
    }

    box.innerHTML = `
        <p>${escapeHTML(title)} (${results.length})</p>

        <div class="results-grid">
            ${results.map(book => `
                <button class="result-card"
                        onclick="openBook(${book.id})">

                    <img src="${escapeHTML(book.cover)}"
                         alt=""
                         loading="lazy"
                         onerror="imageFallback(this)">

                    <strong>${escapeHTML(book.title)}</strong>
                    <small>${escapeHTML(book.author)}</small>

                </button>
            `).join("")}
        </div>
    `;
}

document.getElementById("searchInput")
    .addEventListener("input", performSearch);

/* ============================
   القائمة الجانبية
============================ */

function toggleSidebar() {
    const sidebar = document.getElementById("sidebar");
    const backdrop = document.getElementById("sidebarBackdrop");

    const shouldOpen = !sidebar.classList.contains("active");

    sidebar.classList.toggle("active", shouldOpen);
    backdrop.classList.toggle("active", shouldOpen);

    document.body.style.overflow = shouldOpen ? "hidden" : "";
}

function closeSidebar() {
    document.getElementById("sidebar").classList.remove("active");
    document.getElementById("sidebarBackdrop").classList.remove("active");
    document.body.style.overflow = "";
}

/* ============================
   الوضع الليلي
============================ */

function toggleTheme() {
    const dark = document.body.classList.toggle("dark");

    try {
        localStorage.setItem(KEY.theme, dark ? "dark" : "light");
    } catch {}

    updateThemeIcon();
}

function updateThemeIcon() {
    const dark = document.body.classList.contains("dark");

    document.getElementById("themeButton").innerHTML = dark
        ? '<i class="fa-solid fa-sun"></i>'
        : '<i class="fa-solid fa-moon"></i>';
}

/* ============================
   مشاركة الموقع
============================ */

async function shareSite() {
    const data = {
        title: "مكتبتي",
        text: "اكتشف الكتب في مكتبتي",
        url: location.href
    };

    try {
        if (navigator.share) {
            await navigator.share(data);
        } else {
            await navigator.clipboard.writeText(location.href);
            notify("تم نسخ رابط الموقع.");
        }
    } catch (error) {
        if (error.name !== "AbortError") {
            window.prompt("انسخ رابط الموقع:", location.href);
        }
    }
}

/* ============================
   النوافذ
============================ */

function closeModal(id) {
    document.getElementById(id).classList.remove("active");
}

document.querySelectorAll(".overlay").forEach(overlay => {
    overlay.addEventListener("click", event => {
        if (event.target === overlay) {
            overlay.classList.remove("active");
        }
    });
});

document.addEventListener("keydown", event => {
    if (event.key === "Escape") {
        document.querySelectorAll(".overlay.active").forEach(overlay => {
            overlay.classList.remove("active");
        });

        closeSidebar();
    }
});

/* ============================
   شريط الصور التلقائي
============================ */

function renderSlide() {
    const track = document.getElementById("heroTrack");
    const dots = document.querySelectorAll(".hero-dot");

    track.style.transform = `translateX(${slideIndex * 100}%)`;

    dots.forEach((dot, index) => {
        dot.classList.toggle("active", index === slideIndex);
    });
}

function changeSlide(direction) {
    const total = document.querySelectorAll(".hero-slide").length;

    slideIndex = (slideIndex + direction + total) % total;

    renderSlide();
    restartSlider();
}

function goToSlide(index) {
    slideIndex = index;
    renderSlide();
    restartSlider();
}

function startSlider() {
    stopSlider();

    if (!window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
        slideTimer = setInterval(() => {
            const total = document.querySelectorAll(".hero-slide").length;

            slideIndex = (slideIndex + 1) % total;
            renderSlide();
        }, 5000);
    }
}

function stopSlider() {
    if (slideTimer !== null) {
        clearInterval(slideTimer);
        slideTimer = null;
    }
}

function restartSlider() {
    startSlider();
}

document.querySelector(".hero").addEventListener("mouseenter", stopSlider);
document.querySelector(".hero").addEventListener("mouseleave", startSlider);

/* ============================
   تشغيل الموقع
============================ */

(function init() {
    try {
        if (localStorage.getItem(KEY.theme) === "dark") {
            document.body.classList.add("dark");
        }
    } catch {}

    updateThemeIcon();
    renderHome();
    renderSlide();
    startSlider();
})();
</script>

</body>
</html>
