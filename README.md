<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>(주)성화태크 | SUNGHWA TECH</title>
    <link href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css" rel="stylesheet">
    <style>
        :root {
            --primary: #2B5B84;       /* 신선한 딥 파스텔 블루 */
            --secondary: #EBF4F6;     /* 밀크 부드러운 배경색 */
            --accent: #68A0A6;        /* 포인트 그린/블루 */
            --text-main: #2C3E50;
            --text-sub: #667085;
            --bg-cream: #FDFBF7;     /* 따뜻한 유제품 느낌의 크림색 */
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, system-ui, Roboto, sans-serif;
        }

        body {
            color: var(--text-main);
            background-color: var(--bg-cream);
            line-height: 1.7;
            word-break: keep-all;
        }

        /* Navigation */
        header {
            position: sticky;
            top: 0;
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 18px 8%;
            z-index: 1000;
            border-bottom: 1px solid #EAEAEA;
        }

        .logo {
            font-size: 1.3rem;
            font-weight: 700;
            color: var(--primary);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .logo span {
            font-size: 0.85rem;
            color: var(--accent);
            font-weight: 500;
        }

        nav a {
            margin-left: 28px;
            text-decoration: none;
            color: var(--text-main);
            font-weight: 500;
            font-size: 0.95rem;
            transition: color 0.2s;
        }

        nav a:hover {
            color: var(--primary);
        }

        /* Hero Section */
        .hero {
            padding: 100px 8% 80px;
            text-align: center;
            background: linear-gradient(180deg, #EBF4F6 0%, var(--bg-cream) 100%);
            border-radius: 0 0 40px 40px;
        }

        .hero .badge {
            display: inline-block;
            padding: 6px 16px;
            background-color: #FFFFFF;
            border: 1px solid #D1E5E7;
            border-radius: 20px;
            font-size: 0.85rem;
            color: var(--primary);
            font-weight: 600;
            margin-bottom: 20px;
        }

        .hero h1 {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 16px;
            letter-spacing: -0.5px;
        }

        .hero p {
            font-size: 1.1rem;
            color: var(--text-sub);
            max-width: 600px;
            margin: 0 auto;
        }

        /* Section Layout */
        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 80px 20px;
        }

        .section-title {
            text-align: center;
            margin-bottom: 50px;
        }

        .section-title h2 {
            font-size: 1.8rem;
            color: var(--primary);
            font-weight: 700;
        }

        .section-title p {
            font-size: 0.95rem;
            color: var(--text-sub);
            margin-top: 6px;
        }

        /* Cards & Grids */
        .grid-3 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 24px;
        }

        .card {
            background: #FFFFFF;
            padding: 36px 28px;
            border-radius: 20px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.03);
            border: 1px solid #F0F0F0;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.06);
        }

        .card .icon-box {
            width: 48px;
            height: 48px;
            background: var(--secondary);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.3rem;
            margin-bottom: 20px;
            color: var(--primary);
        }

        .card h3 {
            font-size: 1.2rem;
            margin-bottom: 10px;
            color: var(--primary);
        }

        .card p {
            font-size: 0.95rem;
            color: var(--text-sub);
        }

        /* Organization Badges */
        .dept-list {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            justify-content: center;
            margin-top: 20px;
        }

        .dept-item {
            background: #FFFFFF;
            border: 1px solid #E2E8F0;
            padding: 12px 24px;
            border-radius: 30px;
            font-weight: 500;
            color: var(--text-main);
            font-size: 0.95rem;
            box-shadow: 0 2px 6px rgba(0,0,0,0.02);
        }

        .dept-item.core {
            background: var(--primary);
            color: #FFFFFF;
            border-color: var(--primary);
        }

        /* Footer */
        footer {
            background: #24292E;
            color: #9AA0A6;
            padding: 60px 8% 40px;
            font-size: 0.88rem;
        }

        .footer-content {
            max-width: 1100px;
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            gap: 30px;
            border-bottom: 1px solid #3A3F44;
            padding-bottom: 40px;
        }

        .footer-brand h3 {
            color: #FFFFFF;
            font-size: 1.2rem;
            margin-bottom: 10px;
        }

        .footer-details p {
            margin-bottom: 6px;
        }

        .copyright {
            max-width: 1100px;
            margin: 30px auto 0;
            text-align: center;
            font-size: 0.8rem;
            color: #6C7278;
        }
    </style>
</head>
<body>

    <!-- Header Navigation -->
    <header>
        <a href="#" class="logo">
            (주)성화태크 <span>SUNGHWA TECH</span>
        </a>
        <nav>
            <a href="#about">기업소개</a>
            <a href="#organization">조직안내</a>
            <a href="#location">오시는 길</a>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <span class="badge">Pure & Technical Standard</span>
        <h1>신선함과 기술을 잇는 가치</h1>
        <p>체계적인 생산·유통 시스템과 끊임없는 경영 혁신으로<br>더 신뢰받는 미래를 만들어갑니다.</p>
    </section>

    <!-- Company Overview -->
    <main class="container" id="about">
        <div class="section-title">
            <h2>기업 개요</h2>
            <p>투명한 경영과 전문성을 바탕으로 성장하는 성화태크입니다.</p>
        </div>

        <div class="grid-3">
            <div class="card">
                <div class="icon-box">🏢</div>
                <h3>기업명</h3>
                <p><strong>(주)성화태크</strong>[cite: 1]<br>대표자: 안동혁[cite: 1]</p>
            </div>
            <div class="card">
                <div class="icon-box">🌱</div>
                <h3>설립 및 업력</h3>
                <p><strong>2024년 설립</strong> (업력 2년차)[cite: 1]<br>지속 가능한 가치 창출 도모</p>
            </div>
            <div class="card">
                <div class="icon-box">👥</div>
                <h3>임직원 현황</h3>
                <p><strong>총 13명</strong>의 분야별 전문 인력 보유[cite: 1]<br>탄탄한 부서별 협업 체계 구축</p>
            </div>
        </div>
    </main>

    <!-- Organization Section -->
    <section style="background-color: var(--secondary);" id="organization">
        <div class="container">
            <div class="section-title">
                <h2>조직 구성</h2>
                <p>각 분야의 전문 부서와 팀이 긴밀히 협력하고 있습니다.</p>
            </div>

            <div class="dept-list">
                <div class="dept-item core">영업·마케팅부[cite: 1]</div>
                <div class="dept-item core">기획·전략부[cite: 1]</div>
                <div class="dept-item core">생산·유통부[cite: 1]</div>
                <div class="dept-item">경영·지원부[cite: 1]</div>
                <div class="dept-item">복리후생지원부[cite: 1]</div>
                <div class="dept-item">감사팀[cite: 1]</div>
                <div class="dept-item">인사팀[cite: 1]</div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer id="location">
        <div class="footer-content">
            <div class="footer-brand">
                <h3>(주)성화태크</h3>
                <p>신선함과 기술이 조화를 이루는 기업</p>
            </div>
            <div class="footer-details">
                <p><strong>대표자:</strong> 안동혁[cite: 1] | <strong>사업자등록번호:</strong> 697-48-28200[cite: 1]</p>
                <p><strong>주소:</strong> 세종특별자치시 우윳군 추출면 신선목장길 69[cite: 1]</p>
            </div>
        </div>
        <div class="copyright">
            2026 SUNGHWA TECH CO., LTD. All rights reserved.[cite: 1]
        </div>
    </footer>

</body>
</html>
