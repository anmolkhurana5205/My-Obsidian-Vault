A **middleware** in Express is **a function that runs between the request coming in (from the client) and the response going out (from the server)**.

It can:

- Look at the incoming request (`req`)
    
- Modify the request or response
    
- Run some code (like logging, authentication, validation)
    
- Decide whether to pass control to the next middleware or end the response
---
### Syntax of Middleware

function middlewareName(req, res, next) {   
	// Your logic here   
	console.log('Middleware is running');   
	next(); // pass control to the next middleware/route 
}

app.use([logger,  authorize]);
// order matters in the above one

---
### Types of Middleware

1. **Application-level middleware**
    
    - Defined using `app.use()` or `app.get()` etc.
        
2. **Router-level middleware**
    
    - Middleware attached only to a specific router.
        
3. **Built-in middleware**
    
    - Like `express.json()` or `express.static()`.
        
4. **Error-handling middleware**
    
    - Middleware with **4 parameters**: `(err, req, res, next)` for error handling.
        
5. **Third-party middleware**
    
    - Like `morgan` (logging), `cors` (cross-origin resource sharing), etc.
        

---
### Simple Analogy

Think of middleware like **security checks at an airport**:

1. You arrive (request comes in).
    
2. Security checks your passport (middleware runs).
    
3. If everything is fine, you go to boarding (next middleware/route).
    
4. If there’s a problem, you’re stopped (middleware sends response).