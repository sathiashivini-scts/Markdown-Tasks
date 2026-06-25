# Food Delivery Application API Documentation

This documentation describes the APIs used to manage customer accounts in a food delivery application.

---

# 1. Customer Registration API

### Endpoint Details

| Method | Endpoint | Purpose |
|---------|----------|---------|
| POST | /api/customers/register | Creates a new customer account |

### Request Headers

- Content-Type: application/json

### Request Body

```json
{
  "full_name": "Sathiasree S",
  "phone_number": "9876543210",
  "email": "sathiasree@gmail.com",
  "password": "Food@123"
}
```

### Sample Response

```json
{
  "message": "Customer account created successfully",
  "customer_id": 5501,
  "status": "Active"
}
```

### Error Responses

- 400 Bad Request
  - Missing required fields
  - Email already registered

- 500 Internal Server Error
  - Server unavailable

---

# 2. Customer Login API

### Endpoint Details

| Method | Endpoint | Purpose |
|---------|----------|---------|
| POST | /api/customers/login | Allows customers to access their account |

### Request Headers

- Content-Type: application/json

### Request Body

```json
{
  "email": "sathiasree@gmail.com",
  "password": "Food@123"
}
```

### Sample Response

```json
{
  "message": "Login successful",
  "access_token": "xyz123abc456token"
}
```

### Error Responses

- 401 Unauthorized
  - Incorrect password
  - Customer account not found

---

# 3. Get Customer Profile API

### Endpoint Details

| Method | Endpoint | Purpose |
|---------|----------|---------|
| GET | /api/customers/{customer_id} | Retrieves customer profile details |

### Request Headers

- Authorization: Bearer Access Token

### Sample Response

```json
{
  "customer_id": 5501,
  "full_name": "Sathiasree S",
  "email": "sathiasree@gmail.com",
  "phone_number": "9876543210",
  "membership": "Gold"
}
```

### Error Responses

- 403 Forbidden
  - Invalid access token

- 404 Not Found
  - Customer does not exist