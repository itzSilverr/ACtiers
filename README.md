[Ac.html.html](https://github.com/user-attachments/files/29149874/Ac.html.html)
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ACTIERS Dashboard</title>
    <style>
        /* ==================== 1. تصميم الألوان والثيم الخورافي (CSS) ==================== */
        :root {
            --bg-color: #0d121a;
            --card-bg: #141b26;
            --accent-color: #ffaa00;
            --text-main: #ffffff;
            --text-muted: #62728a;
            --border-color: #1e293b;
            --tab-active: #1e293b;
            --na-color: #ff4757;
            --eu-color: #2ed573;
            --delete-color: #ff4757;
        }

        body {
            margin: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            direction: rtl;
        }

        /* الهيدر العلوي */
        header {
            background-color: var(--card-bg);
            padding: 15px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--border-color);
        }

        .logo {
            font-size: 24px;
            font-weight: bold;
            color: var(--accent-color);
            letter-spacing: 1px;
        }

        /* لوحة التحكم لإضافة اللاعبين */
        .admin-panel {
            background: linear-gradient(135deg, #1a2333, #141b26);
            margin: 30px auto;
            padding: 25px;
            border-radius: 12px;
            max-width: 900px;
            box-shadow: 0 8px 24px rgba(0,0,0,0.3);
            border: 1px solid var(--border-color);
        }

        .admin-panel h2 {
            margin-top: 0;
            color: var(--text-main);
            font-size: 20px;
            margin-bottom: 20px;
        }

        .form-group {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }

        .admin-auth-box {
            width: 100%;
            margin-bottom: 15px;
            border-bottom: 1px dashed var(--border-color);
            padding-bottom: 15px;
        }

        input, select {
            background-color: var(--bg-color);
            border: 1px solid var(--border-color);
            color: var(--text-main);
            padding: 12px 20px;
            border-radius: 8px;
            font-size: 15px;
            flex: 1;
            min-width: 150px;
            outline: none;
            transition: 0.3s;
        }

        input:focus, select:focus {
            border-color: var(--accent-color);
        }

        input.auth-email {
            border-color: rgba(255, 170, 0, 0.4);
        }

        button {
            background-color: var(--accent-color);
            color: #000;
            font-weight: bold;
            border: none;
            padding: 12px 30px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            transition: 0.3s;
        }

        button:hover {
            background-color: #e09500;
            transform: translateY(-2px);
        }

        /* حاوية الترتيب */
        .rankings-container {
            max-width: 950px;
            margin: 0 auto 50px auto;
            background-color: var(--card-bg);
            border-radius: 12px;
            padding: 20px;
            border: 1px solid var(--border-color);
        }

        /* التبويبات العلوية */
        .tabs-container {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 15px;
            overflow-x: auto;
        }

        .tab {
            padding: 10px 20px;
            border-radius: 20px;
            background-color: transparent;
            color: var(--text-muted);
            font-weight: 600;
            font-size: 14px;
            cursor: pointer;
        }

        .tab.active {
            background-color: var(--tab-active);
            color: var(--text-main);
            border: 1px solid var(--accent-color);
        }

        /* رسالة القائمة الفارغة */
        .empty-message {
            text-align: center;
            padding: 40px;
            color: var(--text-muted);
            font-size: 16px;
            border: 2px dashed var(--border-color);
            border-radius: 8px;
        }

        /* قائمة الأسطر */
        .player-list {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .player-row {
            display: flex;
            align-items: center;
            background-color: rgba(255, 255, 255, 0.02);
            border-radius: 8px;
            padding: 15px 20px;
            border: 1px solid transparent;
            transition: 0.2s;
        }

        .player-row:hover {
            border-color: rgba(255, 170, 0, 0.3);
            background-color: rgba(255, 255, 255, 0.04);
        }

        .player-rank {
            font-size: 24px;
            font-weight: 900;
            font-style: italic;
            width: 50px;
            color: var(--text-muted);
            direction: ltr;
            text-align: right;
        }

        .player-list .player-row:nth-child(1) .player-rank { color: #ffaa00; }
        .player-list .player-row:nth-child(2) .player-rank { color: #cccccc; }
        .player-list .player-row:nth-child(3) .player-rank { color: #cd7f32; }

        /* سكن ماين كرافت */
        .player-avatar {
            width: 48px;
            height: 48px;
            border-radius: 6px;
            margin-left: 20px;
            background-color: #222;
            image-rendering: pixelated; 
            border: 2px solid var(--border-color);
        }

        .player-info {
            flex: 2;
            display: flex;
            flex-direction: column;
            gap: 4px;
            text-align: right;
        }

        .player-name {
            font-size: 18px;
            font-weight: bold;
            color: var(--text-main);
        }

        .player-title {
            font-size: 13px;
            color: var(--accent-color);
        }

        .player-points {
            color: var(--text-muted);
            font-size: 12px;
        }

        .player-region {
            padding: 5px 12px;
            border-radius: 6px;
            font-weight: bold;
            font-size: 14px;
            margin-left: 20px;
            min-width: 35px;
            text-align: center;
        }

        .region-na { background-color: rgba(255, 71, 87, 0.2); color: var(--na-color); }
        .region-eu { background-color: rgba(46, 213, 115, 0.2); color: var(--eu-color); }

        .player-tier {
            background-color: #1e293b;
            padding: 6px 15px;
            border-radius: 20px;
            font-size: 13px;
            font-weight: bold;
            color: #ffaa00;
            border: 1px solid rgba(255, 170, 0, 0.2);
            margin-left: 20px;
        }

        /* زر الحذف */
        .btn-delete {
            background-color: rgba(255, 71, 87, 0.1);
            color: var(--delete-color);
            border: 1px solid rgba(255, 71, 87, 0.3);
            padding: 6px 12px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 12px;
            font-weight: bold;
            transition: 0.2s;
        }

        .btn-delete:hover {
            background-color: var(--delete-color);
            color: #fff;
        }
    </style>
</head>
<body>

    <!-- ==================== 2. هيكل الصفحة (HTML) ==================== -->
    <header>
        <div class="logo">ACTIERS</div>
        <div style="color: var(--text-muted); font-size: 14px;">لوحة الترتيب الرسمية المربوطة بماين كرافت</div>
    </header>

    <!-- لوحة التحكم للآدمين بحماية الجيميل الخاص بك -->
    <div class="admin-panel">
        <div class="admin-auth-box">
            <h2>🔐 التحقق من المتحكم بالمنصة</h2>
            <input type="email" id="adminEmail" class="auth-email" placeholder="أدخل بريدك الإلكتروني (Gmail) الخاص بالتحكم..." required>
        </div>

        <h2>⚡ إضافة لاعب للترتيب وتحديث السكنات</h2>
        <div class="form-group">
            <input type="text" id="playerName" placeholder="اسم لاعب ماين كرافت (الـ Username)..." required>
            <input type="number" id="playerPoints" placeholder="النقاط (مثال: 420)..." required>
            
            <select id="playerRegion">
                <option value="NA">NA (أمريكا الشمالية)</option>
                <option value="EU">EU (أوروبا)</option>
            </select>

            <select id="playerTier">
                <option value="HT1">HT1 (Combat Master)</option>
                <option value="LT1">LT1</option>
                <option value="HT2">HT2</option>
                <option value="LT2">LT2</option>
            </select>

            <button onclick="addPlayer()">إضافة للترتيب ➕</button>
        </div>
    </div>

    <!-- لوحة عرض الترتيب -->
    <div class="rankings-container">
        <div class="tabs-container">
            <div class="tab active">Overall</div>
            <div class="tab">Vanilla</div>
            <div class="tab">UHC</div>
            <div class="tab">Pot</div>
            <div class="tab">Sword</div>
        </div>

        <div class="player-list" id="playerList">
            <div class="empty-message" id="emptyMessage">القائمة فارغة! يرجى إدخال الجيميل المعتمد بالأعلى للبدء بإضافة اللاعبين...</div>
        </div>
    </div>

    <!-- ==================== 3. منطق التحكم وحماية الإيميل (JavaScript) ==================== -->
    <script>
        // 🔒 تم ربط السطر بإيميلك الشخصي بنجاح
        const ADMIN_GMAIL = "silveryassin38@gmail.com"; 

        let players = [];

        // دالة التحقق من صلاحية الجيميل
        function checkAuthorization() {
            const emailInput = document.getElementById('adminEmail').value.trim().toLowerCase();
            if (emailInput !== ADMIN_GMAIL.toLowerCase()) {
                alert('🛑 خطأ: غير مصرح لك بالتحكم! الإيميل المدخل لا يطابق إيميل مالك الموقع.');
                return false;
            }
            return true;
        }

        // دالة تحديث قائمة الترتيب
        function renderPlayers() {
            const listElement = document.getElementById('playerList');
            const emptyMessage = document.getElementById('emptyMessage');
            
            if (players.length === 0) {
                listElement.innerHTML = '';
                listElement.appendChild(emptyMessage);
                emptyMessage.style.display = 'block';
                return;
            } else {
                emptyMessage.style.display = 'none';
                listElement.innerHTML = '';
            }

            // ترتيب تنازلي حسب نقاط ماين كرافت
            players.sort((a, b) => b.points - a.points);

            players.forEach((player, index) => {
                const avatarUrl = `https://crafatar.com/avatars/${player.name}?size=100&overlay`;

                const rowHtml = `
                    <div class="player-row">
                        <div class="player-rank">#${index + 1}</div>
                        <img class="player-avatar" src="${avatarUrl}" alt="${player.name}" onerror="this.src='https://crafatar.com/avatars/steve?size=100'">
                        
                        <div class="player-info">
                            <span class="player-name">${player.name}</span>
                            <span class="player-title">🔶 ${player.title} <span class="player-points">(${player.points} points)</span></span>
                        </div>

                        <div class="player-region region-${player.region.toLowerCase()}">${player.region}</div>
                        <div class="player-tier">${player.tier}</div>
                        
                        <button class="btn-delete" onclick="deletePlayer(${player.id})">حذف ❌</button>
                    </div>
                `;
                listElement.innerHTML += rowHtml;
            });
        }

        // دالة إضافة لاعب جديد (مشروطة بالإيميل)
        function addPlayer() {
            if (!checkAuthorization()) return;

            const nameInput = document.getElementById('playerName');
            const pointsInput = document.getElementById('playerPoints');
            const regionInput = document.getElementById('playerRegion');
            const tierInput = document.getElementById('playerTier');

            if (nameInput.value.trim() === '' || pointsInput.value === '') {
                alert('الرجاء تعبئة اسم الحساب والنقاط!');
                return;
            }

            let title = "Combat Competitor";
            if(tierInput.value === "HT1") title = "Combat Master";
            if(tierInput.value === "LT1") title = "Combat Elite";

            const newPlayer = {
                id: Date.now(),
                name: nameInput.value.trim(),
                points: parseInt(pointsInput.value),
                region: regionInput.value,
                tier: tierInput.value,
                title: title
            };

            players.push(newPlayer);
            renderPlayers();

            nameInput.value = '';
            pointsInput.value = '';
        }

        // دالة الحذف (مشروطة بالإيميل)
        function deletePlayer(id) {
            if (!checkAuthorization()) return;

            players = players.filter(player => player.id !== id);
            renderPlayers();
        }

        window.onload = renderPlayers;
    </script>
</body>
</html>
