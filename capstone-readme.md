# Capstone Project: Create an "Order Tracking" application

## Teams

### Engineers

| Front-end       | Back-end       | Database       | DevSecOps        |
|-----------------|----------------|----------------|------------------|

### Analysts

| Front-end        | Back-end         | Database         | DevSecOps         |
|------------------|------------------|------------------|-------------------|
| |  |  |  |

Adesina Adeniran
Anushca-Mai Dunkley
Calvin Graves
Chardana Martin
Crystal Lobo
Ian Botelho
Joseph Calderon
Julia Pyun
Karanpreet Tatla
Kayla Shah
Marina Mincheva
Michael Lawson-Adesanya
Moises Naldo
Riwa Kulkarni           
Sophia Datsko
Taryn Bennett
Tatiana Jean-Louis
## Application description

We have some customers that still prefer using our paper catalog. TJX sends them said catalog with a phone number they can call. The phone number connects customers to our Customer Service Reps (CSRs). The CSRs need an application that lets them manage customers and their orders.

What should our CSRs be able to do?

- Log in / Log out
- For any Customer
  - Find an existing customer
  - Enter a new customer into the system
  - Edit a customer's details
  - Close a customer's account
- For any Order
  - Find an existing order
  - Enter a new order into the system
  - Modify an existing order
    - Add/remove/edit products
  - Check order status
- For any Product
  - Search products
  - See product details (photo, price, inventory?)
  - Add a product to an order
  - Notify when a product is part of an order

### Order lifecycle

- All interactions
  - Customer calls in, CSR answers
  - CSR adds Customer if they do not exist
  - CSR edits/updates Customer as needed

- New Order
  - CSR creates an Order
  - Add Product(s)
    - Check if available
    - Add to the Order if so
  - More products, save the order, or ship the order?
    - Update order status accordingly

