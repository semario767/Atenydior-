<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>My Shop</title>
<style>
/* ===== Global Styles ===== */
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f8f9fa; color: #333; }

/* ===== Header ===== */
header {
    background: linear-gradient(90deg, #007BFF, #00AFFF);
    color: #fff;
    text-align: center;
    padding: 25px 10px;
    box-shadow: 0 6px 10px rgba(0,0,0,0.1);
    position: relative;
}
header h1 { font-size: 2.2rem; letter-spacing: 1px; }

/* ===== Cart Counter ===== */
#cart-counter {
    position: absolute;
    top: 20px;
    right: 20px;
    background-color: #ff4500;
    color: #fff;
    font-weight: bold;
    padding: 6px 12px;
    border-radius: 50%;
    font-size: 1rem;
    min-width: 28px;
    text-align: center;
    cursor: pointer;
    box-shadow: 0 2px 6px rgba(0,0,0,0.2);
}

/* ===== Navigation ===== */
nav { display: flex; justify-content: center; background-color: #0056b3; flex-wrap: wrap; }
nav a {
    color: white;
    text-decoration: none;
    padding: 15px 25px;
    transition: all 0.3s;
    font-weight: 600;
    border-radius: 5px;
    margin: 5px;
}
nav a:hover { background-color: #004080; transform: scale(1.05); }

/* ===== Main Sections ===== */
main { padding: 25px 20px; min-height: 75vh; }
.section { display: none; animation: fadeIn 0.5s ease; }

/* ===== Carousel ===== */
.carousel {
    position: relative;
    max-width: 100%;
    margin-bottom: 30px;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 6px 15px rgba(0,0,0,0.1);
}
.carousel img { width: 100%; height: 300px; object-fit: cover; display: none; }
.carousel img.active { display: block; animation: fadeSlide 1s ease; }
@keyframes fadeSlide { from {opacity:0;} to {opacity:1;} }

/* ===== Banner ===== */
.banner {
    background: linear-gradient(90deg, #00aaff, #007BFF);
    color: white;
    text-align: center;
    padding: 60px 25px;
    border-radius: 12px;
    margin-bottom: 35px;
    box-shadow: 0 6px 15px rgba(0,0,0,0.1);
}
.banner h2 { font-size: 2.5rem; margin-bottom: 15px; letter-spacing: 1px; }
.banner p { font-size: 1.25rem; }

/* ===== Filters ===== */
.filters { text-align: center; margin-bottom: 20px; }
.filters button {
    background-color: #007BFF;
    color: #fff;
    border: none;
    padding: 8px 15px;
    margin: 0 5px 10px 5px;
    border-radius: 6px;
    cursor: pointer;
    font-weight: 600;
    transition: all 0.3s;
}
.filters button:hover, .filters button.active { background-color: #0056b3; }

/* ===== Search ===== */
#search { width: 100%; max-width: 400px; padding: 10px 15px; border-radius: 6px; border: 1px solid #ccc; margin: 0 auto 25px auto; display: block; }

/* ===== Shop ===== */
.products { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 25px; }
.product {
    background: #fff;
    padding: 18px;
    border-radius: 12px;
    text-align: center;
    transition: transform 0.3s, box-shadow 0.3s;
    box-shadow: 0 4px 12px rgba(0,0,0,0.08);
}
.product:hover { transform: translateY(-5px); box-shadow: 0 10px 20px rgba(0,0,0,0.15); }
.product img { width: 100%; height: 160px; object-fit: cover; border-radius: 12px; margin-bottom: 12px; }
.product h3 { margin-bottom: 6px; font-size: 1.2rem; font-weight: 600; }
.product p.desc { font-size: 0.95rem; margin-bottom: 8px; color: #555; }
.product p.price { font-weight: bold; font-size: 1.1rem; margin-bottom: 12px; }

/* ===== Buttons ===== */
button { background-color: #007BFF; color: white; border: none; padding: 12px 20px; cursor: pointer; border-radius: 8px; font-weight: 600; font-size: 0.95rem; transition: all 0.3s; }
button:hover { background-color: #0056b3; transform: translateY(-2px); box-shadow: 0 4px 12px rgba(0,0,0,0.2); }

/* ===== Contact ===== */
form { max-width: 520px; margin: 0 auto; background-color: #fff; padding: 30px; border-radius: 12px; box-shadow: 0 6px 15px rgba(0,0,0,0.1); }
input, textarea { width: 100%; padding: 14px; margin-bottom: 18px; border-radius: 8px; border: 1px solid #ccc; transition: all 0.3s; font-size: 1rem; }
input:focus, textarea:focus { border-color: #007BFF; outline: none; box-shadow: 0 0 8px rgba(0,123,255,0.3); }
form button { width: 100%; font-size: 1.05rem; border-radius: 8px; }

/* ===== Footer ===== */
footer { text-align: center; background-color: #007BFF; color: white; padding: 18px 10px; margin-top: 35px; border-top-left-radius: 12px; border-top-right-radius: 12px; box-shadow: 0 -4px 8px rgba(0,0,0,0.1); }

/* ===== Cart Modal ===== */
#cart-modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); justify-content: center; align-items: center; }
#cart-modal .modal-content { background: #fff; padding: 25px; border-radius: 12px; width: 90%; max-width: 450px; position: relative; box-shadow: 0 8px 20px rgba(0,0,0,0.2); animation: slideIn 0.3s ease; }
#cart-modal h2 { margin-bottom: 18px; font-size: 1.5rem; }
#cart-modal .close { position: absolute; top: 12px; right: 18px; cursor: pointer; font-weight: bold; font-size: 1.3rem; color: #555; }
#cart-items li { margin-bottom: 14px; display: flex; justify-content: space-between; align-items: center; font-size: 1rem; }
.quantity-control { display: flex; align-items: center; gap: 6px; }
.quantity-control button { background-color: #007BFF; padding: 4px 10px; font-size: 0.9rem; border-radius: 6px; }
#cart-total { margin-top: 12px; font-weight: bold; font-size: 1.15rem; }
#checkout-btn { margin-top: 15px; width: 100%; background-color: #28a745; font-weight: 600; padding: 12px; font-size: 1rem; }
#checkout-btn:hover { background-color: #1e7e34; transform: translateY(-2px); box-shadow: 0 4px 12px rgba(0,0,0,0.2); }

/* ===== Animations ===== */
@keyframes fadeIn { from {opacity: 0;} to {opacity: 1;} }
@keyframes slideIn { from {transform: translateY(-30px); opacity: 0;} to {transform: translateY(0); opacity: 1;} }
@media (max-width: 600px) { header h1 { font-size: 1.7rem; } .banner h2 { font-size: 1.8rem; } .banner p { font-size: 1rem; } .products { grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 15px; } }
</style>
</head>
<body>

<header>
    <h1>My Shop</h1>
    <div id="cart-counter" onclick="toggleCart()">0</div>
</header>

<nav>
    <a onclick="showSection('home')">Home</a>
    <a onclick="showSection('shop')">Shop</a>
    <a onclick="showSection('contact')">Contact</a>
</nav>

<main>
    <div id="home" class="section">
        <div class="carousel">
            <img src="https://via.placeholder.com/800x300?text=Featured+1" class="active" alt="Featured 1">
            <img src="https://via.placeholder.com/800x300?text=Featured+2" alt="Featured 2">
            <img src="https://via.placeholder.com/800x300?text=Featured+3" alt="Featured 3">
        </div>
        <div class="banner">
            <h2>Welcome to the Best Products!</h2>
            <p>Discover our amazing collection at unbeatable prices.</p>
        </div>
    </div>

    <div id="shop" class="section">
        <input type="text" id="search" placeholder="Search products..." onkeyup="searchProducts()">
        <div class="filters">
            <button onclick="filterCategory('All')" class="active">All</button>
            <button onclick="filterCategory('Electronics')">Electronics</button>
            <button onclick="filterCategory('Fashion')">Fashion</button>
            <button onclick="filterCategory('Home')">Home</button>
        </div>
        <div class="products">
            <div class="product" data-name="Smartphone" data-price="200" data-category="Electronics">
                <img src="https://via.placeholder.com/220?text=Smartphone" alt="Smartphone">
                <h3>Smartphone</h3>
                <p class="desc">Latest model with high-speed performance.</p>
                <p class="price">$200</p>
                <button onclick="addToCart(this)">Add to Cart</button>
            </div>
            <div class="product" data-name="T-Shirt" data-price="25" data-category="Fashion">
                <img src="https://via.placeholder.com/220?text=T-Shirt" alt="T-Shirt">
                <h3>T-Shirt</h3>
                <p class="desc">Comfortable and stylish.</p>
                <p class="price">$25</p>
                <button onclick="addToCart(this)">Add to Cart</button>
            </div>
            <div class="product" data-name="Coffee Maker" data-price="50" data-category="Home">
                <img src="https://via.placeholder.com/220?text=Coffee+Maker" alt="Coffee Maker">
                <h3>Coffee Maker</h3>
                <p class="desc">Brew your perfect coffee every morning.</p>
                <p class="price">$50</p>
                <button onclick="addToCart(this)">Add to Cart</button>
            </div>
            <div class="product" data-name="Headphones" data-price="80" data-category="Electronics">
                <img src="https://via.placeholder.com/220?text=Headphones" alt="Headphones">
                <h3>Headphones</h3>
                <p class="desc">Crystal-clear sound quality.</p>
                <p class="price">$80</p>
                <button onclick="addToCart(this)">Add to Cart</button>
            </div>
        </div>
    </div>

    <div id="contact" class="section">
        <form onsubmit="event.preventDefault(); sendMessage();">
            <input type="text" id="name" placeholder="Your Name" required>
            <input type="email" id="email" placeholder="Your Email" required>
            <textarea id="message" rows="5" placeholder="Your Message" required></textarea>
            <button type="submit">Send Message</button>
        </form>
    </div>
</main>

<footer>
    &copy; 2025 My Shop
</footer>

<div id="cart-modal">
    <div class="modal-content">
        <span class="close" onclick="toggleCart()">&times;</span>
        <h2>Your Cart</h2>
        <ul id="cart-items"></ul>
        <p id="cart-total"></p>
        <button id="checkout-btn" onclick="checkout()">Checkout</button>
    </div>
</div>

<script>
function showSection(id) {
    document.querySelectorAll('.section').forEach(s => s.style.display='none');
    document.getElementById(id).style.display='block';
}
showSection('home');

let cart = {};

function addToCart(button){
    const product = button.parentElement;
    const name = product.dataset.name;
    const price = Number(product.dataset.price);
    if(cart[name]) cart[name].quantity++;
    else cart[name] = {price: price, quantity: 1};
    updateCartCounter();
    alert(name + " added to cart!");
}

function updateCartCounter(){
    const count = Object.values(cart).reduce((sum,i)=>sum+i.quantity,0);
    document.getElementById('cart-counter').innerText = count;
}

function toggleCart(){
    const modal = document.getElementById('cart-modal');
    if(modal.style.display==='flex') modal.style.display='none';
    else { showCartItems(); modal.style.display='flex'; }
}

function showCartItems(){
    const itemsContainer = document.getElementById('cart-items');
    const totalContainer = document.getElementById('cart-total');
    itemsContainer.innerHTML='';
    let total=0;
    for(const [name,item] of Object.entries(cart)){
        const li=document.createElement('li');
        li.innerHTML = `<span>${name} - $${item.price * item.quantity}</span>
        <div class="quantity-control">
        <button onclick="changeQuantity('${name}', -1)">-</button>
        <span>${item.quantity}</span>
        <button onclick="changeQuantity('${name}', 1)">+</button>
        <button onclick="removeFromCart('${name}')">Remove</button>
        </div>`;
        itemsContainer.appendChild(li);
        total += item.price * item.quantity;
    }
    totalContainer.textContent = `Total: $${total}`;
}

function changeQuantity(name, delta){
    if(cart[name]){
        cart[name].quantity += delta;
        if(cart[name].quantity <=0) delete cart[name];
        updateCartCounter();
        showCartItems();
    }
}

function removeFromCart(name){
    delete cart[name];
    updateCartCounter();
    showCartItems();
}

function checkout(){
    if(Object.keys(cart).length === 0){
        alert("Your cart is empty!");
        return;
    }
    alert("Thank you for your purchase! Total: $" + Object.values(cart).reduce((sum,i)=>sum+i.price*i.quantity,0));
    cart = {};
    updateCartCounter();
    showCartItems();
    toggleCart();
}

function sendMessage(){
    const name=document.getElementById("name").value;
    const email=document.getElementById("email").value;
    const message=document.getElementById("message").value;
    if(name && email && message){
        alert("Thank you, "+name+"! Your message has been sent.");
        document.getElementById("name").value='';
        document.getElementById("email").value='';
        document.getElementById("message").value='';
    } else alert("Please fill all fields.");
}

/* ===== Carousel Script ===== */
let slideIndex = 0;
const slides = document.querySelectorAll('.carousel img');
function showSlides(){
    slides.forEach(s => s.classList.remove('active'));
    slideIndex = (slideIndex+1) % slides.length;
    slides[slideIndex].classList.add('active');
}
setInterval(showSlides, 3000);

/* ===== Search and Filter ===== */
function searchProducts(){
    const search = document.getElementById('search').value.toLowerCase();
    document.querySelectorAll('.products .product').forEach(p=>{
        const name = p.dataset.name.toLowerCase();
        p.style.display = name.includes(search) ? 'block' : 'none';
    });
}

function filterCategory(category){
    document.querySelectorAll('.filters button').forEach(b=>b.classList.remove('active'));
    event.target.classList.add('active');
    document.querySelectorAll('.products .product').forEach(p=>{
        p.style.display = (category==='All' || p.dataset.category===category) ? 'block' : 'none';
    });
}
</script>

</body>
</html>
