 <!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>Dapur Alya - Masakan Nusantara</title>
    <style>
        :root {
            --bg: #fff8f0;
            --card-bg: #ffffff;
            --primary: #c0392b;
            --primary-light: #e74c3c;
            --gold: #f39c12;
            --gold-light: #fdcb6e;
            --green: #27ae60;
            --green-light: #2ecc71;
            --text: #2c3e50;
            --text-light: #5d6d7e;
            --shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
            --shadow-lg: 0 8px 40px rgba(0, 0, 0, 0.12);
            --radius: 20px;
            --radius-sm: 12px;
            --transition: 0.3s cubic-bezier(0.25, 0.8, 0.25, 1.2);
            --font-title: 'Georgia', 'Times New Roman', serif;
            --font-body: 'Segoe UI', 'Roboto', 'Helvetica Neue', sans-serif;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
            -webkit-user-select: none;
            user-select: none;
        }

        body {
            font-family: var(--font-body);
            background: linear-gradient(180deg, #fff5eb 0%, #fdebd0 30%, #fce4c8 60%, #fef9f3 100%);
            min-height: 100vh;
            min-height: 100dvh;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow-x: hidden;
            padding: 10px;
            background-attachment: fixed;
        }

        /* Game Container */
        #game-container {
            width: 100%;
            max-width: 440px;
            background: var(--card-bg);
            border-radius: 24px;
            box-shadow: var(--shadow-lg);
            overflow: hidden;
            position: relative;
            min-height: 680px;
            min-height: 85dvh;
            display: flex;
            flex-direction: column;
            border: 3px solid #f0d9c0;
        }

        /* Screen system */
        .screen {
            display: none;
            flex-direction: column;
            flex: 1;
            padding: 20px 16px;
            overflow-y: auto;
            position: relative;
            animation: fadeSlideIn 0.4s ease;
        }
        .screen.active {
            display: flex;
        }

        @keyframes fadeSlideIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        @keyframes popIn {
            0% {
                transform: scale(0.3);
                opacity: 0;
            }
            60% {
                transform: scale(1.1);
                opacity: 1;
            }
            100% {
                transform: scale(1);
                opacity: 1;
            }
        }
        @keyframes bounce {
            0%,
            100% {
                transform: translateY(0);
            }
            30% {
                transform: translateY(-18px);
            }
            50% {
                transform: translateY(-6px);
            }
            70% {
                transform: translateY(-12px);
            }
        }
        @keyframes pulse {
            0%,
            100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
        }
        @keyframes steam {
            0% {
                opacity: 0.8;
                transform: translateY(0) scale(1);
            }
            100% {
                opacity: 0;
                transform: translateY(-60px) scale(1.8);
            }
        }
        @keyframes sparkle {
            0%,
            100% {
                opacity: 0;
                transform: scale(0) rotate(0deg);
            }
            50% {
                opacity: 1;
                transform: scale(1) rotate(180deg);
            }
        }
        @keyframes shake {
            0%,
            100% {
                transform: translateX(0);
            }
            20% {
                transform: translateX(-8px);
            }
            40% {
                transform: translateX(8px);
            }
            60% {
                transform: translateX(-5px);
            }
            80% {
                transform: translateX(5px);
            }
        }
        @keyframes floatUp {
            0% {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
            100% {
                opacity: 0;
                transform: translateY(-80px) scale(1.5);
            }
        }

        .shake {
            animation: shake 0.5s ease;
        }

        /* ============ TITLE SCREEN ============ */
        #title-screen {
            align-items: center;
            justify-content: center;
            text-align: center;
            gap: 16px;
            background: linear-gradient(180deg, #fff8f0 0%, #ffe8d5 40%, #fde0c8 100%);
        }
        #title-screen .chef-emoji {
            font-size: 90px;
            animation: bounce 2s ease-in-out infinite;
            filter: drop-shadow(0 6px 12px rgba(0, 0, 0, 0.15));
            line-height: 1;
        }
        #title-screen h1 {
            font-family: var(--font-title);
            font-size: 2rem;
            color: #8b4513;
            letter-spacing: 1px;
            text-shadow: 2px 2px 0 rgba(255, 180, 100, 0.4);
        }
        #title-screen h1 .highlight {
            color: #c0392b;
            font-size: 2.2rem;
        }
        #title-screen .subtitle {
            font-size: 0.9rem;
            color: #a0522d;
            letter-spacing: 2px;
            text-transform: uppercase;
            font-weight: 600;
        }
        #title-screen .decor {
            display: flex;
            gap: 8px;
            font-size: 28px;
            opacity: 0.7;
        }
        .btn-start {
            margin-top: 10px;
            padding: 16px 48px;
            font-size: 1.2rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            background: linear-gradient(135deg, #e74c3c, #c0392b);
            color: white;
            cursor: pointer;
            letter-spacing: 1px;
            box-shadow: 0 6px 24px rgba(192, 57, 43, 0.35);
            transition: var(--transition);
            font-family: var(--font-body);
            position: relative;
            overflow: hidden;
        }
        .btn-start:active {
            transform: scale(0.94);
            box-shadow: 0 3px 12px rgba(192, 57, 43, 0.3);
        }
        .btn-start::after {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(135deg, transparent 40%, rgba(255, 255, 255, 0.3) 50%, transparent 60%);
            background-size: 200% 200%;
            animation: shimmer 2s infinite;
        }
        @keyframes shimmer {
            0% {
                background-position: 200% 0;
            }
            100% {
                background-position: -200% 0;
            }
        }

        /* ============ MENU SCREEN ============ */
        #menu-screen {
            gap: 14px;
            background: #fffaf5;
        }
        #menu-screen .menu-header {
            text-align: center;
        }
        #menu-screen .menu-header h2 {
            font-family: var(--font-title);
            font-size: 1.5rem;
            color: #6b3a2a;
            letter-spacing: 1px;
        }
        #menu-screen .menu-header .total-score {
            font-size: 0.85rem;
            color: #b8860b;
            font-weight: 700;
            background: #fff8e1;
            display: inline-block;
            padding: 6px 16px;
            border-radius: 20px;
            margin-top: 4px;
            border: 2px solid #f0d78c;
        }
        .recipe-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
        }
        @media (max-width: 360px) {
            .recipe-grid {
                grid-template-columns: 1fr;
                gap: 8px;
            }
        }
        .recipe-card {
            background: #fff;
            border-radius: var(--radius-sm);
            padding: 14px 10px;
            text-align: center;
            cursor: pointer;
            border: 2px solid #f0e0d0;
            transition: var(--transition);
            box-shadow: var(--shadow);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 6px;
            position: relative;
            overflow: hidden;
        }
        .recipe-card:active {
            transform: scale(0.95);
            border-color: #e74c3c;
            box-shadow: 0 4px 16px rgba(231, 76, 60, 0.2);
        }
        .recipe-card .dish-emoji {
            font-size: 50px;
            line-height: 1;
            transition: var(--transition);
        }
        .recipe-card:active .dish-emoji {
            animation: popIn 0.3s ease;
        }
        .recipe-card .dish-name {
            font-weight: 700;
            font-size: 0.9rem;
            color: #4a3020;
            letter-spacing: 0.5px;
        }
        .recipe-card .dish-desc {
            font-size: 0.7rem;
            color: #8b7355;
            line-height: 1.3;
        }
        .recipe-card .difficulty {
            font-size: 0.65rem;
            font-weight: 600;
            padding: 3px 10px;
            border-radius: 10px;
            letter-spacing: 1px;
        }
        .diff-mudah {
            background: #e8f5e9;
            color: #2e7d32;
        }
        .diff-sedang {
            background: #fff3e0;
            color: #e65100;
        }
        .diff-sulit {
            background: #fce4ec;
            color: #c62828;
        }

        /* ============ COOKING SCREEN ============ */
        #cooking-screen {
            align-items: center;
            gap: 16px;
            background: #fffaf5;
            justify-content: flex-start;
            padding-top: 10px;
        }
        #cooking-screen .cook-header {
            text-align: center;
            width: 100%;
        }
        #cooking-screen .cook-header h3 {
            font-family: var(--font-title);
            font-size: 1.3rem;
            color: #5d3a2a;
        }
        #cooking-screen .stage-indicator {
            display: flex;
            gap: 8px;
            justify-content: center;
            margin: 4px 0;
        }
        .stage-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #e0d0c0;
            transition: all 0.3s ease;
        }
        .stage-dot.done {
            background: #27ae60;
            box-shadow: 0 0 8px rgba(39, 174, 96, 0.5);
        }
        .stage-dot.current {
            background: #f39c12;
            box-shadow: 0 0 12px rgba(243, 156, 18, 0.6);
            animation: pulse 0.8s ease-in-out infinite;
        }
        #cooking-screen .dish-display {
            font-size: 80px;
            line-height: 1;
            transition: all 0.3s ease;
            position: relative;
            min-height: 100px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        #cooking-screen .stage-name {
            font-weight: 700;
            font-size: 1rem;
            color: #8b4513;
            text-align: center;
            letter-spacing: 1px;
            min-height: 24px;
        }
        /* Meter Bar */
        .meter-container {
            width: 100%;
            max-width: 360px;
            position: relative;
            margin: 4px 0;
        }
        .meter-label {
            text-align: center;
            font-size: 0.75rem;
            font-weight: 600;
            color: #7d6b5d;
            margin-bottom: 4px;
            letter-spacing: 1px;
        }
        .meter-bar {
            width: 100%;
            height: 44px;
            background: linear-gradient(90deg,
                    #e74c3c 0%, #e74c3c 15%,
                    #f39c12 15%, #f39c12 35%,
                    #2ecc71 35%, #2ecc71 65%,
                    #f39c12 65%, #f39c12 85%,
                    #e74c3c 85%, #e74c3c 100%);
            border-radius: 22px;
            position: relative;
            overflow: hidden;
            box-shadow: inset 0 3px 8px rgba(0, 0, 0, 0.15);
            border: 3px solid #e8d5c0;
        }
        .meter-indicator {
            position: absolute;
            top: -6px;
            width: 8px;
            height: 56px;
            background: #2c3e50;
            border-radius: 4px;
            box-shadow: 0 0 16px rgba(44, 62, 80, 0.6), 0 0 6px rgba(255, 255, 255, 0.5);
            transition: none;
            z-index: 2;
            border: 2px solid #fff;
        }
        .meter-zones {
            position: absolute;
            inset: 0;
            display: flex;
            pointer-events: none;
            font-size: 10px;
            font-weight: 700;
            color: rgba(255, 255, 255, 0.9);
            align-items: center;
            justify-content: space-around;
            padding: 0 8px;
            letter-spacing: 1px;
            text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
        }
        .btn-tap-area {
            width: 100%;
            max-width: 360px;
            padding: 18px;
            font-size: 1.1rem;
            font-weight: 700;
            border: 3px dashed #e74c3c;
            border-radius: 50px;
            background: #fff5f5;
            color: #c0392b;
            cursor: pointer;
            letter-spacing: 2px;
            transition: var(--transition);
            font-family: var(--font-body);
            text-align: center;
        }
        .btn-tap-area:active {
            background: #ffe0e0;
            border-style: solid;
            transform: scale(0.96);
        }
        .btn-tap-area.disabled {
            opacity: 0.5;
            pointer-events: none;
            border-color: #ccc;
            color: #999;
        }
        #cooking-screen .feedback-text {
            font-weight: 700;
            font-size: 1.2rem;
            min-height: 30px;
            text-align: center;
            transition: all 0.2s ease;
        }
        .feedback-perfect {
            color: #27ae60;
            animation: popIn 0.4s ease;
        }
        .feedback-good {
            color: #f39c12;
        }
        .feedback-ok {
            color: #e67e22;
        }
        .feedback-miss {
            color: #e74c3c;
        }
        .particles-container {
            position: fixed;
            inset: 0;
            pointer-events: none;
            z-index: 100;
        }
        .particle {
            position: absolute;
            font-size: 22px;
            animation: floatUp 1s ease-out forwards;
            pointer-events: none;
        }

        /* ============ RESULT SCREEN ============ */
        #result-screen {
            align-items: center;
            justify-content: center;
            text-align: center;
            gap: 12px;
            background: #fffaf5;
        }
        #result-screen .result-emoji {
            font-size: 70px;
            animation: bounce 1.5s ease-in-out infinite;
        }
        #result-screen .result-title {
            font-family: var(--font-title);
            font-size: 1.4rem;
            color: #5d3a2a;
            font-weight: 700;
        }
        #result-screen .result-score {
            font-size: 2.5rem;
            font-weight: 900;
            color: #c0392b;
            letter-spacing: 2px;
        }
        #result-screen .result-breakdown {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            justify-content: center;
            font-size: 0.8rem;
            color: #6b5b4f;
        }
        #result-screen .result-breakdown span {
            background: #fef5ec;
            padding: 6px 12px;
            border-radius: 14px;
            border: 1px solid #f0dcc8;
            font-weight: 600;
        }
        .btn-back {
            padding: 14px 36px;
            font-size: 1rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            background: linear-gradient(135deg, #f39c12, #e67e22);
            color: white;
            cursor: pointer;
            letter-spacing: 1px;
            box-shadow: 0 6px 20px rgba(230, 126, 34, 0.3);
            transition: var(--transition);
            font-family: var(--font-body);
            margin-top: 8px;
        }
        .btn-back:active {
            transform: scale(0.94);
        }
        .btn-back.secondary {
            background: #fff;
            color: #8b4513;
            border: 2px solid #e0c8a8;
            box-shadow: none;
        }

        /* Responsive */
        @media (max-width: 400px) {
            #game-container {
                border-radius: 16px;
                min-height: 90dvh;
            }
            .screen {
                padding: 14px 10px;
            }
            #title-screen .chef-emoji {
                font-size: 70px;
            }
            #title-screen h1 {
                font-size: 1.5rem;
            }
            #title-screen h1 .highlight {
                font-size: 1.7rem;
            }
            .btn-start {
                padding: 14px 36px;
                font-size: 1rem;
            }
            .recipe-card .dish-emoji {
                font-size: 38px;
            }
            .recipe-card .dish-name {
                font-size: 0.78rem;
            }
            #cooking-screen .dish-display {
                font-size: 60px;
                min-height: 80px;
            }
            .meter-bar {
                height: 36px;
                border-radius: 18px;
            }
            .meter-indicator {
                width: 6px;
                height: 46px;
                top: -5px;
            }
            .btn-tap-area {
                padding: 14px;
                font-size: 0.95rem;
            }
        }
        @media (min-width: 401px) and (max-width: 480px) {
            .recipe-card .dish-emoji {
                font-size: 44px;
            }
            #cooking-screen .dish-display {
                font-size: 70px;
            }
        }
    </style>
