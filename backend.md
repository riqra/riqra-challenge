# Backend Developer

The challenge is to build a GraphQL API with a tiny set of the features we currently have in production.

Basically a user should be able to login or signup, and start adding products to its shopping cart to finally make a purchase and receive an email notification with a summary.

With this in mind lets take a look at what you need to build.

All the steps from signing up to making the purchase must be tested using a tool like [graphiql](https://github.com/graphql/graphiql) or [graphql-playground](https://github.com/prisma/graphql-playground).

## Requirements

### Auth

In order for a user to purchase in our store, it must be logged in first, but some of them don't have an account yet, so must allow that too.

#### Login

Generate a mutation to login the user using its email and password.

- When the email does not exist the API must say 'User not found '
- When the password is incorrect the API must respond 'Oops! incorrect password'.
- When the email and password are correct a new token should be generated, take into account that this token will have to be sent to all further requests (product, cart and order operations).

#### Signup

Generate a mutation that receives an email and password as parameters.

- The email has to be unique in the database.
- If the email already exists the API must say 'User already exists'.
- The password must be contain more than 6 characters.
- Once the user is created a new token must be generated to be used in further requests.

### Products

The product must have a few required properties: id, name, image, brand and price.

Once the user is logged in, it is able to create its own products.

> Users don't share products.

- When a product is created, updated or removed, it must be synchronized to [Algolia](https://algolia.com) for search operations by its name and brand fields.
- The name must not be longer than 35 characters.
- The product must be related to a brand (send the brand id).
- The image sent to the mutation must be uploaded to [Cloudinary](https://cloudinary.com).

### Search

Create a search query in the schema that receives a term, page and limit parameters using Algolia in the resolver.

- The term can be the product's name or brand.
- When the term is empty, the query returns all the entries.
- Limit and page parameters are used for pagination.

> Remember that all search operations must use Algolia, do not hit the database for this.

### Cart

Now is time to start rolling our cart and filling it with all we need.

Cart properties: total, tax, subtotal

Create mutations to add, update and remove a product in a cart passing the productId as part of the parameters and a quantity when needed.

- A Cart cannot have duplicated products.
- Every time a user operates in the cart, the API must recalculate the total, tax and subtotal prices.

### Order

Once we have all the products we want in our cart, we have to convert our cart to an actual Order.

Order properties: code, total, tax, subtotal.

Create a mutation called `createOrder` and convert the user's cart into an actual order and generate a code for it.

- The order code should be incremental, and must have 5 characters including the P.  
example: for the first order the code will be P0001 for the order 20 the code should be P0020.
- An email should be sent to the user once the order is created.
