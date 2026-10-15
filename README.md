<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="مكتبتي — مكتبة رقمية عربية لاكتشاف الكتب وقراءتها وحفظها.">
<meta name="theme-color" content="#1c5fad">
<title>مكتبتي | المكتبة الرقمية العربية</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">

<style>
:root {
    --primary: #1c5fad;
    --primary2: #4da6ff;
    --accent: #e74c3c;
    --text: #0d3b66;
    --muted: #64748b;
    --surface: #ffffff;
    --page: #f2f7fc;
    --line: #e2e8f0;
    --shadow: 0 10px 28px rgba(13,59,102,.12);
    --nav-height: 70px;
}

* {
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: 'Cairo', Tahoma, sans-serif;
    margin: 0;
    padding: 0 0 calc(var(--nav-height) + 14px);
    background: var(--page);
    color: var(--text);
    transition: background .25s, color .25s;
    overflow-x: hidden;
}

button, input, textarea {
    font: inherit;
}

button {
    cursor: pointer;
}

img {
    max-width: 100%;
    display: block;
}

/* الشريط العلوي */

.topbar {
    height: 60px;
    position: fixed;
    z-index: 1000;
    top: 0;
    right: 0;
    left: 0;
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 0 16px;
    background: rgba(255,255,255,.96);
    box-shadow: 0 2px 12px rgba(13,59,102,.1);
    backdrop-filter: blur(12px);
}

.icon-btn {
    width: 40px;
    height: 40px;
    border: 0;
    border-radius: 12px;
    background: transparent;
    color: var(--text);
    font-size: 18px;
    display: grid;
    place-items: center;
}

.icon-btn:hover {
    background: #eaf3ff;
}

.brand {
    font-size: 21px;
    font-weight: 800;
    margin: auto;
    white-space: nowrap;
}

.brand span {
    color: var(--primary2);
}

/* شريط الصور العلوي */

.hero-slider {
    position: relative;
    width: 100%;
    height: clamp(250px, 38vw, 400px);
    overflow: hidden;
    margin-top: 60px;
    border-radius: 0 0 20px 20px;
    box-shadow: var(--shadow);
    background: #123;
}

.slides-container {
    display: flex;
    width: 100%;
    height: 100%;
    direction: ltr;
    transition: transform .55s ease-in-out;
}

.slide {
    flex: 0 0 100%;
    position: relative;
    min-width: 100%;
    height: 100%;
    overflow: hidden;
}

.slide img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: brightness(.55);
}

.slide::after {
    content: "";
    position: absolute;
    inset: 0;
    background: linear-gradient(
        90deg,
        rgba(0,0,0,.05),
        rgba(0,0,0,.48)
    );
}

.slide-content {
    position: absolute;
    z-index: 1;
    top: 50%;
    right: clamp(22px, 7vw, 90px);
    transform: translateY(-50%);
    color: white;
    text-shadow: 0 2px 7px #0008;
    max-width: min(600px, 78%);
}

.slide-content h2 {
    font-size: clamp(1.4rem, 3.2vw, 2.5rem);
    line-height: 1.4;
    margin: 0 0 12px;
}

.slide-content p {
    font-size: clamp(.9rem, 1.6vw, 1.2rem);
    margin: 0 0 22px;
}

.hero-btn {
    background: var(--primary2);
    color: white;
    border: 0;
    padding: 10px 20px;
    border-radius: 30px;
    display: inline-flex;
    align-items: center;
    gap: 9px;
    transition: .2s;
    box-shadow: 0 5px 15px #0002;
}

.hero-btn:hover {
    background: var(--primary);
    transform: translateY(-2px);
}

.slide-nav {
    position: absolute;
    z-index: 3;
    top: 50%;
    transform: translateY(-50%);
    background: #0007;
    color: white;
    border: 0;
    width: 42px;
    height: 42px;
    border-radius: 50%;
    display: grid;
    place-items: center;
}

.slide-nav:hover {
    background: #000b;
}

.slide-nav.prev {
    right: 14px;
}

.slide-nav.next {
    left: 14px;
}

.slide-dots {
    position: absolute;
    z-index: 3;
    bottom: 17px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 9px;
    direction: ltr;
}

.dot {
    width: 10px;
    height: 10px;
    border: 0;
    padding: 0;
    background: #ffffff90;
    border-radius: 50%;
    transition: all .2s;
}

.dot.active {
    background: #fff;
    transform: scale(1.35);
}

/* المحتوى الرئيسي */

.container {
    max-width: 1400px;
    margin: -25px auto 24px;
    padding: clamp(14px, 3vw, 28px);
    background: var(--surface);
    border-radius: 18px;
    box-shadow: var(--shadow);
    position: relative;
    z-index: 4;
    min-height: 240px;
}

.welcome {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
    margin: 0 0 22px;
}

.welcome h1 {
    font-size: clamp(1.2rem, 2.5vw, 1.8rem);
    margin: 0;
}

.welcome p {
    margin: 5px 0 0;
    color: var(--muted);
    font-size: .9rem;
}

.section {
    margin: 25px 0 32px;
}

.section-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
    margin-bottom: 14px;
}

.section-title {
    font-size: 1.2rem;
    margin: 0;
    display: flex;
    align-items: center;
    gap: 9px;
}

.section-title i {
    color: var(--primary2);
}

.text-btn {
    border: 0;
    background: transparent;
    color: var(--primary);
    font-weight: 700;
}

/* بطاقات الكتب */

.books-grid {
    display: grid;
    grid-template-columns: repeat(5, minmax(0, 1fr));
    gap: 16px;
}

.book-card {
    min-width: 0;
    border: 1px solid var(--line);
    border-radius: 14px;
    overflow: hidden;
    background: var(--surface);
    cursor: pointer;
    transition: transform .2s, box-shadow .2s;
}

.book-card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow);
}

.book-cover-container {
    height: 220px;
    position: relative;
    background: #eaf1f8;
}

