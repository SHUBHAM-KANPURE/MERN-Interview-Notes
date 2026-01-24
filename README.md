# Welcome To The MERN Interview Channel

## -> JavaScript (Core + Advanced)

### Q.1 Difference between var, let, and const

#### 1. var
**Definition:** `var` is a function-scoped variable. It can be re-declared and updated and is hoisted with undefined.

**Example:**
```js
var x = 10;
var x = 20; // allowed
x = 30;     // allowed

console.log(x); // 30
```
---

#### 2. let
**Definition:** `let` is block-scoped. It can be updated but not re-declared in the same scope. Hoisted but not accessible before declaration.

**Example:**
```js
let y = 10;
y = 20;     // allowed
// let y = 30; not allowed in same scope

console.log(y); // 20
```
---

#### 3. const
**Definition:** `const` is block-scoped and cannot be re-declared or updated. Value must be assigned at declaration.

**Example:**
```js
const z = 10;
// z = 20; not allowed

const obj = { name: "Shubham" };
obj.name = "Shivam"; // allowed (object mutation)

```
-------------------------------------------------------------------------------------------------------------------------

### Q.2 Explain hoisting with example
**Definition:** `Hoisting` is JavaScript’s behavior where variable and function declarations are moved to the top of their scope during compilation, before code execution.

**Example:**
```js
console.log(a); // undefined
var a = 10;
```
---
---

## -> Node.js

### Q.1 What is Node.js and why is it fast?
**Definition:** `Node.js` is a JavaScript runtime environment built on Chrome’s V8 engine that allows JavaScript to run outside the browser, mainly on the server side.

-------------------------------------------------------------------------------------------------------------------------

### Q.2 Why is Node.js Fast?
#### 1. V8 Engine
- Compiles JS to machine code
- Very fast execution

#### 2. Non-Blocking I/O
- Async operations
- Doesn’t wait for I/O tasks

#### 3. Event Loop
- Handles multiple requests with single thread

#### 4. No Thread Creation Overhead
- Uses fewer system resources

-------------------------------------------------------------------------------------------------------------------------

### Q.3 Node.js Use Cases
✔ Real-time apps (chat, gaming)
✔ APIs & microservices
✔ Streaming apps
✔ IoT applications

-------------------------------------------------------------------------------------------------------------------------

### Q.4 Explain single-threaded nature of Node
#### 1. What does “Single-Threaded” mean in Node.js?
**Definition:** `Node.js` is single-threaded because it uses one main thread (the event loop) to execute JavaScript code.

#### 2. Then how does Node handle multiple requests?
Node.js is single-threaded but NOT single-tasked.

#### How it works:
- Synchronous JS → runs on main thread
- Async tasks (DB, file, network) → handled by libuv thread pool / OS
- Results → sent back to event loop
- Callback executed when call stack is free

**Example:**
```js
console.log("Start");

setTimeout(() => {
  console.log("Async Task");
}, 0);

console.log("End");
```
#### 3. Why Node.js Uses Single Thread?
✔ Avoids thread-locking & deadlocks
✔ Lightweight & memory efficient
✔ Easier to scale with async I/O

### 4. Limitation
❌ CPU-intensive tasks block the event loop.
✔ Solution:

- Worker Threads
- Child Processes
- Cluster module

-------------------------------------------------------------------------------------------------------------------------

### Q.5 What is event-driven architecture?
**Definition:** `Event-Driven` Architecture (EDA) is a design pattern where the flow of the application is determined by events such as user actions, messages, or system changes.

#### 1. Key Components
-Event Producer
- Event
- Event Consumer

**Example:**
```js
const EventEmitter = require("events");
const emitter = new EventEmitter();

emitter.on("orderPlaced", (orderId) => {
  console.log("Processing order:", orderId);
});

emitter.emit("orderPlaced", 101);
```

#### 2. Real-World Examples
✔ Button click in UI
✔ API request handling
✔ Message queues (Kafka, RabbitMQ)
✔ WebSockets & real-time apps

### 3. Why Node.js Fits EDA Well?
- Non-blocking I/O
- Event loop based
- Highly scalable

### 4. Advantages
✔ Loose coupling
✔ Scalability
✔ Faster response

### 4. Disadvantages
❌ Debugging can be complex
❌ Event flow hard to track

-------------------------------------------------------------------------------------------------------------------------

### Q.6 What are streams?
**Definition:** `Streams` are objects in Node.js that allow you to read or write data in chunks, instead of loading the entire data into memory at once.

#### 1. Types of Streams
- Readable
- Writable
- Duplexों
- Transform

**Example:**
```js
const fs = require("fs");

const stream = fs.createReadStream("file.txt");

stream.on("data", chunk => {
  console.log(chunk.toString());
});
```

#### 2. Why Use Streams?
✔ Handles large files
✔ Low memory usage
✔ Faster processing
✔ Real-time data handling

#### 3. Real-World Use Cases
- File upload/download
- Video streaming
- Data processing pipelines
- API responses

-------------------------------------------------------------------------------------------------------------------------

### Q.6 What is middleware?
-------------------------------------------------------------------------------------------------------------------------

### Q.7 Difference between process.nextTick() and setImmediate()
-------------------------------------------------------------------------------------------------------------------------

### Q.8 How does Node handle multiple requests?
-------------------------------------------------------------------------------------------------------------------------

### Q.9 What is cluster module?
-------------------------------------------------------------------------------------------------------------------------

### Q.10 What is buffer?
-------------------------------------------------------------------------------------------------------------------------

### Q.11 Error handling in Node.js
-------------------------------------------------------------------------------------------------------------------------

## -> Express.js (Node js)

### Q.1 What is Express?
-------------------------------------------------------------------------------------------------------------------------

### Q.2 What is middleware? Types?
-------------------------------------------------------------------------------------------------------------------------

### Q.3 Difference between `req.params`, `req.query`, `req.body`
-------------------------------------------------------------------------------------------------------------------------

### Q.4 How authentication works in Express?
-------------------------------------------------------------------------------------------------------------------------

### Q.5 What is CORS?
-------------------------------------------------------------------------------------------------------------------------

### Q.6 How do you secure APIs?
-------------------------------------------------------------------------------------------------------------------------

### Q.7 How do you handle errors globally?
-------------------------------------------------------------------------------------------------------------------------

### Q.8 Express vs Fastify
-------------------------------------------------------------------------------------------------------------------------

### Q.9 How routing works internally?
-------------------------------------------------------------------------------------------------------------------------

### Q.10 How to validate request data?
-------------------------------------------------------------------------------------------------------------------------

## -> MongoDB (Node js)

### Q.1 Difference between SQL & NoSQL
-------------------------------------------------------------------------------------------------------------------------

### Q.2 What is a document?
-------------------------------------------------------------------------------------------------------------------------

### Q.3 Indexes — types & usage
-------------------------------------------------------------------------------------------------------------------------

### Q.4 Aggregation pipeline
-------------------------------------------------------------------------------------------------------------------------

### Q.5 Difference between findOne() and find()
-------------------------------------------------------------------------------------------------------------------------

### Q.6 What is ObjectId?
-------------------------------------------------------------------------------------------------------------------------

### Q.7 Embedded vs referenced documents
-------------------------------------------------------------------------------------------------------------------------

### Q.8 Transactions in MongoDB
-------------------------------------------------------------------------------------------------------------------------

### Q.9 What is populate() in Mongoose?
-------------------------------------------------------------------------------------------------------------------------

### Q.10 How to optimize queries?
-------------------------------------------------------------------------------------------------------------------------
