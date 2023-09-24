# REST Wrapper

A RESTful wrapper for Ethereum JSON-RPC API for execution layer.

## Motivation

Ethereum nodes offer a rich set of functionalities through the JSON-RPC interface, which allows users to query and interact with the blockchain. However, JSON-RPC is not a very user-friendly or standard way of accessing web services. Many users are more familiar and comfortable with using REST APIs, which are widely adopted and supported by various tools and frameworks. A REST wrapper would bridge the gap between the JSON-RPC and the REST paradigms, enabling users to access Ethereum nodes with a different syntax and format.

## Project description

The project aims to create a middleware application that acts as a bridge between the REST and the JSON-RPC interfaces for Ethereum nodes. The middleware application would provide a REST API endpoint that accepts HTTP requests from users and converts them to JSON-RPC requests for Ethereum nodes. The middleware application would also receive JSON-RPC responses from Ethereum nodes and convert them to REST responses for users. The middleware application would follow the OpenAPI Specification and use the Ethereum Execution Layer API Documentation as a reference for mapping and converting the requests and responses between the two formats. The middleware application would also handle any errors or exceptions that may occur during the conversion or execution of the requests.

## Specification

The middleware would be developed in Go, using the following packages and frameworks:

- `ethclient`: A Go package that provides access to the Ethereum JSON-RPC API, allowing the middleware to communicate with Ethereum nodes and execute various methods and functions. The ethclient package supports both HTTP and WebSocket transports, and provides more methods for querying and interacting with the ethereum, such as BalanceAt, TransactionReceipt, FilterLogs, etc.
- `Fiber`: A web framework for Go that is inspired by Express.js, a popular framework for Node.js. Fiber provides a fast, easy, and flexible way to create a REST API endpoint that accepts HTTP requests from users and returns responses in JSON format.
- `jsonschema`: A Go package that implements JSON Schema, a standard for validating and describing JSON data. jsonschema allows the middleware to define and use schemas that specify the rules for mapping and converting the requests and responses between the REST and the JSON-RPC formats.

The middleware would have the following components and functionalities:

1. A REST API endpoint that accepts HTTP GET and POST requests from users, with query parameters or request body respectively. The endpoint would parse the request and validate it against a predefined schema that defines the REST format for Ethereum methods and parameters. The endpoint would also handle any errors or exceptions that may occur during the parsing or validation process.
2. A JSON-RPC client that sends JSON-RPC requests to an Ethereum node, using the ethclient package. The client would map the request from the REST format to the JSON-RPC format, using a predefined schema that defines the mapping rules. The client would also receive JSON-RPC responses from the Ethereum node and convert them to the REST format, using another predefined schema that defines the conversion rules.
3. A response handler that sends REST responses back to the user, along with any relevant headers or status codes. The response handler would also handle any errors or exceptions that may occur during the conversion or execution of the requests.

## Roadmap

The proposed timeline for the project is as follows:

### Phase 1

#### Week 0:

Introduction and joining discord groups. Getting familiar with the project idea, the mentor, and the cohort.

#### Week 1:

Exploring and researching the Ethereum protocol and the JSON-RPC API. Reading the Ethereum whitepaper and learning about UTXO, accounts, transactions, blocks, contracts, and events. Reading stories on inevitable ethereum and learning about EIPs.

#### Week 2:

Finding purpose of life (or proposal for EPF). Choosing the REST wrapper project idea and expressing interest to the mentor. Starting to work on the Ethereum REST API specification, based on the OpenAPI Specification and the Ethereum Execution Layer API Documentation. Proposing some features that would make the REST wrapper more user-friendly, such as using a boolean flag for using integers instead of hashes.

### Phase 2

#### Week 3:

Specing out half of the RPC methods on OPENAPI. Merging some of the JSON-RPC methods into more generalised REST APIs, such as `/eth/block/hash/{HashOrNumber}`. Proposing some implementation details that would make interacting with execution-apis more user-friendly, such as using a `?useInt` flag for using integers in place of hashes for parameters like Index.

#### Week 4:

Creating a presentation, doing a presentation with the peers and mentors in standup call, and drafting a proposal. Getting feedback and suggestions from the mentor and the cohort. Finalizing the Ethereum REST API specification and preparing for the next phase of development.

### Phase 3

#### Week 5-15:

