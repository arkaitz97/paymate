# Bank API

A Ruby on Rails API application for the Paymate payment system.

## Prerequisites

- Ruby 3.x
- Docker & Docker Compose
- Bundler

## Development Setup

### 1. Install Dependencies

```bash
bundle install
```

### 2. Start Services (PostgreSQL & Redis)

```bash
docker-compose up -d
```

This will start:
- **PostgreSQL 16** on port 5432
- **Redis 7** on port 6379

### 3. Setup Database

```bash
bundle exec rails db:create
bundle exec rails db:migrate
bundle exec rails db:seed
```

### 4. Run the Application

```bash
bundle exec rails server
```

The API will be available at `http://localhost:3000`

## Service Configuration

### PostgreSQL Database
- **Host:** localhost
- **Port:** 5432
- **Database:** bank_api_development
- **Username:** paymate
- **Password:** paymate_dev_password
- **Test Database:** bank_api_test

### Redis
- **Host:** localhost
- **Port:** 6379
- **Database 0:** Cache
- **Database 1:** Action Cable

## Testing

```bash
bundle exec rails test
```

## Docker Commands

### Start all services
```bash
docker-compose up -d
```

### Stop all services
```bash
docker-compose down
```

### Stop and remove all data (reset)
```bash
docker-compose down -v
```

### View logs
```bash
# All services
docker-compose logs -f

# PostgreSQL only
docker-compose logs -f postgres

# Redis only
docker-compose logs -f redis
```

### Check service status
```bash
# PostgreSQL
docker-compose exec postgres pg_isready -U paymate

# Redis
docker-compose exec redis redis-cli ping
```

### Connect to services
```bash
# PostgreSQL CLI
docker-compose exec postgres psql -U paymate -d bank_api_development

# Redis CLI
docker-compose exec redis redis-cli
```

## Environment Variables

Override service hosts by setting:
```bash
export DB_HOST=localhost
export REDIS_URL=redis://localhost:6379/0
```

When running Rails in a container:
```bash
export DB_HOST=postgres
export REDIS_URL=redis://redis:6379/0
```

## What Uses Redis?

- **Cache Store**: Application caching (database 0)
- **Action Cable**: WebSocket connections (database 1)
- **Background Jobs**: Solid Queue uses PostgreSQL by default
