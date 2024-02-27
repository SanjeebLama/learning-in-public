# [GraphQL](https://graphql.org/learn/)

> a Query Language for your APIs

- and a runtime for fulfilling those queries with your existing data.
- GraphQL provides a complete and understandable description of the data in your API,
- gives clients the power to ask for exactly what they need and nothing more,
- makes it easier to evolve APIs over time, and enables powerful developer tools.
- single endpoint

### A simple CRUD (Create, Read, Update, Delete) example using GraphQL:

1. **Schema Definition**:

```graphql
type Book {
  id: ID!
  title: String!
  author: String!
}

type Query {
  books: [Book!]!
  book(id: ID!): Book
}

input BookInput {
  title: String!
  author: String!
}

type Mutation {
  createBook(input: BookInput!): Book!
  updateBook(id: ID!, input: BookInput!): Book!
  deleteBook(id: ID!): Book!
}
```

2. **Resolver Functions** (assuming you're using some GraphQL server implementation like Apollo Server or GraphQL Yoga):

```javascript
const books = [
  { id: "1", title: "The Great Gatsby", author: "F. Scott Fitzgerald" },
  { id: "2", title: "To Kill a Mockingbird", author: "Harper Lee" },
];

const resolvers = {
  Query: {
    books: () => books,
    book: (_, { id }) => books.find((book) => book.id === id),
  },
  Mutation: {
    createBook: (_, { input }) => {
      const newBook = { id: String(books.length + 1), ...input };
      books.push(newBook);
      return newBook;
    },
    updateBook: (_, { id, input }) => {
      const index = books.findIndex((book) => book.id === id);
      if (index === -1) throw new Error("Book not found");
      books[index] = { ...books[index], ...input };
      return books[index];
    },
    deleteBook: (_, { id }) => {
      const index = books.findIndex((book) => book.id === id);
      if (index === -1) throw new Error("Book not found");
      const deletedBook = books.splice(index, 1);
      return deletedBook[0];
    },
  },
};

module.exports = resolvers;
```

3. **Example Queries/Mutations**:

- Query all books:

```graphql
query {
  books {
    id
    title
    author
  }
}
```

- Query a single book by ID:

```graphql
query {
  book(id: "1") {
    id
    title
    author
  }
}
```

- Create a new book:

```graphql
mutation {
  createBook(input: { title: "1984", author: "George Orwell" }) {
    id
    title
    author
  }
}
```

- Update a book:

```graphql
mutation {
  updateBook(
    id: "1"
    input: { title: "The Great Gatsby", author: "F. Scott Fitzgerald" }
  ) {
    id
    title
    author
  }
}
```

- Delete a book:

```graphql
mutation {
  deleteBook(id: "1") {
    id
    title
    author
  }
}
```

This example demonstrates basic CRUD operations using GraphQL.

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/44397e62-b1b6-4d25-97b3-79c74c858acd)

### Rest API drawbacks:

1. Ovefetching
2. Underfetching

# resources"

- [GraphQL Course for Beginners](https://www.youtube.com/watch?v=5199E50O7SI)
