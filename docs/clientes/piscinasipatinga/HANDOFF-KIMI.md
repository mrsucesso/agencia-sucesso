# HANDOFF KIMI — Piscinas Ipatinga / Infinity Spa & Pools

## Missão

Construir o MVP de **piscinasipatinga.com.br** para a marca **Infinity Spa & Pools**, com foco em geração de orçamento local em Ipatinga/MG e região.

Prioridades, nesta ordem:
1. clareza comercial;
2. conversão para WhatsApp/orçamento;
3. SEO local;
4. velocidade e qualidade técnica;
5. facilidade de expansão posterior.

Leia primeiro:
- `docs/clientes/piscinasipatinga/README.md`
- `docs/clientes/piscinasipatinga/BRIEFING-E-ARQUITETURA.md`

## Não confundir as marcas

**Marca do site:** Infinity Spa & Pools.  
**Domínio:** piscinasipatinga.com.br.  
**Cristallite:** tratar como marca/operação separada. Não explicar relação societária ou operacional entre as duas sem autorização.

## Dados canônicos

**Infinity Spa & Pools**  
Rua Zita Soares de Oliveira, 24  
Centro — Ipatinga/MG  
CEP 35160-007  
WhatsApp: +55 31 98630-5668

Razão informada: Infinity Spa & Pools Cleber Monteiro Dias LTDA.  
CNPJ: ainda não inserir se não estiver confirmado.

## Stack desejada

Preferência: site estático/moderno compatível com GitHub + Cloudflare Pages.

Você pode escolher Astro, Vite/React ou HTML/CSS/JS bem estruturado, mas:
- evite dependências desnecessárias;
- priorize build rápido;
- gere conteúdo rastreável sem depender de JS para texto crítico;
- mantenha componentes reutilizáveis;
- Lighthouse/Core Web Vitals devem ser prioridade;
- nada de CMS pesado no MVP.

Se criar um repositório próprio, usar preferencialmente:
**mrsucesso/piscinasipatinga-com-br**

Se não houver permissão para criar repo, entregar o pacote pronto e documentar exatamente como transferir.

## Escopo MVP

Construir estas 9 páginas:
1. Home
2. Piscinas de Fibra
3. Spas
4. Equipamentos
5. Produtos para Piscina
6. Soluções em Fibra
7. Projetos
8. Sobre
9. Contato/Orçamento

### Rotas
```
/
/piscinas-de-fibra-ipatinga/
/spas/
/equipamentos/
/produtos-para-piscina/
/solucoes-em-fibra/
/projetos/
/sobre/
/contato/
```

## Home obrigatória

Ordem:
1. Header
2. Hero
3. Categorias
4. Piscinas em destaque
5. Solução completa
6. Projetos reais
7. Aquecimento/equipamentos
8. Soluções em fibra
9. Para empresas
10. Localização
11. FAQ
12. Orçamento
13. Footer

### Hero
H1:
**Piscinas em Ipatinga para sua casa, empresa ou área de lazer**

Subtexto:
**Piscinas de fibra, spas, equipamentos, acessórios e soluções para cuidar da sua piscina em Ipatinga e região.**

CTAs:
- **Quero um orçamento**
- **Ver piscinas**

## Direção visual

Usar a **logo oficial da Infinity Spa & Pools** como fonte primária da identidade.

### Paleta da marca a usar no site
```css
--infinity-turquoise-light: #17A8AD;
--infinity-turquoise:       #278F94;
--infinity-teal-dark:       #247278;
--infinity-blue:            #227EB0;
--infinity-gray:            #73787B;
--infinity-white:           #FFFFFF;
--infinity-bg:              #F4F7F8;
--infinity-text:            #17363A;
```

As cores são aproximações extraídas da logo raster fornecida. Caso apareça SVG/manual oficial, substituir pelos valores oficiais.

### Hierarquia cromática
1. principal: `#278F94`;
2. contraste/áreas escuras: `#247278`;
3. acento: `#17A8AD`;
4. acento secundário: `#227EB0`;
5. neutros: branco, `#F4F7F8`, `#73787B`;
6. texto: `#17363A`.

**Não usar `#00AEEF` ou `#073B5C` como cores principais.** Esses tons pertenciam à hipótese visual preliminar e não correspondem bem à logo recebida.

Gradientes, quando usados, devem seguir a própria assinatura visual da marca: **turquesa → teal escuro**, com moderação.

Sensação:
- contemporâneo;
- limpo;
- comercial;
- leve;
- confiável;
- água/lazer sem estética infantil ou "parque aquático";
- fotos grandes e boa hierarquia editorial.

