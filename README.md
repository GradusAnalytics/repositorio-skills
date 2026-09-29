# Repositório de Skills — ferramenta freeform do PPR

Catálogo das skills da Gradus (Gestão Metodológica), publicado no PPR como ferramenta
**freeform**: o PPR carrega `repositorio-skills.html` num iframe a partir do GitHub Pages.

| Branch | URL servida | Uso no PPR |
|---|---|---|
| `main` | https://gradusanalytics.github.io/repositorio-skills/main/repositorio-skills.html | stage `prd` |
| `dev`  | https://gradusanalytics.github.io/repositorio-skills/dev/repositorio-skills.html  | testes |

O workflow `.github/workflows/deploy-pages.yml` copia os `.html` de cada branch para a pasta
de mesmo nome na `gh-pages` a cada push.

## Usuário logado

A página não faz login. Ao carregar o iframe, o PPR envia
`postMessage({type:'ppr.init', payload:{user:{email, nome, is_staff}, ferramenta, tema}})`.
A página só aceita a mensagem da janela-mãe e das origens em `PPR_ORIGENS`, monta o
usuário e responde `ppr.ready`, que acende "Conectado" no cabeçalho do PPR.

- Admin (Gestão Metodológica) = e-mails em `ADMINS_EMAILS`, **a definir**; vazia, todos entram como consulta.
  É checagem só no navegador, não controle de acesso.
- Aberta fora do PPR, a página mostra um aviso e não inicia. `?demo=1` liga o modo demonstração
  (perfis fictícios) para testar sem o PPR.

## Limitação conhecida

Não há backend: cadastros, sugestões e aprovações vivem na memória da sessão e somem ao
recarregar. As skills em si ficam no repositório privado `GradusAnalytics/repositorio-skills-conteudo`.

**Este repositório é público** (exigência do GitHub Pages no plano Free): não commitar aqui
conteúdo interno.
