# PAGINA-DE-VENDA-LANCHE



<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Food Delivery - Pedido Online</title>
  
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  
  <!-- FontAwesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <!-- Google Font: Poppins & Inter -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">

  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ['Poppins', 'Inter', 'sans-serif'],
          },
          colors: {
            skybrand: {
              50: '#f0f9ff',
              100: '#e0f2fe',
              200: '#bae6fd',
              300: '#7dd3fc',
              400: '#38bdf8',
              500: '#0ea5e9',
              600: '#0284c7',
              700: '#0369a1',
              800: '#075985',
              900: '#0c4a6e',
            }
          }
        }
      }
    }
  </script>

  <style>
    /* Custom Scrollbars and Glassmorphism styles */
    body {
      background: linear-gradient(135deg, #e0f2fe 0%, #38bdf8 50%, #0284c7 100%);
      background-attachment: fixed;
    }

    .glass-card {
      background: rgba(255, 255, 255, 0.95);
      backdrop-filter: blur(12px);
      box-shadow: 0 20px 40px rgba(2, 132, 199, 0.18);
    }

    .badge-pulse {
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.05); }
    }

    /* Custom Input Focus Ring */
    .custom-input {
      transition: all 0.25s ease-in-out;
    }

    .custom-input:focus {
      border-color: #38bdf8;
      box-shadow: 0 0 0 4px rgba(56, 189, 248, 0.25);
    }

    /* Floating Header Anim */
    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-6px); }
    }
    .floating-icon {
      animation: float 3s ease-in-out infinite;
    }
  </style>
