# 📬 Formulário com Serviço Externo (Third-Party Form Integration)

## 💡 O que é

Sites estáticos — como portfólios em HTML puro hospedados no GitHub Pages — não têm backend próprio para processar dados de formulários. A solução mais simples é delegar esse processamento a um **serviço externo de formulários**: o HTML envia os dados para a URL do serviço via `POST`, e o serviço cuida de receber, validar, armazenar e encaminhar as mensagens (geralmente por e-mail).

Os serviços mais populares são:

- **Formspree** — basta apontar o `action` do `<form>` para a URL do endpoint criado na plataforma
- **Netlify Forms** — detecta formulários automaticamente no deploy via Netlify
- **Web3Forms** — similar ao Formspree, gratuito até certo volume

Essa abordagem elimina a necessidade de criar um servidor Node.js, PHP ou Python apenas para receber contatos, mantendo a simplicidade da hospedagem estática.

## ⚙️ Como é usado neste projeto

O formulário de contato em `index.html` usa o **Formspree**: o atributo `action` aponta para o endpoint personalizado `https://formspree.io/f/mykldwjd`. Quando o usuário clica em "Enviar mensagem", o navegador faz um `POST` com os campos `nome`, `email` e `mensagem` diretamente para o Formspree, que encaminha a mensagem para o e-mail cadastrado na conta.

Não é necessário nenhum JavaScript para o envio — o comportamento padrão do `<form>` com `method="POST"` é suficiente.

## 🔍 Exemplo do projeto

```html
<!-- index.html — formulário de contato via Formspree -->
<form
  action="https://formspree.io/f/mykldwjd"
  method="POST"
  class="contato-form"
>
  <div class="form-group">
    <label for="nome">Nome</label>
    <input type="text" id="nome" name="nome" placeholder="Seu nome" required />
  </div>

  <div class="form-group">
    <label for="email">E-mail</label>
    <input type="email" id="email" name="email" placeholder="seu@email.com" required />
  </div>

  <div class="form-group">
    <label for="mensagem">Mensagem</label>
    <textarea id="mensagem" name="mensagem" rows="5" required></textarea>
  </div>

  <button type="submit" class="submit-btn">Enviar mensagem →</button>
</form>
```

> [!NOTE]
> O atributo `required` nos campos garante validação nativa do navegador antes do envio — sem JavaScript adicional. O Formspree também realiza validação do lado servidor.

## 📚 Recursos para aprofundamento

- [Formspree — Getting started](https://formspree.io/guides/) — guia de configuração e personalização de formulários
- [MDN — Sending form data](https://developer.mozilla.org/en-US/docs/Learn/Forms/Sending_and_retrieving_form_data) — como o método POST funciona no protocolo HTTP
