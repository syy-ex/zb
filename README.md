<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>朱振博的鹿世界</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a2f1a 0%, #3d2c1d 100%);
            color: #f0e6d2;
            overflow-x: hidden;
            background-attachment: fixed;
        }
        
        .deer-pattern {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100"><path d="M50,20 C60,10 80,10 90,20 C100,30 100,50 90,60 C80,70 60,70 50,60 C40,70 20,70 10,60 C0,50 0,30 10,20 C20,10 40,10 50,20 Z" fill="none" stroke="%233a5a40" stroke-width="0.5" opacity="0.2"/></svg>');
            z-index: -1;
            opacity: 0.3;
        }
        
        .deer-running {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        
        .running-deer {
            position: absolute;
            width: 40px;
            height: 40px;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><path d="M40,30 Q45,20 50,25 Q55,20 60,30 Q70,25 75,35 Q85,40 80,50 Q85,60 75,65 Q70,75 60,70 Q55,80 50,75 Q45,80 40,70 Q30,75 25,65 Q15,60 20,50 Q15,40 25,35 Q30,25 40,30 Z" fill="%23d4b483"/><circle cx="35" cy="35" r="5" fill="%23333"/><circle cx="65" cy="35" r="5" fill="%23333"/><path d="M45,45 Q50,50 55,45" stroke="%23333" stroke-width="2" fill="none"/><path d="M30,60 Q40,65 50,60 Q60,65 70,60" stroke="%23d4b483" stroke-width="4" fill="none"/></svg>');
            background-size: contain;
            opacity: 0.7;
            animation: run linear infinite;
        }
        
        @keyframes run {
            0% { transform: translateX(-50px); }
            100% { transform: translateX(calc(100vw + 50px)); }
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .header-content {
            position: relative;
            z-index: 10;
        }
        
        .deer-antlers {
            position: absolute;
            top: -50px;
            width: 300px;
            height: 200px;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 100"><path d="M100,10 Q120,0 140,20 Q160,40 170,60 Q180,80 160,90 Q140,100 120,80 Q100,60 80,80 Q60,100 40,90 Q20,80 30,60 Q40,40 60,20 Q80,0 100,10 Z" fill="%23d4b483" opacity="0.7"/></svg>');
            background-repeat: no-repeat;
            background-position: center;
            opacity: 0.8;
        }
        
        h1 {
            font-size: 5rem;
            margin-bottom: 20px;
            text-shadow: 0 0 10px rgba(212, 180, 131, 0.8);
            color: #f0e6d2;
        }
        
        .subtitle {
            font-size: 1.8rem;
            margin-bottom: 30px;
            color: #d4b483;
        }
        
        .scroll-down {
            position: absolute;
            bottom: 40px;
            left: 50%;
            transform: translateX(-50%);
            animation: bounce 2s infinite;
            color: #d4b483;
            font-size: 2rem;
        }
        
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {transform: translateY(0) translateX(-50%);}
            40% {transform: translateY(-20px) translateX(-50%);}
            60% {transform: translateY(-10px) translateX(-50%);}
        }
        
        section {
            min-height: 100vh;
            padding: 80px 20px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            position: relative;
            border-bottom: 1px solid rgba(212, 180, 131, 0.3);
        }
        
        .section-title {
            font-size: 3rem;
            margin-bottom: 50px;
            text-align: center;
            color: #d4b483;
            position: relative;
        }
        
        .section-title::after {
            content: "";
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(to right, transparent, #d4b483, transparent);
        }
        
        .about-content {
            display: flex;
            gap: 40px;
            align-items: center;
        }
        
        .deer-icon {
            flex: 1;
            text-align: center;
        }
        
        .deer-icon i {
            font-size: 10rem;
            color: #d4b483;
            animation: pulse 3s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        .about-text {
            flex: 2;
            font-size: 1.2rem;
            line-height: 1.8;
            background: rgba(58, 90, 64, 0.5);
            padding: 30px;
            border-radius: 15px;
            border: 1px solid #d4b483;
        }
        
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .gallery-item {
            height: 250px;
            background: rgba(212, 180, 131, 0.1);
            border-radius: 10px;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
            border: 1px solid rgba(212, 180, 131, 0.3);
            transition: transform 0.3s;
        }
        
        .gallery-item:hover {
            transform: translateY(-10px);
        }
        
        .gallery-item::before {
            content: "🦌";
            font-size: 8rem;
            opacity: 0.3;
        }
        
        .deer-facts {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .fact-card {
            background: rgba(58, 90, 64, 0.5);
            padding: 25px;
            border-radius: 15px;
            border: 1px solid #d4b483;
            transition: transform 0.3s;
        }
        
        .fact-card:hover {
            transform: scale(1.03);
            background: rgba(58, 90, 64, 0.7);
        }
        
        .fact-card h3 {
            color: #d4b483;
            margin-bottom: 15px;
            font-size: 1.5rem;
        }
        
        .fact-card i {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: #d4b483;
        }
        
        .contact-form {
            max-width: 600px;
            margin: 0 auto;
            background: rgba(58, 90, 64, 0.5);
            padding: 40px;
            border-radius: 15px;
            border: 1px solid #d4b483;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: #d4b483;
        }
        
        .form-group input, 
        .form-group textarea {
            width: 100%;
            padding: 12px;
            background: rgba(240, 230, 210, 0.1);
            border: 1px solid #d4b483;
            border-radius: 5px;
            color: #f0e6d2;
            font-size: 1rem;
        }
        
        .form-group textarea {
            height: 150px;
            resize: vertical;
        }
        
        button {
            background: #d4b483;
            color: #1a2f1a;
            border: none;
            padding: 12px 30px;
            font-size: 1.1rem;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
            font-weight: bold;
            display: block;
            margin: 0 auto;
        }
        
        button:hover {
            background: #c0a06a;
        }
        
        footer {
            text-align: center;
            padding: 40px 20px;
            color: #d4b483;
            background: rgba(26, 47, 26, 0.8);
            border-top: 1px solid rgba(212, 180, 131, 0.3);
        }
        
        .social-icons {
            margin: 20px 0;
        }
        
        .social-icons a {
            display: inline-block;
            margin: 0 15px;
            color: #d4b483;
            font-size: 1.8rem;
            transition: transform 0.3s;
        }
        
        .social-icons a:hover {
            transform: translateY(-5px);
        }
        
        @media (max-width: 768px) {
            .about-content {
                flex-direction: column;
            }
            
            h1 {
                font-size: 3.5rem;
            }
            
            .subtitle {
                font-size: 1.4rem;
            }
            
            .section-title {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <!-- 背景元素 -->
    <div class="deer-pattern"></div>
    <div class="deer-running" id="deerRunning"></div>
    
    <div class="container">
        <!-- 头部区域 -->
        <header>
            <div class="deer-antlers"></div>
            <div class="header-content">
                <h1>朱振博</h1>
                <div class="subtitle">鹿的爱好者与守护者</div>
                <p>探索鹿的优雅世界，感受自然的和谐之美</p>
            </div>
            <div class="scroll-down">
                <i class="fas fa-chevron-down"></i>
            </div>
        </header>
        
        <!-- 关于我 -->
        <section id="about">
            <h2 class="section-title">关于我</h2>
            <div class="about-content">
                <div class="deer-icon">
                    <i class="fas fa-deer"></i>
                </div>
                <div class="about-text">
                    <p>你好，我是朱振博，一个深深热爱鹿的自然爱好者。鹿对我来说不仅仅是动物，它们是优雅、自由和自然和谐的象征。</p>
                    <p>从小我就被鹿的优雅姿态和温柔眼神所吸引。每当我走进森林，看到鹿群在晨曦中漫步，内心就会充满平静与喜悦。</p>
                    <p>通过这个网站，我想与你分享我对鹿的热爱，展示这些美丽生灵的迷人之处，以及我们如何更好地保护它们和它们的栖息地。</p>
                </div>
            </div>
        </section>
        
        <!-- 鹿的相册 -->
        <section id="gallery">
            <h2 class="section-title">鹿的优雅瞬间</h2>
            <div class="gallery">
                <div class="gallery-item"></div>
                <div class="gallery-item"></div>
                <div class="gallery-item"></div>
                <div class="gallery-item"></div>
                <div class="gallery-item"></div>
                <div class="gallery-item"></div>
            </div>
        </section>
        
        <!-- 鹿的知识 -->
        <section id="facts">
            <h2 class="section-title">鹿的奇妙世界</h2>
            <div class="deer-facts">
                <div class="fact-card">
                    <i class="fas fa-running"></i>
                    <h3>优雅的奔跑者</h3>
                    <p>鹿的最高奔跑速度可达60公里/小时，并且能够跳过2.5米高的障碍物。它们强健的后腿提供了惊人的爆发力。</p>
                </div>
                <div class="fact-card">
                    <i class="fas fa-utensils"></i>
                    <h3>独特的消化系统</h3>
                    <p>鹿是反刍动物，拥有四个胃室。它们会反刍食物以充分消化纤维素，这种消化过程可持续24-48小时。</p>
                </div>
                <div class="fact-card">
                    <i class="fas fa-chess-rook"></i>
                    <h3>雄伟的鹿角</h3>
                    <p>鹿角是哺乳动物中生长最快的组织，每天可生长2.5厘米。鹿角每年脱落并再生，新鹿角覆盖着称为"天鹅绒"的血管组织。</p>
                </div>
                <div class="fact-card">
                    <i class="fas fa-eye"></i>
                    <h3>卓越的感官</h3>
                    <p>鹿拥有近乎360度的视野，能够探测到最轻微的运动。它们的听力也十分敏锐，可以旋转耳朵以定位声音来源。</p>
                </div>
            </div>
        </section>
        
        <!-- 联系我 -->
        <section id="contact">
            <h2 class="section-title">与我联系</h2>
            <div class="contact-form">
                <div class="form-group">
                    <label for="name">姓名</label>
                    <input type="text" id="name" placeholder="请输入您的姓名">
                </div>
                <div class="form-group">
                    <label for="email">邮箱</label>
                    <input type="email" id="email" placeholder="请输入您的邮箱">
                </div>
                <div class="form-group">
                    <label for="message">留言</label>
                    <textarea id="message" placeholder="分享您对鹿的看法或问题..."></textarea>
                </div>
                <button type="submit">发送信息</button>
            </div>
        </section>
        
        <!-- 页脚 -->
        <footer>
            <h3>朱振博的鹿世界</h3>
            <div class="social-icons">
                <a href="#"><i class="fab fa-weixin"></i></a>
                <a href="#"><i class="fab fa-weibo"></i></a>
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-github"></i></a>
            </div>
            <p>© 2023 朱振博 | 探索鹿的优雅世界</p>
            <p>用爱感受自然，用心守护生命</p>
        </footer>
    </div>

    <script>
        // 创建奔跑的鹿
        function createRunningDeer() {
            const deerRunning = document.getElementById('deerRunning');
            const deerCount = 15;
            
            for (let i = 0; i < deerCount; i++) {
                const deer = document.createElement('div');
                deer.className = 'running-deer';
                
                // 随机位置和大小
                const topPos = Math.random() * 100;
                const size = 20 + Math.random() * 40;
                const duration = 15 + Math.random() * 30;
                const delay = Math.random() * 20;
                
                deer.style.top = `${topPos}%`;
                deer.style.width = `${size}px`;
                deer.style.height = `${size}px`;
                deer.style.animationDuration = `${duration}s`;
                deer.style.animationDelay = `-${delay}s`;
                
                deerRunning.appendChild(deer);
            }
        }
        
        // 滚动效果
        function setupScrollEffects() {
            const sections = document.querySelectorAll('section');
            
            window.addEventListener('scroll', () => {
                sections.forEach(section => {
                    const sectionTop = section.getBoundingClientRect().top;
                    const windowHeight = window.innerHeight;
                    
                    if (sectionTop < windowHeight * 0.75) {
                        section.style.opacity = 1;
                        section.style.transform = 'translateY(0)';
                    }
                });
            });
        }
        
        // 初始化
        document.addEventListener('DOMContentLoaded', () => {
            createRunningDeer();
            setupScrollEffects();
            
            // 为所有部分添加初始样式
            document.querySelectorAll('section').forEach(section => {
                section.style.opacity = 0;
                section.style.transform = 'translateY(50px)';
                section.style.transition = 'opacity 0.8s ease, transform 0.8s ease';
            });
            
            // 显示第一个部分
            document.querySelector('section').style.opacity = 1;
            document.querySelector('section').style.transform = 'translateY(0)';
        });
    </script>
</body>
</html>
