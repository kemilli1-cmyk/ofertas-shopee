<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ofertas da Shopee</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 0; background: #f7f7f7; }
    header { background: #ee4d2d; color: white; padding: 1em; text-align: center; font-size: 1.5em; }
    .grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 1em; padding: 1em; }
    .card { background: white; border-radius: 8px; box-shadow: 0 2px 6px rgba(0,0,0,0.1); overflow: hidden; display: flex; flex-direction: column; }
    .card img { width: 100%; height: 200px; object-fit: cover; }
    .card-body { padding: 1em; flex: 1; display: flex; flex-direction: column; justify-content: space-between; }
    .title { font-size: 1em; margin-bottom: 0.5em; }
    .price { font-weight: bold; color: #ee4d2d; margin-bottom: 0.5em; }
    .btn { background: #ee4d2d; color: white; border: none; padding: 0.5em; cursor: pointer; border-radius: 4px; }
  </style>
</head>
<body>
  <header>Ofertas da Shopee</header>
  <main class="grid" id="offers"></main>

  <script>
    const afiliado = "18311280604";

    // Simulando produtos - futuramente podemos puxar via API ou arquivo externo
    const produtos = [
      {
        nome: "Fone Bluetooth TWS",
        preco: "R$ 39,90",
        imagem: "https://cf.shopee.com.br/file/7e2c1f43a95f41b6e44cb5f2caa7c0dd",
        link: "https://shope.ee/1L1F2gEz8D"
      },
      {
        nome: "Relógio Smartwatch",
        preco: "R$ 59,99",
        imagem: "https://cf.shopee.com.br/file/5976a4b18f6df453ae8c5b3f697f6f16",
        link: "https://shope.ee/8A7Z2UzmYa"
      },
      {
        nome: "Kit Maquiagem Completo",
        preco: "R$ 29,90",
        imagem: "https://cf.shopee.com.br/file/2d41ecb66c1a54d90a8f48b1be3d6459",
        link: "https://shope.ee/9KpNn4YuKD"
      }
    ];

    const container = document.getElementById("offers");
    produtos.forEach(produto => {
      const card = document.createElement("div");
      card.className = "card";
      card.innerHTML = `
        <img src="${produto.imagem}" alt="${produto.nome}" />
        <div class="card-body">
          <div class="title">${produto.nome}</div>
          <div class="price">${produto.preco}</div>
          <button class="btn" onclick="copiarLink('${produto.link}?af_click_id=${afiliado}')">Copiar link</button>
        </div>
      `;
      container.appendChild(card);
    });

    function copiarLink(link) {
      navigator.clipboard.writeText(link);
      alert("Link copiado com sucesso!");
    }
  </script>
</body>
</html>
