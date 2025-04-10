# Backend API Documentation

## Register User
Register a new user in the system.

**Endpoint:** `/users/register`
**Method:** `POST`

### Request Body
```json
{
    "fullname": {
        "firstname": "string", // minimum 3 characters
        "lastname": "string"   // optional, minimum 3 characters if provided
    },
    "email": "string",        // valid email format
    "password": "string"      // minimum 6 characters
}
```

### Response

#### Success Response (201 Created)
```json
{
    "token": "JWT_TOKEN_STRING",
    "user": {
        "fullname": {
            "firstname": "John",
            "lastname": "Doe"
        },
        "email": "john@example.com",
        "_id": "user_id"
    }
}
```

#### Error Responses

**400 Bad Request**
- When validation fails
```json
{
    "errors": [
        {
            "msg": "First name must be at least 3 characters long",
            "param": "fullname.firstname",
            "location": "body"
        }
    ]
}
```

- When user already exists
```json
{
    "message": "User already exist"
}
```

### Required Fields
- `fullname.firstname` (String, min length: 3)
- `email` (String, valid email format)
- `password` (String, min length: 6)

### Optional Fields
- `fullname.lastname` (String, min length: 3 if provided)
