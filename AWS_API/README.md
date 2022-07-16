## AWS_API

### What is Amazon API Gateway?

AWS also launched AWS HTTP APIs. These are a potential alternative to API Gateway REST APIs that we discuss in detail in our Ultimate Guide to AWS HTTP APIs.

Amazon API Gateway is a managed service that allows developers to define the HTTP endpoints of a REST API or a WebSocket API and connect those endpoints with the corresponding backend business logic. It also handles authentication, access control, monitoring, and tracing of API requests.

Many Serverless applications use Amazon API Gateway, which conveniently replaces the API servers with a managed serverless solution.


### How does API Gateway work?

API Gateway sits between the backend services of your API and your API’s users, handling the HTTP requests to your API endpoints and routing them to the correct backends. It provides a set of tools that help you manage your API definitions and the mappings between endpoints and their respective backend services. It can also generate API references from your definitions and make them available to your users as API documentation.


API Gateway integrates with many other AWS services like AWS Lambda, AWS SNS, AWS IAM, and Cognito Identity Pools. These integrations allow for fully managed authentication and authorization layers, as well as detailed metrics and tracing for API requests.




### How does API Gateway integrate with other AWS services?

Many AWS services support integration with Amazon API Gateway, including:

* AWS Lambda: run Lambda functions to generate HTTP API responses.
* AWS SNS: publish SNS notifications when an HTTP API endpoint is accessed.
* Amazon Cognito: provide authentication and authorization for your HTTP APIs.
API Gateway supports direct integrations that can be configured in the API Gateway user interface (or via the API Gateway’s own API) for the following actions:

* Invoking an AWS Lambda function.
* Invoking another HTTP endpoint, with or without VPC Link.
* Making an HTTP call against the API of any AWS service that provides an HTTP API.
* Returning a mock response generated within API Gateway without calling out to other services.

### Benefits of Amazon API Gateway

Using API Gateway to create HTTP APIs in AWS offers four main benefits:

Map HTTP requests to specific functions in a Serverless application via an API Gateway event. Connecting HTTP endpoints to individual functions is straightforward with API Gateway, obviating the need for a dedicated API server.

Map WebSocket events to Serverless functions. If you are building a WebSocket API, API Gateway also lets you map its events to a Serverless function. This works great for real-time functionality like in-app updates and notifications.

Use multiple microservices to serve the same top-level API. API Gateway makes it easy to have different Serverless functions serving different parts of your API. This means you can better encapsulate your functionality into each function and clearly separate the business logic of different parts of your API. Another benefit here is that you can transparently replace the function called by a given API request—the users won’t notice any change on the API layer.

Save time with integrations: authentication, developer portal, CloudTrail, CloudWatch. API Gateway allows you to implement a fully managed authentication and authorization layer by using Amazon Cognito and Lambda custom authorizers without running your own auth systems. By using API Gateway you also get access to the developer portals that are generated automatically from your API schemas. In addition, CloudTrail, CloudWatch and X-RAY all integrate with API Gateway, simplifying the profiling and debugging of API requests.

These benefits boil down to reducing your time to market for new HTTP APIs and increasing developer productivity, while also ensuring that the solutions your teams are building stay scalable.



# AWS DynamoDB 

DynamoDB is a hosted NoSQL database offered by Amazon Web Services (AWS). It offers:

* reliable performance even as it scales;
* a managed experience, so you won't be SSH-ing into servers to upgrade the crypto libraries;
* a small, simple API allowing for simple key-value access as well as more advanced query patterns.


DynamoDB is a particularly good fit for the following use cases:

* Applications with large amounts of data and strict latency requirements. As your amount of data scales, JOINs and advanced SQL operations can slow down your queries. With DynamoDB, your queries have predictable latency up to any size, including over 100 TBs!

* Serverless applications using AWS Lambda. AWS Lambda provides auto-scaling, stateless, ephemeral compute in response to event triggers. DynamoDB is accessible via an HTTP API and performs authentication & authorization via IAM roles, making it a perfect fit for building Serverless applications.

* Data sets with simple, known access patterns. If you're generating recommendations and serving them to users, DynamoDB's simple key-value access patterns make it a fast, reliable choice.