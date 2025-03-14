# Airline Management System

A modern microservice-based airline management system built with Spring Boot. This system allows users to manage flights, schedules, users, and ticket bookings through RESTful APIs.

![Java](https://img.shields.io/badge/Java-21-orange)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.4.3-green)
![Maven](https://img.shields.io/badge/Maven-3.8.1-blue)

## Table of Contents

- [Features](#features)
- [Project Structure](#project-structure)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
- [API Documentation](#api-documentation)
- [Data Models](#data-models)
- [Validation](#validation)


## Features

- **Flight Management:** Create and manage flights and their schedules
- **User Management:** Register and manage user accounts
- **Ticket Booking:** Book, view and cancel flight tickets
- **Validation:**  input validation with custom constraints
- **Error Handling:** Centralized exception handling

## Project Structure

The system follows a microservice architecture with three main services:

```
airline-management-system/
├── flight-service/             # Flight management service
├── user-service/               # User management service
└── ticket-service/             # Ticket booking service
```

Each service is independently deployable and has its own:
- Database (H2 in-memory)
- REST controllers
- Business logic
- Data access layer
- Validation rules
- Error handling

## Technologies Used

- **Java 21**
- **Spring Boot 3.4.3**
- **Spring Data JPA**
- **Spring Validation**
- **H2 Database**
- **Lombok**
- **MapStruct**
- **Maven**

## Getting Started

### Prerequisites

- Java 21+
- Maven 3.8+

### Installation

1. Clone the repository:

```bash
git clone https://github.com/yourusername/airline-management-system.git
cd airline-management-system
```

2. Build the project:

```bash
mvn clean install
```

## API Documentation

### Flight Service API

Base URL: `http://localhost:8080/flights`

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Get all flights |
| `/` | POST | Create a new flight |
| `/{id}` | GET | Get flight by ID |
| `/{id}/schedules` | GET | Get schedules for a flight |
| `/schedules/{id}` | GET | Get flight schedule by Id |


### User Service API

Base URL: `http://localhost:8080/users`

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | POST | Create a new user |
| `/{id}` | GET | Get user by ID |

### Ticket Service API

Base URL: `http://localhost:8080/tickets`

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | POST | Create/book a new ticket |
| `/{id}` | GET | Get ticket by ID |
| `/{id}` | DELETE | Cancel a ticket |


## Data Models

### Flight Service

- **Flight:** Represents an airline flight route
- **FlightSchedule:** Represents a specific scheduled occurrence of a flight

### User Service

- **User:** Represents a user account with personal information

### Ticket Service

- **Ticket:** Represents a flight booking for a user

## Validation

The system uses Jakarta Validation with custom constraints:

- **@UniqueFlightNumber:** Ensures flight numbers are unique
- **@ValidDateRange:** Validates arrival time is after departure time
- **@UniqueEmail:** Ensures email addresses are unique
