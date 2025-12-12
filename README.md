<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>المكتبة الرقمية العربية</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #2c3e50;
            --secondary: #34495e;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --text: #333;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: var(--text);
            transition: background 0.3s;
            overflow-x: hidden;
        }

        /* شريط الصور العلوي */
        .hero-slider {
            position: relative;
            width: 100%;
            height: 400px;
            overflow: hidden;
            margin-top: 60px;
            border-radius: 0 0 20px 20px;
            box-shadow: var(--shadow);
        }

        .slides-container {
            display: flex;
            width: 300%;
            height: 100%;
            transition: transform 0.5s ease-in-out;
        }

        .slide {
            flex: 1;
            position: relative;
            min-width: 100%;
            height: 100%;
        }

        .slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: brightness(0.7);
        }

        .slide-content {
            position: absolute;
            top: 50%;
            right: 50px;
            transform: translateY(-50%);
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
            max-width: 500px;
        }

        .slide-content h2 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }

        .slide-content p {
            font-size: 1.2rem;
            margin-bottom: 30px;
        }

        .hero-btn {
            background: var(--accent);
            color: white;
            border: none;
            padding: 12px 25px;
            font-size: 1.1rem;
            border-radius: 30px;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .hero-btn:hover {
            background: #c0392b;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        /* أزرار التنقل */
        .slide-nav {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(0,0,0,0.5);
            color: white;
            border: none;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
        }

        .slide-nav:hover {
            background: rgba(0,0,0,0.8);
        }

        .slide-nav.prev {
            right: 20px;
        }

        .slide-nav.next {
            left: 20px;
        }

        /* النقاط الإرشادية */
        .slide-dots {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 10px;
        }

        .dot {
            width: 12px;
            height: 12px;
            background: rgba(255,255,255,0.5);
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s;
        }

        .dot.active {
            background: var(--accent);
            transform: scale(1.3);
        }

        /* باقي CSS كما هو */
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            box-shadow: var(--shadow);
            margin-top: -50px;
            position: relative;
            z-index: 1;
        }
    </style>
</head>
<body>
    <!-- الهيدر -->
    <header>
        <!-- ... (نفس الكود السابق) ... -->
    </header>

    <!-- شريط الصور العلوي (مُصلح) -->
    <div class="hero-slider" onmouseenter="stopAutoSlide()" onmouseleave="resumeAutoSlide()">
        <div class="slides-container">
            <div class="slide active">
                <img src="https://images.unsplash.com/photo-1481627834876-b7833e8f5570?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&h=400&q=80" alt="مكتبة عربية">
                <div class="slide-content">
                    <h2>أكبر مكتبة رقمية عربية</h2>
                    <p>آلاف الكتب المجانية في جميع المجالات</p>
                    <button onclick="toggleSearch()" class="hero-btn">
                        <i class="fas fa-search"></i> ابدأ البحث الآن
                    </button>
                </div>
            </div>
            
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1506880018603-83d5b814b5a6?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&h=400&q=80" alt="قراءة إلكترونية">
                <div class="slide-content">
                    <h2>اقرأ أينما كنت</h2>
                    <p>تصفح مكتبتنا من أي جهاز، في أي وقت</p>
                    <button onclick="loadBooks()" class="hero-btn">
                        <i class="fas fa-book-open"></i> استعرض الكتب
                    </button>
                </div>
            </div>
            
            <div class="slide">
                <img src="https://images.unsplash.com/photo-1521587760476-6c12a4b040da?ixlib=rb-1.2.1&auto=format&fit=crop&w=1200&h=400&q=80" alt="كتب متنوعة">
                <div class="slide-content">
                    <h2>أحدث الإصدارات</h2>
                    <p>اكتشف كتبًا جديدة تضاف أسبوعيًا</p>
                    <button onclick="showNewBooks()" class="hero-btn">
                        <i class="fas fa-star"></i> الكتب الجديدة
                    </button>
                </div>
            </div>
        </div>
        
        <!-- أزرار التنقل -->
        <button class="slide-nav prev" onclick="changeSlide(-1)">
            <i class="fas fa-chevron-right"></i>
        </button>
        <button class="slide-nav next" onclick="changeSlide(1)">
            <i class="fas fa-chevron-left"></i>
        </button>
        
        <!-- النقاط الإرشادية -->
        <div class="slide-dots">
            <span class="dot active" onclick="goToSlide(0)"></span>
            <span class="dot" onclick="goToSlide(1)"></span>
            <span class="dot" onclick="goToSlide(2)"></span>
        </div>
    </div>

    <!-- المحتوى الرئيسي -->
    <div class="container">
        <div id="content"></div>
    </div>

    <!-- النوافذ المنبثقة -->
    <div id="searchOverlay" class="overlay">
        <!-- ... (نفس الكود السابق) ... -->
    </div>
    
    <div id="bookDetailsOverlay" class="overlay">
        <!-- ... (نفس الكود السابق) ... -->
    </div>
    
    <div id="readingOverlay" class="overlay">
        <!-- ... (نفس الكود السابق) ... -->
    </div>
    <script>
    // بيانات الكتب (نفسها)
    const booksData = [
        // ... (نفس مصفوفة الكتب السابقة) ...
    ];

    const categories = ['كتب تطوير الذات', 'كتب تعليمية'];

    // ========== دوال الشريط العلوي ==========
    let currentSlide = 0;
    let slideInterval;
    const slides = document.querySelectorAll ? document.querySelectorAll('.slide') : [];
    const dots = document.querySelectorAll ? document.querySelectorAll('.dot') : [];

    // دالة التبديل بين الشرائح
    function changeSlide(direction) {
        if (slides.length === 0) return;
        
        // إزالة النشاط من الشريحة والنقطة الحالية
        slides[currentSlide].classList.remove('active');
        dots[currentSlide].classList.remove('active');
        
        // حساب الشريحة الجديدة
        currentSlide = (currentSlide + direction + slides.length) % slides.length;
        
        // إضافة النشاط للشريحة والنقطة الجديدة
        slides[currentSlide].classList.add('active');
        dots[currentSlide].classList.add('active');
        
        // إعادة تشغيل المؤقت التلقائي
        resetAutoSlide();
    }

    // دالة للذهاب لشريحة محددة
    function goToSlide(slideIndex) {
        if (slides.length === 0) return;
        
        slides[currentSlide].classList.remove('active');
        dots[currentSlide].classList.remove('active');
        
        currentSlide = slideIndex;
        
        slides[currentSlide].classList.add('active');
        dots[currentSlide].classList.add('active');
        
        resetAutoSlide();
    }

    // دالة بدء التمرير التلقائي
    function startAutoSlide() {
        if (slides.length === 0) return;
        
        slideInterval = setInterval(() => {
            changeSlide(1); // الانتقال للشريحة التالية
        }, 3000); // كل 3000 مللي ثانية (3 ثوانٍ)
    }

    // دالة إعادة ضبط المؤقت التلقائي
    function resetAutoSlide() {
        clearInterval(slideInterval);
        startAutoSlide();
    }

    // دالة لإيقاف التمرير التلقائي عند التمرير فوق الشريط
    function stopAutoSlide() {
        clearInterval(slideInterval);
    }

    // دالة لاستئناف التمرير التلقائي
    function resumeAutoSlide() {
        startAutoSlide();
    }

    // دالة عرض الكتب الجديدة
    function showNewBooks() {
        const newBooks = booksData.filter(book => book.id >= 31);
        displaySearchResults(newBooks);
    }

    // ========== دوال المكتبة الرئيسية ==========
    function loadBooks() {
        const content = document.getElementById('content');
        content.innerHTML = '';
        
        categories.forEach(category => {
            const section = document.createElement('div');
            section.className = 'section';
            
            const sectionTitle = document.createElement('h2');
            sectionTitle.className = 'section-title';
            sectionTitle.innerHTML = `<i class="fas fa-book"></i> ${category}`;
            
            const booksSliderContainer = document.createElement('div');
            booksSliderContainer.className = 'books-slider-container';
            
            const booksSlider = document.createElement('div');
            booksSlider.className = 'books-slider';
            booksSlider.id = `slider-${category}`;
            
            // فلترة الكتب حسب التصنيف
            const categoryBooks = booksData.filter(book => book.category === category);
            
            // إضافة الكتب
            categoryBooks.forEach(book => {
                const bookCard = document.createElement('div');
                bookCard.className = 'book-card';
                bookCard.onclick = () => showBookDetails(book.id);
                
                bookCard.innerHTML = `
                    <div class="book-cover-container">
                        <img src="${book.cover}" alt="${book.title}" class="book-cover">
                        <div class="book-rating">
                            <i class="fas fa-star"></i>
                            ${(book.likes / 10).toFixed(1)}
                        </div>
                        <div class="book-category">${book.category}</div>
                    </div>
                    <div class="book-info">
                        <div class="book-title">${book.title}</div>
                        <div class="book-author">${book.author}</div>
                        <div class="book-stats">
                            <div class="book-stat">
                                <i class="fas fa-download"></i>
                                ${book.downloads}
                            </div>
                            <div class="book-stat">
                                <i class="fas fa-eye"></i>
                                ${book.views}
                            </div>
                            <div class="book-stat">
                                <i class="fas fa-heart" style="color: ${book.liked ? 'var(--accent)' : '#aaa'}"></i>
                                ${book.likes}
                            </div>
                        </div>
                    </div>
                `;
                
                booksSlider.appendChild(bookCard);
            });
            
            booksSliderContainer.appendChild(booksSlider);
            section.appendChild(sectionTitle);
            section.appendChild(booksSliderContainer);
            content.appendChild(section);
        });
    }
        // دالة البحث
    function searchBooks() {
        const searchInput = document.getElementById('searchInput').value.toLowerCase();
        const searchResults = booksData.filter(book => 
            book.title.toLowerCase().includes(searchInput) ||
            book.author.toLowerCase().includes(searchInput) ||
            book.category.toLowerCase().includes(searchInput) ||
            book.description.toLowerCase().includes(searchInput)
        );
        
        displaySearchResults(searchResults);
    }

    function displaySearchResults(results) {
        const searchOverlay = document.getElementById('searchOverlay');
        const searchResultsContainer = document.getElementById('searchResults');
        
        if (results.length === 0) {
            searchResultsContainer.innerHTML = `
                <div class="no-results">
                    <i class="fas fa-search"></i>
                    <h3>لا توجد نتائج</h3>
                    <p>لم يتم العثور على كتب تطابق بحثك</p>
                </div>
            `;
        } else {
            searchResultsContainer.innerHTML = `
                <h3 class="search-results-title">نتائج البحث (${results.length})</h3>
                <div class="search-results-grid">
                    ${results.map(book => `
                        <div class="search-book-card" onclick="showBookDetails(${book.id})">
                            <img src="${book.cover}" alt="${book.title}" class="search-book-cover">
                            <div class="search-book-info">
                                <h4>${book.title}</h4>
                                <p class="search-book-author">${book.author}</p>
                                <div class="search-book-stats">
                                    <span><i class="fas fa-download"></i> ${book.downloads}</span>
                                    <span><i class="fas fa-heart" style="color: ${book.liked ? 'var(--accent)' : '#aaa'}"></i> ${book.likes}</span>
                                </div>
                            </div>
                        </div>
                    `).join('')}
                </div>
            `;
        }
        
        searchOverlay.classList.add('active');
    }

    function clearSearch() {
        document.getElementById('searchInput').value = '';
        document.getElementById('searchResults').innerHTML = '';
    }

    // دوال المكتبة الأخرى (نفسها)
    function showBookDetails(bookId) {
        // ... (نفس الكود السابق) ...
    }

    function closeBookDetails() {
        document.getElementById('bookDetailsOverlay').classList.remove('active');
    }

    function readBook(bookId) {
        // ... (نفس الكود السابق) ...
    }

    function closeReading() {
        document.getElementById('readingOverlay').classList.remove('active');
    }

    function handleDownload(bookId) {
        // ... (نفس الكود السابق) ...
    }

    function toggleLike(bookId) {
        // ... (نفس الكود السابق) ...
    }

    function updateBookDisplay(bookId) {
        // ... (نفس الكود السابق) ...
    }

    function updateFavoritesCount() {
        // ... (نفس الكود السابق) ...
    }

    function changeFontSize(change) {
        // ... (نفس الكود السابق) ...
    }

    function toggleBookmark() {
        // ... (نفس الكود السابق) ...
    }

    function toggleNightMode() {
        // ... (نفس الكود السابق) ...
    }

    function logout() {
        // ... (نفس الكود السابق) ...
    }

    // دوال الواجهة
    function toggleSidebar() {
        document.getElementById('sidebar').classList.toggle('active');
    }
    
    function toggleSearch() {
        document.getElementById('searchOverlay').classList.toggle('active');
        if (document.getElementById('searchOverlay').classList.contains('active')) {
            document.getElementById('searchInput').focus();
        }
    }
    
    function toggleMode() {
        document.body.classList.toggle('light');
        const themeBtn = document.getElementById('themeBtn');
        if (document.body.classList.contains('light')) {
            themeBtn.innerHTML = '<i class="fas fa-moon"></i>';
            themeBtn.title = 'الوضع الليلي';
        } else {
            themeBtn.innerHTML = '<i class="fas fa-sun"></i>';
            themeBtn.title = 'الوضع النهاري';
        }
    }
    
    function showSection(section) {
        console.log('عرض قسم: ' + section);
        document.querySelectorAll('.nav-btn').forEach(btn => {
            btn.classList.remove('active');
        });
        event.target.classList.add('active');
    }
    
    function shareSite() {
        if (navigator.share) {
            navigator.share({
                title: 'المكتبة الرقمية العربية',
                text: 'اكتشف آلاف الكتب العربية المجانية',
                url: window.location.href
            });
        } else {
            alert('المشاركة غير مدعومة في هذا المتصفح. يمكنك نسخ الرابط: ' + window.location.href);
        }
    }

    // ========== تهيئة الصفحة ==========
    document.addEventListener('DOMContentLoaded', function() {
        // تحميل الكتب
        loadBooks();
        updateFavoritesCount();
        
        // بدء الشريط التلقائي بعد تأخير بسيط
        setTimeout(() => {
            startAutoSlide();
        }, 1000);
        
        // إضافة مستمعات الأحداث لإيقاف/استئناف التمرير
        const heroSlider = document.querySelector('.hero-slider');
        if (heroSlider) {
            heroSlider.addEventListener('mouseenter', stopAutoSlide);
            heroSlider.addEventListener('mouseleave', resumeAutoSlide);
        }
        
        // إضافة وسم META للعربية
        const meta = document.createElement('meta');
        meta.name = "description";
        meta.content = "المكتبة الرقمية العربية - أكبر مكتبة عربية تحتوي على آلاف الكتب المجانية";
        document.head.appendChild(meta);
    });
</script>
</body>
</html>
