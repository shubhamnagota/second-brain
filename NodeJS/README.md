https://nodejs.org/en

Node.js® is an open-source, cross-platform JavaScript runtime environment.
- Open Source - Public Source Code
- Cross Platform - Available on all platforms (windows, linux, macos)
- Javascript Runtime Environment - Provides all necessary components in order to use and run Javascript code outside the browser

## Why nodejs?
- Backend **javascript** development 
- Big companies like Paypal, netflix etc onboarded
- Fullstack development
- High community support

## Agenda
- What is nodejs?
- Modules (User defined)
- Built-in modules
- Node.js internals
- Npm - Node Package Manager
- CLI Tool
- Misc
	- Event Loop
- ExpressJs

## History of Javascript?
- [Ecmascript] 
	- 1993, First web browser (Mosaic)
	- 1994, Netscape company created Netscape Navigator browser with no interactions
	- 1995, Netscape created JavaScript
	- 1995, Microsoft creation Internet Explorer
	- 1996, Reverse engineered Javascript and created JScript
	- Both the implementation were different and were not able to develop for both.
	- 1996 Nov, Netscape submitted JS to Ecma International for industry standard.
	- Ecma 262 standard for JavaScript and TC39 committee.
	- Oracle aquired Microsystems has the rights of JavaScript, so Ecma decided to call Ecmascript as the offical language.
	- Ecmascript Versions 
		- 1997, Ecmascript 1
		- 1998, Ecmascript 2
		- 1999, Ecmascript 3
		- 2000, Ecmascript 4
		- 2009, Ecmascript 5
		- 2015, Ecmascript 2015 (ES6)
		- One version every year since 2015 like ES7, ES8, ES9
	- Both Ecmascript and Javascript are same, Ecma is the standard and Javascript is the language build on top of the standard.

## Chrome V8 Engine (v8.dev)
- Javascript engine - convert javascript code to machine code
- Every browser has javascript engine
	- V8 - Chrome (Open Source) released in 2008
	- Spider Monkey - Firefox
	- Javascript Core - Apple Safari
	- Chakra - Microsoft Edge
- It is written in C++ and open source and used in Google Chrome
- It can run standalone and can be embedded in any C++ application
- C++ application like Node.js takes benefit from it.
- C++ is great for low level operations like file handling, database and network operations, this functionalities can be extended to Javascript with Node.js
## Javascript Runtime
- Javascript Engine - Memory and CallStack
- Web Apis - DOM, Storage, Timers
- Event Loop
- Microtask Queue
- Callback/Task Queue
- ![[Pasted image 20230323020914.png]]
## What is NodeJS?
- Node.js is an open-source, cross-platform JavaScript runtime environment.
- We can build
	- Websites
	- APIs
	- Real time applications
	- Streaming services
	- CLI Tools
	- Multiplayer Games
- Github: github.com/nodejs/node
	- deps
		- v8 (javascript engine)
		- uv (access to file system and networking)
	- src
		- C++ features for low level programming
	- lib
		- Javascript code to access C++ features
	- ![[Pasted image 20230323021651.png]]
- No access to browser APIs
## REPL
- Read, Evaluate, Print, Loop
## Browser vs NodeJS
- DOM Interaction with browser, document, window and all other object are not available in NodeJS
- NodeJS provides modules to access file system, database
- NodeJS, we (developers) can manage versions
- Browser, users choose browser version
## Callbacks
- Functions are first class objects
- Function can be passed or returned from functions
- Any function is passed to another function is called as **callback function**
- Any function is which accepts or returns a function is called **higher order function**
- Types
	- Syncronous - Immediately executed eg. sort, map, filter array methods
	- Asyncronous - To continue code execution when an async operation has completed.
		- Callbacks are used to delay the execution until a particular time or event has occured
		- Nodejs have an async nature to prevent blocking of execution
			- eg. reading data from file, fetching data from db, handling a network request
		- Browser, register event listerner callbacks but executes when event occurs.