.book-cover {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.book-rating {
    position: absolute;
    top: 8px;
    right: 8px;
    background: #ffffffed;
    color: #a16207;
    border-radius: 20px;
    padding: 3px 7px;
    font-size: .75rem;
}

.book-info {
    padding: 10px;
}

.book-title {
    font-weight: 800;
    line-height: 1.5;
    min-height: 48px;
    font-size: .92rem;
}

.book-author {
    color: var(--muted);
    font-size: .8rem;
    margin-top: 4px;
}

.book-stats {
    display: flex;
    justify-content: space-between;
    gap: 6px;
    color: var(--muted);
    font-size: .75rem;
    margin-top: 10px;
}

.book-stat {
    display: flex;
    align-items: center;
    gap: 4px;
}

.book-stat .fa-heart {
    color: var(--accent);
}

.empty {
    padding: 32px;
    text-align: center;
    color: var(--muted);
    background: var(--page);
    border-radius: 14px;
}

/* النوافذ المنبثقة */

.overlay {
    display: none;
    position: fixed;
    inset: 0;
    z-index: 2000;
    background: #071a2bd9;
    align-items: center;
    justify-content: center;
    padding: 16px;
}

.overlay.active {
    display: flex;
}

.modal {
    width: min(900px, 100%);
    max-height: 90vh;
    overflow: auto;
    background: var(--surface);
    color: var(--text);
    border-radius: 18px;
    box-shadow: 0 20px 70px #0004;
    padding: 22px;
}

.modal-head {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;
    margin-bottom: 16px;
}

.modal-head h2 {
    margin: 0;
    font-size: 1.3rem;
}

.close-btn {
    border: 0;
    background: var(--page);
    color: var(--text);
    width: 38px;
    height: 38px;
    border-radius: 50%;
}

.search-row {
    display: flex;
    gap: 8px;
    margin-bottom: 18px;
}

.search-row input {
    flex: 1;
    min-width: 0;
    border: 1px solid var(--line);
    border-radius: 12px;
    padding: 12px;
    background: var(--surface);
    color: var(--text);
    outline-color: var(--primary2);
}

.primary-btn,
.danger-btn,
.soft-btn {
    border: 0;
    border-radius: 10px;
    padding: 10px 15px;
    font-weight: 700;
}

.primary-btn {
    background: var(--primary);
    color: white;
}

.danger-btn {
    background: #dc3545;
    color: white;
}

.soft-btn {
    background: #eaf3ff;
    color: var(--primary);
}

.search-results-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(145px, 1fr));
    gap: 12px;
}

.search-book-card {
    border: 1px solid var(--line);
    border-radius: 12px;
    overflow: hidden;
    cursor: pointer;
}

.search-book-cover {
    width: 100%;
    height: 170px;
    object-fit: cover;
    background: #eaf1f8;
}

.search-book-info {
    padding: 9px;
}

.search-book-info h4 {
    margin: 0;
    font-size: .9rem;
}

.search-book-info p {
    margin: 4px 0;
    color: var(--muted);
    font-size: .8rem;
}

/* تفاصيل الكتاب */

.detail-layout {
    display: grid;
    grid-template-columns: 220px 1fr;
    gap: 22px;
}

.detail-cover {
    width: 100%;
    height: 300px;
    object-fit: cover;
    border-radius: 12px;
    background: #eaf1f8;
}

.detail-title {
    margin: 0 0 8px;
}

.detail-author {
    color: var(--muted);
    margin: 0 0 14px;
}

.detail-description {
    line-height: 1.9;
    white-space: pre-line;
}

.detail-actions {
    display: flex;
    flex-wrap: wrap;
    gap: 9px;
    margin-top: 20px;
}

.reader-note {
    color: var(--muted);
    font-size: .9rem;
}

/* قارئ الكتب */

.reader {
    width: min(850px, 100%);
    height: 90vh;
    display: flex;
    flex-direction: column;
    background: var(--surface);
    color: var(--text);
    border-radius: 18px;
    overflow: hidden;
}

.reader-toolbar {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 12px;
    border-bottom: 1px solid var(--line);
    flex-wrap: wrap;
}

.reader-toolbar strong {
    margin-left: auto;
}

.reader-page {
    overflow: auto;
    padding: 25px;
    line-height: 2;
    font-size: 18px;
    white-space: pre-line;
}

/* القائمة الجانبية */

.sidebar-backdrop {
    display: none;
    position: fixed;
    inset: 0;
    background: #0006;
    z-index: 1500;
}

.sidebar-backdrop.active {
    display: block;
}

.sidebar {
    position: fixed;
    z-index: 1501;
    top: 0;
    bottom: 0;
    right: 0;
    width: min(310px, 85vw);
    background: var(--surface);
    color: var(--text);
    padding: 22px;
    transform: translateX(110%);
    transition: transform .25s;
    box-shadow: var(--shadow);
    overflow: auto;
}

.sidebar.active {
    transform: translateX(0);
}

.sidebar button {
    width: 100%;
    text-align: right;
    margin: 5px 0;
}

/* شريط التنقل السفلي */

.bottom-nav {
    position: fixed;
    z-index: 1000;
    bottom: 0;
    right: 0;
    left: 0;
    height: var(--nav-height);
    display: flex;
    justify-content: space-around;
    align-items: center;
    background: rgba(255,255,255,.97);
    border-top: 1px solid var(--line);
    box-shadow: 0 -4px 20px #0d3b660c;
    backdrop-filter: blur(10px);
}

.nav-btn {
    border: 0;
    background: transparent;
    color: var(--muted);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 3px;
    font-size: .72rem;
    min-width: 55px;
    padding: 6px 8px;
    border-radius: 12px;
}

.nav-btn i {
    font-size: 19px;
}

.nav-btn.active {
    color: var(--primary);
    font-weight: 800;
    background: #eaf3ff;
}

/* رسالة التنبيه */

.toast {
    position: fixed;
    z-index: 3000;
    bottom: calc(var(--nav-height) + 18px);
    left: 50%;
    transform: translateX(-50%);
    background: #16324f;
    color: white;
    padding: 11px 18px;
    border-radius: 12px;
    box-shadow: var(--shadow);
    display: none;
    max-width: 90%;
    text-align: center;
}

.toast.show {
    display: block;
}

/* الوضع الليلي */

body.dark {
    --text: #e4efff;
    --muted: #a7b7cc;
    --surface: #132338;
    --page: #0b1726;
    --line: #2b3d53;
    --shadow: 0 10px 28px #0004;
}

body.dark .topbar,
body.dark .bottom-nav {
    background: rgba(19,35,56,.97);
}

body.dark .icon-btn:hover,
body.dark .nav-btn.active,
body.dark .soft-btn {
    background: #203a59;
}

body.dark .book-cover-container,
body.dark .detail-cover {
    background: #203047;
}

/* توافق الأجهزة */

