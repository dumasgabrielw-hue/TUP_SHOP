<!DOCTYPE html>
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
<br>
<p>📸 Voye prèv tranzaksyon ou pou verifikasyon.</p>
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


