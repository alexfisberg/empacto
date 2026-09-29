# EmPacto — site de divulgação dos cursos

Protótipo de landing page (`index.html`, arquivo único, sem dependências de build) com os 7 formatos de formação da EmPacto, pronto para publicar no GitHub Pages com o domínio **empacto.social**.

---

## 1. Proposta de domínio — empacto.social

`.social` é um domínio genérico (gTLD), não um domínio brasileiro (`.br`) — por isso ele **não é registrado no Registro.br**, e sim em qualquer registrador internacional credenciado pela ICANN. Isso não muda nada na prática: o site funciona normalmente, com HTTPS, e-mail próprio etc.

**Comparação de registradores** (preços em 29/set/2026, dólar a ~R$5,20 — confirme o valor atual no carrinho antes de comprar):

| Registrador | 1º ano | Renovação | Observação |
|---|---|---|---|
| [Namecheap](https://www.namecheap.com/domains/registration/gtld/social/) | US$ 3,98 (~R$ 21) | US$ 55,98/ano (~R$ 291) | Preço de entrada muito baixo, mas o salto na renovação é grande — comum nesse mercado |
| [GoDaddy](https://www.godaddy.com/tlds/social-domain) | promocional (varia) | próximo de US$ 40–55/ano | Suporte em português, mas também tem salto na renovação |
| [SuperDomínios](https://superdominios.org/dominios/social/) | R$ 54,99/ano | próximo do mesmo valor | Preço fixo e previsível, cobrança em real, inclui 2 contas de e-mail e proteção de privacidade — bom para quem quer evitar surpresa na renovação |

**Recomendação:** para a EmPacto, que já pensa em manter o domínio no longo prazo (não é um teste de um ano), o critério mais importante não é o preço do primeiro ano — é o preço da renovação e não ter surpresa. O **SuperDomínios** (revendedor brasileiro credenciado ICANN) tem o custo mais previsível e cobrança em real; o **Namecheap** é uma alternativa internacional confiável, mas com preço de renovação mais alto e cobrança em dólar.

Passo a passo do registro:
1. Acesse o registrador escolhido e busque `empacto.social`.
2. Complete o cadastro e o pagamento (ative a proteção de privacidade do WHOIS, se oferecida).
3. Depois de registrado, você vai precisar editar a **zona de DNS** do domínio (passo 4 abaixo) — isso é feito no painel do próprio registrador.

---

## 2. Estrutura de arquivos deste site

```
empacto-site/
├── index.html   → a landing page (tudo em um arquivo: HTML + CSS + JS)
├── CNAME        → arquivo que diz ao GitHub qual domínio customizado usar
└── README.md    → este guia
```

Não há build, framework ou dependência — é HTML puro, então qualquer hospedagem de arquivo estático funciona (GitHub Pages, Netlify, Vercel, Cloudflare Pages). O passo a passo abaixo é para **GitHub Pages**, por ser gratuito e ser o que você pediu.

---

## 3. Passo a passo — publicar no GitHub Pages

### 3.1. Criar o repositório

1. Crie uma conta no [github.com](https://github.com), se ainda não tiver.
2. Clique em **New repository** (botão verde, ou `+` no canto superior direito → *New repository*).
3. Nome sugerido: `empacto-site` (pode ser outro nome, não precisa ser `empacto.github.io`).
4. Marque como **Public** (obrigatório para GitHub Pages gratuito).
5. Não marque "Add a README" — vamos subir os arquivos já prontos.
6. Clique em **Create repository**.

### 3.2. Subir os arquivos

Na página do repositório recém-criado:

1. Clique em **uploading an existing file** (ou no botão **Add file → Upload files**).
2. Arraste os três arquivos desta pasta: `index.html`, `CNAME` e `README.md`.
3. Role até o final da página e clique em **Commit changes**.

*(Alternativa via linha de comando, se preferir git local: `git init`, `git add .`, `git commit -m "site inicial"`, `git remote add origin <url-do-repo>`, `git push -u origin main`.)*

### 3.3. Ativar o GitHub Pages

1. No repositório, vá em **Settings** (aba no topo).
2. No menu lateral, clique em **Pages**.
3. Em **Build and deployment → Source**, selecione **Deploy from a branch**.
4. Em **Branch**, selecione `main` e a pasta `/ (root)`. Clique em **Save**.
5. Aguarde 1–2 minutos. O GitHub mostra o link temporário, algo como `https://seu-usuario.github.io/empacto-site/` — confirme que o site abre normalmente antes de seguir para o domínio próprio.

### 3.4. Conectar o domínio empacto.social

**No GitHub:**
1. Ainda em **Settings → Pages**, no campo **Custom domain**, digite `empacto.social` e clique em **Save**.
   - Isso atualiza automaticamente o arquivo `CNAME` do repositório (o mesmo que você já subiu).
2. Marque a opção **Enforce HTTPS** assim que ela ficar disponível (pode levar alguns minutos até o certificado ser emitido).

**No painel do registrador (SuperDomínios, Namecheap etc.), na configuração de DNS do domínio:**

Adicione estes registros — isso aponta `empacto.social` para os servidores do GitHub Pages:

| Tipo | Nome/Host | Valor |
|---|---|---|
| A | @ (ou em branco) | 185.199.108.153 |
| A | @ (ou em branco) | 185.199.109.153 |
| A | @ (ou em branco) | 185.199.110.153 |
| A | @ (ou em branco) | 185.199.111.153 |
| CNAME | www | seu-usuario.github.io |

- Os 4 registros **A** apontam o domínio raiz (`empacto.social`).
- O registro **CNAME** faz `www.empacto.social` redirecionar também — opcional, mas recomendado.
- Cada registrador tem uma tela ligeiramente diferente para isso ("Gerenciar DNS", "Zona DNS" ou "Advanced DNS") — o nome dos campos pode variar, mas a lógica é sempre Tipo + Host + Valor.

### 3.5. Aguardar propagação

A propagação de DNS pode levar de alguns minutos até 24–48h (geralmente é rápida, 1–2h). Para verificar se já propagou, use [dnschecker.org](https://dnschecker.org) e busque `empacto.social`.

Quando o certificado HTTPS for emitido automaticamente pelo GitHub (você verá um cadeado ao lado de "Enforce HTTPS" nas configurações), o site estará no ar em `https://empacto.social`.

---

## 4. O que ajustar antes de divulgar

O arquivo `index.html` tem dois pontos marcados como placeholder — procure por `TODO` no código ou pelos textos abaixo:

1. **Número de WhatsApp** — o formulário de contato abre o WhatsApp com um número fictício (`5511900000000`). Troque pelo número real da EmPacto no início do arquivo, na linha `var WHATSAPP_NUMBER = ...`.
2. **E-mail de contato** — está como `contato@empacto.social`; troque se o e-mail real for outro (e lembre de configurar essa caixa de e-mail no registrador, já que muitos oferecem e-mail incluso no plano do domínio).

Fora isso, o site já está funcional: navegação, os 7 cursos, seção "como funciona" e formulário de contato via WhatsApp — tudo em uma página só, responsivo para celular.

---

## 5. Próximos passos possíveis

- Adicionar Google Analytics ou Plausible para acompanhar visitas (basta um snippet de script no `<head>`).
- Trocar o link de WhatsApp por um formulário que salve os leads em uma planilha (dá para fazer com Google Forms embutido, por exemplo).
- Migrar de "página única" para páginas individuais por curso, se o catálogo crescer.
