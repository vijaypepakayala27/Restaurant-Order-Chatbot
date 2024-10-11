# Restaurant Order Chatbot

## Overview
This project implements a chatbot-based food ordering system using Django, Django REST Framework, PostgreSQL/MongoDB, and WhatsApp integration. The chatbot allows users to interact with restaurants, view menus, and place orders via WhatsApp. The backend manages restaurant information, menu items, and orders.

## Key Features
- **Django + Django REST Framework**: Backend for restaurant and order management.
- **PostgreSQL/MongoDB**: Data storage for restaurants, menus, and orders.
- **WhatsApp Chatbot**: User interaction through WhatsApp.
- **Web Panel for Restaurants**: Dashboard for restaurant owners to manage menus, configure prices, and view orders.

## Table of Contents
1. [Installation](#installation)
2. [Configuration](#configuration)
3. [Running the Application](#running-the-application)
4. [API Endpoints](#api-endpoints)
5. [WhatsApp Integration](#whatsapp-integration)
6. [Deployment](#deployment)
7. [License](#license)

## Installation
1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/restaurant-order-chatbot.git
   cd restaurant-order-chatbot
   ```

2. **Create a Virtual Environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install Dependencies**
   ```bash
   pip install django djangorestframework psycopg2 twilio
   ```

## Configuration
1. **Database Setup**
   - For PostgreSQL:
     1. Create a PostgreSQL database.
     2. Update `settings.py`:
     ```python
     DATABASES = {
         'default': {
             'ENGINE': 'django.db.backends.postgresql',
             'NAME': 'your_db_name',
             'USER': 'your_db_user',
             'PASSWORD': 'your_password',
             'HOST': 'localhost',
             'PORT': '5432',
         }
     }
     ```

   - For MongoDB (Optional):
     1. Install `djongo`:
     ```bash
     pip install djongo
     ```
     2. Update `settings.py`:
     ```python
     DATABASES = {
         'default': {
             'ENGINE': 'djongo',
             'NAME': 'your_mongo_db_name',
         }
     }
     ```

2. **WhatsApp Integration**
   - Set up a Twilio account and obtain your credentials (Account SID, Auth Token, WhatsApp number).
   - Update your webhook URL in the Twilio dashboard to point to your Django app.

## Running the Application
1. **Run Migrations**
   ```bash
   python manage.py migrate
   ```

2. **Create a Superuser**
   ```bash
   python manage.py createsuperuser
   ```

3. **Run the Development Server**
   ```bash
   python manage.py runserver
   ```

4. Access the admin panel at `http://127.0.0.1:8000/admin` to manage restaurants, menu items, and orders.

## API Endpoints
- **GET /api/restaurants/**: List all restaurants.
- **GET /api/menu-items/**: List all menu items.
- **GET /api/orders/**: List all orders.
- **POST /api/orders/**: Create a new order.

## WhatsApp Integration
The WhatsApp chatbot can respond to user messages. Users can inquire about restaurants and place orders. Incoming messages are processed in the `whatsapp_bot` view, which responds based on the user's input.

## Deployment
To deploy the application:
- Use platforms like **Heroku**, **AWS**, or **DigitalOcean** to host the Django app.
- For the database, consider **AWS RDS** for PostgreSQL or **MongoDB Atlas** for MongoDB.
- Ensure your Twilio webhook is configured to point to the deployed Django app.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements
- Django: [Django Official Site](https://www.djangoproject.com/)
- Django REST Framework: [DRF Official Site](https://www.django-rest-framework.org/)
- Twilio: [Twilio Official Site](https://www.twilio.com/whatsapp)
