<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>المكتبة الرقمية العربية</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --dark-bg: #121212;
            --dark-header: #1c1c1c;
            --dark-card: #252525;
            --dark-text: #ffffff;
            --light-bg: #f5f5f5;
            --light-header: #ffffff;
            --light-card: #ffffff;
            --light-text: #333333;
            --primary: #2E7D32;
            --secondary: #1565C0;
            --accent: #D32F2F;
            --gold: #FFD700;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', 'Arial', sans-serif;
            background: var(--dark-bg);
            color: var(--dark-text);
            transition: all 0.3s ease;
            padding-top: 70px;
            padding-bottom: 70px;
        }

        body.light {
            background: var(--light-bg);
            color: var(--light-text);
        }

        .hidden {
            display: none !important;
        }

        /* ============ الهيدر ============ */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: var(--dark-header);
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
        }
        
        body.light header {
            background: var(--light-header);
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .header-right {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .header-title {
            font-weight: bold;
            color: #4CAF50;
            font-size: 18px;
            text-align: center;
            flex-grow: 1;
        }

        .header-btn {
            background: none;
            border: none;
            color: inherit;
            font-size: 22px;
            cursor: pointer;
            padding: 5px;
            transition: transform 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .header-btn:hover {
            transform: scale(1.1);
        }

        #themeBtn .fa-sun {
            color: #FFD700;
        }

        #themeBtn .fa-moon {
            color: #E0E0E0;
        }
        
        /* ============ القائمة الجانبية ============ */
        #sidebar {
            position: fixed;
            top: 0;
            right: -300px;
            width: 280px;
            height: 100%;
            background: var(--dark-card);
            transition: right 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            z-index: 1100;
            padding: 20px;
            overflow-y: auto;
        }

        body.light #sidebar {
            background: var(--light-card);
        }

        #sidebar.active {
            right: 0;
        }

        #closeSidebar {
            font-size: 28px;
            cursor: pointer;
            color: var(--accent);
            position: absolute;
            left: 15px;
            top: 15px;
        }

        #sidebar h2 {
            margin: 20px 0 30px;
            text-align: center;
            color: inherit;
            border-bottom: 2px solid var(--primary);
            padding-bottom: 10px;
        }

        .sidebar-item {
            padding: 15px;
            margin: 8px 0;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .sidebar-item:hover {
            background: rgba(76, 175, 80, 0.1);
        }

        .sidebar-item i {
            width: 24px;
            text-align: center;
        }/* ============ شريط الصور المتحرك المحسن ============ */
.top-slider {
    width: 100%;
    height: 180px;
    overflow: hidden;
    border-radius: 0 0 12px 12px;
    margin-bottom: 20px;
    position: relative;
}

.slider-container {
    width: 100%;
    height: 100%;
    position: relative;
}

.slider-track {
    display: flex;
    width: 300%;
    height: 100%;
    position: relative;
}

.slider-track.animated {
    animation: slideAnimation 25s infinite linear;
}

.slide {
    width: 33.333%;
    height: 100%;
    flex-shrink: 0;
}

.slide img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
}

.slider-controls {
    position: absolute;
    bottom: 15px;
    right: 50%;
    transform: translateX(50%);
    display: flex;
    gap: 8px;
    z-index: 10;
}

.slider-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: rgba(255,255,255,0.5);
    cursor: pointer;
    transition: background 0.3s;
}

.slider-dot.active {
    background: var(--primary);
    transform: scale(1.2);
}

@keyframes slideAnimation {
    0% { transform: translateX(0); }
    33.333% { transform: translateX(0); }
    38.333% { transform: translateX(-33.333%); }
    66.666% { transform: translateX(-33.333%); }
    71.666% { transform: translateX(-66.666%); }
    100% { transform: translateX(-66.666%); }
}

.slider-track:hover {
    animation-play-state: paused;
}

/* ============ واجهة البحث ============ */
#searchOverlay {
    position: fixed;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.95);
    z-index: 1200;
    display: none;
    padding: 20px;
}

body.light #searchOverlay {
    background: rgba(255,255,255,0.98);
}

#searchOverlay.active {
    display: block;
}

#closeSearch {
    position: absolute;
    top: 20px;
    left: 20px;
    font-size: 30px;
    color: var(--accent);
    cursor: pointer;
}

.search-container {
    max-width: 700px;
    margin: 80px auto 0;
}

.search-box {
    display: flex;
    background: var(--dark-card);
    border-radius: 50px;
    padding: 15px 25px;
    margin-bottom: 20px;
    box-shadow: 0 5px 20px rgba(0,0,0,0.3);
}

body.light .search-box {
    background: var(--light-card);
    box-shadow: 0 5px 20px rgba(0,0,0,0.1);
}

.search-box input {
    flex-grow: 1;
    border: none;
    background: none;
    color: inherit;
    font-size: 18px;
    outline: none;
    padding: 0 15px;
}

.search-box button {
    background: none;
    border: none;
    color: var(--primary);
    font-size: 20px;
    cursor: pointer;
}

.suggestions-container {
    background: var(--dark-card);
    border-radius: 15px;
    max-height: 400px;
    overflow-y: auto;
    box-shadow: 0 5px 20px rgba(0,0,0,0.2);
}

body.light .suggestions-container {
    background: var(--light-card);
}

.suggestion-item {
    padding: 15px 20px;
    border-bottom: 1px solid rgba(255,255,255,0.1);
    cursor: pointer;
    transition: background 0.2s;
    display: flex;
    align-items: center;
    gap: 15px;
}

body.light .suggestion-item {
    border-bottom: 1px solid rgba(0,0,0,0.1);
}

.suggestion-item:hover {
    background: rgba(76, 175, 80, 0.1);
}

.suggestion-item .book-cover {
    width: 50px;
    height: 70px;
    border-radius: 5px;
    object-fit: cover;
    background: #444;
}

body.light .suggestion-item .book-cover {
    background: #ddd;
}

.suggestion-info h4 {
    margin-bottom: 5px;
    font-size: 16px;
}

.suggestion-info p {
    color: #888;
    font-size: 14px;
}

body.light .suggestion-info p {
    color: #666;
}/* ============ أقسام الكتب - محسنة ============ */
#content {
    padding: 0 15px 30px;
    max-width: 1400px;
    margin: 0 auto;
}

.section-title {
    margin: 30px 0 20px;
    font-size: 24px;
    font-weight: bold;
    color: var(--primary);
    display: flex;
    align-items: center;
    gap: 12px;
    padding-right: 12px;
    border-right: 5px solid var(--primary);
}

.section-title i {
    font-size: 22px;
}

.books-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 20px;
    padding: 15px 0 30px;
}

