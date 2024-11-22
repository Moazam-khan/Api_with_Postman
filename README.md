# Api_with_Postman

# Simple Books API

This repository contains notes and examples for working with the Simple Books API.

## API Overview
- **Base URL:** `https://simple-books-api.glitch.me`

### **Endpoints**
1. **API Status**  
   - **GET `/status`**  
     Returns the status of the API.

2. **List of Books**  
   - **GET `/books`**  
     Returns a list of books.  
     - Optional query parameters:
       - `type` (fiction or non-fiction)
       - `limit` (1 to 20)

3. **Single Book Details**  
   - **GET `/books/:bookId`**  
     Retrieve detailed information about a book.

4. **Submit an Order**  
   - **POST `/orders`**  
     - Requires authentication.  
     - **Body:**
       ```json
       {
         "bookId": 1,
         "customerName": "John"
       }
       ```
     - Example response:
       ```json
       {
         "orderId": 123
       }
       ```

### **API Authentication**
To use order-related endpoints, register your API client:  

- **POST `/api-clients/`**  
  **Body:**
  ```json
  {
    "clientName": "Postman",
    "clientEmail": "valentin@example.com"
  }
