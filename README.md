<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MarkShop Elite</title>

<style>
body {margin:0;font-family:Arial;background:#f5f5f5;}

header {
background:#131921;color:white;
padding:15px;display:flex;
justify-content:space-between;align-items:center;
}

header h1 {margin:0;}

.search-box input {
padding:8px;border-radius:5px;border:none;
}

.cart {
background:orange;
padding:8px 12px;
border-radius:5px;
cursor:pointer;
}

nav {
background:#232f3e;color:white;
padding:10px;display:flex;gap:15px;
}

nav span {cursor:pointer;}

.container {
padding:20px;
display:grid;
grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
gap:20px;
}

.product {
background:white;
padding:15px;
border-radius:10px;
text-align:center;
transition:0.2s;
}

.product:hover {transform:scale(1.05);}

.product img {
width:100%;height:160px;
object-fit:cover;border-radius:10px;
}

.price {color:green;font-weight:bold;}

button, .btn {
background:orange;
border:none;
padding:10px;
border-radius:5px;
cursor:pointer;
margin-top:10px;
text-decoration:none;
display:inline-block;
color:black;
}

#cartBox {
position:fixed;
right:0;top:0;
width:300px;height:100%;
background:white;
box-shadow:-2px 0 10px rgba(0,0,0,0.2);
padding:20px;
display:none;
overflow-y:auto;
}

#popup {
position:fixed;
bottom:20px;
left:20px;
background:black;
color:white;
padding:15px;
border-radius:10px;
display:none;
}

</style>
</head>

<body>

<header>
<h1>🛒 MarkShop Elite</h1>
<input type="text" id="search" placeholder="Rechercher..." onkeyup="searchProduct()">
<div class="cart" onclick="toggleCart()">🛒 (<span id="count">0</span>)</div>
</header>

<nav>
<span onclick="filter('all')">Tout</span>
<span onclick="filter('tech')">Tech</span>
<span onclick="filter('accessories')">Accessoires</span>
</nav>

<div class="container" id="products">

<!-- PRODUIT 1 -->
<div class="product" data-category="tech">
<img src="https://via.placeholder.com/200">
<h3>Smartphone</h3>
<p>Rapide et puissant</p>
<div class="price">$120</div>
<p style="color:red;">⚠️ Stock limité</p>
<p>⭐⭐⭐⭐⭐ (124 avis)</p>
<button onclick="addToCart('Smartphone',120)">Ajouter</button>
<a href="TON LIEN AFFILIÉ" class="btn" target="_blank">Acheter</a>
</div>

<!-- PRODUIT 2 -->
<div class="product" data-category="accessories">
<img src="https://via.placeholder.com/200">
<h3>Power Bank</h3>
<p>Batterie portable ultra rapide</p>
<div class="price">$25</div>
<p style="color:red;">⚠️ Stock limité</p>
<p>⭐⭐⭐⭐⭐ (89 avis)</p>
<button onclick="addToCart('Power Bank',25)">Ajouter</button>
<a href="TON LIEN AFFILIÉ" class="btn" target="_blank">Acheter</a>
</div>

<!-- PRODUIT 3 -->
<div class="product" data-category="tech">
<img src="https://via.placeholder.com/200">
<h3>Casque Bluetooth</h3>
<p>Son immersif</p>
<div class="price">$40</div>
<p style="color:red;">⚠️ Stock limité</p>
<p>⭐⭐⭐⭐⭐ (63 avis)</p>
<button onclick="addToCart('Casque',40)">Ajouter</button>
<a href="TON LIEN AFFILIÉ" class="btn" target="_blank">Acheter</a>
</div>

</div>

<!-- PANIER -->
<div id="cartBox">
<h2>Panier</h2>
<ul id="cartItems"></ul>
<h3>Total: $<span id="total">0</span></h3>
<button onclick="checkout()">Commander</button>
</div>

<!-- POPUP PROMO -->
<div id="popup">
🎁 -10% aujourd’hui seulement !
</div>

<footer style="background:#131921;color:white;text-align:center;padding:15px;margin-top:20px;">
© 2026 MarkShop Elite
</footer>

<script>

let cart = [];

// PANIER
function addToCart(name, price) {
cart.push({name, price});
updateCart();
}

function updateCart() {
let list = document.getElementById("cartItems");
let total = 0;
list.innerHTML = "";

cart.forEach(item => {
let li = document.createElement("li");
li.innerText = item.name + " - $" + item.price;
list.appendChild(li);
total += item.price;
});

document.getElementById("total").innerText = total;
document.getElementById("count").innerText = cart.length;
}

function toggleCart() {
let box = document.getElementById("cartBox");
box.style.display = box.style.display === "block" ? "none" : "block";
}

function checkout() {
alert("Ajoute Stripe ou PayPal ici pour encaisser");
}

// RECHERCHE
function searchProduct() {
let input = document.getElementById("search").value.toLowerCase();
let products = document.querySelectorAll(".product");

products.forEach(p => {
let title = p.querySelector("h3").innerText.toLowerCase();
p.style.display = title.includes(input) ? "block" : "none";
});
}

// FILTRE
function filter(cat) {
let products = document.querySelectorAll(".product");

products.forEach(p => {
if (cat === "all" || p.dataset.category === cat) {
p.style.display = "block";
} else {
p.style.display = "none";
}
});
}

// POPUP AUTO
setTimeout(() => {
document.getElementById("popup").style.display = "block";
}, 3000);

</script>

</body>
</html>
