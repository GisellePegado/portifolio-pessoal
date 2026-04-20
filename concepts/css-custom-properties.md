# 🎨 Propriedades Customizadas CSS (CSS Custom Properties)

## 💡 O que é

Propriedades customizadas CSS — popularmente chamadas de **variáveis CSS** — são identificadores definidos pelo desenvolvedor que armazenam valores reutilizáveis dentro de folhas de estilo. Elas são declaradas com dois hifens no início do nome (ex: `--cor-primaria`) e consumidas com a função `var()`.

Diferentemente de variáveis em pré-processadores como Sass ou Less, as propriedades customizadas CSS são **nativas do navegador**: existem no DOM, podem ser alteradas em tempo real via JavaScript e respeitam a cascata e a herança do CSS. Isso significa que um componente filho pode sobrescrever uma variável definida em seu pai sem afetar o restante do documento.

O padrão mais comum é declarar todas as variáveis globais no seletor `:root`, que representa o elemento raiz do documento (`<html>`). Isso cria um **sistema de design tokens** — um vocabulário central de cores, tamanhos, fontes e espaçamentos que garante consistência visual em todo o projeto.

## ⚙️ Como é usado neste projeto

Em `style.css`, o seletor `:root` define 15+ tokens de design usados em todo o arquivo:

- **Paleta de cores:** `--purple`, `--pink`, `--blue` e suas variantes `*-light`
- **Camadas de fundo:** `--bg`, `--bg-card`, `--bg-card-hover`
- **Bordas:** `--border`, `--border-hover`
- **Tipografia:** `--text-primary`, `--text-secondary`, `--text-muted`
- **Gradientes:** `--gradient-text`, `--gradient-btn`
- **Fontes:** `--font-display` (Fraunces) e `--font-body` (DM Sans)

Ao modificar um único token — por exemplo, `--purple: #6d28d9` —, toda a interface se atualiza automaticamente, sem necessidade de busca e substituição manual.

## 🔍 Exemplo do projeto

```css
/* style.css — declaração dos tokens globais */
:root {
  --purple: #7c3aed;
  --purple-light: #c4b5fd;
  --pink: #db2777;
  --bg: #0d0a14;
  --bg-card: rgba(255, 255, 255, 0.04);
  --border: rgba(255, 255, 255, 0.08);
  --gradient-btn: linear-gradient(135deg, #7c3aed, #db2777);
  --font-display: 'Fraunces', serif;
  --font-body: 'DM Sans', sans-serif;
}

/* Consumo em qualquer seletor do arquivo */
body {
  font-family: var(--font-body);
  background: var(--bg);
  color: var(--text-primary);
}

.nav-hamburger {
  background: var(--gradient-btn);
  border: 0.5px solid var(--border);
}
```

## 📚 Recursos para aprofundamento

- [MDN — Using CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties) — referência completa com exemplos de herança e fallback
- [web.dev — CSS Custom Properties](https://web.dev/articles/css-variables) — guia prático sobre tokens de design e temas dinâmicos
