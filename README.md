<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>(주)성화태크 | SUNGHWA TECH</title>
    <link href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css" rel="stylesheet">
    
    <!-- Firebase SDK (v9, 모듈/자바스크립트 지원) -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
        import { getAuth, GoogleAuthProvider, signInWithPopup, signOut, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js";
        import { getFirestore, collection, addDoc, getDocs, deleteDoc, doc, serverTimestamp, query, orderBy } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-firestore.js";

        // Firebase 설정 (본인의 Firebase 프로젝트 설정 값으로 교체해주셔야 작동합니다)
        const firebaseConfig = {
            apiKey: "YOUR_API_KEY",
            authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
            projectId: "YOUR_PROJECT_ID",
            storageBucket: "YOUR_PROJECT_ID.appspot.com",
            messagingSenderId: "YOUR_SENDER_ID",
            appId: "YOUR_APP_ID"
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const db = getFirestore(app);
        const provider = new GoogleAuthProvider();

        const ADMIN_EMAIL = "20240153@bangok.hs.kr";
        let currentUser = null;

        // Auth 상태 감지
        onAuthStateChanged(auth, (user) => {
            currentUser = user;
            const authBtn = document.getElementById('auth-btn');
            const userDisplay = document.getElementById('user-display');
            const productFormContainer = document.getElementById('product-form-container');

            if (user) {
                authBtn.innerText = "로그아웃";
                userDisplay.innerText = `${user.displayName} (${user.email})`;
                productFormContainer.style.display = "block"; // 로그인 시 등록 폼 노출
            } else {
                authBtn.innerText = "Google 로그인";
                userDisplay.innerText = "";
                productFormContainer.style.display = "none";
            }
            loadProducts();
        });

        // Google 로그인 / 로그아웃
        window.toggleAuth = () => {
            if (currentUser) {
                signOut(auth).then(() => alert("로그아웃 되었습니다."));
            } else {
                signInWithPopup(auth, provider).catch((error) => console.error(error));
            }
        };

        // 제품 등록
        window.addProduct = async (e) => {
            e.preventDefault();
            if (!currentUser) {
                alert("로그인이 필요합니다.");
                return;
            }

            const name = document.getElementById('product-name').value;
            const desc = document.getElementById('product-desc').value;
            const price = document.getElementById('product-price').value;

            try {
                await addDoc(collection(db, "products"), {
                    name: name,
                    description: desc,
                    price: price,
                    createdAt: serverTimestamp(),
                    userEmail: currentUser.email
                });
                alert("제품이 등록되었습니다.");
                document.getElementById('product-form').reset();
                loadProducts();
            } catch (error) {
                console.error("제품 등록 오류:", error);
            }
        };

        // 제품 목록 불러오기
        async function loadProducts() {
            const grid = document.getElementById('product-grid');
            grid.innerHTML = "";

            try {
                const q = query(collection(db, "products"), orderBy("createdAt", "desc"));
                const querySnapshot = await getDocs(q);

                querySnapshot.forEach((docSnap) => {
                    const data = docSnap.data();
                    const card = document.createElement('div');
                    card.className = 'card';
                    
                    let deleteBtn = '';
                    if (currentUser && currentUser.email === ADMIN_EMAIL) {
                        deleteBtn = `<button class="btn-delete" onclick="deleteProduct('${docSnap.id}')">삭제 (관리자)</button>`;
                    }

                    card.innerHTML = `
                        <div class="icon-box">🥛</div>
                        <h3>${data.name}</h3>
                        <p><strong>가격:</strong> ${data.price}원</p>
                        <p>${data.description}</p>
                        ${deleteBtn}
                    `;
                    grid.appendChild(card);
                });
            } catch (error) {
                console.error("목록 불러오기 오류:", error);
            }
        }

        // 제품 삭제 (관리자 전용)
        window.deleteProduct = async (id) => {
            if (currentUser && currentUser.email === ADMIN_EMAIL) {
                if (confirm("정말 이 제품을 삭제하시겠습니까?")) {
                    await deleteDoc(doc(db, "products", id));
                    alert("삭제되었습니다.");
                    loadProducts();
                }
            } else {
                alert("관리자 권한이 없습니다.");
            }
        };
    </script>

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
            color: var(--text-sub);
        }

        /* Hero Section */
        .hero {
            padding: 100px 8% 80px;
            text-align: center;
            background: linear-gradient(180deg, #EBF4F6 0%, var(--bg-cream) 100%);
            border-radius: 0 0 40px 40px;
        }

        .hero h1 {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 16px;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 60px 20px;
        }

        .section-title {
            text-align: center;
            margin-bottom: 40px;
        }

        .section-title h2 {
            font-size: 1.8rem;
            color: var(--primary);
        }

        /* Forms */
        .form-card {
            background: #fff;
            padding: 24px;
            border-radius: 16px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
            margin-bottom: 40px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
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

        /* Cards & Grid */
        .grid-3 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 24px;
        }

        .card {
            background: #FFFFFF;
            padding: 30px 24px;
            border-radius: 20px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.03);
            border: 1px solid #F0F0F0;
            position: relative;
        }

        .icon-box {
            font-size: 2rem;
            margin-bottom: 10px;
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

        /* Footer */
        footer {
            background: #24292E;
            color: #9AA0A6;
            padding: 40px 8%;
            font-size: 0.88rem;
            text-align: center;
        }
    </style>
</head>
<body>

    <header>
        <a href="#" class="logo">
            (주)성화태크 <span>SUNGHWA TECH</span>
        </a>
        <nav>
            <a href="#about">기업소개</a>
            <a href="#products">제품안내</a>
            <div class="auth-container">
                <span id="user-display" class="user-info"></span>
                <button id="auth-btn" class="btn-auth" onclick="toggleAuth()">Google 로그인</button>
            </div>
        </nav>
    </header>

    <section class="hero">
        <h1>신선함과 기술을 잇는 가치</h1>
        <p>체계적인 생산·유통 시스템으로 더 신뢰받는 미래를 만들어갑니다.</p>
    </section>

    <!-- 기업 소개 -->
    <main class="container" id="about">
        <div class="section-title">
            <h2>기업 개요</h2>
        </div>
        <div class="grid-3">
            <div class="card">
                <h3>기업명</h3>
                <p><strong>(주)성화태크</strong><br>대표자: 안동혁</p>
            </div>
            <div class="card">
                <h3>설립 및 업력</h3>
                <p><strong>2024년 설립</strong> (업력 2년차)</p>
            </div>
            <div class="card">
                <h3>임직원 현황</h3>
                <p><strong>총 13명</strong>의 전문 인력 보유</p>
            </div>
        </div>
    </main>

    <!-- 제품 목록 및 등록 영역 -->
    <section style="background-color: var(--secondary);" id="products">
        <div class="container">
            <div class="section-title">
                <h2>제품 안내</h2>
                <p>방문자 등록 제품 및 대표 우유 유통 라인업</p>
            </div>

            <!-- 로그인 사용자 전용 등록 폼 -->
            <div id="product-form-container" class="form-card" style="display: none;">
                <h3>신규 제품 직접 등록하기</h3>
                <form id="product-form" onsubmit="addProduct(event)">
                    <div class="form-group">
                        <label>제품명</label>
                        <input type="text" id="product-name" required placeholder="예: 신선한 성화 유기농 우유">
                    </div>
                    <div class="form-group">
                        <label>가격 (원)</label>
                        <input type="number" id="product-price" required placeholder="3500">
                    </div>
                    <div class="form-group">
                        <label>설명</label>
                        <textarea id="product-desc" rows="3" required placeholder="제품에 대한 설명을 입력해 주세요."></textarea>
                    </div>
                    <button type="submit" class="btn-submit">제품 등록하기</button>
                </form>
            </div>

            <!-- 동적 제품 목록 카드 출력 영역 -->
            <div id="product-grid" class="grid-3">
                <!-- 자바스크립트에 의해 제품 카드가 불러와집니다 -->
            </div>
        </div>
    </section>

    <footer>
        <p><strong>(주)성화태크</strong> | 대표자: 안동혁 | 사업자등록번호: 697-48-28200</p>
        <p>주소: 세종특별자치시 우윳군 추출면 신선목장길 69</p>
        <p style="margin-top: 10px; font-size: 0.8rem;">© 2026 SUNGHWA TECH CO., LTD. All rights reserved.</p>
    </footer>

</body>
</html>
