# 📐 Tipografia Fluida (Fluid Typography)

## 💡 O que é

Tipografia fluida é a técnica de fazer tamanhos de fonte **crescerem e diminuírem suavemente** conforme a largura da tela muda — sem saltos abruptos causados por media queries. O resultado é um tamanho de texto sempre proporcional ao viewport, como se a fonte "respirasse" junto com o layout.

A principal ferramenta CSS para isso é a função `clamp(mínimo, preferido, máximo)`:

- **mínimo** — o menor tamanho aceito (ex: `1.7rem` em telas muito pequenas)
- **preferido** — valor relativo ao viewport que cresce com a largura (ex: `5vw`)
- **máximo** — o maior tamanho aceito (ex: `2.4rem` em telas grandes)

O navegador escolhe o valor **preferido** quando ele está entre mínimo e máximo. Caso contrário, usa o limite correspondente. Isso elimina vários breakpoints de `@media` apenas para ajustar fontes e torna o código muito mais limpo.

`clamp()` também funciona para larguras, margens e espaçamentos — qualquer propriedade que aceite unidades de comprimento.

## ⚙️ Como é usado neste projeto

`style.css` usa `clamp()` em quatro pontos para os títulos mais proeminentes do portfólio, garantindo legibilidade em mobile sem exagero em desktop:

| Elemento | Mínimo | Preferido | Máximo |
|----------|--------|-----------|--------|
| Título da hero (`h1`) | `2.8rem` | `8vw` | `5.5rem` |
| Subtítulo da hero | `1rem` | `2.5vw` | `1.15rem` |
| Títulos de seção (`h2`) | `1.7rem` | `5vw` | `2.4rem` |
| Subtítulos de seção | `1.4rem` | `4vw` | `1.8rem` |

## 🔍 Exemplo do projeto

```css
/* style.css — tipografia fluida nos títulos principais */

/* Nome na seção hero — encolhe em mobile, amplia em desktop */
.hero-name {
  font-size: clamp(2.8rem, 8vw, 5.5rem);
}

/* Subtítulo descritivo abaixo do nome */
.hero-sub {
  font-size: clamp(1rem, 2.5vw, 1.15rem);
}

/* Títulos das seções (Sobre, Formação, Portfólio...) */
.section-title {
  font-size: clamp(1.7rem, 5vw, 2.4rem);
}
```

Em uma tela de 400px de largura, `8vw` equivale a `32px` — que está entre `2.8rem ≈ 44.8px` e `5.5rem ≈ 88px`, então o navegador usa `2.8rem`. Em uma tela de 1200px, `8vw = 96px` ultrapassa `5.5rem ≈ 88px`, então o navegador trava em `5.5rem`.

## 📚 Recursos para aprofundamento

- [MDN — clamp()](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp) — sintaxe, compatibilidade e exemplos detalhados
- [CSS Tricks — Fluid Typography](https://css-tricks.com/simplified-fluid-typography/) — explicação visual com calculadora interativa
