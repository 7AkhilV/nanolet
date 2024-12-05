# **Nanolet**

**Nanolet** is a lightweight and minimal Node.js framework designed to simplify the creation of HTTP servers. It provides an intuitive API for routing, middleware management, and response handling, making it an ideal choice for developers who want to build web servers with ease.

---

## **Features**
- 🌀 **Minimal and Lightweight**: Focused on simplicity and efficiency.
- 🔗 **Middleware Support**: Chain middleware functions for cleaner and modular code.
- 🚀 **Customizable Routing**: Easily define routes for your application.
- 📂 **File Streaming**: Send files with ease using the built-in `res.sendFile`.
- 🌐 **JSON Responses**: Send JSON responses with a single method.
- 📦 **Plug-and-Play**: Start using Nanolet with minimal setup.

---

## **Installation**
To install Nanolet, run:

```bash
npm install nanolet
```

---

## **Getting Started**
Here’s how to get started with Nanolet:

### **Basic Usage**
```javascript
const Nanolet = require("nanolet");

const server = new Nanolet();

server.route("get", "/", (req, res) => {
  res.json({ message: "Welcome to Nanolet!" });
});

server.route("get", "/hello", (req, res) => {
  res.status(200).json({ greeting: "Hello, World!" });
});

server.listen(3000, () => {
  console.log("Nanolet server running on http://localhost:3000");
});
```

### **Middleware**
You can use `beforeEach` to add middleware that runs before your routes:

```javascript
server.beforeEach((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});
```

### **File Streaming**
Send a file to the client using `res.sendFile`:

```javascript
server.route("get", "/file", (req, res) => {
  res.sendFile("./path/to/file.txt", "text/plain");
});
```

---

## **API Reference**

### `Nanolet.route(method, path, callback)`
- Define a route with a specific HTTP method and path.
- **Parameters**:
  - `method` _(string)_: The HTTP method (e.g., `"get"`, `"post"`).
  - `path` _(string)_: The route path (e.g., `"/"`, `"/api"`).
  - `callback` _(function)_: The function to handle the route, with `(req, res)`.

---

### `Nanolet.beforeEach(callback)`
- Add middleware to execute before all routes.
- **Parameters**:
  - `callback` _(function)_: The middleware function, with `(req, res, next)`.

---

### `res.sendFile(path, mimeType)`
- Send a file to the client.
- **Parameters**:
  - `path` _(string)_: Path to the file.
  - `mimeType` _(string)_: MIME type of the file (e.g., `"text/plain"`).

---

### `res.status(code)`
- Set the HTTP status code for the response.
- **Parameters**:
  - `code` _(number)_: The HTTP status code.

---

### `res.json(data)`
- Send a JSON response.
- **Parameters**:
  - `data` _(object)_: The JSON data to send.

---

## **Example Application**
```javascript
const Nanolet = require("nanolet");

const server = new Nanolet();

server.beforeEach((req, res, next) => {
  console.log(`Request received: ${req.method} ${req.url}`);
  next();
});

server.route("get", "/", (req, res) => {
  res.json({ message: "Hello, Nanolet!" });
});

server.route("post", "/data", (req, res) => {
  res.status(201).json({ success: true, data: "Your data has been saved!" });
});

server.route("get", "/file", (req, res) => {
  res.sendFile("./example.txt", "text/plain");
});

server.listen(3000, () => {
  console.log("Server running at http://localhost:3000");
});
```

---

## **Contributing**
Contributions are welcome! If you’d like to contribute:
1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Submit a pull request with a detailed description of your changes.

---

## **License**
This project is licensed under the **MIT License**. See the [LICENSE](./LICENSE) file for details.

---

## **Author**
Created with ❤️ by **Akhil V**.  
Feel free to reach out on [GitHub](https://github.com/7AkhilV) for any questions or feedback.