@media (min-width: 768px) {
    .books-grid {
        grid-template-columns: repeat(3, 1fr);
    }
}

@media (min-width: 1024px) {
    .books-grid {
        grid-template-columns: repeat(6, 1fr);
    }
}

.book-card {
    background: var(--dark-card);
    border-radius: 12px;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    position: relative;
    height: 280px;
    display: flex;
    flex-direction: column;
}

body.light .book-card {
    background: var(--light-card);
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

.book-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 12px 24px rgba(0,0,0,0.3);
}

.book-cover-container {
    height: 180px;
    width: 100%;
    overflow: hidden;
    position: relative;
}

.book-cover {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s;
}

.book-card:hover .book-cover {
    transform: scale(1.05);
}

.book-info {
    padding: 15px;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
}

.book-title {
    font-weight: bold;
    font-size: 15px;
    margin-bottom: 6px;
    line-height: 1.3;
    height: 2.6em;
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
}

.book-author {
    font-size: 13px;
    color: #888;
    margin-bottom: 8px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

body.light .book-author {
    color: #666;
}

.book-rating {
    background: rgba(0,0,0,0.7);
    color: var(--gold);
    padding: 4px 8px;
    border-radius: 12px;
    font-size: 12px;
    display: flex;
    align-items: center;
    gap: 4px;
    position: absolute;
    top: 10px;
    left: 10px;
    backdrop-filter: blur(4px);
}

.book-category {
    position: absolute;
    top: 10px;
    right: 10px;
    background: rgba(46, 125, 50, 0.9);
    color: white;
    padding: 3px 8px;
    border-radius: 10px;
    font-size: 10px;
}

.book-stats {
    display: flex;
    justify-content: space-between;
    margin-top: auto;
    font-size: 11px;
    color: #aaa;
}

.book-stat {
    display: flex;
    align-items: center;
    gap: 3px;
}

/* ============ واجهة تفاصيل الكتاب ============ */
#bookDetailsOverlay {
    position: fixed;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: var(--dark-bg);
    z-index: 1300;
    display: none;
    overflow-y: auto;
    padding: 20px;
}

body.light #bookDetailsOverlay {
    background: var(--light-bg);
}

#bookDetailsOverlay.active {
    display: block;
}

#closeBookDetails {
    position: fixed;
    top: 20px;
    left: 20px;
    font-size: 30px;
    color: var(--accent);
    cursor: pointer;
    z-index: 1301;
    background: rgba(0,0,0,0.5);
    width: 45px;
    height: 45px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
}.book-details-container {
    max-width: 1000px;
    margin: 0 auto;
    background: var(--dark-card);
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 15px 50px rgba(0,0,0,0.5);
}

body.light .book-details-container {
    background: var(--light-card);
}

.book-details-header {
    position: relative;
    height: 300px;
    display: flex;
    align-items: flex-end;
    padding: 30px;
    color: white;
    background: linear-gradient(to top, rgba(0,0,0,0.8), rgba(0,0,0,0.4));
}

.book-details-cover {
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: -1;
}

.book-header-text {
    flex-grow: 1;
}

.book-details-title {
    font-size: 32px;
    font-weight: bold;
    margin-bottom: 10px;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
}

.book-details-author {
    font-size: 22px;
    opacity: 0.95;
    margin-bottom: 15px;
}

.book-stats-large {
    display: flex;
    gap: 25px;
    margin-top: 20px;
}

.stat-item-large {
    display: flex;
    flex-direction: column;
    align-items: center;
    background: rgba(255,255,255,0.15);
    backdrop-filter: blur(10px);
    padding: 12px 18px;
    border-radius: 12px;
    min-width: 90px;
    transition: transform 0.2s;
    cursor: pointer;
}

.stat-item-large:hover {
    transform: scale(1.05);
    background: rgba(255,255,255,0.2);
}

.stat-value-large {
    font-weight: bold;
    font-size: 22px;
}

.stat-label-large {
    font-size: 14px;
    opacity: 0.9;
    margin-top: 5px;
}

.book-actions {
    display: flex;
    gap: 20px;
    padding: 25px;
    border-bottom: 1px solid rgba(255,255,255,0.1);
}

body.light .book-actions {
    border-bottom: 1px solid rgba(0,0,0,0.1);
}

.action-btn {
    flex: 1;
    padding: 16px;
    border: none;
    border-radius: 12px;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    transition: all 0.2s;
}

.read-btn {
    background: var(--primary);
    color: white;
}

.read-btn:hover {
    background: #1B5E20;
    transform: translateY(-2px);
}

.download-btn {
    background: var(--accent);
    color: white;
}

.download-btn:hover {
    background: #B71C1C;
    transform: translateY(-2px);
}

.book-content {
    padding: 30px;
}

.content-section {
    margin-bottom: 30px;
}

.content-section h3 {
    margin-bottom: 15px;
    color: var(--primary);
    font-size: 22px;
    border-bottom: 3px solid var(--primary);
    padding-bottom: 8px;
    display: inline-block;
}

.content-section p {
    line-height: 1.8;
    color: #ddd;
    font-size: 16px;
}

body.light .content-section p {
    color: #555;
}

/* ============ واجهة القراءة ============ */
#readingOverlay {
    position: fixed;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: var(--dark-bg);
    z-index: 1400;
    display: none;
    flex-direction: column;
}

body.light #readingOverlay {
    background: var(--light-bg);
}

#readingOverlay.active {
    display: flex;
}

.reading-header {
    background: var(--dark-header);
    padding: 15px 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid rgba(255,255,255,0.1);
}

body.light .reading-header {
    background: var(--light-header);
    border-bottom: 1px solid rgba(0,0,0,0.1);
}

#closeReading {
    font-size: 24px;
    color: var(--accent);
    cursor: pointer;
}

.reading-title {
    font-weight: bold;
    font-size: 18px;
}

.reading-content {
    flex-grow: 1;
    padding: 30px;
    overflow-y: auto;
    line-height: 1.8;
    font-size: 18px;
    text-align: justify;
    max-width: 800px;
    margin: 0 auto;
}

.reading-controls {
    background: var(--dark-header);
    padding: 15px;
    display: flex;
    justify-content: space-around;
    border-top: 1px solid rgba(255,255,255,0.1);
}

body.light .reading-controls {
    background: var(--light-header);
    border-top: 1px solid rgba(0,0,0,0.1);
}

.reading-btn {
    background: none;
    border: none;
    color: inherit;
    font-size: 22px;
    cursor: pointer;
    padding: 10px 20px;
    transition: all 0.2s;
}