@media (max-width: 1000px) {
    .books-grid {
        grid-template-columns: repeat(4, minmax(0, 1fr));
    }

    .book-cover-container {
        height: 205px;
    }
}

@media (max-width: 700px) {
    .books-grid {
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 10px;
    }

    .book-cover-container {
        height: 175px;
    }

    .container {
        border-radius: 14px;
        margin-top: -18px;
    }

    .brand {
        font-size: 19px;
    }

    .detail-layout {
        grid-template-columns: 130px 1fr;
        gap: 14px;
    }

    .detail-cover {
        height: 190px;
    }

    .modal {
        padding: 16px;
    }
}

@media (max-width: 430px) {
    .books-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
    }

    .book-cover-container {
        height: 210px;
    }

    .slide-content {
        right: 48px;
        max-width: 75%;
    }

    .slide-content p {
        margin-bottom: 14px;
    }

    .hero-btn {
        padding: 8px 12px;
        font-size: .85rem;
    }

    .slide-nav {
        width: 34px;
        height: 34px;
    }

    .detail-layout {
        grid-template-columns: 1fr;
    }

    .detail-cover {
        width: 145px;
        height: 200px;
    }

    .nav-btn {
        min-width: 48px;
        font-size: .65rem;
        padding: 5px;
    }

    .nav-btn i {
        font-size: 17px;
    }
}

@media (prefers-reduced-motion: reduce) {
    *,
    *::before,
    *::after {
        scroll-behavior: auto !important;
        transition-duration: .01ms !important;
    }
}
</style>
</head>

<body>

<header class="topbar">
    <button class="icon-btn" aria-label="فتح القائمة" onclick="toggleSidebar()">
        <i class="fa-solid fa-bars"></i>
    </button>

    <button class="icon-btn" aria-label="البحث" onclick="toggleSearch()">
        <i class="fa-solid fa-magnifying-glass"></i>
    </button>

    <div class="brand">مكتبتي <span>📚</span></div>

    <button class="icon-btn" id="themeBtn" aria-label="تبديل الوضع" onclick="toggleMode()">
        <i class="fa-solid fa-moon"></i>
    </button>

    <button class="icon-btn" aria-label="مشاركة الموقع" onclick="shareSite()">
        <i class="fa-solid fa-share-nodes"></i>
    </button>
</header>

<!-- شريط الصور العلوي -->

<section class="hero-slider"
         aria-label="عروض المكتبة"
         onmouseenter="stopAutoSlide()"
         onmouseleave="resumeAutoSlide()">

    <div class="slides-container" id="slidesContainer">

        <div class="slide">
            <img
                src="https://images.unsplash.com/photo-1481627834876-b7833e8f5570?auto=format&fit=crop&w=1600&h=600&q=80"
                alt="رفوف كتب في مكتبة"
                fetchpriority="high">

            <div class="slide-content">
                <h2>أكبر مكتبة رقمية عربية</h2>
                <p>اكتشف كتبًا في مجالات متنوعة وابدأ رحلة القراءة.</p>

                <button class="hero-btn" onclick="toggleSearch()">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    ابدأ البحث الآن
                </button>
            </div>
        </div>

        <div class="slide">
            <img
                src="https://images.unsplash.com/photo-1506880018603-83d5b814b5a6?auto=format&fit=crop&w=1600&h=600&q=80"
                alt="شخص يقرأ كتابًا">

            <div class="slide-content">
                <h2>اقرأ أينما كنت</h2>
                <p>تصفح مجموعتك المحفوظة من هاتفك أو حاسوبك.</p>

                <button class="hero-btn" onclick="loadBooks()">
                    <i class="fa-solid fa-book-open"></i>
                    استعرض الكتب
                </button>
            </div>
        </div>

        <div class="slide">
            <img
                src="https://images.unsplash.com/photo-1521587760476-6c12a4b040da?auto=format&fit=crop&w=1600&h=600&q=80"
                alt="مكتبة مليئة بالكتب">

            <div class="slide-content">
                <h2>افتح باب المعرفة</h2>
                <p>اختر كتابك التالي من مكتبتنا المتنوعة.</p>

                <button class="hero-btn" onclick="showNewBooks()">
                    <i class="fa-solid fa-star"></i>
                    كتب مقترحة
                </button>
            </div>
        </div>

    </div>

    <button class="slide-nav prev" aria-label="الشريحة التالية" onclick="changeSlide(1)">
        <i class="fa-solid fa-chevron-right"></i>
    </button>

    <button class="slide-nav next" aria-label="الشريحة السابقة" onclick="changeSlide(-1)">
        <i class="fa-solid fa-chevron-left"></i>
    </button>

    <div class="slide-dots">
        <button class="dot active" aria-label="الشريحة 1" onclick="goToSlide(0)"></button>
        <button class="dot" aria-label="الشريحة 2" onclick="goToSlide(1)"></button>
        <button class="dot" aria-label="الشريحة 3" onclick="goToSlide(2)"></button>
    </div>
</section>

<!-- المحتوى الرئيسي -->

<main class="container" id="homeContent">

    <div class="welcome">
        <div>
            <h1 id="pageTitle">مرحبًا بك في مكتبتي</h1>
            <p id="pageSubtitle">اختر كتابًا جديدًا، فقد تكون بداخله فكرة تغيّر يومك.</p>
        </div>

        <button class="soft-btn" onclick="toggleSearch()">
            <i class="fa-solid fa-search"></i>
            ابحث
        </button>
    </div>

    <div id="content" aria-live="polite"></div>
</main>

<!-- نافذة البحث -->

<div class="overlay" id="searchOverlay" role="dialog" aria-modal="true" aria-label="البحث عن الكتب">
    <div class="modal">

        <div class="modal-head">
            <h2><i class="fa-solid fa-magnifying-glass"></i> البحث في مكتبتي</h2>

            <button class="close-btn" onclick="closeOverlay('searchOverlay')" aria-label="إغلاق">
                <i class="fa-solid fa-xmark"></i>
            </button>
        </div>

        <div class="search-row">
            <input
                id="searchInput"
                type="search"
                placeholder="اكتب اسم الكتاب أو المؤلف أو القسم..."
                oninput="searchBooks()">

            <button class="primary-btn" onclick="searchBooks()">بحث</button>
        </div>

        <div id="searchResults">
            <div class="empty">اكتب كلمة للبحث عن كتاب.</div>
        </div>

    </div>
</div>

<!-- نافذة تفاصيل الكتاب -->

