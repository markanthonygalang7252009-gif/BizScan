# BizScan
Nothing
<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BizScan Food & Drinks Marketplace</title>
<style>
body { font-family: Arial, sans-serif; margin:0; padding:0; background: #1c1c1c; color: #f0f0f0;}
header { background:#111; color:#f0f0f0; padding:25px 20px; text-align:center; box-shadow:0 4px 6px rgba(0,0,0,0.3);}
header h1 { margin:0; font-size:26px;}
header p { margin:10px auto 0; font-size:15px; max-width:800px; line-height:1.5;}
.container { width:90%; max-width:1000px; margin:30px auto; background:#2c2c2c; padding:25px; border-radius:12px; box-shadow:0 4px 10px rgba(0,0,0,0.5);}
h2 { color:#ffcc00; margin-top:0;}
.product-form input { width:100%; padding:10px; margin:5px 0; border-radius:5px; border:1px solid #555; background:#1c1c1c; color:#f0f0f0;}
.product-form button { width:100%; padding:12px; background:#ffcc00; color:#111; border:none; cursor:pointer; margin-top:5px; border-radius:5px; font-weight:bold;}
.product-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(220px,1fr)); gap:15px; margin-top:20px;}
.product-card { background:#3c3c3c; border-radius:8px; padding:10px; box-shadow:0 2px 8px rgba(0,0,0,0.5); position:relative; transition: transform 0.2s;}
.product-card:hover { transform:scale(1.03);}
.product-card img { width:100%; border-radius:5px; height:150px; object-fit:cover; margin-bottom:8px;}
.product-card .price { font-weight:bold; margin-top:5px; color:#ffcc00;}
.order-btn, .remove-btn { width:48%; padding:8px; margin-top:8px; border:none; color:white; cursor:pointer; border-radius:5px; font-weight:bold;}
.order-btn { background:#28a745;}
.remove-btn { background:#dc3545; float:right;}
.clear { clear:both;}
</style>
</head>
<body>
<header>
<h1>BizScan: Promotional QR Code for Grade 12 Entrepreneurship Business Simulation</h1>
<p>BizScan is a QR-code–based promotional project designed to showcase the upcoming products and services of Grade 12 young business owners during their Entrepreneurship Business Simulation. By scanning the QR code, students, teachers, and staff can access a digital platform that features product information, promotional commercials, prices, and ordering details. This project allows ABM students to apply marketing, management, and entrepreneurial skills while promoting innovation and awareness of future business products within the school.</p>
</header>
<div class="container">
<h2>Add Product</h2>
<div class="product-form">
<input id="imgInput" type="text" placeholder="Image URL">
<input id="nameInput" type="text" placeholder="Product Name">
<input id="descInput" type="text" placeholder="Description">
<input id="priceInput" type="number" placeholder="Price (₱)">
<button onclick="addProduct()">Add Product</button>
</div>
<h2>Products</h2>
<div class="product-grid" id="productGrid"></div>
</div>
<script>
let products = JSON.parse(localStorage.getItem('products')) || [];
function displayProducts(){
const grid=document.getElementById('productGrid');
grid.innerHTML='';
products.forEach((p,index)=>{
grid.innerHTML+=`<div class="product-card"><img src="${p.img}"><h3>${p.name}</h3><p>${p.desc}</p><p class="price">₱${p.price}</p><button class="order-btn">Order Now</button><button class="remove-btn" onclick="removeProduct(${index})">Remove</button><div class="clear"></div></div>`;
});
}
function addProduct(){
const img=document.getElementById('imgInput').value;
const name=document.getElementById('nameInput').value;
const desc=document.getElementById('descInput').value;
const price=document.getElementById('priceInput').value;
if(!img||!name||!desc||!price) return alert("Fill all fields!");
products.push({img,name,desc,price});
localStorage.setItem('products',JSON.stringify(products));
displayProducts();
document.getElementById('imgInput').value='';
document.getElementById('nameInput').value='';
document.getElementById('descInput').value='';
document.getElementById('priceInput').value='';
}
function removeProduct(index){
if(!confirm("Remove this product?")) return;
products.splice(index,1);
localStorage.setItem('products',JSON.stringify(products));
displayProducts();
}
displayProducts();
</script>
</body>
</html>