.reading-btn:hover {
    color: var(--primary);
    transform: scale(1.1);
}         /* ============ الشريط السفلي ============ */
        footer {
            position: fixed;
            bottom: 0;
            width: 100%;
            background: var(--dark-header);
            display: flex;
            justify-content: space-around;
            padding: 12px 0;
            border-top: 1px solid rgba(255,255,255,0.1);
            z-index: 999;
        }
        
        body.light footer {
            background: var(--light-header);
            border-top: 1px solid rgba(0,0,0,0.1);
        }

        .nav-btn {
            background: none;
            border: none;
            color: inherit;
            font-size: 22px;
            cursor: pointer;
            padding: 8px 20px;
            position: relative;
            transition: all 0.2s;
            border-radius: 10px;
        }

        .nav-btn.active {
            color: var(--primary);
            background: rgba(76, 175, 80, 0.1);
        }

        .nav-btn:hover {
            transform: translateY(-3px);
            background: rgba(76, 175, 80, 0.05);
        }

        .nav-badge {
            position: absolute;
            top: -5px;
            left: 5px;
            background: var(--accent);
            color: white;
            font-size: 10px;
            padding: 2px 6px;
            border-radius: 10px;
            min-width: 18px;
            text-align: center;
        }

        /* ============ تأثيرات ============ */
        .pulse {
            animation: pulse 0.3s ease-in-out;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        .fade-in {
            animation: fadeIn 0.3s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .scale-in {
            animation: scaleIn 0.3s ease-out;
        }

        @keyframes scaleIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        /* ============ التجاوب مع الأجهزة الصغيرة ============ */
        @media (max-width: 768px) {
            .top-slider {
                height: 150px;
            }
            
            .book-card {
                height: 260px;
            }
            
            .book-cover-container {
                height: 160px;
            }
            
            .book-details-header {
                height: 250px;
                padding: 20px;
            }
            
            .book-details-title {
                font-size: 24px;
            }
            
            .book-details-author {
                font-size: 18px;
            }
            
            .book-stats-large {
                gap: 15px;
            }
            
            .stat-item-large {
                min-width: 70px;
                padding: 10px 12px;
            }
            
            .stat-value-large {
                font-size: 18px;
            }
            
            .books-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 15px;
            }
            
            .action-btn {
                font-size: 16px;
                padding: 14px;
            }
            
            .reading-content {
                font-size: 16px;
                padding: 20px;
            }
        }

        @media (max-width: 480px) {
            .header-title {
                font-size: 16px;
            }
            
            .header-btn {
                font-size: 20px;
            }
            
            .top-slider {
                height: 130px;
            }
            
            .section-title {
                font-size: 20px;
            }
            
            .books-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 12px;
            }
            
            .book-card {
                height: 240px;
            }
            
            .book-cover-container {
                height: 140px;
            }
            
            .book-details-header {
                height: 220px;
            }
            
            .book-details-title {
                font-size: 20px;
            }
            
            .book-details-author {
                font-size: 16px;
            }
            
            .book-actions {
                flex-direction: column;
                gap: 15px;
            }
            
            .books-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- الهيدر -->
    <header>
        <button class="header-btn" onclick="toggleSidebar()">
            <i class="fas fa-bars"></i>
        </button>
        <div class="header-title">المكتبة الرقمية العربية</div>
        <div class="header-right">
            <button class="header-btn" onclick="toggleSearch()">
                <i class="fas fa-search"></i>
            </button>
            <button class="header-btn" onclick="shareSite()" title="مشاركة">
                <i class="fas fa-share-alt"></i>
            </button>
            <button class="header-btn" id="themeBtn" onclick="toggleMode()" title="تبديل الوضع">
                <i class="fas fa-sun"></i>
            </button>
        </div>
    </header>

    <!-- القائمة الجانبية -->
    <div id="sidebar">
        <span id="closeSidebar" onclick="toggleSidebar()">×</span>
        <h2><i class="fas fa-book-open"></i> المكتبة</h2>
        <div class="sidebar-item" onclick="showSection('home')">
            <i class="fas fa-home"></i>
            <span>الرئيسية</span>
        </div>
        <div class="sidebar-item" onclick="showSection('favorites')">
            <i class="fas fa-heart"></i>
            <span>المفضلة</span>
        </div>
        <div class="sidebar-item" onclick="showSection('history')">
            <i class="fas fa-history"></i>
            <span>السجل</span>
        </div>
        <div class="sidebar-item" onclick="showSection('categories')">
            <i class="fas fa-list"></i>
            <span>التصنيفات</span>
        </div>
        <div class="sidebar-item" onclick="showSection('settings')">
            <i class="fas fa-cog"></i>
            <span>الإعدادات</span>
        </div>
        <div class="sidebar-item" onclick="logout()" style="color: var(--accent);">
            <i class="fas fa-sign-out-alt"></i>
            <span>تسجيل خروج</span>
        </div>
    </div><!-- شريط الصور العلوي المحسن -->
<div class="top-slider">
    <div class="slider-container">
        <div class="slider-track animated" id="sliderTrack">
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1524995997946-a1c2e315a42f?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="مكتبة عربية">
            </div>
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1481627834876-b7833e8f5570?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="قراءة">
            </div>
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1532012197267-da84d127e765?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="كتب عربية">
            </div>
        </div>
        <div class="slider-controls">
            <div class="slider-dot active" onclick="goToSlide(0)"></div>
            <div class="slider-dot" onclick="goToSlide(1)"></div>
            <div class="slider-dot" onclick="goToSlide(2)"></div>
        </div>
    </div>
</div>

<!-- واجهة البحث -->
<div id="searchOverlay">
    <div id="closeSearch" onclick="toggleSearch()">×</div>
    <div class="search-container fade-in">
        <div class="search-box">
            <input type="text" id="searchInput" placeholder="ابحث عن كتاب أو مؤلف أو تصنيف...">
            <button><i class="fas fa-search"></i></button>
        </div>
        <div class="suggestions-container" id="suggestionsContainer">
            <!-- سيتم ملؤها بالنتائج -->
        </div>
    </div>
</div>

<!-- المحتوى الرئيسي -->
<div id="content">
    <!-- سيتم توليد الأقسام تلقائياً -->
</div>

<!-- واجهة تفاصيل الكتاب -->
<div id="bookDetailsOverlay">
    <div id="closeBookDetails" onclick="closeBookDetails()">×</div>
    <div class="book-details-container">
        <!-- سيتم ملؤها ديناميكياً -->
    </div>
</div>

<!-- واجهة القراءة -->
<div id="readingOverlay">
    <div class="reading-header">
        <span id="closeReading" onclick="closeReading()">×</span>
        <span class="reading-title" id="readingTitle"></span>
        <div></div> <!-- عنصر فارغ للمحاذاة -->
    </div>
    <div class="reading-content" id="readingContent">
        <!-- سيتم ملؤها ديناميكياً -->
    </div>
    <div class="reading-controls">
        <button class="reading-btn" onclick="changeFontSize(-1)" title="تصغير الخط">
            <i class="fas fa-font"></i>
        </button>
        <button class="reading-btn" onclick="changeFontSize(1)" title="تكبير الخط">
            <i class="fas fa-text-height"></i>
        </button>
        <button class="reading-btn" onclick="toggleBookmark()" title="إضافة إشارة">
            <i class="far fa-bookmark"></i>
        </button>
        <button class="reading-btn" onclick="toggleNightMode()" title="الوضع الليلي">
            <i class="fas fa-moon"></i>
        </button>
    </div>
</div>

<!-- الشريط السفلي -->
<footer>
    <button class="nav-btn active" onclick="showSection('home')">
        <i class="fas fa-home"></i>
    </button>
    <button class="nav-btn" onclick="showSection('library')">
        <i class="fas fa-book"></i>
    </button>
    <button class="nav-btn" onclick="showSection('add')">
        <i class="fas fa-plus-circle"></i>
    </button>
    <button class="nav-btn" onclick="showSection('favorites')">
        <i class="fas fa-star"></i>
        <span class="nav-badge" id="favoritesBadge">0</span>
    </button>
    <button class="nav-btn" onclick="showSection('profile')">
        <i class="fas fa-user"></i>
    </button>
</footer>
<script>
// بيانات التطبيق
const categories = [
    "كتب دينية",
    "روايات وقصص",
    "كتب علمية",
    "كتب تاريخية",
    "كتب تطوير الذات",
    "كتب تعليمية"
];// بيانات الكتب المعدلة - 6 كتب لكل قسم
const booksData = [
    // كتب دينية (6 كتب)
    {
        id: 1,
        title: "تفسير القرآن الكريم",
        author: "ابن كثير",
        category: "كتب دينية",
        cover: "https://images.unsplash.com/photo-1524995997946-a1c2e315a42f?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 156,
        views: 480,
        likes: 320,
        liked: false,
        authorBio: "عماد الدين إسماعيل بن عمر بن كثير القرشي الدمشقي، من كبار المفسرين والمؤرخين المسلمين.",
        description: "تفسير جامع للقرآن الكريم يعتمد على تفسير القرآن بالقرآن والسنة النبوية وآثار الصحابة والتابعين."
    },
    {
        id: 2,
        title: "رياض الصالحين",
        author: "النووي",
        category: "كتب دينية",
        cover: "https://images.unsplash.com/photo-1512820790803-83ca734da794?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 134,
        views: 420,
        likes: 298,
        liked: true,
        authorBio: "يحيى بن شرف النووي، عالم مسلم شهير، صاحب مؤلفات عديدة في الحديث والفقه.",
        description: "كتاب يجمع الأحاديث النبوية الصحيحة التي تتعلق بجميع جوانب الحياة الإسلامية."
    },
    {
        id: 3,
        title: "الأربعون النووية",
        author: "النووي",
        category: "كتب دينية",
        cover: "https://images.unsplash.com/photo-1544716278-ca5e3f4abd8c?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 178,
        views: 520,
        likes: 356,
        liked: false,
        authorBio: "يحيى بن شرف النووي، من أبرز علماء الشافعية في القرن السابع الهجري.",
        description: "مجموعة من أربعين حديثاً نبوياً تتناول أهم أساسيات الدين الإسلامي."
    },
    {
        id: 4,
        title: "فقه السنة",
        author: "سيد سابق",
        category: "كتب دينية",
        cover: "https://images.unsplash.com/photo-1507842217343-583bb7270b66?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 145,
        views: 460,
        likes: 312,
        liked: true,
        authorBio: "سيد سابق، داعية إسلامي مصري، متخصص في الفقه المقارن.",
        description: "كتاب في الفقه الإسلامي يعرض المسائل الفقهية بأسلوب سهل معتمداً على السنة النبوية."
    },
    {
        id: 5,
        title: "السيرة النبوية",
        author: "ابن هشام",
        category: "كتب دينية",
        cover: "https://images.unsplash.com/photo-1516979187457-637abb4f9353?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 162,
        views: 510,
        likes: 345,
        liked: false,
        authorBio: "عبد الملك بن هشام، مؤرخ مسلم، جمع سيرة ابن إسحاق واختصره.",
        description: "أشهر كتاب في سيرة النبي محمد صلى الله عليه وسلم، يروي تفاصيل حياته ودعوته."
    },
    {
        id: 6,
        title: "الحاوي في الفقه",
        author: "الماوردي",
        category: "كتب دينية",
        cover: "https://images.unsplash.com/photo-1481627834876-b7833e8f5570?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 128,
        views: 410,
        likes: 287,
        liked: true,
        authorBio: "أبو الحسن علي بن محمد الماوردي، فقيه شافعي وقاضٍ مشهور.",
        description: "موسوعة فقهية شاملة لجميع أبواب الفقه الإسلامي."
    },
    
    // روايات وقصص (6 كتب)
    {
        id: 7,
        title: "ألف ليلة وليلة",
        author: "مجهول",
        category: "روايات وقصص",
        cover: "https://images.unsplash.com/photo-1532012197267-da84d127e765?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 198,
        views: 620,
        likes: 432,
        liked: true,
        authorBio: "مجموعة قصص مجهولة المؤلف، تعود أصولها إلى الحضارات العربية والفارسية والهندية.",
        description: "مجموعة من القصص الشعبية العربية التي تجمع بين الخيال والحكمة والمغامرة."
    },
    {
        id: 8,
        title: "كليلة ودمنة",
        author: "ابن المقفع",
        category: "روايات وقصص",
        cover: "https://images.unsplash.com/photo-1518709268805-4e9042af2176?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 167,
        views: 530,
        likes: 378,
        liked: false,
        authorBio: "عبد الله بن المقفع، كاتب ومترجم فارسي اعتنق الإسلام، من أعلام الأدب العربي.",
        description: "كتاب حكايات رمزية على ألسنة الحيوانات، يحوي عبراً وحكماً وأمثالاً."
    },
    {
        id: 9,
        title: "الأيام",
        author: "طه حسين",
        category: "روايات وقصص",
        cover: "https://images.unsplash.com/photo-1551029506-0807df4e2031?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 154,
        views: 490,
        likes: 345,
        liked: true,
        authorBio: "طه حسين، عميد الأدب العربي، أديب وناقد مصري، من رواد حركة التنوير.",
        description: "سيرة ذاتية روائية تحكي قصة كفاح طه حسين ضد الظلام والجهل والفقر."
    },
    {
        id: 10,
        title: "عائد إلى حيفا",
        author: "غسان كنفاني",
        category: "روايات وقصص",
        cover: "https://images.unsplash.com/photo-1578662996442-48f60103fc96?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 143,
        views: 470,
        likes: 325,
        liked: false,
        authorBio: "غسان كنفاني، أديب وصحفي فلسطيني، من أبرز كتاب القضية الفلسطينية.",
        description: "رواية تعالج موضوع اللجوء الفلسطيني والهوية والصراع العربي الإسرائيلي."
    },
    {
        id: 11,
        title: "رامة والتنين",
        author: "إدوار الخراط",
        category: "روايات وقصص",
        cover: "https://images.unsplash.com/photo-1541963463532-d68292c34b19?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 132,
        views: 440,
        likes: 298,
        liked: true,
        authorBio: "إدوار الخراط، كاتب وقاص مصري، من رواد التجريب في الأدب العربي الحديث.",
        description: "رواية تحكي قصة حب في إطار فلسفي يتناول موضوعات الوجود والزمن والمصير."
    },
    {
        id: 12,
        title: "موسم الهجرة إلى الشمال",
        author: "الطيب صالح",
        category: "روايات وقصص",
        cover: "https://images.unsplash.com/photo-1543002588-bfa74002ed7e?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 176,
        views: 580,
        likes: 412,
        liked: false,
        authorBio: "الطيب صالح، روائي سوداني، يعد من أشهر الروائيين العرب في القرن العشرين.",
        description: "رواية تتعامل مع صراع الهوية والثقافة بين الشرق والغرب."
    }
];    // إضافة المزيد من الكتب لتكملة 6 كتب لكل قسم
    // كتب علمية (6 كتب)
    {
        id: 13,
        title: "الكون الأنيق",
        author: "براين غرين",
        category: "كتب علمية",
        cover: "https://images.unsplash.com/photo-1532094349884-543bc11b234d?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 145,
        views: 465,
        likes: 310,
        liked: true,
        authorBio: "براين غرين، عالم فيزياء نظرية أمريكي، متخصص في نظرية الأوتار.",
        description: "كتاب يشرح نظرية الأوتار الفائقة ومحاولات توحيد قوى الكون الأربع."
    },
    {
        id: 14,
        title: "تاريخ موجز للزمن",
        author: "ستيفن هوكينج",
        category: "كتب علمية",
        cover: "https://images.unsplash.com/photo-1559757148-5c350d0d3c56?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 167,
        views: 520,
        likes: 365,
        liked: false,
        authorBio: "ستيفن هوكينج، عالم فيزياء نظرية بريطاني، من أبرز علماء الكونيات.",
        description: "كتاب يشرح مفاهيم الكون والزمان والمكان والثقوب السوداء بلغة مبسطة."
    },
    {
        id: 15,
        title: "الجينوم",
        author: "مات ريدلي",
        category: "كتب علمية",
        cover: "https://images.unsplash.com/photo-1559757175-0eb30cd8c063?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 138,
        views: 450,
        likes: 298,
        liked: true,
        authorBio: "مات ريدلي، كاتب وعالم أحياء بريطاني، متخصص في العلوم السلوكية.",
        description: "رحلة في ثلاثة وعشرين فصلاً تشرح تاريخ الجينات البشرية وتطورها."
    },
    {
        id: 16,
        title: "الذكاء العاطفي",
        author: "دانييل جولمان",
        category: "كتب علمية",
        cover: "https://images.unsplash.com/photo-1507842217343-583bb7270b66?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 189,
        views: 610,
        likes: 432,
        liked: false,
        authorBio: "دانييل جولمان، عالم نفس وصحفي علمي أمريكي، رائد في مفهوم الذكاء العاطفي.",
        description: "كتاب يشرح أهمية الذكاء العاطفي في النجاح الشخصي والمهني والاجتماعي."
    },
    {
        id: 17,
        title: "عالم صوفي",
        author: "جوستاين غاردر",
        category: "كتب علمية",
        cover: "https://images.unsplash.com/photo-1544947950-fa07a98d237f?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 156,
        views: 500,
        likes: 356,
        liked: true,
        authorBio: "جوستاين غاردر، كاتب نرويجي، متخصص في تبسيط الفلسفة والعلوم.",
        description: "رواية فلسفية تقدم تاريخ الفلسفة الغربية بطريقة قصصية شيقة."
    },
    {
        id: 18,
        title: "الكون في قشرة جوز",
        author: "ستيفن هوكينج",
        category: "كتب علمية",
        cover: "https://images.unsplash.com/photo-1531259683007-016a7b628fc3?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 143,
        views: 480,
        likes: 325,
        liked: false,
        authorBio: "ستيفن هوكينج، أحد أعظم العقول العلمية في القرن العشرين.",
        description: "كتاب يلخص أحدث النظريات في الفيزياء الحديثة ومستقبل الكون."
    },
    
    // كتب تاريخية (6 كتب)
    {
        id: 19,
        title: "تاريخ الأمم والملوك",
        author: "الطبري",
        category: "كتب تاريخية",
        cover: "https://images.unsplash.com/photo-1541963463532-d68292c34b19?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 134,
        views: 430,
        likes: 287,
        liked: true,
        authorBio: "محمد بن جرير الطبري، مؤرخ ومفسر وفقيه مسلم، من أعلام القرن الثالث الهجري.",
        description: "أشهر كتاب في التاريخ الإسلامي العام، يغطي تاريخ البشرية من بدء الخليقة."
    },
    {
        id: 20,
        title: "الكامل في التاريخ",
        author: "ابن الأثير",
        category: "كتب تاريخية",
        cover: "https://images.unsplash.com/photo-1512820790803-83ca734da794?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 145,
        views: 460,
        likes: 312,
        liked: false,
        authorBio: "عز الدين بن الأثير، مؤرخ عربي، من أشهر مؤرخي العصر الأيوبي.",
        description: "موسوعة تاريخية شاملة تغطي تاريخ العالم حتى القرن السابع الهجري."
    },
    {
        id: 21,
        title: "مقدمة ابن خلدون",
        author: "ابن خلدون",
        category: "كتب تاريخية",
        cover: "https://images.unsplash.com/photo-1544716278-ca5e3f4abd8c?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 167,
        views: 520,
        likes: 365,
        liked: true,
        authorBio: "عبد الرحمن بن خلدون، مؤسس علم الاجتماع الحديث، وفيلسوف التاريخ.",
        description: "كتاب يؤسس لعلم العمران البشري ويعرض نظريات في تطور المجتمعات والدول."
    },
    {
        id: 22,
        title: "البداية والنهاية",
        author: "ابن كثير",
        category: "كتب تاريخية",
        cover: "https://images.unsplash.com/photo-1507842217343-583bb7270b66?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 156,
        views: 490,
        likes: 332,
        liked: false,
        authorBio: "ابن كثير الدمشقي، مفسر ومؤرخ وفقيه، من أبرز علماء القرن الثامن الهجري.",
        description: "موسوعة تاريخية تبدأ بخلق الكون وتنتهي بأحداث يوم القيامة."
    },
    {
        id: 23,
        title: "تاريخ الحضارات",
        author: "ويل ديورانت",
        category: "كتب تاريخية",
        cover: "https://images.unsplash.com/photo-1516979187457-637abb4f9353?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 178,
        views: 560,
        likes: 398,
        liked: true,
        authorBio: "ويل ديورانت، مؤرخ وفيلسوف أمريكي، حائز على جائزة بوليتزر.",
        description: "موسوعة تاريخية ضخمة تغطي تاريخ الحضارة الإنسانية من العصور القديمة."
    },
    {
        id: 24,
        title: "تاريخ العرب",
        author: "فيليب حتي",
        category: "كتب تاريخية",
        cover: "https://images.unsplash.com/photo-1481627834876-b7833e8f5570?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&h=500&q=80",
        downloads: 142,
        views: 455,
        likes: 308,
        liked: false,
        authorBio: "فيليب حتي، مؤرخ لبناني أمريكي، متخصص في التاريخ العربي والإسلامي.",
        description: "كتاب شامل عن تاريخ العرب من الجاهلية إلى العصر الحديث."
    }
];

    // حالة التطبيق
    let appState = {
        currentBook: null,
        favorites: JSON.parse(localStorage.getItem('favorites')) || [],
        viewedBooks: JSON.parse(localStorage.getItem('viewedBooks')) || [],
        likedBooks: JSON.parse(localStorage.getItem('likedBooks')) || [],
        downloadedBooks: JSON.parse(localStorage.getItem('downloadedBooks')) || [],
        darkMode: localStorage.getItem('darkMode') !== 'false',
        currentSlide: 0,
        sliderInterval: null
    };// تطبيق وضع التصميم