## Modules
- Reusable chunk of code
- Each file is module
- We use require to import a module (CommonJS)
- NodeJS uses IIFE that provides private scope without any conflicts and can reuse variable names in different files/modules
- ### Module Wrapper
	- function (exports, require, module, __filename, __dirname)
	- __dirname - path to current folder
	- __filename - filename of the current execution
	- require - function to import module by path, **cache** the module which is imported
	- module - reference to current module
	- exports - functions which are exported
- ### Module Caching
	- NodeJS imports the module once and uses it by reference and cache it
	- It will be used at a lot of places, it is used to improve performance.
- Types
	- Local/User Modules
	- Built-in Modules
	- 3rd Party Modules


## Local Modules
	- We create in our application
	- Create a add function and export it
	- CommonJS - standard how a module is structured and shared
		- const module = require("module")
		- .js file extension
	- ES Modules - a new standard module system from ecamscript, node.js 14+ supports it
		- .mjs file extension
		- type: module in package.json
		- import module from "module"
	- Nodejs check for .js file then .json file when imported but ideal to mention the extension for .json files
## Build-in Modules
	- Node.js ships it, also referred as core modules
	- Modules like path, fs, events
	- node: protocol
		- optional
		- import valid absolute url
		- future proof
		- clearly mention that it is an node module
	- path module
		- path.basename() - returns the last portion of the path
		- path.extname() - returns the extension of the path, empty for directory
		- path.parse() - return object with significant information of the path
		- path.format() - return the path string given an object from parse method
		- path.isAbsolute() - return true if it is an absolute path
		- path.join() - return the resulting path after joining with platform specific delimeters
		- path.resolve() - return sequence of paths in an absolute path
	- events module
		- an event is an occurrence that has happened which we can respond to
		- we can create our own events and respond to those events in a non-blocking manner
		- Real life scenario - Ordering pizza in dominoz, ordering pizza event resulting in baking pizza and delivering it.
		- emit() - to emit an event
		- on() - to listen to an event
		- extens EventEmitter - to create our own module by event emitter class
	- fs module
		- fs.readFile() - read contents of file
		- fs.writeFile() - write content to file, {flag: "a"} to append
		- sync methods available for all above methods, but it will block the execution
		- fs/promises module is available in new version to support promises and async await
	- http module
		- creation of web server which works over HTTP 
		- http.createServer() - return a server object which can listen to
		- res.write(status, headers)
		- res.end - sends the data back to the client
		- Content-Type - text/plain, text/html, application/json
		- req.url - gives the route query string
		- req.method - given method of request GET, POST

## Watch Mode
- Introduced in Nodejs 18
- node --watch index.js
- It constantly watches the file and rerun it.

## Character Sets
- These are prefilled lists of characters represented by numbers
- Popular Sets - Unicode and ASCII
## Character Encoding
- It tells how to represent a number in a character sets as binary data before it can be stored in computer
- It dictates how many bits used to store that number
- Eg. UTF-8, stored in 8 bytes
- 4 will be represented as 00000-100
- V(86) will be represented as 0-1010110
## Streams
- A sequence of data that is moved from one point to another
- Eg. computer to computer over internet or file system
- Process streams of data in chunks before waiting for full data arrival for processing
- Eg. youtube videos comes in chunks, file transfers
- Chunks are processed and then this process repeats
## Buffers
- YET TO READ
- https://www.youtube.com/watch?v=br8VB99qPzE&list=PLC3y8-rFHvwh8shCMHFA5kWxD9PaPwxaY&index=24

## Asyncronous Javascript
- JS is syncronous, blocking, single threaded language
- Web browsers and Node.js define functions and APIs that allows us to register functions that should execute async when some event occurs.
- Eg. passage of time (setTimeout or setInterval)
- Eg. Mouse click event listeners 
- Eg. data read from systems
- Eg. Arrival of data from network (callback, promises, async await)
- which allows us to run other code without waiting
## Streams
- Readable - Data can be read, file reading
- Writeable - Data can be write, file writing
- Duplex - Data can be read and write, sockets 
- Transform - Modify data as it is read and written, file compression to and from 
## Pipes
- Directly sending data within streams
- readableStream.pipe(writeableStream)
- Also we can chain streams data but it has to be a readable, duplex or transform stream
- eg. we can use zlib module to compress a file post reading and write to a gz file

