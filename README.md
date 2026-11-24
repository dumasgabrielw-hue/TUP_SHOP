<!DOCTYPE DOCTYPEhtmltml lang="ht"><!DOCTYPE html>
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
 }cuivdiv class="banner">
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
