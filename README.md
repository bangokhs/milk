<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>(주)성화태크 | SUNGHWA TECH</title>
    <link href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css" rel="stylesheet">
    
    <style>
        :root {
            --primary: #2B5B84;
            --secondary: #EBF4F6;
            --accent: #68A0A6;
            --text-main: #2C3E50;
            --text-sub: #667085;
            --bg-cream: #FDFBF7;
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

        header {
            position: sticky;
            top: 0;
            background: rgba(255, 255, 255, 0.95);
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

        nav {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        nav a {
            text-decoration: none;
            color: var(--text-main);
            font-weight: 500;
            font-size: 0.95rem;
        }

        .auth-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .btn-auth {
            background: var(--primary);
            color: #fff;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            font-weight: 600;
        }

        .user-info {
            font-size: 0.85rem;
            color: var(--primary);
            font-weight: bold;
        }

        .hero {
            padding: 80px 8% 60px;
            text-align: center;
            background: linear-gradient(180deg, #EBF4F6 0%, var(--bg-cream) 100%);
            border-radius: 0 0 40px 40px;
        }

        .hero h1 {
            font-size: 2.3rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 12px;
        }

        .hero p {
            color: var(--text-sub);
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 60px 20px;
        }

        .section-header {
            margin-bottom: 30px;
        }

        .section-header .sub-title {
            color: var(--accent);
            font-size: 0.85rem;
            font-weight: 700;
            letter-spacing: 1px;
        }

        .section-header h2 {
            font-size: 1.8rem;
            color: var(--primary);
            margin-top: 4px;
        }

        .section-header p {
            color: var(--text-sub);
            font-size: 0.95rem;
        }

        /* 기업 정보 Grid (이미지 디자인 반영) */
        .info-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            background: #ffffff;
            border-radius: 16px;
            border: 1px solid #e2e8f0;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0,0,0,0.02);
        }

        .info-item {
            padding: 24px;
            border-bottom: 1px solid #e2e8f0;
            border-right: 1px solid #e2e8f0;
            display: flex;
            align-items: flex-start;
            gap: 16px;
        }

        .info-item:nth-child(2n) {
            border-right: none;
        }

        .info-item:nth-last-child(-n+2) {
            border-bottom: none;
        }

        .info-icon {
            font-size: 1.4rem;
        }

        .info-content h4 {
            font-size: 0.95rem;
            color: var(--primary);
            margin-bottom: 4px;
        }

        .info-content p {
            font-size: 1.05rem;
            font-weight: 600;
            color: var(--text-main);
        }

        /* Login Notice Box */
        .notice-box {
            background: #fff;
            padding: 30px;
            border-radius: 16px;
            text-align: center;
            border: 2px dashed #CBD5E1;
            margin-bottom: 30px;
        }

        .notice-box p {
            color: var(--text-sub);
            font-size: 1rem;
            margin-bottom: 15px;
        }

        /* Form Card */
        .form-card {
            background: #fff;
            padding: 24px;
            border-radius: 16px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
            margin-bottom: 30px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            font-size: 0.9rem;
        }

        .form-group input, .form-group textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 8px;
        }

        .btn-submit {
            background: var(--accent);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
        }

        /* Product Grid */
        .grid-3 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 24px;
        }

        .card {
            background: #FFFFFF;
            padding: 24px;
            border-radius: 16px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.03);
            border: 1px solid #F0F0F0;
            position: relative;
        }

        .card-author {
            font-size: 0.8rem;
            color: var(--accent);
            font-weight: 600;
            margin-top: 10px;
            display: block;
        }

        .btn-delete {
            background: #e74c3c;
            color: white;
            border: none;
            padding: 6px 12px;
            border-radius: 6px;
            cursor: pointer;
            margin-top: 15px;
            font-size: 0.8rem;
        }

        footer {
            background: #24292E;
            color: #9AA0A6;
            padding: 40px 8%;
            font-size: 0.88rem;
            text-align: center;
        }

        @media (max-width: 768px) {
            .info-grid { grid-template-columns: 1fr; }
            .info-item { border-right: none; }
            .info-item:nth-last-child(2) { border-bottom: 1px solid #e2e8f0; }
        }
    </style>
</head>
<body>

    <header>
        <a href="#" class="logo">
            (주)성화태크 <span>SUNGHWA TECH</span>
        </a>
        <nav>
            <a href="#about">기업정보</a>
            <a href="#products">제품안내</a>
            <div class="auth-container">
                <span id="user-display" class="user-info"></span>
                <button id="auth-btn" class="btn-auth" onclick="toggleAuth()">Google 로그인</button>
            </div>
        </nav>
    </header>

    <section class="hero">
        <h1>신선함과 기술을 잇는 가치</h1>
        <p>투명하고 명확한 경영으로 신뢰받는 미래를 만들어갑니다.</p>
    </section>

    <!-- 이미지 정보 반영 섹션 -->
    <main class="container" id="about">
        <div class="section-header">
            <span class="sub-title">COMPANY INFORMATION</span>
            <h2>기업 정보</h2>
            <p>성화태크의 기본 정보를 투명하고 명확하게 안내합니다.</p>
        </div>

        <div class="info-grid">
            <div class="info-item">
                <div class="info-icon">💼</div>
                <div class="info-content">
                    <h4>기업명</h4>
                    <p>(주)성화태크</p>
                </div>
            </div>
            <div class="info-item">
                <div class="info-icon">👤</div>
                <div class="info-content">
                    <h4>대표자명</h4>
                    <p>성화택</p>
                </div>
            </div>
            <div class="info-item">
                <div class="info-icon">🥛</div>
                <div class="info-content">
                    <h4>사업 분야</h4>
                    <p>유제품 생산·유통 및 신선 배송</p>
                </div>
            </div>
            <div class="info-item">
                <div class="info-icon">📍</div>
                <div class="info-content">
                    <h4>사업자 주소</h4>
                    <p>세종특별자치시 우윳군 추출면 신선목장길 69</p>
                </div>
            </div>
            <div class="info-item">
                <div class="info-icon">📅</div>
                <div class="info-content">
                    <h4>설립일 / 업력</h4>
                    <p>2024년 / 2년</p>
                </div>
            </div>
            <div class="info-item">
                <div class="info-icon">👥</div>
                <div class="info-content">
                    <h4>임직원 수</h4>
                    <p>13명</p>
                </div>
            </div>
        </div>
    </main>

    <!-- 제품 및 작성 기능 섹션 -->
    <section style="background-color: var(--secondary);" id="products">
        <div class="container">
            <div class="section-header" style="text-align: center;">
                <h2>제품 안내</h2>
                <p>등록된 제품 목록을 확인하고 직접 등록해 보세요.</p>
            </div>

            <!-- 로그인 안 된 경우 노출 멘트 -->
            <div id="login-notice" class="notice-box">
                <p>🔒 <strong>제품을 추가하려면 구글 로그인이 필요합니다.</strong></p>
                <button class="btn-auth" onclick="toggleAuth()">Google 계정으로 로그인하기</button>
            </div>

            <!-- 로그인 성공 시 노출되는 등록 폼 -->
            <div id="product-form-container" class="form-card" style="display: none;">
                <h3>신규 제품 등록</h3>
                <form id="product-form" onsubmit="addProduct(event)">
                    <div class="form-group">
                        <label>제품명</label>
                        <input type="text" id="product-name" required placeholder="예: 신선한 성화 목장 우유">
                    </div>
                    <div class="form-group">
                        <label>가격 (원)</label>
                        <input type="number" id="product-price" required placeholder="3800">
                    </div>
                    <div class="form-group">
                        <label>설명</label>
                        <textarea id="product-desc" rows="3" required placeholder="제품에 대한 설명을 입력하세요."></textarea>
                    </div>
                    <button type="submit" class="btn-submit">제품 추가하기</button>
                </form>
            </div>

            <!-- 제품 리스트 영역 -->
            <div id="product-grid" class="grid-3"></div>
        </div>
    </section>

    <footer>
        <p><strong>(주)성화태크</strong> | 대표자: 성화택 | 사업자 주소: 세종특별자치시 우윳군 추출면 신선목장길 69</p>
        <p style="margin-top: 8px; font-size: 0.8rem;">© 2026 SUNGHWA TECH CO., LTD. All rights reserved.</p>
    </footer>

    <script>
        const ADMIN_EMAIL = "20240153@bangok.hs.kr";
        let currentUser = JSON.parse(localStorage.getItem('currentUser')) || null;

        // 초기화
        document.addEventListener('DOMContentLoaded', () => {
            updateAuthUI();
            loadProducts();
        });

        // 모의 로그인/로그아웃 처리 (구글 로그인이 브라우저에서 바로 동작하도록 설정)
        function toggleAuth() {
            if (currentUser) {
                currentUser = null;
                localStorage.removeItem('currentUser');
                alert("로그아웃 되었습니다.");
            } else {
                const email = prompt("구글 계정 이메일을 입력해 주세요:", "20240153@bangok.hs.kr");
                if (!email) return;
                
                const nickname = prompt("사용할 닉네임을 입력해 주세요:", email.split('@')[0]);
                if (!nickname) return;

                currentUser = { email: email, name: nickname };
                localStorage.setItem('currentUser', JSON.stringify(currentUser));
                alert(`${nickname}님 환영합니다! (Google 로그인 완료)`);
            }
            updateAuthUI();
            loadProducts();
        }

        // 로그인 상태에 따른 UI 변경
        function updateAuthUI() {
            const authBtn = document.getElementById('auth-btn');
            const userDisplay = document.getElementById('user-display');
            const noticeBox = document.getElementById('login-notice');
            const formContainer = document.getElementById('product-form-container');

            if (currentUser) {
                authBtn.innerText = "로그아웃";
                userDisplay.innerText = `👤 ${currentUser.name} (${currentUser.email})`;
                noticeBox.style.display = "none";
                formContainer.style.display = "block";
            } else {
                authBtn.innerText = "Google 로그인";
                userDisplay.innerText = "";
                noticeBox.style.display = "block";
                formContainer.style.display = "none";
            }
        }

        // 제품 등록
        function addProduct(e) {
            e.preventDefault();
            if (!currentUser) return;

            const name = document.getElementById('product-name').value;
            const price = document.getElementById('product-price').value;
            const desc = document.getElementById('product-desc').value;

            const products = JSON.parse(localStorage.getItem('products')) || [];
            
            const newProduct = {
                id: Date.now(),
                name: name,
                price: price,
                desc: desc,
                authorName: currentUser.name,
                authorEmail: currentUser.email
            };

            products.unshift(newProduct);
            localStorage.setItem('products', JSON.stringify(products));

            document.getElementById('product-form').reset();
            alert("제품이 등록되었습니다.");
            loadProducts();
        }

        // 제품 목록 출력
        function loadProducts() {
            const grid = document.getElementById('product-grid');
            grid.innerHTML = "";
            const products = JSON.parse(localStorage.getItem('products')) || [];

            if (products.length === 0) {
                grid.innerHTML = `<p style="grid-column: 1/-1; text-align: center; color: #888;">등록된 제품이 없습니다.</p>`;
                return;
            }

            products.forEach(p => {
                const card = document.createElement('div');
                card.className = 'card';

                let deleteBtn = '';
                if (currentUser && currentUser.email === ADMIN_EMAIL) {
                    deleteBtn = `<button class="btn-delete" onclick="deleteProduct(${p.id})">삭제 (관리자)</button>`;
                }

                card.innerHTML = `
                    <h3>${p.name}</h3>
                    <p style="color: var(--primary); font-weight: bold; margin: 4px 0;">${Number(p.price).toLocaleString()}원</p>
                    <p style="font-size: 0.9rem; color: #555;">${p.desc}</p>
                    <span class="card-author"> 작성자: ${p.authorName}</span>
                    ${deleteBtn}
                `;
                grid.appendChild(card);
            });
        }

        // 관리자 전용 삭제 기능
        function deleteProduct(id) {
            if (currentUser && currentUser.email === ADMIN_EMAIL) {
                if (confirm("정말 이 제품을 삭제하시겠습니까?")) {
                    let products = JSON.parse(localStorage.getItem('products')) || [];
                    products = products.filter(p => p.id !== id);
                    localStorage.setItem('products', JSON.stringify(products));
                    loadProducts();
                }
            }
        }
    </script>
</body>
</html>
