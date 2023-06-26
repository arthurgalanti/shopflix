<p align="center">
  <img alt="logo" src="shopflix.png" /> 
</p>

# Overview

This shopping list application aims to provide an easy and efficient solution for managing personal shopping lists. The application will be developed using .NET for the back-end, React for the front-end, Flutter for mobile, and SQL Server as database. The project will be split into several parts to facilitate collaboration and development.

# Architecture

The application's architecture will be divided into three main layers:

- **Back-end (API):** Developed using .NET, it will be responsible for managing business logic, processing requests, and interacting with the database.
- **Front-end (Web):** Developed with React, it will provide a responsive and appealing user interface for users to interact with the application.
- **Mobile**: Developed with Flutter, it will enable access to the application through mobile devices (Android and iOS).

# Requirements

## Back-end (.NET)

- Implement a RESTful API to manage business logic and interact with database.
- Use the repository pattern to abstract the interaction with the database.
- Implement authentication and authorization using JWT (JSON Web Tokens).
- Implement data validation and error handling.
- Provide endpoints for:
  - CRUD operations for users (registration and login).
  - CRUD operations for shopping list items (creation, update, deletion, and complete).

## Front-end (React)

- Create a responsive and appealing user interface using React and a CSS framework (like [Bootstrap](https://getbootstrap.com/docs/5.3/getting-started/introduction/), [Tailwind CSS](https://tailwindcss.com/docs/installation), [Foundation](https://get.foundation/develop/getting-started.html)).
- Implement proper navigation and routing.
- Integrate the API to perform back-end operations.
- Implement authentication and authorization.
- Implement forms for:
  - User registration and login.
  - Creation, delete and complete of shopping list items.

## Mobile (Flutter)

- Develop a mobile application compatible with Android and iOS using Flutter.
- Create an intuitive and responsive user interface.
- Implement proper navigation and routing.
- Integrate .NET API to perform back-end operations.
- Implement authentication and authorization.
- Implement screens for:
  - User registration and login.
  - Creation, delete and complete of shopping list items.

## Database (Mongo DB)

- Use Mongo DB as a non relational database.
- Define data schemas and models for users and shopping list items.

# Final challenge: Dockerization

Docker is a platform that allows developers to create, deploy, and run applications in containers. Containers package up an application with everything it needs to run consistently across various environments. Dockerizing the shopping list application will involve creating Dockerfiles for each component (back-end, front-end, and database) and a Docker Compose file to manage multi-container deployment.

# Data structure

## In database

Required fields are marked with an asterisk (\*).

### User

| Type     | Field        |
| -------- | ------------ |
| UUID     | Id \*        |
| String   | Name \*      |
| String   | Email \*     |
| String   | Password \*  |
| DateTime | CreatedAt \* |

### Item

| Type     | Field          |
| -------- | -------------- |
| UUID     | Id \*          |
| UUID     | UserId \*      |
| String   | Description \* |
| Decimal  | Quantity \*    |
| Boolean  | IsPurchased \* |
| DateTime | CreatedAt \*   |
| DateTime | PurchasedAt    |
| String   | Image          |

## Endpoints

### User

#### Register (POST) - /users/register

```jsonc
// Request
{
  "name": "string",
  "email": "string",
  "password": "string"
}

// Response
{
    "token": "string",
    "user": {
        "id": "string",
        "name": "string",
        "email": "string",
        "createdAt": "string"
    }
}
```

#### Login (POST) - /users/login

```jsonc
// Request
{
  "email": "string",
  "password": "string"
}
// Response
{
    "token": "string",
    "user": {
        "id": "string",
        "name": "string",
        "email": "string",
        "createdAt": "string"
    }
}
```

### Item

#### Create (POST) - /items

```jsonc
// Header
Authorization: Bearer <token>

// Request
{
  "description": "string",
  "quantity": 0.0,
  "image": "string"
}

// Response
{
    "id": "string",
    "userId": "string",
    "description": "string",
    "quantity": 0.0,
    "isPurchased": false,
    "createdAt": "string",
    "purchasedAt": "null",
    "image": "string"
}
```

#### Get my all items (GET) - /items

```jsonc
// Header
Authorization: Bearer <token>

// Response
[
    {
        "id": "string",
        "userId": "string",
        "description": "string",
        "quantity": 0.0,
        "isPurchased": false,
        "createdAt": "string",
        "purchasedAt": "null",
        "image": "string"
    }
]
```

#### Purchase (POST) - /items/purchase

```jsonc
// Header
Authorization: Bearer <token>

// Request
{
  "id": "string"
}

// Response
{
    "id": "string",
    "userId": "string",
    "description": "string",
    "quantity": 0.0,
    "isPurchased": true,
    "createdAt": "string",
    "purchasedAt": "string",
    "image": "string"
}
```

#### Delete (DELETE) - /items/{id}

```jsonc
// Header
Authorization: Bearer <token>
```

# Participants
- [Alexandre Beato](https://github.com/alexandrebeato/)
- [Arthur Dias](https://github.com/arthurferro)
- [Arthur Galanti](https://github.com/arthurgalanti)
- [Ítalo Covas](https://github.com/ItaloCovas)
- [Vinicius Victor](https://github.com/vinevictor)

# Contributing

If you find a bug or have a feature request, please open an issue on GitHub. Pull requests are also welcome!

# License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
