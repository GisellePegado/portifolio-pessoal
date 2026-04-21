# 🚀 Páginas GitHub (GitHub Pages)

## 💡 O que é

GitHub Pages é um serviço de **hospedagem estática gratuita** oferecido pelo GitHub. Ele publica automaticamente o conteúdo de um repositório como um site acessível na internet, sem necessidade de servidor, banco de dados ou configuração de infraestrutura.

O serviço é ideal para:

- Portfólios pessoais e sites de apresentação
- Documentação de projetos open source
- Projetos de frontend em HTML, CSS e JavaScript
- Blogs gerados estaticamente (ex: com Jekyll ou Hugo)

O GitHub Pages funciona servindo os arquivos estáticos do repositório diretamente ao navegador. O endereço padrão segue o padrão `https://<usuario>.github.io/<repositorio>/`. Para projetos especiais do tipo `<usuario>.github.io`, o repositório em si se torna o domínio raiz.

O deploy acontece automaticamente a cada `git push` na branch configurada (normalmente `main` ou `gh-pages`), sem necessidade de pipeline de CI/CD adicional para sites estáticos simples.

## ⚙️ Como é usado neste projeto

O portfólio está publicado em **https://gisellepegado.github.io/portifolio-pessoal/** via GitHub Pages, servindo os arquivos `index.html`, `style.css` e `imagemgi.jpg` diretamente do repositório. Qualquer alteração comitada na branch `main` é refletida no site em segundos.

Não há backend, banco de dados ou build step envolvido — o navegador recebe exatamente os arquivos que estão no repositório.

## 🔍 Exemplo do projeto

```
Repositório: github.com/GisellePegado/portifolio-pessoal
Branch:      main
Arquivos publicados:
  index.html   → https://gisellepegado.github.io/portifolio-pessoal/
  style.css    → carregado pelo index.html
  imagemgi.jpg → referenciada pelo index.html

URL pública: https://gisellepegado.github.io/portifolio-pessoal/
```

Para ativar o GitHub Pages em um repositório:

```
Repositório → Settings → Pages → Source: Deploy from a branch → Branch: main → /root
```

## 📚 Recursos para aprofundamento

- [GitHub Docs — GitHub Pages](https://docs.github.com/en/pages) — documentação oficial com guia de configuração e domínios customizados
- [GitHub Pages — Getting started](https://pages.github.com/) — tutorial interativo oficial
