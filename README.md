<html lang="uk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Chicken Clicker v1.9 - Neon</title>

<style>
body{
    background:#111;
    color:#0fa;
    text-align:center;
    font-family:sans-serif;
    user-select:none;
}

.neon-text {
    font-weight: bold;
    font-size: 26px;
    background: linear-gradient(270deg, #0ff, #f0f, #0ff);
    background-size: 600% 600%;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: neonGradient 3s ease infinite;
    text-shadow: 0 0 5px #0ff, 0 0 10px #f0f, 0 0 20px #0ff;
}

@keyframes neonGradient {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
}

.screen{display:none;padding:20px;}
.active{display:block;}

#chicken-img{
    width:170px;
    cursor:pointer;
    transition:0.1s;
    background:#222;
    border-radius:50%;
    padding:10px;
    box-shadow: 0 0 10px #0ff, 0 0 20px #0ff, 0 0 40px #0ff;
}
#chicken-img:active{transform:scale(0.9);}

.menu-btn{
    display:block;
    width:240px;
    padding:14px;
    margin:8px auto;
    background:#333;
    border:2px solid #0fa;
    color:#0ff;
    font-weight:bold;
    border-radius:10px;
    font-size:17px;
    text-shadow:0 0 5px #0ff, 0 0 10px #f0f;
    cursor:pointer;
}
.menu-btn:hover, .buy-btn:hover {
    box-shadow: 0 0 10px #0ff, 0 0 20px #f0f;
    transform: scale(1.05);
}

.item-box{
    border:1px solid #444;
    padding:14px;
    margin:10px auto;
    background:#1a1a1a;
    border-radius:8px;
    display:flex;
    justify-content:space-between;
    align-items:center;
    max-width:90%;
}

.buy-btn{
    background:#0fa;
    border:none;
    padding:8px 14px;
    font-weight:bold;
    border-radius:6px;
    color:#000;
    cursor:pointer;
}

input{
    font-size:16px;
}
</style>
</head>

<body>

<div class="stats neon-text">🪙 Коіни: <span id="coins">0</span></div>

<!-- MAIN -->
<div id="main" class="screen active">
    <h2 class="neon-text">Chicken Clicker v1.9</h2>
    <div id="click-power-text" class="neon-text">Клік: +1</div>
    <img id="chicken-img" src="https://img.icons8.com/color/200/chicken.png" onclick="clickChicken()">

    <button class="menu-btn" onclick="show('shop')">МАГАЗИН ⚔️</button>
    <button class="menu-btn" onclick="show('cases')">КЕЙСИ 🎁</button>
    <button class="menu-btn" onclick="show('inv')">РЮКЗАК 🎒</button>
    <button class="menu-btn" onclick="show('prof')">ПРОФІЛЬ 👤</button>
</div>

<!-- SHOP -->
<div id="shop" class="screen">
    <h2 class="neon-text">МАГАЗИН</h2>
    <div class="item-box"><span class="neon-text">💣 Бомба (150 🪙)</span><button class="buy-btn" onclick="buyItem('💣 Бомба',150)">КУПИТИ</button></div>
    <div class="item-box"><span class="neon-text">🔪 Ніж (500 🪙)</span><button class="buy-btn" onclick="buyItem('🔪 Ніж',500)">КУПИТИ</button></div>
    <div class="item-box"><span class="neon-text">🪓 Сокира (3000 🪙)</span><button class="buy-btn" onclick="buyItem('🪓 Сокира',3000)">КУПИТИ</button></div>
    <div class="item-box"><span class="neon-text">🔫 Пістолет (7000 🪙)</span><button class="buy-btn" onclick="buyItem('🔫 Пістолет',7000)">КУПИТИ</button></div>
    <div class="item-box"><span class="neon-text">🧨 Динаміт (15000 🪙)</span><button class="buy-btn" onclick="buyItem('🧨 Динаміт',15000)">КУПИТИ</button></div>
    <div class="item-box"><span class="neon-text">⚔️ Меч (40000 🪙)</span><button class="buy-btn" onclick="buyItem('⚔️ Меч',40000)">КУПИТИ</button></div>
    <div class="item-box"><span class="neon-text">🔥 Вогнемет (100000 🪙)</span><button class="buy-btn" onclick="buyItem('🔥 Вогнемет',100000)">КУПИТИ</button></div>

    <div class="item-box">
        <span class="neon-text">🤖 Автоклікер (10000 🪙)</span>
        <button class="buy-btn" onclick="buyAutoclicker()">КУПИТИ</button>
    </div>

    <div class="item-box">
        <span class="neon-text">⚡️ Апгрейд кліка (+1) (<span id="click-upgrade-price">5000</span> 🪙)</span>
        <button class="buy-btn" onclick="upgradeClick()">КУПИТИ</button>
    </div>

    <button class="menu-btn" style="border-color:red;" onclick="show('main')">НАЗАД</button>
