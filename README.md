<!DOCTYPE html>
<html lang="ht"><!DOCTYPE html>
<html lang="ht">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gaboo Shop 🎮</title>

<style>
body {
  background:#080812;
  color:white;
  font-family:Arial;
  text-align:center;
  padding:20px;
}
.box {
  background:#19192d;
  padding:20px;
  border-radius:15px;
  max-width:400px;
  margin:20px auto;
}
input {
  width:90%;
  padding:12px;
  margin:8px;
  border-radius:8px;
  border:none;
}
button {
  padding:12px 20px;
  margin:8px;
  border:0;
  border-radius:8px;
  background:#8b35ff;
  color:white;
  font-weight:bold;
}
.balance {
  color:#00ff99;
  font-size:25px;
}
</style>
</head>

<body>

<h1>🎮 GABOO SHOP</h1>
<p>Byenveni nan Gaboo Shop!</p>

<div class="box" id="register">
<h2>KREYE KONT</h2>
<input id="name" placeholder="Non ou">
<input id="email" placeholder="Imèl ou">
<input id="password" type="password" placeholder="Modpas">
<button onclick="register()">KREYE KONT</button>
</div>

<div class="box" id="login">
<h2>KONEKTE</h2>
<input id="loginEmail" placeholder="Imèl">
<input id="loginPassword" type="password" placeholder="Modpas">
<button onclick="login()">KONEKTE</button>
</div>

<div class="box" id="account" style="display:none">
<h2>👤 KONT MWEN</h2>
<p id="welcome"></p>
<p>Balans mwen:</p>
<div class="balance" id="balance">0 HTG</div>

<button onclick="deposit()">📥 DEPO</button>
<button onclick="buy()">🛒 ACHAT</button>
<button onclick="logout()">DEKONEKTE</button>

</div>

<script>
let users = JSON.parse(localStorage.getItem("gabooUsers")) || [];
let currentUser = null;

function register() {
 let name = document.getElementById("name").value;
 let email = document.getElementById("email").value;
 let password = document.getElementById("password").value;

 if(!name || !email || !password) {
   alert("Ranpli tout enfòmasyon yo!");
   return;
 }

 if(users.some(u => u.email === email)) {
   alert("Kont sa deja egziste!");
   return;
 }

 users.push({name,email,password,balance:0});
 localStorage.setItem("gabooUsers",JSON.stringify(users));

 alert("Kont kreye!");
}

function login() {
 let email = document.getElementById("loginEmail").value;
 let password = document.getElementById("loginPassword").value;

 let user = users.find(u =>
   u.email === email && u.password === password
 );

 if(!user) {
   alert("Enfòmasyon yo pa kòrèk!");
   return;
 }

 currentUser = user;
 showAccount();
}

function showAccount() {
 document.getElementById("register").style.display="none";
 document.getElementById("login").style.display="none";
 document.getElementById("account").style.display="block";

 document.getElementById("welcome").innerText =
 "Byenveni "+currentUser.name;

 document.getElementById("balance").innerText =
 currentUser.balance+" HTG";
}

function deposit() {
 alert("Pou depoze, kontakte administratè Gaboo Shop sou Natcash. Balans lan ap ajou apre verifikasyon peman.");
}

function buy() {
 alert("Chwazi pwodwi ou vle achte nan Gaboo Shop!");
}

function logout() {
 currentUser=null;
 location.reload();
}
</script>

</body>
</html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TUP SHOP 🎮</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}
body{background:#080b16;color:white;font-family:Arial}
header{text-align:center;padding:30px 15px;background:linear-gradient(135deg,#101d45,#5c168e)}
.logo{display:inline-block;border:3px solid #00eaff;padding:12px 22px;border-radius:18px;font-size:30px;font-weight:900;color:#00eaff}
header p{margin-top:12px}
.contact{display:inline-block;margin-top:15px;background:#00c853;color:white;padding:12px 22px;border-radius:25px;text-decoration:none;font-weight:bold}
.container{max-width:1000px;margin:auto;padding:18px}
.banner{background:#171c39;padding:22px;border-radius:18px;text-align:center;margin-bottom:25px}
.banner h2,.game-title{color:#00eaff}
.game-title{text-align:center;font-size:25px;margin:30px 0 18px}
.free-title{color:#ff9b28}
.games{display:grid;grid-template-columns:repeat(auto-fit,minmax(145px,1fr));gap:15px}
.card{background:#151b2c;border:1px solid #343d59;border-radius:15px;padding:15px 10px;text-align:center}
.game-logo{font-size:20px;font-weight:900;margin-bottom:12px}
.flex-logo{color:#00eaff}
.ff-logo{color:#ff9b28}
.product{font-weight:bold;margin-bottom:10px}
.price{color:#00eaff;font-size:20px;font-weight:bold;margin-bottom:13px}
input{width:100%;padding:11px;margin:6px 0;background:#080b16;color:white;border:1px solid #59627c;border-radius:8px}
.buy{display:block;background:#00c853;color:white;text-decoration:none;padding:11px 5px;border-radius:9px;font-weight:bold;margin-top:10px}
.payment{background:#151b2c;padding:22px;border-radius:15px;margin-top:30px;text-align:center;border:1px solid #00c853;line-height:2}
footer{text-align:center;padding:25px;color:#aaa}
</style>
</head>

<body>

<header>
<div class="logo">TUP_SHOP 👑</div>
<p>🔥 Byenvini sou TUP SHOP 🔥</p>
<p>Top-Up Flex City & Free Fire</p>
<a class="contact" href="https://wa.me/50941712851">📲 Kontakte nou</a>
</header>

<div class="container">

<div class="banner">
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

</body>
</html>
