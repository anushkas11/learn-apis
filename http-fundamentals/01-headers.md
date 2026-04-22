# Common HTTP Headers

HTTP headers are key-value pairs sent in both directions between a client and a server. They play a crucial role in web communication by providing necessary information about the request or response, enhancing security, controlling cache behavior, and improving performance.

## 1. Content-Type
- **Purpose**: Specifies the media type of the resource.
- **Example**: `Content-Type: application/json`

## 2. User-Agent
- **Purpose**: Identifies the application, operating system, and version of the client making the request.
- **Example**: `User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3`

## 3. Accept
- **Purpose**: Informs the server about the types of media that the client can process.
- **Example**: `Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8`

## 4. Authorization
- **Purpose**: Contains credentials for authenticating a user agent with a server.
- **Example**: `Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=` (where the value is a Base64-encoded string)

## 5. Cache-Control
- **Purpose**: Directs caching mechanisms on how to store and reuse responses.
- **Example**: `Cache-Control: no-cache`

## 6. Cookie
- **Purpose**: Sent by the client to the server; contains stored HTTP cookies.
- **Example**: `Cookie: sessionId=abc123; token=xyz456`

## 7. Referer
- **Purpose**: Indicates the URL of the resource that linked to the resource being requested.
- **Example**: `Referer: https://www.example.com/previous-page`

## 8. Host
- **Purpose**: Specifies the domain name of the server and the TCP port number on which the server is listening.
- **Example**: `Host: www.example.com`

## 9. Accept-Language
- **Purpose**: Indicates the language preferred by the client.
- **Example**: `Accept-Language: en-US,en;q=0.5`

## 10. Connection
- **Purpose**: Controls whether the network connection stays open after the current transaction finishes.
- **Example**: `Connection: keep-alive`

These headers contribute to efficient data transfer and improve user experience across the web.