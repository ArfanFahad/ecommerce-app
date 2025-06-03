draw.io link:

# Tables:

- User (id, name, email, password)
- Product (id, name, price, image, stock)
- Order (id, user_id, created_at)
- OrderItem (id, order_id, product_id, quantity)
- Cart can be stored in Redis, not the database

### User

- id(PK)
- name
- email
- password

### Product

- id (PK)
- name
- price
- stock

### Order

- id (PK)
- user_id (FK)
- created_at

### OrderItem

- id (PK)
- order_id (FK)
- product_id (FK)
- quantity
