# ♿ Acessibilidade Web (Web Accessibility)

## 💡 O que é

Acessibilidade web (também chamada de **a11y** — "a" + 11 letras + "y") é o conjunto de práticas que tornam sites e aplicações utilizáveis por **todas as pessoas**, incluindo aquelas com deficiências visuais, motoras, auditivas ou cognitivas. O padrão internacional que guia essas práticas é o **WCAG** (Web Content Accessibility Guidelines), mantido pelo W3C.

Na prática, acessibilidade web envolve:

- **ARIA (Accessible Rich Internet Applications)** — atributos HTML que comunicam estado e papel de elementos dinâmicos para tecnologias assistivas (leitores de tela)
- **Navegação por teclado** — garantir que toda funcionalidade seja acessível sem mouse
- **Redução de movimento** — respeitar usuários que têm sensibilidade a animações (condições como epilepsia fotossensível ou vertigem)
- **Contraste de cores** — garantir que texto seja legível sobre o fundo

ARIA não substitui HTML semântico — ela complementa casos onde o comportamento interativo vai além do que os elementos nativos comunicam por padrão.

## ⚙️ Como é usado neste projeto

O portfólio implementa várias práticas de acessibilidade no menu hambúrguer e nas animações de fundo:

**Atributos ARIA no hambúrguer:**
- `aria-label="Abrir menu"` — descreve o botão para leitores de tela (que não enxergam as três barrinhas)
- `aria-expanded="false/true"` — comunica se o menu está aberto ou fechado
- `aria-controls="mobile-menu"` — referencia o elemento que o botão controla
- `aria-hidden="true"` no menu fechado — oculta o menu do leitor de tela quando invisível

**Navegação por teclado:**
- Ao pressionar `Escape`, o menu fecha e o foco retorna ao botão hambúrguer (`hamburgerBtn.focus()`)

**Preferência de movimento reduzido:**
- `@media (prefers-reduced-motion: reduce)` desativa animações para usuários que configuraram isso no SO

**Aria semântico:**
- `aria-hidden="true"` na `div.aurora-canvas` — impede que os orbs decorativos poluam a árvore de acessibilidade

## 🔍 Exemplo do projeto

```html
<!-- index.html — botão hambúrguer com ARIA completo -->
<button
  class="nav-hamburger"
  aria-label="Abrir menu"
  aria-expanded="false"
  aria-controls="mobile-menu"
>
  <span class="hamburger-bar"></span>
  <span class="hamburger-bar"></span>
  <span class="hamburger-bar"></span>
</button>

<!-- Menu mobile referenciado pelo aria-controls -->
<div class="mobile-menu" id="mobile-menu" aria-hidden="true">
  <!-- links... -->
</div>

<!-- Elemento decorativo excluído da árvore de acessibilidade -->
<div class="aurora-canvas" aria-hidden="true">
  <div class="aurora-orb orb-1"></div>
</div>
```

```javascript
// index.html <script> — devolução de foco ao fechar com Escape
document.addEventListener('keydown', (e) => {
  if (e.key === 'Escape' && mobileMenu.classList.contains('open')) {
    toggleMenu(false);
    hamburgerBtn.focus(); // foco retorna ao botão
  }
});
```

```css
/* style.css — respeito à preferência de movimento reduzido */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## 📚 Recursos para aprofundamento

- [MDN — ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA) — guia completo de atributos e padrões ARIA
- [web.dev — Accessibility](https://web.dev/learn/accessibility) — curso completo de acessibilidade web do Google
- [WCAG 2.1 Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/) — critérios de sucesso por nível (A, AA, AAA)
