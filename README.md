<div class="wallet">
  <h2>💰 MON BALANCE</h2>
  <h1 id="balance">0 HTG</h1>
  <button onclick="showDeposit()">
    AJOUTER SUR BALANCE
  </button>
</div>

<div id="deposit" style="display:none;">
  <h3>AJOUTER SUR BALANCE</h3>
  <input id="amount" type="number"
         placeholder="Montant HTG">
  <button onclick="requestDeposit()">
    CONTINUER
  </button>
</div>

<h2>🛒 PRODUITS</h2>

<div class="product">
  <h3>Free Fire Diamonds 💎</h3>
  <p>Prix: 200 HTG</p>
  <button onclick="buyProduct('Free Fire Diamonds',200)">
    ACHETER
  </button>
</div>

<h2>📦 PRODUITS EN ATTENTE</h2>
<div id="pending"></div>

<script>
let balance = 0;

function updateBalance() {
  document.getElementById("balance").innerText =
    balance + " HTG";
}

function showDeposit() {
  document.getElementById("deposit").style.display = "block";
}

function requestDeposit() {
  let amount = Number(document.getElementById("amount").value);

  if (amount <= 0 || !Number.isFinite(amount)) {
    alert("Montant invalide");
    return;
  }

  alert("Demande de dépôt enregistrée. Paiement à vérifier.");
}

function buyProduct(name, price) {
  if (balance < price) {
    alert("Balance insuffisante ! Ajoutez de l'argent.");
    showDeposit();
    return;
  }

  balance -= price;
  updateBalance();

  let item = document.createElement("p");
  item.innerText = name + " - " + price +
    " HTG | PRODUIT EN ATTENTE ⏳";

  document.getElementById("pending").appendChild(item);
}
</script><button id="buyBtn" onclick="acheterProduit()">
  ACHETER UN PRODUIT
</button>

<p id="status"></p>

<style>
#buyBtn {
  background: linear-gradient(135deg, #6c2cff, #a000ff);
  color: white;
  border: none;
  padding: 15px 25px;
  border-radius: 12px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
}

#status {
  color: #00ff88;
  font-weight: bold;
  margin-top: 12px;
}
</style>