## Node Internals
- libuv
	- libuv is cross platform open source library written in C
	- It handles async non-blocking operations in NodeJS
	- It uses ***thread pool*** and ***event loop*** to achieve the same
	- Thread Pool
		- Every method in NodeJS with sync suffix, runs on main thread of NodeJS
		- ![[Pasted image 20230323142007.png]]
		- libuv thread pool, async methods runs here
		- ![[Pasted image 20230323142308.png]]
		- Thread pool size = 4, 5th call will go in next cycle
		- ![[Pasted image 20230323142446.png]]
		- process.env.UV_THREADPOOL_SIZE = 6, it will be able to run things together
		- Thread pool size should not exceed the cpu cores, otherwise it will slow down the normal process execution time.
		- If we change the thread pool to 16, it will take more time to process these.
		- ![[Pasted image 20230323142849.png]]
		- libuv thread pool, all the async methods dont use it
		- https.request method is not affected by thread pool or max calls
		- It's a network I/O operation and not a CPU bound operation, it don't use thread pool and delegates the work to OS kernel and poll the kernel and see the req is completed.
	- Kernels
		- epoll - Linux
		- Kqueue - Macos
		- IO Completion Port - Windows
	- Event Loop
		- It's a C program and a part of libuv
		- It's a design pattern that orchestrates or co-ordinates the execution of syncronous and asynchronous code in NodeJS
		- ![[Pasted image 20230323144339.png]]
		- Event loop is alive until the nodejs app is running
		- 6 different queues holds the callbacks
			- libuv queues
				- Timer Queue - setTimeout and setInterval (FIFO), MinHeap Data Structure
				- I/O Queue - I/O callbacks, fs http modules
				- Check Queue - setImmidiate
				- Close Queue - close event of async tasks
			- nodejs queues
				- Microtask Queue: nextTick Queue - process.nextTick
				- Microtask Queue: promise Queue - promise callbacks
		- Execution order of queues
			- Any callback in microtask queue, nextTick first then promise queue
			- All callbacks in timer queue are executed, after every call it checks microtask queue.
			- Any callbacks in microtask queue, nextTick first then promise queue
			- All callbacks in the I/O queue are executed.
			- Any callbacks in microtask queue, nextTick first then promise queue
			- All callbacks in the check queue are executed.
			- Any callbacks in microtask queue, nextTick first then promise queue
			- All callbacks in the close queue are executed.
			- Any callbacks in microtask queue, nextTick first then promise queue
		- process.nextTick is discouraged to be used, only when
			- To allow users to handle errors, cleanup unneeded resources, try request again before the event loop continues
			- To allow a callback to run after the callstack has unwound but before event loop continues
		- Timer Queue
			- 0 millisecond delay changes to 1ms because of the code handling in DOMTimer in nodejs
		- I/O Queue
			- I/O events are polled and not available at the start, callback functions are added to the queue only after i/o operations are completed.
		- Check Queue
			- First this gets executed because it takes time to resolve timer queue
		- Close Queue
			- all .close(), callbacks are executed after all queues
## NPM
- Software library/registery, all the javascript packages are stored here from developers
- It is a software package manager, used to install, publish packages, updates, dependents.
- Alernatives - yarn, pnpm
- Node Package Manager => General Javascript Package Manager
## Packages
- package.json - configuration file for npm
- Semantic Versioning (SemVer)
	- X.Y.Z
	- X = Major Verion (not compatible, Y = 0, Z =0)
	- Y = Minor Version (functionality, and Z = 0)
	- Z = Patch (bug)
	- 0.1.0 is the first package version
	- first production ready version can be 1.0.0
- Local packages - local to a project
- Global packages - global to the system (-g flag)

## NPM Scripts
- commands to perform some operation like dev, start, build, test
- npm run `<command>`

## Clusters
## Worker Threads
## Expressjs
## Jest or Vitest
## Typescript



