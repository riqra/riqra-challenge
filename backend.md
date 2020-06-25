# Backend Developer

The assignment is designed to check your coding and problem-solving skills. It is intentionally made too big. We suggest you spend a maximum of 4-5 hours on it, therefore you need to decide which parts of the system you will code and which you will mock. For example, we are more interested in Architecture and Domain model design than in Database setup or resolver implementations.

What we evaluate in the code:

- Domain model design (usage of DDD concepts: aggregates, value objects, domain services, etc)
- Messaging (Commands and Events)
- Code organization (modularity, dependencies between modules, etc)
- Exception handling and logging
- Writing and organizing tests
- Task-based asynchronous programming

The challenge is to build a GraphQL API with a tiny set of the features we currently have in production.

Basically a user should be able to login or signup, and start adding products to its shopping cart to finally make a purchase and receive an email notification with a summary.

All the steps from signing up to making the purchase will be tested by us using a tool like [graphiql](https://github.com/graphql/graphiql) or [graphql-playground](https://github.com/prisma/graphql-playground).

No UI needed.

## Requirements

### Auth

In order for a user to purchase in our store, it must be logged in first.

#### Login

Generate a mutation to login the user using its email and password.

- When the email does not exist the API must say 'User not found '
- When the password is incorrect the API must respond 'Oops! incorrect password'.
- When the email and password are correct a new token must be generated for further requests.

but some of them don't have an account yet.
 
#### Signup

Generate a mutation that receives an email and password as parameters.

- The email has to be unique in the database.
- If the email already exists the API must say 'User already exists'.
- The password must be longer than 6 characters.
- Once the user is created a new token must be generated for further requests.

### Products

Product properties: id, name, image, brand and price.

A logged in user is able to create its own products.

> Users don't share products.

- When a product is created, updated or removed, it must be synchronized to [Algolia](https://algolia.com) for search operations.
- The name must not be longer than 35 characters.
- The image sent to the mutation must be uploaded to [Cloudinary](https://cloudinary.com).

### Search

Create a search query in the schema that receives a term, page and limit parameters using Algolia in the resolver.

Since users do not share products, they cannot find others products while searching.

- The term can be the product's name or brand.
- When the term is empty, the query returns all the entries.
- Limit and page parameters are used for pagination.

> Remember that all search operations must use Algolia, do not hit the database for this.

### Cart

Now is time to start filling our cart with all products we need.

Cart properties: total, tax, subtotal

Create mutations to add, update and remove a product in a cart passing the productId as part of the parameters and a quantity when needed.

- A Cart cannot have duplicated products.
- Every time a user operates in the cart, the API must recalculate the total, tax and subtotal prices.

> Taxes are 18% of the total price.

### Order

Order properties: code, total, tax, subtotal.

Create a mutation to convert the user's cart into an actual order and generate a code for it.

- The order code should be incremental, and must have 5 characters including the P. For the first order the code will be P0001 for the order 20 the code should be P0020. The code is not shared between users, there can 2 users with the same order code.
- An email should be sent to the user once the order is created.
- The user must be able to list all its orders.

## Tools

### Backend

1. Use [graphql-js](https://github.com/graphql/graphql-js) to build the api
1. Use Typescript for the code.
1. Use MySQL as database and [sequelize](https://github.com/sequelize/sequelize) as ORM to handle operations.
1. Use [express](https://github.com/expressjs/express) as server.

### Deploy

1. Use [Heroku](https://www.heroku.com/) as plataform to deploy.
2. Use [JawsDB](https://elements.heroku.com/addons/jawsdb) as the addon to deploy your MySQL database.

## Resources

1. [How to GraphQL](https://www.howtographql.com/)
2. [Beginner GraphQL Series](https://www.youtube.com/watch?v=DyvsMKsEsyE&list=PLN3n1USn4xln0j_NN9k4j5hS1thsGibKi)
3. [Learn Sequelize](https://www.youtube.com/watch?v=pxo7L5nd1gA)
