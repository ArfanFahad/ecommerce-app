### 1. Plan and Design

a. Designing Core Features

- List all must-have features (already done earlier).
- Confirm Redis will be used for:
  - Storing sessions (user login)
  - Caching cart data (for speed and persistence)

b. Design Database Schema

- Use draw\.io or pen-paper to design ERD with tables:
  - `User`, `Product`, `Cart`, `Order`, `OrderItem`
- Define fields for each table (e.g., Product → id, name, price, stock).
- Define relationships:

  - One user → many orders
  - One order → many order items
  - One product → many order items
  - One user → one cart

c. Plan API Endpoints

- Write down RESTful API routes in `project-plan.md`, e.g.:
  - `POST /api/auth/register`, `GET /api/products`, `POST /api/cart/add`, etc.

### 2. Setup Backend Basic Environment

a. Initialize Node Project

- `npm init -y`
- Install dependencies: `express`, `dotenv`, `sequelize`, `pg`, `redis`, etc.

b. Setup Express Server

- Create `server.js` → run server.
- Create `app.js` → set up middleware, routers.

c. Setup `.env` and Config

- Add `.env` with variables like:
  - `DB_HOST`, `DB_USER`, `DB_PASS`, `PORT`, `REDIS_URL`
- Create `config/db.config.js`, `redis.config.js`, `session.config.js`

d. Test DB Connection

- Write Sequelize connection code and test it with `sequelize.authenticate()`

### 3. Create Database Models

a. Define Sequelize Models

- Create models: `user.model.js`, `product.model.js`, `cart.model.js`, `order.model.js`, `orderItem.model.js`

b. Setup Associations in `models/index.js`

- `User.hasMany(Order)`
- `Order.belongsTo(User)`
- etc.

c. Sync to DB

- Use `sequelize.sync({ alter: true })` to create/update DB tables.

### 4. Build Core Backend API Routes

a. Create Route Files

- `auth.routes.js`, `product.routes.js`, etc.
- Register them in `index.routes.js`

b. Create Controllers

- Add placeholder methods: e.g., `registerUser`, `getProducts`

c. Setup Middlewares

- Add input validation middleware
- Auth middleware (can be empty for now)

### 5. Implement Business Logic in Services

a. Create Service Files

- `auth.service.js`, `product.service.js`, etc.

b. Move Logic

- Controllers should just call service methods.
- Handle logic like: cart updates, product queries, validation, error throwing.

### 6. Seed Initial Data

a. Write Seeder Scripts

- In `seeders/seedProducts.js`, write code to add sample products and users

b. Run Script

- Create a `seed()` function that inserts mock data when run manually.

### 7. Build Frontend Static Pages

a. Create HTML Pages

- `index.html`, `login.html`, `register.html`, `cart.html`, `checkout.html`

b. Create Partial Components

- Move `navbar.html` and `footer.html` to `client/partials/`
- Optionally create `client/components/productCard.html` for product template

c. Add CSS & Assets

- Setup `style.css`, add images/icons in `assets/images/`

### 8. Connect Frontend to Backend

a. Write Fetch Calls in JS

- `auth.js`: login/register
- `product.js`: get products from `/api/products`
- `cart.js`: add/remove items

b. Handle DOM Updates

- Dynamically render products using templates
- Update cart page on user actions

c. Manage Session State

- Use `sessionStorage` or `cookie` to track login state on frontend

### 9. Implement Authentication

a. Secure Auth Routes

- Hash password with `bcrypt`
- Store user session in Redis

b. Create Auth Middleware

- Backend: block protected routes if not logged in
- Frontend: redirect to login if no session

c. Link Frontend ↔ Backend Auth

- Login/register forms send data to backend
- Display login/logout state on UI

10. Build Cart and Order Features

a. Cart Logic

- Backend:

  - Add/update/delete items in Redis

- Frontend:
  - Show cart items
  - Allow updates (quantity, remove)

b. Order Logic

- Backend:

  - On checkout, convert Redis cart → DB order
  - Save `Order` and `OrderItems`

- Frontend:
  - Checkout button sends request
  - Show order success message
