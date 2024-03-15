# Capstone Project: Create an "Order Tracking" application

## Teams for the mini-sprint

See below for the definintion of the mini sprint. You are not restricted to being on these teams for the duration of the capstone. You will be able to switch teams for sprints 1 and 2.

### Engineers

| Front-end          | Back-end         | Database              | DevSecOps      |
| ------------------ | ---------------- | --------------------- | -------------- |
| Anas Samadi        | Alessandro Blasi | Allen Garcia          | Hassan Alazawi |
| Divyanksha Bangwal | Daury Argueta    | Dean Beebe            | Umar Sajjad    |
| Emran Rahmat       | Sharun Kugan     | Lanique Lynn Peterson | Parth Patel    |
| Matthew Favazza    | Tom Conboy       | Sohail Quadir         | Zubeda Newaz   |
| Tom Campbell       |                  |                       |                |

### Analysts

| Front-end          | Back-end        | Database                | DevSecOps           |
| ------------------ | --------------- | ----------------------- | ------------------- |
| Chardana Martin    | Joseph Calderon | Adesina Adeniran        | Anushca-Mai Dunkley |
| Ian Botelho        | Sophia Datsko   | Kayla Shah              | Karanpreet Tatla    |
| Tatiana Jean-Louis | Calvin Graves   | Michael Lawson-Adesanya | Marina Mincheva     |
| Julia Pyun         | Crystal Lobo    | Moises Naldo            | Taryn Bennett       |
|                    |                 | Riwa Kulkarni           |                     |

## Application description

We have some customers that still prefer using our paper catalog. TJX sends them said catalog with a phone number they can call. The phone number connects customers to our Customer Service Reps (CSRs). The CSRs need an application that lets them manage customers and their orders.

What should our CSRs be able to do?

- Log in / Log out
- For any Customer
  - Find an existing customer
  - Enter a new customer into the system
  - Edit a customer's details
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

### Order lifecycle

- All interactions
  - Customer calls in, CSR answers
  - CSR adds Customer if they do not exist
  - CSR edits/updates Customer as needed

- New Order
  - CSR creates an Order
  - Add Product(s)
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

### CSRs need to be able to

- Authenticate themselves via a login mechanism
- CRUD for Orders including the ability to interactively add products from the Product catalog
- CRUD for Customers
- Tie the order to a Customer
- Browse the product catalog (as a CSR adds or removes products from an order, the product count needs to be updated)
- Browse the customer database
- There should be the ability to save an Order as a draft
- Track and change the status of the order

## Tech stack

### Front-end

- Browser
  - TJX standard is the most recent version of Edge
  - Also support Chrome - 2 (latest three versions of Chrome)

The rest of the front-end stack is left to the front-end team's discretion. The suggestions below are only that, suggestions.

- Wireframing: [Visio](https://www.microsoft.com/en-us/microsoft-365/visio/visio-in-microsoft-365) is recommended; other software is possible at your request and TJX approval
  - But keep your time constraints in mind!
- CSS: 
	- [Bootstrap](https://getbootstrap.com/) is recommended
	- Though alternatives are allowed
	- Or write the CSS yourself!
- JS
  - You can use plain, vanilla JS to do everything if you want
  - You can also use any library or framework that you'd like  
    - [Vue.js](https://vuejs.org)  
    - [React](https://react.dev/)  
    - [Angular](https://angular.io/)  
    - Something else?
  - Helpful libraries
    - [JQuery](https://jquery.com/) General low-level DOM tools
    - [Wretch](https://github.com/elbywan/wretch) Better `fetch` experience
    - [Lodash](https://lodash.com/docs/) General JavaScript tools

### Back-end

- [Node.js](https://nodejs.org/en) >=18, >= 20 preferred
- [ExpressJS](https://expressjs.com/) 4
- [Sequelize](https://sequelize.org/) as an ORM library
- Other libraries as you see fit
- Other technologies at the team's discretion

### Database and Analytics

- MySQL >=8.
- Sequelize for ORM
- Power BI is provided to the database and analytics team
- Additional software for analytics is unconstrained.

### DevSecOps

- GitHub Actions will be used for CI/CD pipelines in conjunction with Azure.
- John P. will work with DevSecOps on initial repo and Azure setup
- Pipeline should include
  - Tests (possibly at several levels)
  - Code formatting (all code has to look the same in the repo)
  - Linting? (Optional, but recommended)
  - Generate deployment artifact
  - Deploy to Azure

### Documentation and Project Management

- Project management software: Discuss with John Kidd. Use what makes sense.
- Coding teams (back-end, front-end) should use [JSDoc](https://jsdoc.app/)
  - Code review should require appropriate comments
  - Code should not be merged to main without adequate comments
- Back-end API must be documented using [OpenAPI](https://swagger.io/specification/) specification. Additional Swagger tools can be used as desired.
- Overall documentation is up to the team. Some possibilities:
  - Custom Wiki
  - GitHub Wiki
  - Something else?
- Documentation requirements
  - If a new person joins a team, what documentation do they need?
  - What are the requirements of the application?
    - Which have been met?
    - Which are you planning to meet?
    - Which will be met in a future, post-capstone, sprint (theoretically)?

### Other stuff

- Authentication and authorization solutions are unconstrained, but required.
- Testing 
	- Engineering and Analysts should work together closely here!
	- Framework(s) is/are left unconstrained, but consider: 
		- [Vitest](https://vitest.dev/) Works natively with ESM, modern, easy to setup
	  - [Mocha](https://mochajs.org/) Requires add-ons like chai and sinon, no watch mode
	  - Front-end and testing teams should look at libraries like [Testing Library](https://testing-library.com/docs/) for unit and integration tests. 
	  - Maybe [Supertest](https://github.com/visionmedia/supertest/) for API testing?
	  - Teams should examine libraries for other integration tests.

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

1. Set up a capstone team in Teams, with channels for General, Analysts, Engineers, Front-end, Back-end, Database, and DevSecOps. Make sure to invite everyone (engineers, analysts, John Paxton, John Kidd, Abby, Rachael) to the team.
2. How will you coordinate amongst teams? Amongst yourselves? How can your PM see progress? Keep in mind that Analysts and Engineers will work together closely. As will different teams. Lots of cross-communication to be managed!
3. John and John will publish a "to do" list for all teams. Analysts will take this up and shepherd it for the next two days of work.
4. Work with your clients (John and John will be the clients for this project) to establish a Minimum Viable Product (MVP). One important goal of the MVP is that it must be complete by the first sprint. 

## Sprint structure

The capstone will be divided up as follows:

- March 15, 18: A "mini-sprint" where we set our foundation. Engineers are assigned to a team and have a to-do list, which they will work on with John P. Analysts have these two days 
- March 19-22: Sprint 1
- March 25-29: Sprint 2 (UK and Canada have March 29th off)
- The sprints are "compressed" in that they're shorter, but will otherwise generally follow the structure of a sprint. We will talk more about this at the general meeting on March 18.

## Asking for help

For the mini-sprint and Sprint 1, the Johns are available for technical help. Make appointments with them as needed. This may change in Sprint 2.

Ask each other for help! Swarm on difficult topics.

If you know former EICs, you can ask them for help as well. The details of their capstones may be different in small and large ways, but they can help you with tasks if they have the time.


## Capstone presentation

The Tuesday (2nd April) after the Capstone concludes, you'll be expected to deliver a presentation about your experience on a per-team basis. The presenation should be about 10-15 minutes long. Use TJX slide show assets as a base. We will talk more about this as the Capstone goes on. 

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
