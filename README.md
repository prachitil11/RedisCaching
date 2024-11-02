**Project Setup**
This project uses:

Spring Boot: for application framework and dependency injection
Postgres: as the primary database
Redis: for caching to improve performance

**Technologies Used**
Java (Spring Boot)
Spring Data Postgres
Spring Cache with Redis

**Features**
Caching of database records using Redis to reduce the load on Postgres.
RESTful API endpoints to perform CRUD operations on product data.

**Getting Started**
Follow these instructions to set up and run the project on your local machine.

**Prerequisites**
Java 17 or higher
Maven (for dependency management)
Postgres installed locally or run in Docker
Redis installed locally or run in Docker

**Configuration**
1. Clone the Repository
bash
Copy code
git clone https://github.com/prachitil11/RedisCaching.git
cd your-repo-name
2. Setup application.properties
Edit the src/main/resources/application.properties file with the correct configuration for Redis and Postgres.

properties
Copy code
# Postgres properties
spring.datasource.url=jdbc:postgresql://localhost:5433/jwtsecurity
spring.datasource.username=postgres
spring.datasource.password=1234
spring.datasource.driver-class-name=org.postgresql.Driver

# Redis properties
spring.data.redis.host=localhost
spring.data.redis.port=6379

bash
Copy code

Build and Run the Application
Build and start the Spring Boot application:

bash
Copy code
mvn clean install
mvn spring-boot:run
Usage
The application provides API endpoints to manage Product entities.

Sample API Endpoints
Get Product by ID (with caching):
GET /api/products/{id}

Create a Product:
POST /api/products

Update a Product:
PUT /api/products/{id}

Delete a Product (and evict cache):
DELETE /api/products/{id}

Note: The first time a product is fetched by ID, it will be stored in Redis cache. Subsequent calls with the same ID will retrieve it from Redis until it expires or is updated.
