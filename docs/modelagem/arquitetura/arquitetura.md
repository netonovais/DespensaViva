# Despensa Viva — Arquitetura

## Visão

A solução será implementada como um monolito Django modular. A interface web renderiza páginas com Django Templates e Bootstrap. A API REST utiliza os mesmos modelos e regras de negócio. A integração externa é isolada em um módulo próprio.

## Componentes

| Componente | Responsabilidade |
|---|---|
| Django Templates + Bootstrap | Interface web responsiva |
| `accounts` | autenticação, sessão e isolamento por usuário |
| `inventory` | categorias, produtos, locais, itens e movimentações |
| `reports` | consolidação e exportação de relatórios |
| `api` | endpoints REST, autenticação, filtros e paginação |
| `integrations` | comunicação com Open Food Facts |
| PostgreSQL | persistência de produção |
| SQLite | desenvolvimento local |
| Open Food Facts | dados externos de produtos |

## Camadas

1. **Apresentação:** templates, formulários e views Django.
2. **Aplicação/API:** views/API views, serializers e validações.
3. **Domínio/persistência:** models Django e regras relacionadas ao estoque.
4. **Integração:** cliente isolado da Open Food Facts.
5. **Dados:** PostgreSQL em produção.

## Fluxo web

Usuário → Django Templates → Views/Formulários → Models/Regras → Banco.

## Fluxo API

Consumidor → `/api/v1/` → autenticação/autorização → serializers/views → Models/Regras → Banco → JSON.

## Fluxo Open Food Facts

Usuário informa código → `integrations` consulta Open Food Facts → resposta validada → dados usados no cadastro → produto armazenado localmente.

## Decisões

- **Monolito modular:** reduz complexidade para uma equipe pequena e um projeto acadêmico.
- **Banco relacional:** adequado aos relacionamentos entre usuário, produto, estoque e movimentações.
- **Cache local de produto:** reduz dependência da API externa e permite reutilizar informações já consultadas.
- **Isolamento por usuário:** cada consulta e alteração deve considerar o usuário autenticado.
- **REST separado da interface:** permite que terceiros consumam dados sem depender dos templates.

## Requisitos não funcionais relacionados

- páginas comuns: alvo de até 2 s para até 5.000 itens por usuário;
- timeout da API externa: 5 s;
- HTTPS e `DEBUG=False` em produção;
- segredos em variáveis de ambiente;
- limitação de requisições na API;
- interface responsiva.
