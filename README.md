<h1 align='center'>
    JSON Server React Entrega 5A04
</h1>

## Endpoints

A url base da API é https://reactatividade-s5-renatosuguiy.herokuapp.com/

## Rotas que não precisam de autenticação

<h3 align='center'> Cadastro de usuário</h3>

`POST /register - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "renatosuguiy@gmail.com",
  "password": "123456",
  "name": "Renato",
  "age": 31
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InJlbmF0b3N1Z3VpeUBnbWFpbC5jb20iLCJpYXQiOjE2MzUxODgyNDMsImV4cCI6MTYzNTE5MTg0Mywic3ViIjoiMiJ9.2RlYnFu1xmqEEbmJM89YmMI8YFu745cksdgkR5pSDr4",
  "user": {
    "email": "renatosuguiy@gmail.com",
    "name": "Renato",
    "age": 31,
    "id": 2
  }
}
```

<h3 align='center'> Login </h3>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "renatosuguiy@gmail.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InJlbmF0b3N1Z3VpeUBnbWFpbC5jb20iLCJpYXQiOjE2MzUxODk0NTcsImV4cCI6MTYzNTE5MzA1Nywic3ViIjoiMiJ9.ICDyqztTS7PYM8hebNx77LD48US91sMecMSqJQuJ3JM",
  "user": {
    "email": "renatosuguiy@gmail.com",
    "name": "Renato",
    "age": 31,
    "id": 2
  }
}
```

<h3 align='center'> Lista de  amigos </h3>

`GET /friends - FORMATO DA RESPOSTA - STATUS 200`

```JSON
[
  {
    "name": "felipe",
    "age": 31,
    "userId": 2,
    "id": 1
  },
  {
    "name": "Cachorro",
    "age": 31,
    "userId": 2,
    "id": 2
  }
]
```

## Rotas que não precisam de autenticação

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

Após o usuário estar logado, ele deve conseguir acessar os endpoints abaixo:

<h3 align='center'> Adicionar grupos </h3>

`POST /groups - FORMATO DA REQUISIÇÃO`

```JSON
{
	"type": "Animais",
	"name": "Grupo dos Cachorros",
	"description": "Grupo criado para teste"
}
```

Caso dê tudo certo, a resposta será assim:

```json
{
  "type": "Animais",
  "name": "Grupo dos Cachorros",
  "description": "Grupo criado para teste",
  "id": 5
}
```

<h3 align='center'> Adicionar amigo </h3>

`POST /friends - FORMATO DA REQUISIÇÃO`

```json
{
  "name": "Gato",
  "age": 10,
  "userId": 2
}
```

Caso dê tudo certo, a resposta será assim:

`POST /friends - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "name": "Gato",
  "age": 10,
  "userId": 2,
  "id": 4
}
```

<h3 align='center'> Listar Grupos </h3>

`GET /groups - FORMATO DA RESPOSTA - STATUS 200`

```JSON

[
  {
    "type": "Animais",
    "name": "Grupo dos Gatos",
    "description": "Grupo criado para teste",
    "id": 4
  }
]
```