<div class="overlay" id="bookDetailsOverlay" role="dialog" aria-modal="true" aria-label="تفاصيل الكتاب">
    <div class="modal">

        <div class="modal-head">
            <h2>تفاصيل الكتاب</h2>

            <button class="close-btn" onclick="closeBookDetails()" aria-label="إغلاق">
                <i class="fa-solid fa-xmark"></i>
            </button>
        </div>

        <div id="bookDetails"></div>
    </div>
</div>

<!-- نافذة القراءة -->

<div class="overlay" id="readingOverlay" role="dialog" aria-modal="true" aria-label="قارئ الكتاب">
    <div class="reader">

        <div class="reader-toolbar">
            <strong id="readerTitle">القراءة</strong>

            <button class="soft-btn" onclick="changeFontSize(-1)">A−</button>
            <button class="soft-btn" onclick="changeFontSize(1)">A+</button>

            <button class="soft-btn" onclick="toggleBookmark()">
                <i class="fa-regular fa-bookmark"></i>
                حفظ الموضع
            </button>

            <button class="close-btn" onclick="closeReading()" aria-label="إغلاق القراءة">
                <i class="fa-solid fa-xmark"></i>
            </button>
        </div>

        <div class="reader-page" id="readerPage"></div>
    </div>
</div>

<!-- القائمة الجانبية -->

<div class="sidebar-backdrop" id="sidebarBackdrop" onclick="toggleSidebar()"></div>

<aside class="sidebar" id="sidebar">

    <div class="modal-head">
        <h2>القائمة</h2>

        <button class="close-btn" onclick="toggleSidebar()" aria-label="إغلاق">
            <i class="fa-solid fa-xmark"></i>
        </button>
    </div>

    <button class="soft-btn" onclick="showSection('home')">
        <i class="fa-solid fa-house"></i>
        الرئيسية
    </button>

    <button class="soft-btn" onclick="showSection('all')">
        <i class="fa-solid fa-book"></i>
        جميع الكتب
    </button>

    <button class="soft-btn" onclick="showSection('favorites')">
        <i class="fa-solid fa-heart"></i>
        مكتبتي — المفضلة
    </button>

    <button class="soft-btn" onclick="showSection('history')">
        <i class="fa-solid fa-clock-rotate-left"></i>
        سجل القراءة
    </button>

    <button class="soft-btn" onclick="showSection('downloaded')">
        <i class="fa-solid fa-download"></i>
        الكتب المحفوظة للتنزيل
    </button>

    <hr style="border:0;border-top:1px solid var(--line);margin:18px 0">

    <button class="soft-btn" onclick="shareSite()">
        <i class="fa-solid fa-share-nodes"></i>
        مشاركة الموقع
    </button>

    <p class="reader-note">
        هذه نسخة واجهة أمامية تجريبية؛ بيانات الكتب والمفضلة تُحفظ محليًا في هذا المتصفح.
    </p>
</aside>

<!-- شريط التنقل السفلي -->

<nav class="bottom-nav" aria-label="التنقل الرئيسي">

    <button class="nav-btn active" data-page="home" onclick="showSection('home',this)">
        <i class="fa-solid fa-house"></i>
        <span>الرئيسية</span>
    </button>

    <button class="nav-btn" data-page="categories" onclick="showSection('categories',this)">
        <i class="fa-solid fa-layer-group"></i>
        <span>الأقسام</span>
    </button>

    <button class="nav-btn" data-page="favorites" onclick="showSection('favorites',this)">
        <i class="fa-solid fa-bookmark"></i>
        <span>مكتبتي</span>
    </button>

    <button class="nav-btn" data-page="history" onclick="showSection('history',this)">
        <i class="fa-solid fa-clock"></i>
        <span>السجل</span>
    </button>

    <button class="nav-btn" data-page="about" onclick="showSection('about',this)">
        <i class="fa-solid fa-circle-info"></i>
        <span>حول الموقع</span>
    </button>

</nav>

<div class="toast" id="toast" role="status"></div>

<!-- ضع القسم الثاني مباشرة هنا، قبل نهاية الملف -->
<script>
'use strict';

/* =====================================
   بيانات الكتب التجريبية
===================================== */

