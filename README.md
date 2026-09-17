# API de Produtos - Node.js com Express

API REST simples desenvolvida para a disciplina de Projeto Integrador VI da faculdade UNIFIO, aplicando arquitetura em camadas com manipulação de dados em memória.

---

## 🛠️ Tecnologias

- **Node.js**
- **Express**
- **Nodemon** (reinicialização automática em ambiente de desenvolvimento)

---

## 📁 Estrutura de Pastas

```text
projeto-integrador-vi/
├── package.json
├── package-lock.json
├── README.md
├── docs/
│   ├── 01-visao.md
│   ├── 02-requisitos.md
│   └── 03-criterios-aceitacao.md
└── src/
    ├── app.js
    ├── app.test.js
    ├── models/
    │   ├── produto.model.js
    │   ├── produto.model.test.js
    │   ├── funcionario.model.js
    │   └── funcionario.model.test.js
    ├── controllers/
    │   ├── produto.controller.js
    │   ├── produto.controller.test.js
    │   ├── funcionario.controller.js
    │   └── funcionario.controller.test.js
    ├── services/
    │   ├── produtos.service.js
    │   ├── produtos.service.test.js
    │   ├── funcionario.service.js
    │   └── funcionario.service.test.js
    └── routes/
        ├── produto.routes.js
        └── funcionario.routes.js

```

### Papel de Cada Camada

- **`models/`**: Define as classes `Produto` e `Funcionario` (estrutura dos dados e regras do domínio).
- **`services/`**: Concentra a regra de negócio, validações e dados em memória.
- **`controllers/`**: Recebe a requisição HTTP, aciona o Service e define status e resposta.
- **`routes/`**: Mapeia as URLs e verbos HTTP para as funções do Controller.
- **`app.js`**: Ponto de entrada que inicializa o servidor Express.
- **Arquivos `*.test.js`**: Testes unitários e de integração de cada camada, usando o test runner nativo do Node (`node:test`).

---

## 🚀 Como Executar o Projeto

1. Instale as dependências:

```bash
   npm install

```

2. Inicie o servidor em modo de desenvolvimento:

```bash
   npm run dev

```

O servidor estará ativo em: `http://localhost:3000`.

---

## ✅ Como Executar os Testes

```bash
npm test
```

Os testes usam o test runner nativo do Node.js (`node --test`), sem dependências externas.

---

## 📡 Rotas da API

| Método | Endpoint            | Descrição                                | Status de Retorno                  |
| ------ | ------------------- | ----------------------------------------- | ----------------------------------- |
| `GET`  | `/produtos`         | Retorna a lista de todos os produtos      | `200 OK`                           |
| `GET`  | `/produtos/:id`     | Busca um produto pelo ID                  | `200 OK` ou `404 Not Found`        |
| `POST` | `/produtos`         | Cadastra um novo produto                  | `201 Created` ou `400 Bad Request` |
| `GET`  | `/funcionarios`     | Retorna a lista de todos os funcionários  | `200 OK`                           |
| `GET`  | `/funcionarios/:id` | Busca um funcionário pelo ID              | `200 OK` ou `404 Not Found`        |
| `POST` | `/funcionarios`     | Cadastra um novo funcionário              | `201 Created` ou `400 Bad Request` |

---

## 🧪 Exemplo de Requisição (POST `/produtos`)

**Corpo da requisição (JSON):**

```json
{
  "nome": "Teclado Mecânico",
  "preco": 250
}
```

**Resposta de sucesso (`201 Created`):**

```json
{
  "id": 3,
  "nome": "Teclado Mecânico",
  "preco": 250
}
```
