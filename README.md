<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>池上素食旅遊導覽</title>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@300;400;500;700&display=swap" rel="stylesheet">
    <style>
        /* --- 變數與色彩規劃 --- */
        :root {
            --rice-green: #A9C686; /* 主色：稻田綠 */
            --sky-blue: #8FC8E2;   /* 輔色：天空藍 */
            --sun-yellow: #F5D76E; /* 強調色：日光黃 */
            --cream-bg: #FFFDF5;   /* 背景：米白 */
            --text-dark: #4A5D23;
            --white: #ffffff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            text-decoration: none; /* 移除選單字體底線 */
            list-style: none;
        }

        body {
            font-family: 'Noto Sans TC', sans-serif;
            background-color: var(--cream-bg);
            color: var(--text-dark);
            scroll-behavior: smooth;
        }

        /* --- 導覽列 UI --- */
        header {
            background-color: var(--white);
            height: 80px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 5%;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--rice-green);
        }

        .nav-container {
            height: 100%;
        }

        .nav-main {
            display: flex;
            height: 100%;
        }

        .nav-item {
            position: relative;
            height: 100%;
            display: flex;
            align-items: center;
        }

        .nav-link {
            padding: 0 20px;
            color: var(--text-dark);
            font-weight: 500;
            transition: 0.3s;
        }

        .nav-link:hover {
            color: var(--rice-green);
        }

        /* --- 下拉式選單 CSS --- */
        .dropdown {
            position: absolute;
            top: 80px;
            right: 0;
            background-color: var(--white);
            min-width: 250px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.1);
            opacity: 0;
            visibility: hidden;
            transform: translateY(10px);
            transition: all 0.3s ease;
            border-bottom: 4px solid var(--sun-yellow);
        }

        .nav-item:hover .dropdown {
            opacity: 1;
            visibility: visible;
            transform: translateY(0);
        }

        .dropdown li a {
            padding: 12px 20px;
            display: block;
            color: #666;
            font-size: 0.95rem;
            border-bottom: 1px solid #f9f9f9;
        }

        .dropdown li a:hover {
            background-color: var(--cream-bg);
            color: var(--rice-green);
            padding-left: 25px;
            transition: 0.2s;
        }

        .submenu-title {
            background-color: #f1f5f1;
            padding: 8px 20px;
            font-size: 0.8rem;
            font-weight: 700;
            color: var(--text-dark);
            display: block;
        }

        /* =====================
   跑馬燈區
===================== */
        .slider {
          position: relative;
          width: 100%;           /* 撐滿整個畫面寬度 */
          height: 840px;         /* 增加高度，畫面更大 */
          margin: 0 auto;        /* 水平置中（保險用） */
          overflow: hidden;      /* 超出範圍的圖片裁切 */
          display: flex;
          justify-content: center; /* 確保內容不偏移 */
        }

/* 跑馬燈圖片 */
        .slide {
          position: absolute;
          top: 0;
          left: 0;
          width: 100%;          /* 圖片寬度撐滿 */
          max-height: 100%;         /* 圖片高度撐滿 */
          object-fit: contain;    /* 等比例裁切，不變形 */
          opacity: 0;
          transition: opacity 1s ease-in-out;
        }

/* 顯示中的圖片 */
        .slide.active {
          opacity: 1;
        }

        /* --- 區塊設定 --- */
        #section {
            padding: 80px 10%;
            min-height: 40vh;
        }

        /* 首頁空白介面 */
        #home {
           /* display: flex; */
            flex-direction: column;
            align-items: center;
            text-align: center;
        }

        .home-content {
            padding: 40px;
            color: var(--rice-green);
            font-size: 20px;
        }

        /* 聯絡資訊獨立介面 */
        #contact {
            background-color: var(--sky-blue);
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .contact-card {
            background: white;
            padding: 60px;
            border-radius: 20px;
            color: var(--text-dark);
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            max-width: 500px;
            width: 90%;
        }

        .email-link {
            color: var(--sky-blue);
            font-weight: 700;
            font-size: 1.3rem;
            display: block;
            margin: 20px 0;
        }
        
        .contact-card h2 {
            margin-bottom: 10px;
        }

        footer {
            text-align: center;
            padding: 20px;
            background: var(--rice-green);
            color: white;
            font-size: 20px;
        }

    </style>