</div>

<!-- CASES -->
<div id="cases" class="screen">
    <h2 class="neon-text">КЕЙСИ 🎁</h2>
    <div class="item-box">
        <span class="neon-text"><b>ZCY11K</b> кейс (5000 🪙)</span>
        <button class="buy-btn" onclick="openCase()">ВІДКРИТИ</button>
    </div>
    <button class="menu-btn" style="border-color:red;" onclick="show('main')">НАЗАД</button>
</div>

<!-- INVENTORY -->
<div id="inv" class="screen">
    <h2 class="neon-text">РЮКЗАК 🎒</h2>
    <div id="inv-list" class="neon-text">Порожньо</div>
    <button class="menu-btn" style="border-color:red;" onclick="show('main')">НАЗАД</button>
</div>

<!-- PROFILE -->
<div id="prof" class="screen">
    <h2 class="neon-text">ПРОФІЛЬ</h2>
    <div>Telegram: <span id="tg-username" class="neon-text">Не підключено</span></div>
    <div>Кліків: <span id="total-clicks" class="neon-text">0</span></div>
    <div>Титул: <span id="rank" class="neon-text">Новачок</span></div>
    <div id="tg-connect">
        <input type="text" id="tg-input" placeholder="Введіть Telegram username" style="padding:5px; border-radius:5px; border:none; text-align:center;">
        <button class="menu-btn" onclick="connectTG()" style="width:150px; margin-top:5px;">Підключити</button>
    </div>

    <!-- Нова статистика -->
    <h3 class="neon-text">СТАТИСТИКА 📊</h3>
    <div class="neon-text">
        Кількість покупок: <span id="total-buys">0</span><br>
        Витрачені коїни: <span id="coins-spent">0</span>
    </div>
    <button class="menu-btn" style="border-color:red;" onclick="resetGame()">СБРОСИТИ ВСЕ 🔄</button>

    <button class="menu-btn" style="border-color:red;" onclick="show('main')">НАЗАД</button>
</div>

<script>
let coins=0,totalClicks=0,clickPower=1;
let inventory=[];
let autoclicker=false;
let clickUpgradePrice=5000;
let tgUsername = "";
let totalBuys = 0;
let coinsSpent = 0;
let autoclickerInterval = null;

/* SAVE */
function save(){
 localStorage.setItem("chickenSave",JSON.stringify({coins,totalClicks,clickPower,inventory,autoclicker,clickUpgradePrice,totalBuys,coinsSpent}));
}

/* LOAD */
function load(){
 let s=JSON.parse(localStorage.getItem("chickenSave"));
 if(s){
     coins=s.coins; totalClicks=s.totalClicks; clickPower=s.clickPower; inventory=s.inventory;
     autoclicker=s.autoclickerfalse; clickUpgradePrice=s.clickUpgradePrice5000;
     totalBuys = s.totalBuys||0;
     coinsSpent = s.coinsSpent||0;
 }
 let savedTG = localStorage.getItem("tgUsername");
 if(savedTG){
     tgUsername = savedTG;
     document.getElementById("tg-username").innerText = tgUsername;
     document.getElementById("tg-connect").style.display = "none";
 }
 update();
 if(autoclicker) startAutoclicker();
}
window.onload=load;

/* GAME */
function clickChicken(){
 coins=Math.floor(coins + clickPower);
 totalClicks++;
 update(); save();
}

