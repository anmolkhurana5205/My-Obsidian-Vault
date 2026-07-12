### Importing Them
```
import { NextRequest, NextResponse } from 'next/server';
```

### NextResponse.json(payload, { status })
- It is a utility method provided by next.js to construct and return a json response from a route handler or middleware.
#### Components:
- payload - This is the which you want to send in the response body. It must be js object that can be serialized into json.
```
const data = { message: "Success", user: { id: 1, name: "John Doe" } };
```
- { status } - This is the optional object that allow you to configure the response. 
	1. 200 for OK
	2. 201 for Created
	3. 400 for Not Found
	4. 500 for Internal Server Error

### How it works
- It automatically sets the content-type header to application/json
- It serializes the payload object into a strict json string body.
- If status object is omitted then it by default sets to 200 OK
- .json() method is here for developer convenience like previously developer manually need to create the object not it is automatically done by this methos. (everything like status, headers, everything gets automatically setted) 