if (!appState.darkMode) {
    document.body.classList.add('light');
    document.getElementById('themeBtn').innerHTML = '<i class="fas fa-moon"></i>';
}

// تحديث عداد المفضلة
document.getElementById('favoritesBadge').textContent = appState.favorites.length;

// تهيئة السلايدر
function initSlider() {
    startSlider();
    
    // إضافة التحكم عند التمرير
    document.querySelector('.slider-track').addEventListener('mouseenter', function() {
        if (appState.sliderInterval) {
            clearInterval(appState.sliderInterval);
            appState.sliderInterval = null;
        }
    });
    
    document.querySelector('.slider-track').addEventListener('mouseleave', function() {
        if (!appState.sliderInterval) {
            startSlider();
        }
    });
}

function startSlider() {
    if (appState.sliderInterval) {
        clearInterval(appState.sliderInterval);
    }
    
    appState.sliderInterval = setInterval(() => {
        goToSlide((appState.currentSlide + 1) % 3);
    }, 5000);
}

function goToSlide(slideIndex) {
    appState.currentSlide = slideIndex;
    const track = document.getElementById('sliderTrack');
    track.style.transform = `translateX(-${slideIndex * 33.333}%)`;
    
    // تحديث النقاط النشطة
    document.querySelectorAll('.slider-dot').forEach((dot, index) => {
        if (index === slideIndex) {
            dot.classList.add('active');
        } else {
            dot.classList.remove('active');
        }
    });
}

