Axios is a **JavaScript library** that helps you send and receive data from a server easily. You use it to make **HTTP requests** (like GET, POST, PUT, DELETE) without reloading your webpage. It works in both the **browser** and **Node.js**

### **Axios Response Object**  
Axios always returns a **response object**.  
A typical response from Axios looks like this:

{
  "data": { /* the actual response data from server */ },
  "status": 200,
	  "statusText": "OK",
  "headers": { /* headers info */ },
  "config": { /* axios config */ },
  "request": {}
}

The important part is that Axios wraps your **actual server response** inside a key called `data`.