const booksData = [
    {
        id: 1,
        title: 'العادات الذرية',
        author: 'جيمس كلير',
        category: 'تطوير الذات',
        description: 'كتاب عن بناء العادات الصغيرة وتغيير السلوك تدريجيًا. هذه نبذة تعريفية وليست نص الكتاب الكامل.',
        cover: 'https://covers.openlibrary.org/b/isbn/9780735211292-L.jpg',
        likes: 42,
        downloads: 120,
        views: 850
    },
    {
        id: 2,
        title: 'فكر تصبح غنيًا',
        author: 'نابليون هيل',
        category: 'تطوير الذات',
        description: 'يتناول الكتاب التفكير وتحديد الأهداف والمثابرة في سبيل تحقيقها.',
        cover: 'https://covers.openlibrary.org/b/isbn/9781585424337-L.jpg',
        likes: 36,
        downloads: 98,
        views: 720
    },
    {
        id: 3,
        title: 'قوة الآن',
        author: 'إيكهارت تول',
        category: 'تطوير الذات',
        description: 'مقدمة إلى التركيز على اللحظة الحالية والانتباه إلى الأفكار.',
        cover: 'https://covers.openlibrary.org/b/isbn/9781577314806-L.jpg',
        likes: 28,
        downloads: 76,
        views: 610
    },
    {
        id: 4,
        title: 'الأب الغني والأب الفقير',
        author: 'روبرت كيوساكي',
        category: 'ثقافية',
        description: 'يعرض أفكارًا عامة عن الثقافة المالية والأصول والالتزامات.',
        cover: 'https://covers.openlibrary.org/b/isbn/9781612680194-L.jpg',
        likes: 51,
        downloads: 140,
        views: 940
    },
    {
        id: 5,
        title: 'مقدمة ابن خلدون',
        author: 'عبد الرحمن بن خلدون',
        category: 'ثقافية',
        description: 'عمل تراثي بارز في التاريخ والعمران والاجتماع البشري.',
        cover: 'https://covers.openlibrary.org/b/isbn/9780140449150-L.jpg',
        likes: 33,
        downloads: 81,
        views: 680
    },
    {
        id: 6,
        title: 'الأمير',
        author: 'نيكولو مكيافيلي',
        category: 'قانونية',
        description: 'نص كلاسيكي يناقش الحكم والسياسة والسلطة في سياقه التاريخي.',
        cover: 'https://covers.openlibrary.org/b/isbn/9780140449150-L.jpg',
        likes: 22,
        downloads: 53,
        views: 490
    },
    {
        id: 7,
        title: 'تعلم البرمجة للمبتدئين',
        author: 'فريق مكتبتي',
        category: 'تقنية',
        description: 'دليل تمهيدي مقترح للتعرف إلى المفاهيم الأساسية للبرمجة.',
        cover: 'https://images.unsplash.com/photo-1515879218367-8466d910aaa4?auto=format&fit=crop&w=600&q=80',
        likes: 31,
        downloads: 65,
        views: 520
    },
    {
        id: 8,
        title: 'مبادئ علم النفس',
        author: 'فريق مكتبتي',
        category: 'تعليمية',
        description: 'نبذة تعريفية تمهيدية عن موضوعات علم النفس الأساسية.',
        cover: 'https://images.unsplash.com/photo-1456513080510-7bf3a84b82f8?auto=format&fit=crop&w=600&q=80',
        likes: 19,
        downloads: 42,
        views: 360
    },
    {
        id: 9,
        title: 'رحلة إلى مركز الأرض',
        author: 'جول فيرن',
        category: 'روايات وقصص',
        description: 'رواية مغامرات كلاسيكية تدور حول رحلة استكشافية خيالية إلى باطن الأرض.',
        cover: 'https://covers.openlibrary.org/b/isbn/9780140449129-L.jpg',
        likes: 27,
        downloads: 71,
        views: 580
    },
    {
        id: 10,
        title: 'حول العالم في 80 يومًا',
        author: 'جول فيرن',
        category: 'روايات وقصص',
        description: 'رواية مغامرات عن رهان للقيام برحلة حول العالم في مدة محددة.',
        cover: 'https://covers.openlibrary.org/b/isbn/9780140449068-L.jpg',
        likes: 24,
        downloads: 60,
        views: 510
    },
    {
        id: 11,
        title: 'مدخل إلى العلوم',
        author: 'فريق مكتبتي',
        category: 'علمية',
        description: 'مقدمة مبسطة إلى التفكير العلمي وطرائق الملاحظة والاستنتاج.',
        cover: 'https://images.unsplash.com/photo-1532094349884-543bc11b234d?auto=format&fit=crop&w=600&q=80',
        likes: 16,
        downloads: 29,
        views: 290
    },
    {
        id: 12,
        title: 'مختارات من الحكم',
        author: 'مجموعة مؤلفين',
        category: 'دينية',
        description: 'مجموعة تعريفية بالحكم والمواعظ. ينبغي إضافة مصدر موثوق للنص الكامل.',
        cover: 'https://images.unsplash.com/photo-1609599006353-e629aaabfeae?auto=format&fit=crop&w=600&q=80',
        likes: 39,
        downloads: 110,
        views: 800
    }
];

const categories = [
    'كتب شائعة',
    'دينية',
    'ثقافية',
    'روايات وقصص',
    'تعليمية',
    'تطوير الذات',
    'علمية',
    'قانونية',
    'تقنية'
];

const categoryMap = {
    'كتب شائعة': null,
    'دينية': 'دينية',
    'ثقافية': 'ثقافية',
    'روايات وقصص': 'روايات وقصص',
    'تعليمية': 'تعليمية',
    'تطوير الذات': 'تطوير الذات',
    'علمية': 'علمية',
    'قانونية': 'قانونية',
    'تقنية': 'تقنية'
};

const storageKeys = {
    favorites: 'maktabati_favorites',
    history: 'maktabati_history',
    downloaded: 'maktabati_downloaded',
    likes: 'maktabati_likes',
    views: 'maktabati_views',
    bookmarks: 'maktabati_bookmarks'
};

let currentSlide = 0;
let slideInterval = null;
let currentBookId = null;
let readerFontSize = 18;

const slidesContainer = document.getElementById('slidesContainer');
const slides = Array.from(document.querySelectorAll('.slide'));
const dots = Array.from(document.querySelectorAll('.dot'));

/* =====================================
   التخزين والمساعدات
===================================== */

function getStored(key, fallback = []) {
    try {
        const value = JSON.parse(localStorage.getItem(key));
        return value ?? fallback;
    } catch {
        return fallback;
    }
}

function setStored(key, value) {
    try {
        localStorage.setItem(key, JSON.stringify(value));
    } catch {
        toast('تعذر حفظ البيانات في هذا المتصفح.');
    }
}

function toast(message) {
    const element = document.getElementById('toast');

    element.textContent = message;
    element.classList.add('show');

    clearTimeout(toast.timer);

    toast.timer = setTimeout(() => {
        element.classList.remove('show');
    }, 2600);
}

function safeText(value) {
    return String(value ?? '').replace(/[&<>"']/g, character => ({
        '&': '&amp;',
        '<': '&lt;',
        '>': '&gt;',
        '"': '&quot;',
        "'": '&#39;'
    })[character]);
}

function bookById(id) {
    return booksData.find(book => book.id === Number(id));
}

function getLikes(book) {
    const likes = getStored(storageKeys.likes, {});
    return Number(likes[book.id] ?? book.likes);
}

function getViews(book) {
    const views = getStored(storageKeys.views, {});
    return Number(views[book.id] ?? book.views);
}

/* =====================================
   شريط الصور
===================================== */

function renderSlides() {
    slidesContainer.style.transform =
        `translateX(${currentSlide * 100}%)`;

    slides.forEach((slide, index) => {
        slide.classList.toggle('active', index === currentSlide);
    });

    dots.forEach((dot, index) => {
        dot.classList.toggle('active', index === currentSlide);
    });
}

function changeSlide(direction) {
    if (!slides.length) return;

    currentSlide =
        (currentSlide + direction + slides.length) % slides.length;

    renderSlides();
    resetAutoSlide();
}

function goToSlide(index) {
    if (index < 0 || index >= slides.length) return;

    currentSlide = index;

    renderSlides();
    resetAutoSlide();
}

function startAutoSlide() {
    stopAutoSlide();

    if (
        !window.matchMedia('(prefers-reduced-motion: reduce)').matches &&
        slides.length > 1
    ) {
        slideInterval = setInterval(() => {
            currentSlide = (currentSlide + 1) % slides.length;
            renderSlides();
        }, 5000);
    }
}

