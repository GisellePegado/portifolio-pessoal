# 📄 Aplicação de Página Única (Single-Page Application)

## 💡 O que é

Uma **Single-Page Application (SPA)** é uma aplicação web que carrega um único arquivo HTML e apresenta todo o conteúdo dentro dele, sem recarregar a página ao navegar entre seções. A sensação de "mudar de página" é simulada por JavaScript: o conteúdo é mostrado, ocultado ou atualizado dinamicamente, enquanto a URL pode mudar via hash (`#sobre`) ou via History API.

Há dois modelos comuns:

1. **SPA com frameworks** (React, Vue, Angular) — o JavaScript gera e gerencia o HTML dinamicamente; quase nenhum conteúdo vem do servidor
2. **SPA estática com âncoras** — todo o HTML já está no arquivo; o JavaScript apenas rola para seções e atualiza estados visuais (como o link ativo no menu)

O segundo modelo, mais simples e sem dependências, é ideal para portfólios e landing pages. Ele mantém os benefícios de SEO (conteúdo presente no HTML estático) e elimina a complexidade de bundlers e frameworks.

## ⚙️ Como é usado neste projeto

O portfólio é uma SPA estática: todo o conteúdo (hero, sobre, formação, portfólio, contato) está em um único `index.html`. A navegação funciona via **hash links** (`href="#sobre"`): ao clicar, o JavaScript intercepta o evento, cancela o scroll padrão e executa `scrollIntoView` com animação suave.

O JavaScript também detecta qual seção está visível enquanto o usuário rola a página (via `getBoundingClientRect()`), atualizando a classe `active` no link correspondente do menu — criando a ilusão de navegação entre "páginas".

## 🔍 Exemplo do projeto

```html
<!-- index.html — todos os links apontam para IDs internos -->
<nav>
  <ul class="menu">
    <li><a href="#inicio" class="menu-link active">Início</a></li>
    <li><a href="#sobre"  class="menu-link">Sobre</a></li>
    <li><a href="#portfolio" class="menu-link">Portfólio</a></li>
  </ul>
</nav>

<!-- Todo o conteúdo existe no mesmo HTML, em seções com IDs -->
<main>
  <section id="inicio">  <!-- hero --> </section>
  <section id="sobre">   <!-- bio  --> </section>
  <section id="portfolio"> <!-- projetos --> </section>
</main>
```

```javascript
// index.html <script> — link ativo baseado na seção visível
function updateActiveMenuLink() {
  const sections = document.querySelectorAll('section[id]');
  const navLinks  = document.querySelectorAll('.menu-link');
  let current = '';

  sections.forEach((section) => {
    const rect = section.getBoundingClientRect();
    if (rect.top <= 120 && rect.bottom >= 120) current = section.id;
  });

  navLinks.forEach((link) => link.classList.remove('active'));
  const active = document.querySelector(`a[href="#${current}"]`);
  if (active) active.classList.add('active');
}

window.addEventListener('scroll', updateActiveMenuLink);
```

## 📚 Recursos para aprofundamento

- [MDN — History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API) — como manipular a URL sem recarregar a página
- [web.dev — JavaScript SPA and SEO](https://web.dev/articles/rendering-on-the-web) — trade-offs de renderização para SPAs
