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
-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------

## -> React.js

### Q.1 What is virtual DOM?
**Definition:** `Virtual DOM` is a lightweight in-memory representation of the real DOM. React compares the previous and new Virtual DOM and updates only the necessary parts of the real DOM.

**Example:**
```jsx
function Counter() {
    const [count, setCount] = React.useState(0);

    return (
        <button onClick={() => setCount(count + 1)}>
            Count: {count}
        </button>
    );
}
```
-------------------------------------------------------------------------------------------------------------------------

### Q.2 Difference between Virtual DOM vs Real DOM (React)
-------------------------------------------------------------------------------------------------------------------------

### Q.3 What is state?
-------------------------------------------------------------------------------------------------------------------------

### Q.4 What is props?
-------------------------------------------------------------------------------------------------------------------------

### Q.5 componentDidMount and componentWillUnmount
-------------------------------------------------------------------------------------------------------------------------

### Q.6 Difference between controlled & uncontrolled components
#### 1. Controlled Component
**Definition:** A controlled component is a form element whose value is controlled by React state.

**Example:**
```jsx
function Form() {
    const [name, setName] = React.useState("");

    return (
        <input
            value={name}
            onChange={(e) => setName(e.target.value)}
        />
    );
}
```

#### 2. Uncontrolled Component
**Definition:** An uncontrolled component stores its value in the DOM and is accessed using `useRef`.

**Example:**
```jsx
function Form() {
    const inputRef = React.useRef();

    const handleSubmit = () => {
        console.log(inputRef.current.value);
    };

    return (
        <>
            <input ref={inputRef} />
            <button onClick={handleSubmit}>Submit</button>
        </>
    );
}
```

#### Key Difference
- Controlled → React state manages the value.
- Uncontrolled → DOM manages the value.
-------------------------------------------------------------------------------------------------------------------------

### Q.7 Explain React hooks lifecycle
**Definition:** React Hooks handle component lifecycle mainly using `useEffect`.

#### 1. Mount
Runs when the component is rendered for the first time.

```jsx
useEffect(() => {
    console.log("Component mounted");
}, []);
```

#### 2. Update
Runs when a dependency changes.

```jsx
useEffect(() => {
    console.log("Count updated");
}, [count]);
```

#### 3. Unmount
The cleanup function runs when the component is removed.

```jsx
useEffect(() => {
    const id = setInterval(() => console.log("Running"), 1000);

    return () => clearInterval(id);
}, []);
```
-------------------------------------------------------------------------------------------------------------------------

### Q.8 useEffect dependency array — common mistakes
#### Common Mistakes
- Missing a dependency used inside `useEffect`.
- Using `[]` when the effect should run when a value changes.
- Using unstable functions, objects, or arrays as dependencies unnecessarily.
- Forgetting cleanup for timers, subscriptions, or event listeners.

**Example:**
```jsx
useEffect(() => {
    fetchData(userId);
}, [userId]);
```

👉 The effect runs when `userId` changes.
-------------------------------------------------------------------------------------------------------------------------

### Q.9 Difference between useMemo, useCallback, useRef
#### 1. useMemo
Memoizes a calculated value.

```jsx
const total = useMemo(() => calculateTotal(products), [products]);
```

#### 2. useCallback
Memoizes a function reference.

```jsx
const handleClick = useCallback(() => {
    console.log("Clicked");
}, []);
```

#### 3. useRef
Stores a mutable value without causing a re-render. It is also commonly used for DOM access.

```jsx
const inputRef = useRef(null);

inputRef.current?.focus();
```

#### Key Difference
- `useMemo` → memoizes a value.
- `useCallback` → memoizes a function.
- `useRef` → stores a mutable value/reference without re-rendering.
-------------------------------------------------------------------------------------------------------------------------

### Q.10 What is prop drilling? How to avoid it?
**Definition:** `Prop drilling` occurs when props are passed through multiple intermediate components to reach a deeply nested component that actually needs the data.

