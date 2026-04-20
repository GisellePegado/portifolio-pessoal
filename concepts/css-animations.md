# ✨ Animações CSS (CSS Animations)

## 💡 O que é

Animações CSS permitem que elementos HTML transicionem suavemente entre estados visuais ao longo do tempo, **sem qualquer código JavaScript**. Elas são compostas por duas partes: a regra `@keyframes`, que define os fotogramas-chave da animação (início, meio, fim), e as propriedades `animation-*`, que controlam como e quando a animação é aplicada a um elemento.

As propriedades mais usadas são:

- `animation-name` — nome do `@keyframes` a aplicar
- `animation-duration` — tempo total de um ciclo
- `animation-delay` — espera antes de iniciar
- `animation-iteration-count` — quantas vezes repetir (`infinite` para loop eterno)
- `animation-timing-function` — curva de aceleração (`ease`, `linear`, `ease-in-out`)
- `animation-direction` — direção (`alternate` vai e volta entre 0% e 100%)

Animações CSS são altamente performáticas quando aplicadas sobre propriedades como `transform` e `opacity`, pois o navegador pode delegá-las ao compositor gráfico sem afetar o layout da página.

## ⚙️ Como é usado neste projeto

A animação mais visível do portfólio é o **efeito aurora de fundo**, formado por quatro `div`s com a classe `aurora-orb`. Cada orb usa a mesma `@keyframes drift` — que alterna posição e escala — mas com durações e delays diferentes, criando um movimento orgânico e não sincronizado.

O projeto também respeita a preferência do sistema operacional do usuário via `@media (prefers-reduced-motion: reduce)`, reduzindo as animações para usuários que as desabilitaram por razões de acessibilidade ou saúde.

## 🔍 Exemplo do projeto

```css
/* style.css — definição dos fotogramas-chave */
@keyframes drift {
  0%   { transform: translate(0, 0) scale(1); }
  100% { transform: translate(40px, -30px) scale(1.08); }
}

/* Aplicação nas aurora orbs */
.aurora-orb {
  animation: drift 10s ease-in-out infinite alternate;
}

.orb-1 { background: var(--purple); animation-duration: 12s; }
.orb-2 { background: var(--pink);   animation-duration: 9s;  animation-delay: -3s; }
.orb-3 { background: var(--blue);   animation-duration: 14s; animation-delay: -6s; }
.orb-4 { background: var(--purple); animation-duration: 11s; animation-delay: -2s; }

/* Respeito à preferência do usuário */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

> [!NOTE]
> O `animation-delay` negativo é uma técnica que faz a animação iniciar já no meio do ciclo, evitando que todos os orbs se movam no mesmo compasso ao carregar a página.

## 📚 Recursos para aprofundamento

- [MDN — CSS Animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animations/Using_CSS_animations) — guia completo com todos os valores e propriedades
- [web.dev — Animations Guide](https://web.dev/articles/animations-guide) — boas práticas de performance com `transform` e `opacity`