- Develop and test the middleware using Go, ethclient, Fiber, and jsonschema packages. The middleware would implement the REST API endpoint that accepts HTTP requests from users and converts them to JSON-RPC requests for Ethereum nodes. The middleware would also convert the JSON-RPC responses from Ethereum nodes to REST responses for users. The middleware would handle any errors or exceptions that may occur during the process.

- Document and deploy the middleware. The documentation would explain how to use the middleware, what are the requirements and dependencies, and what are the features and limitations. The deployment would make the middleware accessible and usable by anyone who wants to interact with Ethereum nodes using a RESTful interface.

- Evaluate and improve the middleware based on feedback and testing. The evaluation would measure the performance, reliability, usability, and compatibility of the middleware. The improvement would address any issues or bugs that may arise, as well as add any enhancements or features that may be requested or suggested.

## Possible challenges

Some of the difficulties and obstacles that may need to be overcome are:

- The JSON-RPC methods and parameters may not have a clear or natural mapping to the REST format, requiring some design decisions and trade-offs. For example, some JSON-RPC methods may have multiple parameters, whereas some REST APIs may only accept one parameter. Some JSON-RPC methods may return complex or nested data structures, whereas some REST APIs may only return simple or flat data structures (a good practice). Some JSON-RPC methods may have different names or meanings than their REST counterparts, requiring some clarification or explanation (as we have already done some merging of few methods in one call).

- Naturally, the middleware may introduce some _delay_ or overhead in the communication between the user and the Ethereum node, affecting the performance or reliability of the requests. For example, the middleware need to parse, validate, map, convert, and handle the requests and responses, which may take some time and resources. The middleware may also depend on some external packages or frameworks, which may have some bugs or vulnerabilities. The middleware may also face some network issues or errors, such as timeouts, connection failures, etc.

- The middleware _may need to support different protocols_ and transports for communicating with Ethereum nodes in the _future_, such as WebSocket, IPC, etc. Currently, the middleware is at the **wrapper** stage and works mainly with HTTP, which is a widely used and supported protocol that can handle most of the JSON-RPC methods and parameters. However, HTTP is not a full duplex protocol, which means that it only allows one-way communication per request. Therefore, HTTP cannot support some features and functionalities that require bidirectional communication, such as subscriptions or real-time events. WebSocket and IPC are full duplex protocols that enable bidirectional communication over a single connection, which are ideal for subscriptions or real-time events. However, WebSocket and IPC are newer protocols that may not be compatible or allowed by some browsers, servers, proxies, firewalls, etc., requiring some fallback mechanisms or workarounds. Each protocol and transport may have its own advantages and disadvantages, such as speed, reliability, security, etc. The middleware may need to adapt to different scenarios and preferences of the users and the nodes, such as using HTTP for simple queries and WebSocket or IPC for subscriptions or real-time events.

- The middleware may need to comply with some standards and specifications for defining and documenting the REST API, such as the OpenAPI Specification and the JSON Schema. These standards and specifications may have some rules and constraints that may limit or complicate the design and implementation of the REST API. The middleware will need to **keep up with the updates and changes of these standards and specifications**, as well as the Ethereum JSON-RPC API.

## Goal of the project

The success of the project would be measured by:

- The completeness and correctness of the Ethereum REST API specification, covering all the JSON-RPC methods and parameters, and describing how they are mapped and converted to the REST format. The specification would also include examples and schemas for validating and describing the requests and responses.
- The functionality and robustness of the middleware application, handling all kinds of requests and responses without errors or exceptions.
- The usability and accessibility of the middleware application, providing a clear and consistent interface for users to interact with Ethereum nodes.

The end goal of the project is to make it easier and more standard for users to access Ethereum nodes using a RESTful interface, improving the reliability, usability, and compatibility of the communication which will overall contribute in improvement and innovation on Ethereum protocol.

## Collaborators

### Fellows

[@amit0617](https://github.com/amit0617)

### Mentors

@lightclient

### Resources

[OpenAPI Specification](https://spec.openapis.org/oas/v3.0.3)  
[Ethereum Execution Layer API Documentation](https://ethereum.github.io/execution-apis/api-documentation/)  
[Ethereum JSON-RPC Specification](https://ethereum.org/en/developers/docs/apis/json-rpc)  
https://pkg.go.dev/github.com/ethereum/go-ethereum/ethclient  
[`ethclient` package Documentation](https://geth.ethereum.org/docs/developers/dapp-developer/native#overview)  
[RPC wrapper presentation slides](https://drive.google.com/file/d/1RoFP3nbU8xhzfa7nP6B5SioDfrzaMao-/view?usp=sharing)