</head>
<body>

    <!-- Particle container for effects -->
    <div class="particles-container" id="particles-container"></div>

    <!-- Game Container -->
    <div id="game-container">

        <!-- TITLE SCREEN -->
        <div class="screen active" id="title-screen">
            <div class="decor">🍚 🥘 🍢 🥗 🍜 🥞</div>
            <div class="chef-emoji">👩‍🍳</div>
            <h1>Dapur <span class="highlight">Alya</span></h1>
            <p class="subtitle">Masakan Nusantara</p>
            <p style="color:#8b7355;font-size:0.85rem;max-width:280px;">Masak makanan tradisional Indonesia & jadi koki handal!</p>
            <button class="btn-start" id="btn-start-game" onclick="showScreen('menu')">
                🔥 Mulai Memasak!
            </button>
            <div class="decor">✨ 🌶️ 🧅 🥥 ✨</div>
        </div>

        <!-- MENU SCREEN -->
        <div class="screen" id="menu-screen">
            <div class="menu-header">
                <h2>📋 Pilih Resep</h2>
                <div class="total-score">⭐ Total Skor: <strong id="total-score-display">0</strong></div>
            </div>
            <div class="recipe-grid" id="recipe-grid">
                <!-- Generated by JS -->
            </div>
        </div>

        <!-- COOKING SCREEN -->
        <div class="screen" id="cooking-screen">
            <div class="cook-header">
                <h3 id="cook-recipe-name">Nasi Goreng</h3>
                <div class="stage-indicator" id="stage-indicator"></div>
            </div>
            <div class="dish-display" id="dish-display">🍚</div>
            <div class="stage-name" id="stage-name">Siapkan bahan...</div>
            <div class="meter-container">
                <div class="meter-label">⏱️ TEPATKAN METER!</div>
                <div class="meter-bar" id="meter-bar">
                    <div class="meter-indicator" id="meter-indicator"></div>
                    <div class="meter-zones">
                        <span>😢</span><span>👍</span><span>⭐</span><span>👍</span><span>😢</span>
                    </div>
                </div>
            </div>
            <button class="btn-tap-area" id="btn-tap" onclick="tapMeter()">
                👆 TAP UNTUK MEMASAK!
            </button>
            <div class="feedback-text" id="feedback-text"></div>
            <button class="btn-back secondary" id="btn-cancel-cook" onclick="cancelCooking()" style="margin-top:0;">
                ⬅ Kembali ke Menu
            </button>
        </div>

        <!-- RESULT SCREEN -->
        <div class="screen" id="result-screen">
            <div class="result-emoji" id="result-emoji">🎉</div>
            <div class="result-title" id="result-title">Masakan Selesai!</div>
            <div class="result-score" id="result-score">+85</div>
            <div class="result-breakdown" id="result-breakdown"></div>
            <button class="btn-back" onclick="showScreen('menu')">📋 Kembali ke Menu</button>
            <button class="btn-back secondary" id="btn-retry" onclick="retryRecipe()">🔄 Coba Lagi</button>
        </div>
    </div>

    <script>
        // ==================== GAME ENGINE ====================
        const recipes = [{
            id: 'nasigoreng',
            name: 'Nasi Goreng',
            emoji: '🍚',
            finalEmoji: '🍛',
            desc: 'Nasi goreng khas Indonesia dengan bumbu kecap',
            difficulty: 'mudah',
            stages: [
                { name: 'Tumis bumbu halus!', speed: 0.025, emoji: '🧄' },
                { name: 'Masukkan nasi & aduk!', speed: 0.035, emoji: '🍚' },
                { name: 'Tambahkan kecap manis!', speed: 0.045, emoji: '🍯' },
            ],
        }, {
            id: 'rendang',
            name: 'Rendang',
            emoji: '🥘',
            finalEmoji: '🍖',
            desc: 'Daging sapi dimasak santan & rempah khas Padang',
            difficulty: 'sulit',
            stages: [
                { name: 'Haluskan bumbu rempah!', speed: 0.028, emoji: '🌶️' },
                { name: 'Masak daging dengan santan!', speed: 0.04, emoji: '🥥' },
                { name: 'Aduk hingga kering & karamel!', speed: 0.055, emoji: '🔥' },
            ],
        }, {
            id: 'sateayam',
            name: 'Sate Ayam',
            emoji: '🍢',
            finalEmoji: '🍡',
            desc: 'Sate ayam bumbu kacang, dibakar di atas arang',
            difficulty: 'sedang',
            stages: [
                { name: 'Marinasi ayam dengan bumbu!', speed: 0.022, emoji: '🍗' },
                { name: 'Tusuk daging ke lidi!', speed: 0.032, emoji: '📌' },
                { name: 'Bakar sate di atas bara!', speed: 0.048, emoji: '🔥' },
            ],
        }, {
            id: 'gadogado',
            name: 'Gado-Gado',
            emoji: '🥗',
            finalEmoji: '🥙',
            desc: 'Sayuran segar dengan siraman bumbu kacang',
            difficulty: 'mudah',
            stages: [
                { name: 'Rebus sayuran segar!', speed: 0.02, emoji: '🥬' },
                { name: 'Giling bumbu kacang!', speed: 0.03, emoji: '🥜' },
                { name: 'Siram & aduk merata!', speed: 0.04, emoji: '💧' },
            ],
        }, {
            id: 'sotoayam',
            name: 'Soto Ayam',
            emoji: '🍜',
            finalEmoji: '🥣',
            desc: 'Soto kuning hangat dengan suwiran ayam kampung',
            difficulty: 'sedang',
            stages: [
                { name: 'Rebus kaldu ayam & rempah!', speed: 0.024, emoji: '🐔' },
                { name: 'Suwir daging ayam!', speed: 0.034, emoji: '🍖' },
                { name: 'Racik pelengkap & sajikan!', speed: 0.05, emoji: '🥚' },
            ],
        }, {
            id: 'martabak',
            name: 'Martabak Manis',
            emoji: '🥞',
            finalEmoji: '🧇',
            desc: 'Martabak tebal bersarang dengan topping melimpah',
            difficulty: 'sedang',
            stages: [
                { name: 'Kocok adonan hingga mengembang!', speed: 0.026, emoji: '🥚' },
                { name: 'Tuang & masak di wajan!', speed: 0.038, emoji: '🍳' },
                { name: 'Beri topping & lipat!', speed: 0.052, emoji: '🧈' },
            ],
        }];

        let gameState = {
            currentScreen: 'title',
            currentRecipe: null,
            currentStage: 0,
            totalScore: 0,
            stageResults: [],
            meterAnimId: null,
            meterPosition: 0,
            meterDirection: 1,
            meterSpeed: 0.03,
            meterActive: false,
            meterPaused: false,
            comboCount: 0,
        };

        // ==================== SCREEN MANAGEMENT ====================
        function showScreen(screenName) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            const target = document.getElementById(screenName + '-screen');
            if (target) {
                target.classList.add('active');
                gameState.currentScreen = screenName;
            }
            if (screenName === 'menu') {
                renderRecipeCards();
                updateTotalScoreDisplay();
                stopMeter();
                gameState.currentRecipe = null;
                gameState.currentStage = 0;
                gameState.stageResults = [];
            }
            if (screenName === 'title') {
                stopMeter();
                gameState.totalScore = 0;
                updateTotalScoreDisplay();
            }
            if (screenName === 'cooking' && gameState.currentRecipe) {
                setupCookingScreen();
            }
            document.getElementById('game-container').scrollTop = 0;
            window.scrollTo(0, 0);
        }

        // ==================== RECIPE CARDS ====================
        function renderRecipeCards() {
            const grid = document.getElementById('recipe-grid');
            grid.innerHTML = '';
            recipes.forEach((recipe, index) => {
                const card = document.createElement('div');
                card.className = 'recipe-card';
                card.innerHTML = `
                <div class="dish-emoji">${recipe.emoji}</div>
                <div class="dish-name">${recipe.name}</div>
                <div class="dish-desc">${recipe.desc}</div>
                <div class="difficulty diff-${recipe.difficulty}">${recipe.difficulty.toUpperCase()}</div>
              `;
                card.addEventListener('click', () => startCooking(recipe));
                card.addEventListener('touchend', (e) => {
                    e.preventDefault();
                    startCooking(recipe);
                });
                grid.appendChild(card);
            });
        }

        function updateTotalScoreDisplay() {
            const display = document.getElementById('total-score-display');
            if (display) display.textContent = gameState.totalScore;
        }

        // ==================== COOKING SYSTEM ====================
        function startCooking(recipe) {
            gameState.currentRecipe = recipe;
            gameState.currentStage = 0;
            gameState.stageResults = [];
            gameState.comboCount = 0;
            showScreen('cooking');
            setupCookingScreen();
        }

        function retryRecipe() {
            if (gameState.currentRecipe) {
                gameState.currentStage = 0;
                gameState.stageResults = [];
                gameState.comboCount = 0;
                showScreen('cooking');
                setupCookingScreen();
            }
        }

        function cancelCooking() {
            stopMeter();
            // Deduct small penalty or just go back
            gameState.currentRecipe = null;
            gameState.currentStage = 0;
            gameState.stageResults = [];
            showScreen('menu');
        }

        function setupCookingScreen() {
            const recipe = gameState.currentRecipe;
            if (!recipe) return;

            document.getElementById('cook-recipe-name').textContent = recipe.name;
            document.getElementById('dish-display').textContent = recipe.emoji;
            document.getElementById('feedback-text').textContent = '';
            document.getElementById('feedback-text').className = 'feedback-text';
            document.getElementById('btn-tap').classList.remove('disabled');

            // Stage indicator dots
            const stageIndicator = document.getElementById('stage-indicator');
            stageIndicator.innerHTML = '';
            recipe.stages.forEach((_, i) => {
                const dot = document.createElement('span');
                dot.className = 'stage-dot';
                if (i < gameState.currentStage) dot.classList.add('done');
                if (i === gameState.currentStage) dot.classList.add('current');
                stageIndicator.appendChild(dot);
            });

            // Stage name
            const stage = recipe.stages[gameState.currentStage];
            document.getElementById('stage-name').textContent = `Langkah ${gameState.currentStage + 1}: ${stage.name}`;
            document.getElementById('dish-display').textContent = stage.emoji;

            // Start meter
            startMeter(stage.speed);
        }

        function startMeter(speed) {
            stopMeter();
            gameState.meterActive = true;
            gameState.meterPaused = false;
            gameState.meterPosition = Math.random() * 0.4 + 0.1; // Start somewhat randomly
            gameState.meterDirection = Math.random() > 0.5 ? 1 : -1;
            gameState.meterSpeed = speed;
            document.getElementById('btn-tap').classList.remove('disabled');
            document.getElementById('feedback-text').textContent = '';
            document.getElementById('feedback-text').className = 'feedback-text';
            updateMeterVisual();
            gameState.meterAnimId = requestAnimationFrame(animateMeter);
        }

        function stopMeter() {
            gameState.meterActive = false;
            gameState.meterPaused = true;
            if (gameState.meterAnimId) {
                cancelAnimationFrame(gameState.meterAnimId);
                gameState.meterAnimId = null;
            }
        }

        function animateMeter(timestamp) {
            if (!gameState.meterActive || gameState.meterPaused) return;

            const barWidth = 1; // normalized 0-1
            gameState.meterPosition += gameState.meterSpeed * gameState.meterDirection;

            // Bounce at edges
            if (gameState.meterPosition >= 0.98) {
                gameState.meterPosition = 0.98;
                gameState.meterDirection = -1;
            } else if (gameState.meterPosition <= 0.02) {
                gameState.meterPosition = 0.02;
                gameState.meterDirection = 1;
            }

            updateMeterVisual();
            gameState.meterAnimId = requestAnimationFrame(animateMeter);
        }

        function updateMeterVisual() {
            const indicator = document.getElementById('meter-indicator');
            if (!indicator) return;
            const bar = document.getElementById('meter-bar');
            if (!bar) return;
            const barWidth = bar.clientWidth;
            const indicatorWidth = indicator.clientWidth || 8;
            const maxLeft = barWidth - indicatorWidth;
            const left = gameState.meterPosition * maxLeft;
            indicator.style.left = left + 'px';
        }

        function tapMeter() {
            if (!gameState.meterActive || gameState.meterPaused) return;
            if (!gameState.currentRecipe) return;

            // Stop the meter
            gameState.meterPaused = true;
            const pos = gameState.meterPosition;
            const recipe = gameState.currentRecipe;
            const stage = recipe.stages[gameState.currentStage];

            let result;
            // Green zone: 0.35 - 0.65 (center 30%)
            if (pos >= 0.35 && pos <= 0.65) {
                result = 'perfect';
                gameState.comboCount++;
                spawnParticles('⭐', 5);
            }
            // Yellow zone: 0.15-0.35 or 0.65-0.85
            else if ((pos >= 0.15 && pos < 0.35) || (pos > 0.65 && pos <= 0.85)) {
                result = 'good';
                gameState.comboCount = Math.max(0, gameState.comboCount - 1);
                spawnParticles('✨', 3);
            }
            // Orange zone: 0.05-0.15 or 0.85-0.95
            else if ((pos >= 0.05 && pos < 0.15) || (pos > 0.85 && pos <= 0.95)) {
                result = 'ok';
                gameState.comboCount = 0;
                spawnParticles('💨', 2);
            }
            // Red zone: edges
            else {
                result = 'miss';
                gameState.comboCount = 0;
                spawnParticles('💢', 1);
            }

            // Combo bonus
            let comboBonus = 0;
            if (result === 'perfect' && gameState.comboCount >= 2) {
                comboBonus = gameState.comboCount * 5;
            }

            gameState.stageResults.push({ result, comboBonus, stageIndex: gameState.currentStage });

            // Show feedback
            const feedbackEl = document.getElementById('feedback-text');
            const feedbackMap = {
                perfect: { text: '🌟 SEMPURNA! 🌟', class: 'feedback-perfect' },
                good: { text: '👍 Bagus!', class: 'feedback-good' },
                ok: { text: '😅 Cukup...', class: 'feedback-ok' },
                miss: { text: '😢 Melenceng!', class: 'feedback-miss' },
            };
            const fb = feedbackMap[result];
            feedbackEl.textContent = comboBonus > 0 ? fb.text + ` +${comboBonus} kombo!` : fb.text;
            feedbackEl.className = 'feedback-text ' + fb.class;

            // Shake on miss
            const container = document.getElementById('game-container');
            if (result === 'miss') {
                container.classList.add('shake');
                setTimeout(() => container.classList.remove('shake'), 500);
            }

            // Disable tap button temporarily
            const btnTap = document.getElementById('btn-tap');
            btnTap.classList.add('disabled');

            // Advance after delay
            setTimeout(() => {
                advanceStage();
            }, 900);
        }

        function advanceStage() {
            const recipe = gameState.currentRecipe;
            if (!recipe) return;

            gameState.currentStage++;

            if (gameState.currentStage >= recipe.stages.length) {
                // All stages complete
                finishRecipe();
            } else {
                // Next stage
                setupCookingScreen();
            }
        }

        function finishRecipe() {
            stopMeter();
            const recipe = gameState.currentRecipe;
            const results = gameState.stageResults;

            // Calculate score
            let totalStageScore = 0;
            let perfectCount = 0;
            let goodCount = 0;
            let okCount = 0;
            let missCount = 0;

            results.forEach(r => {
                const baseScore = { perfect: 40, good: 20, ok: 8, miss: 0 };
                totalStageScore += baseScore[r.result] + r.comboBonus;
                if (r.result === 'perfect') perfectCount++;
                if (r.result === 'good') goodCount++;
                if (r.result === 'ok') okCount++;
                if (r.result === 'miss') missCount++;
            });

            // Bonus for all perfect
            if (perfectCount === recipe.stages.length) {
                totalStageScore += 30;
            }

            gameState.totalScore += totalStageScore;
            updateTotalScoreDisplay();

            // Show result screen
            showScreen('result');
            const resultEmoji = document.getElementById('result-emoji');
            const resultTitle = document.getElementById('result-title');
            const resultScore = document.getElementById('result-score');
            const resultBreakdown = document.getElementById('result-breakdown');

            if (perfectCount === recipe.stages.length) {
                resultEmoji.textContent = '🏆';
                resultTitle.textContent = 'LUAR BIASA! Semua Sempurna!';
            } else if (perfectCount >= recipe.stages.length - 1 && missCount === 0) {
                resultEmoji.textContent = '🎉';
                resultTitle.textContent = 'Masakan ' + recipe.name + ' Jadi!';
            } else if (missCount >= 2) {
                resultEmoji.textContent = '😅';
                resultTitle.textContent = 'Masakan ' + recipe.name + '... Cukup!';
            } else {
                resultEmoji.textContent = '🍽️';
                resultTitle.textContent = 'Masakan ' + recipe.name + ' Selesai!';
            }

            resultScore.textContent = '+' + totalStageScore;
            resultBreakdown.innerHTML = `
            <span>⭐ Sempurna: ${perfectCount}</span>
            <span>👍 Bagus: ${goodCount}</span>
            <span>😅 OK: ${okCount}</span>
            <span>😢 Miss: ${missCount}</span>
          `;
            document.getElementById('dish-display').textContent = recipe.finalEmoji;

            // Store for retry
            document.getElementById('btn-retry').dataset.recipeId = recipe.id;

            // Spawn celebration particles
            if (perfectCount >= 2) {
                spawnParticles('🎉', 10);
                spawnParticles('✨', 8);
            }
        }

        // ==================== PARTICLES ====================
        function spawnParticles(emoji, count) {
            const container = document.getElementById('particles-container');
            const centerX = window.innerWidth / 2;
            const centerY = window.innerHeight / 2;

            for (let i = 0; i < count; i++) {
                const particle = document.createElement('span');
                particle.className = 'particle';
                particle.textContent = emoji;
                particle.style.left = (centerX + (Math.random() - 0.5) * 200) + 'px';
                particle.style.top = (centerY + (Math.random() - 0.5) * 100) + 'px';
                particle.style.animationDuration = (0.6 + Math.random() * 1) + 's';
                particle.style.fontSize = (16 + Math.random() * 20) + 'px';
                container.appendChild(particle);

                setTimeout(() => {
                    if (particle.parentNode) particle.parentNode.removeChild(particle);
                }, 1200);
            }
        }

        // ==================== INITIALIZATION ====================
        function init() {
            renderRecipeCards();
            updateTotalScoreDisplay();
            showScreen('title');

            // Handle window resize for meter
            window.addEventListener('resize', () => {
                if (gameState.currentScreen === 'cooking' && gameState.meterActive) {
                    updateMeterVisual();
                }
            });

            // Prevent double-tap zoom on mobile
            document.addEventListener('dblclick', function(e) {
                if (e.target.closest('#game-container')) {
                    e.preventDefault();
                }
            }, { passive: false });

            // Prevent scrolling while cooking
            document.getElementById('cooking-screen').addEventListener('touchmove', function(e) {
                if (gameState.meterActive && !gameState.meterPaused) {
                    // Allow scrolling in the cooking screen but prevent accidental
                }
            }, { passive: true });

            // Keyboard support for testing
            document.addEventListener('keydown', function(e) {
                if (e.code === 'Space' && gameState.currentScreen === 'cooking' && gameState.meterActive && !
                    gameState.meterPaused) {
                    e.preventDefault();
                    tapMeter();
                }
            });

            console.log('🍳 Dapur Alya - Masakan Nusantara siap!');
            console.log('📋 ' + recipes.length + ' resep masakan tradisional Indonesia tersedia');
            console.log('👆 Tap meter saat indikator di zona hijau untuk hasil sempurna!');
            console.log('📱 Optimal dimainkan di ponsel');
        }

        // Start the game
        init();
    </script>
</body>
</html>