function stopAutoSlide() {
    if (slideInterval !== null) {
        clearInterval(slideInterval);
        slideInterval = null;
    }
}

function resetAutoSlide() {
    startAutoSlide();
}

function resumeAutoSlide() {
    startAutoSlide();
}

/* =====================================
   بطاقات الكتب
===================================== */

function renderBookCard(book) {
    const favorites = getStored(storageKeys.favorites);
    const liked = favorites.includes(book.id);

    return `
        <article
            class="book-card"
            tabindex="0"
            role="button"
            aria-label="تفاصيل ${safeText(book.title)}"
            onclick="showBookDetails(${book.id})"
            onkeydown="if(event.key==='Enter'||event.key===' '){event.preventDefault();showBookDetails(${book.id})}">

            <div class="book-cover-container">
                <img
                    class="book-cover"
                    loading="lazy"
                    src="${safeText(book.cover)}"
                    alt="غلاف ${safeText(book.title)}"
                    onerror="this.onerror=null;this.src='https://placehold.co/400x600/eaf1f8/0d3b66?text=Book'">

                <div class="book-rating">
                    <i class="fa-solid fa-heart"></i>
                    ${getLikes(book)}
                </div>
            </div>

            <div class="book-info">
                <div class="book-title">${safeText(book.title)}</div>
                <div class="book-author">${safeText(book.author)}</div>

                <div class="book-stats">
                    <span class="book-stat">
                        <i class="fa-solid fa-download"></i>
                        ${book.downloads}
                    </span>

                    <span class="book-stat">
                        <i class="fa-solid fa-eye"></i>
                        ${getViews(book)}
                    </span>

                    <span class="book-stat">
                        <i class="fa-solid fa-heart"></i>
                        ${liked ? 'محفوظ' : 'إعجاب'}
                    </span>
                </div>
            </div>
        </article>
    `;
}

function renderBookGrid(books) {
    if (!books.length) {
        return `
            <div class="empty">
                <i class="fa-solid fa-book-open"></i>
                <p>لا توجد كتب لعرضها هنا حاليًا.</p>
            </div>
        `;
    }

    return `
        <div class="books-grid">
            ${books.map(renderBookCard).join('')}
        </div>
    `;
}

function renderSection(title, books, pageKey = '') {
    if (!books.length) return '';

    return `
        <section class="section">
            <div class="section-head">
                <h2 class="section-title">
                    <i class="fa-solid fa-book-open"></i>
                    ${safeText(title)}
                </h2>

                <button class="text-btn"
                    onclick="showSection('${pageKey || 'all'}')">
                    عرض الكل
                    <i class="fa-solid fa-arrow-left"></i>
                </button>
            </div>

            ${renderBookGrid(books)}
        </section>
    `;
}

/* =====================================
   الصفحة الرئيسية والأقسام
===================================== */

function loadBooks() {
    const content = document.getElementById('content');

    const popular = [...booksData]
        .sort((a, b) => getViews(b) - getViews(a))
        .slice(0, 6);

    content.innerHTML =
        renderSection('كتب شائعة', popular, 'all') +
        categories
            .filter(category => category !== 'كتب شائعة')
            .map(category => renderSection(
                category,
                booksData.filter(book =>
                    book.category === categoryMap[category]
                ),
                'category:' + category
            ))
            .join('');

    document.getElementById('pageTitle').textContent =
        'مرحبًا بك في مكتبتي';

    document.getElementById('pageSubtitle').textContent =
        'اختر كتابًا جديدًا، فقد تكون بداخله فكرة تغيّر يومك.';
}

function showNewBooks() {
    displaySearchResults(
        [...booksData].reverse(),
        'كتب مقترحة'
    );

    document.getElementById('searchOverlay').classList.add('active');
}

/* =====================================
   البحث
===================================== */

function searchBooks() {
    const input = document.getElementById('searchInput')
        .value.trim().toLocaleLowerCase('ar');

    const results = booksData.filter(book =>
        [
            book.title,
            book.author,
            book.category,
            book.description
        ].some(value =>
            String(value).toLocaleLowerCase('ar').includes(input)
        )
    );

    displaySearchResults(results, 'نتائج البحث');
}

function displaySearchResults(results, title = 'نتائج البحث') {
    const box = document.getElementById('searchResults');

    if (!results.length) {
        box.innerHTML = `
            <div class="empty">
                <i class="fa-solid fa-magnifying-glass"></i>
                <h3>لا توجد نتائج</h3>
                <p>جرّب كلمة أخرى أو تحقق من الإملاء.</p>
            </div>
        `;
        return;
    }

    box.innerHTML = `
        <h3>${safeText(title)} (${results.length})</h3>

        <div class="search-results-grid">
            ${results.map(book => `
                <article
                    class="search-book-card"
                    tabindex="0"
                    role="button"
                    onclick="showBookDetails(${book.id})"
                    onkeydown="if(event.key==='Enter')showBookDetails(${book.id})">

                    <img
                        class="search-book-cover"
                        loading="lazy"
                        src="${safeText(book.cover)}"
                        alt="غلاف ${safeText(book.title)}"
                        onerror="this.onerror=null;this.src='https://placehold.co/400x600/eaf1f8/0d3b66?text=Book'">

                    <div class="search-book-info">
                        <h4>${safeText(book.title)}</h4>
                        <p>${safeText(book.author)}</p>
                        <p>
                            <i class="fa-solid fa-eye"></i>
                            ${getViews(book)}
                            &nbsp;
                            <i class="fa-solid fa-heart"></i>
                            ${getLikes(book)}
                        </p>
                    </div>
                </article>
            `).join('')}
        </div>
    `;
}

function toggleSearch() {
    const overlay = document.getElementById('searchOverlay');

    overlay.classList.toggle('active');

    if (overlay.classList.contains('active')) {
        setTimeout(() => {
            document.getElementById('searchInput').focus();
        }, 50);
    }
}

/* =====================================
   تفاصيل الكتاب
===================================== */

