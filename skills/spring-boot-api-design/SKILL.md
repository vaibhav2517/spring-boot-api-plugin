---

name: spring-boot-api-design

description: Design production-quality REST APIs using Java and Spring Boot, including resources, endpoints, DTOs, validation, HTTP status codes, error handling, pagination, and API contracts.

---

# Spring Boot API Design

Use this skill when designing REST APIs for Java Spring Boot applications.

## Design process

When designing an API:

1. Understand the business requirement.

2. Identify the main resources.

3. Define REST endpoints.

4. Select appropriate HTTP methods.

5. Define request DTOs.

6. Define response DTOs.

7. Define validation rules.

8. Define HTTP status codes.

9. Define error handling.


## REST conventions

Prefer resource-oriented URLs.

Examples:

GET /customers

GET /customers/{id}

POST /customers

PUT /customers/{id}

PATCH /customers/{id}

DELETE /customers/{id}

Avoid action-oriented URLs such as:

POST /createCustomer

POST /deleteCustomer

unless the operation represents a genuine domain action.

## DTOs

Do not expose JPA entities directly through REST APIs.

Prefer a separation such as:

Controller

    ↓

Request DTO

    ↓

Service

    ↓

Repository

    ↓

Response DTO

## Validation

Validate incoming requests at the API boundary.

Use Jakarta Bean Validation where appropriate, such as:

@NotNull

@NotBlank

@Size

@Email

## Error handling

Use consistent error responses.

Prefer centralized exception handling using:

@RestControllerAdvice

Avoid repetitive exception handling in individual controllers.

## HTTP status codes

Use status codes deliberately.

Common examples:

200 OK

201 Created

204 No Content

400 Bad Request

401 Unauthorized

403 Forbidden

404 Not Found

409 Conflict

500 Internal Server Error



## API documentation

For shared or public APIs, define an OpenAPI contract containing:

- endpoint

- HTTP method

- parameters

- request body

- response body

- status codes

- validation errors

- authentication requirements

## Before implementation

Do not immediately write implementation code.

First determine:

1. What is the resource?

2. What endpoints are required?

3. What are the request models?

4. What are the response models?

5. What validation is required?

6. What status codes are expected?

7. How are errors represented?


Then produce the API design.