**Example:**
```jsx
function App() {
    const user = "Shubham";
    return <Parent user={user} />;
}

function Parent({ user }) {
    return <Child user={user} />;
}

function Child({ user }) {
    return <h1>Hello {user}</h1>;
}
```

**How to avoid it:**
- Context API
- Redux or other state management libraries
- Component composition
-------------------------------------------------------------------------------------------------------------------------

### Q.11 Context API vs Redux
#### Context API
`Context API` is a built-in React feature used to share data between components without prop drilling.

```jsx
const UserContext = React.createContext();

function App() {
    return (
        <UserContext.Provider value="Shubham">
            <Profile />
        </UserContext.Provider>
    );
}

function Profile() {
    const user = React.useContext(UserContext);
    return <h1>{user}</h1>;
}
```

#### Redux
`Redux` is a state management library that provides a centralized store for application state.

```jsx
const user = useSelector((state) => state.user);
```

#### Key Difference
- Context API → Simple shared/global data such as theme or auth.
- Redux → Complex application state and business logic, especially in larger applications.
-------------------------------------------------------------------------------------------------------------------------

### Q.12 How do you optimize React performance?
**Definition:** React performance optimization means reducing unnecessary re-renders, expensive calculations, and initial bundle size.

#### Common Techniques
- `React.memo` → prevents unnecessary child re-renders.
- `useMemo` → memoizes expensive calculations.
- `useCallback` → memoizes function references.
- Lazy loading and code splitting → load code when needed.
- Pagination/virtualization → efficiently handle large lists.
- Keep state local when possible.

**Example:**
```jsx
const User = React.memo(({ name }) => {
    return <h2>{name}</h2>;
});

const total = useMemo(() => calculateTotal(products), [products]);
```

👉 Use memoization only when there is an actual performance benefit.
-------------------------------------------------------------------------------------------------------------------------

### Q.13 What are keys in React lists?
-------------------------------------------------------------------------------------------------------------------------

### Q.14 Explain lazy loading & code splitting
-------------------------------------------------------------------------------------------------------------------------

### Q.15 What is HOC?
-------------------------------------------------------------------------------------------------------------------------

### Q.16 Class vs Functional components
-------------------------------------------------------------------------------------------------------------------------

### Q.17 How to handle forms in React?
-------------------------------------------------------------------------------------------------------------------------

### Q.18 What happens when state updates?
-------------------------------------------------------------------------------------------------------------------------

### Q.19 Explain reconciliation
-------------------------------------------------------------------------------------------------------------------------

### Q.20 Controlled vs uncontrolled components

-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------

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

### Q.7 What is middleware?
**Definition:** `Middleware` is a function that runs between the client request and the final response. It can modify the request/response, perform validation or authentication, or pass control using `next()`.

**Example:**
```js
app.use((req, res, next) => {
    console.log("Request received");
    next();
});

app.get("/", (req, res) => {
    res.send("Hello World");
});
```
-------------------------------------------------------------------------------------------------------------------------

### Q.8 Difference between process.nextTick() and setImmediate()
**Definition:** `process.nextTick()` schedules a callback to run after the current operation completes, before the event loop continues. `setImmediate()` schedules a callback for the check phase of the event loop.

**Example:**
```js
console.log("Start");

process.nextTick(() => {
    console.log("nextTick");
});

setImmediate(() => {
    console.log("setImmediate");
});

console.log("End");
```

**Typical output:**
```text
Start
End
nextTick
setImmediate
```

#### Key Difference
- `process.nextTick()` → higher priority; runs before the event loop continues.
- `setImmediate()` → runs in the event loop's check phase.
-------------------------------------------------------------------------------------------------------------------------

### Q.9 How does Node handle multiple requests?
**Definition:** Node.js handles multiple requests using a single-threaded, event-driven, non-blocking I/O model.

#### How it works
- JavaScript code runs on the main thread.
- Async I/O operations are handled by the OS or libuv.
- The event loop continues processing other requests.
- When an async operation completes, its callback is executed.