// توليد الأقسام والكتب
function generateContent() {
    const container = document.getElementById('content');
    container.innerHTML = '';
    
    categories.forEach(cat => {
        const categoryBooks = booksData.filter(book => book.category === cat);
        if (categoryBooks.length === 0) return;
        
        // أخذ أول 6 كتب فقط لكل قسم
        const displayedBooks = categoryBooks.slice(0, 6);
        
        const sectionHTML = `
            <div class="section-title scale-in">
                <i class="fas fa-book"></i>
                ${cat}
                <span class="book-count">(${displayedBooks.length} كتاب)</span>
            </div>
            <div class="books-grid">
                ${displayedBooks.map(book => `
                    <div class="book-card fade-in" onclick="openBookDetails(${book.id})">
                        <div class="book-cover-container">
                            <img src="${book.cover}" alt="${book.title}" class="book-cover">
                            <div class="book-rating">
                                <i class="fas fa-star"></i>
                                ${Math.floor(Math.random() * 2 + 3)}.${Math.floor(Math.random() * 9)}
                            </div>
                            <div class="book-category">${book.category.split(' ')[0]}</div>
                        </div>
                        <div class="book-info">
                            <div class="book-title">${book.title}</div>
                            <div class="book-author">${book.author || 'مجهول'}</div>
                            <div class="book-stats">
                                <div class="book-stat">
                                    <i class="fas fa-eye"></i> ${book.views}
                                </div>
                                <div class="book-stat">
                                    <i class="fas fa-heart ${book.liked ? 'liked' : ''}"></i> ${book.likes}
                                </div>
                                <div class="book-stat">
                                    <i class="fas fa-download"></i> ${book.downloads}
                                </div>
                            </div>
                        </div>
                    </div>
                `).join('')}
            </div>
        `;
        container.innerHTML += sectionHTML;
    });
}

