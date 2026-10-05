# Despensa Viva — Documento de Visão

## 1. Contexto e problema

Famílias e pessoas que moram sozinhas costumam controlar os alimentos de forma informal, sem registro do que existe, onde está guardado ou quando vence. Isso favorece compras repetidas, produtos esquecidos e desperdício por vencimento.

A Despensa Viva propõe uma aplicação web para centralizar o estoque doméstico, permitindo registrar locais de armazenamento, produtos, itens com quantidade e validade, consumo e descarte, além de acompanhar alertas e indicadores.

## 2. Justificativa

A solução busca reduzir o desperdício doméstico e facilitar a organização da despensa por meio de informações centralizadas e consultas rápidas.

A consulta por código de barras à Open Food Facts reduz o trabalho de cadastro quando o produto já está disponível na base externa.

## 3. Objetivos

### Objetivo geral
Desenvolver uma aplicação web que auxilie no controle do estoque e das validades de alimentos domésticos.

### Objetivos específicos
- permitir cadastro e autenticação de usuários;
- isolar os dados de cada usuário;
- cadastrar locais, categorias, produtos e itens de estoque;
- consultar produtos por código de barras;
- registrar consumo e descarte;
- pesquisar e filtrar o estoque;
- apresentar itens vencidos ou próximos do vencimento;
- gerar relatório consolidado;
- disponibilizar API REST própria.

## 4. Público-alvo

- moradores de residências;
- famílias;
- estudantes e pessoas que moram sozinhas;
- pessoas que desejam organizar compras e reduzir desperdício.

## 5. Stakeholders

| Stakeholder | Interesse |
|---|---|
| Morador | Controlar estoque, validade, consumo e descarte |
| Administrador | Gerenciar categorias e manter a aplicação |
| Terceiro consumidor da API | Consultar dados disponibilizados pela API REST |
| Equipe do projeto | Desenvolver, testar e manter a solução |
| Professor/avaliador | Avaliar documentação e implementação conforme a disciplina |

## 6. Escopo

### Dentro do escopo
- autenticação;
- categorias;
- cadastro e manutenção de produtos;
- consulta de produto por código de barras;
- cadastro e manutenção de itens de estoque;
- registro de consumo e descarte;
- busca e filtros;
- alertas de vencimento;
- relatório consolidado;
- API REST própria;
- integração com Open Food Facts;
- interface responsiva.

### Fora do escopo
- leitura de código de barras pela câmera;
- notificações por e-mail ou push;
- compartilhamento de uma despensa entre usuários;
- compra automática de produtos;
- integração com supermercados;
- reconhecimento de produtos por imagem;
- aplicativo mobile nativo.

## 7. Funcionalidades

| ID | Funcionalidade |
|---|---|
| RF01 | Cadastro, login e logout |
| RF03 | Manutenção de categorias |
| RF04 | CRUD de produtos |
| RF05 | Consulta por código de barras/Open Food Facts |
| RF06 | CRUD de itens de estoque |
| RF07 | Consumo e descarte com histórico |
| RF08 | Busca e filtros |
| RF09 | Alertas de itens vencidos e a vencer em até 7 dias |
| RF10 | Relatório consolidado, CSV e impressão |
| RF11 | API REST v1 com autenticação, filtros, paginação e OpenAPI |

## 8. Restrições

- backend em Python/Django;
- banco relacional;
- API REST própria;
- integração com API externa;
- interface responsiva;
- publicação em URL pública na Fase 2;
- segredos mantidos em variáveis de ambiente;
- documentação e fontes dos diagramas versionadas no GitHub.

## 9. Premissas

- o usuário possui acesso à Internet;
- a Open Food Facts pode estar indisponível ocasionalmente;
- nem todos os produtos estarão cadastrados na API externa;
- o cadastro manual permanece disponível;
- o PostgreSQL será utilizado em produção e SQLite pode ser utilizado no desenvolvimento.

## 10. Riscos iniciais

| Risco | Impacto | Mitigação |
|---|---|---|
| Open Food Facts indisponível | Médio | Timeout, tratamento de erro e cadastro manual |
| Produto não encontrado | Médio | Permitir preenchimento manual |
| Vazamento de dados entre usuários | Alto | Filtrar consultas pelo usuário autenticado |
| Crescimento do volume de itens | Médio | Índices e filtros no banco |
| Atraso da implementação | Alto | Priorizar RF01, RF04, RF05, RF06, RF07, RF08, RF09, RF10 e RF11 |

## 11. Critérios de sucesso da Fase 1

- documentação obrigatória disponível;
- diagramas coerentes com os requisitos;
- modelo de dados compatível com os casos de uso;
- API inicial definida;
- integração externa definida;
- arquivos-fonte dos diagramas versionados;
- README permitindo localizar os artefatos.

## 12. Critérios de sucesso da solução

- usuário consegue controlar seu estoque;
- dados de usuários permanecem isolados;
- produtos podem ser enriquecidos por código de barras;
- vencimentos são identificados;
- consumo e descarte deixam histórico;
- relatório consolida o estado da despensa;
- API própria fornece dados selecionados.