function showBookDetails(bookId) {
    const book = bookById(bookId);

    if (!book) {
        toast('لم يتم العثور على الكتاب.');
        return;
    }

    currentBookId = book.id;

    const views = getStored(storageKeys.views, {});
    views[book.id] = getViews(book) + 1;

    setStored(storageKeys.views, views);

    const favorites = getStored(storageKeys.favorites);

    document.getElementById('bookDetails').innerHTML = `
        <div class="detail-layout">

            <img
                class="detail-cover"
                src="${safeText(book.cover)}"
                alt="غلاف ${safeText(book.title)}"
                onerror="this.onerror=null;this.src='https://placehold.co/400x600/eaf1f8/0d3b66?text=Book'">

            <div>
                <h2 class="detail-title">${safeText(book.title)}</h2>

                <p class="detail-author">
                    تأليف: ${safeText(book.author)}
                    · القسم: ${safeText(book.category)}
                </p>

                <p class="detail-description">
                    ${safeText(book.description)}
                </p>

                <p class="reader-note">
                    المشاهدات: ${getViews(book)}
                    · الإعجابات: ${getLikes(book)}
                    · التنزيلات: ${book.downloads}
                </p>

                <div class="detail-actions">

                    <button class="primary-btn"
                        onclick="readBook(${book.id})">
                        <i class="fa-solid fa-book-open"></i>
                        قراءة النبذة
                    </button>

                    <button class="soft-btn"
                        onclick="toggleLike(${book.id})">
                        <i class="fa-solid fa-heart"></i>
                        ${favorites.includes(book.id)
                            ? 'إزالة من مكتبتي'
                            : 'إضافة إلى مكتبتي'}
                    </button>

                    <button class="soft-btn"
                        onclick="handleDownload(${book.id})">
                        <i class="fa-solid fa-download"></i>
                        حفظ بيانات الكتاب
                    </button>

                </div>

                <p class="reader-note">
                    لا يتوفر ملف PDF كامل لهذا الكتاب في هذه النسخة التجريبية.
                    لا يتم إنشاء رابط تنزيل وهمي.
                </p>
            </div>
        </div>
    `;

    document.getElementById('bookDetailsOverlay')
        .classList.add('active');
}

function closeBookDetails() {
    document.getElementById('bookDetailsOverlay')
        .classList.remove('active');
}

/* =====================================
   قارئ الكتب
===================================== */

function readBook(bookId) {
    const book = bookById(bookId);

    if (!book) return;

    currentBookId = book.id;

    const history = getStored(storageKeys.history);

    history.unshift({
        id: book.id,
        time: Date.now()
    });

    const uniqueHistory = history.filter(
        (item, index, array) =>
            array.findIndex(entry => entry.id === item.id) === index
    ).slice(0, 50);

    setStored(storageKeys.history, uniqueHistory);

    document.getElementById('readerTitle').textContent = book.title;

    const readerPage = document.getElementById('readerPage');

    readerPage.style.fontSize = readerFontSize + 'px';

    readerPage.textContent =
        book.description +
        '\n\nهذه نسخة تجريبية من القارئ تعرض نبذة تعريفية فقط، وليست النص الكامل للكتاب. لإتاحة القراءة الكاملة، أضف نصًا تملك حق نشره أو رابطًا قانونيًا لنسخة متاحة.';

    const bookmarks = getStored(storageKeys.bookmarks, {});
    readerPage.scrollTop = bookmarks[book.id]?.scrollTop || 0;

    closeBookDetails();

    document.getElementById('readingOverlay')
        .classList.add('active');
}

function closeReading() {
    document.getElementById('readingOverlay')
        .classList.remove('active');
}

function changeFontSize(change) {
    readerFontSize = Math.min(
        30,
        Math.max(14, readerFontSize + change * 2)
    );

    document.getElementById('readerPage').style.fontSize =
        readerFontSize + 'px';
}

function toggleBookmark() {
    const page = document.getElementById('readerPage');

    if (!currentBookId) return;

    const bookmarks = getStored(storageKeys.bookmarks, {});

    bookmarks[currentBookId] = {
        scrollTop: page.scrollTop,
        title: bookById(currentBookId)?.title || ''
    };

    setStored(storageKeys.bookmarks, bookmarks);

    toast('تم حفظ موضع القراءة لهذا الكتاب.');
}

/* =====================================
   المفضلة والتنزيلات
===================================== */

function toggleLike(bookId) {
    const book = bookById(bookId);

    if (!book) return;

    const favorites = getStored(storageKeys.favorites);
    const likes = getStored(storageKeys.likes, {});

    if (favorites.includes(book.id)) {
        setStored(
            storageKeys.favorites,
            favorites.filter(id => id !== book.id)
        );

        likes[book.id] = Math.max(0, getLikes(book) - 1);

        toast('أزيل الكتاب من مكتبتي.');
    } else {
        favorites.unshift(book.id);

        setStored(storageKeys.favorites, favorites);

        likes[book.id] = getLikes(book) + 1;

        toast('أضيف الكتاب إلى مكتبتي.');
    }

    setStored(storageKeys.likes, likes);

    showBookDetails(book.id);
    updateFavoritesCount();
    loadBooks();
}

function handleDownload(bookId) {
    const book = bookById(bookId);

    if (!book) return;

    const downloaded = getStored(storageKeys.downloaded);

    if (!downloaded.includes(book.id)) {
        downloaded.unshift(book.id);
    }

    setStored(storageKeys.downloaded, downloaded);

    const content =
        `${book.title}\n` +
        `المؤلف: ${book.author}\n` +
        `القسم: ${book.category}\n\n` +
        `${book.description}\n`;

    const blob = new Blob(
        [content],
        { type: 'text/plain;charset=utf-8' }
    );

    const url = URL.createObjectURL(blob);
    const link = document.createElement('a');

    link.href = url;
    link.download =
        `${book.title.replace(/[\\/:*?"<>|]/g, '-')}.txt`;

    document.body.appendChild(link);
    link.click();
    link.remove();

    setTimeout(() => URL.revokeObjectURL(url), 1000);

    toast('تم حفظ بطاقة بيانات الكتاب. هذا ليس ملف PDF.');
}

function updateFavoritesCount() {
    // محفوظة هنا لتوافق الاستدعاءات الأخرى.
}

/* =====================================
   القائمة الجانبية والوضع الليلي
===================================== */

function toggleSidebar() {
    const sidebar = document.getElementById('sidebar');
    const backdrop = document.getElementById('sidebarBackdrop');

    sidebar.classList.toggle('active');
    backdrop.classList.toggle('active');
}

function toggleMode() {
    const dark = document.body.classList.toggle('dark');

    const button = document.getElementById('themeBtn');

    button.innerHTML = dark
        ? '<i class="fa-solid fa-sun"></i>'
        : '<i class="fa-solid fa-moon"></i>';

    button.title = dark ? 'الوضع النهاري' : 'الوضع الليلي';

    try {
        localStorage.setItem(
            'maktabati_theme',
            dark ? 'dark' : 'light'
        );
    } catch {}
}

