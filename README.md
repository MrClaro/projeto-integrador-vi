# API de Produtos e Funcionários - TypeScript com Express & Sequelize

API REST desenvolvida para a disciplina de Projeto Integrador VI da faculdade UNIFIO, aplicando arquitetura em camadas com inversão de dependência (Repository Pattern), banco de dados relacional via Sequelize + SQLite e suíte de testes automatizados com Jest.

---

## 🛠️ Tecnologias

- **Node.js**
- **TypeScript** (tipagem estática e interfaces)
- **Express** (framework HTTP)
- **Sequelize & SQLite** (ORM para banco de dados relacional)
- **Jest & ts-jest** (testes automatizados com cobertura > 90%)
- **Supertest** (testes de integração das rotas HTTP)
- **TSX** (execução e recarregamento automático em desenvolvimento)

---

## 📁 Estrutura de Pastas

```text
projeto-integrador-vi/
├── package.json
├── package-lock.json
├── tsconfig.json
├── jest.config.js
├── README.md
├── docs/
│   ├── 01-visao.md
│   ├── 02-requisitos.md
│   └── 03-criterios-aceitacao.md
└── src/
    ├── app.ts
    ├── server.ts
    ├── database/
    │   ├── sequelize.ts
    │   └── produto.sequelize-model.ts
    ├── repositories/
    │   ├── produto.repository.ts
    │   └── produto.repository.sequelize.ts
    ├── models/
    │   ├── produto.model.ts
    │   └── funcionario.model.ts
    ├── controllers/
    │   ├── produto.controller.ts
    │   └── funcionario.controller.ts
    ├── services/
    │   ├── produto.service.ts
    │   └── funcionario.service.ts
    ├── routes/
    │   ├── produto.routes.ts
    │   └── funcionario.routes.ts
    └── __tests__/
        ├── produto.model.test.ts
        ├── produto.controller.test.ts
        └── produto.test.ts
```

### Papel de Cada Camada

- **`models/`**: Define as classes de domínio (`Produto`, `Funcionario`) e regras de negócio essenciais.
- **`repositories/`**: Define o contrato via **interface** (`ProdutoRepository`) e a implementação concreta com Sequelize (`ProdutoRepositorySequelize`).
- **`database/`**: Configura a conexão relacional do Sequelize (SQLite) e os modelos de persistência.
- **`services/`**: Concentra as regras de negócio e validações, dependendo da interface do repositório.
- **`controllers/`**: Recebe a requisição HTTP, valida dados de entrada, aciona o Service e formata a resposta HTTP com status adequado.
- **`routes/`**: Mapeia URLs e verbos HTTP (GET, POST, PUT, DELETE) para os métodos do Controller.
- **`app.ts` / `server.ts`**: Configuram o Express, rotas e inicializam a sincronização com o banco de dados.
- **`__tests__/`**: Suíte de testes unitários e de integração utilizando Jest e Supertest.

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

3. Para gerar o build em JavaScript:

```bash
npm run build
```

4. Para iniciar o build gerado:

```bash
npm start
```

---

## ✅ Como Executar os Testes

```bash
npm test
```

Os testes são executados através do **Jest** com **ts-jest**, medindo a taxa de cobertura de código exigida (> 90%):

- `src/__tests__/produto.model.test.ts`: Testes unitários do Model.
- `src/__tests__/produto.controller.test.ts`: Testes unitários do Controller.
- `src/__tests__/produto.test.ts`: Testes de integração do CRUD completo com banco SQLite em memória.

> **Cobertura atual:** 100% em declarações (Statements), ramificações (Branches), funções (Functions) e linhas (Lines).

---

## 📡 Rotas da API

### Módulo de Produtos (CRUD Completo)

| Método   | Endpoint        | Descrição                                | Status de Retorno                  |
| -------- | --------------- | ---------------------------------------- | ---------------------------------- |
| `GET`    | `/produtos`     | Retorna a lista de todos os produtos     | `200 OK`                           |
| `GET`    | `/produtos/:id` | Busca um produto pelo ID                 | `200 OK` ou `404 Not Found`        |
| `POST`   | `/produtos`     | Cadastra um novo produto                 | `201 Created` ou `400 Bad Request` |
| `PUT`    | `/produtos/:id` | Atualiza dados (nome/preço) de um produto| `200 OK`, `400` ou `404`           |
| `DELETE` | `/produtos/:id` | Remove um produto pelo ID                | `204 No Content` ou `404 Not Found`|

### Módulo de Funcionários

| Método   | Endpoint            | Descrição                               | Status de Retorno                  |
| -------- | ------------------- | --------------------------------------- | ---------------------------------- |
| `GET`    | `/funcionarios`     | Retorna a lista de todos os funcionários| `200 OK`                           |
| `GET`    | `/funcionarios/:id` | Busca um funcionário pelo ID             | `200 OK` ou `404 Not Found`        |
| `POST`   | `/funcionarios`     | Cadastra um novo funcionário             | `201 Created` ou `400 Bad Request` |

---

## 🧪 Exemplos de Requisição

### Criar Produto (`POST /produtos`)
```json
{
  "nome": "Monitor Gamer 144Hz",
  "preco": 1200
}
```

### Atualizar Produto (`PUT /produtos/1`)
```json
{
  "preco": 1050
}
```
