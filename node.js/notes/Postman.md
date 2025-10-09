Postman is a software application (desktop & web) used by developers and testers to send HTTP requests to APIs, inspect responses, and debug issues. Instead of writing code to test APIs, you can quickly use Postman’s GUI to send requests (like GET, POST, PUT, DELETE) and see the response instantly.
### 🔹 Core Features

1. **Send Requests Easily**
    
    - Choose method (GET, POST, PUT, DELETE, PATCH, etc.)
        
    - Enter URL, headers, body, and params.
        
    - Click **Send** and see response immediately.
        
2. **Collections**
    
    - You can group API requests into “collections” (like folders) to organize your API testing.
        
3. **Environment Variables**
    
    - You can set variables (like base URLs, tokens) and easily switch between environments (e.g., dev, staging, production).
        
4. **Authentication Testing**
    
    - Supports multiple auth methods: API keys, OAuth, JWT, Basic Auth, etc.
        
5. **Pre-request & Tests Scripts**
    
    - You can write JavaScript snippets that run **before a request** (set headers dynamically) or **after a request** (validate responses).
        
6. **Mock Servers**
    
    - Simulate API endpoints for frontend devs when backend is not ready.
        
7. **Automation**
    
    - Postman lets you run API test scripts and integrate them in CI/CD pipelines.
        
8. **Monitoring**
    
    - Automatically schedule API tests to ensure endpoints are up and running.
        

---

### 🔹 How It Works (Simple Flow)

1. Open Postman.
    
2. Create a request → Choose HTTP method (GET, POST, etc.).
    
3. Add URL → Example: `https://api.example.com/users`
    
4. Add **params, headers, and body** (if needed).
    
5. Hit **Send** → See API response (status code, JSON data, time, size).
    
6. Save this request in a **collection** for future use.