</head>
<body class="min-h-screen text-slate-800 antialiased font-sans py-6 px-4 md:py-10">

  <div class="max-w-4xl mx-auto">
    
    <!-- Top Header Banner -->
    <header class="text-center mb-8">
      <div class="inline-flex items-center justify-center p-4 bg-white/90 backdrop-blur rounded-full shadow-lg mb-4 text-skybrand-600 floating-icon">
        <i class="fa-solid fa-utensils text-3xl md:text-4xl"></i>
      </div>
      <h1 class="text-3xl md:text-5xl font-extrabold text-white drop-shadow-md tracking-tight">
        Sabor Express 🍔
      </h1>
      <p class="text-skybrand-100 mt-2 text-base md:text-lg font-medium drop-shadow-sm">
        Monte seu pedido e receba no conforto da sua casa!
      </p>
    </header>

    <!-- Main Card Container -->
    <div class="glass-card rounded-3xl p-6 md:p-10 border border-white/60">
      
      <form id="orderForm" onsubmit="finalizarPedido(event)">
        
        <!-- SECTION 1: PRODUCT SELECTION -->
        <section class="mb-10">
          <div class="flex items-center justify-between border-b-2 border-skybrand-100 pb-3 mb-6">
            <h2 class="text-xl md:text-2xl font-bold text-skybrand-700 flex items-center gap-2">
              <i class="fa-solid fa-burger text-skybrand-500"></i> 
              1. Escolha seus Produtos
            </h2>
            <span class="text-xs md:text-sm bg-skybrand-100 text-skybrand-700 px-3 py-1 rounded-full font-semibold">
              Menu Principal
            </span>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="menuContainer">
            <!-- Items generated via JavaScript -->
          </div>
        </section>

        <!-- SECTION 2: ORDER SUMMARY & PAYMENT -->
        <section class="mb-10">
          
          <!-- Live Total Bar -->
          <div class="bg-gradient-to-r from-skybrand-500 to-skybrand-600 text-white rounded-2xl p-5 mb-8 flex flex-col sm:flex-row justify-between items-center shadow-lg gap-4">
            <div class="flex items-center gap-3">
              <div class="p-3 bg-white/20 rounded-xl">
                <i class="fa-solid fa-receipt text-2xl"></i>
              </div>
              <div>
                <span class="text-xs uppercase tracking-wider text-skybrand-100 font-bold block">Resumo do Pedido</span>
                <span class="text-sm font-medium" id="itensResumo">Nenhum item selecionado</span>
              </div>
            </div>
            <div class="text-right">
              <span class="text-xs text-skybrand-100 uppercase font-semibold block">Valor Total</span>
              <span class="text-3xl font-extrabold tracking-tight" id="valorTotal">R$ 0,00</span>
            </div>
          </div>

          <div class="flex items-center justify-between border-b-2 border-skybrand-100 pb-3 mb-6">
            <h2 class="text-xl md:text-2xl font-bold text-skybrand-700 flex items-center gap-2">
              <i class="fa-solid fa-credit-card text-skybrand-500"></i> 
              2. Forma de Pagamento
            </h2>
          </div>

          <div class="grid grid-cols-2 sm:grid-cols-4 gap-3">
            <label class="cursor-pointer">
              <input type="radio" name="pagamento" value="Pix" class="peer hidden" required>
              <div class="p-4 rounded-xl border-2 border-slate-200 bg-slate-50/50 hover:bg-skybrand-50 peer-checked:border-skybrand-500 peer-checked:bg-skybrand-50 peer-checked:text-skybrand-700 text-center transition flex flex-col items-center gap-2 font-medium">
                <i class="fa-brands fa-pix text-2xl text-emerald-500"></i>
                <span class="text-sm">Pix</span>
              </div>
            </label>

            <label class="cursor-pointer">
              <input type="radio" name="pagamento" value="Cartão de Crédito" class="peer hidden">
              <div class="p-4 rounded-xl border-2 border-slate-200 bg-slate-50/50 hover:bg-skybrand-50 peer-checked:border-skybrand-500 peer-checked:bg-skybrand-50 peer-checked:text-skybrand-700 text-center transition flex flex-col items-center gap-2 font-medium">
                <i class="fa-regular fa-credit-card text-2xl text-skybrand-500"></i>
                <span class="text-sm">Crédito</span>
              </div>
            </label>

            <label class="cursor-pointer">
              <input type="radio" name="pagamento" value="Cartão de Débito" class="peer hidden">
              <div class="p-4 rounded-xl border-2 border-slate-200 bg-slate-50/50 hover:bg-skybrand-50 peer-checked:border-skybrand-500 peer-checked:bg-skybrand-50 peer-checked:text-skybrand-700 text-center transition flex flex-col items-center gap-2 font-medium">
                <i class="fa-solid fa-credit-card text-2xl text-indigo-500"></i>
                <span class="text-sm">Débito</span>
              </div>
            </label>

            <label class="cursor-pointer">
              <input type="radio" name="pagamento" value="Dinheiro" class="peer hidden">
              <div class="p-4 rounded-xl border-2 border-slate-200 bg-slate-50/50 hover:bg-skybrand-50 peer-checked:border-skybrand-500 peer-checked:bg-skybrand-50 peer-checked:text-skybrand-700 text-center transition flex flex-col items-center gap-2 font-medium">
                <i class="fa-solid fa-money-bill-wave text-2xl text-green-600"></i>
                <span class="text-sm">Dinheiro</span>
              </div>
            </label>
          </div>
        </section>

        <!-- SECTION 3: DELIVERY DETAILS -->
        <section class="mb-8">
          <div class="flex items-center justify-between border-b-2 border-skybrand-100 pb-3 mb-6">
            <h2 class="text-xl md:text-2xl font-bold text-skybrand-700 flex items-center gap-2">
              <i class="fa-solid fa-truck-fast text-skybrand-500"></i> 
              3. Dados de Entrega
            </h2>
          </div>

          <div class="space-y-4">
            
            <!-- Nome Completo -->
            <div>
              <label for="nome" class="block text-sm font-semibold text-slate-700 mb-1">Nome Completo *</label>
              <div class="relative">
                <span class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400">
                  <i class="fa-regular fa-user"></i>
                </span>
                <input type="text" id="nome" name="nome" placeholder="Ex: Maria Silva" required
                  class="custom-input w-full pl-10 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl text-sm outline-none">
              </div>
            </div>

            <!-- Telefone e Email -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
              <div>
                <label for="telefone" class="block text-sm font-semibold text-slate-700 mb-1">Telefone / WhatsApp *</label>
                <div class="relative">
                  <span class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400">
                    <i class="fa-brands fa-whatsapp"></i>
                  </span>
                  <input type="tel" id="telefone" name="telefone" placeholder="(85) 90000-0000" required
                    class="custom-input w-full pl-10 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl text-sm outline-none">
                </div>
              </div>

              <div>
                <label for="email" class="block text-sm font-semibold text-slate-700 mb-1">E-mail *</label>
                <div class="relative">
                  <span class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400">
                    <i class="fa-regular fa-envelope"></i>
                  </span>
                  <input type="email" id="email" name="email" placeholder="seu@email.com" required
                    class="custom-input w-full pl-10 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl text-sm outline-none">
                </div>
              </div>
            </div>

            <!-- Data de Entrega e País -->
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
              <div>
                <label for="data" class="block text-sm font-semibold text-slate-700 mb-1">Data de Entrega *</label>
                <div class="relative">
                  <span class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400">
                    <i class="fa-regular fa-calendar"></i>
                  </span>
                  <input type="date" id="data" name="data" required
                    class="custom-input w-full pl-10 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl text-sm outline-none">
                </div>
              </div>

              <div>
                <label for="pais" class="block text-sm font-semibold text-slate-700 mb-1">País *</label>
                <div class="relative">
                  <span class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400">
                    <i class="fa-solid fa-globe"></i>
                  </span>
                  <select id="pais" name="pais" required
                    class="custom-input w-full pl-10 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl text-sm outline-none appearance-none">
                    <option value="" disabled selected>Selecione seu país</option>
                    <option value="Brasil">Brasil</option>
                    <option value="Portugal">Portugal</option>
                    <option value="Angola">Angola</option>
                    <option value="Moçambique">Moçambique</option>
                    <option value="Outro">Outro</option>
                  </select>
                </div>
              </div>
            </div>

            <!-- Cidade e Endereço -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
              <div>
                <label for="cidade" class="block text-sm font-semibold text-slate-700 mb-1">Cidade *</label>
                <div class="relative">
                  <span class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400">
                    <i class="fa-solid fa-city"></i>
                  </span>
                  <input type="text" id="cidade" name="cidade" placeholder="Ex: Fortaleza" required
                    class="custom-input w-full pl-10 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl text-sm outline-none">
                </div>
              </div>

              <div class="md:col-span-2">
                <label for="endereco" class="block text-sm font-semibold text-slate-700 mb-1">Endereço Completo *</label>
                <div class="relative">
                  <span class="absolute inset-y-0 left-0 flex items-center pl-3.5 text-slate-400">
                    <i class="fa-solid fa-location-dot"></i>
                  </span>
                  <input type="text" id="endereco" name="endereco" placeholder="Rua, número, bairro e referência" required
                    class="custom-input w-full pl-10 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl text-sm outline-none">
                </div>
              </div>
            </div>

          </div>
        </section>

        <!-- SUBMIT BUTTON -->
        <button type="submit" 
          class="w-full py-4 px-6 bg-gradient-to-r from-emerald-500 to-green-600 hover:from-emerald-600 hover:to-green-700 text-white font-bold text-lg rounded-2xl shadow-xl hover:shadow-2xl transition transform hover:-translate-y-0.5 active:translate-y-0 flex items-center justify-center gap-3">
          <i class="fa-brands fa-whatsapp text-2xl"></i>
          <span>Enviar Pedido para WhatsApp</span>
        </button>

      </form>

      <!-- Success Modal Overlay -->
      <div id="modalSucesso" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm hidden flex items-center justify-center p-4 z-50">
        <div class="bg-white rounded-3xl p-6 md:p-8 max-w-sm w-full text-center shadow-2xl animate-bounce-short">
          <div class="w-16 h-16 bg-emerald-100 text-emerald-600 rounded-full flex items-center justify-center text-3xl mx-auto mb-4">
            <i class="fa-solid fa-circle-check"></i>
          </div>
          <h3 class="text-xl font-bold text-slate-800 mb-2">Pedido Quase Pronto!</h3>
          <p class="text-sm text-slate-600 mb-6">
            Você será redirecionado para o WhatsApp para confirmar seu pedido.
          </p>
          <div class="flex justify-center">
            <div class="w-8 h-8 border-4 border-skybrand-500 border-t-transparent rounded-full animate-spin"></div>
          </div>
        </div>
      </div>

    </div>

    <!-- Footer Disclaimer -->
    <footer class="text-center text-white/80 text-xs mt-8">
      <p>© 2026 Sabor Express - Todos os direitos reservados.</p>
    </footer>

  </div>

  <script>
    // Product List Catalog Data
    const produtos = [
      { id: 'burguer', nome: 'Hambúrguer Artesanal', preco: 25.00, icone: 'fa-burger', cor: 'text-amber-500', desc: 'Pão brioche, 180g de carne, queijo cheddar e bacon' },
      { id: 'batata', nome: 'Batata Frita Especial', preco: 15.00, icone: 'fa-box-tissue', cor: 'text-yellow-500', desc: 'Crocantes, acompanhadas de molho da casa' },
      { id: 'refri', nome: 'Refrigerante Lata', preco: 6.00, icone: 'fa-bottle-water', cor: 'text-red-500', desc: 'Lata 350ml trincando de gelada' },
      { id: 'pizza', nome: 'Pizza Broto Especial', preco: 35.00, icone: 'fa-pizza-slice', cor: 'text-orange-500', desc: 'Massa artesanal, bastante queijo e calabresa' },
      { id: 'sobremesa', nome: 'Sobremesa Churros', preco: 12.00, icone: 'fa-ice-cream', cor: 'text-pink-500', desc: 'Recheados com doce de leite cremoso' }
    ];

    // State array for product quantities
    const quantidades = {};
    produtos.forEach(p => quantidades[p.id] = 0);

    // Initialize HTML Menu Items on Load
    function inicializarMenu() {
      const container = document.getElementById('menuContainer');
      container.innerHTML = '';

      produtos.forEach(prod => {
        const itemHtml = `
          <div class="p-4 bg-slate-50 border border-slate-200 rounded-2xl flex items-center justify-between hover:border-skybrand-300 transition shadow-sm">
            <div class="flex items-center gap-3.5">
              <div class="w-12 h-12 bg-white rounded-xl flex items-center justify-center text-2xl shadow-inner ${prod.cor}">
                <i class="fa-solid ${prod.icone}"></i>
              </div>
              <div>
                <h3 class="font-bold text-slate-800 text-sm md:text-base">${prod.nome}</h3>
                <p class="text-xs text-slate-500 line-clamp-1 mb-1">${prod.desc}</p>
                <span class="text-skybrand-600 font-extrabold text-sm">R$ ${prod.preco.toFixed(2).replace('.', ',')}</span>
              </div>
            </div>

            <!-- Qty Counter -->
            <div class="flex items-center bg-white border border-slate-200 rounded-xl p-1 shadow-sm gap-2">
              <button type="button" onclick="alterarQtd('${prod.id}', -1)" 
                class="w-7 h-7 bg-slate-100 hover:bg-skybrand-100 hover:text-skybrand-700 text-slate-600 rounded-lg flex items-center justify-center font-bold text-sm transition">
                -
              </button>
              <span id="qty-${prod.id}" class="w-6 text-center font-bold text-sm text-slate-800">0</span>
              <button type="button" onclick="alterarQtd('${prod.id}', 1)" 
                class="w-7 h-7 bg-skybrand-500 hover:bg-skybrand-600 text-white rounded-lg flex items-center justify-center font-bold text-sm transition">
                +
              </button>
            </div>
          </div>
        `;
        container.innerHTML += itemHtml;
      });
    }

    // Alter quantity handler
    function alterarQtd(id, delta) {
      if (quantidades[id] !== undefined) {
        quantidades[id] += delta;
        if (quantidades[id] < 0) quantidades[id] = 0;
        
        document.getElementById(`qty-${id}`).innerText = quantidades[id];
        atualizarTotal();
      }
    }

    // Update Live Total Summary Calculation
    function atualizarTotal() {
      let total = 0;
      let totalItens = 0;

      produtos.forEach(p => {
        const qty = quantidades[p.id];
        if (qty > 0) {
          total += qty * p.preco;
          totalItens += qty;
        }
      });

      document.getElementById('valorTotal').innerText = `R$ ${total.toFixed(2).replace('.', ',')}`;
      document.getElementById('itensResumo').innerText = totalItens > 0 
        ? `${totalItens} ${totalItens === 1 ? 'item selecionado' : 'itens selecionados'}` 
        : 'Nenhum item selecionado';

      return total;
    }

    // Input Telephone Mask Setup
    document.addEventListener("DOMContentLoaded", () => {
      inicializarMenu();

      const telefoneInput = document.getElementById("telefone");
      const dataInput = document.getElementById("data");

      // Set min date to today
      const hoje = new Date().toISOString().split("T")[0];
      if (dataInput) {
        dataInput.setAttribute("min", hoje);
      }

      // Telephone Input Mask
      if (telefoneInput) {
        telefoneInput.addEventListener("input", (e) => {
          let value = e.target.value.replace(/\D/g, "");
          if (value.length > 11) value = value.slice(0, 11);

          if (value.length > 6) {
            value = `(${value.slice(0, 2)}) ${value.slice(2, 7)}-${value.slice(7)}`;
          } else if (value.length > 2) {
            value = `(${value.slice(0, 2)}) ${value.slice(2)}`;
          } else if (value.length > 0) {
            value = `(${value}`;
          }

          e.target.value = value;
        });
      }
    });

    // Form Submission & WhatsApp Redirecting
    function finalizarPedido(e) {
      e.preventDefault();

      const total = atualizarTotal();
      if (total === 0) {
        alert("Por favor, selecione pelo menos 1 item do cardápio para continuar!");
        return;
      }

      // Collect Selected Payment Method
      const pagamentoEl = document.querySelector('input[name="pagamento"]:checked');
      if (!pagamentoEl) {
        alert("Por favor, selecione a forma de pagamento!");
        return;
      }
      const pagamento = pagamentoEl.value;

      // Collect Items Text
      let itensTexto = "";
      produtos.forEach(p => {
        const qty = quantidades[p.id];
        if (qty > 0) {
          const subtotal = qty * p.preco;
          itensTexto += `• ${qty}x ${p.nome} (R$ ${subtotal.toFixed(2).replace('.', ',')})\n`;
        }
      });

      // Collect User Info
      const nome = document.getElementById("nome").value.trim();
      const telefone = document.getElementById("telefone").value.trim();
      const email = document.getElementById("email").value.trim();
      const data = document.getElementById("data").value;
      const pais = document.getElementById("pais").value;
      const cidade = document.getElementById("cidade").value.trim();
      const endereco = document.getElementById("endereco").value.trim();

      // Format Date
      const partesData = data.split("-");
      const dataFormatada = `${partesData[2]}/${partesData[1]}/${partesData[0]}`;

      // Assemble WhatsApp Message text
      const mensagem = 
`*NOVO PEDIDO DE COMPRA* 🛒
--------------------------------
*ITENS DO PEDIDO:*
${itensTexto}
*FORMA DE PAGAMENTO:* ${pagamento}
*VALOR TOTAL:* R$ ${total.toFixed(2).replace('.', ',')}
--------------------------------
*DADOS DE ENTREGA:*
*Nome:* ${nome}
*Telefone:* ${telefone}
*E-mail:* ${email}
*Data Desejada:* ${dataFormatada}
*País:* ${pais}
*Cidade:* ${cidade}
*Endereço:* ${endereco}

--------------------------------
✨ *Muito obrigado pela preferência, ${nome}!* 
Seu pedido está em processamento. Desejamos a você um excelente apetite! 😋🍔`;

      const numeroWhatsApp = "5585999316821";
      const whatsappUrl = `https://wa.me/${numeroWhatsApp}?text=${encodeURIComponent(mensagem)}`;

      // Show Modal
      const modal = document.getElementById("modalSucesso");
      modal.classList.remove("hidden");

      // Redirect after 1.5 seconds
      setTimeout(() => {
        window.open(whatsappUrl, "_blank");
        modal.classList.add("hidden");
      }, 1500);
    }
  </script>
</body>
</html>
