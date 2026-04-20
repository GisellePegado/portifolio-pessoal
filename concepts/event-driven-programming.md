# ⚡ Programação Orientada a Eventos (Event-Driven Programming)

## 💡 O que é

Programação orientada a eventos é um paradigma em que o fluxo de execução do programa é determinado por **eventos** — ações do usuário (cliques, teclas pressionadas, scroll) ou do sistema (carregamento da página, timers). Em vez de executar instruções sequencialmente do início ao fim, o código registra **ouvintes de eventos** (`event listeners`) e aguarda passivamente até que o evento ocorra.

No JavaScript do navegador, o método central é `addEventListener(tipo, callback)`:

- `tipo` — nome do evento: `'click'`, `'scroll'`, `'keydown'`, `'load'`, etc.
- `callback` — função executada quando o evento dispara; recebe um objeto `Event` com informações sobre o que aconteceu

Esse modelo é fundamental para interfaces interativas porque o navegador é **assíncrono por natureza**: o usuário pode clicar, rolar e digitar em qualquer ordem e a qualquer momento.

## ⚙️ Como é usado neste projeto

O script embutido em `index.html` usa `addEventListener` para implementar toda a interatividade do portfólio:

| Evento | Alvo | Ação |
|--------|------|------|
| `scroll` | `window` | Atualiza o link ativo no menu de navegação |
| `load` | `window` | Inicializa o link ativo ao carregar a página |
| `click` | links `a[href^="#"]` | Intercepta e executa scroll suave |
| `click` | botão hambúrguer | Abre/fecha o menu mobile |
| `click` | links do menu mobile | Fecha o menu ao navegar |
| `click` | `document` | Fecha o menu ao clicar fora dele |
| `keydown` | `document` | Fecha o menu ao pressionar `Escape` |

## 🔍 Exemplo do projeto

```javascript
// index.html <script>

// Evento de scroll: atualiza o link ativo no menu
window.addEventListener('scroll', updateActiveMenuLink);
window.addEventListener('load',   updateActiveMenuLink);

// Evento de clique: smooth scroll em todos os links de âncora
document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
  anchor.addEventListener('click', function (e) {
    e.preventDefault(); // cancela o comportamento padrão do link
    const target = document.querySelector(this.getAttribute('href'));
    if (target) target.scrollIntoView({ behavior: 'smooth', block: 'start' });
  });
});

// Evento de teclado: fecha menu com Escape
document.addEventListener('keydown', (e) => {
  if (e.key === 'Escape' && mobileMenu.classList.contains('open')) {
    toggleMenu(false);
    hamburgerBtn.focus();
  }
});

// Evento de clique fora: fecha menu ao clicar no restante da página
document.addEventListener('click', (e) => {
  if (
    mobileMenu.classList.contains('open') &&
    !mobileMenu.contains(e.target) &&
    !hamburgerBtn.contains(e.target)
  ) {
    toggleMenu(false);
  }
});
```

> [!TIP]
> `e.preventDefault()` é chamado no clique dos links para evitar o scroll brusco nativo do navegador e substituí-lo pelo scroll animado com `scrollIntoView`.

## 📚 Recursos para aprofundamento

- [MDN — EventTarget.addEventListener()](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener) — referência completa com todos os tipos de eventos
- [MDN — Introduction to events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events) — guia introdutório ao modelo de eventos do DOM