- Modify existing order
  - Customer asks about order
    - Find by customer
    - Find by order number
  - Customer makes changes to order
    - Can the order be modified (e.g., it hasn't been shipped yet)?
    - Add/remove products
    - Update quantities
    - Could anything else have changed?
  - CSR saves changes to order
  - CSR updates status on order

## Tech stack

### Documentation and Project Management
- Project management software: JIRA is available, as are Mural, Microsoft Planner, Tasks and To Do. Use what makes sense.
- Coding teams (back-end, front-end) should use [JSDoc](https://jsdoc.app/)
  - Code review should require appropriate comments
  - Code should not be merged to main without adequate comments
- Back-end API must be documented using [OpenAPI](https://swagger.io/specification/) specification. Additional Swagger tools can be used as desired.
- Overall documentation is up to the overall team. Some possibilities:
  - Custom Wiki
  - GitHub Wiki
  - Confluence? (John and Abby to determine)
  - Something else?
- Documentation requirements
  - If a new person joins a team, what documentation do they need?
  - What are the requirements of the application?
    - Which have been met?
    - Which are you planning to meet?
    - Which will be met in a future, post-capstone, sprint (theoretically)?

### Back-end

- [Node.js](https://nodejs.org/en) >=16
- [ExpressJS](https://expressjs.com/) 4
- [Sequelize](https://sequelize.org/) as an ORM library
- Other libraries as you see fit
- Other technologies at the team's discretion

### Front-end

- Browser
  - TJX standard is the most recent version of Edge
  - Also support Chrome - 2 (latest three versions of Chrome)

The rest of the front-end stack is left to the front-end team's discretion. The suggestions below are only that, suggestions.

- Wireframing: [Visio](https://www.microsoft.com/en-us/microsoft-365/visio/visio-in-microsoft-365) is recommended; other software is possible at your request and TJX approval
  - But keep your time constraints in mind!
- CSS: [Bootstrap](https://getbootstrap.com/) is recommended, though alternatives are allowed
- JS
  - You can use plain, vanilla JS to do everything if you want
  - You can also use any library or framework that you'd like  
    - [Vue.js](https://vuejs.org)  
    - [React](https://react.dev/)  
    - [Angular](https://angular.io/)  
    - Something else?
  - Helpful libraries
    - [JQuery](https://jquery.com/)
    - [Axios](https://github.com/axios/axios)
    - [Lodash](https://lodash.com/docs/)

### Database and Analytics

- MySQL >=8.
- Sequelize for ORM
- Additional software for analytics is unconstrained.
- Power BI is provided to the database and analytics team

### DevSecOps

- GitHub Actions will be used for CI/CD pipelines in conjunction with Azure.
- John will work with DevSecOps on initial repo setup
- Pipeline should include
  - Tests (possibly at several levels)
  - Code formatting (all code has to look the same in the repo)
  - Linting? (Optional, but recommended)
  - Generate deployment artifact
  - Deploy to Azure

### Other stuff

- Authentication and authorization solutions are unconstrained, but required.

- Testing framework(s) is left unconstrained, but consider: 
  - [Mocha](https://mochajs.org/) 
  - [Jest](https://jestjs.io/) are recommended. 
  - Front-end and testing teams should consider libraries like [Testing Library](https://testing-library.com/docs/) for unit and integration tests. 
  - Consider [Supertest](https://github.com/visionmedia/supertest/) for API testing. 
  - Teams should examine libraries for other integration tests.

## Application requirements

### CSRs need to be able to

- Authenticate themselves via a login mechanism
- CRUD for Orders including the ability to interactively add products from the Product catalog
- CRUD for Customers
- Tie the order to a Customer
- Browse the product catalog (as a CSR adds or removes products from an order, the product count needs to be updated)
- Browse the customer database
- There should be the ability to save an Order as a draft
- Track and change the status of the order

## API starting point

| Method    | URLs              | Actions                                                                           |
| :-------- | :---------------- | :-------------------------------------------------------------------------------- |
| GET       | api/customers     | Get all customers                                                                 |
| GET       | api/customers/:id | Get specific customer                                                             |
| POST      | api/customers     | Create new customer                                                               |
| PUT/PATCH | api/customers/:id | Modify existing customer                                                          |
| DELETE    | api/customers/:id | Remove customer (data compliance/right to be forgotten)                           |
| GET       | api/orders        | Get all orders                                                                    |
| GET       | api/orders/:id    | Get specific order                                                                |
| POST      | api/orders        | Create new order (think about how to differentiate between draft and live orders) |
| PUT/PATCH | api/orders/:id    | Modify existing order                                                             |
| DELETE    | api/orders/:id    | Delete a draft order (shouldn't allow for deletion of live orders)                |
| GET       | api/products      | Get all products                                                                  |
| GET       | api/products/:id  | Get specific product                                                              |
| PUT/PATCH | api/products/:id  | Modify product (e.g., inventory)                                                  |

What about searching? Filtering? Versioning? Pagination? Limiting the result set?

## First steps

1. Set up a capstone team in Teams, with channels for Analysts, Engineers, Front-end, Back-end, Database, DevSecOps, and General. Make sure to invite everyone (engineers, analysts, John, Raymond, Abby, Rachael) to the team.
1. Discuss the architecture of the app amongst the team. Create a diagram that illustrates the flow of data between various components.
1. Review the suggested API design and think about the objects/representations. Do they support all of the functionality that is required for the application? Can you visualize which API methods will need to be called, and how the objects will change at each step of the order lifecycle?
1. How will you coordinate amongst teams? Amongst yourselves? How can your PM see progress?
1. Database team: Draw/generate an Entity Relationship Diagram for the DB schema. Once this is in hand, creation and intialization of the required tables is trivial.
1. Back-end team: Encode the API using the [OpenAPI](https://swagger.io/specification/) specification. Doing so will not only serve as a canoncial source of living documentation, but also allow for the auto generation of client and server method stubs.
1. Front-end team: Review the suggested JS and CSS frameworks. Your choice of server side tech is non-negotiable in this case, but management defers to you regarding choice of front-end technologies.
1. Work with your clients (John and Raymond) to establish a Minimum Viable Product (MVP). One important goal of the MVP is that it must be complete by the first sprint. 

## Sprint structure

The capstone will be divided into two sprints: August 2-10 and August 10-17. Roughly five business days each.

The minimum viable product is due by the end of the first sprint.

The clients will discuss goals for the second sprint with the analysts.

## Suggested milestones

This is not comprehensive or exhaustive. Nor is it in any particular order!

### First sprint

- DevSecOps has set up a repo in TJX's GitHub
- Front-end has a screen that talks to the back-end
- Database has a table that the back-end can talk to via Sequelize
- Back-end can draw data from the database
- Back-end has an API endpoint that receives requests from the front-end, talks to the database, returns to the front-end
- DevSecOps has CI/CD set up to do some work (initially deployments, quickly thereafter testing and other requirements)
- Front-end and back-end have at least one unit test each
- DevSecOps and/or Database have deployed the database to Azure
- DevSecOps and/or back-end have deployed the API to Azure
- DevSecOps and/or front-end have deployed the front-end to Azure

### Second sprint

- DevSecOps coordinates with appropriate teams for a login system
- Teams generate integration tests (front-end to back-end, front-end to back-end to database, back-end to database, others?)
- Teams generate user acceptance tests, UI testing, boundary testing
- Teams maintain the README and other documentation (Wiki?)

## Capstone presentation

The Monday (21st August) after the Capstone concludes, you'll be expected to deliver a presentation about your experience on a per-team basis. The presenation should be about 10-15 minutes long. Use TJX slide show assets as a base. We will talk more about this as the Capstone goes on. 

### Presentation prompts

**Required**:

- What team are you?
- Who's on the team?
- What was the team's job?
- How does this fit into the greater app?

**Suggestions**
(don't use all of them, feel free to include other stuff you wanted to say, keep it to 10 minutes or less)

- What were some challenges you faced?
- Anything you were particularly proud of?
- Demonstrate some of the work you did
- Show off a technical thing that you felt was really cool
- What lessons did you learn?
- What would you do differently?
- Anyone you want to shout out/hype up for their help (on your team, other teams, or outside the bootcamp)?
- Favorite topics in the bootcamp?
- Most challenging topics in the bootcamp?
- What did you learn from the capstone? (Perhaps focusing on the non-technical stuff, e.g. "It was interesting working across time zones")

### Presentation tips

If you're going to demo something (and you should!), have the demo loaded up and ready to go. Don't wait for it to load while people are watching. Possibly have the start page and the end page loaded in different tabs so you can show the results even if you're having technical difficulties.

If you want to show a complex process (here's what it looks like when we check in code...), consider recording a screen capture of it and displaying that as part of your presentation. You can guarantee it's successful.

If you are going to demo something live, TRY IT OUT THAT MORNING **BEFORE THE PRESENTATION**. Nothing worse than something that changed and now doesn't work and you only figure that out as you're walking through your demo.
