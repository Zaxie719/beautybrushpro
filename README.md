<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WoolBloom | 专业羊毛化妆刷</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* ====== 核心设计变量 (修改这里可快速改变整体画风) ====== */
        :root {
            --primary-color: #FFB6C1; /* 主色调：暖粉色 */
            --secondary-color: #9370DB; /* 辅助色：中紫色 */
            --dark-color: #2A2D43; /* 深色：用于文字和导航 */
            --light-color: #FFF9FB; /* 浅色：背景 */
            --accent-color: #FFD166; /* 点缀色：金黄色 */
            --text-color: #333;
            --text-light: #777;
            --shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            --radius: 12px;
            --transition: all 0.3s ease;
        }

        /* ====== 基础样式重置 ====== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        html {
            scroll-behavior: smooth;
        }
        body {
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background-color: var(--light-color);
        }
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* ====== 顶部栏 (含语言切换) ====== */
        .top-bar {
            background-color: var(--dark-color);
            color: white;
            padding: 8px 0;
            font-size: 0.9rem;
        }
        .top-bar .container {
            display: flex;
            justify-content: flex-end;
            align-items: center;
        }
        .language-switcher {
            display: flex;
            gap: 10px;
        }
        .lang-btn {
            background: transparent;
            border: 1px solid rgba(255,255,255,0.3);
            color: white;
            padding: 4px 12px;
            border-radius: 4px;
            cursor: pointer;
            transition: var(--transition);
            font-size: 0.85rem;
        }
        .lang-btn:hover,
        .lang-btn.active {
            background-color: var(--primary-color);
            border-color: var(--primary-color);
        }

        /* ====== 主导航栏 ====== */
        .main-nav {
            background-color: white;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 18px 0;
        }
        .logo {
            display: flex;
            align-items: center;
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--dark-color);
            text-decoration: none;
        }
        .logo i {
            color: var(--primary-color);
            margin-right: 10px;
        }
        .nav-links {
            display: flex;
            list-style: none;
            gap: 35px;
        }
        .nav-links a {
            text-decoration: none;
            color: var(--dark-color);
            font-weight: 600;
            font-size: 1.05rem;
            padding: 8px 0;
            position: relative;
            transition: var(--transition);
        }
        .nav-links a:hover,
        .nav-links a.active {
            color: var(--primary-color);
        }
        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary-color);
            transition: width 0.3s ease;
        }
        .nav-links a:hover::after,
        .nav-links a.active::after {
            width: 100%;
        }
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--dark-color);
            cursor: pointer;
        }

        /* ====== 英雄大图区域 ====== */
        .hero {
            padding: 100px 0;
            background: linear-gradient(rgba(255, 182, 193, 0.1), rgba(147, 112, 219, 0.05)), url('https://images.unsplash.com/photo-1596462502278-27bfdc403348?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80');
            background-size: cover;
            background-position: center;
            text-align: center;
            color: var(--dark-color);
        }
        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 20px;
            color: var(--dark-color);
        }
        .hero p {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 40px;
            color: var(--text-light);
        }
        .cta-button {
            display: inline-block;
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 16px 40px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1.1rem;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }
        .cta-button:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(255, 182, 193, 0.4);
        }

        /* ====== 产品分类导航 ====== */
        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin: 80px 0 40px;
            color: var(--dark-color);
            position: relative;
        }
        .section-title::after {
            content: '';
            display: block;
            width: 80px;
            height: 4px;
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            margin: 15px auto;
            border-radius: 2px;
        }
        .category-filter {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 50px;
        }
        .filter-btn {
            padding: 12px 28px;
            background-color: white;
            border: 2px solid #eee;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            color: var(--text-light);
            transition: var(--transition);
        }
        .filter-btn:hover,
        .filter-btn.active {
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            border-color: transparent;
        }

        /* ====== 产品网格 ====== */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 35px;
            margin-bottom: 80px;
        }
        .product-card {
            background: white;
            border-radius: var(--radius);
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }
        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.12);
        }
        .product-img {
            height: 220px;
            background-color: #f5f5f5;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3.5rem;
            color: var(--primary-color);
        }
        .product-info {
            padding: 25px;
        }
        .product-category {
            display: inline-block;
            background-color: rgba(255, 182, 193, 0.15);
            color: var(--primary-color);
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
            margin-bottom: 10px;
        }
        .product-info h3 {
            font-size: 1.4rem;
            margin-bottom: 10px;
            color: var(--dark-color);
        }
        .product-desc {
            color: var(--text-light);
            font-size: 0.95rem;
            margin-bottom: 20px;
            min-height: 60px;
        }
        .product-price {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--secondary-color);
            margin-bottom: 20px;
        }
        .add-to-cart {
            width: 100%;
            padding: 14px;
            background-color: var(--dark-color);
            color: white;
            border: none;
            border-radius: var(--radius);
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
        }
        .add-to-cart:hover {
            background-color: var(--secondary-color);
        }

        /* ====== 联系/关于区域 ====== */
        .contact-section {
            background-color: white;
            padding: 80px 0;
            border-top: 1px solid #eee;
        }
        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 50px;
            align-items: center;
        }
        .contact-info h3 {
            font-size: 2rem;
            margin-bottom: 20px;
            color: var(--dark-color);
        }
        .contact-detail {
            display: flex;
            align-items: center;
            margin-bottom: 25px;
        }
        .contact-detail i {
            width: 50px;
            height: 50px;
            background-color: rgba(255, 182, 193, 0.1);
            color: var(--primary-color);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            margin-right: 20px;
        }

        /* ====== 页脚 ====== */
        .footer {
            background-color: var(--dark-color);
            color: white;
            padding: 60px 0 30px;
        }
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }
        .footer-logo {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 20px;
        }
        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }
        .social-links a {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: rgba(255,255,255,0.1);
            border-radius: 50%;
            color: white;
            transition: var(--transition);
        }
        .social-links a:hover {
            background-color: var(--primary-color);
            transform: translateY(-3px);
        }
        .footer-bottom {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255,255,255,0.1);
            font-size: 0.9rem;
            color: rgba(255,255,255,0.7);
        }

        /* ====== 响应式设计 (适配平板和手机) ====== */
        @media (max-width: 992px) {
            .hero h1 { font-size: 2.8rem; }
            .section-title { font-size: 2.2rem; }
        }
        @media (max-width: 768px) {
            .mobile-menu-btn { display: block; }
            .nav-links {
                position: fixed;
                top: 80px;
                left: -100%;
                width: 100%;
                background: white;
                flex-direction: column;
                align-items: center;
                padding: 30px 0;
                box-shadow: 0 10px 20px rgba(0,0,0,0.1);
                transition: left 0.3s ease;
            }
            .nav-links.active { left: 0; }
            .hero h1 { font-size: 2.3rem; }
            .hero p { font-size: 1rem; }
            .contact-grid { grid-template-columns: 1fr; }
        }
        @media (max-width: 576px) {
            .hero { padding: 70px 0; }
            .category-filter { gap: 10px; }
            .filter-btn { padding: 10px 20px; font-size: 0.9rem; }
            .section-title { font-size: 1.9rem; margin: 60px 0 30px; }
        }
    </style>
