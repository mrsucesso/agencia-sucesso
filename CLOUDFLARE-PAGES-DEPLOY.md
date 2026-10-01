# Publicação — Cloudflare Pages

## Mecanismo oficial

- Repositório: `mrsucesso/agencia-sucesso`
- Branch de produção: `main`
- Projeto Cloudflare Pages: `agencia-sucesso`
- Domínio: `https://agencia.sucesso.com.br`
- Diretório publicado: raiz do repositório (arquivos rastreados pelo Git)
- Build: nenhum; site HTML estático
- Automação: GitHub Actions (`.github/workflows/deploy.yml`) executa `cloudflare/wrangler-action@v3` em cada push para `main` e envia os arquivos rastreados ao projeto Pages com branch e SHA do commit.
- Credenciais do workflow: secrets `CLOUDFLARE_API_TOKEN` e `CLOUDFLARE_ACCOUNT_ID`; nunca armazenar valores no repositório.

## Publicar propostas

Adicionar uma pasta com `index.html` em:

```text
orcamentos/<cliente>/index.html
```

Exemplo:

```text
orcamentos/edcar/index.html
```

Após commit e push para `main`, o GitHub Actions publica o site completo no Cloudflare Pages. A URL fica:

```text
https://agencia.sucesso.com.br/orcamentos/<cliente>/
```

Não é necessário executar Wrangler manualmente. Assets relativos devem ser testados na rota final; em `/orcamentos/<cliente>/`, `../../canva/logo-sucesso.png` resolve para `/canva/logo-sucesso.png`.

## Auditoria e comportamento de rotas

Na auditoria de 01/10/2026, o projeto existente era Direct Upload: o recurso Pages não tinha fonte GitHub associada (`source: null`). A branch de produção estava definida como `main`, mas isso não significava integração automática. O último deploy era `ad_hoc`, sem SHA; o workflow anterior era “Deploy to GitHub Pages”, falhava ao consultar um site GitHub Pages inexistente e não publicava no Cloudflare.

O projeto declara `uses_functions: false`. Não havia `_redirects`, `_routes.json`, configuração Wrangler ou Functions no repositório auditado. O Pages retornava a homepage também para `/orcamentos/edcar/` e para o logo ausente no snapshot publicado. Sem regra própria, Cloudflare Pages usa o `index.html` da raiz como fallback para rotas desconhecidas. Arquivos físicos `orcamentos/<cliente>/index.html` e `canva/logo-sucesso.png` devem ter precedência quando presentes no artefato publicado.

O workflow de GitHub Pages foi substituído por um único workflow Cloudflare. Não há deploy concorrente pelo GitHub Pages.

## Validação após publicar

Para cada release, conferir:

1. GitHub Actions concluiu com sucesso e usou o SHA esperado.
2. Cloudflare Pages registra deployment `production`, branch `main`, SHA correspondente e etapa `deploy=success`.
3. URL imutável do deployment e domínio customizado servem conteúdo correto.
4. A proposta apresenta título `Proposta Comercial · EDCAR Auto Elétrica e Disk Bateria`, e não o HTML da home.
5. Logo `/canva/logo-sucesso.png` responde como imagem e não como HTML.
6. Home, proposta e demais rotas estáticas existentes continuam funcionais.
7. Domínio customizado e SSL permanecem ativos.

Não alterar DNS para trocar a fonte de deploy: o hostname já está anexado ao projeto Pages. Manter o projeto anterior e deployments anteriores disponíveis para rollback.

## Rollback

Se um deploy regressar o site, reverter o commit na `main`; o workflow publicará automaticamente o estado anterior. Para uma recuperação imediata, selecionar um deployment anterior do projeto Cloudflare Pages, sem remover o projeto nem alterar DNS.