<script>
function acheterProduit() {
  const btn = document.getElementById("buyBtn");
  const status = document.getElementById("status");

  btn.disabled = true;
  btn.innerText = "PROCESSING... ⏳";
  status.innerText = "Traitement de votre commande...";

  setTimeout(() => {
    btn.innerText = "ACHETER UN PRODUIT";
    btn.disabled = false;
    status.innerText =
      "Commande prête à être confirmée. Vérifiez votre paiement.";
  }, 3000);
}
</script>unctionnsendDeposit() {<!DOCTYPE html>
<html lang="ht">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gaboo Shop 🎮</title>

<style>
*{box-sizing:border-box}
body{
 margin:0;
 background:#080812;
 color:white;
 font-family:Arial,sans-serif;
}
header{
 background:linear-gradient(135deg,#15152b,#6420a0);
 text-align:center;
 padding:25px 12px;
}
header h1{font-size:32px}
.container{max-width:900px;margin:auto;padding:15px}
.card{
 background:#17172a;
 padding:18px;
 border-radius:15px;
 margin:15px 0;
 border:1px solid #6332a0;
}
button{
 background:#8c35df;
 color:white;
 border:0;
 padding:13px;
 border-radius:9px;
 width:100%;
 margin-top:10px;
 font-weight:bold;
}
input,select{
 width:100%;
 padding:13px;
 margin-top:10px;
 border-radius:8px;
 border:0;
}
.price{color:#42ff9b;font-weight:bold}
.hidden{display:none}
</style>
</head>

<header>
<h1>🎮 GABOO SHOP</h1>
<p>Byenvini nan pi bon boutik Top Up la!</p>
</header>

<div class="container">

<div class="card">
<h2>👛 Balans mwen</h2>
<h1 id="balance">0 HTG</h1>
<button onclick="show('deposit')">💰 DEPOZE LAJAN</button>
</div>

<div id="deposit" class="card hidden">
<h2>💳 Fè depo</h2>
<p>Voye peman ou sou Natcash.</p>
<input id="amount" type="number" placeholder="Kantite HTG">
<input id="reference" placeholder="Nimewo tranzaksyon">
<label>Foto tranzaksyon:</label>
<input id="proof" type="file" accept="image/*">
<button onclick="deposit()">Voye demann depo</button>
</div>

<div class="card">
<h2>🎮 Pwodwi nou yo</h2>

<div class="card">
<h3>🏙️ Flex City</h3>
<p>125 Diamonds</p>
<p class="price">187 HTG</p>
<button onclick="buy('Flex City - 125 Diamonds',187)">Achte kounye a</button>
</div>

<div class="card">
<h3>💎 Flex Pass</h3>
<p class="price">Pri pou konfime</p>
<button onclick="buy('Flex Pass',0)">Kòmande</button>
</div>

<div class="card">
<h3>🔥 Free Fire</h3>
<p>Diamonds Top Up</p>
<button onclick="buy('Free Fire Diamonds',0)">Kòmande</button>
</div>

<div class="card">
<h3>⚽ DLS</h3>
<p>Top Up DLS</p>
<button onclick="buy('DLS Top Up',0)">Kòmande</button>
</div>

<div class="card">
<h3>🎯 PUBG Mobile</h3>
<p>UC Top Up</p>
<button onclick="buy('PUBG Mobile UC',0)">Kòmande</button>
</div>
</div>

<div id="order" class="card hidden">
<h2>📦 Fini kòmand ou</h2>
<p id="product"></p>
<input id="player" placeholder="ID jwèt ou">
<input id="contact" placeholder="Nimewo WhatsApp ou">
<button onclick="sendOrder()">Konfime kòmand</button>
</div>

<div class="card">
<h3>📋 Swiv kòmand mwen</h3>
<p>Voye nimewo kòmand ou bay administratè a pou verifye estati li.</p>
</div>

</div>

<script>
let balance = Number(localStorage.getItem("gabooBalance") || 0);
let selected = "";

function update(){
 document.getElementById("balance").innerText=balance+" HTG";
}
function show(id){
 document.getElementById(id).classList.toggle("hidden");
}
function deposit(){
 let amount=Number(document.getElementById("amount").value);
 let ref=document.getElementById("reference").value;
 let proof=document.getElementById("proof").files[0];

 if(amount<=0 || !ref || !proof){
 alert("Tanpri ranpli tout enfòmasyon yo.");
 return;
 }
 alert("Demann depo a pare. Administratè a dwe verifye peman an anvan balans lan ogmante.");
}
function buy(name,price){
 selected=name;
 document.getElementById("product").innerText=name+" - "+(price?price+" HTG":"Pri pou konfime");
 document.getElementById("order").classList.remove("hidden");
}
function sendOrder(){
 let player=document.getElementById("player").value;
 let contact=document.getElementById("contact").value;

 if(!player || !contact){
 alert("Ranpli ID jwèt ak nimewo kontak ou.");
 return;
 }
 alert("Kòmand ou prepare. Voye enfòmasyon yo bay administratè Gaboo Shop pou konfimasyon.");
}
update();
</script>

</body>
</html>
const amount = Number(
    document.getElementById("amount").value
  );

  const receipt =
    document.getElementById("receipt").files[0];

  const message =
    document.getElementById("depositMessage");

  if (!amount || amount <= 0) {
    message.innerText = "Antre yon kantite lajan valab.";
    return;
  }

  if (!receipt || !receipt.type.startsWith("image/")) {
    message.innerText = "Tanpri mete foto resi a.";
    return;
  }

  message.innerText =
    "Demann ou pare. Li bezwen voye sou sèvè a pou administratè a verifye li.";
}<section class="payment" id="depo">
  <h2>💰 AJOUTE LAJAN</h2>

  <p>Balans ou: <b id="balance">0 HTG</b></p>

  <input type="number" id="amount"
  placeholder="Antre kantite HTG">

  <p>📸 Mete foto resi Natcash ou</p>

  <input type="file" id="receipt"
  accept="image/*">

  <button onclick="sendDeposit()">
    VOYE POU VALIDASYON
  </button>

  <p id="depositMessage"></p>
</section> <!DOCTYPE html>
<html lang="ht">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gaboo Shop 🎮</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}
body{
 font-family:Arial,sans-serif;
 background:#f4f6fb;
 color:#20283a;
}
header{
 background:linear-gradient(135deg,#182c76,#5424b8);
 color:white;padding:25px 15px;text-align:center;
}
header h1{font-size:30px}
header p{margin-top:8px}
nav{
 display:flex;gap:10px;overflow-x:auto;
 padding:14px;background:white;
 position:sticky;top:0;z-index:10;
}
nav a{
 white-space:nowrap;text-decoration:none;
 color:#25345c;border:1px solid #ddd;
 border-radius:25px;padding:12px 17px;
 font-weight:bold;
}
.profile{
 background:#eaf0ff;padding:20px;
 margin:15px;border-radius:15px;
}
.profile h3{color:#243fa9}
.balance{color:#253fae;font-size:21px;
 font-weight:bold;margin-top:10px}
.banner{
 margin:15px;border-radius:18px;
 background:linear-gradient(135deg,#34218c,#172b70);
 color:white;padding:35px 15px;text-align:center;
}
.banner h2{margin-bottom:10px}
.search{
 display:block;width:92%;padding:15px;
 margin:20px auto;border:1px solid #ddd;
 border-radius:12px;font-size:16px;
}
.section{
 margin:18px 15px;
 border:1px solid #dce1f1;
 border-radius:18px;overflow:hidden;
 background:white;
}
.section-title{
 padding:17px;background:#e9ebff;
 color:#343db3;font-weight:bold;font-size:18px;
}
.gold-title{background:#fff1d9;color:#e69a00}
.grid{
 display:grid;
 grid-template-columns:repeat(3,minmax(0,1fr));
 gap:10px;padding:12px;
}
.card{
 border:1px solid #d7dce7;
 border-radius:13px;overflow:hidden;
 text-align:center;background:white;
 display:flex;flex-direction:column;
}
.photo{
 height:115px;background:#10121d;
 display:flex;align-items:center;
 justify-content:center;font-size:55px;
}
.card h3{
 font-size:15px;padding:10px 4px;
 min-height:57px;
}
.price{
 color:#303dc0;font-weight:bold;
 font-size:15px;padding:8px 2px;
}
.gold-price{color:#e69a00}
.stock{font-size:11px;color:#399767;padding:7px}
.card button{
 background:#3035ef;color:white;
 border:0;padding:13px 3px;
 font-weight:bold;font-size:14px;
 cursor:pointer;margin-top:auto;
}
.gold button{background:#f4a000}
.other button{background:#5733bd}
.payment,.contact{
 margin:18px 15px;padding:22px;
 background:white;border-radius:15px;
 text-align:center;line-height:2;
}
.payment h2,.contact h2{color:#253db5}
footer{
 background:#17245b;color:white;
 text-align:center;padding:25px;margin-top:25px;
}
.modal{
 display:none;position:fixed;inset:0;
 background:#0009;z-index:30;
 align-items:center;justify-content:center;
 padding:15px;
}
.modal-box{
 background:white;border-radius:15px;
 padding:22px;width:100%;max-width:400px;
}
.modal-box input{
 width:100%;padding:13px;margin:10px 0;
 border:1px solid #ccc;border-radius:8px;
}
.modal-box button{
 width:100%;padding:13px;border:0;
 border-radius:8px;background:#3035ef;
 color:white;font-weight:bold;margin-top:8px;
}
.close{background:#777!important}
@media(max-width:420px){
 .grid{gap:7px;padding:8px}
 .photo{height:95px;font-size:42px}
 .card h3{font-size:13px}
 .price{font-size:13px}
}
</style>
</head>

<body>

<header>
<h1>GABOO SHOP 🎮</h1>
<p>Tout Top Up ou bezwen nan yon sèl kote!</p>
</header>

<nav>
<a href="#">🏠 AKÈY</a>
<a href="#boutik">🛍️ BOUTIK</a>
<a href="#kont">👤 KONT MWEN</a>
<a href="#payment">💰 DEPO</a>
</nav>

<div class="profile" id="kont">
<h3>👤 Byenvini nan Gaboo Shop</h3>
<p>Kliyan nou yo toujou enpòtan!</p>
<div class="balance">💰 Balans: 0 HTG</div>
</div>

<div class="banner">
<h2>🔥 GABOO SHOP</h2>
<p>Achte Diamonds, Gold, Pass ak lòt pwodwi jwèt.</p>
<p>⚡ Sèvis rapid • Livrezon manyèl</p>
</div>

<input class="search" id="search"
placeholder="🔎 Chèche yon pwodwi..."
oninput="searchProducts()">

<div id="boutik">

<!-- FLEX CITY -->

<section class="section">
<div class="section-title">💎 FLEX CITY – DIAMONDS</div>
<div class="grid" id="diamonds">

</div>
</section>

<!-- GOLD -->

<section class="section">
<div class="section-title gold-title">🪙 FLEX CITY – PACK GOLD</div>
<div class="grid" id="gold"></div>
</section>

<!-- FREE FIRE -->

<section class="section">
<div class="section-title">🔥 FREE FIRE DIAMONDS</div>
<div class="grid" id="freefire"></div>
</section>

<!-- OTHER GAMES -->

<section class="section">
<div class="section-title">🎮 LÒT JÈT</div>
<div class="grid" id="other"></div>
</section>

</div>

<section class="payment" id="payment">
<h2>💰 PEMAN NATCASH</h2>
<p>Fè peman ou atravè Natcash.</p>
<p>📱 Nimewo Natcash: <b id="natcash">POU RANPLI</b></p>
<p>📸 Voye prèv tranzaksyon an pou verifikasyon.</p>
<p>⚡ Livrezon fèt apre verifikasyon peman.</p>
</section>

<section class="contact">
<h2>📞 KONTAK GABOO SHOP</h2>
<p>Kontakte administratè a pou èd.</p>
<p>GABOO SHOP 🎮</p>
</section>

<footer>
<p>© 2026 GABOO SHOP 🎮</p>
<p>Tout dwa rezève.</p>
</footer>

<div class="modal" id="modal">
<div class="modal-box">
<h2>🛒 Fè kòmand ou</h2>
<p id="selected"></p>
<input id="player" placeholder="ID jwèt ou">
<input id="playername" placeholder="Non ou">
<button onclick="submitOrder()">KONFIME KÒMAND</button>
<button class="close" onclick="closeModal()">FÈMEN</button>
<p id="message"></p>
</div>
</div>

<script>

// METE PRI AK PWODWI YO LA

const diamonds = [
["825 Diamonds – 80% Rabè","499.78"],
["825 Diamonds – 70% Rabè","600.60"],
["825 Diamonds – 60% Rabè","798.60"],
["825 Diamonds – 40% Rabè","1155"]
];

const gold = [
["2 750 Lò","686.40"],
["5 750 Lò","1374.45"],
["15 000 Lò","3436.95"],
["62 500 Lò","6873.90"],
["130 000 Lò","13749.45"],
["145 000 Lò","32998.35"],
["225 000 Lò","49498.35"],
["320 000 Lò","65998.35"]
];

const freefire = [
["100 Diamonds","Pri pou mete"],
["310 Diamonds","Pri pou mete"],
["520 Diamonds","Pri pou mete"],
["1060 Diamonds","Pri pou mete"]
];

const other = [
["Flex Pass","Pri pou mete"],
["DLS Top Up","Pri pou mete"],
["PUBG Mobile UC","Pri pou mete"]
];

let currentProduct = "";

function createCards(items,container,icon,style=""){
 const box=document.getElementById(container);

 items.forEach(item=>{
 const card=document.createElement("div");
 card.className="card "+style;

 card.innerHTML=`
 <div class="photo">${icon}</div>
 <h3>${item[0]}</h3>
 <div class="price ${style==='gold'?'gold-price':''}">
 ${item[1].includes("Pri")?item[1]:item[1]+" HTG"}
 </div>
 <div class="stock">⚡ Livrezon Manyèl</div>
 <button onclick="buy('${item[0]}','${item[1]}')">
 🛒 Achte
 </button>`;

 box.appendChild(card);
 });
}

createCards(diamonds,"diamonds","💎");
createCards(gold,"gold","🪙","gold");
createCards(freefire,"freefire","🔥");
createCards(other,"other","🎮","other");

function buy(name,price){
 currentProduct=name+" - "+price+" HTG";
 document.getElementById("selected").innerText=
 "Pwodwi: "+currentProduct;
 document.getElementById("modal").style.display="flex";
 document.getElementById("message").innerText="";
}

function closeModal(){
 document.getElementById("modal").style.display="none";
}

function submitOrder(){
 const id=document.getElementById("player").value.trim();
 const name=document.getElementById("playername").value.trim();

 if(!id || !name){
  document.getElementById("message").innerText=
  "Tanpri ranpli ID jwèt la ak non ou.";
  return;
 }

 const order=
 "KÒMAND GABOO SHOP\n"+
 "Pwodwi: "+currentProduct+"\n"+
 "Non: "+name+"\n"+
 "ID jwèt: "+id;

 document.getElementById("message").innerText=
 "Kòmand ou prepare! Kontakte administratè Gaboo Shop pou verifye peman ak livrezon.";

 alert(order);
}

function searchProducts(){
 const value=document.getElementById("search").value.toLowerCase();
 document.querySelectorAll(".card").forEach(card=>{
 card.style.display=card.innerText.toLowerCase().includes(value)
 ? "flex":"none";
 });
}

</script>
</body>
</html><!DOCTYPE html>
<html lang="ht">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gaboo Shop 🎮</title>

<style>
*{
 margin:0;
 padding:0;
 box-sizing:border-box;
 font-family:Arial,sans-serif;
}

body{
 background:#080b16;
 color:white;
}

header{
 background:linear-gradient(135deg,#111936,#5124a8);
 padding:25px 15px;
 text-align:center;
}

header h1{
 font-size:32px;
 color:#fff;
}

header p{
 color:#ddd;
 margin-top:8px;
}

nav{
 display:flex;
 justify-content:center;
 gap:20px;
 padding:15px;
 background:#11172a;
 flex-wrap:wrap;
}

nav a{
 color:white;
 text-decoration:none;
 font-weight:bold;
}

.banner{
 margin:20px;
 padding:30px 15px;
 text-align:center;
 border-radius:15px;
 background:linear-gradient(135deg,#5424c9,#101d48);
}

.banner h2{
 font-size:25px;
 margin-bottom:10px;
}

.banner p{
 color:#eee;
}

.search{
 display:block;
 width:90%;
 max-width:500px;
 margin:20px auto;
 padding:14px;
 border:none;
 border-radius:10px;
 font-size:16px;
}

.title{
 text-align:center;
 margin:25px 0;
 color:#a98aff;
}

.games{
 display:grid;
 grid-template-columns:repeat(auto-fit,minmax(145px,1fr));
 gap:15px;
 padding:15px;
}

.card{
 background:#151c31;
 border:1px solid #303c61;
 border-radius:15px;
 padding:18px 12px;
 text-align:center;
 transition:.3s;
}

.card:hover{
 transform:translateY(-5px);
 border-color:#a47aff;
}

.icon{
 font-size:40px;
 margin-bottom:12px;
}

.card h3{
 margin-bottom:10px;
}

.price{
 color:#50e6a0;
 font-weight:bold;
 margin:12px 0;
}

button{
 background:linear-gradient(135deg,#713cff,#a044ff);
 color:white;
 border:none;
 padding:12px 18px;
 border-radius:9px;
 font-weight:bold;
 cursor:pointer;
 width:100%;
}

button:hover{
 opacity:.85;
}

.payment{
 margin:20px;
 padding:25px;
 background:#151c31;
 border-radius:15px;
 text-align:center;
}

.payment h2{
 color:#50e6a0;
 margin-bottom:12px;
}

footer{
 background:#11172a;
 text-align:center;
 padding:25px;
 margin-top:30px;
 color:#aaa;
}
</style>
</head>

<body>

<header>
<h1>GABOO SHOP 🎮</h1>
<p>Pi bon kote pou achte Top Up jwèt ou yo!</p>
</header>

<nav>
<a href="#">Akèy</a>
<a href="#games">Boutik</a>
<a href="#payment">Peman</a>
<a href="#contact">Kontak</a>
</nav>

<section class="banner">
<h2>🔥 BYENVINI NAN GABOO SHOP</h2>
<p>Achte Diamonds, Pass ak lòt pwodwi jwèt ou renmen yo.</p>
</section>

<input class="search" type="text"
id="search"
placeholder="🔎 Chèche yon pwodwi..."
onkeyup="searchProducts()">

<h2 class="title" id="games">🎮 PWODWI NOU YO</h2>

<section class="games">

<div class="card">
<div class="icon">💎</div>
<h3>Flex City Diamonds</h3>
<p>Top Up Diamonds</p>
<div class="price">Pri disponib</div>
<button onclick="buy('Flex City Diamonds')">ACHTE KOUNYE A</button>
</div>

<div class="card">
<div class="icon">🎟️</div>
<h3>Flex Pass</h3>
<p>Flex City Pass</p>
<div class="price">Pri disponib</div>
<button onclick="buy('Flex Pass')">ACHTE KOUNYE A</button>
</div>

<div class="card">
<div class="icon">🔥</div>
<h3>Free Fire</h3>
<p>Diamonds Free Fire</p>
<div class="price">Pri disponib</div>
<button onclick="buy('Free Fire Diamonds')">ACHTE KOUNYE A</button>
</div>

<div class="card">
<div class="icon">⚽</div>
<h3>DLS</h3>
<p>Top Up DLS</p>
<div class="price">Pri disponib</div>
<button onclick="buy('DLS')">ACHTE KOUNYE A</button>
</div>

<div class="card">
<div class="icon">🎯</div>
<h3>PUBG Mobile</h3>
<p>UC PUBG</p>
<div class="price">Pri disponib</div>
<button onclick="buy('PUBG Mobile')">ACHTE KOUNYE A</button>
</div>

</section>

<section class="payment" id="payment">
<h2>💰 MÒD PEMAN</h2>
<p>Nou aksepte peman atravè Natcash.</p>
scriptp>📸 Voye prèv tranzaksyon ou pou verifikasyon.</p>
</section>

<section class="payment" id="contact">
<h2>📞 KONTAK NOU</h2>
<p>Gaboo Shop 🎮</p>
<p>Sèvis kliyan disponib pou ede w.</p>
</section>

<footer>
<p>© 2026 GABOO SHOP 🎮</p>
<p>Tout dwa rezève.</p>
</footer>

<script>
function buy(product){
 alert("Ou chwazi: "+product+
 "\nKontakte Gaboo Shop pou fini kòmand ou.");
}

function searchProducts(){
 let input=document.getElementById("search")
 .value.toLowerCase();

 let cards=document.querySelectorAll(".card");

 cards.forEach(card=>{
 let name=card.innerText.toLowerCase();
 card.style.display=name.includes(input)
 ? "block":"none";
 });
}
</script>
<h2>🏙️ TUP SHOP 🏙️</h2>

<p>💎 Diamonds | 🎟️ Pass | 🔥 Top-Up</p>
</div>

<h2 class="game-title">🏙️ FLEX CITY 🌆</h2>
<div class="games" id="flex"></div>

<h2 class="game-title free-title">🔥 FREE FIRE 🔥</h2>
<div class="games" id="freefire"></div>

<div class="payment">
<h2>💰 MÒD PEMAN</h2>
<p>✅ Natcash</p>
<p>📞 +509 41712851</p>
<p>Voye prèv peman ou sou WhatsApp.</p>
</div>

</div>

<footer>
<h3>TUP_SHOP 👑🎮</h3>
<p>Mèsi paske ou chwazi TUP SHOP!</p>
<p>© 2026 TUP SHOP</p>
</footer>

<script>

<img src="flex-city-banner.jpg"
class="flex-logo"
alt="Flex City RP">
const flexProducts = [
["Retire publicité",400],
["FLEX PASS",615],
["825 💎",500],
["1 Kantenè",200],
["2 Kantenè",400],
["3 Kantenè",600],
["50 Kantenè",10000],
["VIP",1000],
["125 💎",300],
["60 💎",250],
["300 💎",400]
];

const freeProducts = [
["BOOYAH PASS",1000],
["110 💎",150],
["220 💎",300],
["1000 💎",1500]
];

function displayProducts(products,element,game){

const area=document.getElementById(element);

products.forEach(item=>{

const name=item[0];
const price=item[1];

const card=document.createElement("div");
card.className="card";

const isFree=game==="Free Fire";

card.innerHTML=`
<div class="game-logo ${isFree?'ff-logo':'flex-logo'}">
${isFree?'FREE FIRE 🔥':'FLEX CITY 🏙️'}
</div>

<div class="product">${name}</div>
<div class="price">${price} HTG 💰</div>

<input type="text" class="account" placeholder="Non kont ou">

${isFree?
'<input type="text" class="playerid" placeholder="ID Free Fire ou">':
''}

<a href="#" class="buy">🛒 ACHTE KOUNYE A</a>
`;

card.querySelector(".buy").addEventListener("click",function(e){

e.preventDefault();

const account=card.querySelector(".account").value.trim();

if(!account){
alert("Tanpri antre non kont ou.");
return;
}

let playerID="";

if(isFree){
playerID=card.querySelector(".playerid").value.trim();

if(!playerID){
alert("Tanpri antre ID Free Fire ou.");
return;
}
}

let message=
"BONJOU TUP SHOP!\n"+
"Pwodwi: "+name+"\n"+
"Jwèt: "+game+"\n"+
"Non kont: "+account+"\n"+
(isFree?"ID Free Fire: "+playerID+"\n":"")+
"Pri: "+price+" HTG\n"+
"Peman: Natcash";

const whatsapp=
"https://wa.me/50941712851?text="+
encodeURIComponent(message);

window.open(whatsapp,"_blank");

});

area.appendChild(card);

});

}

displayProducts(flexProducts,"flex","Flex City");
displayProducts(freeProducts,"freefire","Free Fire");

</script>


