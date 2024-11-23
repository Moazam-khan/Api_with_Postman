# Simple Books API

This repository provides an overview of the Simple Books API, which allows users to view books, place orders, and manage orders with authentication.

## API Overview
- **Base URL:** `https://simple-books-api.glitch.me`

---

## Endpoints

### 1. API Status
- **GET `/status`**  
  - Returns the status of the API.  
  - Example response:
    ```json
    {
      "status": "OK"
    }
    ```

---

### 2. List of Books
- **GET `/books`**  
  - Retrieves a list of books.
  - **Optional Query Parameters**:
    - `type`: Filter books by type (`fiction` or `non-fiction`).
    - `limit`: Limit the number of results (1 to 20).  
  - Example request:
    ```
    GET /books?type=fiction&limit=5
    ```
  - Example response:
    ```json
    [
      {
        "id": 1,
        "name": "The Great Book",
        "type": "fiction"
      },
      ...
    ]
    ```

---

### 3. Single Book Details
- **GET `/books/:bookId`**  
  - Retrieves detailed information about a specific book.
  - Example request:
    ```
    GET /books/1
    ```
  - Example response:
    ```json
    {
      "id": 1,
      "name": "The Great Book",
      "type": "fiction",
      "available": true
    }
    ```

---

### 4. Submit an Order
- **POST `/orders`**  
  - Submits a new order.  
  - **Authentication Required**: Bearer token in the header.
  - **Request Body** (JSON format):
    ```json
    {
      "bookId": 1,
      "customerName": "John"
    }
    ```
  - Example request:
    ```
    POST /orders
    Authorization: Bearer <YOUR TOKEN>
    ```
  - Example response:
    ```json
    {
      "orderId": 123
    }
    ```

---

### 5. Get All Orders
- **GET `/orders`**  
  - Retrieves all orders.  
  - **Authentication Required**: Bearer token in the header.

---

### 6. Get a Single Order
- **GET `/orders/:orderId`**  
  - Retrieves details about a specific order.  
  - **Authentication Required**: Bearer token in the header.

---

### 7. Update an Order
- **PATCH `/orders/:orderId`**  
  - Updates an existing order.  
  - **Authentication Required**: Bearer token in the header.
  - **Request Body** (JSON format):
    ```json
    {
      "customerName": "John"
    }
    ```
  - Example request:
    ```
    PATCH /orders/123
    Authorization: Bearer <YOUR TOKEN>
    ```

---

### 8. Delete an Order
- **DELETE `/orders/:orderId`**  
  - Deletes an existing order.  
  - **Authentication Required**: Bearer token in the header.

---

### 9. API Client Registration
- **POST `/api-clients/`**  
  - Registers your API client to use order-related endpoints.
  - **Request Body** (JSON format):
    ```json
    {
      "clientName": "Postman",
      "clientEmail": "example@example.com"
    }
    ```
  - Example response:
    ```json
    {
      "accessToken": "your-access-token"
    }
    ```
  - **Note**: The access token is valid for 7 days.

---

## Postman Concepts

### 1. Variables
- **Local Variables**: Temporary variables used within a single request or collection run.
- **Global Variables**: Available across all collections and environments.
- **Collection Variables**: Scoped to the collection, making them reusable across multiple requests.
- **Environment Variables**: Scoped to a specific environment, useful for dynamic base URLs or tokens.

### 2. Authorization
- Postman supports various authentication mechanisms:
  - **Bearer Token**: Used for Simple Books API.
  - Example:
    ```
    Authorization: Bearer <YOUR_TOKEN>
    ```
- Set this in the **Authorization** tab for requests requiring authentication.

### 3. Headers
- Used to include additional information, such as `Content-Type` or `Authorization`.
  - Example:
    ```
    Content-Type: application/json
    Authorization: Bearer <YOUR_TOKEN>
    ```

### 4. Body
- Defines the data sent with POST, PUT, or PATCH requests.
- Supported formats:
  - **Raw (JSON)**:
    ```json
    {
      "bookId": 1,
      "customerName": "John"
    }
    ```
  - **Form-data** and **x-www-form-urlencoded**.

### 5. Params and Path Variables
- **Params**: Add query parameters to the URL.
  - Example: `GET /books?type=fiction&limit=5`
- **Path Variables**: Dynamic segments in the endpoint.
  - Example: `/books/:bookId` -> `/books/1`.

### 6. Monitors
- Automate testing and monitor API performance at regular intervals.

---

### Errors and Solutions
- **Status 409 (Conflict)**:  
  - "API client already registered."
  - Solution: Change `clientEmail` and `clientName` to unique values.

---

## Example Collection Structure for Postman
- **Folder: Simple Books API**
  - GET `/status`
  - GET `/books`
  - GET `/books/:bookId`
  - POST `/orders`
  - GET `/orders`
  - PATCH `/orders/:orderId`
  - DELETE `/orders/:orderId`
  - POST `/api-clients`
