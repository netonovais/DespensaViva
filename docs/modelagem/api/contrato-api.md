# Despensa Viva — Contrato inicial da API REST

## Base

`/api/v1/`

Formato principal: JSON.

Autenticação prevista: token para consumo da API. Endpoints que expõem dados privados devem validar o usuário/contexto autorizado.

## Recursos

| Método | Endpoint | Finalidade |
|---|---|---|
| POST | `/auth/token/` | obter token |
| GET | `/produtos/` | listar produtos |
| GET | `/produtos/{id}/` | consultar produto |
| POST | `/produtos/` | criar produto |
| PUT | `/produtos/{id}/` | atualizar produto |
| DELETE | `/produtos/{id}/` | excluir produto |
| GET | `/estoque/` | listar itens |
| GET | `/estoque/{id}/` | consultar item |
| POST | `/estoque/` | criar item |
| PUT | `/estoque/{id}/` | atualizar item |
| DELETE | `/estoque/{id}/` | excluir item |
| GET | `/movimentacoes/` | consultar histórico |
| POST | `/movimentacoes/` | registrar consumo/descarte |
| GET | `/relatorios/estoque/` | consultar consolidado |

## Filtros

`/estoque/?produto=&categoria=&local=&validade_ate=&page=1&page_size=20`

Filtros previstos:
- produto/nome;
- categoria;
- local;
- validade;
- página;
- tamanho da página.

## Exemplo — GET /produtos/

### Resposta 200

```json
{
  "count": 1,
  "next": null,
  "previous": null,
  "results": [
    {
      "id": 12,
      "nome": "Arroz",
      "marca": "Exemplo",
      "codigo_barras": "7890000000000",
      "categoria": 2
    }
  ]
}
```

## Exemplo — POST /estoque/

```json
{
  "produto": 12,
  "local": 3,
  "quantidade": 5,
  "unidade": "kg",
  "validade": "2026-12-30",
  "preco": 25.90
}
```

### Resposta 201

```json
{
  "id": 41,
  "produto": 12,
  "local": 3,
  "quantidade": 5,
  "unidade": "kg",
  "validade": "2026-12-30",
  "preco": "25.90"
}
```

## Exemplo — movimentação

```json
{
  "item_estoque": 41,
  "tipo": "CONSUMO",
  "quantidade": 1.5,
  "observacao": "Uso doméstico"
}
```

## Códigos HTTP

| Código | Uso |
|---|---|
| 200 | consulta/alteração bem-sucedida |
| 201 | recurso criado |
| 204 | exclusão sem conteúdo |
| 400 | dados inválidos |
| 401 | autenticação ausente ou inválida |
| 403 | acesso não permitido |
| 404 | recurso inexistente |
| 429 | limite de requisições excedido |
| 500 | erro interno |

## Paginação

A resposta de listagem usa `count`, `next`, `previous` e `results`. O tamanho padrão poderá ser 20 registros.

## OpenAPI

Na Fase 2, o contrato poderá ser publicado em Swagger/OpenAPI com `drf-spectacular`.
