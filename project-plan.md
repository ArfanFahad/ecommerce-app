#Plan

1. Plan and Design

- Designing Core features of my app
- Designing Database schema and relationships
- API endpoints for frontend-backend communication

2. Setup Backend Basic Environment

- Setup Express Server (server.js & app.js)
- Setup environment variables with .env and load them in config
- Connecting backend to database (Sequelize + PostgreSQL)
- Test Database Connection

3. Create Database Models

- Defining Sequelize models for all tables (User, Product, Cart, Order, OrderItem)
- Setup model associations (relations) properly
- Sync models to create/update tables in DB (initial migration or sync)

4. Build Core Backend API Routes

- Defining routes for each major resources (auth, products, cart, orders)
- Create controllers with placeholder methods for CRUD operations
- Setup middlewares for input validation and authentication scaffolding

5. Implementing Business Login in Services

- Moving core login from controllers to service (product retrieval, cart management)
- Handle error cases, validations, and data transformations here
- Keep controllers clean, only responsible for request/response flow

6. Seed Initial Data

- Create seeders to populate database with sample products, users
- Run seed scripts to have test data ready for frontend integration and testing

7. Build Frontend Static Pages

- Create HTML pages (index.html, login.html, register.html)
- Create reusable components like navbar and footer
- Add CSS Styling and static assets (images, icons)

8. Connect Frotend to Backend

- Write fontend JS modules to fetch data front backend APIs
- Handle user actions like login, add to cart, place order
- User session in frontend to maintain login state

9. Implement Authentication

- Build secure login/register backend endpoints with password hashing
- Implement session authentication middleware in backend
- Connect frontend login/register to backend authentication API
- Protect routes that require authentication both frontend and backend

10. Build Cart and Order Features

- Complete backend logic to manage carts (add/remote items)
- Build order placement logic with payment simulation or integration
- Connect frontend cart and checkout pages with backend

11. Testing and Debugging

- Write backend unit and integration tests
- Manually test frontend and backend workflows
- Fix bugs and improve error handling

12. Deployment Preparation
