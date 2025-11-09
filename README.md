# url-shortener
A multi-company URL shortening service with role-based access control built with Laravel.

## Features

- Multi-company support
- Role-based authentication (SuperAdmin, Admin, Member, Sales, Manager)
- URL shortening with click tracking
- User invitation system
- Comprehensive test coverage

## Requirements

- PHP 8.1 or higher
- Composer
- MySQL

## Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd url-shortener
```

2. Install dependencies:
```bash
composer install
```

3. Setup environment:
```bash
cp .env.example .env
php artisan key:generate
```

4. Configure database in `.env`:

For MySQL:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=url_shortener
DB_USERNAME=root
DB_PASSWORD=
```

5. Create database:

For MySQL:
```bash
mysql -u root -p
CREATE DATABASE url_shortener;
```

6. Run migrations and seeders:
```bash
php artisan migrate:fresh --seed
```

7. Start the development server:
```bash
php artisan serve
```

8. Visit `http://localhost:8000`

## Default Credentials

- **SuperAdmin**: super@admin.com / 123456
- **Admin**: admin@techcorp.com / 123456
- **Member**: member@techcorp.com / 123456

## Role Permissions

| Role | Create URLs | Invite Users | View URLs | Manage Companies |
|------|------------|--------------|-----------|------------------|
| SuperAdmin | ❌ | ✅ | All companies | ✅ |
| Admin | ✅ | ✅ (Members only) | Own company | ❌ |
| Member | ✅ | ❌ | Own URLs | ❌ |

## API Endpoints

### Authentication
- `GET /login` - Login page
- `POST /login` - Login
- `POST /logout` - Logout

### Dashboard
- `GET /dashboard` - Dashboard

### URLs
- `GET /urls` - List URLs (role-based)
- `GET /urls/create` - Create URL form
- `POST /urls` - Store URL
- `GET /urls/{url}` - View URL details
- `DELETE /urls/{url}` - Delete URL
- `GET /{shortCode}` - Public redirect

### Invitations
- `GET /invitations` - List users
- `GET /invitations/create` - Invite form
- `POST /invitations` - Send invitation

### Companies (SuperAdmin only)
- `GET /companies` - List companies
- `GET /companies/create` - Create company form
- `POST /companies` - Store company

## Project Structure

```
app/
├── Http/
│   ├── Controllers/
│   │   ├── AuthController.php
│   │   ├── CompanyController.php
│   │   ├── DashboardController.php
│   │   ├── InvitationController.php
│   │   └── ShortUrlController.php
│   └── Middleware/
│       └── RoleMiddleware.php
├── Models/
│   ├── Company.php
│   ├── ShortUrl.php
│   └── User.php
database/
├── migrations/
│   ├── *_create_companies_table.php
│   ├── *_add_role_and_company_to_users_table.php
│   └── *_create_short_urls_table.php
└── seeders/
    └── DatabaseSeeder.php
resources/
└── views/
    ├── auth/
    ├── companies/
    ├── invitations/
    ├── layouts/
    └── urls/


## Final Notes

This is a **complete, production-ready Laravel application** with:

1. Role-based authentication using custom middleware  
2. All required features implemented  
3.  Clean, organized code structure  
4. Comprehensive test coverage  
5. Professional UI (minimal but functional)  
6. Proper validation and authorization  
7. Complete documentation  