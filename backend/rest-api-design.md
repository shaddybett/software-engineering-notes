# REST API Design

REST (Representational State Transfer) is an architectural style for designing networked applications using HTTP methods and stateless communication.

## Core Principles

- **Stateless**: Each request contains all necessary information
- **Resource-based**: URLs represent resources, not actions
- **HTTP Methods**: Use appropriate verbs for operations
- **Uniform Interface**: Consistent patterns across endpoints

## HTTP Methods

| Method | Purpose                 | Idempotent |
| ------ | ----------------------- | ---------- |
| GET    | Retrieve resource       | Yes        |
| POST   | Create resource         | No         |
| PUT    | Update/replace resource | Yes        |
| PATCH  | Partial update          | No         |
| DELETE | Remove resource         | Yes        |

## URL Design

```
✅ Good:
GET    /api/users           # Get all users
GET    /api/users/123       # Get user 123
POST   /api/users           # Create user
PUT    /api/users/123       # Update user 123
DELETE /api/users/123       # Delete user 123

❌ Avoid:
GET /api/getUsers
POST /api/createUser
GET /api/users/delete/123
```

## Response Status Codes

- `200 OK` - Successful GET/PUT/PATCH
- `201 Created` - Successful POST
- `204 No Content` - Successful DELETE
- `400 Bad Request` - Invalid input
- `401 Unauthorized` - Authentication required
- `404 Not Found` - Resource doesn't exist
- `500 Internal Server Error` - Server failure

## Best Practices

- Use nouns for resources, not verbs
- Version your API (`/api/v1/users`)
- Support filtering, sorting, pagination
- Return consistent error response format
- Use HTTPS in production
- Document with OpenAPI/Swagger
