<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chicken Clicker BETA v1.2</title>
    <style>
        body { 
            background: #111; color: white; text-align: center; 
            font-family: sans-serif; user-select: none; 
        }
        .stats { font-size: 32px; margin: 20px; color: #0fa; font-weight: bold; }
        .screen { display: none; padding: 20px; }
        .active { display: block; }
        
        #chicken-img { 
            width: 180px; cursor: pointer; transition: 0.1s; 
            background: #222; border-radius: 50%; padding: 10px;
        }
        #chicken-img:active { transform: scale(0.9); }

        .menu-btn { 
            display: block; width: 220px; padding: 15px; margin: 10px auto; 
            background: #333; border: 2px solid #0fa; color: white; 
            font-weight: bold; cursor: pointer; border-radius: 10px;
        }
        .item-box { 
            border: 1px solid #444; padding: 15px; margin: 10px; 
            display: flex; justify-content: space-between; align-items: center; 
            background: #1a1a1a; border-radius: 8px;
        }
        .buy-btn { background: #0fa; border: none; padding: 8px 15px; cursor: pointer; font-weight: bold; }
        .buy-btn:disabled { background: #444; cursor: not-allowed; }
        
        .promo-section { margin: 20px; padding: 15px; border-top: 1px solid #333; }
        input { padding: 10px; border-radius: 5px; border: none; width: 120px; }
    </style>
</head>
<body>

    <div class="stats">🪙 Коіни: <span id="coins">0</span></div>

    <div id="main" class="screen active">
        <div id="click-power-text" style="color: #00f2ff; margin-bottom: 10px;">Клік: +1</div>
        <img id="chicken-img" src="https://img.icons8.com/color/200/chicken.png" onclick="clickChicken()">
        
        <button class="menu-btn" onclick="show('shop')">МАГАЗИН ⚔️</button>
        <button class="menu-btn" onclick="show('inv')">РЮКЗАК 🎒</button>
        <button class="menu-btn" onclick="show('prof')">ПРОФІЛЬ 👤</button>

        <div class="promo-section">
            <input type="text" id="promo-input" placeholder="ПРОМОКОД">
            <button class="buy-btn" onclick="checkPromo()">OK</button>
        </div>
        <p style="color: #555;">YouTube: @pro48k_bs</p>
    </div>

    <div id="shop" class="screen">
        <h2>ПРОКАЧКА ТА ЗБРОЯ</h2>
        
        <div class="item-box">
            <span>Сила кліку +1 (50 🪙)</span>
            <button class="buy-btn" onclick="buyUpgrade(50)">КУПИТИ</button>
        </div>

        <div class="item-box">
            <span>Ніж (100 🪙)</span>
            <button class="buy-btn" onclick="buyItem('Ніж', 100)">КУПИТИ</button>
        </div>

        <button class="menu-btn" style="border-color: red;" onclick="show('main')">НАЗАД</button>
    </div>

    <div id="inv" class="screen">
        <h2>ТВІЙ РЮКЗАК</h2>
        <div id="inv-list" style="margin: 20px; font-size: 18px;">Порожньо</div>
        <button class="menu-btn" style="border-color: red;" onclick="show('main')">НАЗАД</button>
    </div>

    <div id="prof" class="screen">
        <h2>ТВІЙ ПРОФІЛЬ</h2>
        <div style="font-size: 20px; margin: 10px;">Всього кліків: <span id="total-clicks">0</span></div>
        <div style="font-size: 20px; margin: 10px;">Звання: <span id="rank">Новачок</span></div>
        <button class="menu-btn" style="border-color: red;" onclick="show('main')">НАЗАД</button>
    </div>

    <script>
        let coins = 0;
        let totalClicks = 0;
        let clickPower = 1;
        let inventory = [];
        let usedPromo = false;

        function clickChicken() {
            coins += clickPower;
            totalClicks++;
            updateDisplay();
        }
        function updateDisplay() {
            document.getElementById('coins').innerText = coins;
            document.getElementById('total-clicks').innerText = totalClicks;
            document.getElementById('click-power-text').innerText = "Клік: +" + clickPower;
            
            let rank = "Новачок";
            if(totalClicks > 100) rank = "Клікер-аматор";
            if(totalClicks > 500) rank = "Майстер курки";
            document.getElementById('rank').innerText = rank;
        }

        function show(id) {
            document.getElementById('main').style.display = 'none';
            document.getElementById('shop').style.display = 'none';
            document.getElementById('inv').style.display = 'none';
            document.getElementById('prof').style.display = 'none';
            document.getElementById(id).style.display = 'block';
            if(id === 'inv') updateInv();
        }

        // КУПІВЛЯ ПРОКАЧКИ
        function buyUpgrade(price) {
            if(coins >= price) {
                coins -= price;
                clickPower++;
                updateDisplay();
                alert("Сила кліку збільшена!");
            } else {
                alert("Мало коїнів!");
            }
        }

        function buyItem(name, price) {
            if(coins >= price) {
                coins -= price;
                inventory.push(name);
                updateDisplay();
                alert("Куплено: " + name);
            } else {
                alert("Мало коїнів!");
            }
        }

        function updateInv() {
            let list = document.getElementById('inv-list');
            list.innerText = inventory.length === 0 ? "Порожньо" : inventory.join(', ');
        }

        // ПРОМОКОД
        function checkPromo() {
            let input = document.getElementById('promo-input').value.toUpperCase();
            if(usedPromo) {
                alert("Ти вже використав промокод!");
                return;
            }
            if(input === "PRO48K") {
                coins += 5000;
                usedPromo = true;
                updateDisplay();
                alert("Успіх! +5000 коїнів 🪙");
                document.getElementById('promo-input').value = "";
            } else {
                alert("Невірний код!");
            }
        }
    </script>
</body>
</html>