Evitar:
- aparência de template barato;
- cards demais;
- sombras pesadas;
- excesso de azul saturado;
- ícones genéricos em excesso;
- animações que atrapalhem carregamento;
- linguagem de panfleto;
- visual copiando posts de Instagram.

## Imagens

Até recebermos acervo organizado:
- estruturar placeholders elegantes;
- não apresentar imagem genérica como instalação real da empresa;
- separar claramente "imagem ilustrativa" de "projeto realizado";
- preparar `srcset`, WebP/AVIF quando possível e lazy load;
- preservar proporção e evitar CLS.

## Copy

Tom:
- direto;
- profissional;
- acessível;
- sem clichês;
- sem superlativos não comprovados.

Mensagem central:
**Piscina, equipamentos e tratamento em um só lugar.**

Outra mensagem:
**Não é só a piscina. A Infinity ajuda você a montar a solução completa.**

Evitar:
- "momentos inesquecíveis";
- "mergulho na qualidade";
- "realize seu sonho";
- "a melhor de Ipatinga";
- "preço justo";
- "qualidade incomparável";
- garantias ou prazos não confirmados.

## Conversão

Implementar WhatsApp contextual por página/produto.

Base:
`https://wa.me/5531986305668`

Exemplos:
- página de piscina: "Olá, vi as piscinas no site Piscinas Ipatinga e gostaria de receber um orçamento."
- equipamentos: "Olá, estou vendo a página de equipamentos e gostaria de orientação/orçamento."

Adicionar:
- CTA no header;
- botão flutuante;
- CTA após blocos comerciais;
- formulário curto na página de contato e na Home.

Campos:
- Nome
- WhatsApp
- Cidade
- Interesse
- Mensagem

Preparar atributos/eventos para mensuração futura.

## SEO

### Home
Title:
**Piscinas em Ipatinga MG | Infinity Spa & Pools**

H1:
**Piscinas em Ipatinga para sua casa, empresa ou área de lazer**

Meta description sugerida:
**Infinity Spa & Pools em Ipatinga: piscinas de fibra, spas, equipamentos, aquecimento, acessórios e produtos para tratamento da água. Solicite um orçamento.**

### Obrigatório
- meta title/description únicos;
- canonical;
- Open Graph;
- sitemap.xml;
- robots.txt;
- breadcrumbs;
- schema;
- NAP no footer/contato;
- alt text;
- headings corretos;
- links internos;
- 404;
- favicon;
- manifest se fizer sentido;
- sem conteúdo duplicado.

Schema local deve usar o nome **Infinity Spa & Pools**, endereço de Ipatinga e telefone informado. Não inventar horário, coordenadas, rating ou faixa de preço.

## Acessibilidade e qualidade

- contraste AA;
- foco de teclado visível;
- labels reais nos formulários;
- navegação por teclado;
- `prefers-reduced-motion`;
- sem texto inserido apenas dentro de imagens;
- responsivo de 320px a desktop;
- testar Chrome/Edge/Safari mobile quando possível.

## Performance

Meta de referência em produção/preview:
- Lighthouse Performance >= 90;
- Accessibility >= 95;
- Best Practices >= 95;
- SEO >= 95.

Não sacrificar experiência real para perseguir nota artificial.

## Entrega técnica

Entregar:
- código-fonte completo;
- README com comandos;
- build limpo;
- `.gitignore`;
- sem caminhos locais da máquina/ambiente Kimi;
- sem chaves/tokens;
- sem URLs privadas;
- lista de dependências;
- instruções de deploy Cloudflare Pages;
- lista de pendências;
- checklist de QA;
- commit final identificado.

## QA obrigatório antes de entregar

Validar:
- todas as 9 rotas HTTP 200 no preview;
- menu desktop/mobile;
- WhatsApp com número correto;
- nenhum lorem ipsum;
- nenhum texto sobre Cristallite não aprovado;
- endereço correto;
- nenhuma alegação inventada;
- title/meta/canonical;
- sitemap;
- robots;
- imagens;
- formulário;
- links internos;
- 404;
- console sem erros relevantes;
- build reproduzível.

## Publicação

**NÃO alterar DNS, domínio oficial, Perfil da Empresa no Google ou registros externos.**

Primeiro:
1. gerar build;
2. publicar preview técnico;
3. enviar URL de preview;
4. enviar commit;
5. relatar QA;
6. aguardar aprovação de Mauricio.

## Critério de sucesso

A pessoa que chega procurando "piscinas em Ipatinga" deve entender em poucos segundos:
- que está falando com a Infinity Spa & Pools;
- o que a empresa vende;
- que atende Ipatinga;
- quais categorias pode consultar;
- como pedir orçamento imediatamente.

A arquitetura deve permitir adicionar catálogo, páginas individuais de modelos, projetos, cidades e conteúdo sem reconstruir o site.