function toggleNightMode() {
    toggleMode();
}

function logout() {
    toast('لا يوجد تسجيل دخول في هذه النسخة التجريبية.');
}

/* =====================================
   التنقل بين الصفحات
===================================== */

function showSection(section, button) {

    if (typeof section === 'string' &&
        section.startsWith('category:')) {

        const category = section.slice(9);

        document.getElementById('content').innerHTML =
            renderSection(
                category,
                booksData.filter(book => book.category === category),
                'all'
            );

        document.getElementById('pageTitle').textContent = category;
        document.getElementById('pageSubtitle').textContent =
            'تصفح الكتب المتاحة في هذا القسم.';

    } else if (section === 'home') {

        loadBooks();

    } else if (section === 'all' || section === 'categories') {

        document.getElementById('content').innerHTML =
            section === 'categories'
                ? categories
                    .filter(category => category !== 'كتب شائعة')
                    .map(category => renderSection(
                        category,
                        booksData.filter(book =>
                            book.category === categoryMap[category]
                        ),
                        'category:' + category
                    )).join('')
                : renderSection('جميع الكتب', booksData, 'all');

        document.getElementById('pageTitle').textContent =
            section === 'categories' ? 'أقسام المكتبة' : 'جميع الكتب';

        document.getElementById('pageSubtitle').textContent =
            'اختر قسمًا أو افتح أي كتاب لمعرفة تفاصيله.';

    } else if (section === 'favorites') {

        const ids = getStored(storageKeys.favorites);

        document.getElementById('content').innerHTML =
            renderSection(
                'كتبي المحفوظة',
                booksData.filter(book => ids.includes(book.id)),
                'all'
            );

        document.getElementById('pageTitle').textContent = 'مكتبتي';
        document.getElementById('pageSubtitle').textContent =
            'الكتب التي أضفتها إلى قائمتك.';

    } else if (section === 'history') {

        const ids = getStored(storageKeys.history)
            .map(item => item.id);

        const unique = [...new Set(ids)];

        document.getElementById('content').innerHTML =
            renderSection(
                'سجل القراءة',
                unique.map(id => bookById(id)).filter(Boolean),
                'all'
            );

        document.getElementById('pageTitle').textContent = 'سجل القراءة';
        document.getElementById('pageSubtitle').textContent =
            'الكتب التي فتحتها مؤخرًا على هذا الجهاز.';

    } else if (section === 'downloaded') {

        const ids = getStored(storageKeys.downloaded);

        document.getElementById('content').innerHTML =
            renderSection(
                'الكتب التي حفظت بياناتها',
                booksData.filter(book => ids.includes(book.id)),
                'all'
            );

        document.getElementById('pageTitle').textContent = 'التنزيلات';
        document.getElementById('pageSubtitle').textContent =
            'قائمة الكتب التي حفظت بطاقات بياناتها.';

    } else if (section === 'about') {

        document.getElementById('content').innerHTML = `
            <div class="empty">
                <h2>عن مكتبتي</h2>
                <p>
                    موقع تجريبي لتصفح مجموعة من الكتب
                    والتعرف عليها وحفظها محليًا.
                </p>
                <p>
                    هذه النسخة لا تتضمن خادمًا أو حسابات مستخدمين
                    أو ملفات كتب كاملة.
                </p>
            </div>
        `;

        document.getElementById('pageTitle').textContent = 'حول الموقع';
        document.getElementById('pageSubtitle').textContent =
            'معلومات عن النسخة التجريبية.';
    }

    document.querySelectorAll('.nav-btn').forEach(navButton => {
        navButton.classList.remove('active');
    });

    const matchingButton =
        button ||
        document.querySelector(`.nav-btn[data-page="${section}"]`);

    if (matchingButton) {
        matchingButton.classList.add('active');
    }

    const sidebar = document.getElementById('sidebar');

    if (sidebar.classList.contains('active')) {
        toggleSidebar();
    }

    window.scrollTo({
        top: document.getElementById('homeContent').offsetTop - 70,
        behavior: 'smooth'
    });
}

/* =====================================
   مشاركة الموقع
===================================== */

async function shareSite() {
    const shareData = {
        title: 'مكتبتي — المكتبة الرقمية العربية',
        text: 'اكتشف الكتب في مكتبتي',
        url: window.location.href
    };

    try {
        if (navigator.share) {
            await navigator.share(shareData);

        } else if (navigator.clipboard &&
                   window.isSecureContext) {

            await navigator.clipboard.writeText(window.location.href);

            toast('تم نسخ رابط الموقع.');

        } else {
            window.prompt(
                'انسخ رابط الموقع:',
                window.location.href
            );
        }

    } catch (error) {
        if (error.name !== 'AbortError') {
            toast('تعذرت المشاركة. يمكنك نسخ رابط الموقع من شريط العنوان.');
        }
    }
}

/* =====================================
   إغلاق النوافذ واختصارات لوحة المفاتيح
===================================== */

function closeOverlay(id) {
    document.getElementById(id).classList.remove('active');
}

document.addEventListener('keydown', event => {

    if (event.key === 'Escape') {
        document.querySelectorAll('.overlay.active').forEach(overlay => {
            overlay.classList.remove('active');
        });

        if (document.getElementById('sidebar').classList.contains('active')) {
            toggleSidebar();
        }
    }

    if (!document.querySelector('.overlay.active')) {
        if (event.key === 'ArrowRight') {
            changeSlide(1);
        }

        if (event.key === 'ArrowLeft') {
            changeSlide(-1);
        }
    }
});

document.querySelectorAll('.overlay').forEach(overlay => {
    overlay.addEventListener('click', event => {
        if (event.target === overlay) {
            overlay.classList.remove('active');
        }
    });
});

/* =====================================
   تشغيل الموقع
===================================== */

document.addEventListener('DOMContentLoaded', () => {

    try {
        if (localStorage.getItem('maktabati_theme') === 'dark') {
            document.body.classList.add('dark');
        }
    } catch {}

    document.getElementById('themeBtn').innerHTML =
        document.body.classList.contains('dark')
            ? '<i class="fa-solid fa-sun"></i>'
            : '<i class="fa-solid fa-moon"></i>';

    renderSlides();
    loadBooks();
    updateFavoritesCount();
    startAutoSlide();
});
</script>
</body>
</html>
