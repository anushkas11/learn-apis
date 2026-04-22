# HTTP Fundamentals

## HTTP Methods

- **GET**: Retrieves data from a server. Typically used to request data from a specified resource.
- **POST**: Sends data to the server. Used to create a new resource.
- **PUT**: Updates an existing resource or creates a new one if it doesn't exist.
- **PATCH**: Partially updates an existing resource.
- **DELETE**: Removes a specified resource from the server.

## HTTP Status Codes

- **2xx (Successful)**: The request was successfully received, understood, and accepted. Examples include:
  - 200 OK
  - 201 Created

- **3xx (Redirection)**: Further action needs to be taken to complete the request. Examples include:
  - 301 Moved Permanently
  - 302 Found

- **4xx (Client Error)**: The request contains bad syntax or cannot be fulfilled. Examples include:
  - 400 Bad Request
  - 404 Not Found

- **5xx (Server Error)**: The server failed to fulfill a valid request. Examples include:
  - 500 Internal Server Error
  - 503 Service Unavailable

## Request/Response Structure

- **Request Structure**:
  - **Method**: The HTTP method (e.g., GET, POST)
  - **URL**: The resource location
  - **Headers**: Metadata for the request (e.g., Content-Type)
  - **Body**: The data sent with the request (for POST and PUT)

- **Response Structure**:
  - **Status Code**: Indicates the result of the request (e.g., 200, 404)
  - **Headers**: Metadata for the response
  - **Body**: The data returned from the server (if applicable)