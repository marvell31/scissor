**Scissor API Documentation**

---

**Introduction**

Scissor is a URL shortening service that allows users to create shortened versions of URLs, generate QR codes for easy access, and track visit analytics. This API documentation provides comprehensive details on how to interact with the Scissor backend services.

- **Backend URL**: [https://scissor-mbob.onrender.com](https://scissor-mbob.onrender.com)

---

**Authentication**

The Scissor API uses JWT (JSON Web Tokens) for authentication. Users need to register and login to obtain an access token, which should be included in the header of authenticated requests.

---

**Endpoints**

1. **Register**
   - **URL**: `/register`
   - **Method**: `POST`
   - **Description**: Register a new user.
   - **Request Body**:
     ```json
     {
       "fname": "string",
       "surname": "string",
       "email": "string",
       "pwd": "string",
       "cpwd": "string"
     }
     ```
   - **Response**:
     ```json
     {
       "fname": "string",
       "surname": "string",
       "email": "string",
       "token": "string"
     }
     ```

2. **Login**
   - **URL**: `/login`
   - **Method**: `POST`
   - **Description**: Authenticate user and get access token.
   - **Request Body**:
     ```json
     {
       "email": "string",
       "pwd": "string"
     }
     ```
   - **Response**:
     ```json
     {
       "access_token": "string",
       "token_type": "bearer",
       "user": {
         "id": "integer",
         "fname": "string",
         "surname": "string",
         "email": "string"
       }
     }
     ```

3. **Shorten URL**
   - **URL**: `/shorten-url`
   - **Method**: `POST`
   - **Description**: Create a shortened URL.
   - **Request Body**:
     ```json
     {
       "original_url": "string",
       "id": "integer"
     }
     ```
   - **Response**:
     ```json
     {
       "original_url": "string",
       "shortened_url": "string",
       "qr_code_image": "string",
       "user_id": "integer"
     }
     ```

4. **Redirect to Original URL**
   - **URL**: `/{short_url}`
   - **Method**: `GET`
   - **Description**: Redirect to the original URL associated with the shortened URL.
   - **Response**: Redirect to the original URL.

5. **Get QR Code**
   - **URL**: `/get-qr/{short_url}`
   - **Method**: `GET`
   - **Description**: Get the QR code image associated with the shortened URL.
   - **Response**: QR code image file.

6. **Get Original URL**
   - **URL**: `/original-url/{short_url}`
   - **Method**: `GET`
   - **Description**: Get the original URL associated with the shortened URL.
   - **Response**:
     ```json
     {
       "shortened_url": "string",
       "original_url": "string"
     }
     ```

7. **Get Analytics**
   - **URL**: `/analytics/{short_url}`
   - **Method**: `GET`
   - **Description**: Get analytics data for a shortened URL.
   - **Response**:
     ```json
     {
       "original_url": "string",
       "short_url": "string",
       "visit_times": ["datetime"],
       "visit_count": "integer"
     }
     ```

8. **Get Link History**
   - **URL**: `/link-history/{id}`
   - **Method**: `GET`
   - **Description**: Get the link history for a specific user.
   - **Response**:
     ```json
     [
       {
         "id": "integer",
         "original_url": "string",
         "shortened_url": "string",
         "visit_count": "integer",
         "times_visited": ["datetime"]
       }
     ]
     ```

---

**Rate Limiting**

Certain endpoints are rate-limited to prevent abuse. If the rate limit is exceeded, the API will respond with a `429 Too Many Requests` status code.

---

**Frontend Integration**

Scissor's frontend is a React app deployed on [https://scissor-teal.vercel.app](https://scissor-teal.vercel.app). The frontend application can interact with the Scissor backend API to provide users with URL shortening, QR code generation, and analytics features.

---

**Conclusion**

This documentation provides a detailed overview of the Scissor backend API, including authentication, endpoints, request/response formats, rate limiting, and integration with the frontend application. Developers can use this documentation to effectively utilize Scissor's URL shortening and management features.