</head>
<body>

    <header>
        <a href="#home" class="logo">池上旅遊導覽</a>
        <nav class="nav-container">
            <ul class="nav-main">
                <li class="nav-item"><a href="#home" class="nav-link">首頁</a></li>
                
                <li class="nav-item">
                    <a href="#" class="nav-link">景點導覽 ▾</a>
                    <ul class="dropdown">
                        <span class="submenu-title">自然景觀</span>
                        <li><a href="https://tour.taitung.gov.tw/zh-tw/attraction/details/430" target="_blank">伯朗大道</a></li>
                        <li><a href="https://tour.taitung.gov.tw/zh-tw/media/live-camera/14" target="_blank">天堂路</a></li>
                        <li><a href="https://tour.taitung.gov.tw/zh-tw/attraction/details/252" target="_blank">池上大坡池</a></li>
                        <li><a href="https://tour.taitung.gov.tw/zh-tw/attraction/details/1391" target="_blank">金城武樹</a></li>
                        <span class="submenu-title">人文景點</span>
                        <li><a href="https://tour.taitung.gov.tw/zh-tw/attraction/details/1429" target="_blank">池上穀倉藝術館</a></li>
                        <li><a href="https://tour.taitung.gov.tw/zh-tw/attraction/details/1591" target="_blank">池上圳進水口公園</a></li>
                        <li><a href="https://tour.taitung.gov.tw/zh-tw/attraction/details/458" target="_blank">金色豐收館</a></li>
                        <li><a href="https://tour.taitung.gov.tw/zh-tw/attraction/details/1312" target="_blank">地牛故事館</a></li>
                    </ul>
                </li>

                <li class="nav-item">
                    <a href="#" class="nav-link">素食美食 ▾</a>
                    <ul class="dropdown">
                        <li><a href="https://maps.app.goo.gl/yJ8UBKEmZwPAzmVq7" target="_blank">巧本味蔬食人文料理</a></li>
                        <li><a href="https://maps.app.goo.gl/aCi74yytqfzHR9Vx7" target="_blank">舒食男孩</a></li>
                        <li><a href="https://maps.app.goo.gl/v2wiSHpYdDvBY6PR9" target="_blank">吉祥軒素食飯包店</a></li>
                        <li><a href="https://maps.app.goo.gl/FzGogJQb1a1LfN1n8" target="_blank">池上百寶蔬食</a></li>
                        <li><a href="https://maps.app.goo.gl/xMMqbiHDzr1Zodeh7" target="_blank">舒食男孩滷味店</a></li>
                        <li><a href="https://maps.app.goo.gl/9TcenWaRL5zk6tAEA" target="_blank">池上豆之間</a></li>
                        <li><a href="https://maps.app.goo.gl/MteunXP4FAPP1XHeA" target="_blank">保庇素食</a></li>
                    </ul>
                </li>

                <li class="nav-item">
                    <a href="#" class="nav-link">素食早餐 ▾</a>
                    <ul class="dropdown">
                        <li><a href="https://maps.app.goo.gl/w5aGyLWmyUixPsX88" target="_blank">秋月養生素食早餐</a></li>
                        <li><a href="https://maps.app.goo.gl/p4XhNJLW6meeVAg78" target="_blank">大佛水煎包池上店</a></li>
                    </ul>
                </li>

                <li class="nav-item">
                    <a href="#" class="nav-link">住宿資訊 ▾</a>
                    <ul class="dropdown">
                        <li><a href="https://maps.app.goo.gl/mCkkX7HhcQa86f7y6" target="_blank">好和院景 How Has (素食早餐)</a></li>
                        <li><a href="https://maps.app.goo.gl/UYMpNtQNLihccU1d8" target="_blank">稻荷寒舍 (素食早餐)</a></li>
                        <li><a href="https://maps.app.goo.gl/QgVkvQ1hN7S361aR8" target="_blank">池上稻香文旅</a></li>
                        <li><a href="https://maps.app.goo.gl/CSiaaBgWNrMKgAiH8" target="_blank">池上伯朗大道民宿</a></li>
                        <li><a href="https://maps.app.goo.gl/K4GZ15v5RSGGSf1S6" target="_blank">玉蟾園民宿 (寵物友善)</a></li>
                    </ul>
                </li>

                <li class="nav-item"><a href="#contact" class="nav-link">聯絡資訊</a></li>
            </ul>
        </nav>
    </header>


    <!-- =====================
     圖片跑馬燈區塊
===================== -->
      <section class="slider">
  <!-- 跑馬燈圖片 -->
          <img src="768.jpg" class="slide.active">
          <img src="769.jpg" class="slide">
          <img src="814.jpg" class="slide">
          <img src="768.jpg" class="slide">
          <img src="769.jpg" class="slide">
          <img src="814.jpg" class="slide">
  <!-- 圖片上的文字 -->
      </section>

      
    <script>
        let slides = document.querySelectorAll(".slide");
        let current = 0;

        setInterval(() => {
            slides[current].classList.remove("active");
            current = (current + 1)% slides.length;
            slides[current].classList.add("active");
        },3000);
    </script>

    <section id="home">
        <div class="home-content">
            <h1>歡迎來到池上</h1>
            <p>感受稻浪的律動與蔬食的純粹</p>
        </div>
    </section>

    <section id="contact">
        <div class="contact-card">
            <h2>聯絡資訊</h2>
            <p>如果有任何建議或問題，歡迎聯繫我們</p>
            <a href="mailto:starxuan0411@gmail.com" class="email-link">starxuan0411@gmail.com</a>
            <p style="font-size: 1.5rem; color: var(--rice-green); font-weight: 700;">很高興為你服務</p>
        </div>
    </section>

    <footer>
        <p>2025 池上素食旅遊導覽 - 感受大地的溫暖</p>
    </footer>

</body>
</html>
