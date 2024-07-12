# E-commerce API with Flask

This repository contains a simple e-commerce application built with Flask. The application includes user authentication, product management, and a shopping cart feature. 

## Features  

- User registration and login
- Product management (add, update, delete, view)
- Shopping cart management (add to cart, view cart, remove from cart, checkout)
- API endpoints for interacting with the application
- Basic user authentication using Flask-Login

## Requirements

- Python 3.x
- Flask
- Flask-SQLAlchemy
- Flask-CORS
- Flask-Login

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/ecommerce-flask.git
   cd ecommerce-flask
   ```

2. Create a virtual environment and activate it:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

4. Initialize the database:
   ```bash
   flask shell
   >>> db.create_all()
   >>> db.session.commit()
   >>> exit()
   ```

## Configuration

Make sure to configure your Flask application by setting the necessary environment variables in a `.env` file or directly in your `app.py` file:

```python
app.config['SECRET_KEY'] = "minha_chave_123"
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///ecommerce.db'
```

## Running the Application

To run the application, use the following command:

```bash
flask run
```

The application will be available at `http://127.0.0.1:5000`.

## API Endpoints

### User Authentication

- **Login**: `POST /login`
- **Logout**: `POST /logout`

### Product Management

- **Add Product**: `POST /api/products/add`
- **Delete Product**: `DELETE /api/products/delete/<int:product_id>`
- **Get Product Details**: `GET /api/products/<int:product_id>`
- **Update Product**: `PUT /api/products/update/<int:product_id>`
- **List Products**: `GET /api/products`

### Shopping Cart Management

- **Add to Cart**: `POST /api/cart/add/<int:product_id>`
- **View Cart**: `GET /api/cart`
- **Remove from Cart**: `DELETE /api/cart/remove/<int:item_id>`
- **Checkout**: `POST /api/cart/checkout`

## Models

### User
- `id`: Integer, Primary Key
- `username`: String(80), Unique, Not Null
- `password`: String(80), Not Null
- `cart`: Relationship with `CartItem`

### Product
- `id`: Integer, Primary Key
- `name`: String(120), Not Null
- `price`: Float, Not Null
- `description`: Text

### CartItem
- `id`: Integer, Primary Key
- `user_id`: Foreign Key to `User`
- `product_id`: Foreign Key to `Product`

## Flask Shell Commands

- **Drop all tables**: `db.drop_all()`
- **Create all tables**: `db.create_all()`
- **Commit the session**: `db.session.commit()`

## License

This project is licensed under the MIT License.
