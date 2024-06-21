
# Django E-com Web Application

This is a Django web application that includes user authentication, registration, email handling, and integration with Stripe for billing. The application is containerized using Docker for ease of deployment.

## Features

- User authentication (login/logout)
- User registration
- Password reset via email
- Stripe payment integration
- Deployment ready with Docker

## Prerequisites

- Python 3.10 or higher
- Django 5.0
- Docker
- Stripe account (for payment integration)
- Postgres database

## Setup

### Environment Variables

Create a `.env` file in the root directory of your project and add the following environment variables:

```
DEBUG=on
SECRET_KEY=your_secret_key
ALLOWED_HOSTS=.railway.app,127.0.0.1,localhost
DATABASE_URL=postgres://user:password@hostname:port/dbname
EMAIL_HOST=smtp.example.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=your_email@example.com
EMAIL_HOST_PASSWORD=your_email_password
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
```

### Local Development

1. **Clone the repository**:

    ```bash
    git clone https://github.com/felixojiambo/e-django.git
    cd yourproject
    ```

2. **Create a virtual environment and activate it**:

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. **Install the dependencies**:

    ```bash
    pip install -r requirements.txt
    ```

4. **Run migrations**:

    ```bash
    python manage.py migrate
    ```

5. **Create a superuser**:

    ```bash
    python manage.py createsuperuser
    ```

6. **Run the development server**:

    ```bash
    python manage.py runserver
    ```

7. **Access the application**:

    Open your web browser and go to `http://127.0.0.1:8000`.

### Docker

1. **Build the Docker image**:

    ```bash
    docker build -t yourproject .
    ```

2. **Run the Docker container**:

    ```bash
    docker run --env-file .env -p 8000:8000 yourproject
    ```

3. **Access the application**:

    Open your web browser and go to `http://localhost:8000`.

### Deployment

This project is configured for deployment on platforms like Railway. Ensure all environment variables are set in the deployment environment.

1. **Collect static files**:

    ```bash
    python manage.py collectstatic --noinput
    ```

2. **Run migrations**:

    ```bash
    python manage.py migrate
    ```

3. **Start the server**:

    ```bash
    gunicorn yourproject.wsgi:application --bind 0.0.0.0:8000
    ```

## Project Structure

```
yourproject/
├── yourapp/
│   ├── migrations/
│   ├── static/
│   ├── templates/
│   ├── admin.py
│   ├── apps.py
│   ├── forms.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── yourproject/
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
├── templates/
├── static/
├── .env
├── Dockerfile
├── requirements.txt
└── manage.py
```

## Contributing

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes.
4. Commit your changes (`git commit -am 'Add some feature'`).
5. Push to the branch (`git push origin feature/your-feature`).
6. Create a new Pull Request.

## License

This project is licensed under the MIT License.

## Contact

For any inquiries, please contact [felixojiamboe@gmail.com].
