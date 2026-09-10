# Formulário de orçamento

## Estado atual

Página pública:

```text
https://agencia.sucesso.com.br/formsites/
```

O formulário pertence à nova Agência do Sucesso e envia os dados para:

```text
https://api.sucesso.com.br/api/form-sites
```

A API é servida pelo container `api-formularios` na porta interna `3001`, por meio do Cloudflare Tunnel `api-sucesso-net-br`.

O hostname legado `api.sucesso.net.br` continua preservado e não é usado pelo formulário novo.

## Notificação por e-mail

Cada solicitação é enviada para:

- Destinatário: `contato@sucesso.com.br`;
- Cópia: `mauricio@sucesso.com.br`;
- Cópia: `atendimento@sucesso.com.br`.

O envio usa o `gog gmail send` com o corpo recebido via stdin (`--body-file=-`). O binário e a configuração do `gog` estão disponíveis no container de formulários.

## Campos

O frontend converte os nomes visuais para os nomes esperados pela API:

- `nome` → `nome_completo`;
- `objetivo` → `objetivo_principal`;
- `publico` → `publico_alvo`;
- `orcamento` → `faixa_investimento`.

Os demais campos são preservados, incluindo contato, domínio, identidade visual, infraestrutura, prazo, referências, funcionalidades, redes sociais e arquivos informados.

## WhatsApp

A opção alternativa de atendimento pelo WhatsApp foi removida do formulário:

- removido o bloco “Prefere responder pelo WhatsApp?”;
- removido o botão “Quero fazer pelo WhatsApp”;
- removido o botão de WhatsApp do rodapé.

O campo de telefone/WhatsApp permanece apenas como dado de contato do orçamento.

## Correções realizadas

- Corrigido o endpoint frontend, que apontava para `/form-sites` no hostname legado;
- Corrigido o caminho para `/api/form-sites`;
- Criado `api.sucesso.com.br` para a API de formulários;
- Criado ingress do túnel para `localhost:3001`;
- Corrigido o serviço `cloudflared-api-sucesso-net-br` para funcionar como serviço de usuário;
- Corrigido o parâmetro incompatível do `gog` (`--body-stdin` → `--body-file=-`);
- Corrigido o mapeamento de nomes de campos;
- Atualizado o destinatário e as cópias.

## Teste real validado

Foi enviado um formulário sintético completo, autorizado pelo responsável, com todos os campos preenchidos.

Resultado confirmado:

```text
HTTP 200
Form web processado
Email enviado com sucesso!
```

O registro também foi lido de volta no arquivo de dados da API e todos os campos foram confirmados.

Não usar dados reais em testes futuros. Para validar o envio, usar e-mail, domínio e conteúdo sintéticos.
