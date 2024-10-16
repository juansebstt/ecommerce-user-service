# E-commerce User Service

## Overview

The **E-commerce User Service** is responsible for managing user data and operations within the e-commerce platform. It handles tasks such as user registration, profile management, authentication, and authorization. This service interacts with the **E-commerce Auth Service** for authentication-related tasks and integrates with other services like the API Gateway and Notification Service.

## Features

- **User Registration**: Allows users to create accounts on the platform.
- **Profile Management**: Users can update and manage their profiles.
- **Authentication & Authorization**: Works with the **E-commerce Auth Service** to authenticate users and enforce role-based access controls.
- **Integration with Other Services**: User data is shared across various services, such as the Order and Cart services.

## Technologies Used

- **Java**
- **Spring Boot**
- **Maven** (for dependency management)
- **MySQL** (or any other relational database)
- **Spring Security** (for authentication and authorization)

## Prerequisites

Before running this service, ensure you have the following:

- **Java JDK 11 or higher**
- **Maven** (for building the project)
- A running **MySQL** database (or other supported database).
- Access to the relevant microservices (e.g., Auth Service, API Gateway, Notification Service).

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/juansebstt/ecommerce-user-service.git
    ```

2. Navigate to the project directory:

    ```bash
    cd ecommerce-user-service
    ```

3. Build the project using Maven:

    ```bash
    mvn clean install
    ```


## Configuration

You need to configure the database and authentication settings in your `application.yml` or `application.properties` file.

### Sample Configuration

```yaml
server:
  port: 8082

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/ecommerce_user_db
    username: yourUsername
    password: yourPassword
    driver-class-name: com.mysql.cj.jdbc.Driver

  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true

  application:
    name: ecommerce-user-service
```

## Inter-Service Communication

The **E-commerce User Service** communicates with various microservices:

- **[E-commerce API Gateway](https://github.com/juansebstt/ecommerce-api-gateway)**:
    - Routes user-related requests (e.g., login, profile management) to the User Service.
- **[E-commerce Auth Service](https://github.com/juansebstt/ecommerce-auth-service)**:
    - Handles authentication and authorization tasks for the User Service.
- **[E-commerce Notification Service](https://github.com/juansebstt/ecommerce-notification-service)**:
    - Sends notifications to users regarding account updates or other events.

## Usage

### User Registration

The user registration feature allows new users to create an account. To test this feature, make a POST request to the `/register` endpoint with the following payload:

```json
{
  "username": "testuser",
  "email": "testuser@example.com",
  "password": "securepassword"
}
```

### Profile Management

Authenticated users can update their profile by making a PUT request to the `/profile` endpoint. For example:

```json
{
  "email": "newemail@example.com",
  "firstName": "John",
  "lastName": "Doe"
}
```

## Testing

You can use tools like **Postman** or **curl** to test the various API endpoints. Ensure you have proper authentication tokens when testing secured endpoints.

## Contributing

Feel free to submit pull requests or open issues if you find bugs or want to contribute to the project.