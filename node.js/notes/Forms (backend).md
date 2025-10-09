### How to manage data sent by forms

==app.use(express.urlencoded({extended: false}));==

- Tells Express to **parse incoming URL-encoded data** (data sent from forms) and put it into `req.body`
- Without it, `req.body` would be `undefined` when you try to read form inputs.
#### The `extended` Option:

- `extended: false` → Uses the **querystring** library to parse data.
    
    - Can only handle simple key-value pairs (like `username=anmol&password=123`).
        
- `extended: true` → Uses the **qs** library, which supports **nested objects**.
    
    - Example: `user[name]=Anmol&user[age]=21` would become `{ user: { name: 'Anmol', age: '21' } }`.