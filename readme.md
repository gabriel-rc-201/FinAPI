# FinAPI

Essa é uma API de uma aplicação financeira.

Esse é o primeiro projeto desenvolvido no curso do Ignite.

Nela nós podemos criar, deletar e editar uma conta com a rota `"/account"`.

```js
app.get("/account");
app.post("/account");
app.put("/account");
app.delete("/account");
```

Podemos realizar depósitos (`app.post("/deposit")`) e saques `app.post("/withdraw")`.

Tambem podemos ver o saldo da conta com a rota: `app.get("/balance")`.

Por fim tambem podemos ver as movimentações finaceiras que foram realizadas na conta com as rotas `app.get("/statement")` para ver todas as movimentações na conta e `app.get("/statement/date")` para as movimentações em um dia específico.

Todas as rotas, com exceção para a criação de conta, passam por um middleware que verificam qual usuário está usando o sistema.

A rota `app.get("/statement/date")` recebe o parametro `date` como query params no formato `aaaa-mm-dd`.

As demais rotas recebem dados através do `body` com entradas de dados do tipo `json`

Para a **criação de usuário** a rota (`app.post("/account");`) recebe como parametro o CPF e o nome da pessoa.

```json
{
  "cpf": "33333333333",
  "name": "Nome do Ser Humano"
}
```

A unica **modificação** que se pode fazer na conta é no nome do usuário (rota: `app.put("/account");`)

```json
{
  "name": "Novo Nome"
}
```

A entrada para fazer um **depósito** o usuário deve fornecer uma `description` e o `amount` (rota: `app.post("/deposit")`)

```json
{
  "description": "winer's deposit",
  "amount": 3500.0
}
```

Para o **saque** basta fornecer o `amount` (rota: `app.post("/withdraw")`)

```json
{
  "amount": 2000
}
```
