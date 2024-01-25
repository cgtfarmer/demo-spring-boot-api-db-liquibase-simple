# Getting Started

### Installation

1. Clone this project
1. Run: `docker-compose build`
1. Run: `docker-compose run --rm app mvn dependency:resolve`
1. Run: `docker-compose up -d postgres & sleep 10` to bring up DB
1. Run: `docker-compose up liquibase` to migrate DB
1. Run: `docker-compose up -d app` to bring up app
1. Run: `docker-compose logs -f app` to tail logs
1. Navigate to `http://localhost:3000/users` in your browser

### Development

- Run: `docker-compose down; docker-compose up -d postgres app`
- Wait for stack to finish starting up

## Wipe Database

Run: `docker-compose down`
Run: `docker-compose run --rm liquibase drop-all`
Run: `docker-compose up liquibase`

### Run Playwright Tests

Run: `docker-compose down; docker-compose up -d postgres app & sleep 10; docker-compose up playwright`

## Run Playwright Tests (w/ Stack Reuse)

- Leave dev stack running
- Run in another terminal: `docker-compose up playwright` (repeat as needed)
- Or: `docker-compose run --rm playwright npx playwright test --debug` (repeat as needed)
- Or: `docker-compose run --rm playwright npx playwright test file.test.js --debug` (repeat as needed)
- Or: `docker-compose run --rm playwright npx playwright test -g "create user" --debug` (repeat as needed)

### Endpoints

#### User CRUD

```
GET /api/users
POST /api/users

GET /api/users/:id
PUT /api/users/:id
DELETE /api/users/:id
```