**Example:**
```js
const http = require("http");

const server = http.createServer((req, res) => {
    setTimeout(() => {
        res.end("Response handled");
    }, 2000);
});

server.listen(3000);
```

👉 While one request is waiting for the async operation, Node can continue handling other requests.
-------------------------------------------------------------------------------------------------------------------------

### Q.10 What is cluster module?
**Definition:** The `cluster` module allows Node.js to create multiple worker processes so an application can use multiple CPU cores and handle more traffic.

**Example:**
```js
const cluster = require("cluster");
const http = require("http");
const os = require("os");

if (cluster.isPrimary) {
    for (let i = 0; i < os.cpus().length; i++) {
        cluster.fork();
    }
} else {
    http.createServer((req, res) => {
        res.end(`Worker ${process.pid}`);
    }).listen(3000);
}
```

👉 Each worker is a separate Node.js process and can handle requests independently.
-------------------------------------------------------------------------------------------------------------------------

### Q.11 What is Closer
-------------------------------------------------------------------------------------------------------------------------

### Q.12 What is buffer?
**Definition:** A `Buffer` is a Node.js object used to store and manipulate raw binary data as bytes.

**Example:**
```js
const buf = Buffer.from("Hello");

console.log(buf);
console.log(buf.toString()); // Hello
```

#### Common Use Cases
- Files
- Streams
- Images/audio/video
- Network data
-------------------------------------------------------------------------------------------------------------------------

### Q.13 Error handling in Node.js
**Definition:** Error handling is the process of detecting and safely managing errors so the application can respond properly instead of failing unexpectedly.

#### 1. try/catch with async/await
```js
async function getData() {
    try {
        const data = await fetchData();
        return data;
    } catch (error) {
        console.error(error.message);
    }
}
```

#### 2. Express Error Middleware
```js
app.use((err, req, res, next) => {
    res.status(500).json({
        success: false,
        message: err.message
    });
});
```

👉 In Express applications, centralized error-handling middleware is commonly used.
-------------------------------------------------------------------------------------------------------------------------

### Q.14 How would you design a role-based dashboard?
-------------------------------------------------------------------------------------------------------------------------

### Q.15 How to handle large file uploads?
-------------------------------------------------------------------------------------------------------------------------

### Q.16 How to optimize API performance?
-------------------------------------------------------------------------------------------------------------------------

### Q.17 How caching works (Redis basics)
-------------------------------------------------------------------------------------------------------------------------

### Q.18 How would you scale a Node app?
-------------------------------------------------------------------------------------------------------------------------

### Q.19 What is ENV and its role?
-------------------------------------------------------------------------------------------------------------------------

### Q.20 Node js Life cycle
-------------------------------------------------------------------------------------------------------------------------

### Q.21 Difference between authentication and authorization
-------------------------------------------------------------------------------------------------------------------------

### Q.22 What is Non-Blocking I/O?
**Definition:** `Non-blocking I/O` means Node.js does not wait for a task (like DB call or file read) to complete. Instead, it continues executing the next code.

**Example:**
```js
fs.readFile("file.txt", () => {
  console.log("File read completed");
});
console.log("Hello");

**Output:**
Hello
File read completed
```
-------------------------------------------------------------------------------------------------------------------------

### Q.23 What is fs module?
**Definition:** `fs` (File System) module is a built-in Node.js module used to interact with the file system (read, write, update, delete files).

#### 1. Read file

**Example:**
```js
const fs = require('fs');

fs.readFile('demo.txt', 'utf8', (err, data) => {
  if (err) {
    console.log(err);
    return;
  }
  console.log(data);
});
```

#### 2. Write File

**Example:**
```js
fs.writeFile('demo.txt', 'Hello Shubham', (err) => {
  if (err) throw err;
  console.log('File written successfully');
});
```

#### 3. Write File

**Example:**
```js
fs.appendFile('demo.txt', '\nNew Line Added', (err) => {
  if (err) throw err;
  console.log('Data appended');
});
```

-------------------------------------------------------------------------------------------------------------------------
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
-------------------------------------------------------------------------------------------------------------------------

