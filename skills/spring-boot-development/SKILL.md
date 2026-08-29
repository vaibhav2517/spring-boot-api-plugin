---
name: spring-boot-development
description: Implement production-quality Java Spring Boot REST APIs using controllers, services, repositories, DTOs, validation, exception handling, and appropriate Spring Boot patterns.
---

# Spring Boot Development

Use this skill when implementing REST APIs with Java and Spring Boot.

## Architecture

Prefer a layered architecture:

Controller
    ↓
Service
    ↓
Repository
    ↓
Database

Use DTOs at the API boundary rather than exposing persistence entities directly.

## Controllers

Controllers should:

- Handle HTTP requests.
- Validate incoming request data.
- Delegate business logic to services.
- Return appropriate HTTP responses.
- Avoid containing business logic.

Prefer:

@RestController

and appropriate request mapping annotations.

## Services

Services should contain business logic.

Prefer:

@Service

Controllers should not contain substantial business logic.

## Repositories

Use Spring Data repositories where appropriate.

For example:

@Repository

or Spring Data interfaces such as:

JpaRepository

Do not put business logic into repositories.

## DTOs

Use separate request and response DTOs.

Example structure:

CustomerCreateRequest
CustomerUpdateRequest
CustomerResponse

Do not expose JPA entities directly from REST endpoints unless there is a deliberate reason to do so.

## Validation

Use Jakarta Bean Validation.

Examples:

@NotNull
@NotBlank
@Email
@Size
@Positive

Use @Valid or @Validated where appropriate.

## Exception handling

Prefer centralized exception handling.

Use:

@RestControllerAdvice

Create consistent API error responses.

Handle common cases such as:

- Resource not found
- Validation failure
- Duplicate resource
- Invalid request
- Unauthorized access
- Forbidden access

## HTTP responses

Use appropriate status codes.

Examples:

201 Created
200 OK
204 No Content
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict

## Transactions

Use @Transactional at the service layer when transaction boundaries are required.

Avoid unnecessary transactions around read-only operations.

## Dependency injection

Prefer constructor injection.

Avoid field injection.

Example:

public CustomerService(CustomerRepository repository) {
    this.repository = repository;
}

## Implementation workflow

Before writing code:

1. Understand the API contract.
2. Identify domain objects.
3. Define request and response DTOs.
4. Define validation.
5. Define repository requirements.
6. Define service operations.
7. Define controller endpoints.
8. Define exception handling.
9. Consider transaction boundaries.
10. Consider security.

## Code quality

Prefer:

- Small focused classes
- Constructor injection
- Clear naming
- Immutable DTOs where appropriate
- Consistent exception handling
- Meaningful HTTP status codes
- Testable service logic

Avoid:

- Business logic inside controllers
- Direct entity exposure
- Field injection
- Large monolithic services
- Catching generic Exception unnecessarily
- Duplicated validation logic