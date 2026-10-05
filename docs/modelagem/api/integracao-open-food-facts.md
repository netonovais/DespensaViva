# Despensa Viva — Plano de integração Open Food Facts

## Finalidade

A Open Food Facts será utilizada para preencher automaticamente dados de produtos a partir do código de barras informado pelo usuário.

Isso participa de um fluxo real do sistema: consulta → preenchimento do cadastro → confirmação → armazenamento do produto.

## Dados utilizados

Quando disponíveis:
- nome do produto;
- marca;
- código de barras;
- Nutri-Score;
- dados nutricionais.

## Fluxo

1. Usuário informa o código de barras.
2. Aplicação verifica se o produto já está no catálogo local.
3. Se não estiver, módulo `integrations` consulta a Open Food Facts.
4. Resposta é validada.
5. Campos encontrados são apresentados ao usuário.
6. Usuário confirma ou complementa os dados.
7. Produto é salvo localmente.

## Tratamento de falhas

- timeout máximo previsto: 5 segundos;
- erro de conexão: informar indisponibilidade e permitir cadastro manual;
- produto inexistente: informar que não houve resultado;
- resposta incompleta: utilizar apenas campos válidos;
- limite de requisições: tratar a resposta sem interromper o cadastro manual;
- API externa indisponível: catálogo local continua utilizável.

## Cache local

O produto consultado poderá ser armazenado no catálogo local. Isso reduz consultas repetidas e evita que uma falha posterior da API externa impeça o uso dos dados já cadastrados.

## Autenticação

A integração utiliza a API pública da Open Food Facts conforme a documentação vigente. Eventuais credenciais/configurações exigidas pela infraestrutura não devem ser versionadas.

## Referência oficial

Open Food Facts — documentação da API:
https://openfoodfacts.github.io/openfoodfacts-server/api/
