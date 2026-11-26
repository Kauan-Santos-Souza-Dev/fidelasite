# CLAUDE.md — Fidela Web

Este arquivo orienta o Claude Code neste repositório. Leia tudo antes de alterar qualquer coisa.

## Sobre o projeto

Site institucional da **Fidela Web**, empresa de criação de sites para pequenos negócios (e empresas de médio porte), fundada por **Kauan Santos**. O site apresenta a empresa, os serviços e uma vitrine de modelos de sites (a barbearia é o primeiro; outros nichos aparecem como "em breve").

- Idioma do site e dos textos: **português do Brasil**.
- Público inicial: barbearias e pequenos negócios de Brasília-DF. Outros nichos virão depois, então os textos devem ser **genéricos**, sem prender o site a um único segmento.

## Stack

- **HTML, CSS e JavaScript puro.** Sem frameworks.
- Bibliotecas só quando forem realmente necessárias. Nesse caso, explique qual e por quê antes de adicionar.
- Hospedagem: **Cloudflare Pages**, conectado a este repositório do GitHub.
- Back-end (Python/Django + MySQL) é um plano futuro e **não faz parte do escopo atual**. Não crie back-end sem eu pedir.

## Fluxo de branches e deploy

- `main` = **site oficial**. Todo push/merge nela publica em produção.
- Qualquer outra branch gera um **link de preview** no Cloudflare.
- **Nunca** faça push, merge, rebase ou qualquer alteração na `main`. Eu mesmo faço o merge depois de aprovar o preview.
- Trabalhe apenas na branch em que eu estiver. Antes de começar, confirme com `git branch` e me avise se estiver na `main`.
- **Não faça push** sem eu pedir. Faça commits locais e me avise quando estiver pronto.
- Não altere configurações de build/deploy nem crie arquivos de configuração do Cloudflare, a menos que eu peça.

## Padrões de código

- **Leia a estrutura do projeto antes de alterar** e siga o que já existe: nomes de arquivos, organização de pastas, variáveis CSS, componentes de header/footer e estilo visual.
- **Mobile first**, responsivo, HTML semântico e acessível (alt nas imagens, hierarquia de títulos coerente, contraste adequado, foco visível).
- Reutilize variáveis CSS e classes existentes em vez de criar estilos duplicados.
- Respeite `prefers-reduced-motion` em qualquer animação.
- Imagens com `alt` descritivo e `loading="lazy"` quando fizerem sentido.
- Não quebre páginas e rotas existentes. Header, footer e navegação devem ficar **consistentes em todas as páginas**. Ao criar uma página nova, adicione o link no menu e no footer de todas.
- Prefira mudanças pequenas e fáceis de revisar. Não refatore partes que não foram pedidas.

## Assets

- Os arquivos ficam na pasta `assets`. **Não renomeie nem apague** arquivos de lá sem eu pedir.
- O servidor do Cloudflare **diferencia maiúsculas de minúsculas**: use os nomes dos arquivos exatamente como estão (mesmas letras) e **caminhos relativos ao projeto**. Nunca use caminhos absolutos do Windows.
- Use somente imagens locais da pasta `assets`. Não baixe nem use links externos para imagens ou logos.
- Logos das tecnologias em **SVG** (`python.svg`, `django.svg`, `javascript.svg`, `nodejs.svg`, `mysql.svg` etc.); foto do fundador em **`fotopessoal.webp`** (fundo transparente). O `fotopessoal.png` original é mantido na pasta.
- Se faltar um asset, **não invente**: deixe um comentário no código, não quebre o layout e me avise.

## Regras de conteúdo e negócio

- O **contato principal é o WhatsApp**.
- **Instagram** oficial: https://www.instagram.com/fidelaweb/ . Use sempre esse link, com `target="_blank"` e `rel="noopener noreferrer"`. Se encontrar outro link de Instagram no projeto, avise ou corrija.
- **E-mail** só como texto, com botão de copiar (não como link `mailto`).
- **Sem depoimentos, números, estatísticas ou promessas inventados.** Se não foi informado por mim, não escreva.
- **O preço do plano pode aparecer no site; não mencione contrato, multa ou fidelidade.**
- Serviços de tráfego orgânico ou outros ainda não testados aparecem apenas como **"em breve"**, sem prometer resultado.
- O modelo de serviço pode ser descrito de forma geral (taxa inicial de desenvolvimento + assinatura mensal de manutenção).
- Na dúvida sobre um texto, uma informação ou uma regra de negócio, **pergunte** em vez de supor.

## Como trabalhar comigo

- Para tarefas maiores, **apresente um plano curto e espere minha aprovação** antes de implementar.
- Faça **commits pequenos e descritivos em português**, por exemplo:
  - `feat: adiciona página Quem somos`
  - `fix: atualiza link do Instagram`
  - `style: ajusta espaçamento da seção de tecnologias`
- Ao terminar uma tarefa, informe:
  1. arquivos criados e alterados;
  2. assets utilizados (e se algum faltou);
  3. decisões de design que tomou e pontos pendentes;
  4. como testar localmente.
- Explique de forma clara, mas sem enrolação. Tenho formação em Análise e Desenvolvimento de Sistemas, então não precisa explicar o básico de HTML/CSS/JS.

## Testar localmente

Abra o `index.html` no navegador ou rode um servidor estático na raiz do projeto:

```bash
python -m http.server 8000
```

Depois acesse `http://localhost:8000`. Confira mobile e desktop e se todos os links do menu funcionam.