</head>
<body>
    <!-- 顶部语言切换栏 -->
    <div class="top-bar">
        <div class="container">
            <div class="language-switcher">
                <button class="lang-btn active" data-lang="zh">中文</button>
                <button class="lang-btn" data-lang="en">English</button>
            </div>
        </div>
    </div>

    <!-- 主导航栏 -->
    <nav class="main-nav">
        <div class="container nav-container">
            <a href="#home" class="logo">
                <i class="fas fa-feather-alt"></i>
                WoolBloom
            </a>
            <button class="mobile-menu-btn" id="mobileMenuBtn">
                <i class="fas fa-bars"></i>
            </button>
            <ul class="nav-links" id="navLinks">
                <li><a href="#home" class="active">主页</a></li>
                <li><a href="#products">产品</a></li>
                <li><a href="#contact">联系</a></li>
            </ul>
        </div>
    </nav>

    <!-- 首页英雄区域 -->
    <section class="hero" id="home">
        <div class="container">
            <h1>温柔触感，源自天然</h1>
            <p>WoolBloom 精选全球优质羊毛，由匠人手工打造每一支专业化妆刷。为美妆爱好者与化妆师提供无可比拟的上妆体验。</p>
            <a href="#products" class="cta-button">探索我们的刷具</a>
        </div>
    </section>

    <!-- 产品展示区 -->
    <section class="container">
        <h2 class="section-title" id="products">精选产品</h2>
        <div class="category-filter">
            <button class="filter-btn active" data-filter="all">全部产品</button>
            <button class="filter-btn" data-filter="face">面部刷</button>
            <button class="filter-btn" data-filter="eye">眼部刷</button>
            <button class="filter-btn" data-filter="cheek">腮红/高光刷</button>
            <button class="filter-btn" data-filter="set">套装</button>
        </div>

        <div class="products-grid" id="productsContainer">
            <!-- 产品卡片将通过JavaScript动态生成 -->
        </div>
    </section>

    <!-- 联系信息区 -->
    <section class="contact-section" id="contact">
        <div class="container">
            <h2 class="section-title">联系我们</h2>
            <div class="contact-grid">
                <div class="contact-info">
                    <h3>获取专业咨询</h3>
                    <div class="contact-detail">
                        <i class="fas fa-map-marker-alt"></i>
                        <div>
                            <h4>地址</h4>
                            <p>中国上海市浦东新区创意园区123号</p>
                        </div>
                    </div>
                    <div class="contact-detail">
                        <i class="fas fa-phone"></i>
                        <div>
                            <h4>电话</h4>
                            <p>+86 400-888-9999</p>
                        </div>
                    </div>
                    <div class="contact-detail">
                        <i class="fas fa-envelope"></i>
                        <div>
                            <h4>邮箱</h4>
                            <p>contact@woolbloom.com</p>
                        </div>
                    </div>
                </div>
                <div class="map-placeholder">
                    <!-- 这里可以未来嵌入地图，例如百度地图或Google Maps -->
                    <div style="background: #f0f0f0; height: 300px; border-radius: var(--radius); display: flex; align-items: center; justify-content: center; color: var(--text-light);">
                        <div style="text-align: center;">
                            <i class="fas fa-map" style="font-size: 3rem; margin-bottom: 15px; color: #ccc;"></i>
                            <p>地图位置展示</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 页脚 -->
    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <div>
                    <div class="footer-logo">
                        <i class="fas fa-feather-alt"></i> WoolBloom
                    </div>
                    <p>天然羊毛，专业妆效。致力于为全球美妆人士提供高品质的化妆工具。</p>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-weixin"></i></a>
                        <a href="#"><i class="fab fa-weibo"></i></a>
                        <a href="#"><i class="fab fa-xiaohongshu"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                    </div>
                </div>
                <div>
                    <h4>快速链接</h4>
                    <ul style="list-style: none; padding: 0;">
                        <li style="margin-bottom: 10px;"><a href="#home" style="color: rgba(255,255,255,0.8); text-decoration: none;">主页</a></li>
                        <li style="margin-bottom: 10px;"><a href="#products" style="color: rgba(255,255,255,0.8); text-decoration: none;">产品</a></li>
                        <li style="margin-bottom: 10px;"><a href="#contact" style="color: rgba(255,255,255,0.8); text-decoration: none;">联系</a></li>
                    </ul>
                </div>
                <div>
                    <h4>服务支持</h4>
                    <p style="color: rgba(255,255,255,0.8);">周一至周五 9:00-18:00</p>
                    <p style="color: rgba(255,255,255,0.8);">专业客服团队，为您解答产品与采购疑问。</p>
                </div>
            </div>
            <div class="footer-bottom">
                <p>&copy; 2024 WoolBloom. 保留所有权利。 | 专业羊毛化妆刷制造商</p>
            </div>
        </div>
    </footer>

    <script>
        // ====== 网站核心交互逻辑 ======
        document.addEventListener('DOMContentLoaded', function() {
            // 1. 移动端菜单切换
            const mobileMenuBtn = document.getElementById('mobileMenuBtn');
            const navLinks = document.getElementById('navLinks');
            mobileMenuBtn.addEventListener('click', () => {
                navLinks.classList.toggle('active');
                mobileMenuBtn.innerHTML = navLinks.classList.contains('active')
                    ? '<i class="fas fa-times"></i>'
                    : '<i class="fas fa-bars"></i>';
            });

            // 点击导航链接后关闭移动菜单
            document.querySelectorAll('.nav-links a').forEach(link => {
                link.addEventListener('click', () => {
                    navLinks.classList.remove('active');
                    mobileMenuBtn.innerHTML = '<i class="fas fa-bars"></i>';
                });
            });

            // 2. 产品数据与动态生成
            const products = [
                {id:1, name: "专业散粉刷", category: "face", desc: "细光锋羊毛，触感柔软如云，适合全脸轻薄定妆。", price: "¥428", icon: "fas fa-sun"},
                {id:2, name: "斜角修容刷", category: "face", desc: "山羊毛，精准贴合面部轮廓，打造自然立体感。", price: "¥298", icon: "fas fa-mountain"},
                {id:3, name: "圆头腮红刷", category: "cheek", desc: "柔软羊毛，轻松打造自然红晕，避免色块。", price: "¥268", icon: "fas fa-circle"},
                {id:4, name: "基础眼影套刷", category: "eye", desc: "三支套装，含铺色刷、晕染刷与细节刷。", price: "¥388", icon: "fas fa-eye"},
                {id:5, name: "精准高光刷", category: "cheek", desc: "小马毛，精准捕捉光线，点亮颧骨与眉骨。", price: "¥238", icon: "fas fa-sparkles"},
                {id:6, name: "大师全套装", category: "set", desc: "12支全系列刷具，满足从底妆到眼妆的所有需求。", price: "¥1,288", icon: "fas fa-gem"}
            ];

            const productsContainer = document.getElementById('productsContainer');
            function renderProducts(filter = 'all') {
                productsContainer.innerHTML = '';
                const filteredProducts = filter === 'all' ? products : products.filter(p => p.category === filter);
                filteredProducts.forEach(product => {
                    const card = document.createElement('div');
                    card.className = 'product-card';
                    card.innerHTML = `
                        <div class="product-img">
                            <i class="${product.icon}"></i>
                        </div>
                        <div class="product-info">
                            <span class="product-category">${getCategoryName(product.category)}</span>
                            <h3>${product.name}</h3>
                            <p class="product-desc">${product.desc}</p>
                            <div class="product-price">${product.price}</div>
                            <button class="add-to-cart" onclick="addToCart(${product.id})">
                                <i class="fas fa-cart-plus"></i> 加入购物车
                            </button>
                        </div>
                    `;
                    productsContainer.appendChild(card);
                });
            }

            function getCategoryName(category) {
                const names = {face:'面部刷', eye:'眼部刷', cheek:'腮红/高光刷', set:'套装'};
                return names[category] || '其他';
            }

            // 3. 产品分类筛选
            document.querySelectorAll('.filter-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    const filter = this.getAttribute('data-filter');
                    renderProducts(filter);
                });
            });

            // 4. 多语言切换 (示例功能)
            document.querySelectorAll('.lang-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    document.querySelectorAll('.lang-btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    const lang = this.getAttribute('data-lang');
                    alert(`示例：已切换到 ${lang === 'zh' ? '中文' : 'English'} 模式。实际开发中，这里将替换页面上的所有文本。`);
                });
            });

            // 5. 导航栏激活状态
            function updateActiveNav() {
                const sections = document.querySelectorAll('section');
                const navLinks = document.querySelectorAll('.nav-links a');
                let current = '';
                sections.forEach(section => {
                    const sectionTop = section.offsetTop;
                    const sectionHeight = section.clientHeight;
                    if (scrollY >= (sectionTop - 100)) {
                        current = section.getAttribute('id');
                    }
                });
                navLinks.forEach(link => {
                    link.classList.remove('active');
                    if (link.getAttribute('href') === `#${current}`) {
                        link.classList.add('active');
                    }
                });
            }
            window.addEventListener('scroll', updateActiveNav);

            // 初始渲染全部产品
            renderProducts();
        });

        // 示例：添加到购物车函数
        function addToCart(productId) {
            alert(`产品 ${productId} 已添加到购物车！`);
            console.log(`Added product ${productId} to cart.`);
        }
    </script>
</body>
</html>
