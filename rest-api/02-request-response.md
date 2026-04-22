# Request and Response in REST API

In RESTful APIs, request and response structures play crucial roles in how clients and servers communicate. Understanding the components of request and response can help you effectively design, implement, and utilize REST APIs. This document outlines the main components: headers, query parameters, path parameters, request body, and response structure.

## 1. Headers
HTTP headers are key-value pairs sent in an HTTP request or response. They provide essential information about the request or response, such as content type, authentication tokens, and more.

### Common Headers
- **Content-Type**: Indicates the media type of the resource (e.g., `application/json`, `application/xml`).
- **Authorization**: Used for sending authentication credentials (e.g., `Bearer <token>`).

### Example:
```
GET /api/users HTTP/1.1
Host: example.com
Authorization: Bearer token123
Content-Type: application/json
```

## 2. Query Parameters
Query parameters are used to filter or modify the results returned by an API. They are specified in the URL after the `?` character and are usually presented in key-value pairs.

### Example:
```
GET /api/users?age=25&active=true
```
In this example, the request is filtered to get users who are 25 years old and active.

## 3. Path Parameters
Path parameters are placeholders in the URL that allow you to pass data to an API endpoint dynamically. They are typically used to identify a specific resource.

### Example:
```
GET /api/users/{userId}
```
If you want to fetch the user with ID 123, the request would look like:
```
GET /api/users/123
```

## 4. Request Body
The request body is where you send data to the server for operations like creating or updating a resource. This is usually used with methods like POST, PUT, or PATCH.

### Example:
```
POST /api/users
Content-Type: application/json

{
  "name": "John Doe",
  "age": 30,
  "active": true
}
```
In this example, the request body contains a JSON object representing a new user.

## 5. Response Structure
The server responds to a client's request with a structured response, typically including a status code, headers, and a body.

### Example:
```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 123,
  "name": "John Doe",
  "age": 30,
  "active": true
}
```
In this case, the response body contains a JSON object with the details of the requested user.

## Conclusion
Understanding these components is essential for working with REST APIs efficiently. They help in constructing valid requests, interpreting responses, and troubleshooting issues that may arise during API interactions.