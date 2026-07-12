### What is Express.js?

- **Express.js** is a **minimal and flexible Node.js web framework** used to build **web applications and APIs**.
- It simplifies handling **HTTP requests, responses, routing, middleware, and server configuration**.
- Think of it as a lightweight layer on top of Node’s built-in `http` module, making backend development faster.
### 1. `app.get(path, callback)`

- Handles **GET requests** (used to fetch data).
    
- Runs the callback when a client makes a GET request to the specified path.
### 2. `app.post(path, callback)`

- Handles **POST requests** (used to send data, like forms or JSON).
    
- Typically used for creating new resources.
### 3. `app.put(path, callback)`

- Handles **PUT requests** (used to completely update a resource).
### 4. `app.delete(path, callback)`

- Handles **DELETE requests** (used to delete a resource).
### 5. `app.all(path, callback)`

- Matches **all HTTP methods** (GET, POST, PUT, DELETE, etc.) for a path.
    
- Commonly used for **catch-all routes** (like 404 pages).
### 6. `app.use(middleware)`

- Used to apply **middleware** to every incoming request or to specific routes.
    
- Middleware is code that runs **before** route handlers.
ex -> app.use(express.json()); // Built-in middleware to parse JSON
ex -> app.use('/api', myLogger);
### 7. `app.listen(port, callback)`

- Starts the Express **server** on a given port and listens for requests.