// توليد المحتوى عند التحميل
generateContent();
initSlider();

// القائمة الجانبية
function toggleSidebar() {
    document.getElementById('sidebar').classList.toggle('active');
}

// البحث
function toggleSearch() {
    const overlay = document.getElementById('searchOverlay');
    overlay.classList.toggle('active');
    if (overlay.classList.contains('active')) {
        document.getElementById('searchInput').focus();
        updateSuggestions('');
    }
}

// تحديث المقترحات
function updateSuggestions(query) {
    const container = document.getElementById('suggestionsContainer');
    const normalizedQuery = query.toLowerCase().trim();
    
    if (!normalizedQuery) {
        container.innerHTML = '<div class="suggestion-item" style="text-align: center; color: #888;">اكتب للبحث عن كتب أو مؤلفين</div>';
        return;
    }
    
    const filteredBooks = booksData.filter(book => 
        book.title.toLowerCase().includes(normalizedQuery) || 
        book.author.toLowerCase().includes(normalizedQuery) ||
        book.category.toLowerCase().includes(normalizedQuery)
    );
    
    if (filteredBooks.length === 0) {
        container.innerHTML = '<div class="suggestion-item" style="text-align: center; color: #888;">لا توجد نتائج</div>';
        return;
    }
    
    container.innerHTML = filteredBooks.map(book => `
        <div class="suggestion-item" onclick="openBookDetails(${book.id}); toggleSearch();">
            <img src="${book.cover}" alt="${book.title}" class="book-cover">
            <div class="suggestion-info">
                <h4>${book.title}</h4>
                <p>${book.author || 'مجهول'}</p>
                <small>${book.category}</small>
            </div>
        </div>
    `).join('');
}

