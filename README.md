<!DOCTYPE html>
<html lang="pt-BR">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Oliveira Artigos</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;600&display=swap" rel="stylesheet">

<style>

body{
margin:0;
font-family:'Poppins',sans-serif;
background:#f5f5f5;
}

/* HEADER */

header{
background:white;
padding:15px 30px;
display:flex;
justify-content:space-between;
align-items:center;
box-shadow:0 2px 10px rgba(0,0,0,0.1);
}

.logo{
font-size:22px;
font-weight:600;
color:#2563eb;
}

/* MENU */

nav{
display:flex;
gap:20px;
}

nav a{
text-decoration:none;
color:#333;
cursor:pointer;
font-weight:500;
}

/* BANNER */

.banner{
background:url("https://images.unsplash.com/photo-1445205170230-053b83016050");
background-size:cover;
background-position:center;
height:350px;
display:flex;
align-items:center;
justify-content:center;
color:white;
text-align:center;
}

.banner h1{
font-size:45px;
background:rgba(0,0,0,0.5);
padding:20px;
border-radius:10px;
}

/* CONTAINER */

.container{
max-width:1200px;
margin:auto;
padding:30px;
}

.tela{display:none}
.ativa{display:block}

/* PRODUTOS */

.produtos{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
gap:25px;
}

.produto{
background:white;
border-radius:12px;
overflow:hidden;
box-shadow:0 4px 15px rgba(0,0,0,0.1);
transition:0.3s;
}

.produto:hover{
transform:translateY(-5px);
}

.produto img{
width:100%;
height:220px;
object-fit:cover;
}

.info{
padding:15px;
text-align:center;
}

.info h3{
margin:10px 0;
}

.preco{
font-weight:bold;
color:#2563eb;
margin-bottom:10px;
}

button{
background:#2563eb;
border:none;
color:white;
padding:10px 15px;
border-radius:8px;
cursor:pointer;
}

button:hover{
background:#1e40af;
}

/* CARRINHO */

.pixbox{
background:white;
padding:30px;
border-radius:12px;
max-width:400px;
margin:auto;
text-align:center;
box-shadow:0 5px 20px rgba(0,0,0,0.1);
}

</style>

</head>

<body>

<header>

<div class="logo">Oliveira Artigos</div>

<nav>

<a onclick="mostrar('home')">Início</a>
<a onclick="mostrar('loja')">Loja</a>
<a onclick="mostrar('login')">Login</a>
<a onclick="mostrar('cadastro')">Cadastro</a>
<a onclick="abrirCarrinho()">Carrinho</a>

</nav>

</header>

<div class="banner">
<h1>Moda Masculina Estilo Premium</h1>
</div>

<div class="container">

<!-- HOME -->

<div id="home" class="tela ativa">

<h2>Produtos em destaque</h2>

</div>

<!-- LOJA -->

<div id="loja" class="tela">

<h2>Nossos Produtos</h2>

<div class="produtos">

<div class="produto">

<img src="https://images.unsplash.com/photo-1521572163474-6864f9cf17ab">

<div class="info">

<h3>Camiseta Premium</h3>

<p class="preco">R$79</p>

<button onclick="addCarrinho('Camiseta',79)">Comprar</button>

</div>

</div>

<div class="produto">

<img src="https://images.unsplash.com/photo-1541099649105-f69ad21f3246">

<div class="info">

<h3>Calça Jeans</h3>

<p class="preco">R$149</p>

<button onclick="addCarrinho('Calça Jeans',149)">Comprar</button>

</div>

</div>

<div class="produto">

<img src="https://images.unsplash.com/photo-1529139574466-a303027c1d8b">

<div class="info">

<h3>Jaqueta</h3>

<p class="preco">R$199</p>

<button onclick="addCarrinho('Jaqueta',199)">Comprar</button>

</div>

</div>

</div>

</div>

<!-- LOGIN -->

<div id="login" class="tela">

<h2>Login</h2>

<input id="emailLogin" placeholder="Email"><br><br>

<input id="senhaLogin" type="password" placeholder="Senha"><br><br>

<button onclick="login()">Entrar</button>

</div>

<!-- CADASTRO -->

<div id="cadastro" class="tela">

<h2>Criar Conta</h2>

<input id="emailCad" placeholder="Email"><br><br>

<input id="senhaCad" type="password" placeholder="Senha"><br><br>

<button onclick="cadastrar()">Cadastrar</button>

</div>

<!-- CARRINHO -->

<div id="carrinho" class="tela">

<h2>Carrinho</h2>

<ul id="lista"></ul>

<p id="total"></p>

<button onclick="pagar()">Ir para pagamento</button>

</div>

<!-- PAGAMENTO -->

<div id="pagamento" class="tela">

<div class="pixbox">

<h2>Pagamento PIX</h2>

<p id="valorPix"></p>

<p>Chave PIX</p>

<b id="pixKey">42778546804</b>

<br><br>

<button onclick="copiarPix()">Copiar chave PIX</button>

<br><br>

<button onclick="confirmarPagamento()">Já paguei</button>

</div>

</div>

</div>

<script>

let carrinho=[];

function mostrar(t){

document.querySelectorAll(".tela").forEach(e=>e.classList.remove("ativa"));

document.getElementById(t).classList.add("ativa");

}

function addCarrinho(nome,preco){

carrinho.push({nome,preco});

alert("Produto adicionado ao carrinho");

}

function abrirCarrinho(){

mostrar("carrinho");

let lista=document.getElementById("lista");

lista.innerHTML="";

let total=0;

carrinho.forEach((p)=>{

lista.innerHTML+=`<li>${p.nome} - R$${p.preco}</li>`;

total+=p.preco;

});

document.getElementById("total").innerText="Total: R$ "+total;

}

function pagar(){

let total=0;

carrinho.forEach(p=>{

total+=p.preco;

});

document.getElementById("valorPix").innerText="Total: R$ "+total;

mostrar("pagamento");

}

function copiarPix(){

let chave=document.getElementById("pixKey").innerText;

navigator.clipboard.writeText(chave);

alert("Chave PIX copiada!");

}

function confirmarPagamento(){

alert("Pedido enviado!");

carrinho=[];

mostrar("home");

}

function cadastrar(){

let email=document.getElementById("emailCad").value;
let senha=document.getElementById("senhaCad").value;

localStorage.setItem("usuarioEmail",email);
localStorage.setItem("usuarioSenha",senha);

alert("Conta criada!");

mostrar("login");

}

function login(){

let email=document.getElementById("emailLogin").value;
let senha=document.getElementById("senhaLogin").value;

let emailSalvo=localStorage.getItem("usuarioEmail");
let senhaSalva=localStorage.getItem("usuarioSenha");

if(email===emailSalvo && senha===senhaSalva){

alert("Login realizado!");

mostrar("loja");

}else{

alert("Email ou senha incorretos");

}

}

</script>

</body>
</html>
