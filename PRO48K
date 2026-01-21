<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Chicken Test</title>
    <style>
        body { background: #111; color: white; text-align: center; font-family: sans-serif; user-select: none; }
        .stat { font-size: 30px; margin: 20px; color: gold; }
        .screen { display: none; padding: 20px; }
        .active { display: block; }
        #chick { width: 150px; cursor: pointer; border-radius: 50%; background: #222; padding: 10px; }
        .btn { 
            display: block; width: 200px; padding: 15px; margin: 10px auto; 
            background: #444; border: 2px solid #0fa; color: white; font-weight: bold; 
        }
    </style>
</head>
<body>

    <div class="stat">Коіни: <span id="c">0</span></div>

    <div id="s1" class="screen active">
        <img id="chick" src="https://img.icons8.com/color/200/chicken.png" onclick="klick()">
        <button class="btn" onclick="nav('s2')">МАГАЗИН ⚔️</button>
        <button class="btn" onclick="nav('s3')">ПРОФІЛЬ 👤</button>
    </div>

    <div id="s2" class="screen">
        <h2>МАГАЗИН</h2>
        <button class="btn" onclick="buyItem()">КУПИТИ НІЖ (10 🪙)</button>
        <button class="btn" style="border-color: red;" onclick="nav('s1')">НАЗАД</button>
    </div>

    <div id="s3" class="screen">
        <h2>ПРОФІЛЬ</h2>
        <p id="p_stat">Кліків: 0</p>
        <button class="btn" style="border-color: red;" onclick="nav('s1')">НАЗАД</button>
    </div>

    <script>
        // ТИМЧАСОВІ ЗМІННІ БЕЗ ЗБЕРЕЖЕННЯ (ДЛЯ ТЕСТУ)
        let coins = 0;
        let clicks = 0;

        function klick() {
            coins = coins + 1;
            clicks = clicks + 1;
            document.getElementById('c').innerText = coins;
            console.log("Клік спрацював! Коінів:", coins);
        }

        function nav(id) {
            // Ховаємо всі екрани
            document.getElementById('s1').style.display = 'none';
            document.getElementById('s2').style.display = 'none';
            document.getElementById('s3').style.display = 'none';
            
            // Показуємо потрібний
            document.getElementById(id).style.display = 'block';
            
            if(id === 's3') {
                document.getElementById('p_stat').innerText = "Кліків: " + clicks;
            }
        }

        function buyItem() {
            if(coins >= 10) {
                coins = coins - 10;
                document.getElementById('c').innerText = coins;
                alert("Куплено!");
            } else {
                alert("Немає грошей!");
            }
        }
    </script>
</body>
</html>