// البحث في الوقت الحقيقي
document.getElementById('searchInput').addEventListener('input', function(e) {
    updateSuggestions(e.target.value);
});

// زر المشاركة
function shareSite() {
    if (navigator.share) {
        navigator.share({
            title: 'المكتبة الرقمية العربية',
            text: 'اكتشف مجموعة رائعة من الكتب العربية مجاناً',
            url: window.location.href
        });
    } else {
        alert('شارك الرابط: ' + window.location.href);
    }
}// الوضع المظلم/الفاتح
function toggleMode() {
    const isLight = document.body.classList.toggle('light');
    const themeBtn = document.getElementById('themeBtn');
    
    if (isLight) {
        themeBtn.innerHTML = '<i class="fas fa-moon"></i>';
        appState.darkMode = false;
    } else {
        themeBtn.innerHTML = '<i class="fas fa-sun"></i>';
        appState.darkMode = true;
    }
    
    localStorage.setItem('darkMode', appState.darkMode);
}

// فتح تفاصيل الكتاب
function openBookDetails(bookId) {
    const book = booksData.find(b => b.id === bookId);
    if (!book) return;
    
    appState.currentBook = book;
    
    // زيادة عدد المشاهدات
    if (!appState.viewedBooks.includes(bookId)) {
        book.views++;
        appState.viewedBooks.push(bookId);
        localStorage.setItem('viewedBooks', JSON.stringify(appState.viewedBooks));
    }
    
    // التحقق إذا كان الكتاب في المفضلة
    const isLiked = appState.likedBooks.includes(bookId);
    book.liked = isLiked;
    
    // بناء واجهة التفاصيل
    const detailsHTML = `
        <div class="book-details-header">
            <img src="${book.cover}" alt="${book.title}" class="book-details-cover">
            <div class="book-header-text">
                <h1 class="book-details-title">${book.title}</h1>
                <p class="book-details-author">${book.author || 'مجهول'}</p>
                <div class="book-stats-large">
                    <div class="stat-item-large" onclick="incrementDownloads(${bookId})">
                        <span class="stat-value-large" id="downloadsCount">${book.downloads}</span>
                        <span class="stat-label-large">⬇️ التحميلات</span>
                    </div>
                    <div class="stat-item-large">
                        <span class="stat-value-large">${book.views}</span>
                        <span class="stat-label-large">👁️ المشاهدات</span>
                    </div>
                    <div class="stat-item-large" onclick="toggleLike(${bookId})">
                        <span class="stat-value-large ${isLiked ? 'liked' : ''}" id="likesCount">${book.likes}</span>
                        <span class="stat-label-large ${isLiked ? 'liked' : ''}">❤️ الإعجابات</span>
                    </div>
                </div>
            </div>
        </div>
        <div class="book-actions">
            <button class="action-btn read-btn" onclick="openReading()">
                <i class="fas fa-book-open"></i>
                قراءة الكتاب
            </button>
            <button class="action-btn download-btn" onclick="downloadBook(${bookId})">
                <i class="fas fa-download"></i>
                تحميل الكتاب
            </button>
        </div>
        <div class="book-content">
            <div class="content-section">
                <h3><i class="fas fa-user"></i> نبذة عن المؤلف</h3>
                <p>${book.authorBio}</p>
            </div>
            <div class="content-section">
                <h3><i class="fas fa-book"></i> نبذة عن الكتاب</h3>
                <p>${book.description}</p>
            </div>
            <div class="content-section">
                <h3><i class="fas fa-tags"></i> التصنيف</h3>
                <p>${book.category}</p>
            </div>
        </div>
    `;
    
    document.querySelector('.book-details-container').innerHTML = detailsHTML;
    document.getElementById('bookDetailsOverlay').classList.add('active');
}

// إغلاق تفاصيل الكتاب
function closeBookDetails() {
    document.getElementById('bookDetailsOverlay').classList.remove('active');
    appState.currentBook = null;
}

// زيادة عدد التحميلات
function incrementDownloads(bookId) {
    const book = booksData.find(b => b.id === bookId);
    if (!book) return;
    
    // زيادة العداد مع الحد الأقصى 999
    if (book.downloads < 999) {
        book.downloads++;
        document.getElementById('downloadsCount').textContent = book.downloads;
        document.getElementById('downloadsCount').classList.add('pulse');
        
        // إزالة تأثير النبض بعد فترة
        setTimeout(() => {
            document.getElementById('downloadsCount').classList.remove('pulse');
        }, 300);
        
        // حفظ في التحميلات المحلية
        if (!appState.downloadedBooks.includes(bookId)) {
            appState.downloadedBooks.push(bookId);
            localStorage.setItem('downloadedBooks', JSON.stringify(appState.downloadedBooks));
        }
    }
}

