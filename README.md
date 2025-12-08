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
}

/* ============ شريط الصور المتحرك ============ */
.auto-slider {
    width: 95%;
    margin: 10px auto 20px;
    height: 160px;
    overflow: hidden;
    border-radius: 12px;
    position: relative;
    box-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

.slider-track {
    display: flex;
    width: 400%;
    height: 100%;
    animation: slide 30s infinite linear;
}

.slider-track:hover {
    animation-play-state: paused;
}

.slide {
    width: 25%;
    height: 100%;
}

.slide img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

@keyframes slide {
    0% { transform: translateX(0); }
    25% { transform: translateX(0); }
    30% { transform: translateX(-25%); }
    50% { transform: translateX(-25%); }
    55% { transform: translateX(-50%); }
    75% { transform: translateX(-50%); }
    80% { transform: translateX(-75%); }
    100% { transform: translateX(-75%); }
}

/* شريط الصور الإضافي (قبل الأقسام) */
.top-slider {
    width: 100%;
    height: 140px;
    overflow: hidden;
    border-radius: 0 0 12px 12px;
    margin-bottom: 20px;
}

.top-slider-track {
    display: flex;
    width: 300%;
    height: 100%;
    animation: topSlide 40s infinite linear;
}

@keyframes topSlide {
    0% { transform: translateX(0); }
    33% { transform: translateX(0); }
    38% { transform: translateX(-33.333%); }
    66% { transform: translateX(-33.333%); }
    71% { transform: translateX(-66.666%); }
    100% { transform: translateX(-66.666%); }
}
/* ============ واجهة البحث ============ */
#searchOverlay {
    position: fixed;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.9);
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
}
/* ============ أقسام الكتب ============ */
#content {
    padding: 0 15px 30px;
}

.section-title {
    margin: 25px 0 15px;
    font-size: 22px;
    font-weight: bold;
    color: var(--primary);
    display: flex;
    align-items: center;
    gap: 10px;
    padding-right: 10px;
    border-right: 4px solid var(--primary);
}

.books-row {
    display: flex;
    overflow-x: auto;
    gap: 15px;
    padding: 10px 5px 20px;
    scrollbar-width: thin;
    scrollbar-color: var(--primary) transparent;
}

.books-row::-webkit-scrollbar {
    height: 6px;
}

.books-row::-webkit-scrollbar-track {
    background: transparent;
}

.books-row::-webkit-scrollbar-thumb {
    background-color: var(--primary);
    border-radius: 3px;
}

.book-card {
    min-width: 140px;
    height: 220px;
    background: var(--dark-card);
    border-radius: 12px;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.3s;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    position: relative;
}

body.light .book-card {
    background: var(--light-card);
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.book-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 16px rgba(0,0,0,0.3);
}

.book-cover {
    width: 100%;
    height: 140px;
    object-fit: cover;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.book-info {
    padding: 12px;
}

.book-title {
    font-weight: bold;
    font-size: 14px;
    margin-bottom: 5px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.book-author {
    font-size: 12px;
    color: #888;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

body.light .book-author {
    color: #666;
}

.book-rating {
    position: absolute;
    bottom: 10px;
    left: 10px;
    background: rgba(0,0,0,0.7);
    color: var(--gold);
    padding: 2px 6px;
    border-radius: 10px;
    font-size: 12px;
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
}

.book-details-container {
    max-width: 800px;
    margin: 0 auto;
    background: var(--dark-card);
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 10px 40px rgba(0,0,0,0.4);
}

body.light .book-details-container {
    background: var(--light-card);
}

.book-details-header {
    position: relative;
    height: 250px;
    display: flex;
    align-items: flex-end;
    padding: 20px;
    color: white;
    background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.7));
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
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 8px;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
}

.book-details-author {
    font-size: 18px;
    opacity: 0.9;
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
    overflow: hidden;
}

.book-stats {
    display: flex;
    gap: 20px;
    margin-top: 15px;
}

.stat-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    background: rgba(255,255,255,0.2);
    padding: 8px 12px;
    border-radius: 10px;
    min-width: 70px;
}

