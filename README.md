### Description

Create initial Fastify Node.js web server, initialize as a Node.js project folder using Node Package Manager (npm), add Fastify to project using npm, and test using Visual Studio Code (VSCode), add git repo, exclude node_modules folder from git, make commits, fix MIME error, test, and commit, and add a second route with query parameters, test, and commit.

### Code

// Require the Fastify framework and instantiate it
const fastify = require("fastify")();
// Handle GET verb for / route using Fastify
// Note use of "chain" dot notation syntax
fastify.get("/", (request, reply) => {
  reply
    .code(200)
    .header("Content-Type", "text/html; charset=utf-8")
    .send("<h1>Hello from Lab 4!</h1>");
});

//Name route
fastify.get("/name", (request, reply) => {
    const {first, last} = request.query;
    const name = first && last ? `${first} ${last}` : `Guest`;
    reply
    .code(200)
    .header("Content-Type", "text/html; charset=utf-8")
    .send(`<h1>Hello, ${name}</h1>`);
});
// Start server and listen to requests using Fastify
const listenIP = "localhost";
const listenPort = 8080;
fastify.listen(listenPort, listenIP, (err, address) => {
  if (err) {
    console.log(err);
    process.exit(1);
  }
  console.log(`Server listening on ${address}`);
});
