
# Riqra Challenge: Full-Stack JavaScript Developers

Welcome to our challenge, it means a lot to us, you already passed the interview process and we are closer to start working as a team.

### Make sure you...

1. Create a public repository and do your best.
2. Do not build extra features.
3. Use the tools mentioned below.
4. Deploy your solution.
4. Send the repository and deploy urls via email.

![ninja developer](https://i0.wp.com/people.collabora.co.uk/~mbatle/images/Ninja-pounce.jpg)

## About it

The challenge is a basic shopping cart, it allows you to search, add, update and remove products.

Once you have all you need in your shopping cart you can complete the order and visit the thank you page.

You can see the [prototype](https://www.figma.com/proto/C1cHqoUvqWQaXmZSVKW3tA/Riqra-Challenge?node-id=0%3A3&viewport=-1360%2C66%2C0.5&scaling=min-zoom) and the [design inspector](https://www.figma.com/file/C1cHqoUvqWQaXmZSVKW3tA/Riqra-Challenge?node-id=0%3A1)

You will have to signup in Figma in order to use inspector.

## Screens

### Empty cart

At the beginning the cart is empty, the pricing panel is set to zero, the delivery date is calculated (see the **rules** section to know how to calculate it) and the complete order button is disabled.

The search box lets you find products.

![Empty Cart](https://user-images.githubusercontent.com/5007653/64066196-82d8ca00-cbdc-11e9-8315-cc8c0a7a4ba0.png)

### Cart with search results

When you type the name of a product, the matched results will appear in the cart panel.

The cart panel shows the results when the search box is not empty, otherwise, it shows the products already added to the cart.

From this view you can add the product using the counter component (see **rules** section).


![Cart with Search Results](https://user-images.githubusercontent.com/5007653/64066195-82403380-cbdc-11e9-88bb-6638c1c161de.png)

### Cart with products

Here you can see the products added to our cart, the pricing panel updated and the complete order button enabled (see **rules** section to know when to enable the button).

Remember that you can only access the cart products if the searchbox is empty.

![Cart with Products](https://user-images.githubusercontent.com/5007653/64066194-82403380-cbdc-11e9-8927-0cc5c83fd58a.png)

### Thank you 

Once you complete the order you visit this page, it displays the order code and gives you a link to continue shopping.

![Thank you](https://user-images.githubusercontent.com/5007653/64066197-82d8ca00-cbdc-11e9-8fdc-1dd5f7831915.png)

## Tools

### Frontend

1. Use [create-react-app](https://github.com/facebook/create-react-app) to setup the project.
2. Use [styled-components](https://github.com/styled-components/styled-components) to style the components.
3. Use [apollo-client](https://github.com/apollographql/apollo-client) to communicate with the backend and state management.
4. Use [reach-router](https://github.com/reach/router) as the router.

### Backend

1. Use [graphql-js](https://github.com/graphql/graphql-js) to build the api
2. Use MySQL as database and [sequelize](https://github.com/sequelize/sequelize) as ORM to handle operations.
3. Use [express](https://github.com/expressjs/express) as server.

### Deploy

1. Use [Heroku](https://www.heroku.com/) as plataform to deploy.
2. Use [JawsDB](https://elements.heroku.com/addons/jawsdb) as the addon to deploy your MySQL database.

## Resources

1. [How to GraphQL](https://www.howtographql.com/)
2. [Beginner GraphQL Series](https://www.youtube.com/watch?v=DyvsMKsEsyE&list=PLN3n1USn4xln0j_NN9k4j5hS1thsGibKi)
3. [Learn Sequelize](https://www.youtube.com/watch?v=pxo7L5nd1gA)

## Rules

### Delivery date

The company delivers in 24 hours from Monday to Friday. Take this rule into account while calculating the delivery date.  

For example:

A person buying on Friday, Saturday or Sunday will see Monday as the delivery date instead of Saturday.
A person buying on Monday will see Tuesday as the delivery date.

![image](https://user-images.githubusercontent.com/5007653/64048283-edcfc580-cb36-11e9-809f-69046a3ec853.png)

### Pricing

The shipping cost is always 10% of the products cost. 
Taxes are 18% of the products cost.
Product prices have taxes included.

Example:

if all products cost $100 the shipping cost will be $10 while taxes is $18 and the final price $110.

The shipping cost line must highlighted.

![image](https://user-images.githubusercontent.com/5007653/64048346-1061de80-cb37-11e9-9112-db5b23fdccdb.png)

### Complete order button

The complete order button is only enabled and has an orange color if the total price is equal or greather than $50, otherwise, the button is disabled and the order cannot be completed.

![image](https://user-images.githubusercontent.com/5007653/64048318-fb854b00-cb36-11e9-904d-23286f3662c2.png)

### Shopping cart products

A shopping cart product can be removed by clicking on the delete button.

![image](https://user-images.githubusercontent.com/5007653/64048275-e6a8b780-cb36-11e9-901a-48537eba9b2a.png)

### The Product and Counter components

> Check the behaviour in [here](http://truck-master.surge.sh/iframe.html?id=product-mobile--with-stock-limit)

The counter component will dull the product component if opened and show two knowbs to decrease and increase the product quantity while the number in the middle gets updated as well as the pricing panel.

![image](https://user-images.githubusercontent.com/5007653/64048401-3edfb980-cb37-11e9-9325-2ae758bbbf5c.png)

### Empty cart

If the cart has no products and the search box is empty, an empty cart state is shown.

![image](https://user-images.githubusercontent.com/5007653/64048422-54ed7a00-cb37-11e9-8ede-d633477e5368.png)

### The Order code

The order code should be incremental, and must have 5 characters including the `P`.

example: for the first order the code will be `P0001` for the order 20 the code should be`P0020`.

![image](https://user-images.githubusercontent.com/5007653/64048530-97af5200-cb37-11e9-8ce7-4301d011f45f.png)