.stat-value {
    font-weight: bold;
    font-size: 18px;
}

.stat-label {
    font-size: 12px;
    opacity: 0.8;
}

.liked {
    color: #FF4081 !important;
}

.book-actions {
    display: flex;
    gap: 15px;
    padding: 20px;
    border-bottom: 1px solid rgba(255,255,255,0.1);
}

body.light .book-actions {
    border-bottom: 1px solid rgba(0,0,0,0.1);
}

.action-btn {
    flex: 1;
    padding: 12px;
    border: none;
    border-radius: 10px;
    font-size: 16px;
    font-weight: bold;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    transition: all 0.2s;
}

.read-btn {
    background: var(--primary);
    color: white;
}

.read-btn:hover {
    background: #1B5E20;
}

.download-btn {
    background: var(--accent);
    color: white;
}

.download-btn:hover {
    background: #B71C1C;
}

.book-content {
    padding: 25px;
}

.content-section {
    margin-bottom: 25px;
}

.content-section h3 {
    margin-bottom: 10px;
    color: var(--primary);
    font-size: 18px;
    border-bottom: 2px solid var(--primary);
    padding-bottom: 5px;
    display: inline-block;
}

.content-section p {
    line-height: 1.6;
    color: #ddd;
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
            padding: 10px;
        }

        /* ============ الشريط السفلي ============ */
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
            padding: 8px 15px;
            position: relative;
            transition: all 0.2s;
        }

        .nav-btn.active {
            color: var(--primary);
        }

        .nav-btn:hover {
            transform: translateY(-3px);
        }

        .nav-badge {
            position: absolute;
            top: -5px;
            left: 5px;
            background: var(--accent);
            color: white;
            font-size: 10px;
            padding: 2px 5px;
            border-radius: 10px;
            min-width: 15px;
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

        /* ============ التجاوب مع الأجهزة الصغيرة ============ */
        @media (max-width: 768px) {
            .auto-slider, .top-slider {
                height: 130px;
            }
            
            .book-card {
                min-width: 120px;
                height: 200px;
            }
            
            .book-details-header {
                height: 220px;
            }
            
            .book-stats {
                gap: 10px;
            }
            
            .stat-item {
                min-width: 60px;
                padding: 6px 8px;
            }
            
            .action-btn {
                font-size: 14px;
                padding: 10px;
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
            
            .auto-slider, .top-slider {
                height: 110px;
            }
            
            .section-title {
                font-size: 19px;
            }
            
            .book-card {
                min-width: 110px;
                height: 190px;
            }
            
            .book-details-header {
                height: 200px;
            }
            
            .book-details-title {
                font-size: 20px;
            }
            
            .book-details-author {
                font-size: 16px;
            }
            
            .book-actions {
                flex-direction: column;
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
        <div class="header-title">القدس لنا</div>
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
    </div>

    <!-- شريط الصور العلوي -->
    <div class="top-slider">
        <div class="top-slider-track">
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1524995997946-a1c2e315a42f?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="مكتبة">
            </div>
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1481627834876-b7833e8f5570?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="قراءة">
            </div>
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1532012197267-da84d127e765?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="كتب">
            </div>
        </div>
    </div>

    <!-- واجهة البحث -->
    <div id="searchOverlay">
        <div id="closeSearch" onclick="toggleSearch()">×</div>
        <div class="search-container fade-in">
            <div class="search-box">
                <input type="text" id="searchInput" placeholder="ابحث عن كتاب أو مؤلف...">
                <button><i class="fas fa-search"></i></button>
            </div>
            <div class="suggestions-container" id="suggestionsContainer">
                <!-- سيتم ملؤها بالنتائج -->
            </div>
        </div>
    </div>

    <!-- شريط الصور المتحرك -->
    <div class="auto-slider">
        <div class="slider-track">
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1507842217343-583bb7270b66?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="كتاب 1">
            </div>
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1512820790803-83ca734da794?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="كتاب 2">
            </div>
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1544716278-ca5e3f4abd8c?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="كتاب 3">
            </div>
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1516979187457-637abb4f9353?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&q=80" alt="كتاب 4">
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
            <button class="reading-btn" onclick="changeFontSize(-1)"><i class="fas fa-font"></i></button>
            <button class="reading-btn" onclick="changeFontSize(1)"><i class="fas fa-text-height"></i></button>
            <button class="reading-btn" onclick="toggleBookmark()"><i class="far fa-bookmark"></i></button>
            <button class="reading-btn" onclick="toggleNightMode()"><i class="fas fa-moon"></i></button>
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
        "كتب شائعة",
        "كتب دينية",
        "كتب ثقافية",
        "روايات وقصص",
        "كتب تعليمية",
        "كتب تطوير الذات",
        "كتب علمية",
        "كتب قانونية",
        "كتب تقنية",
        "كتب تاريخية"
    ];

    // بيانات الكتب
    const booksData = [
        {
            id: 1,
            title: "العادات الذرية",
            author: "جيمس كلير",
            category: "كتب تطوير الذات",
            cover: "https://images.unsplash.com/photo-1544716278-ca5e3f4abd8c?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 45,
            views: 120,
            likes: 89,
            liked: false,
            authorBio: "كاتب ومتحدث أمريكي مشهور في مجال تطوير الذات والعادات.",
            description: "كتاب يشرح كيفية بناء عادات صغيرة تؤدي إلى تغييرات كبيرة في الحياة."
        },
        {
            id: 2,
            title: "فن الحرب",
            author: "صن تزو",
            category: "كتب تاريخية",
            cover: "https://images.unsplash.com/photo-1516979187457-637abb4f9353?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 67,
            views: 210,
            likes: 156,
            liked: true,
            authorBio: "قائد عسكري وفيلسوف صيني قديم.",
            description: "كتاب كلاسيكي عن الاستراتيجية العسكرية والتكتيكات."
        },
        {
            id: 3,
            title: "القرآن الكريم",
            author: "",
            category: "كتب دينية",
            cover: "https://images.unsplash.com/photo-1524995997946-a1c2e315a42f?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 99,
            views: 350,
            likes: 287,
            liked: true,
            authorBio: "كتاب الله المنزل على النبي محمد صلى الله عليه وسلم.",
            description: "الكتاب المقدس للإسلام، يحتوي على توجيهات إلهية للحياة."
        },
        {
            id: 4,
            title: "الذكاء العاطفي",
            author: "دانييل جولمان",
            category: "كتب علمية",
            cover: "https://images.unsplash.com/photo-1507842217343-583bb7270b66?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 38,
            views: 165,
            likes: 112,
            liked: false,
            authorBio: "عالم نفس وصحفي علمي أمريكي.",
            description: "كتاب يشرح أهمية الذكاء العاطفي في النجاح الشخصي والمهني."
        },
        {
            id: 5,
            title: "الاقتصاد في ساعة",
            author: "د. فهد العامري",
            category: "كتب تعليمية",
            cover: "https://images.unsplash.com/photo-1512820790803-83ca734da794?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 52,
            views: 189,
            likes: 134,
            liked: false,
            authorBio: "خبير اقتصادي وكاتب سعودي متخصص في تبسيط المفاهيم الاقتصادية.",
            description: "كتاب يشرح أساسيات الاقتصاد بطريقة مبسطة وسهلة الفهم."
        },
        {
            id: 6,
            title: "برمجة تطبيقات الجوال",
            author: "أحمد السعدي",
            category: "كتب تقنية",
            cover: "https://images.unsplash.com/photo-1518709268805-4e9042af2176?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 71,
            views: 198,
            likes: 167,
            liked: true,
            authorBio: "مطور برمجيات ومدون تقني مصري.",
            description: "دليل شامل لتعلم برمجة تطبيقات الجوال للمبتدئين والمحترفين."
        },
        {
            id: 7,
            title: "قوانين العمل السعودية",
            author: "د. محمد القاضي",
            category: "كتب قانونية",
            cover: "https://images.unsplash.com/photo-1481627834876-b7833e8f5570?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 29,
            views: 143,
            likes: 98,
            liked: false,
            authorBio: "خبير قانوني وأستاذ في القانون بجامعة الملك سعود.",
            description: "شرح مفصل لقوانين العمل والأنظمة ذات الصلة في المملكة العربية السعودية."
        },
        {
            id: 8,
            title: "ألف ليلة وليلة",
            author: "مجهول",
            category: "روايات وقصص",
            cover: "https://images.unsplash.com/photo-1532012197267-da84d127e765?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 82,
            views: 267,
            likes: 201,
            liked: true,
            authorBio: "مجموعة قصص مجهولة المؤلف تعود للعصر الذهبي الإسلامي.",
            description: "مجموعة من القصص الشعبية العربية التي تجمع بين الخيال والحكمة."
        },
        {
            id: 9,
            title: "الثقافة العربية والإسلامية",
            author: "د. علي الحمداني",
            category: "كتب ثقافية",
            cover: "https://images.unsplash.com/photo-1551029506-0807df4e2031?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 41,
            views: 176,
            likes: 123,
            liked: false,
            authorBio: "باحث وأكاديمي متخصص في الدراسات الثقافية العربية والإسلامية.",
            description: "دراسة شاملة لتطور الثقافة العربية والإسلامية عبر العصور."
        },
        {
            id: 10,
            title: "التاريخ الإسلامي",
            author: "د. راغب السرجاني",
            category: "كتب تاريخية",
            cover: "https://images.unsplash.com/photo-1578662996442-48f60103fc96?ixlib=rb-1.2.1&auto=format&fit=crop&w=400&q=80",
            downloads: 63,
            views: 234,
            likes: 187,
            liked: true,
            authorBio: "مؤرخ وداعية إسلامي مصري معاصر.",
            description: "سرد تاريخي شامل للأمة الإسلامية من بداية الدعوة إلى العصر الحديث."
        }
    ];

    // حالة التطبيق
    let appState = {
        currentBook: null,
        favorites: JSON.parse(localStorage.getItem('favorites')) || [],
        viewedBooks: JSON.parse(localStorage.getItem('viewedBooks')) || [],
        likedBooks: JSON.parse(localStorage.getItem('likedBooks')) || [],
        downloadedBooks: JSON.parse(localStorage.getItem('downloadedBooks')) || [],
        darkMode: localStorage.getItem('darkMode') !== 'false'
    };

    // تطبيق وضع التصميم
    if (!appState.darkMode) {
        document.body.classList.add('light');
        document.getElementById('themeBtn').innerHTML = '<i class="fas fa-moon"></i>';
    }

    // تحديث عداد المفضلة
    document.getElementById('favoritesBadge').textContent = appState.favorites.length;
    // توليد الأقسام والكتب
function generateContent() {
    const container = document.getElementById('content');
    container.innerHTML = '';
    
    categories.forEach(cat => {
        const categoryBooks = booksData.filter(book => book.category === cat);
        if (categoryBooks.length === 0) return;
        
        const sectionHTML = `
            <div class="section-title">
                <i class="fas fa-book"></i>
                ${cat}
            </div>
            <div class="books-row">
                ${categoryBooks.map(book => `
                    <div class="book-card" onclick="openBookDetails(${book.id})">
                        <img src="${book.cover}" alt="${book.title}" class="book-cover">
                        <div class="book-info">
                            <div class="book-title">${book.title}</div>
                            <div class="book-author">${book.author || 'مجهول'}</div>
                        </div>
                        <div class="book-rating">
                            <i class="fas fa-star"></i>
                            ${Math.floor(Math.random() * 2 + 3)}.${Math.floor(Math.random() * 9)}
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
        book.author.toLowerCase().includes(normalizedQuery)
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
            text: 'اكتشف مجموعة رائعة من الكتب العربية',
            url: window.location.href
        });
    } else {
        alert('شارك الرابط: ' + window.location.href);
    }
}
// الوضع المظلم/الفاتح
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
                <div class="book-stats">
                    <div class="stat-item" onclick="incrementDownloads(${bookId})">
                        <span class="stat-value" id="downloadsCount">${book.downloads}</span>
                        <span class="stat-label">⬇️ التحميلات</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-value">${book.views}</span>
                        <span class="stat-label">👁️ المشاهدات</span>
                    </div>
                    <div class="stat-item" onclick="toggleLike(${bookId})">
                        <span class="stat-value ${isLiked ? 'liked' : ''}" id="likesCount">${book.likes}</span>
                        <span class="stat-label ${isLiked ? 'liked' : ''}">❤️ الإعجابات</span>
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
    
    // زيادة العداد مع الحد الأقصى 99
    if (book.downloads < 99) {
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
}        // تبديل الإعجاب
        function toggleLike(bookId) {
            const book = booksData.find(b => b.id === bookId);
            if (!book) return;
            
            const likesElement = document.getElementById('likesCount');
            const labelElement = document.querySelector('.stat-item:nth-child(3) .stat-label');
            
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
                if (book.likes < 99) book.likes++;
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
        }

        // تحميل الكتاب
        function downloadBook(bookId) {
            const book = booksData.find(b => b.id === bookId);
            if (!book) return;
            
            // زيادة عدد التحميلات
            incrementDownloads(bookId);
            
            // محاكاة التحميل
            alert(`جاري تحميل "${book.title}" ...`);
            
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
                <p>هذا نص تجريبي لمحتوى الكتاب. في التطبيق الحقيقي، سيتم تحميل النص الكامل للكتاب هنا.</p>
                <p>يمكنك التمرير لقراءة المحتوى كاملاً. هذا النص مخصص للعرض فقط.</p>
                <p>الكتاب يتحدث عن ${appState.currentBook.description.toLowerCase()}</p>
                <p>مؤلف الكتاب هو ${appState.currentBook.authorBio}</p>
                <p>هذا الكتاب من فئة ${appState.currentBook.category} وقد حصل على تقييمات عالية من القراء.</p>
                <p>نتمنى لك قراءة ممتعة ومفيدة. يمكنك استخدام الأزرار أدنى الشاشة للتحكم في حجم الخط والإعدادات الأخرى.</p>
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
            if (newSize >= 14 && newSize <= 30) {
                content.style.fontSize = newSize + 'px';
            }
        }

        // إضافة/إزالة إشارة مرجعية
        function toggleBookmark() {
            alert('تم حفظ الصفحة في الإشارات المرجعية');
        }

        // تبديل وضع القراءة الليلي
        function toggleNightMode() {
            const readingOverlay = document.getElementById('readingOverlay');
            readingOverlay.classList.toggle('light');
        }

        // عرض الأقسام
        function showSection(section) {
            // تحديث الأزرار النشطة
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            event.currentTarget.classList.add('active');
            
            // إغلاق القائمة الجانبية إذا كانت مفتوحة
            document.getElementById('sidebar').classList.remove('active');
            
            // في تطبيق حقيقي، هنا سيتم تحميل المحتوى المناسب
            alert(`عرض قسم: ${section}`);
        }

        // تسجيل الخروج
        function logout() {
            if (confirm('هل تريد تسجيل الخروج؟')) {
                alert('تم تسجيل الخروج');
                // في تطبيق حقيقي، هنا سيتم توجيه المستخدم لصفحة تسجيل الدخول
            }
        }

        // منع الإغلاق عند النقر خارج البحث (اختياري)
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
        });
    </script>
</body>
</html>