// تبديل الإعجاب
function toggleLike(bookId) {
    const book = booksData.find(b => b.id === bookId);
    if (!book) return;
    
    const likesElement = document.getElementById('likesCount');
    const labelElement = document.querySelector('.stat-item-large:nth-child(3) .stat-label-large');
    
    if (book.liked) {
        // إلغاء الإعجاب
        if (book.likes > 0) book.likes--;
        book.liked = false;
        likesElement.classList.remove('liked');
        labelElement.classList.remove('liked');
        
        // إزالة من المفضلة
        const index = appState.likedBooks.indexOf(bookId);
        if (index > -1) {
            appState.likedBooks.splice(index, 1);
        }
        
        const favIndex = appState.favorites.indexOf(bookId);
        if (favIndex > -1) {
            appState.favorites.splice(favIndex, 1);
        }
    } else {
        // إضافة إعجاب
        if (book.likes < 999) book.likes++;
        book.liked = true;
        likesElement.classList.add('liked');
        labelElement.classList.add('liked');
        
        // إضافة للمفضلة
        if (!appState.likedBooks.includes(bookId)) {
            appState.likedBooks.push(bookId);
        }
        
        if (!appState.favorites.includes(bookId)) {
            appState.favorites.push(bookId);
        }
    }
    
    likesElement.textContent = book.likes;
    document.getElementById('favoritesBadge').textContent = appState.favorites.length;
    
    // حفظ في التخزين المحلي
    localStorage.setItem('likedBooks', JSON.stringify(appState.likedBooks));
    localStorage.setItem('favorites', JSON.stringify(appState.favorites));
    
    // تأثير النبض
    likesElement.classList.add('pulse');
    setTimeout(() => {
        likesElement.classList.remove('pulse');
    }, 300);
    
    // تحديث عرض الكتب
    generateContent();
}    // تحميل الكتاب
    function downloadBook(bookId) {
        const book = booksData.find(b => b.id === bookId);
        if (!book) return;
        
        // زيادة عدد التحميلات
        incrementDownloads(bookId);
        
        // محاكاة التحميل
        alert(`جاري تحميل "${book.title}" ...\nسيبدأ التحميل تلقائياً`);
        
        // في تطبيق حقيقي، هنا سيتم تنزيل الملف
        console.log(`Downloading book: ${book.title}`);
    }

    // فتح واجهة القراءة
    function openReading() {
        if (!appState.currentBook) return;
        
        const content = `
            <h2>${appState.currentBook.title}</h2>
            <h3>${appState.currentBook.author || 'مجهول'}</h3>
            <hr>
            <p>هذا نص تجريبي لمحتوى الكتاب "${appState.currentBook.title}". في التطبيق الحقيقي، سيتم تحميل النص الكامل للكتاب هنا.</p>
            <p>${appState.currentBook.description}</p>
            <p><strong>نبذة عن المؤلف:</strong> ${appState.currentBook.authorBio}</p>
            <h4>الفصل الأول: مقدمة الكتاب</h4>
            <p>بسم الله الرحمن الرحيم، نبدأ رحلتنا مع هذا الكتاب القيم الذي يعد من أهم المراجع في مجال ${appState.currentBook.category.split(' ')[1] || appState.currentBook.category}.</p>
            <p>لقد حرص المؤلف على تقديم المعلومة بطريقة واضحة وسهلة الفهم، معتمداً على مصادر موثوقة وأسلوب علمي رصين.</p>
            <h4>الفصل الثاني: المحتوى الرئيسي</h4>
            <p>يتناول هذا الكتاب موضوعات متعددة تهم القارئ العربي، حيث يقدم رؤية شاملة ومتكاملة للموضوع المطروح.</p>
            <p>تم تقسيم الكتاب إلى عدة أقسام لتسهيل عملية القراءة والاستيعاب، مع تقديم أمثلة وتطبيقات عملية.</p>
            <h4>الفصل الثالث: الخاتمة والتوصيات</h4>
            <p>يختتم الكتاب بمجموعة من التوصيات والخلاصات المهمة التي تساعد القارئ على تطبيق ما تعلمه.</p>
            <p>نتمنى لك قراءة ممتعة ومفيدة، وندعوك لاكتشاف المزيد من الكتب القيمة في مكتبتنا الرقمية.</p>
        `;
        
        document.getElementById('readingTitle').textContent = appState.currentBook.title;
        document.getElementById('readingContent').innerHTML = content;
        document.getElementById('readingOverlay').classList.add('active');
    }

    // إغلاق واجهة القراءة
    function closeReading() {
        document.getElementById('readingOverlay').classList.remove('active');
    }

    // تغيير حجم الخط في واجهة القراءة
    function changeFontSize(delta) {
        const content = document.getElementById('readingContent');
        const currentSize = parseFloat(window.getComputedStyle(content).fontSize);
        const newSize = currentSize + delta;
        
        // الحد الأدنى والحد الأقصى لحجم الخط
        if (newSize >= 14 && newSize <= 32) {
            content.style.fontSize = newSize + 'px';
        }
    }

    // إضافة/إزالة إشارة مرجعية
    function toggleBookmark() {
        const bookmarkBtn = document.querySelector('.reading-btn:nth-child(3) i');
        if (bookmarkBtn.classList.contains('far')) {
            bookmarkBtn.classList.remove('far');
            bookmarkBtn.classList.add('fas');
            bookmarkBtn.style.color = 'var(--gold)';
            alert('تم إضافة الإشارة المرجعية');
        } else {
            bookmarkBtn.classList.remove('fas');
            bookmarkBtn.classList.add('far');
            bookmarkBtn.style.color = '';
            alert('تم إزالة الإشارة المرجعية');
        }
    }

    // تبديل وضع القراءة الليلي
    function toggleNightMode() {
        const readingOverlay = document.getElementById('readingOverlay');
        const nightBtn = document.querySelector('.reading-btn:nth-child(4) i');
        
        if (readingOverlay.classList.contains('light')) {
            readingOverlay.classList.remove('light');
            nightBtn.classList.remove('fa-sun');
            nightBtn.classList.add('fa-moon');
        } else {
            readingOverlay.classList.add('light');
            nightBtn.classList.remove('fa-moon');
            nightBtn.classList.add('fa-sun');
        }
    }

    // عرض الأقسام
    function showSection(section) {
        // تحديث الأزرار النشطة
        document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
        event.currentTarget.classList.add('active');
        
        // إغلاق القائمة الجانبية إذا كانت مفتوحة
        document.getElementById('sidebar').classList.remove('active');
        
        // في تطبيق حقيقي، هنا سيتم تحميل المحتوى المناسب
        const sectionNames = {
            'home': 'الرئيسية',
            'library': 'المكتبة',
            'add': 'إضافة كتاب',
            'favorites': 'المفضلة',
            'profile': 'الملف الشخصي'
        };
        
        alert(`جاري تحميل قسم: ${sectionNames[section] || section}`);
    }

    // تسجيل الخروج
    function logout() {
        if (confirm('هل تريد تسجيل الخروج من المكتبة؟')) {
            localStorage.clear();
            alert('تم تسجيل الخروج بنجاح');
            location.reload();
        }
    }

    // منع الإغلاق عند النقر خارج البحث
    document.getElementById('searchOverlay').addEventListener('click', function(e) {
        if (e.target.id === 'searchOverlay') {
            toggleSearch();
        }
    });

    // منع الإغلاق عند النقر خارج تفاصيل الكتاب
    document.getElementById('bookDetailsOverlay').addEventListener('click', function(e) {
        if (e.target.id === 'bookDetailsOverlay') {
            closeBookDetails();
        }
    });

    // تهيئة البحث عند تحميل الصفحة
    document.addEventListener('DOMContentLoaded', function() {
        updateSuggestions('');
        
        // إضافة تأثيرات عند التحميل
        setTimeout(() => {
            document.querySelectorAll('.book-card').forEach((card, index) => {
                setTimeout(() => {
                    card.style.opacity = '1';
                    card.style.transform = 'translateY(0)';
                }, index * 100);
            });
        }, 300);
    });
    </script>
</body>
</html>
