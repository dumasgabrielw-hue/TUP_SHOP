<!DOCTYPE html>
<html lang="ht">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>GABOO SHOP 🎮</title>
<style>
body{background:#080812;color:white;font-family:Arial;text-align:center;padding:15px}
.box{background:#19192d;padding:20px;border-radius:15px;margin:15px auto;max-width:400px}
input{padding:12px;width:85%;margin:8px;border-radius:8px;border:0}
button{background:#8b35ff;color:white;padding:12px;border:0;border-radius:8px;margin:7px;font-weight:bold}
.balance{color:#00ff99;font-size:27px}
</style>
</head>
<body>

<h1>🎮 GABOO SHOP</h1>
<p>Byenveni nan magazen nou an!</p>

<div class="box" id="register">
<h2>👤 KREYE KONT</h2>
<input id="name" placeholder="Non ou">
<input id="email" placeholder="Imèl ou">
<input id="password" type="password" placeholder="Modpas">
<button onclick="register()">KREYE KONT</button>
</div>

<div class="box" id="account" hidden>
<h2>👤 KONT MWEN</h2>
<p id="welcome"></p>
<p>💰 Balans mwen</p>
<span class="balance" id="balance">0 HTG</span>
<button onclick="toggleBalance()">⋮</button>
<button onclick="showDeposit()">📥 DEPO</button>
<button onclick="logout()">DEKONEKTE</button>
</div>

<div class="box" id="deposit" hidden>
<h2>💰 DEPO NATCASH</h2>
<input id="amount" type="number" placeholder="Kantite HTG">
<p>📸 Foto resi tranzaksyon an</p>
<input id="receipt" type="file" accept="image/*">
<button onclick="submitDeposit()">✅ VALIDE DEPO</button>
<p>🚀 Livrezon estime: 30 a 50 minit</p>
<p id="message"></p>
</div>

<div class="box" id="admin" hidden>
<h2>👑 ESPAS ADMIN</h2>
<input id="adminPass" type="password" placeholder="Modpas ADMIN">
<button onclick="adminLogin()">ANTRE ADMIN</button>
<div id="requests"></div>
</div>

<script>
let users=JSON.parse(localStorage.getItem("users")||"[]");
let requests=JSON.parse(localStorage.getItem("requests")||"[]");
let current=null;
let visible=true;

function save(){
localStorage.setItem("users",JSON.stringify(users));
localStorage.setItem("requests",JSON.stringify(requests));
}

function register(){
let n=name.value.trim(),e=email.value.trim(),p=password.value;
if(!n||!e||!p)return alert("Ranpli tout chan yo!");
if(users.some(u=>u.email===e))return alert("Kont sa deja egziste!");
let u={name:n,email:e,password:p,balance:0};
users.push(u);save();
current=u;
showAccount();
}

function showAccount(){
registerBox();
account.hidden=false;
welcome.innerText="Byenveni "+current.name;
updateBalance();
}
function registerBox(){
document.getElementById("register").hidden=true;
}
function updateBalance(){
balance.innerText=visible?current.balance+" HTG":"••••••";
}
function toggleBalance(){
visible=!visible;updateBalance();
}
function showDeposit(){
deposit.hidden=false;
}
function submitDeposit(){
let a=Number(amount.value);
let file=receipt.files[0];
if(a<=0||!file)return alert("Mete kantite kòb ak foto resi a!");
if(file.size>3*1024*1024)return alert("Foto a twò gwo!");
requests.push({
email:current.email,
amount:a,
date:new Date().toLocaleString(),
status:"An atant"
});
save();
message.innerText="Demann depo voye pou verifikasyon!";
amount.value="";
receipt.value="";
}

function adminLogin(){
if(adminPass.value!=="CHANGE_ADMIN_PASSWORD")
return alert("Modpas ADMIN pa kòrèk!");
document.getElementById("requests").innerHTML="";
requests.forEach((r,i)=>{
let div=document.createElement("div");
div.innerHTML=`<p>${r.email} - ${r.amount} HTG - ${r.status}</p>`;
if(r.status==="An atant"){
let b=document.createElement("button");
b.innerText="VALIDE";
b.onclick=()=>approve(i);
div.appendChild(b);
let reject=document.createElement("button");
reject.innerText="REFIZE";
reject.onclick=()=>{r.status="Refize";save();adminLogin()};
div.appendChild(reject);
}
requestsBox.appendChild(div);
});
}
function approve(i){
let r=requests[i];
let u=users.find(x=>x.email===r.email);
if(!u||r.status!=="An atant")return;
u.balance+=r.amount;
r.status="Valide";
save();adminLogin();
}
function logout(){
current=null;location.reload();
}
const requestsBox=document.getElementById("requests");
</script>
</body>
</html><div class="box">
<h2>💰 DEPO SOU TUP_SHOP</h2>

<p>Antre kantite kòb ou vle depoze:</p>

<input type="number" id="depositAmount"
placeholder="Kantite HTG">

<p>📸 Mete foto resi tranzaksyon an:</p>

<input type="file" id="receipt" accept="image/*">

<button onclick="submitDeposit()">
✅ VALIDE DEPO
</button>

<p id="depositMessage"></p>

<hr>

<h3>🚀 LIVREZON RAPID</h3>
<p>⏱️ Tan livrezon estime: 30 a 50 minit.</p>
</div>

<script>
function submitDeposit() {
 const amount = Number(
 document.getElementById("depositAmount").value
 );

 const receipt =
 document.getElementById("receipt").files[0];

 if(amount <= 0 || !receipt) {
   alert("Mete kantite kòb la ak foto resi a!");
   return;
 }

 document.getElementById("depositMessage").innerHTML =
 "✅ Demann depo ou resevwa!<br>" +
 "⏳ Nap verifye tranzaksyon ou.";
}
</scripts>
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
