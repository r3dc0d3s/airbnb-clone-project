# airbnb-clone-project
exciting new journey into a complex project through baby steps in order to remaster the ropes of modern full stack developpment with an accent on the back-end side for the time being

Team Roles :

(i am not sure how this wil be graded, is it through regex or other means ? we will see if this test passes) 

even if the test is passed successfully i want to allocate 30 minutes reading about the topics and exploring the workflows of each team member

(the test passed successfully despite the dummy response which is fine i suppose but my goal is learning hence i will proceed as promised

Technology Stack :
> learn more about GraphQL and RestAPIs
> Learned quite a bit about the difference between REST (something something State Transfer) and GraphQL (query Language) , i will b mostly parrotting these points rather than express a deep understanding at this point but ..
- Graph QL : baiscally is granular but also costly in compute as the server is the one burdened , protocol agnostic though i have to admit i have ZERO idea what that means, some tooling like GraphQL mesh allows you to combine it with gRPC (ok google smthg ... ultra fast and mostly for microservices, bi directional etc ...) and SOAP etc ... api whatever ... frankly again i have no freaking idea what they mean, their purpose etc .. but hey they have crossed my path enough times (mostly in yt where i exist rather than in real projects 😭)
- okay i need to be compliant with the requirements so here goes the tech stack :
  > 1. Django: High-Level Python Web Framework
Django is a batteries-included framework for building web applications using Python. It's built with the goal of simplifying the development process by providing developers with a comprehensive set of tools out of the box. It's particularly well-suited for projects that need rapid development with features like authentication, admin interfaces, and form handling.

Key Features:
MVC Pattern: Django follows the Model-View-Controller (MVC) design pattern, with slight variations:

Model: Represents the database structure.

View: Handles the logic and rendering of data.

Controller: Handles the flow between the Model and View, which in Django is handled by the URLs and Views.

ORM (Object-Relational Mapping): Django’s ORM translates Python code into SQL queries, allowing developers to interact with databases using Python objects rather than raw SQL.

Admin Interface: Automatically generated from your models, Django provides a user-friendly interface to manage and manipulate the content in the database without additional setup.

Security: Django has built-in protections against common web vulnerabilities (e.g., SQL injection, Cross-Site Scripting, Cross-Site Request Forgery, etc.).

Form Handling: Simplifies form creation, validation, and processing for user input, which is crucial for web apps.

2. Django REST Framework (DRF): Building RESTful APIs
Django REST Framework (DRF) is a powerful library built on top of Django that makes it easier to build RESTful APIs.

Key Features:
Serialization: Converts complex data types like Django models or querysets into JSON and vice versa. This is crucial for APIs.

ViewSets & Routers: DRF simplifies the creation of API views and URLs. ViewSets provide the actions like list, create, update, delete, etc., and Routers automatically map these actions to URLs.

Authentication: DRF supports multiple authentication mechanisms out of the box (e.g., Token Authentication, OAuth, Session Authentication).

Permissions: DRF provides a powerful permission system to restrict access to your APIs based on user roles.

Pagination: Helps manage large datasets returned by the API by splitting the response into smaller chunks.

Throttling & Rate-Limiting: Helps control how often API clients can make requests.

3. PostgreSQL: Powerful Relational Database
PostgreSQL is an object-relational database management system (ORDBMS), meaning it combines the features of both relational databases and object-oriented databases. It is widely praised for its robustness, scalability, and support for complex queries.

Key Features:
ACID Compliance: PostgreSQL guarantees Atomicity, Consistency, Isolation, and Durability, ensuring reliable transactions.

SQL & JSON Support: In addition to traditional SQL, PostgreSQL also supports JSON and JSONB (binary JSON), making it a hybrid database suitable for document and relational data.

Indexes: PostgreSQL supports multiple indexing strategies, including B-tree, Hash, GIN, and GiST, which can speed up queries.

Extensibility: PostgreSQL allows you to define your own data types, custom functions, and even create extensions, making it ideal for advanced use cases.

Foreign Keys and Joins: You can define relationships between tables using foreign keys and join them efficiently in queries.

Concurrency: Multi-version concurrency control (MVCC) allows multiple transactions to occur at the same time without interfering with each other.

4. GraphQL: Flexible and Efficient Querying
GraphQL is an open-source query language for APIs and a runtime for executing those queries. It enables clients to request only the data they need, providing flexibility over traditional REST APIs.

Key Features:
Client-Specified Queries: Unlike REST, where the server defines the response structure, GraphQL allows clients to specify exactly which fields they want in the response. This can drastically reduce over-fetching of data.

Single Endpoint: GraphQL uses a single endpoint for all queries and mutations, unlike REST, which typically uses multiple endpoints for different resources.

Strongly Typed: The schema in GraphQL is strictly defined, and any query or mutation must adhere to that schema. This makes it self-documenting and predictable.

Real-Time Data: GraphQL supports subscriptions, which allow clients to receive real-time updates when data changes.

Efficient Aggregation: GraphQL allows querying multiple related data in a single request (with multiple resolvers). It can handle complex queries with relationships across different resources.

5. Celery: Asynchronous Task Queue
Celery is an asynchronous task queue/job queue based on distributed message passing. It’s used to handle time-consuming tasks asynchronously.

Key Features:
Task Scheduling: You can schedule periodic tasks (e.g., sending email notifications) or one-off tasks (e.g., background data processing).

Multiple Broker Support: Celery supports Redis, RabbitMQ, and other message brokers for task queuing.

Concurrency: Celery workers can process multiple tasks concurrently, which is crucial for tasks that would block the web server (e.g., processing payments, sending emails).

Retry Mechanism: Celery supports automatic retries, which is useful for transient failures (e.g., network issues).

Task Result Storage: Celery can store results of tasks, which is handy if you need to check the status or result of a task after it’s completed.

6. Redis: In-memory Key-Value Store
Redis is an open-source, in-memory key-value store that is often used for caching, session management, and message brokering.

Key Features:
Caching: Redis is commonly used to cache frequently accessed data, reducing the load on your database and improving response times for end-users.

Pub/Sub: Redis supports publish/subscribe messaging, allowing one component to send messages that multiple other components can listen to. This is useful for event-driven architectures.

Persistence: While Redis is primarily an in-memory database, it supports persistence through snapshots and append-only files.

Fast Reads/Writes: Redis is optimized for very fast reads and writes, making it ideal for use cases like caching, session management, and job queues.

Data Structures: Redis supports various data structures like strings, sets, sorted sets, hashes, and lists, which provide more flexibility than a simple key-value store.

7. Docker: Containerization Tool
Docker is a platform for developing, shipping, and running applications inside containers, which are lightweight, standalone, executable packages.

Key Features:
Isolation: Docker containers isolate applications and their dependencies, ensuring consistency across development, staging, and production environments.

Portability: Containers can run on any system that supports Docker, ensuring that code behaves the same regardless of the host operating system.

Efficiency: Containers share the host system’s kernel and resources, making them more lightweight than virtual machines.

DevOps/CI-CD Integration: Docker integrates well into Continuous Integration/Continuous Deployment (CI/CD) pipelines, allowing for automated testing, building, and deployment.

Scalability: Docker works well in cloud-native environments, such as Kubernetes, making it ideal for scalable, microservices architectures.

8. CI/CD Pipelines: Automated Testing and Deployment
CI/CD stands for Continuous Integration and Continuous Deployment/Continuous Delivery. CI/CD pipelines automate the process of testing, building, and deploying code changes.

Key Features:
Continuous Integration (CI): CI involves automatically testing code changes that are pushed to the version control system (e.g., Git). It ensures that new code doesn’t break existing features.

Continuous Delivery (CD): After passing tests, the changes are automatically deployed to staging or production environments.

Automated Testing: CI/CD pipelines often include unit tests, integration tests, and end-to-end tests to ensure the software behaves as expected.

Versioning: With CI/CD, every change is tracked and versioned, making it easy to roll back if a deployment introduces a bug.

Monitoring: CI/CD can include automated monitoring to ensure the deployment was successful and that the app is working as expected.

In Summary:
Django is a full-stack framework used for building web applications and APIs, with built-in tools for rapid development.

Django REST Framework simplifies the creation of RESTful APIs in Django.

PostgreSQL is a powerful, scalable, and feature-rich relational database for storing structured data.

GraphQL provides a flexible query language for APIs, allowing clients to request only the data they need.

Celery is used for handling asynchronous tasks, enabling background processing.

Redis is a high-speed, in-memory data store used for caching and session management.

Docker provides containerization for consistent and scalable deployments.

CI/CD pipelines automate the process of testing, building, and deploying code changes, making it easy to maintain a high-quality, consistent codebase.
