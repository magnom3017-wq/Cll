<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>المكتبة الرقمية</title>

    <style>
        body {
            margin: 0;
            font-family: sans-serif;
            background: #121212;
            color: white;
            transition: 0.3s;
        }

        body.light {
            background: #f5f5f5;
            color: #000;
        }

        /* هيدر */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: #1c1c1c;
            padding: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 20;
        }
        body.light header {
            background: white;
        }

        header button {
            background: none;
            border: none;
            color: inherit;
            font-size: 22px;
            cursor: pointer;
            padding: 5px 10px;
        }

        /* القائمة الجانبية */
        #sidebar {
            position: fixed;
            top: 0;
            right: -260px;
            width: 260px;
            height: 100%;
            background: #1c1c1c;
            transition: 0.3s;
            z-index: 30;
            padding: 20px;
        }
        body.light #sidebar {
            background: white;
        }

        #sidebar h2 {
            margin-top: 0;
        }

        #closeSidebar {
            font-size: 26px;
            cursor: pointer;
            color: red;
            position: absolute;
            left: 15px;
            top: 10px;
        }

        /* شريط الصور التحفيزية */
        .slider {
            margin-top: 80px;
            width: 100%;
            height: 160px;
            overflow: hidden;
            border-radius: 10px;
        }

        .slider img {
            width: 100%;
            height: 160px;
            object-fit: cover;
        }

        /* الأقسام */
        .section-title {
            margin: 20px 10px 5px;
            font-size: 20px;
            font-weight: bold;
        }

        .books-row {
            display: flex;
            overflow-x: auto;
            gap: 10px;
            padding: 10px;
        }

        .book {
            min-width: 120px;
            height: 170px;
            background: #333;
            border-radius: 10px;
        }

        body.light .book {
            background: #ddd;
        }

        /* شريط سفلي */
        footer {
            position: fixed;
            bottom: 0;
            width: 100%;
            background: #1c1c1c;
            display: flex;
            justify-content: space-around;
            padding: 10px;
        }
        body.light footer {
            background: white;
        }

        footer button {
            background: none;
            border: none;
            color: inherit;
            font-size: 23px;
            cursor: pointer;
        }

        /* البحث */
        #searchBox {
            display: none;
            position: fixed;
            top: 60px;
            width: 90%;
            right: 5%;
            background: white;
            color: black;
            padding: 10px;
            border-radius: 10px;
            z-index: 25;
        }
        #searchBox input {
            width: 100%;
            padding: 10px;
            font-size: 17px;
            border: none;
            outline: none;
        }

    </style>
</head>
<body>

    <!-- الهيدر -->
    <header>
        <button onclick="toggleSidebar()">☰</button>
        <div>
            <button onclick="toggleSearch()">🔍</button>
            <button onclick="shareSite()">📤</button>
            <button onclick="toggleMode()">🌗</button>
        </div>
    </header>

    <!-- القائمة الجانبية -->
    <div id="sidebar">
        <span id="closeSidebar" onclick="toggleSidebar()">×</span>
        <h2>القائمة</h2>
        <p>الرئيسية</p>
        <p>المفضلة</p>
        <p>الإعدادات</p>
        <p>تسجيل خروج</p>
    </div>

    <!-- البحث -->
    <div id="searchBox">
        <input type="text" placeholder="ابحث عن كتاب...">
    </div>

    <!-- شريط الصور -->
    <div class="slider">
        <img src="https://i.imgur.com/aYtN9.png" alt="">
    </div>

    <!-- الأقسام -->
    <script>
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
    </script>

    <div id="content"></div>

    <!-- الشريط السفلي -->
    <footer>
        <button>🏠</button>
        <button>📚</button>
        <button>➕</button>
        <button>⭐</button>
        <button>👤</button>
    </footer>

    <script>
        // توليد الأقسام تلقائياً
        const container = document.getElementById("content");

        categories.forEach(cat => {
            container.innerHTML += `
                <div class="section-title">${cat}</div>
                <div class="books-row">
                    <div class="book"></div>
                    <div class="book"></div>
                    <div class="book"></div>
                    <div class="book"></div>
                </div>
            `;
        });

        // القائمة
        function toggleSidebar() {
            let bar = document.getElementById("sidebar");
            bar.style.right = (bar.style.right === "0px") ? "-260px" : "0px";
        }

        // البحث
        function toggleSearch() {
            let s = document.getElementById("searchBox");
            s.style.display = (s.style.display === "block") ? "none" : "block";
        }

        // الوضع الداكن
        function toggleMode() {
            document.body.classList.toggle("light");
        }

        // مشاركة
        function shareSite() {
            navigator.share ?
                navigator.share({ title: "المكتبة الرقمية", url: location.href }) :
                alert("المشاركة غير مدعومة في جهازك");
        }
    </script>

</body>
</html>
