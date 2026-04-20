# 📱 Design Responsivo (Responsive Design)

## 💡 O que é

Design responsivo é a abordagem de construir interfaces que se **adaptam ao tamanho e às características do dispositivo** do usuário — celular, tablet ou desktop — sem criar versões separadas do site. O objetivo é que o mesmo HTML e CSS produzam uma experiência adequada em qualquer tela.

Os três pilares do design responsivo são:

1. **Viewport meta tag** — informa ao navegador mobile que a largura da página deve seguir a largura real do dispositivo, não simular um desktop de 980px
2. **Media queries** — blocos `@media` que aplicam estilos apenas quando certas condições (largura, altura, orientação) são atendidas
3. **Layouts fluidos** — uso de unidades relativas (`%`, `vw`, `rem`, `clamp()`) em vez de pixels fixos, para que os elementos se expandam e contraiam naturalmente

Uma estratégia comum é o **mobile-first**: escrever os estilos base pensando em telas pequenas e usar media queries apenas para ampliar o layout nas telas maiores. A alternativa é o **desktop-first**, com media queries de `max-width` para adaptar o layout a telas menores.

## ⚙️ Como é usado neste projeto

`index.html` declara a meta tag de viewport na `<head>`, garantindo o comportamento correto em celulares. Em `style.css`, três breakpoints com `max-width` adaptam o layout:

- **900px** — reorganiza grids de duas colunas para uma
- **768px** — oculta o menu de navegação horizontal e exibe o botão hambúrguer; ajusta cards do portfólio
- **380px** — refinamentos para telas muito pequenas (ex: iPhone SE)

O projeto também inclui um menu hambúrguer completo (HTML + CSS + JS) que só aparece no mobile, substituindo a barra de navegação horizontal.

## 🔍 Exemplo do projeto

```html
<!-- index.html — viewport meta tag obrigatória -->
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

```css
/* style.css — breakpoints de adaptação */

/* Tablet e abaixo */
@media (max-width: 900px) {
  .formacao-grid { grid-template-columns: 1fr; }
}

/* Mobile */
@media (max-width: 768px) {
  .menu        { display: none; }          /* oculta nav desktop */
  .nav-hamburger { display: flex; }        /* exibe botão mobile */
  .portfolio-grid { grid-template-columns: 1fr; }
}

/* Telas muito pequenas */
@media (max-width: 380px) {
  /* ajustes finos para iPhone SE e similares */
}
```

> [!TIP]
> A combinação de `clamp()` para fontes e `@media` para layout reduz o número de breakpoints necessários — a tipografia se ajusta de forma contínua enquanto o layout muda apenas nos pontos críticos.

## 📚 Recursos para aprofundamento

- [MDN — Responsive Design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design) — introdução completa com exemplos
- [web.dev — Responsive web design basics](https://web.dev/articles/responsive-web-design-basics) — guia prático do Google
