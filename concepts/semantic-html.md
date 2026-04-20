# 🏗️ HTML Semântico (Semantic HTML)

## 💡 O que é

HTML semântico é o uso de elementos cujo **nome descreve o significado do conteúdo** que contêm, e não apenas sua aparência visual. Em vez de usar `<div>` para tudo, o desenvolvedor escolhe o elemento que comunica corretamente a função daquele bloco: `<header>` para cabeçalho, `<nav>` para navegação, `<main>` para conteúdo principal, `<section>` para seções temáticas, `<footer>` para rodapé.

Isso traz três benefícios concretos:

1. **Acessibilidade** — leitores de tela (usados por pessoas com deficiência visual) usam a estrutura semântica para criar um "mapa" da página e permitir navegação por atalhos
2. **SEO** — mecanismos de busca interpretam a hierarquia da página com mais precisão, priorizando conteúdo em `<main>` sobre conteúdo em `<aside>`
3. **Manutenibilidade** — o código fica autodocumentado: qualquer desenvolvedor entende a estrutura sem comentários adicionais

Os elementos semânticos introduzidos no HTML5 não substituem `<div>` e `<span>` — esses ainda são válidos para agrupamentos puramente visuais sem significado próprio.

## ⚙️ Como é usado neste projeto

`index.html` segue a estrutura semântica recomendada pelo HTML5:

- `<header>` — contém o `<nav>` com a barra de navegação e o menu mobile
- `<nav>` — lista de links de âncora para as seções
- `<main>` — agrupa todas as seções de conteúdo
- `<section id="...">` — cada bloco temático (Início, Sobre, Formação, Portfólio, Contato)
- `<footer>` — rodapé com copyright
- `<form>` — formulário de contato (elemento semântico para dados de entrada)

## 🔍 Exemplo do projeto

```html
<!-- index.html — estrutura semântica completa -->
<header>
  <nav class="cabecalho">
    <ul class="menu">
      <li><a href="#inicio">Início</a></li>
      <li><a href="#sobre">Sobre</a></li>
      <!-- ... -->
    </ul>
  </nav>
</header>

<main>
  <section id="inicio"> <!-- Seção Hero --> </section>
  <section id="sobre">  <!-- Sobre Mim  --> </section>
  <section id="formacao"> <!-- Formação --> </section>
  <section id="portfolio"> <!-- Projetos --> </section>
  <section id="contato">   <!-- Contato  --> </section>
</main>

<footer>
  <p>&copy; 2025 Giselle Pegado. Todos os direitos reservados.</p>
</footer>
```

> [!NOTE]
> Os atributos `id` nas `<section>`s servem a dois propósitos: âncora para os links de navegação (`href="#sobre"`) e identificador para o JavaScript detectar qual seção está visível no scroll.

## 📚 Recursos para aprofundamento

- [MDN — HTML elements reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) — catálogo de todos os elementos semânticos com descrições
- [web.dev — Semantic HTML](https://web.dev/learn/html/semantic-html) — módulo completo sobre boas práticas de estrutura
