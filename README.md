# SecuringAPI2 Project

## Overview

SecuringAPI2 is a Spring Boot-based application demonstrating a simple user registration and login system. The project is configured with basic authentication and an in-memory user store. Users can register, log in, and update their information. The project includes basic security configurations with the ability to customize roles.

## Features

- **User Registration:** Allows users to register with a username and password.
- **User Login:** Enables users to log in with their credentials using basic authentication.
- **Role-Based Authorization:** Defines roles (ADMIN, USER) and restricts access to certain endpoints based on roles.
- **Password Encryption:** Uses `BCryptPasswordEncoder` to securely store user passwords.
- **In-Memory Users:** Configured with two predefined users for testing purposes.
- **Security Configuration:** Disables CSRF protection for simplicity during development.
  
## Technologies Used

- **Java 17**
- **Spring Boot 3.x**
- **Spring Security**
- **Spring Data JPA**
- **H2 Database (in-memory)**
- **BCryptPasswordEncoder for password encryption**
- **Postman for API testing**

## Getting Started

### Prerequisites

Make sure you have the following installed on your local machine:

- Java 17
- Maven
- Postman (or another API testing tool)

### Running the Application

1. Clone the repository to your local machine.
2. Navigate to the project directory.
3. Run the following Maven command to start the application:

   ```bash
   mvn spring-boot:run
The application will start on https://localhost:8443/.
In-Memory Users
The project is pre-configured with two users for testing:

Admin user:

Username: admin
Password: adminpass
Role: ADMIN
Regular user:

Username: user
Password: userpass
Role: USER
Endpoints
HTTP Method	URL	Description	Roles
POST	/user/register	Register a new user	Public
POST	/login	Login with username and password	Public
GET	/admin/**	Admin-specific actions	ADMIN only
Registering a User
To register a new user, send a POST request to /user/register with the following JSON body:

json
Copy code
{
  "username": "newuser",
  "password": "password"
}
Logging in
To log in as a user, send a POST request to /login with the following JSON body:

json
Copy code
{
  "username": "user",
  "password": "userpass"
}
Once logged in, the user can access the application endpoints according to their role.

H2 Database Console
The project uses an in-memory H2 database to store user information. You can access the H2 database console at:

bash
Copy code
http://localhost:8080/h2-console
JDBC URL: jdbc:h2:mem:testdb
Username: sa
Password: (Leave blank)
Disabling CSRF
For development and testing purposes, CSRF protection has been disabled in this project. In a production environment, it's strongly recommended to enable CSRF protection.

API Testing with Postman
You can test the API using Postman:

Register a user:

Send a POST request to https://localhost:8443/user/register.
In the body, send a JSON object with username and password.
Login:

Send a POST request to https://localhost:8443/login.
Add your credentials to the request body (username and password).
Access admin routes:

You can access any admin/** routes after logging in as the admin user. For example: GET https://localhost:8443/admin/dashboard.
