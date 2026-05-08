const products=[
{name:"POLERA OVERSIZE BASIC STREETWEAR REVOLUTION NEGRA",price:21990,images:["activos/basic-front.jpg","activos/basic-back.jpg"]},
{name:"POLERA OVERSIZE LOST TEDDY STREETWEAR REVOLUTION NEGRA",price:21990,images:["activos/teddy-front.jpg","activos/teddy-back.jpg"]},
{name:"POLERA OVERSIZE LOST DICE STREETWEAR REVOLUTION NEGRA",price:25990,images:["activos/dice-front.jpg","activos/dice-back.jpg"]},
{name:"POLERA OVERSIZE REBIRTH STREETWEAR REVOLUTION NEGRA",price:25990,images:["activos/rebirth-front.jpg","activos/rebirth-back.jpg"]}
];

const productsDiv=document.getElementById("productos");

products.forEach((p,index)=>{
productsDiv.innerHTML+=`
<div class='card'>
<img src='${p.images[0]}'>
<div class='content'>
<h2>${p.name}</h2>
<div class='price'>$${p.price.toLocaleString("es-CL")}</div>
<button onclick='openProduct(${index})'>VER</button>
</div>
</div>`;
});

let currentProduct=null;
let currentSlide=0;
let selectedSize="M";

function openProduct(index){
currentProduct=products[index];
currentSlide=0;
document.getElementById("modal").style.display="flex";
document.getElementById("title").innerText=currentProduct.name;
document.getElementById("price").innerText="$"+currentProduct.price.toLocaleString("es-CL");
updateSlide();
renderRecommended(index);
}

function renderRecommended(currentIndex){
const grid=document.getElementById("recommended-grid");
grid.innerHTML="";
products.forEach((p,i)=>{
if(i!==currentIndex){
grid.innerHTML+=`<img src='${p.images[0]}' onclick='openProduct(${i})'>`;
}
});
}

function closeModal(){document.getElementById("modal").style.display="none";}
function updateSlide(){document.getElementById("slider-img").src=currentProduct.images[currentSlide];}
function nextSlide(){currentSlide=(currentSlide+1)%currentProduct.images.length;updateSlide();}
function prevSlide(){currentSlide=(currentSlide-1+currentProduct.images.length)%currentProduct.images.length;updateSlide();}

function selectSize(btn){
document.querySelectorAll(".sizes button").forEach(b=>b.classList.remove("active"));
btn.classList.add("active");
selectedSize=btn.innerText;
}

let cart=[];

function addToCart(){
cart.push({name:currentProduct.name,price:currentProduct.price,size:selectedSize});
renderCart();
}

function renderCart(){
let total=0;
const items=document.getElementById("cart-items");
items.innerHTML="";
cart.forEach(item=>{
total+=item.price;
items.innerHTML+=`
<div class='cart-item'>
<strong>${item.name}</strong><br>
Talla: ${item.size}<br>
$${item.price.toLocaleString("es-CL")}
</div>`;
});
document.getElementById("total").innerText="$"+total.toLocaleString("es-CL");
document.getElementById("cart-count").innerText=cart.length;
}

function toggleCart(){
document.getElementById("cart").classList.toggle("open");
}

function buyNow(){
const msg=`Hola REVN quiero comprar:%0A%0A${currentProduct.name}%0ATalla: ${selectedSize}%0A$${currentProduct.price.toLocaleString("es-CL")}`;
window.open(`https://wa.me/56942361269?text=${msg}`);
}

function checkout(){
if(cart.length===0)return;
let total=0;
let msg="Hola REVN quiero comprar:%0A%0A";
cart.forEach(item=>{
total+=item.price;
msg+=`- ${item.name} | Talla ${item.size} | $${item.price.toLocaleString("es-CL")}%0A`;
});
msg+=`%0ATOTAL: $${total.toLocaleString("es-CL")}`;
window.open(`https://wa.me/56942361269?text=${msg}`);
}

function registerUser(){
const email=document.getElementById("email").value;
if(!email.includes("@")) return alert("Ingresa un correo válido");
localStorage.setItem("revnUser",email);
document.getElementById("register-modal").classList.add("hidden");
document.getElementById("wheel-modal").classList.remove("hidden");
}

function spinWheel(){
const wheel=document.getElementById("wheel");
const random=Math.random()*100;
let result="PERDISTE";
let rotation=1440;

if(random<=20){result="GANASTE 10%";rotation+=90;}
else if(random<=50){result="GANASTE 5%";rotation+=180;}
else{rotation+=270;}

wheel.style.transform=`rotate(${rotation}deg)`;

setTimeout(()=>{
document.getElementById("result").innerText=result;
},4000);
}

window.onload=()=>{
if(localStorage.getItem("revnUser")){
document.getElementById("register-modal").style.display="none";
document.getElementById("wheel-modal").style.display="none";
}
}


let users = JSON.parse(localStorage.getItem("revnUsers")) || [];

function registerUser(){

const email = document.getElementById("email").value;
const password = document.getElementById("password").value;

if(!email.includes("@") || password.length < 4){
alert("Datos inválidos");
return;
}

users.push({email,password});

localStorage.setItem("revnUsers", JSON.stringify(users));
localStorage.setItem("revnUser", email);

document.getElementById("register-modal").classList.add("hidden");
document.getElementById("wheel-modal").classList.remove("hidden");

}

function loginUser(){

const email = document.getElementById("email").value;
const password = document.getElementById("password").value;

const found = users.find(u => u.email === email && u.password === password);

if(!found){
alert("Cuenta no encontrada");
return;
}

localStorage.setItem("revnUser", email);

document.getElementById("register-modal").style.display="none";

}

function continueGuest(){

document.getElementById("register-modal").style.display="none";

}

