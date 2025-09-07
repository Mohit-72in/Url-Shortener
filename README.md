# Spring Boot URL Shortener

A modern URL shortener service built with Spring Boot, featuring user authentication, private/public URLs, expiration dates, and click tracking.

## Features

- 🔗 Create short URLs from long URLs
- 👤 User authentication and registration
- 🔒 Private URLs (only accessible by creator)
- ⏰ URL expiration dates
- 📊 Click tracking and analytics
- 👨‍💼 Admin dashboard for managing all URLs
- 📱 Responsive web interface
- 🐳 Docker support

## Tech Stack

- **Backend**: Spring Boot 3.5, Spring Security, Spring Data JPA
- **Database**: PostgreSQL with Flyway migrations
- **Frontend**: Thymeleaf, Bootstrap 5
- **Build Tool**: Maven
- **Containerization**: Docker & Docker Compose

## Quick Start

### Using Docker Compose (Recommended)

1. Clone the repository:
```bash
git clone <your-repo-url>
cd spring-boot-url-shortener
```

2. Run with Docker Compose:
```bash
docker-compose up -d
```

3. Access the application at `http://localhost:8080`

### Local Development

1. Start PostgreSQL database:
```bash
docker run -d --name postgres \
  -e POSTGRES_DB=urlshortener \
  -e POSTGRES_USER=postgres \
  -e POSTGRES_PASSWORD=postgres123 \
  -p 5432:5432 postgres:17
```

2. Run the application:
```bash
./mvnw spring-boot:run
```

## Default Users

- **Admin**: admin@gmail.com / admin
- **User**: siva@gmail.com / secret

## Deployment

### Deploy to Render (Free)

1. Fork this repository
2. Connect your GitHub account to [Render](https://render.com)
3. Create a new Web Service from your forked repository
4. Render will automatically detect the `render.yaml` configuration
5. Your app will be deployed with a PostgreSQL database

### Deploy to Railway (Free)

1. Fork this repository
2. Connect your GitHub account to [Railway](https://railway.app)
3. Create a new project from your forked repository
4. Add a PostgreSQL database service
5. Railway will use the `railway.json` and `nixpacks.toml` configurations

### Environment Variables for Production

- `APP_BASE_URL`: Your deployed application URL
- `DATABASE_URL`: PostgreSQL connection string
- `DB_USERNAME`: Database username
- `DB_PASSWORD`: Database password
- `SPRING_PROFILES_ACTIVE`: Set to `prod`

## API Endpoints

- `GET /` - Home page with URL creation form
- `POST /short-urls` - Create a new short URL
- `GET /s/{shortKey}` - Redirect to original URL
- `GET /my-urls` - User's URLs (authenticated)
- `GET /admin/dashboard` - Admin dashboard (admin only)

## Project Structure

```
src/
├── main/
│   ├── java/com/sivalabs/urlshortener/
│   │   ├── domain/          # Domain entities and services
│   │   ├── web/             # Controllers and DTOs
│   │   └── config/          # Configuration classes
│   └── resources/
│       ├── db/migration/    # Flyway database migrations
│       ├── templates/       # Thymeleaf templates
│       └── static/          # CSS, JS, images
└── test/                    # Test classes
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is open source and available under the [MIT License](LICENSE).

## Screenshots

### Home Page
- Clean interface for creating short URLs
- Public URLs listing with pagination

### User Dashboard
- Personal URL management
- Bulk delete functionality
- Private/public URL indicators

### Admin Dashboard
- System-wide URL analytics
- User management capabilities
- Comprehensive URL statistics

## Performance & Scalability

- Efficient database queries with proper indexing
- Connection pooling for database connections
- Stateless architecture for horizontal scaling
- Docker containerization for easy deployment

## Security Features

- BCrypt password hashing
- CSRF protection
- Role-based access control
- Private URL access restrictions
- Input validation and sanitization