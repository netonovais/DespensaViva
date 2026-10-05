# Despensa Viva — Planejamento

## Backlog mínimo

| ID | Tarefa | Responsável | Prioridade | Fase |
|---|---|---|---|---|
| P01 | Configurar projeto Django | José | Alta | 2 |
| P02 | Configurar banco e migrations | José | Alta | 2 |
| P03 | Autenticação e isolamento por usuário | José | Alta | 2 |
| P04 | Models de categorias/produtos/locais/estoque | José | Alta | 2 |
| P05 | CRUD de produtos | José | Alta | 2 |
| P06 | CRUD de estoque | José | Alta | 2 |
| P07 | Consumo e descarte | José | Alta | 2 |
| P08 | Integração Open Food Facts | José | Alta | 2 |
| P09 | API REST v1 | José | Alta | 2 |
| P10 | Templates e identidade visual | Matheus | Alta | 2 |
| P11 | Busca, filtros e alertas | Matheus | Alta | 2 |
| P12 | Relatório e exportação | Matheus | Alta | 2 |
| P13 | Testes principais | Matheus | Média | 2 |
| P14 | Deploy e HTTPS | José | Alta | 2 |
| P15 | SAST/DAST e correções | José + Matheus | Alta | 2 |
| P16 | Apresentação final | José + Matheus | Alta | 2 |

## Marcos

1. **M1 — Fase 1:** documentação, modelagem, arquitetura, API e planejamento.
2. **M2:** projeto Django inicial, banco, autenticação e models.
3. **M3:** CRUD, estoque, movimentações e interface.
4. **M4:** integração externa, busca, alertas, relatório e API.
5. **M5:** testes, segurança, deploy e documentação final.

## Estratégia de execução

Priorizar o caminho crítico:
`autenticação → models → CRUD → estoque → movimentações → integração → API → relatório → testes → deploy`.

Funcionalidades não essenciais ao requisito mínimo devem ficar fora da primeira versão.

## Riscos

| Risco | Resposta |
|---|---|
| Pouco tempo para implementação | Priorizar requisitos mínimos |
| Integração externa instável | Cadastro manual + timeout |
| Inconsistência entre interface e API | Reutilizar models/regras |
| Erros de autorização | Testar isolamento por usuário |
| Problemas no deploy | Configurar produção antes da etapa final |

## Divisão

**José Neto**
- backend;
- API;
- integração externa;
- infraestrutura;
- segurança.

**Matheus Covre**
- templates;
- interface;
- relatórios;
- testes;
- identidade visual.
