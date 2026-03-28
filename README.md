<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Oliveira Artigos</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
body{font-family:'Poppins',sans-serif;background:#f5f5f5;color:#333;}
header{background:white;padding:15px 30px;display:flex;justify-content:space-between;align-items:center;box-shadow:0 3px 10px rgba(0,0,0,0.1);position:sticky;top:0;z-index:100;}
.logo{font-size:26px;font-weight:700;color:#2563eb;}
nav a{text-decoration:none;color:#333;cursor:pointer;font-weight:500;margin-left:20px;transition:0.3s;}
nav a:hover{color:#2563eb;}
.banner{background:url("https://images.unsplash.com/photo-1445205170230-053b83016050");background-size:cover;background-position:center;height:350px;display:flex;align-items:center;justify-content:center;text-align:center;color:white;}
.banner h1{font-size:48px;background:rgba(0,0,0,0.5);padding:20px 30px;border-radius:10px;}
.container{max-width:1200px;margin:auto;padding:40px 20px;}
.tela{display:none;}.ativa{display:block;}
.produtos{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:25px;}
.produto{background:white;border-radius:12px;overflow:hidden;box-shadow:0 5px 20px rgba(0,0,0,0.1);transition:0.3s;position:relative;}
.produto:hover{transform:translateY(-5px);}
.produto img{width:100%;height:220px;object-fit:cover;}
.info{padding:15px;text-align:center;}
.info h3{margin:10px 0;font-weight:600;}
.preco{font-weight:bold;color:#2563eb;margin-bottom:10px;}
button{background:#2563eb;border:none;color:white;padding:10px 15px;border-radius:8px;cursor:pointer;transition:0.3s;font-weight:500;}
button:hover{background:#1e40af;}
.novo{position:absolute;top:10px;left:10px;background:#2563eb;color:white;font-size:12px;font-weight:600;padding:5px 10px;border-radius:5px;}
.promo{position:absolute;top:10px;right:10px;background:red;color:white;font-size:12px;font-weight:600;padding:5px 10px;border-radius:5px;}
input{width:100%;padding:12px 15px;margin:8px 0;border-radius:8px;border:1px solid #ccc;outline:none;transition:0.3s;}
input:focus{border-color:#2563eb;box-shadow:0 0 5px rgba(37,99,235,0.5);}
form button{width:100%;margin-top:10px;}
.pixbox{background:white;padding:30px;border-radius:12px;max-width:400px;margin:auto;text-align:center;box-shadow:0 5px 20px rgba(0,0,0,0.1);}
h2{margin-bottom:20px;color:#2563eb;}
#pesquisa{margin-bottom:20px;padding:10px;border-radius:8px;border:1px solid #ccc;width:100%;}
li{margin-bottom:10px;}
.remover{background:red;padding:3px 8px;font-size:12px;border-radius:5px;margin-left:10px;}
.categorias{margin-bottom:20px;}
.categorias button{margin-right:10px;padding:8px 12px;border:none;border-radius:5px;background:#ddd;cursor:pointer;transition:0.3s;}
.categorias button:hover{background:#2563eb;color:white;}
footer{text-align:center;padding:20px;background:#2563eb;color:white;margin-top:40px;}
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
<h1>Moda Masculina Premium</h1>
</div>

<div class="container">

<div id="home" class="tela ativa">
<h2>Destaques</h2>
<p>Confira nossas novidades e promoções!</p>
<div class="produtos" id="destaques"></div>
</div>

<div id="loja" class="tela">
<h2>Nossos Produtos</h2>
<input id="pesquisa" type="text" placeholder="Pesquisar produtos..." oninput="filtrarProdutos()">
<div class="categorias">
<button onclick="filtrarCategoria('Todos')">Todos</button>
<button onclick="filtrarCategoria('Camisetas')">Camisetas</button>
<button onclick="filtrarCategoria('Calças')">Calças</button>
<button onclick="filtrarCategoria('Moletons')">Moletons</button>
<button onclick="filtrarCategoria('Jaquetas')">Jaquetas</button>
<button onclick="filtrarCategoria('Tênis')">Tênis</button>
</div>
<div class="produtos" id="produtosLista"></div>
</div>

<div id="login" class="tela">
<h2>Login</h2>
<input id="emailLogin" type="email" placeholder="Email">
<input id="senhaLogin" type="password" placeholder="Senha">
<button onclick="login()">Entrar</button>
</div>

<div id="cadastro" class="tela">
<h2>Criar Conta</h2>
<input id="emailCad" type="email" placeholder="Email">
<input id="senhaCad" type="password" placeholder="Senha">
<button onclick="cadastrar()">Cadastrar</button>
</div>

<div id="carrinho" class="tela">
<h2>Carrinho</h2>
<ul id="lista"></ul>
<p id="total"></p>
<button onclick="pagar()">Ir para pagamento</button>
</div>

<div id="pagamento" class="tela">
<div class="pixbox">
<h2>Pagamento PIX</h2>
<p id="valorPix"></p>
<p>Chave PIX</p>
<b id="pixKey">42778546804</b><br><br>
<button onclick="copiarPix()">Copiar chave PIX</button><br><br>
<button onclick="confirmarPagamento()">Já paguei</button>
</div>
</div>

</div>

<footer>
<p>© 2026 Oliveira Artigos - Todos os direitos reservados</p>
<p>Siga-nos: Instagram | Facebook | WhatsApp</p>
</footer>

<script>
let carrinho = [];
let produtos = [
{name:"Camiseta Premium",preco:79,img:"https://images.unsplash.com/photo-1521572163474-6864f9cf17ab",categoria:"Camisetas",novo:true},
{name:"Calça Jeans",preco:149,img:"https://images.unsplash.com/photo-1541099649105-f69ad21f3246",categoria:"Calças",novo:false},
{name:"Jaqueta Casual",preco:199,img:"https://images.unsplash.com/photo-1529139574466-a303027c1d8b",categoria:"Jaquetas",novo:true},
{name:"Moleton Conforto",preco:129,img:"https://images.unsplash.com/photo-1581091012184-1e8b1f1f6fdf",categoria:"Moletons",novo:false},
{name:"Tênis Esportivo",preco:249,img:"https://images.unsplash.com/photo-1562158071-5187f75a1586",categoria:"Tênis",novo:true},
{name:"Camisa Social",preco:179,img:"https://images.unsplash.com/photo-1600180758895-42c771c7d03b",categoria:"Camisetas",novo:false},
{name:"Camisa Polo",preco:139,img:"https://images.unsplash.com/photo-1602810315794-9e22e61d76f3",categoria:"Camisetas",novo:true},
{name:"Bermuda Casual",preco:89,img:"https://images.unsplash.com/photo-1600180758885-7c1a8b2f8e49",categoria:"Calças",novo:false},
{name:"Moleton Canguru",preco:159,img:"https://images.unsplash.com/photo-1581349481915-9a91df4d57b3",categoria:"Moletons",novo:true}
];

function mostrar(t){
document.querySelectorAll(".tela").forEach(e=>e.classList.remove("ativa"));
document.getElementById(t).classList.add("ativa");
if(t==="loja"){renderizarProdutos(produtos);}
if(t==="home"){renderizarDestaques();}
}

function renderizarProdutos(lista){
let container=document.getElementById("produtosLista");
container.innerHTML="";
lista.forEach(p=>{
container.innerHTML+=`<div class="produto">
${p.novo?'<span class="novo">Novo</span>':''}
<img src="${p.img}">
<div class="info"><h3>${p.nome}</h3><p class="preco">R$${p.preco}</p>
<p>Tamanho: P/M/G | Cor: Variada</p>
<button onclick="addCarrinho('${p.nome}',${p.preco})">Comprar</button>
</div></div>`;
});
}

function renderizarDestaques(){
let container=document.getElementById("destaques");
container.innerHTML="";
produtos.slice(0,4).forEach(p=>{
container.innerHTML+=`<div class="produto">
${p.novo?'<span class="novo">Novo</span>':''}
<img src="${p.img}">
<div class="info"><h3>${p.nome}</h3><p class="preco">R$${p.preco}</p></div></div>`;
});
}

function filtrarProdutos(){
let filtro=document.getElementById("pesquisa").value.toLowerCase();
let filtrados = produtos.filter(p=>p.nome.toLowerCase().includes(filtro));
renderizarProdutos(filtrados);
}

function filtrarCategoria(cat){
if(cat==="Todos"){renderizarProdutos(produtos); return;}
let filtrados = produtos.filter(p=>p.categoria===cat);
renderizarProdutos(filtrados);
}

function addCarrinho(nome,preco){
carrinho.push({nome,preco});
alert("Produto adicionado ao carrinho");
abrirCarrinho();
}

function abrirCarrinho(){mostrar("carrinho");atualizarCarrinho();}
function atualizarCarrinho(){
let lista=document.getElementById("lista");lista.innerHTML="";
let total=0;
carrinho.forEach((p,index)=>{
lista.innerHTML+=`<li>${p.nome} - R$${p.preco} <button class="remover" onclick="removerCarrinho(${index})">X</button></li>`;
total+=p.preco;
});
document.getElementById("total").innerText="Total: R$ "+total;
}

function removerCarrinho(i){carrinho.splice(i,1);atualizarCarrinho();}
function pagar(){let total=0;carrinho.forEach(p=>{total+=p.preco;});document.getElementById("valorPix").innerText="Total: R$ "+total;mostrar("pagamento");}
function copiarPix(){let chave=document.getElementById("pixKey").innerText;navigator.clipboard.writeText(chave);alert("Chave PIX copiada!");}
function confirmarPagamento(){alert("Pedido enviado!");carrinho=[];mostrar("home");}
function cadastrar(){let email=document.getElementById("emailCad").value;let senha=document.getElementById("senhaCad").value;if(email && senha){localStorage.setItem("usuarioEmail",email);localStorage.setItem("usuarioSenha",senha);alert("Conta criada!");mostrar("login");}else{alert("Preencha todos os campos!");}}
function login(){let email=document.getElementById("emailLogin").value;let senha=document.getElementById("senhaLogin").value;let emailSalvo=localStorage.getItem("usuarioEmail");let senhaSalva=localStorage.getItem("usuarioSenha");if(email===emailSalvo && senha===senhaSalva){alert("Login realizado!");mostrar("loja");}else{alert("Email ou senha incorretos");}}
</script>
</body>
</html>
