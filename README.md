# Custom User Model

This Django application implements a custom user model that uses email as the primary identifier instead of a username. The implementation extends Django's built-in authentication system while providing additional customization options.

## Features

- Email-based authentication
- Full name field
- Custom user manager with email normalization
- Proper password hashing
- Superuser creation support
- Integration with Django's permission system

## Models

### CustomUser

The `CustomUser` model extends Django's `AbstractBaseUser` and `PermissionsMixin` to provide a complete user authentication system.

#### Fields

- `email` (EmailField): Unique identifier for authentication
- `full_name` (CharField): User's full name
- `is_active` (BooleanField): Designates whether the user account is active
- `is_staff` (BooleanField): Determines if the user can access the admin site

### CustomUserManager

A custom manager class that handles user creation and superuser creation.

#### Methods

- `create_user(email, password=None, **extra_fields)`: Creates and saves a regular user
- `create_superuser(email, password=None, **extra_fields)`: Creates and saves a superuser

## Usage

### Installation

1. Add the custom user model to your Django settings:

```python
AUTH_USER_MODEL = 'your_app_name.CustomUser'
```

2. Run migrations:

```bash
python manage.py makemigrations
python manage.py migrate
```

### Creating Users

```python
# Create a regular user
user = CustomUser.objects.create_user(
    email='user@example.com',
    password='your_password',
    full_name='John Doe'
)

# Create a superuser
superuser = CustomUser.objects.create_superuser(
    email='admin@example.com',
    password='admin_password',
    full_name='Admin User'
)
```

### Authentication

Users can authenticate using their email address and password through Django's standard authentication backend.

## Security Features

- Passwords are automatically hashed using Django's password hashing system
- Email addresses are normalized before saving
- Built-in support for Django's permission system through PermissionsMixin

## Requirements

- Django 3.x or higher
- Python 3.x

## Contributing

Feel free to submit issues and enhancement requests.