<h1 align='center'>
    JSON Server React Entrega 5A04
</h1>

## Endpoints

A url base da API é https://api-hamburgueria-rsuguiy.herokuapp.com/

## Rotas que não precisam de autenticação

<h3 align='center'> Cadastro de usuário</h3>

`POST /register - FORMATO DA REQUISIÇÃO`

```json
{
  "name": "Renato",
  "email": "renatosuguiy@gmail.com",
  "password": "123456",
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
    "id": 2
  }
}
```

<h3 align='center'> Lista de Produtos </h3>

`GET /products - FORMATO DA RESPOSTA - STATUS 200`

```JSON
[
 [
  {
    "id": 1,
    "productName": "Hamburguer",
    "type": "Sanduíche",
    "price": 14,
    "image": "https://bobs.com.br/media/menu/sanduiches/big-bob/Big_Bobs.png.0x180_q85_upscale.png"
  },
  {
    "id": 2,
    "productName": "X-Burguer",
    "type": "Sanduíche",
    "price": 16,
    "image": "https://bobs.com.br/media/menu/sanduiches/double-cheesburguer/Double_cheese_8z6EedM.png"
  }
]
```

## Rotas que precisam de autenticação

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

Após o usuário estar logado, ele deve conseguir acessar os endpoints abaixo:

<h3 align='center'> Adicionar pedido </h3>

`POST /order - FORMATO DA REQUISIÇÃO`

```JSON
 {
    "order": [
      {
        "productId": 1,
        "productName": "Hamburguer",
        "type": "Sanduíche",
        "price": 14,
        "image": "https://bobs.com.br/media/menu/sanduiches/big-bob/Big_Bobs.png.0x180_q85_upscale.png",
        "qtd": 1
      },
      {
        "productId": 2,
        "productName": "X-Burguer",
        "type": "Sanduíche",
        "price": 16,
        "image": "https://bobs.com.br/media/menu/sanduiches/double-cheesburguer/Double_cheese_8z6EedM.png",
        "qtd": 1
      },
    ],
    "userId": 2,
  }
```

Caso dê tudo certo, a resposta será assim:

```json
 {
    "order": [
      {
        "productId": 1,
        "productName": "Hamburguer",
        "type": "Sanduíche",
        "price": 14,
        "image": "https://bobs.com.br/media/menu/sanduiches/big-bob/Big_Bobs.png.0x180_q85_upscale.png",
        "qtd": 1
      },
      {
        "productId": 2,
        "productName": "X-Burguer",
        "type": "Sanduíche",
        "price": 16,
        "image": "https://bobs.com.br/media/menu/sanduiches/double-cheesburguer/Double_cheese_8z6EedM.png",
        "qtd": 1
      },
    ],
    "userId": 2,
    id: 2
  }
```

<h3 align='center'> Ver pedidos </h3>

`GET /order - FORMATO DA REQUISIÇÃO`

```json
[{
    "order": [
      {
        "productId": 1,
        "productName": "Hamburguer",
        "type": "Sanduíche",
        "price": 14,
        "image": "https://bobs.com.br/media/menu/sanduiches/big-bob/Big_Bobs.png.0x180_q85_upscale.png",
        "qtd": 1
      },
      {
        "productId": 2,
        "productName": "X-Burguer",
        "type": "Sanduíche",
        "price": 16,
        "image": "https://bobs.com.br/media/menu/sanduiches/double-cheesburguer/Double_cheese_8z6EedM.png",
        "qtd": 1
      }
    ],
    "userId": 2,
    "id": 2
  },
  {
    "order": [
      {
        "productId": 1,
        "productName": "Hamburguer",
        "type": "Sanduíche",
        "price": 14,
        "image": "https://bobs.com.br/media/menu/sanduiches/big-bob/Big_Bobs.png.0x180_q85_upscale.png",
        "qtd": 1
      },
      {
        "productId": 2,
        "productName": "X-Burguer",
        "type": "Sanduíche",
        "price": 16,
        "image": "https://bobs.com.br/media/menu/sanduiches/double-cheesburguer/Double_cheese_8z6EedM.png",
        "qtd": 1
      }
    ],
    "userId": 2,
    "id": 3
  }
]
```
Para ver os pedidos de um usuário, user o endpoint:

`GET /users/{userId}?_embed=order - FORMATO DA RESPOSTA - STATUS 200`

Caso dê tudo certo, a resposta será assim:

```json
{
  "email": "renatosuguiy@gmail.com",
  "password": "$2a$10$xOt1taGsSYf9jydVtu0ofe5ivSfm0ARgV85HtluYgIb4xuTklj/Jq",
  "name": "Renato Tateiwa Suguiy",
  "confirmPassword": "123456",
  "id": 2,
  "order": [
    {
      "order": [
        {
          "productId": 1,
          "productName": "Hamburguer",
          "type": "Sanduíche",
          "price": 14,
          "image": "https://bobs.com.br/media/menu/sanduiches/big-bob/Big_Bobs.png.0x180_q85_upscale.png",
          "qtd": 1
        },
        {
          "productId": 2,
          "productName": "X-Burguer",
          "type": "Sanduíche",
          "price": 16,
          "image": "https://bobs.com.br/media/menu/sanduiches/double-cheesburguer/Double_cheese_8z6EedM.png",
          "qtd": 1
        }
      ],
      "userId": 2,
      "id": 2
    },
    {
      "order": [
        {
          "productId": 1,
          "productName": "Hamburguer",
          "type": "Sanduíche",
          "price": 14,
          "image": "https://bobs.com.br/media/menu/sanduiches/big-bob/Big_Bobs.png.0x180_q85_upscale.png",
          "qtd": 1
        },
        {
          "productId": 2,
          "productName": "X-Burguer",
          "type": "Sanduíche",
          "price": 16,
          "image": "https://bobs.com.br/media/menu/sanduiches/double-cheesburguer/Double_cheese_8z6EedM.png",
          "qtd": 1
        }
      ],
      "userId": 2,
      "id": 3
    }
  ]
}
```
