# Como colocar seu portfólio no ar de graça

Este arquivo explica, passo a passo, as formas de publicar o portfólio sem pagar nada.
Você não precisa mexer em nenhuma linha de código para publicar.

---

## Opção 1 — A mais rápida: publicar direto no Lovable

1. Abra o projeto no Lovable.
2. Clique no botão **Publicar** (canto superior direito) e depois em **Publicar alterações**.
3. Em cerca de 1 minuto o site abre em um endereço grátis terminando em `.lovable.app`.

Pronto: qualquer pessoa com o link consegue ver o site. Não é preciso GitHub, nem terminal, nem cartão de crédito.

---

## Opção 2 — Recomendada: GitHub (guarda o código) + Vercel (publica de graça)

A Vercel tem plano gratuito (Hobby) que serve para portfólio pessoal, e o endereço fica aberto para qualquer pessoa.

### Passo 1 — Criar conta e repositório no GitHub

1. Acesse **github.com** e crie uma conta (grátis).
2. No canto superior direito, clique em **+** e depois em **New repository**.
3. Em **Repository name**, escreva: `portfolio-weslley`
4. Deixe **Public** marcado se quiser que o código fique visível para qualquer pessoa.
5. **Não** marque a opção "Add a README file" — deixe o repositório vazio.
6. Clique em **Create repository**.

### Passo 2 — Enviar os arquivos do projeto

**Jeito mais fácil (arrastar e soltar, sem comando):**

1. Abra a página do repositório vazio no navegador e clique no link **uploading an existing file**
   (ou digite `github.com/SEU-USUARIO/portfolio-weslley/upload`, trocando SEU-USUARIO pelo seu nome de usuário).
2. No Windows, abra a pasta do projeto e **arraste todos os arquivos e pastas** para a janela do navegador:
   `src`, `public`, `package.json`, `package-lock.json`, `tsconfig.json`, `vite.config.ts`, os arquivos que começam com ponto (`.gitignore`, `.nvmrc`), etc.
3. **Não arraste a pasta `node_modules`** — ela é enorme e não deve subir.
4. Espere a barra de upload terminar (pode demorar um pouco por causa das imagens) e clique em **Commit changes**.

**Jeito alternativo (pelo terminal):**

Abra o terminal (cmd) dentro da pasta do projeto e digite, um por vez:

```
git init
git add .
git commit -m "Meu portfólio"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/portfolio-weslley.git
git push -u origin main
```

Troque `SEU-USUARIO` pelo seu nome de usuário do GitHub. Se o Windows perguntar como entrar, use a janela de login que aparece (ou o Git Credential Manager).

### Passo 3 — Publicar na Vercel

1. Acesse **vercel.com** e clique em **Sign Up**.
2. Escolha **Continue with GitHub** e autorize o acesso.
3. No painel, clique em **Add New...** e depois em **Project**.
4. Procure `portfolio-weslley` na lista e clique em **Import**.
5. **Não precisa mudar nada**: a Vercel reconhece o projeto sozinha (Build Command: `npm run build`).
6. Clique em **Deploy** e aguarde de 1 a 2 minutos.
7. No final aparece um endereço como `https://portfolio-weslley.vercel.app`. Esse é o seu site, no ar e aberto para qualquer pessoa.

### Passo 4 — Atualizar depois de mudar algo

1. Faça a mudança no código.
2. Suba a mudança para o GitHub (arraste os arquivos alterados de novo, ou rode `git add .`, `git commit -m "..."`, `git push`).
3. A Vercel percebe a mudança e publica sozinha, sem você fazer nada.

---

## Opção 3 — Netlify (alternativa à Vercel)

1. Acesse **netlify.com** e entre com a conta do GitHub.
2. Clique em **Add new site** e depois em **Import an existing project**.
3. Escolha o repositório `portfolio-weslley`.
4. Em **Build command** deixe `npm run build`. Não precisa mexer em mais nada.
5. Clique em **Deploy site**.

---

## Requisitos do computador

- **Node.js 20.19 ou mais novo** (o 22 é o recomendado). Confira com `node -v`.
- O arquivo `package-lock.json` está no projeto: ele garante que a instalação fique idêntica em qualquer computador.
- O arquivo `.nvmrc` diz às plataformas de hospedagem para usar o Node 22.
- Nunca suba para o repositório: `node_modules`, `dist`, `.output`, `.vercel`, `.netlify`.

## Antes de publicar (controle de qualidade)

```
npm install
npm run test
npm run build
```

Se os três rodarem sem erro, o site está pronto para publicar.

## Domínio próprio (opcional, pago)

- Na Vercel: **Settings → Domains → Add domain**.
- No Lovable: **Project settings → Domains**.

## Problemas comuns

| O que aparece | O que fazer |
|---|---|
| `vite: command not found` | Rode `npm install` primeiro, dentro da pasta do projeto. |
| A Vercel dá erro no build | Abra a aba **Build logs**, veja a primeira linha de erro e confira se o Node é 22 (o `.nvmrc` cuida disso). |
| O site abre, mas alguma imagem não aparece | Confirme que a pasta `public` foi enviada inteira para o repositório. |
| `Deseja finalizar o arquivo em lotes (S/N)?` no Windows | Digite `N` para o servidor continuar rodando. |
| O servidor parou de responder | Rode `npm run dev` de novo e deixe a janela aberta. |

## Sobre as imagens

As fotos e telas que você enviou estão em `public/images/projects/` e vão junto no site.
As imagens geradas por computador têm o aviso "Imagem ilustrativa" e podem ser trocadas pelas originais
basta substituir o arquivo na mesma pasta, mantendo o mesmo nome.