## -> MongoDB (Node js)

### Q.1 Difference between SQL & NoSQL
-------------------------------------------------------------------------------------------------------------------------

### Q.2 What is a document in MongoDB?
-------------------------------------------------------------------------------------------------------------------------

### Q.3 Indexes — types & usage in MongoDB
-------------------------------------------------------------------------------------------------------------------------

### Q.4 Aggregation pipeline in MongoDB
-------------------------------------------------------------------------------------------------------------------------

### Q.5 Difference between findOne() and find() in MongoDB
-------------------------------------------------------------------------------------------------------------------------

### Q.6 What is ObjectId in MongoDB?
-------------------------------------------------------------------------------------------------------------------------

### Q.7 Embedded vs referenced documents in MongoDB
-------------------------------------------------------------------------------------------------------------------------

### Q.8 Transactions in MongoDB
-------------------------------------------------------------------------------------------------------------------------

### Q.9 What is populate() in Mongoose?
-------------------------------------------------------------------------------------------------------------------------

### Q.10 How to optimize queries in MongoDB?

-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------

## -> Mongoose (Node js)

### Q.1 Schema vs Model in Mongoose
-------------------------------------------------------------------------------------------------------------------------

### Q.2 What is Migration
-------------------------------------------------------------------------------------------------------------------------

### Q.3 Middleware (pre & post hooks)
-------------------------------------------------------------------------------------------------------------------------

### Q.4 Validation in Mongoose
-------------------------------------------------------------------------------------------------------------------------

### Q.5 What is lean()?
-------------------------------------------------------------------------------------------------------------------------

### Q.6 Difference between save() and insertMany()
-------------------------------------------------------------------------------------------------------------------------

### Q.7 Pagination techniques in Mongoose
-------------------------------------------------------------------------------------------------------------------------

### Q.8 How to handle relationships in Mongoose?
-------------------------------------------------------------------------------------------------------------------------

### Q.9 How indexing works in Mongoose?

-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------

## -> Authentication & Security (Node js)

### Q.1 JWT vs Session authentication
-------------------------------------------------------------------------------------------------------------------------

### Q.2 How JWT works internally
-------------------------------------------------------------------------------------------------------------------------

### Q.3 What is refresh token?
-------------------------------------------------------------------------------------------------------------------------

### Q.4 Password hashing (bcrypt)
-------------------------------------------------------------------------------------------------------------------------

### Q.5 How to prevent XSS & CSRF
-------------------------------------------------------------------------------------------------------------------------

### Q.6 Role-based access control
-------------------------------------------------------------------------------------------------------------------------

### Q.7 What is OAuth?
-------------------------------------------------------------------------------------------------------------------------

### Q.8 How to secure REST APIs?

-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------

## -> REST API & Architecture (Node js)

### Q.1 What is REST?
-------------------------------------------------------------------------------------------------------------------------

### Q.2 REST vs GraphQL
-------------------------------------------------------------------------------------------------------------------------

### Q.3 HTTP methods & status codes
-------------------------------------------------------------------------------------------------------------------------

### Q.4 Idempotent APIs
-------------------------------------------------------------------------------------------------------------------------

### Q.5 What is API versioning?
-------------------------------------------------------------------------------------------------------------------------

### Q.6 Pagination vs infinite scroll
-------------------------------------------------------------------------------------------------------------------------

### Q.7 Rate limiting
-------------------------------------------------------------------------------------------------------------------------

### Q.8 Monolith vs Microservices
-------------------------------------------------------------------------------------------------------------------------

### Q.9 MVC architecture
-------------------------------------------------------------------------------------------------------------------------

### Q.10 Clean code practices

-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------

## -> Real Project Questions (Very Important)

### Q.1 Explain one of your projects end-to-end
-------------------------------------------------------------------------------------------------------------------------

### Q.2 Biggest challenge you faced?
-------------------------------------------------------------------------------------------------------------------------

### Q.3 How did you improve performance?
-------------------------------------------------------------------------------------------------------------------------