function update(){
 document.getElementById("coins").innerText=coins;
 document.getElementById("total-clicks").innerText=totalClicks;
 document.getElementById("click-power-text").innerText="Клік: +"+clickPower;

 let r="Новачок";
 if(totalClicks>500) r="Клікер";
 if(totalClicks>5000) r="Майстер";
 if(totalClicks>15000) r="ЛЕГЕНДА 🔥";
 document.getElementById("rank").innerText=r;

 let inv=document.getElementById("inv-list");
 inv.innerHTML=inventory.length?inventory.join("<br>"):"Порожньо";

 document.getElementById("click-upgrade-price").innerText = clickUpgradePrice;
 document.getElementById("total-buys").innerText = totalBuys;
 document.getElementById("coins-spent").innerText = coinsSpent;
}

/* SHOP */
function buyItem(name,price){
 if(coins<price) return alert("❌ Мало коїнів!");
 coins-=price;
 inventory.push(name);
 totalBuys++;
 coinsSpent += price;
 update(); save();
 alert("✅ Куплено: "+name);
}

/* AUTCLICKER */
function buyAutoclicker(){
 if(autoclicker) return alert("🤖 Автоклікер вже активний!");
 if(coins<10000) return alert("❌ Мало коїнів!");
 coins-=10000;
 totalBuys++;
 coinsSpent += 10000;
 autoclicker=true;
 startAutoclicker();
 update(); save();
 alert("✅ Куплено Автоклікер!");
}

function startAutoclicker(){
    if(autoclickerInterval) return;
    autoclickerInterval = setInterval(()=>{
        coins += clickPower;
        update();
        save();
    },1000);
}

/* UPGRADE CLICK */
function upgradeClick(){
 if(coins<clickUpgradePrice) return alert("❌ Мало коїнів!");
 coins-=clickUpgradePrice;
 clickPower++;
 coinsSpent += clickUpgradePrice;
 totalBuys++;
 clickUpgradePrice = Math.floor(clickUpgradePrice * 1.5);
 update(); save();
 alert("⚡️ Клік посилено! +1");
}

/* CASE */
function openCase(){
 if(coins<5000) return alert("Мало коїнів!");
 coins-=5000;
 coinsSpent += 5000;
 totalBuys++;

 const rewards = [
        {chance:2, value:1000000},
        {chance:50, value:500},
        {chance:18, value:8000},
        {chance:30, value:3000}
    ];

    let roll = Math.random()*100;
    let sum=0, reward=0;

    for(let r of rewards){
        sum += r.chance;
        if(roll < sum){ reward = r.value; break; }
    }

 coins += reward;
 update(); save();
 alert("🎉 Випало: +"+reward+" 🪙");
}

/* NAV */
function show(id){
 document.querySelectorAll(".screen").forEach(e => e.style.display="none");
 document.getElementById(id).style.display="block";
}

/* Telegram Connect */
function connectTG(){
 const input = document.getElementById("tg-input");
 if(input.value.trim() === "") return alert("Введіть username!");
 tgUsername = input.value.trim();
 localStorage.setItem("tgUsername", tgUsername);
 document.getElementById("tg-username").innerText = tgUsername;
 document.getElementById("tg-connect").style.display = "none";
 input.value = "";
 alert("✅ Telegram підключено: " + tgUsername);
}

/* RESET GAME */
function resetGame(){
    if(!confirm("⚠️ Ви впевнені, що хочете скинути ВСЕ?")) return;
    coins = 0;
    totalClicks = 0;
    clickPower = 1;
    inventory = [];
    autoclicker = false;
    clickUpgradePrice = 5000;
    totalBuys = 0;
    coinsSpent = 0;
    tgUsername = "";
    localStorage.clear();
    document.getElementById("tg-username").innerText = "Не підключено";
    document.getElementById("tg-connect").style.display = "block";
    update();
    alert("✅ Все скинуто!");
}

/* Додати неоновий клас всім текстам автоматично */
document.querySelectorAll("h2, h3, .stats, #click-power-text, .item-box span, #inv-list, #total-clicks, #rank, #tg-username").forEach(el=>{
  el.classList.add("neon-text");
});
</script>

</body>
</html>
