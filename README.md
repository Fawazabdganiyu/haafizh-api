# Haafizh Backend (GraphQL API)

## Overview

This is the **backend service** for [Haafizh](https://github.com/your-username/haafizh), a secure, user-friendly application for recording, tracking, and managing personal or shared funds.

The backend is built with **NestJS** and exposes a **GraphQL API** powered by **Apollo Server**. It manages authentication, contacts, transactions, and balance calculations while connecting to a **PostgreSQL** database.

👉 Frontend Repository: [Haafizh (Next.js)](https://github.com/your-username/haafizh)

---

## Features (MVP)

* JWT-based authentication & authorization
* Contact management (add, list, delete)
* Transaction management (record funds given/received/collected)
* Balance calculation per contact
* GraphQL API with type-safe schema

**Planned Enhancements:**

* Multi-currency support
* Exportable reports (CSV, PDF)
* Real-time updates with GraphQL subscriptions
* Asset and item tracking

---

## Tech Stack

* **Backend Framework:** NestJS (TypeScript)
* **API:** GraphQL (Apollo Server, `@nestjs/graphql`)
* **Database:** PostgreSQL + Prisma ORM
* **Authentication:** JWT in GraphQL context
* **Testing:** Jest + Supertest
* **Documentation:** GraphQL Playground + auto-generated schema docs

---

## Installation (Backend)

```bash
# Clone backend repo
git clone https://github.com/your-username/haafizh-api.git
cd haafizh-api

# Install dependencies
npm install

# Setup environment variables
cp .env.example .env

# Run database migrations
npx prisma migrate dev

# Start the development server
npm run start:dev
```

---

## Example GraphQL Schema

```graphql
type User {
  id: ID!
  name: String!
  email: String!
  contacts: [Contact!]!
}

type Contact {
  id: ID!
  name: String!
  balance: Float!
  transactions: [Transaction!]!
}

enum TransactionType {
  GIVEN
  RECEIVED
}

type Transaction {
  id: ID!
  amount: Float!
  type: TransactionType!
  date: String!
  contact: Contact!
}

type Query {
  me: User
  contacts: [Contact!]!
  contact(id: ID!): Contact
}

type Mutation {
  signup(name: String!, email: String!, password: String!): AuthPayload!
  login(email: String!, password: String!): AuthPayload!
  addContact(name: String!): Contact!
  addTransaction(contactId: ID!, amount: Float!, type: TransactionType!): Transaction!
}
```

---

## Roadmap

* [x] Setup NestJS GraphQL backend
* [ ] Configure PostgreSQL + Prisma
* [ ] Implement authentication
* [ ] Contact management resolvers
* [ ] Transaction management resolvers
* [ ] Balance calculation
* [ ] Deployment

---

## License

[MIT](LICENSE)

---

⚡ This backend works hand-in-hand with the [Haafizh frontend](https://github.com/your-username/haafizh) to deliver a complete financial record-keeping experience.