### Q.4 How did you handle authentication?
-------------------------------------------------------------------------------------------------------------------------

### Q.5 How did you structure your backend?
-------------------------------------------------------------------------------------------------------------------------

### Q.6 Any production issue you fixed?
-------------------------------------------------------------------------------------------------------------------------

### Q.7 How you handle environment variables?
-------------------------------------------------------------------------------------------------------------------------

### Q.8 How you deploy your app?

-------------------------------------------------------------------------------------------------------------------------

## -> JavaScript Logical or Coding Questions (Problem solving or DSA)

### Q.1. Flatten an array or Make single array or turns a nested multi-dimensional list into a single flat, one-dimensional list.

**Example 1:**
```js
const original = [1, [2, [3, 4], 5], 6];

function flattenArray(arr) {

    let result = [];
    for(let item of arr) {
        if(Array.isArray(item)) {
            result.push(...flattenArray(item));
        } else {
            result.push(item);
        }
    }
    return result;
}

const runFunction = flattenArray(original);
console.log(runFunction);
```

**Example 2:**
```js
const arr = [1, [2, 5], 4, 3];

function sortedArr(arr) {
    
    let result = [];
    for(let i = 0; i < arr.length; i++) {
        if(Array.isArray(arr[i])) {
            for(let j = 0; j < arr[i].length; j++) {
                result.push(arr[i][j]);
            }
        } else {
            result.push(arr[i]);
        }
    }

    return result;
}

console.log(sortedArr(arr));
```
-------------------------------------------------------------------------------------------------------------------------

### Q.2. Remove duplicates from array

**Example:**
```js
const arr = [1, 3, 4, 2, 2, 4, 5];

function removeDuplicate(arr) {

    let read = {};
    let result = [];

    for(let i = 0; i < arr.length; i ++) {
        if(!read[arr[i]]) {
            result.push(arr[i]);
            read[arr[i]] = true;
        }
    }
    return result;
}

const runFunction = removeDuplicate(arr);
console.log(runFunction);
```
-------------------------------------------------------------------------------------------------------------------------

### Q.3. Reverse a string without built-in methods

**Example 1:**
```js
let text = "hello";
let arr = text.split("");

    let start = 0;
    let end = arr.length - 1;

    while(start < end) {
        let temp = arr[start];

        arr[start] = arr[end];
        arr[end] = temp;

        start++;
        end--;
    }

console.log(arr.join(""));
```

**Example 2:**
```js
const str = "hello";

function reverseString(str) {
    let result = "";

    for (let i = str.length - 1; i >= 0; i--) {
        result += str[i];
    }

    return result;
}

console.log(reverseString(str));
```
-------------------------------------------------------------------------------------------------------------------------

### Q.4. Find second largest number

**Example 1:**
```js
const arr = [10, 5, 20, 8, 15];

function secondLargestNumber() {
    let largest = arr[0];
    let secondLargest = arr[1];

    for(let i = 0; i < arr.length; i++) {
        if(arr[i] > largest) {
            secondLargest = largest;
            largest = arr[i];
        } else if(arr[i] > secondLargest && arr[i] !== largest) {
            secondLargest = arr[i];
        }
    }

    return secondLargest
}

const callFunction = secondLargestNumber(arr);
console.log('Second Largest Number:', callFunction);
// 15
```

**Example 2:**
```js
const arr = [10, 5, 20, 8, 15];

function secondLargest(arr) {
    let largest = -Infinity;
    let second = -Infinity;

    for (let i = 0; i < arr.length; i++) {
        if (arr[i] > largest) {
            second = largest;
            largest = arr[i];
        } else if (arr[i] > second && arr[i] !== largest) {
            second = arr[i];
        }
    }

    return second;
}

console.log(secondLargest(arr));
// 15
```
-------------------------------------------------------------------------------------------------------------------------

### Q.5. Find a largest number

