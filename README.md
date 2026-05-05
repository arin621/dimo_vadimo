# dimo_vadimo
d
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>DIMOVADIMO | 50 УРОВНЕЙ PASS | 32 КОНФИГА | 6 ИГР | АДМИН ПАНЕЛЬ</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #0f0c29 0%, #1a1a3e 50%, #24243e 100%);
            font-family: 'Poppins', 'Segoe UI', system-ui, sans-serif;
            color: #fff;
            min-height: 100vh;
        }

        .animated-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: -1;
        }
        .animated-bg span {
            position: absolute;
            width: 3px;
            height: 3px;
            background: rgba(255, 68, 204, 0.4);
            border-radius: 50%;
            animation: float 20s infinite linear;
        }
        @keyframes float {
            0% { transform: translateY(100vh) scale(0); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(-100vh) scale(1); opacity: 0; }
        }

        .wrapper {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 24px;
            position: relative;
            z-index: 2;
        }

        .glass-card {
            background: rgba(20, 20, 50, 0.55);
            backdrop-filter: blur(12px);
            border-radius: 32px;
            border: 1px solid rgba(255, 68, 204, 0.3);
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .glass-card:hover {
            transform: translateY(-4px);
            border-color: #ff44cc;
            box-shadow: 0 10px 30px rgba(255, 68, 204, 0.2);
        }

        .btn-primary {
            background: linear-gradient(95deg, #ff44cc, #ff9900);
            border: none;
            padding: 10px 24px;
            border-radius: 60px;
            font-weight: 600;
            cursor: pointer;
            color: white;
            transition: 0.2s;
        }
        .btn-primary:hover { transform: scale(1.02); box-shadow: 0 0 15px #ff44cc; }
        .btn-secondary {
            background: transparent;
            border: 1px solid #ff44cc;
            padding: 8px 20px;
            border-radius: 60px;
            color: #ff44cc;
            font-weight: 500;
            cursor: pointer;
            transition: 0.2s;
        }
        .btn-secondary:hover { background: rgba(255, 68, 204, 0.2); }
        .btn-gold {
            background: linear-gradient(135deg, #ffd700, #ff8c00);
            color: #1a1a2e;
            border: none;
            padding: 12px 28px;
            border-radius: 60px;
            font-weight: bold;
            cursor: pointer;
        }

        .nav-container {
            background: rgba(0, 0, 0, 0.4);
            backdrop-filter: blur(16px);
            border-radius: 80px;
            padding: 6px;
            display: flex;
            gap: 8px;
            justify-content: center;
            flex-wrap: wrap;
            margin: 20px 0;
        }
        .nav-btn {
            padding: 10px 24px;
            border-radius: 60px;
            font-weight: 600;
            cursor: pointer;
            color: #aaa;
            transition: 0.2s;
        }
        .nav-btn.active {
            background: linear-gradient(95deg, #ff44cc, #ff9900);
            color: white;
            box-shadow: 0 0 12px #ff44cc;
        }
        .nav-btn:hover:not(.active) { background: rgba(255, 68, 204, 0.3); color: white; }

        .page {
            display: none;
            animation: fadeSlide 0.35s ease;
        }
        .page.active-page { display: block; }
        @keyframes fadeSlide {
            from { opacity: 0; transform: translateY(15px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .rank-badge {
            display: inline-block;
            padding: 6px 16px;
            border-radius: 60px;
            font-size: 0.8rem;
            font-weight: bold;
        }
        .rank-iron { background: #6c6c6c; color: white; }
        .rank-bronze { background: #cd7f32; color: white; }
        .rank-silver { background: #c0c0c0; color: black; }
        .rank-gold { background: #ffd700; color: black; }
        .rank-platinum { background: #00bfff; color: white; }
        .rank-diamond { background: #b9f2ff; color: black; }
        .rank-master { background: #9400d3; color: white; }
        .rank-grandmaster { background: #ff0000; color: white; }
        .rank-legend { background: linear-gradient(95deg, #ff44cc, #ff9900); color: white; }

        .config-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(170px, 1fr));
            gap: 16px;
        }
        .premium-badge {
            position: absolute;
            top: -8px;
            right: -8px;
            background: linear-gradient(135deg, #ff44cc, #a855f7);
            padding: 4px 8px;
            border-radius: 60px;
            font-size: 0.6rem;
            font-weight: bold;
        }
        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
        }
        .auto-clicker-btn {
            font-size: 1.5rem;
            padding: 20px;
            width: 100%;
            background: linear-gradient(135deg, #ff44cc, #ff9900);
            border: none;
            border-radius: 60px;
            color: white;
            font-weight: bold;
            cursor: pointer;
        }
        .toast-notify {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #1a1a2e;
            border-left: 4px solid #ff44cc;
            padding: 12px 24px;
            border-radius: 16px;
            z-index: 9999;
            backdrop-filter: blur(8px);
            animation: slideIn 0.3s ease;
        }
        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        .pass-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
            gap: 12px;
            max-height: 500px;
            overflow-y: auto;
            padding: 8px;
        }
        .stat-number {
            font-size: 2rem;
            font-weight: 800;
            background: linear-gradient(95deg, #ffd700, #ff44cc);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }
        input, select {
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid #ff44cc;
            border-radius: 16px;
            padding: 10px;
            color: white;
        }
    </style>
</head>
<body>
<div class="animated-bg" id="bg"></div>
<div class="wrapper">
    <!-- ШАПКА -->
    <div class="flex flex-wrap justify-between items-center py-5 gap-3">
        <div class="flex items-center gap-3">
            <div class="text-4xl animate-pulse">⚡🌀</div>
            <div>
                <span class="text-2xl font-black">DIMO<span style="color:#ff44cc;">VADIMO</span></span>
                <div class="text-[10px] text-gray-400">ЛУЧШИЙ ЧИТ НА РЕАЛЬНОСТЬ | 50 УРОВНЕЙ PASS</div>
            </div>
        </div>
        <div class="flex gap-3 items-center flex-wrap">
            <div class="glass-card px-5 py-2 rounded-full">⭐ <span id="globalDV" class="font-bold text-pink-300">0</span> DV</div>
            <div class="glass-card px-5 py-2 rounded-full">🎫 <span id="globalPassLevel">ур.1</span></div>
            <button id="openLoginBtn" class="btn-secondary" style="padding: 6px 16px;">🔐 ВХОД</button>
            <span id="userNameDisplay" class="text-sm text-pink-300 hidden"></span>
            <button id="logoutBtn" class="btn-secondary hidden" style="border-color:#ff4466;">🚪 ВЫЙТИ</button>
        </div>
    </div>

    <!-- НАВИГАЦИЯ -->
    <div class="nav-container">
        <div class="nav-btn active" data-page="home">🏠 ГЛАВНАЯ</div>
        <div class="nav-btn" data-page="about">📖 ОПИСАНИЕ</div>
        <div class="nav-btn" data-page="configs">⚙️ КОНФИГИ (32)</div>
        <div class="nav-btn" data-page="pass">🎫 DV PASS (50 ур.)</div>
        <div class="nav-btn" data-page="games">🎮 ИГРЫ (6)</div>
        <div class="nav-btn" data-page="profile">👤 ПРОФИЛЬ</div>
        <div class="nav-btn" data-page="admin" id="adminNavBtn" style="display:none;">👑 АДМИН</div>
    </div>

    <!-- ГЛАВНАЯ -->
    <div id="homePage" class="page active-page">
        <div class="grid lg:grid-cols-2 gap-8 py-10">
            <div class="glass-card p-10">
                <h1 class="text-5xl font-bold leading-tight">ЧИТ НА <span style="color:#ff44cc;">РЕАЛЬНОСТЬ</span></h1>
                <p class="text-gray-300 text-lg my-5"><span class="text-pink-300 font-bold">50 уровней Pass</span> | <span class="text-pink-300 font-bold">32 конфига</span> | <span class="text-pink-300 font-bold">6 мини-игр</span> | <span class="text-pink-300 font-bold">Премиум конфиги</span> | <span class="text-pink-300 font-bold">9 рангов</span></p>
                <div class="flex gap-4">
                    <button class="btn-primary" id="toPassBtn">🎫 К DV PASS</button>
                    <button class="btn-secondary" id="toGamesBtn">🎮 ИГРАТЬ</button>
                    <button class="btn-secondary" id="toAboutBtn">📖 УЗНАТЬ БОЛЬШЕ</button>
                </div>
            </div>
            <div class="glass-card p-10 text-center">
                <div class="text-7xl mb-3">🏆</div>
                <h3 class="text-xl mb-2">ТВОЙ РАНГ</h3>
                <div id="rankDisplay" class="rank-badge rank-iron text-xl px-6 py-2">ЖЕЛЕЗО</div>
                <p class="text-sm text-gray-400 mt-4">Повышай уровень Pass, чтобы получить новый ранг!</p>
            </div>
        </div>
    </div>

    <!-- ОПИСАНИЕ САЙТА (ПОЛНОЕ) -->
    <div id="aboutPage" class="page">
        <div class="glass-card p-8 mb-6">
            <h2 class="text-4xl font-bold text-center mb-4">🔥 DIMO<span style="color:#ff44cc;">VADIMO</span> — ЛУЧШИЙ ЧИТ НА РЕАЛЬНОСТЬ</h2>
            <p class="text-center text-gray-300 mb-8">Твой персональный инструмент для взлома реальности. Повышай уровень, открывай мощные конфиги, играй в мини-игры и становись легендой!</p>
            
            <div class="grid md:grid-cols-3 gap-6 mb-8">
                <div class="glass-card p-5 text-center"><div class="text-5xl mb-2">🎫</div><h3 class="text-xl font-bold">50 УРОВНЕЙ DV PASS</h3><p>Прокачивайся, открывай новые ранги и получай эксклюзивные награды. 9 рангов: от Железа до Легенды!</p></div>
                <div class="glass-card p-5 text-center"><div class="text-5xl mb-2">⚙️</div><h3 class="text-xl font-bold">32 УНИКАЛЬНЫХ КОНФИГА</h3><p>12 обычных + 20 премиум конфигов. Каждый даёт мощные бонусы к характеристикам. Премиум — только с DV Pass!</p></div>
                <div class="glass-card p-5 text-center"><div class="text-5xl mb-2">🎮</div><h3 class="text-xl font-bold">6 УВЛЕКАТЕЛЬНЫХ ИГР</h3><p>Угадай число, Автокликер, КНБ, Орёл-решка, Блэкджек, Кости. Зарабатывай DV и повышай уровень!</p></div>
                <div class="glass-card p-5 text-center"><div class="text-5xl mb-2">💎</div><h3 class="text-xl font-bold">ПРЕМИУМ КОНФИГИ</h3><p>Божественный, Абсолют, Хрономаг, Некромант, Архангел и другие. Доступны только с DV Pass!</p></div>
                <div class="glass-card p-5 text-center"><div class="text-5xl mb-2">🏆</div><h3 class="text-xl font-bold">9 РАНГОВ ПРЕСТИЖА</h3><p>Железо → Бронза → Серебро → Золото → Платина → Диамант → Мастер → Грандмастер → Легенда</p></div>
                <div class="glass-card p-5 text-center"><div class="text-5xl mb-2">👑</div><h3 class="text-xl font-bold">АДМИН ПАНЕЛЬ</h3><p>Полный контроль над пользователями, выдача DV, конфигов, уровней Pass и управление премиум доступом.</p></div>
            </div>

            <div class="glass-card p-6">
                <h3 class="text-2xl font-bold mb-4">✨ ФУНКЦИОНАЛ ПРОЕКТА:</h3>
                <ul class="space-y-2 text-gray-300">
                    <li>⭐ • <span class="text-pink-300">DV Pass с 50 уровнями</span> — повышай уровень, получай награды и открывай новые ранги</li>
                    <li>⚙️ • <span class="text-pink-300">32 конфига</span> (12 обычных + 20 премиум) с уникальными бонусами</li>
                    <li>🎮 • <span class="text-pink-300">6 мини-игр</span> для заработка DV и развития</li>
                    <li>💎 • <span class="text-pink-300">Премиум конфиги</span> — эксклюзивные усиления только для владельцев DV Pass</li>
                    <li>🏆 • <span class="text-pink-300">Ранговая система</span> — 9 рангов от Железа до Легенды</li>
                    <li>📋 • <span class="text-pink-300">Ежедневные задания</span> — выполняй и получай опыт для Pass'а</li>
                    <li>👑 • <span class="text-pink-300">Админ панель</span> — полное управление пользователями, выдача DV и конфигов</li>
                    <li>🎨 • <span class="text-pink-300">Красивый интерфейс</span> с анимацией и эффектами</li>
                    <li>💾 • <span class="text-pink-300">Сохранение прогресса</span> — все данные хранятся локально</li>
                </ul>
            </div>

            <div class="text-center mt-6">
                <p class="text-gray-400 text-sm">🔥 DimoVadimo — это не просто чит, это целая экосистема для прокачки твоей реальности! Присоединяйся к сообществу лучших читеров!</p>
            </div>
        </div>
    </div>

    <!-- КОНФИГИ (32 штуки) -->
    <div id="configsPage" class="page">
        <h2 class="text-3xl font-bold text-center mb-6">⚙️ ВСЕ КОНФИГИ (32)</h2>
        <div id="configsGrid" class="config-grid mb-6"></div>
        <div class="glass-card p-5 text-center">
            <p class="text-lg">✨ АКТИВНЫЙ КОНФИГ: <span id="activeConfigSpan" class="text-pink-300 font-bold">не выбран</span></p>
            <p class="text-sm text-gray-400 mt-2">🔒 Премиум конфиги (💎) доступны только при наличии DV Pass</p>
        </div>
    </div>

    <!-- DV PASS (50 УРОВНЕЙ) -->
    <div id="passPage" class="page">
        <div class="glass-card p-6 text-center mb-6">
            <h1 class="text-3xl font-bold">⭐ DV PASS: 50 УРОВНЕЙ ⭐</h1>
            <div class="bg-black/30 rounded-full h-12 overflow-hidden mt-4"><div id="passFillBar" class="bg-gradient-to-r from-yellow-500 to-orange-500 h-full flex items-center justify-end pr-4 font-bold text-black">УРОВЕНЬ 1 / 50</div></div>
            <div class="flex justify-between items-center mt-4 flex-wrap gap-3">
                <span>🏆 РАНГ: <span id="rankNamePass" class="rank-badge rank-iron">ЖЕЛЕЗО</span></span>
                <button id="buyPassBtn" class="btn-gold">🔥 КУПИТЬ PASS (490 DV)</button>
            </div>
        </div>
        <div id="tiersGrid" class="pass-grid"></div>
        <button id="getExpBtn" class="btn-primary w-full mt-6 py-3">📋 ЗАДАНИЯ ДЛЯ ОПЫТА</button>
    </div>

    <!-- 6 МИНИ-ИГР -->
    <div id="gamesPage" class="page">
        <h2 class="text-3xl font-bold text-center mb-6">🎮 6 МИНИ-ИГР</h2>
        <div class="games-grid">
            <div class="glass-card p-5 text-center"><div class="text-5xl">🎲</div><h3 class="text-lg mt-2">УГАДАЙ ЧИСЛО</h3><p class="text-xs text-gray-400">Ставка 10 DV, выигрыш 30 DV</p><input type="number" id="guessNumber" placeholder="1-10" class="w-full mt-2 text-center"><button id="playGuessBtn" class="btn-primary mt-2 w-full">ИГРАТЬ</button><div id="guessResult" class="mt-1 text-sm"></div></div>
            <div class="glass-card p-5 text-center"><div class="text-5xl">🖱️⚡</div><h3 class="text-lg mt-2">АВТОКЛИКЕР</h3><p class="text-xs text-gray-400"><span class="text-pink-300">0.1 DV за клик</span> | 10 секунд</p><div id="clickerScore" class="text-3xl font-bold text-pink-300 my-2">0</div><button id="startClickerBtn" class="auto-clicker-btn text-base">🔴 НАЧАТЬ КЛИКАТЬ</button><div id="clickerTimer" class="text-xs text-yellow-300 mt-1"></div><div id="clickerResult" class="mt-1 text-sm"></div></div>
            <div class="glass-card p-5 text-center"><div class="text-5xl">✊✌️✋</div><h3 class="text-lg mt-2">КНБ</h3><div class="flex gap-1 justify-center mt-2"><button class="btn-secondary text-sm rpsBtn" data-choice="rock">✊</button><button class="btn-secondary text-sm rpsBtn" data-choice="paper">✋</button><button class="btn-secondary text-sm rpsBtn" data-choice="scissors">✌️</button></div><div id="rpsResult" class="mt-2 text-sm"></div></div>
            <div class="glass-card p-5 text-center"><div class="text-5xl">🪙</div><h3 class="text-lg mt-2">ОРЁЛ-РЕШКА</h3><p class="text-xs text-gray-400">Ставка 5 DV, выигрыш 12 DV</p><div class="flex gap-2 justify-center mt-2"><button class="btn-secondary coinBtn" data-side="eagle">🦅 ОРЁЛ</button><button class="btn-secondary coinBtn" data-side="tails">🪙 РЕШКА</button></div><div id="coinResult" class="mt-2 text-sm"></div></div>
            <div class="glass-card p-5 text-center"><div class="text-5xl">🃏</div><h3 class="text-lg mt-2">БЛЭКДЖЕК</h3><p class="text-xs text-gray-400">Ставка 15 DV, выигрыш 40 DV</p><button id="playBlackjackBtn" class="btn-primary mt-2 w-full">ВЗЯТЬ КАРТУ</button><div id="bjResult" class="mt-2 text-sm"></div></div>
            <div class="glass-card p-5 text-center"><div class="text-5xl">🎲🎲</div><h3 class="text-lg mt-2">КОСТИ</h3><p class="text-xs text-gray-400">Ставка 8 DV, выигрыш 25 DV</p><button id="playDiceBtn" class="btn-primary mt-2 w-full">БРОСИТЬ КОСТИ</button><div id="diceResult" class="mt-2 text-sm"></div></div>
        </div>
    </div>

    <!-- ПРОФИЛЬ -->
    <div id="profilePage" class="page">
        <div class="glass-card p-8 max-w-lg mx-auto text-center">
            <div class="text-5xl mb-3">👤</div>
            <h3 class="text-2xl font-bold mb-4">ПРОФИЛЬ</h3>
            <div class="space-y-3 text-left">
                <p><span class="text-gray-400">Никнейм:</span> <span id="profileNick" class="font-bold text-pink-300">Гость</span></p>
                <p><span class="text-gray-400">⭐ DV поинты:</span> <span id="profileDV" class="font-bold text-pink-300">0</span></p>
                <p><span class="text-gray-400">🎫 Уровень Pass:</span> <span id="profilePassLvl" class="font-bold">1</span>/50</p>
                <p><span class="text-gray-400">🏆 Ранг:</span> <span id="profileRank" class="rank-badge rank-iron">ЖЕЛЕЗО</span></p>
                <p><span class="text-gray-400">⚙️ Активный конфиг:</span> <span id="profileConfig">—</span></p>
                <p><span class="text-gray-400">🎮 Побед в играх:</span> <span id="profileWins">0</span></p>
                <p><span class="text-gray-400">💎 Премиум конфигов:</span> <span id="profilePremiumCount">0</span></p>
                <p><span class="text-gray-400">💎 Наличие DV Pass:</span> <span id="profileHasPass">Нет</span></p>
            </div>
            <button id="dailyBonusBtn" class="btn-primary mt-6 w-full">🎁 ЕЖЕДНЕВНЫЙ БОНУС (+10 DV)</button>
        </div>
    </div>

    <!-- АДМИН ПАНЕЛЬ (РАСШИРЕННАЯ) -->
    <div id="adminPage" class="page">
        <div class="glass-card p-8">
            <h2 class="text-3xl font-bold mb-2">👑 АДМИН ПАНЕЛЬ</h2>
            <p class="text-gray-400 mb-6">Полный контроль над проектом</p>
            
            <div class="grid lg:grid-cols-2 gap-6">
                <!-- Статистика -->
                <div class="glass-card p-4"><h3 class="text-xl mb-3">📊 СТАТИСТИКА</h3><div id="adminStats" class="space-y-2"><p>Загрузка...</p></div></div>
                
                <!-- Список пользователей -->
                <div class="glass-card p-4"><h3 class="text-xl mb-3">👥 ПОЛЬЗОВАТЕЛИ</h3><div id="adminUsersList" class="max-h-60 overflow-y-auto space-y-2"></div></div>
                
                <!-- Выдача DV -->
                <div class="glass-card p-4"><h3 class="text-xl mb-3">💎 ВЫДАТЬ DV</h3><select id="adminUserSelect" class="w-full mb-2"></select><input type="number" id="adminDvAmount" placeholder="Количество DV" class="w-full mb-2"><button id="adminGiveDvBtn" class="btn-primary w-full">ВЫДАТЬ DV</button></div>
                
                <!-- Выдача уровня Pass -->
                <div class="glass-card p-4"><h3 class="text-xl mb-3">🎫 ВЫДАТЬ УРОВЕНЬ PASS</h3><select id="adminUserPassSelect" class="w-full mb-2"></select><input type="number" id="adminPassLevel" placeholder="Уровень 1-50" class="w-full mb-2"><button id="adminSetPassBtn" class="btn-primary w-full">УСТАНОВИТЬ</button></div>
                
                <!-- Выдача DV Pass -->
                <div class="glass-card p-4"><h3 class="text-xl mb-3">🎁 ВЫДАТЬ DV PASS</h3><select id="adminUserGivePassSelect" class="w-full mb-2"></select><button id="adminGivePassBtn" class="btn-primary w-full">ВЫДАТЬ PASS</button></div>
                
                <!-- Выдача конфигов -->
                <div class="glass-card p-4"><h3 class="text-xl mb-3">⚙️ ВЫДАТЬ КОНФИГ</h3><select id="adminUserConfigSelect" class="w-full mb-2"></select><select id="adminConfigSelect" class="w-full mb-2"></select><button id="adminGiveConfigBtn" class="btn-primary w-full">ВЫДАТЬ КОНФИГ</button></div>
                
                <!-- Выдача премиум конфига -->
                <div class="glass-card p-4"><h3 class="text-xl mb-3">💎 ВЫДАТЬ ПРЕМИУМ КОНФИГ</h3><select id="adminUserPremiumSelect" class="w-full mb-2"></select><select id="adminPremiumConfigSelect" class="w-full mb-2"></select><button id="adminGivePremiumBtn" class="btn-gold w-full">ВЫДАТЬ</button></div>
                
                <!-- Глобальные действия -->
                <div class="glass-card p-4"><h3 class="text-xl mb-3">🌍 ГЛОБАЛЬНЫЕ ДЕЙСТВИЯ</h3><button id="adminGiveAllDvBtn" class="btn-secondary w-full mb-2">🎁 ВЫДАТЬ ВСЕМ 50 DV</button><button id="adminResetAllBtn" class="btn-secondary w-full" style="border-color:#ff4466;">⚠️ СБРОС ВСЕХ ДАННЫХ</button></div>
            </div>
        </div>
    </div>
</div>

<!-- МОДАЛКИ -->
<div id="questsModal" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.9); backdrop-filter:blur(10px); z-index:10000; justify-content:center; align-items:center;">
    <div class="glass-card p-6 w-96 text-center"><h3 class="text-xl font-bold mb-3">📋 ЕЖЕДНЕВНЫЕ ЗАДАНИЯ</h3><div id="questListModal" class="space-y-3 mb-4"></div><button id="closeQuestsModal" class="btn-secondary w-full">ЗАКРЫТЬ</button></div>
</div>
<div id="authModal" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.8); backdrop-filter:blur(10px); z-index:10000; justify-content:center; align-items:center;">
    <div class="glass-card p-6 w-96 text-center"><h3 class="text-2xl font-bold mb-3">🔐 ВХОД В АККАУНТ</h3><input id="loginInput" placeholder="Твой никнейм" class="w-full p-3 rounded-xl bg-black/50 mb-3"><button id="doLogin" class="btn-primary w-full py-3">ВОЙТИ</button><button id="closeAuth" class="btn-secondary w-full mt-3">ЗАКРЫТЬ</button></div>
</div>

<script>
    // ========== 32 КОНФИГА ==========
    const regularConfigs = [
        { name: "🧊 КОНФИГ ДИМЫ", bonus: "+50% интеллект", emoji: "🧊", premium: false },
        { name: "🔥 КОНФИГ ВАДИМА", bonus: "+50% сила", emoji: "🔥", premium: false },
        { name: "🌙 НОЧНОЙ ВОЛК", bonus: "+30% скорость", emoji: "🌙", premium: false },
        { name: "☀️ СОЛНЕЧНЫЙ", bonus: "+40% энергия", emoji: "☀️", premium: false },
        { name: "⚡ ГРОЗОВОЙ", bonus: "+50% криты", emoji: "⚡", premium: false },
        { name: "❄️ ЛЕДЯНОЙ ДРАКОН", bonus: "+60% контроль", emoji: "❄️", premium: false },
        { name: "🔥 ОГНЕННЫЙ ФЕНИКС", bonus: "+70% сила", emoji: "🔥", premium: false },
        { name: "💀 ПРИЗРАК", bonus: "+50% невидимость", emoji: "💀", premium: false },
        { name: "🌪️ ВИХРЬ", bonus: "+80% скорость", emoji: "🌪️", premium: false },
        { name: "🛡️ НЕПОБЕДИМЫЙ", bonus: "+90% защита", emoji: "🛡️", premium: false },
        { name: "💎 АЛМАЗНЫЙ", bonus: "+200% удача", emoji: "💎", premium: false },
        { name: "🌀 КОСМИЧЕСКИЙ", bonus: "+150% ко всему", emoji: "🌀", premium: false }
    ];

    const premiumConfigs = [
        { name: "💎 БОЖЕСТВЕННЫЙ", bonus: "+300% ко всем характеристикам", emoji: "👑", premium: true },
        { name: "💎 АБСОЛЮТ", bonus: "+500% сила, бессмертие", emoji: "✨", premium: true },
        { name: "💎 ХРОНОМАГ", bonus: "Контроль времени +200%", emoji: "⏰", premium: true },
        { name: "💎 НЕКРОМАНТ", bonus: "Вампиризм +300%", emoji: "💀", premium: true },
        { name: "💎 АРХАНГЕЛ", bonus: "Исцеление +400%", emoji: "👼", premium: true },
        { name: "💎 ДЕМОН", bonus: "Урон +350%, кровотечение", emoji: "👹", premium: true },
        { name: "💎 ТИТАН", bonus: "Защита +500%", emoji: "🗿", premium: true },
        { name: "💎 ДРАКОНИЙ", bonus: "Огонь +300%, чешуя", emoji: "🐉", premium: true },
        { name: "💎 ЭЛЬДАРИЙ", bonus: "Магия +400%", emoji: "🧝", premium: true },
        { name: "💎 КИБЕР", bonus: "Технологии +350%", emoji: "🤖", premium: true },
        { name: "💎 ПРИМОРДИАЛ", bonus: "Древняя сила +600%", emoji: "🌋", premium: true },
        { name: "💎 ВОИД", bonus: "Тьма +450%", emoji: "🌌", premium: true },
        { name: "💎 ЭФИРНЫЙ", bonus: "Неуязвимость +400%", emoji: "✨", premium: true },
        { name: "💎 ЗЕНИТ", bonus: "Максимальная мощь +700%", emoji: "⭐", premium: true },
        { name: "💎 ОМНИ", bonus: "Всё и везде +1000%", emoji: "🌍", premium: true },
        { name: "💎 АКУМА", bonus: "Проклятие +350%", emoji: "👺", premium: true },
        { name: "💎 РАГНАРОК", bonus: "Разрушение +500%", emoji: "⚔️", premium: true },
        { name: "💎 ВАЛЬКИРИЯ", bonus: "Божественная защита +450%", emoji: "🛡️", premium: true },
        { name: "💎 НОД", bonus: "Высшая сила +800%", emoji: "🔷", premium: true },
        { name: "💎 ЭТЕРНУМ", bonus: "Бесконечность +999%", emoji: "♾️", premium: true }
    ];

    const allConfigs = [...regularConfigs, ...premiumConfigs];

    // НАГРАДЫ PASS (50 уровней)
    const tierRewards = [];
    for(let i=1;i<=50;i++){
        if(i===10) tierRewards.push({ level:10, icon:"🏆", name:"РАНГ БРОНЗА", type:"rank" });
        else if(i===15) tierRewards.push({ level:15, icon:"🏆", name:"РАНГ СЕРЕБРО", type:"rank" });
        else if(i===20) tierRewards.push({ level:20, icon:"🏆", name:"РАНГ ЗОЛОТО", type:"rank" });
        else if(i===25) tierRewards.push({ level:25, icon:"🏆", name:"РАНГ ПЛАТИНА", type:"rank" });
        else if(i===30) tierRewards.push({ level:30, icon:"🏆", name:"РАНГ ДИАМАНТ", type:"rank" });
        else if(i===35) tierRewards.push({ level:35, icon:"🏆", name:"РАНГ МАСТЕР", type:"rank" });
        else if(i===40) tierRewards.push({ level:40, icon:"🏆", name:"РАНГ ГРАНДМАСТЕР", type:"rank" });
        else if(i===45) tierRewards.push({ level:45, icon:"🏆", name:"РАНГ ЛЕГЕНДА", type:"rank" });
        else if(i===50) tierRewards.push({ level:50, icon:"🏆🔥", name:"ЭПИЧЕСКАЯ НАГРАДА", type:"gems", amount:500 });
        else if(i%4===0 && i>=16 && i<=44) tierRewards.push({ level:i, icon:"💎", name:premiumConfigs[Math.floor(i/4)-4]?.name || "ПРЕМИУМ КОНФИГ", type:"config", config:premiumConfigs[Math.floor(i/4)-4]?.name });
        else if(i%5===0 && i<30) tierRewards.push({ level:i, icon:"⚙️", name:regularConfigs[Math.floor(i/5)-1]?.name || "КОНФИГ", type:"config", config:regularConfigs[Math.floor(i/5)-1]?.name });
        else tierRewards.push({ level:i, icon:"💎", name:`${i*2} DV`, type:"gems", amount:i*2 });
    }

    let currentUser = localStorage.getItem("dv_user") || null;
    let users = JSON.parse(localStorage.getItem("dv_users")) || {};
    const ADMIN_NAME = "admin";

    function showToast(msg) { let t=document.createElement("div"); t.className="toast-notify"; t.innerText=msg; document.body.appendChild(t); setTimeout(()=>t.remove(),2500); }
    function saveUsers() { localStorage.setItem("dv_users", JSON.stringify(users)); }

    function getRankName(level){
        if(level>=45) return { name:"ЛЕГЕНДА", class:"rank-legend" };
        if(level>=40) return { name:"ГРАНДМАСТЕР", class:"rank-grandmaster" };
        if(level>=35) return { name:"МАСТЕР", class:"rank-master" };
        if(level>=30) return { name:"ДИАМАНТ", class:"rank-diamond" };
        if(level>=25) return { name:"ПЛАТИНА", class:"rank-platinum" };
        if(level>=20) return { name:"ЗОЛОТО", class:"rank-gold" };
        if(level>=15) return { name:"СЕРЕБРО", class:"rank-silver" };
        if(level>=10) return { name:"БРОНЗА", class:"rank-bronze" };
        return { name:"ЖЕЛЕЗО", class:"rank-iron" };
    }

    function updateUI() {
        if(currentUser && users[currentUser]){
            document.getElementById("openLoginBtn").style.display="none";
            document.getElementById("userNameDisplay").style.display="inline-block";
            document.getElementById("userNameDisplay").innerHTML=`👤 ${currentUser}`;
            document.getElementById("logoutBtn").style.display="inline-block";
            let dv = users[currentUser].dv || 0;
            document.getElementById("globalDV").innerHTML = dv.toFixed(1);
            document.getElementById("profileDV").innerHTML = dv.toFixed(1);
            document.getElementById("profileNick").innerText = currentUser;
            let passLvl = users[currentUser].passLevel || 1;
            document.getElementById("globalPassLevel").innerHTML = `ур.${passLvl}`;
            document.getElementById("profilePassLvl").innerText = passLvl;
            let rank = getRankName(passLvl);
            document.getElementById("rankDisplay").innerHTML = rank.name;
            document.getElementById("rankDisplay").className = `rank-badge ${rank.class}`;
            document.getElementById("rankNamePass") && (document.getElementById("rankNamePass").innerHTML = rank.name);
            document.getElementById("rankNamePass") && (document.getElementById("rankNamePass").className = `rank-badge ${rank.class}`);
            document.getElementById("profileRank").innerHTML = rank.name;
            document.getElementById("profileRank").className = `rank-badge ${rank.class}`;
            document.getElementById("profileConfig").innerText = users[currentUser].activeConfig || "—";
            document.getElementById("profileWins").innerText = users[currentUser].wins || 0;
            let premiumCount = (users[currentUser].passConfigs || []).filter(c => premiumConfigs.some(p => p.name === c)).length;
            document.getElementById("profilePremiumCount").innerText = premiumCount;
            document.getElementById("profileHasPass").innerHTML = users[currentUser].hasPass ? "✅ Да" : "❌ Нет";
            document.getElementById("activeConfigSpan").innerText = users[currentUser].activeConfig || "не выбран";
            if(currentUser === ADMIN_NAME || users[currentUser]?.role === "admin") document.getElementById("adminNavBtn").style.display="inline-block";
            else document.getElementById("adminNavBtn").style.display="none";
            renderConfigs();
            renderTiers();
            renderAdminPanel();
        } else {
            document.getElementById("openLoginBtn").style.display="inline-block";
            document.getElementById("userNameDisplay").style.display="none";
            document.getElementById("logoutBtn").style.display="none";
        }
    }

    function renderConfigs(){
        let container = document.getElementById("configsGrid");
        if(!container) return;
        let active = users[currentUser]?.activeConfig;
        let hasPass = users[currentUser]?.hasPass || false;
        container.innerHTML = "";
        allConfigs.forEach(cfg => {
            let isLocked = cfg.premium && !hasPass;
            let isSelected = (active === cfg.name);
            container.innerHTML += `<div class="glass-card p-3 text-center config-card ${isSelected ? 'selected' : ''}" style="position:relative;" data-name="${cfg.name}">
                ${cfg.premium ? '<div class="premium-badge">💎 PREMIUM</div>' : ''}
                <div class="text-4xl">${cfg.emoji}</div>
                <div class="font-bold text-sm mt-1">${cfg.name}</div>
                <div class="text-xs text-gray-400">${cfg.bonus}</div>
                ${isLocked ? `<div class="text-xs text-pink-300 mt-2">🔒 Требуется DV Pass</div>` : `<button class="btn-secondary text-sm mt-3 w-full equipConfigBtn">ЭКИПИРОВАТЬ</button>`}
            </div>`;
        });
        document.querySelectorAll(".equipConfigBtn").forEach(btn => {
            btn.addEventListener("click", (e) => {
                if(!currentUser){ showToast("Войдите в аккаунт"); return; }
                let card = btn.closest(".config-card");
                let name = card.dataset.name;
                let cfg = allConfigs.find(c => c.name === name);
                if(cfg.premium && !users[currentUser].hasPass){ showToast("❌ Это премиум конфиг! Купи DV Pass чтобы использовать его."); return; }
                users[currentUser].activeConfig = name;
                saveUsers();
                updateUI();
                showToast(`⚙️ Конфиг "${name}" экипирован!`);
            });
        });
    }

    function renderTiers(){
        let container = document.getElementById("tiersGrid");
        if(!container || !currentUser) return;
        let user = users[currentUser];
        let lvl = user.passLevel || 1;
        let hasPass = user.hasPass || false;
        let claimed = user.claimedRewards || [];
        container.innerHTML = "";
        for(let i=0;i<tierRewards.length;i++){
            let r = tierRewards[i];
            let levelNum = i+1;
            let canClaim = (hasPass || levelNum<=10) && levelNum<=lvl && !claimed.includes(levelNum);
            container.innerHTML += `<div class="glass-card p-2 text-center ${claimed.includes(levelNum) ? 'opacity-60' : ''}">
                <div class="w-8 h-8 rounded-full bg-yellow-500 text-black font-bold flex items-center justify-center mx-auto mb-1">${levelNum}</div>
                <div class="text-2xl">${r.icon}</div>
                <div class="text-xs font-bold">${r.name}</div>
                ${canClaim ? `<button class="btn-secondary text-xs mt-2 w-full claimTierBtn" data-level="${levelNum}">ЗАБРАТЬ</button>` : claimed.includes(levelNum) ? `<span class="text-green-400 text-xs">✅</span>` : `<span class="text-gray-500 text-xs">🔒</span>`}
            </div>`;
        }
        let percent = (lvl/50)*100;
        document.getElementById("passFillBar").style.width = `${percent}%`;
        document.getElementById("passFillBar").innerHTML = `УРОВЕНЬ ${lvl} / 50`;
        document.querySelectorAll(".claimTierBtn").forEach(btn=>btn.addEventListener("click",()=>claimReward(parseInt(btn.dataset.level))));
    }

    function claimReward(level){
        let user = users[currentUser];
        let hasPass = user.hasPass;
        if(level>10 && !hasPass){ showToast("❌ Купи DV Pass, чтобы получить эту награду!"); return; }
        let reward = tierRewards[level-1];
        if(reward.type === "gems"){ user.dv = (user.dv||0)+reward.amount; showToast(`💎 +${reward.amount} DV!`); }
        if(reward.type === "config"){ if(!user.passConfigs) user.passConfigs=[]; user.passConfigs.push(reward.config); showToast(`⚙️ Конфиг "${reward.config}" получен!`); }
        if(reward.type === "rank"){ showToast(`🏆 Поздравляем с новым рангом!`); }
        if(!user.claimedRewards) user.claimedRewards=[];
        user.claimedRewards.push(level);
        saveUsers();
        renderTiers();
        updateUI();
    }

    // ЗАДАНИЯ
    const passQuests = [
        { id:0, text:"🏃‍♂️ Сделай 3000 шагов", xp:1 },
        { id:1, text:"😊 Улыбнись 5 раз", xp:1 },
        { id:2, text:"📚 Прочитай 15 страниц", xp:2 },
        { id:3, text:"💪 Сделай 15 отжиманий", xp:2 },
        { id:4, text:"🎮 Сыграй в любую игру", xp:1 }
    ];

    function openQuests(){
        if(!currentUser){ showToast("Войдите в аккаунт"); return; }
        let modal = document.getElementById("questsModal");
        let container = document.getElementById("questListModal");
        let user = users[currentUser];
        let completed = user.completedQuests || [];
        let today = new Date().toDateString();
        if(user.lastQuestDate !== today){ user.completedQuests = []; user.lastQuestDate = today; saveUsers(); completed = []; }
        container.innerHTML = "";
        passQuests.forEach(q => {
            let done = completed.includes(q.id);
            container.innerHTML += `<div class="flex justify-between items-center p-2 bg-white/5 rounded-xl"><span>${q.text} <span class="text-pink-300">(+${q.xp} XP)</span></span>${!done ? `<button class="btn-secondary text-sm doQuestBtn" data-id="${q.id}" data-xp="${q.xp}">✅</button>` : `<span class="text-green-400">✅</span>`}</div>`;
        });
        modal.style.display="flex";
        document.querySelectorAll(".doQuestBtn").forEach(btn => {
            btn.addEventListener("click", () => {
                let qid = parseInt(btn.dataset.id);
                let xp = parseInt(btn.dataset.xp);
                if(!user.completedQuests.includes(qid)){
                    user.completedQuests.push(qid);
                    let lvl = user.passLevel || 1;
                    let prog = (user.passProgress || 0) + xp;
                    let add = 0;
                    while(prog >= 10){ prog -= 10; add++; }
                    user.passLevel = Math.min(lvl + add, 50);
                    user.passProgress = prog;
                    saveUsers();
                    showToast(`✅ Задание выполнено! +${xp} XP`);
                    renderTiers();
                    updateUI();
                    openQuests();
                }
            });
        });
    }

    document.getElementById("getExpBtn")?.addEventListener("click", openQuests);
    document.getElementById("closeQuestsModal")?.addEventListener("click", () => document.getElementById("questsModal").style.display = "none");
    document.getElementById("buyPassBtn")?.addEventListener("click", () => {
        if(!currentUser){ showToast("Войдите"); return; }
        let user = users[currentUser];
        if((user.dv||0) >= 490){
            user.dv -= 490;
            user.hasPass = true;
            saveUsers();
            updateUI();
            showToast("🎉 DV Pass активирован! Теперь доступны премиум конфиги и все 50 уровней!");
        } else showToast("❌ Не хватает DV! Нужно 490 DV");
    });

    // ========== МИНИ-ИГРЫ ==========
    // 1. Угадай число
    document.getElementById("playGuessBtn")?.addEventListener("click", () => {
        if(!currentUser){ showToast("Войдите"); return; }
        let user = users[currentUser];
        let guess = parseInt(document.getElementById("guessNumber").value);
        if(isNaN(guess) || guess<1 || guess>10){ showToast("Число 1-10"); return; }
        if((user.dv||0) < 10){ showToast("Нужно 10 DV"); return; }
        user.dv -= 10;
        let rand = Math.floor(Math.random()*10)+1;
        if(guess === rand){
            user.dv += 30;
            user.wins = (user.wins||0)+1;
            document.getElementById("guessResult").innerHTML = `🎉 Победа! +30 DV`;
            showToast(`🎉 Угадал! +30 DV`);
        } else {
            document.getElementById("guessResult").innerHTML = `❌ Было ${rand}. -10 DV`;
            showToast(`❌ Не угадал`);
        }
        saveUsers(); updateUI();
    });

    // 2. Автокликер
    let clickerActive = false, clickCount = 0, clickTimer;
    function startClicker() {
        if(clickerActive) return;
        if(!currentUser){ showToast("Войдите"); return; }
        clickCount = 0;
        document.getElementById("clickerScore").innerText = "0";
        document.getElementById("clickerResult").innerHTML = "";
        clickerActive = true;
        let timeLeft = 10;
        let timerDiv = document.getElementById("clickerTimer");
        let clickBtn = document.getElementById("startClickerBtn");
        clickBtn.innerText = "🔴 КЛИКАЙ СЮДА! 0.1 DV/клик 🔴";
        let clickHandler = () => { if(clickerActive){ clickCount++; document.getElementById("clickerScore").innerText = clickCount; } };
        clickBtn.addEventListener("click", clickHandler);
        clickTimer = setInterval(() => {
            timeLeft--;
            timerDiv.innerText = `⏰ ${timeLeft} сек`;
            if(timeLeft <= 0){
                clearInterval(clickTimer);
                clickerActive = false;
                let reward = clickCount * 0.1;
                users[currentUser].dv = (users[currentUser].dv || 0) + reward;
                users[currentUser].wins = (users[currentUser].wins || 0) + 1;
                saveUsers(); updateUI();
                document.getElementById("clickerResult").innerHTML = `📊 ${clickCount} кликов | +${reward.toFixed(1)} DV!`;
                timerDiv.innerText = "";
                clickBtn.innerText = "🔴 НАЧАТЬ КЛИКАТЬ";
                clickBtn.removeEventListener("click", clickHandler);
                showToast(`Автокликер: +${reward.toFixed(1)} DV`);
            }
        }, 1000);
    }
    document.getElementById("startClickerBtn")?.addEventListener("click", startClicker);

    // 3. КНБ
    document.querySelectorAll(".rpsBtn").forEach(btn => {
        btn.addEventListener("click", () => {
            if(!currentUser){ showToast("Войдите"); return; }
            let user = users[currentUser];
            let choices = { rock:"✊", paper:"✋", scissors:"✌️" };
            let userChoice = btn.dataset.choice;
            let botChoice = ["rock","paper","scissors"][Math.floor(Math.random()*3)];
            if(userChoice === botChoice){
                document.getElementById("rpsResult").innerHTML = `🤝 Ничья!`;
            } else if((userChoice==="rock" && botChoice==="scissors") || (userChoice==="paper" && botChoice==="rock") || (userChoice==="scissors" && botChoice==="paper")){
                user.dv = (user.dv||0) + 15;
                user.wins = (user.wins||0)+1;
                saveUsers(); updateUI();
                document.getElementById("rpsResult").innerHTML = `🎉 Победа! +15 DV!`;
                showToast(`Победа в КНБ! +15 DV`);
            } else {
                document.getElementById("rpsResult").innerHTML = `💀 Поражение`;
                showToast(`Поражение в КНБ`);
            }
        });
    });

    // 4. Орёл-решка
    document.querySelectorAll(".coinBtn").forEach(btn => {
        btn.addEventListener("click", () => {
            if(!currentUser){ showToast("Войдите"); return; }
            let user = users[currentUser];
            if((user.dv||0) < 5){ showToast("Нужно 5 DV"); return; }
            user.dv -= 5;
            let side = Math.random() < 0.5 ? "eagle" : "tails";
            let userSide = btn.dataset.side;
            if(side === userSide){
                user.dv += 12;
                user.wins = (user.wins||0)+1;
                document.getElementById("coinResult").innerHTML = `🪙 Победа! +12 DV`;
                showToast(`Победа! +12 DV`);
            } else {
                document.getElementById("coinResult").innerHTML = `🪙 Поражение -5 DV`;
                showToast(`Поражение`);
            }
            saveUsers(); updateUI();
        });
    });

    // 5. Блэкджек
    document.getElementById("playBlackjackBtn")?.addEventListener("click", () => {
        if(!currentUser){ showToast("Войдите"); return; }
        let user = users[currentUser];
        if((user.dv||0) < 15){ showToast("Нужно 15 DV"); return; }
        user.dv -= 15;
        let playerCard = Math.floor(Math.random()*10)+1;
        let dealerCard = Math.floor(Math.random()*10)+1;
        if(playerCard > dealerCard){
            user.dv += 40;
            user.wins = (user.wins||0)+1;
            document.getElementById("bjResult").innerHTML = `🎉 Победа! +40 DV`;
            showToast(`Победа в блэкджеке! +40 DV`);
        } else {
            document.getElementById("bjResult").innerHTML = `💀 Поражение! -15 DV`;
            showToast(`Поражение в блэкджеке`);
        }
        saveUsers(); updateUI();
    });

    // 6. Кости
    document.getElementById("playDiceBtn")?.addEventListener("click", () => {
        if(!currentUser){ showToast("Войдите"); return; }
        let user = users[currentUser];
        if((user.dv||0) < 8){ showToast("Нужно 8 DV"); return; }
        user.dv -= 8;
        let dice1 = Math.floor(Math.random()*6)+1;
        let dice2 = Math.floor(Math.random()*6)+1;
        let sum = dice1 + dice2;
        if(sum >= 7){
            user.dv += 25;
            user.wins = (user.wins||0)+1;
            document.getElementById("diceResult").innerHTML = `🎲 ${dice1}+${dice2}=${sum} | Победа! +25 DV`;
            showToast(`Победа в костях! +25 DV`);
        } else {
            document.getElementById("diceResult").innerHTML = `🎲 ${dice1}+${dice2}=${sum} | Поражение -8 DV`;
            showToast(`Поражение в костях`);
        }
        saveUsers(); updateUI();
    });

    // Ежедневный бонус
    document.getElementById("dailyBonusBtn")?.addEventListener("click", () => {
        if(!currentUser){ showToast("Войдите"); return; }
        let today = new Date().toDateString();
        let user = users[currentUser];
        if(user.lastDaily !== today){
            user.dv = (user.dv||0) + 10;
            user.lastDaily = today;
            saveUsers();
            updateUI();
            showToast("🎁 Ежедневный бонус: +10 DV!");
        } else showToast("⏳ Бонус уже получен сегодня");
    });

    // РАСШИРЕННАЯ АДМИН ПАНЕЛЬ
    function renderAdminPanel(){
        if(!currentUser || (currentUser !== ADMIN_NAME && users[currentUser]?.role !== "admin")) return;
        let userList = Object.keys(users);
        let container = document.getElementById("adminUsersList");
        let statsDiv = document.getElementById("adminStats");
        let selects = ["adminUserSelect","adminUserPassSelect","adminUserGivePassSelect","adminUserConfigSelect","adminUserPremiumSelect"];
        selects.forEach(id => { let sel = document.getElementById(id); if(sel){ sel.innerHTML = ""; userList.forEach(u => { sel.innerHTML += `<option value="${u}">${u}</option>`; }); } });
        
        if(container) container.innerHTML = userList.map(u => `<div class="glass-card p-2 flex justify-between"><span>${u}</span><span>⭐ ${(users[u].dv||0).toFixed(1)} DV | ур.${users[u].passLevel||1} | ${users[u].hasPass ? "💎 PASS" : ""}</span></div>`).join("");
        
        let totalDV = userList.reduce((sum,u)=> sum + (users[u].dv||0), 0);
        let totalWins = userList.reduce((sum,u)=> sum + (users[u].wins||0), 0);
        let passOwners = userList.filter(u => users[u].hasPass).length;
        if(statsDiv) statsDiv.innerHTML = `<p>👥 Всего игроков: <span class="text-pink-300 font-bold">${userList.length}</span></p><p>⭐ Общий DV: <span class="text-pink-300 font-bold">${totalDV.toFixed(1)}</span></p><p>🎮 Всего побед: <span class="text-pink-300 font-bold">${totalWins}</span></p><p>💎 Владельцев Pass: <span class="text-pink-300 font-bold">${passOwners}</span></p>`;
        
        let premiumSelect = document.getElementById("adminPremiumConfigSelect");
        if(premiumSelect){ premiumSelect.innerHTML = ""; premiumConfigs.forEach(c => { premiumSelect.innerHTML += `<option value="${c.name}">${c.name}</option>`; }); }
        let configSelect = document.getElementById("adminConfigSelect");
        if(configSelect){ configSelect.innerHTML = ""; allConfigs.forEach(c => { configSelect.innerHTML += `<option value="${c.name}">${c.name}</option>`; }); }
    }

    document.getElementById("adminGiveDvBtn")?.addEventListener("click", () => { let u=document.getElementById("adminUserSelect").value, am=parseFloat(document.getElementById("adminDvAmount").value); if(users[u]){ users[u].dv=(users[u].dv||0)+am; saveUsers(); renderAdminPanel(); updateUI(); showToast(`✅ Выдано ${am} DV пользователю ${u}`); } });
    document.getElementById("adminSetPassBtn")?.addEventListener("click", () => { let u=document.getElementById("adminUserPassSelect").value, lvl=parseInt(document.getElementById("adminPassLevel").value); if(users[u] && lvl>=1 && lvl<=50){ users[u].passLevel=lvl; saveUsers(); updateUI(); showToast(`✅ Уровень Pass ${lvl} установлен ${u}`); } });
    document.getElementById("adminGivePassBtn")?.addEventListener("click", () => { let u=document.getElementById("adminUserGivePassSelect").value; if(users[u]){ users[u].hasPass=true; saveUsers(); updateUI(); showToast(`✅ DV Pass выдан ${u}`); } });
    document.getElementById("adminGiveConfigBtn")?.addEventListener("click", () => { let u=document.getElementById("adminUserConfigSelect").value, cfg=document.getElementById("adminConfigSelect").value; if(users[u]){ if(!users[u].passConfigs) users[u].passConfigs=[]; users[u].passConfigs.push(cfg); saveUsers(); showToast(`✅ Конфиг "${cfg}" выдан ${u}`); } });
    document.getElementById("adminGivePremiumBtn")?.addEventListener("click", () => { let u=document.getElementById("adminUserPremiumSelect").value, cfg=document.getElementById("adminPremiumConfigSelect").value; if(users[u]){ if(!users[u].passConfigs) users[u].passConfigs=[]; users[u].passConfigs.push(cfg); saveUsers(); showToast(`✅ Премиум конфиг "${cfg}" выдан ${u}`); } });
    document.getElementById("adminGiveAllDvBtn")?.addEventListener("click", () => { Object.keys(users).forEach(u => { users[u].dv = (users[u].dv||0) + 50; }); saveUsers(); renderAdminPanel(); updateUI(); showToast("✅ Всем выдано 50 DV"); });
    document.getElementById("adminResetAllBtn")?.addEventListener("click", () => { if(confirm("⚠️ ВСЕ ДАННЫЕ БУДУТ УДАЛЕНЫ!")){ localStorage.clear(); location.reload(); } });

    // АВТОРИЗАЦИЯ
    const authModal = document.getElementById("authModal");
    document.getElementById("openLoginBtn")?.addEventListener("click", () => authModal.style.display = "flex");
    document.getElementById("closeAuth")?.addEventListener("click", () => authModal.style.display = "none");
    document.getElementById("doLogin")?.addEventListener("click", () => {
        let name = document.getElementById("loginInput").value.trim();
        if(!name){ showToast("Введите никнейм"); return; }
        if(!users[name]) users[name] = { dv: 50, role: (name===ADMIN_NAME ? "admin" : "user"), passLevel: 1, passProgress: 0, hasPass: false, claimedRewards: [], wins: 0, activeConfig: null, completedQuests: [], passConfigs: [] };
        currentUser = name;
        localStorage.setItem("dv_user", currentUser);
        saveUsers();
        authModal.style.display = "none";
        updateUI();
        showToast(`✨ Добро пожаловать, ${name}! ✨`);
    });
    document.getElementById("logoutBtn")?.addEventListener("click", () => { currentUser = null; localStorage.removeItem("dv_user"); updateUI(); showToast("👋 Вы вышли"); });

    document.querySelectorAll(".nav-btn").forEach(btn => {
        btn.addEventListener("click", () => {
            let page = btn.dataset.page + "Page";
            document.querySelectorAll(".page").forEach(p => p.classList.remove("active-page"));
            document.getElementById(page).classList.add("active-page");
            document.querySelectorAll(".nav-btn").forEach(n => n.classList.remove("active"));
            btn.classList.add("active");
            if(page === "adminPage" && currentUser !== ADMIN_NAME && users[currentUser]?.role !== "admin"){ showToast("⛔ Доступ ограничен!"); document.getElementById("homePage").classList.add("active-page"); }
            if(page === "adminPage") renderAdminPanel();
        });
    });

    document.getElementById("toPassBtn")?.addEventListener("click", () => document.querySelector("[data-page='pass']").click());
    document.getElementById("toGamesBtn")?.addEventListener("click", () => document.querySelector("[data-page='games']").click());
    document.getElementById("toAboutBtn")?.addEventListener("click", () => document.querySelector("[data-page='about']").click());

    for(let i=0;i<150;i++){ let s=document.createElement("span"); s.style.left=Math.random()*100+"%"; s.style.animationDelay=Math.random()*20+"s"; s.style.animationDuration=10+Math.random()*15+"s"; document.getElementById("bg").appendChild(s); }

    if(users[ADMIN_NAME]) users[ADMIN_NAME].role = "admin";
    saveUsers();
    updateUI();
</script>
</body>
</html>
