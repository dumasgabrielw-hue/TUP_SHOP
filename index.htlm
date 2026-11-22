<!DOCTYPE html>
<html lang="ht">
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