**Example:**
```js
const arr = [10, 5, 20, 8, 15];

function largestNumber() {
    let largest = arr[0];

    for(let i = 0; i < arr.length; i++) {
        if(arr[i] > largest) {
            secondLargest = largest;
            largest = arr[i];
        }
    }

    return largest
}

const callFunction = largestNumber(arr);
console.log('Largest Number:', callFunction);
```
-------------------------------------------------------------------------------------------------------------------------

### Q.6. Debounce function implementation

**Definition:** Debouncing ensures a function is executed only after a certain amount of time has passed since the last call.
It is commonly used for search inputs, API calls, resize events, etc.

**Example:**
```js
function debounce(fn, delay) {
    let timer;

    return function (...args) {
        clearTimeout(timer);

        timer = setTimeout(() => {
            fn(...args);
        }, delay);
    };
}

function search(value) {
    console.log("API call:", value);
}

const debouncedSearch = debounce(search, 500);

debouncedSearch("r");
// debouncedSearch("re");
// debouncedSearch("rea");
// debouncedSearch("react");
```
-------------------------------------------------------------------------------------------------------------------------

### Q.7. Deep clone an object

**Definition:** A deep clone creates a completely independent copy of an object, including its nested objects and arrays. Changes to the clone do not affect the original object.

**Example:**
```js
const original = {
    name: "Shubham",
    address: {
        city: "Indore"
    }
}

// console.log(original);

const clone = structuredClone(original);

clone.address.city = "Bhopal";

console.log(original.address.city);
console.log(clone.address.city);
```
-------------------------------------------------------------------------------------------------------------------------

### Q.1. What is callback?

**Definition:**
A callback is function that runs after another function finises its task.

**Example:**
```js

function one(name, callback) {
    console.log("Hello " + name);
    callback();
}

function two() {
    console.log("Bye!");
}

one("Shubham", two);
```
-------------------------------------------------------------------------------------------------------------------------

### Q.2. Closer example

**Definition:**
A closure is created when a function remembers variables from its outer (lexical) scope, even after the outer function has finished executing.

**Example 1:**
```js
function outer() {
    let count = 0;

    function inner() {
        count++;
        console.log(count);
    }

    return inner;
}

const counter = outer();
counter();
counter();
```

**Example 2:**
```js
function first() {
	let count = 0;
	return function second () {
    	count++;
    	return count
	}
}
 
let a = first();
console.log(a());
console.log(a());
```
-------------------------------------------------------------------------------------------------------------------------

### Q.3. How would you remove duplicate characters from a string while preserving the original order, spaces, and case sensitivity—using only logical iteration?

```js
const str = "Happy new year";

function sorting(str) {
    console.log(str);
    let read = {};
    let result = "";
    
    for(let i = 0; i < str.length; i++) {
        if(!read[str[i]]) {
            // console.log('read', read[str[i]]);
            read[str[i]] = true;
            result += str[i];
        }
    }
    
    return result;
}

console.log(sorting(str));
```
-------------------------------------------------------------------------------------------------------------------------

### Q.4. Sort the elements of an array in ascending order.

**Example:**
```js
const arr = [5, 8, 2, 6, 1, 3, 7, 10, 4, 9];

function mySorting(arr) {
    for(let i = 0; i < arr.length; i++) {
        for(let j = 0; j < arr.length; j++) {
            if(arr[j] > arr[j + 1]) {
                let temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    return arr;
}

console.log("Ans:", mySorting(arr));
```
-------------------------------------------------------------------------------------------------------------------------

### Q.5. Reverse an array without using any method or any extra array

**Example:**
```js
const arr = [2, 3, 5, 8, 7, 9];

let start = 0;
let end = arr.length -1;

while (start < end) {
    let temp = arr[start];
    // console.log('1111', temp);
    
    arr[start] = arr[end];
    // console.log('2222', arr[start]);
    
    arr[end] = temp;
    // console.log('3333', arr[start]);
    start++;
    end--
}
console.log(arr);  // [9, 7, 8, 5, 3, 2]
```
-------------------------------------------------------------------------------------------------------------------------

## -> Importants

**JS Questions:**
https://resources.theboringeducation.com/resources/javascript-interview-questions
