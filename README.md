
<!DOCTYPE html>
<html lang="pt-BR">
<head><script type="text/javascript" src="/___vscode_livepreview_injected_script"></script>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>AppVendas</title>

  <!-- Ícones para PWA -->
  <link rel="manifest" href="manifest.json" />
  <link rel="icon" sizes="192x192" href="https://img.icons8.com/?size=100&id=85080&format=png" type="image/png" />
  <link rel="icon" sizes="512x512" href="https://cdn-icons-png.flaticon.com/512/6012/6012718.png" type="image/png" />

  <meta name="theme-color" content="#6200ea" />

  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body, html {
      font-family: 'Arial', sans-serif;
      height: 100%;
      background-color: #f5f5f5;
      color: #333; 
    }
    #app { display: flex; flex-direction: column; height: 100vh; }
    header {
      background-color: #6200ea;
      color: white;
      padding: 1rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: relative;
      z-index: 1001;
    }
    header h1 { font-size: 1.5rem; }
    header button#btn-menu {
      background: none;
      border: none;
      color: white;
      font-size: 1.8rem;   
      cursor: pointer;
      user-select: none;
    }
    nav#menu-lateral {
      position: fixed;
      top: 0;
      left: 0;
      width: 240px;
      height: 100%;
      background-color: #3700b3;
      color: white;
      padding: 1rem;
      transform: translateX(-260px);
      transition: transform 0.3s ease;
      z-index: 1100;
      display: flex;
      flex-direction: column;
    }
    nav#menu-lateral.show { transform: translateX(0); }
    nav#menu-lateral button#btn-close-menu {
      background: none;
      border: none;
      color: white;
      font-size: 2rem;
      cursor: pointer;
      align-self: flex-end;
      margin-bottom: 1rem;
      user-select: none;
    }
    nav#menu-lateral ul {
      list-style: none;
      margin-top: 1rem;
      flex-grow: 1;
    }
    nav#menu-lateral ul li {
      margin-bottom: 1rem;
    }
    nav#menu-lateral a {
      color: white;
      text-decoration: none;
      display: block;
      font-size: 1.1rem;
      cursor: pointer;
      user-select: none;
      transition: color 0.2s;
    }
    nav#menu-lateral a:hover {
      color: #bb86fc;
    }
    main#main-content {
      flex: 1;
      overflow-y: auto;
      padding: 1rem;
      margin-top: 0.5rem;
    }
    footer {
      background-color: #6200ea;
      color: white;
      text-align: center;
      padding: 0.75rem;
    }
    /* Cards */
    .card {
      background: white;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      overflow: hidden;
      margin-bottom: 1rem;
      display: flex;
      flex-direction: column;
    }
    .card img {
      width: 100%;
      object-fit: cover;
      height: 200px;
    }
    .card .info {
      padding: 1rem;
    }
    .card .info h3 {
      font-size: 1.2rem;
      margin-bottom: 0.5rem;
    }
    .card .info p {
      margin-bottom: 0.5rem;
    }
    .card .info .price {
      font-weight: bold;
      margin-bottom: 0.75rem;
      color: #6200ea;
    }
    .card .info button {
      background-color: #6200ea;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s ease;
      user-select: none;
    }
    .card .info button:hover {
      background-color: #3700b3;
    }
    /* Forms */
    .form-container {
      background: white;
      padding: 1rem;
      border-radius: 8px;
      max-width: 400px;
      margin: 0 auto;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
    .form-container h2 {
      margin-bottom: 1rem;
      text-align: center;
    }
    .form-container label {
      display: block;
      margin-bottom: 0.25rem;
      font-weight: 600;
    }
    .form-container input {
      width: 100%;
      padding: 0.5rem;
      margin-bottom: 1rem;
      border: 1px solid #ccc;
      border-radius: 4px;
      font-size: 1rem;
    }
    .form-container button {
      background-color: #6200ea;
      color: white;
      border: none;
      padding: 0.75rem;
      width: 100%;
      border-radius: 4px;
      cursor: pointer;
      font-size: 1.1rem;
      transition: background-color 0.3s ease;
      user-select: none;
    }
    .form-container button:hover {
      background-color: #3700b3;
    }
    /* Carrinho */
    .cart-item {
      display: flex;
      align-items: center;
      margin-bottom: 1rem;
      background: white;
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    }
    .cart-item img {
      width: 80px;
      height: 80px;
      object-fit: cover;
    }
    .cart-item .details {
      flex: 1;
      padding: 0.5rem 1rem;
    }
    .cart-item .details h4 {
      margin-bottom: 0.3rem;
    }
    .cart-item .details p {
      margin-bottom: 0.25rem;
    }
    .cart-item .actions {
      padding: 0.5rem;
    }
    .cart-item .actions button {
      background-color: #b00020;
      border: none;
      color: white;
      padding: 0.5rem 0.75rem;
      border-radius: 4px;
      cursor: pointer;
      user-select: none;
      transition: background-color 0.3s ease;
    }
    .cart-item .actions button:hover {
      background-color: #7a0014;
    }
    .btn-whatsapp {
      background-color: #25D366;
      color: white;
      border: none;
      padding: 0.75rem 1rem;
      border-radius: 4px;
      cursor: pointer;
      font-size: 1rem;
      margin-top: 1rem;
      width: 100%;
      user-select: none;
      transition: background-color 0.3s ease;
    }
    .btn-whatsapp:hover {
      background-color: #1da851;
    }
    /* Slide de propagandas */
    .slide-container {
      position: relative;
      width: 100%;
      max-width: 700px;
      margin: 1rem auto;
      overflow: hidden;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      user-select: none;
    }
    .slides {
      display: flex;
      transition: transform 0.5s ease-in-out;
      width: 100%;
    }
    .slide {
      min-width: 100%;
      box-sizing: border-box;
      position: relative;
      color: white;
      text-align: center;
      background-size: cover;
      background-position: center;
      height: 250px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 1rem;
      font-size: 1.5rem;
      font-weight: bold;
      text-shadow: 1px 1px 6px rgba(0,0,0,0.7);
    }
    .slide p {
      font-weight: normal;
      font-size: 1rem;
      margin-top: 0.5rem;
    }
    /* Cupom */
    .cupom-container {
      max-width: 400px;
      margin: 0.5rem auto 1rem;
      display: flex;
      gap: 0.5rem;
    }
    .cupom-container input {
      flex-grow: 1;
      padding: 0.5rem;
      font-size: 1rem;
      border-radius: 4px;
      border: 1px solid #ccc;
    }
    .cupom-container button {
      background-color: #6200ea;
      color: white;
      border: none;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
      user-select: none;
      transition: background-color 0.3s ease;
    }
    .cupom-container button:hover {
      background-color: #3700b3;
    }
    /* Mensagens de erro e sucesso */
    .msg {
      max-width: 400px;
      margin: 0.5rem auto;
      padding: 0.75rem;
      border-radius: 6px;
      font-weight: 600;
      text-align: center;
      user-select: none;
    }
    .msg.error {
      background-color: #f8d7da;
      color: #721c24;
    }
    .msg.success {
      background-color: #d4edda;
      color: #155724;
    }
  </style>
</head>
<body>
  <div id="app">
    <header>
      <h1>AppVendas</h1>
      <button id="btn-menu" aria-label="Abrir menu">☰</button>
    </header>

    <nav id="menu-lateral" aria-label="Menu lateral">
      <button id="btn-close-menu" aria-label="Fechar menu">×</button>
      <ul>
        <li><a href="#" id="link-home">Home</a></li>
        <li><a href="#" id="link-produtos">Produtos</a></li>
        <li><a href="#" id="link-cadastro">Cadastro / Login</a></li>
        <li><a href="#" id="link-carrinho">Carrinho</a></li>
      </ul>
    </nav>

    <main id="main-content" tabindex="0"></main>

    <footer>
      <p>© 2025 AppVendas</p>
    </footer>
  </div>

<script>
  const STORAGE = {
    USUARIOS: 'appvendas_usuarios',
    SESSAO: 'appvendas_sessao',
    PRODUTOS: 'appvendas_produtos',
    CARRINHO: 'appvendas_carrinho',
    CUPOM: 'appvendas_cupom'
  };

  const produtosIniciais = [
  {
    id: 'p1',
    nome: 'Vestido Estampado Feminino',
    descricao: 'Vestido leve de verão, com estampa floral e tecido macio.',
    preco: 139.90,
    imagem: 'https://images.unsplash.com/photo-1593032457869-04c1a8576f1b?auto=format&fit=crop&w=500&q=80'
  },
  {
    id: 'p2',
    nome: 'Camisa Social Masculina Slim',
    descricao: 'Camisa social masculina, ideal para trabalho ou eventos.',
    preco: 119.90,
    imagem: 'https://images.unsplash.com/photo-1585386959984-a4155224c8d0?auto=format&fit=crop&w=500&q=80'
  },
  {
    id: 'p3',
    nome: 'Jaqueta Jeans Feminina',
    descricao: 'Jaqueta jeans de alta qualidade, modelagem moderna.',
    preco: 199.90,
    imagem: 'https://images.unsplash.com/photo-1542060748-10c28b62716f?auto=format&fit=crop&w=500&q=80'
  },
  {
    id: 'p4',
    nome: 'Blusa Casual Masculina',
    descricao: 'Blusa de algodão com estampa discreta, ideal para o dia a dia.',
    preco: 89.90,
    imagem: 'https://images.unsplash.com/photo-1618354691211-65d4b4ad49af?auto=format&fit=crop&w=500&q=80'
  },
  {
    id: 'p5',
    nome: 'Conjunto Moletom Unissex',
    descricao: 'Moletom completo, ideal para dias frios. Muito confortável.',
    preco: 149.90,
    imagem: 'https://images.unsplash.com/photo-1585386959984-a4155224c8d0?auto=format&fit=crop&w=500&q=80'
  },
  // Produtos adicionais
  {
    id: 'p6',
    nome: 'Saia Midi Floral',
    descricao: 'Saia midi com estampa floral, ideal para ocasiões informais.',
    preco: 89.90,
    imagem: 'https://images.unsplash.com/photo-1503342217505-b0a15ec3261c?auto=format&fit=crop&w=500&q=80'
  },
  {
    id: 'p7',
    nome: 'Tênis Casual Unissex',
    descricao: 'Tênis confortável para uso diário, com design moderno.',
    preco: 179.90,
    imagem: 'https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f?auto=format&fit=crop&w=500&q=80'
  },
  {
    id: 'p8',
    nome: 'Camiseta Básica Masculina',
    descricao: 'Camiseta básica, feita com algodão premium.',
    preco: 59.90,
    imagem: 'https://images.unsplash.com/photo-1530845648727-51d50c29326f?auto=format&fit=crop&w=500&q=80'
  },
  {
    id: 'p9',
    nome: 'Calça Jeans Feminina',
    descricao: 'Calça jeans com modelagem slim e stretch para conforto.',
    preco: 159.90,
    imagem: 'https://images.unsplash.com/photo-1495121605193-b116b5b09a91?auto=format&fit=crop&w=500&q=80'
  },
  {
    id: 'p10',
    nome: 'Casaco de Lã Masculino',
    descricao: 'Casaco quente, ideal para dias frios, com design clássico.',
    preco: 299.90,
    imagem: 'https://images.unsplash.com/photo-1541099649105-f69ad21f3246?auto=format&fit=crop&w=500&q=80'
  }
];

  // Slides de propaganda
  const slides = [
    {
      texto: "Promoção Imperdível!",
      subtitulo: "Até 50% OFF em roupas selecionadas",
      imagem: "https://images.unsplash.com/photo-1503342217505-b0a15ec3261c?auto=format&fit=crop&w=800&q=60",
      bg: "#8e24aa"
    },
    {
      texto: "Nova Coleção Verão",
      subtitulo: "Estilos fresquinhos para você arrasar",
      imagem: "https://images.unsplash.com/photo-1521334884684-d80222895322?auto=format&fit=crop&w=800&q=60",
      bg: "#1e88e5"
    },
    {
      texto: "Frete Grátis",
      subtitulo: "Para compras acima de R$200",
      imagem: "https://images.unsplash.com/photo-1512436991641-6745cdb1723f?auto=format&fit=crop&w=800&q=60",
      bg: "#43a047"
    },
  ];

  // Cupom de desconto fixo para teste
  const cupomValido = {
    codigo: "DESCONTO10",
    desconto: 10 // porcentagem
  };

  let usuarios = JSON.parse(localStorage.getItem(STORAGE.USUARIOS)) || [];
  let sessao = JSON.parse(localStorage.getItem(STORAGE.SESSAO)) || null;
  let produtos = JSON.parse(localStorage.getItem(STORAGE.PRODUTOS)) || produtosIniciais;
  let carrinho = JSON.parse(localStorage.getItem(STORAGE.CARRINHO)) || [];
  let cupomAplicado = JSON.parse(localStorage.getItem(STORAGE.CUPOM)) || null;

  // Elements
  const btnMenu = document.getElementById('btn-menu');
  const btnCloseMenu = document.getElementById('btn-close-menu');
  const menuLateral = document.getElementById('menu-lateral');
  const mainContent = document.getElementById('main-content');
  const linkHome = document.getElementById('link-home');
  const linkProdutos = document.getElementById('link-produtos');
  const linkCadastro = document.getElementById('link-cadastro');
  const linkCarrinho = document.getElementById('link-carrinho');

  // MENU abrir/fechar
  btnMenu.addEventListener('click', () => {
    menuLateral.classList.add('show');
  });
  btnCloseMenu.addEventListener('click', () => {
    menuLateral.classList.remove('show');
  });
  // Fechar menu clicando fora dele
  window.addEventListener('click', e => {
    if (!menuLateral.contains(e.target) && e.target !== btnMenu) {
      menuLateral.classList.remove('show');
    }
  });

  // Navegação simples
  linkHome.addEventListener('click', e => {
    e.preventDefault();
    menuLateral.classList.remove('show');
    renderHome();
  });
  linkProdutos.addEventListener('click', e => {
    e.preventDefault();
    menuLateral.classList.remove('show');
    renderProdutos();
  });
  linkCadastro.addEventListener('click', e => {
    e.preventDefault();
    menuLateral.classList.remove('show');
    renderCadastroLogin();
  });
  linkCarrinho.addEventListener('click', e => {
    e.preventDefault();
    menuLateral.classList.remove('show');
    renderCarrinho();
  });

  // Renderizações
  function renderHome() {
    mainContent.innerHTML = '';

    // Slide de propagandas
    const slideContainer = document.createElement('div');
    slideContainer.className = 'slide-container';

    const slidesWrapper = document.createElement('div');
    slidesWrapper.className = 'slides';

    slides.forEach((slide, i) => {
      const div = document.createElement('div');
      div.className = 'slide';
      div.style.backgroundImage = `url(${slide.imagem})`;
      div.style.backgroundColor = slide.bg;
      div.innerHTML = `<div>${slide.texto}<p>${slide.subtitulo}</p></div>`;
      slidesWrapper.appendChild(div);
    });

    slideContainer.appendChild(slidesWrapper);
    mainContent.appendChild(slideContainer);

    // Iniciar slide automático
    let currentSlide = 0;
    const totalSlides = slides.length;
    setInterval(() => {
      currentSlide = (currentSlide + 1) % totalSlides;
      slidesWrapper.style.transform = `translateX(-${currentSlide * 100}%)`;
    }, 4000);

    // Mostrar produtos em destaque (exemplo)
    const destaque = document.createElement('section');
    destaque.innerHTML = `<h2>Destaques</h2>`;
    produtos.slice(0,3).forEach(prod => {
      const card = criarCardProduto(prod);
      destaque.appendChild(card);
    });
    mainContent.appendChild(destaque);
  }

  function criarCardProduto(produto) {
    const card = document.createElement('div');
    card.className = 'card';

    const img = document.createElement('img');
    img.src = produto.imagem;
    img.alt = produto.nome;

    const info = document.createElement('div');
    info.className = 'info';

    const nome = document.createElement('h3');
    nome.textContent = produto.nome;

    const desc = document.createElement('p');
    desc.textContent = produto.descricao;

    const preco = document.createElement('div');
    preco.className = 'price';
    preco.textContent = `R$ ${produto.preco.toFixed(2)}`;

    const btnComprar = document.createElement('button');
    btnComprar.textContent = 'Adicionar ao Carrinho';
    btnComprar.addEventListener('click', () => {
      adicionarAoCarrinho(produto.id);
    });

    info.appendChild(nome);
    info.appendChild(desc);
    info.appendChild(preco);
    info.appendChild(btnComprar);

    card.appendChild(img);
    card.appendChild(info);

    return card;
  }

  function adicionarAoCarrinho(idProduto) {
    const itemNoCarrinho = carrinho.find(item => item.id === idProduto);
    if (itemNoCarrinho) {
      itemNoCarrinho.quantidade++;
    } else {
      carrinho.push({ id: idProduto, quantidade: 1 });
    }
    salvarCarrinho();
    alert('Produto adicionado ao carrinho!');
  }

  function salvarCarrinho() {
    localStorage.setItem(STORAGE.CARRINHO, JSON.stringify(carrinho));
  }

  function renderProdutos() {
    mainContent.innerHTML = '<h2>Produtos</h2>';
    produtos.forEach(prod => {
      const card = criarCardProduto(prod);
      mainContent.appendChild(card);
    });
  }

  function renderCadastroLogin() {
    mainContent.innerHTML = '';

    const container = document.createElement('div');
    container.className = 'form-container';

    container.innerHTML = `
      <h2>${sessao ? 'Bem-vindo, ' + sessao.nome : 'Cadastro / Login'}</h2>
      ${sessao ? `
        <p>Você está logado como <strong>${sessao.email}</strong>.</p>
        <button id="btn-logout">Sair</button>
      ` : `
        <form id="form-cadastro">
          <label for="nome">Nome:</label>
          <input type="text" id="nome" required minlength="3" />
          <label for="email">Email:</label>
          <input type="email" id="email" required />
          <label for="senha">Senha:</label>
          <input type="password" id="senha" required minlength="6" />
          <button type="submit">Cadastrar</button>
        </form>
        <hr />
        <form id="form-login">
          <label for="login-email">Email:</label>
          <input type="email" id="login-email" required />
          <label for="login-senha">Senha:</label>
          <input type="password" id="login-senha" required />
          <button type="submit">Entrar</button>
        </form>
      `}
      <div id="msg-cadastro-login"></div>
    `;

    mainContent.appendChild(container);

    if (sessao) {
      document.getElementById('btn-logout').addEventListener('click', () => {
        sessao = null;
        localStorage.removeItem(STORAGE.SESSAO);
        alert('Você saiu da conta.');
        renderCadastroLogin();
      });
      return;
    }

    const formCadastro = document.getElementById('form-cadastro');
    const formLogin = document.getElementById('form-login');
    const msgBox = document.getElementById('msg-cadastro-login');

    formCadastro.addEventListener('submit', e => {
      e.preventDefault();
      msgBox.textContent = '';
      const nome = document.getElementById('nome').value.trim();
      const email = document.getElementById('email').value.trim().toLowerCase();
      const senha = document.getElementById('senha').value;

      if (!nome || !email || !senha) {
        mostrarMensagem(msgBox, 'Preencha todos os campos.', 'error');
        return;
      }
      if (usuarios.find(u => u.email === email)) {
        mostrarMensagem(msgBox, 'Email já cadastrado.', 'error');
        return;
      }

      usuarios.push({ nome, email, senha });
      localStorage.setItem(STORAGE.USUARIOS, JSON.stringify(usuarios));
      mostrarMensagem(msgBox, 'Cadastro realizado com sucesso! Agora faça login.', 'success');
      formCadastro.reset();
    });

    formLogin.addEventListener('submit', e => {
      e.preventDefault();
      msgBox.textContent = '';
      const email = document.getElementById('login-email').value.trim().toLowerCase();
      const senha = document.getElementById('login-senha').value;

      const user = usuarios.find(u => u.email === email && u.senha === senha);
      if (!user) {
        mostrarMensagem(msgBox, 'Email ou senha inválidos.', 'error');
        return;
      }
      sessao = { nome: user.nome, email: user.email };
      localStorage.setItem(STORAGE.SESSAO, JSON.stringify(sessao));
      mostrarMensagem(msgBox, `Bem-vindo, ${user.nome}!`, 'success');

      setTimeout(() => {
        renderCadastroLogin();
      }, 1500);
    });
  }

  function mostrarMensagem(elemento, texto, tipo) {
    elemento.textContent = texto;
    elemento.className = 'msg ' + tipo;
    setTimeout(() => {
      elemento.textContent = '';
      elemento.className = '';
    }, 4000);
  }

  function renderCarrinho() {
    mainContent.innerHTML = '<h2>Carrinho</h2>';
    if (carrinho.length === 0) {
      mainContent.innerHTML += '<p>Seu carrinho está vazio.</p>';
      return;
    }

    const container = document.createElement('div');
    carrinho.forEach(item => {
      const produto = produtos.find(p => p.id === item.id);
      if (!produto) return;

      const div = document.createElement('div');
      div.className = 'cart-item';

      const img = document.createElement('img');
      img.src = produto.imagem;
      img.alt = produto.nome;

      const detalhes = document.createElement('div');
      detalhes.className = 'details';

      const nome = document.createElement('h4');
      nome.textContent = produto.nome;

      const preco = document.createElement('p');
      preco.textContent = `Preço: R$ ${produto.preco.toFixed(2)}`;

      const quantidade = document.createElement('p');
      quantidade.textContent = `Quantidade: ${item.quantidade}`;

      detalhes.appendChild(nome);
      detalhes.appendChild(preco);
      detalhes.appendChild(quantidade);

      const acoes = document.createElement('div');
      acoes.className = 'actions';

      const btnRemover = document.createElement('button');
      btnRemover.textContent = 'Remover';
      btnRemover.addEventListener('click', () => {
        removerDoCarrinho(produto.id);
      });

      acoes.appendChild(btnRemover);

      div.appendChild(img);
      div.appendChild(detalhes);
      div.appendChild(acoes);

      container.appendChild(div);
    });

    mainContent.appendChild(container);

    // Total e cupom
    const totalSemDesconto = carrinho.reduce((acc, item) => {
      const prod = produtos.find(p => p.id === item.id);
      return acc + (prod.preco * item.quantidade);
    }, 0);

    const total = cupomAplicado ? totalSemDesconto * (1 - cupomAplicado.desconto / 100) : totalSemDesconto;

    const totalDiv = document.createElement('div');
    totalDiv.style.textAlign = 'right';
    totalDiv.style.fontWeight = 'bold';
    totalDiv.style.marginTop = '1rem';
    totalDiv.textContent = `Total: R$ ${total.toFixed(2)}`;

    mainContent.appendChild(totalDiv);

    // Cupom
    const cupomContainer = document.createElement('div');
    cupomContainer.className = 'cupom-container';

    const inputCupom = document.createElement('input');
    inputCupom.type = 'text';
    inputCupom.placeholder = 'Digite cupom de desconto';
    inputCupom.value = cupomAplicado ? cupomAplicado.codigo : '';

    const btnAplicarCupom = document.createElement('button');
    btnAplicarCupom.textContent = 'Aplicar';

    cupomContainer.appendChild(inputCupom);
    cupomContainer.appendChild(btnAplicarCupom);

    mainContent.appendChild(cupomContainer);

    const msgCupom = document.createElement('div');
    mainContent.appendChild(msgCupom);

    btnAplicarCupom.addEventListener('click', () => {
      const codigo = inputCupom.value.trim().toUpperCase();
      if (codigo === cupomValido.codigo) {
        cupomAplicado = { ...cupomValido };
        localStorage.setItem(STORAGE.CUPOM, JSON.stringify(cupomAplicado));
        mostrarMensagem(msgCupom, `Cupom aplicado! Você tem ${cupomAplicado.desconto}% de desconto.`, 'success');
        renderCarrinho();
      } else {
        mostrarMensagem(msgCupom, 'Cupom inválido.', 'error');
      }
    });

    // Botão WhatsApp
    if (sessao) {
      const btnWhats = document.createElement('button');
      btnWhats.className = 'btn-whatsapp';
      btnWhats.textContent = 'Finalizar Pedido via WhatsApp';

      btnWhats.addEventListener('click', () => {
        enviarPedidoWhatsApp();
      });

      mainContent.appendChild(btnWhats);
    } else {
      const aviso = document.createElement('p');
      aviso.style.color = 'red';
      aviso.textContent = 'Você precisa estar logado para finalizar o pedido.';
      mainContent.appendChild(aviso);
    }
  }

  function removerDoCarrinho(idProduto) {
    carrinho = carrinho.filter(item => item.id !== idProduto);
    salvarCarrinho();
    renderCarrinho();
  }

  function enviarPedidoWhatsApp() {
    if (carrinho.length === 0) {
      alert('Seu carrinho está vazio!');
      return;
    }
    const telefone = '5531993309593'; // Coloque seu número aqui no formato internacional (55 + DDD + número)
    let mensagem = `Olá, meu nome é ${sessao.nome}.\nGostaria de fazer o pedido:\n`;

    carrinho.forEach(item => {
      const prod = produtos.find(p => p.id === item.id);
      mensagem += `- ${prod.nome} (x${item.quantidade}) - R$ ${(prod.preco * item.quantidade).toFixed(2)}\n`;
    });

    const totalSemDesconto = carrinho.reduce((acc, item) => {
      const prod = produtos.find(p => p.id === item.id);
      return acc + (prod.preco * item.quantidade);
    }, 0);
    const total = cupomAplicado ? totalSemDesconto * (1 - cupomAplicado.desconto / 100) : totalSemDesconto;

    mensagem += `Total: R$ ${total.toFixed(2)}\n`;

    if (cupomAplicado) {
      mensagem += `(Cupom aplicado: ${cupomAplicado.codigo} - ${cupomAplicado.desconto}% desconto)\n`;
    }

    const url = `https://wa.me/${telefone}?text=${encodeURIComponent(mensagem)}`;
    window.open(url, '_blank');
  }

  // Salvar produtos no localStorage se não estiver salvo
  if (!localStorage.getItem(STORAGE.PRODUTOS)) {
    localStorage.setItem(STORAGE.PRODUTOS, JSON.stringify(produtosIniciais));
  }

  // Inicializa exibindo Home
  renderHome();
</script>

</body>
</html>
