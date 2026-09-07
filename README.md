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

        /* Header Navigation */
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
            transition: color 0.2s ease;
        }

        nav a:hover {
            color: var(--primary);
        }

        /* Hero Section */
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

        /* 기업 정보 그리드 */
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

        /* 등록 폼 카드 */
        .form-card {
            background: #fff;
            padding: 28px;
            border-radius: 16px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.04);
            margin-bottom: 40px;
            border: 1px solid #E2E8F0;
        }

        .form-card h3 {
            font-size: 1.2rem;
            color: var(--primary);
            margin-bottom: 18px;
        }

        .form-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 16px;
        }

        .form-group {
            margin-bottom: 16px;
        }

        .form-group label {
            display: block;
            margin-bottom: 6px;
            font-weight: 600;
            font-size: 0.9rem;
            color: var(--text-main);
        }

        .form-group input, .form-group textarea {
            width: 100%;
            padding: 11px 14px;
            border: 1px solid #CBD5E1;
            border-radius: 8px;
            font-size: 0.95rem;
            outline: none;
            transition: border-color 0.2s;
        }

        .form-group input:focus, .form-group textarea:focus {
            border-color: var(--primary);
        }

        .btn-submit {
            background: var(--primary);
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            font-size: 0.95rem;
            transition: background 0.2s ease;
        }

        .btn-submit:hover {
            background: #1d4263;
        }

        /* 제품 카드 그리드 */
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
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .card-body h3 {
            font-size: 1.15rem;
            color: var(--primary);
        }

        .card-price {
            color: var(--accent);
            font-weight: 700;
            font-size: 1.1rem;
            margin: 6px 0;
        }

        .card-desc {
            font-size: 0.92rem;
            color: #555;
            margin-bottom: 12px;
        }

        .card-footer {
            border-top: 1px solid #F0F0F0;
            padding-top: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .card-author {
            font-size: 0.82rem;
            color: var(--text-sub);
            font-weight: 600;
        }

        .btn-delete {
            background: #EF4444;
            color: white;
            border: none;
            padding: 6px 12px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.8rem;
            font-weight: 600;
            transition: background 0.2s;
        }

        .btn-delete:hover {
            background: #DC2626;
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

    <!-- Header Navigation -->
    <header>
        <a href="#" class="logo">
            (주)성화태크 <span>SUNGHWA TECH</span>
        </a>
        <nav>
            <a href="#about">기업정보</a>
            <a href="#products">제품안내</a>
        </nav>
    </header>

    <!-- Hero Visual -->
    <section class="hero">
        <h1>신선함과 기술을 잇는 가치</h1>
        <p>투명하고 명확한 경영으로 신뢰받는 미래를 만들어갑니다.</p>
    </section>

    <!-- 기업 정보 세션 (이미지 레이아웃 준수) -->
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

    <!-- 제품 안내 및 직접 추가 영역 -->
    <section style="background-color: var(--secondary);" id="products">
        <div class="container">
            <div class="section-header" style="text-align: center;">
                <h2>제품 안내 및 직접 추가</h2>
                <p>누구나 자유롭게 신규 제품 정보를 등록할 수 있습니다.</p>
            </div>

            <!-- 신규 제품 등록 입력 폼 -->
            <div class="form-card">
                <h3>📝 제품 직접 등록하기</h3>
                <form id="product-form" onsubmit="addProduct(event)">
                    <div class="form-row">
                        <div class="form-group">
                            <label>등록자 이름 (닉네임)</label>
                            <input type="text" id="author-name" required placeholder="예: 홍길동">
                        </div>
                        <div class="form-group">
                            <label>제품명</label>
                            <input type="text" id="product-name" required placeholder="예: 신선한 성화 목장 우유">
                        </div>
                        <div class="form-group">
                            <label>가격 (원)</label>
                            <input type="number" id="product-price" required placeholder="3800">
                        </div>
                    </div>
                    <div class="form-group">
                        <label>제품 설명</label>
                        <textarea id="product-desc" rows="3" required placeholder="제품 특성 및 신선도 안내를 적어주세요."></textarea>
                    </div>
                    <button type="submit" class="btn-submit">제품 등록하기</button>
                </form>
            </div>

            <!-- 동적 제품 목록 -->
            <div id="product-grid" class="grid-3"></div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p><strong>(주)성화태크</strong> | 대표자: 성화택 | 사업자 주소: 세종특별자치시 우윳군 추출면 신선목장길 69</p>
        <p style="margin-top: 8px; font-size: 0.8rem;">© 2026 SUNGHWA TECH CO., LTD. All rights reserved.</p>
    </footer>

    <!-- 자바스크립트 로직 (Local Storage 및 관리자 삭제) -->
    <script>
        const ADMIN_CODE = "1133";

        document.addEventListener('DOMContentLoaded', () => {
            loadProducts();
        });

        // 제품 등록 함수
        function addProduct(e) {
            e.preventDefault();

            const authorName = document.getElementById('author-name').value.trim();
            const productName = document.getElementById('product-name').value.trim();
            const productPrice = document.getElementById('product-price').value.trim();
            const productDesc = document.getElementById('product-desc').value.trim();

            const products = JSON.parse(localStorage.getItem('products')) || [];

            const newProduct = {
                id: Date.now(),
                author: authorName,
                name: productName,
                price: productPrice,
                desc: productDesc
            };

            products.unshift(newProduct);
            localStorage.setItem('products', JSON.stringify(products));

            // 폼 초기화
            document.getElementById('product-form').reset();
            alert("제품이 정상적으로 등록되었습니다!");
            loadProducts();
        }

        // 제품 불러오기 함수
        function loadProducts() {
            const grid = document.getElementById('product-grid');
            grid.innerHTML = "";
            const products = JSON.parse(localStorage.getItem('products')) || [];

            if (products.length === 0) {
                grid.innerHTML = `<p style="grid-column: 1/-1; text-align: center; color: #888; padding: 40px 0;">등록된 제품이 없습니다. 위 폼에서 직접 등록해보세요!</p>`;
                return;
            }

            products.forEach(p => {
                const card = document.createElement('div');
                card.className = 'card';

                card.innerHTML = `
                    <div class="card-body">
                        <h3>${p.name}</h3>
                        <p class="card-price">${Number(p.price).toLocaleString()}원</p>
                        <p class="card-desc">${p.desc}</p>
                    </div>
                    <div class="card-footer">
                        <span class="card-author">✍️ 등록자: ${p.author}</span>
                        <button class="btn-delete" onclick="deleteProduct(${p.id})">삭제</button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        // 삭제 처리 함수 (관리자 코드 확인)
        function deleteProduct(id) {
            const inputCode = prompt("제품을 삭제하려면 관리자 코드를 입력하세요:");
            
            if (inputCode === null) return; // 취소 클릭시 아무 작업 안 함

            if (inputCode === ADMIN_CODE) {
                let products = JSON.parse(localStorage.getItem('products')) || [];
                products = products.filter(p => p.id !== id);
                localStorage.setItem('products', JSON.stringify(products));
                alert("성공적으로 삭제되었습니다.");
                loadProducts();
            } else {
                alert("관리자 코드가 일치하지 않습니다.");
            }
        }
    </script>
</body>
</html>
