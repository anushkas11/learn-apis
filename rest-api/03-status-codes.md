# Comprehensive Guide to HTTP Status Codes

HTTP status codes are three-digit numbers returned by the server to indicate the outcome of a request. They are categorized into five classes:

## 1xx: Informational
- **100 Continue**: Indicates that the initial part of a request has been received and has not yet been rejected by the server.
- **101 Switching Protocols**: The server will switch protocols as requested by the client.

## 2xx: Successful
- **200 OK**: The request has succeeded.
- **201 Created**: The request has succeeded and a new resource has been created.
- **204 No Content**: The server successfully processed the request, but is not returning any content.

## 3xx: Redirection
- **301 Moved Permanently**: The requested resource has been permanently moved to a new URL.
- **302 Found**: The requested resource is temporarily located at a different URL.
- **304 Not Modified**: Indicates that the resource has not been modified since the last request.

## 4xx: Client Errors
- **400 Bad Request**: The server could not understand the request due to invalid syntax.
- **401 Unauthorized**: The client must authenticate itself to get the requested response.
- **403 Forbidden**: The server understood the request, but it refuses to authorize it.
- **404 Not Found**: The server can not find the requested resource.

## 5xx: Server Errors
- **500 Internal Server Error**: The server encountered a situation it doesn't know how to handle.
- **502 Bad Gateway**: The server was acting as a gateway and received an invalid response from the upstream server.
- **503 Service Unavailable**: The server is not ready to handle the request, often due to maintenance.

## When to Use These Codes
Each status code should be used according to the specific condition of the request. For example:
- Use **200** for successful GET requests.
- Use **201** when a resource is created after a POST request.
- Use **404** if the requested resource does not exist.

Make sure to choose appropriate status codes for your API responses to help clients understand the result of their requests effectively!