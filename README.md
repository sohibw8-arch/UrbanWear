<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>UrbanWear | Clothing Store</title>

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family: 'Poppins', sans-serif;
}
body{
  background:#000;
  color:#fff;
}

/* HEADER */
header{
  background:#000;
  padding:15px 20px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}
header h1{
  font-size:22px;
}
header button{
  background:#fff;
  color:#000;
  border:none;
  padding:8px 14px;
  border-radius:20px;
  font-weight:600;
}

/* HERO */
.hero{
  height:230px;
  background:url("https://images.unsplash.com/photo-1512436991641-6745cdb1723f") center/cover no-repeat;
  display:flex;
  align-items:center;
  justify-content:center;
  text-align:center;
}
.hero h2{
  font-size:32px;
}
.hero p{
  opacity:0.8;
}

/* PRODUCTS */
.products{
  padding:25px;
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
  gap:25px;
}
.card{
  background:#fff;
  color:#000;
  border-radius:18px;
  padding:15px;
}
.card img{
  width:100%;
  height:220px;
  object-fit:cover;
  border-radius:14px;
}
.card h3{
  margin:10px 0 5px;
}
.card p{
  font-weight:600;
}
.card button{
  width:100%;
  margin-top:10px;
  padding:10px;
  background:#000;
  color:#fff;
  border:none;
  border-radius:20px;
  cursor:pointer;
}

/* ADMIN */
.admin-panel{
  display:none;
  padding:20px;
  background:#111;
}
.admin-panel input{
  width:100%;
  padding:10px;
  margin:6px 0;
  border-radius:8px;
  border:none;
}
.admin-panel button{
  width:100%;
  padding:10px;
  margin-top:10px;
  background:#fff;
  border:none;
  font-weight:600;
}
</style>
</head>

<body>

<header>
  <h1>UrbanWear</h1>
  <button onclick="openAdmin()">Admin</button>
</header>

<section class="hero">
  <div>
    <h2>UrbanWear</h2>
    <p>Premium Clothing Collection</p>
  </div>
</section>

<section class="products" id="productList"></section>

<section class="admin-panel" id="adminPanel">
  <h2>Add Product</h2>
  <input id="pname" placeholder="Product Name">
  <input id="pprice" placeholder="Price">
  <input id="pimg" placeholder="Image URL">
  <button onclick="addProduct()">Add Product</button>
</section>

<script>
const password = "admin123";
const whatsapp = "919999999999"; // apna number

const sampleProducts = [
 {name:"Oversized Black T-Shirt", price:"799", img:"https://images.unsplash.com/photo-1520975916090-3105956dac38"},
 {name:"White Casual Shirt", price:"1199", img:"https://images.unsplash.com/photo-1602810318383-e386cc2a3ccf"},
 {name:"Blue Denim Jacket", price:"2499", img:"https://images.unsplash.com/photo-1512436991641-6745cdb1723f"},
 {name:"Grey Hoodie", price:"1799", img:"https://images.unsplash.com/photo-1520974735194-6c4f28a88b1d"},
 {name:"Black Jeans", price:"1599", img:"https://images.unsplash.com/photo-1542272604-787c3835535d"}
];

function loadSamples(){
 sampleProducts.forEach(p=>{
  productList.innerHTML+=cardHTML(p.name,p.price,p.img);
 });
}
loadSamples();

function cardHTML(name,price,img){
 return `
 <div class="card">
  <img src="${img}">
  <h3>${name}</h3>
  <p>₹ ${price}</p>
  <button onclick="order('${name}','${price}')">Buy Now</button>
 </div>`;
}

function order(name,price){
 window.open(`https://wa.me/${whatsapp}?text=I want to buy ${name} for ₹${price}`);
}

function openAdmin(){
 let pass=prompt("Admin Password");
 if(pass===password){
  adminPanel.style.display="block";
 }else alert("Wrong Password");
}

function addProduct(){
 productList.innerHTML+=cardHTML(pname.value,pprice.value,pimg.value);
 pname.value="";pprice.value="";pimg.value="";
}
</script>

</body>
</html>
