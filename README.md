# Site EmPacto

Site estático em três idiomas: `index.html` (português), `en/index.html` (inglês) e `es/index.html` (espanhol), mais as pastas `img/` e `docs/`, compartilhadas pelas três versões. Funciona no GitHub Pages sem nenhuma etapa de build.

## Publicar no GitHub Pages

1. Crie um repositório no GitHub (por exemplo `empacto-site`).
2. Envie todo o conteúdo desta pasta para a raiz do repositório (botão **Add file → Upload files**, arrastando `index.html`, `en/`, `es/`, `img/`, `docs/` e este `README.md`).
3. No repositório, vá em **Settings → Pages**. Em *Build and deployment*, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`, e salve.
4. Em um ou dois minutos o site fica disponível em `https://SEU-USUARIO.github.io/empacto-site/`.
5. Para usar o domínio próprio (ex.: `empacto.social`), preencha **Custom domain** na mesma tela e configure o DNS conforme as instruções do GitHub.

## Formulários (envio direto para oi@empacto.social)

Os dois formulários do site (contato e "Por onde começar") enviam as mensagens direto pelo site, sem abrir o programa de e-mail do visitante. O envio usa o serviço gratuito **FormSubmit**.

**Configuração provisória (atual):** as mensagens vão para **alex@mochilasocial.com**, com cópia para **mbm.manuela@gmail.com**.

**Ativação (uma vez só):**

1. Com o site no ar, envie uma mensagem de teste por um dos formulários.
2. O FormSubmit manda um e-mail de confirmação para alex@mochilasocial.com. Abra e clique em **Activate Form**.
3. Pronto: a partir daí todas as mensagens chegam para Alex, com cópia para Manuela. A primeira mensagem (a de teste) não é entregue; as seguintes sim.

**Quando oi@empacto.social existir:** no início do primeiro `<script>` de `index.html`, `en/index.html` e `es/index.html`, troque o endpoint para `https://formsubmit.co/ajax/oi@empacto.social`, o `email` para `oi@empacto.social` e apague a linha `cc`. Depois repita a ativação (o FormSubmit pede uma confirmação para cada endereço novo).

Cada mensagem chega com nome, e-mail (dá para responder direto), mensagem e, no caso do "Por onde começar", o diagnóstico completo (objetivo, perfil, momento, desafio e os dois caminhos sugeridos).

**Trocar o serviço de envio:** a configuração fica no início do primeiro `<script>` do `index.html`:

```js
window.EMPACTO_FORM = {
  endpoint: 'https://formsubmit.co/ajax/alex@mochilasocial.com',
  cc: 'mbm.manuela@gmail.com',
  email: 'alex@mochilasocial.com',
};
```

- Para usar o **Formspree**, crie um formulário em formspree.io com o e-mail oi@empacto.social e troque o `endpoint` por `https://formspree.io/f/SEU_ID`.
- Se o envio falhar, o site mostra ao visitante o endereço definido em `email` para ele escrever direto.

## Outros contatos no site

- WhatsApp (botão fixo): (11) 99212-4664.
- E-mail exibido no rodapé: oi@empacto.social.

## Idiomas

As três versões têm o mesmo conteúdo, fotos e funcionalidades (Por onde começar, recomendações, formulários e WhatsApp), só traduzidos. O seletor PT / EN / ES no topo e no rodapé leva de uma para a outra. Ao alterar um texto em português, lembre de ajustar também `en/index.html` e `es/index.html`.
