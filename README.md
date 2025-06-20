# airbnb-clone-project
exciting new journey into a complex project through baby steps in order to remaster the ropes of modern full stack developpment with an accent on the back-end side for the time being

Team Roles :

(i am not sure how this wil be graded, is it through regex or other means ? we will see if this test passes) 

even if the test is passed successfully i want to allocate 30 minutes reading about the topics and exploring the workflows of each team member

(the test passed successfully despite the dummy response which is fine i suppose but my goal is learning hence i will proceed as promised

Technology Stack :
> learn more about GraphQL and RestAPIs
> Learned quite a bit about the difference between REST (something something State Transfer) and GraphQL (query Language) , i will b mostly parrotting these points rather than express a deep understanding at this point but ..
- Graph QL : baiscally is granular but also costly in compute as the server is the one burdened , protocol agnostic though i have to admit i have ZERO idea what that means, some tooling like GraphQL mesh allows you to combine it with gRPC and SOAP etc ... api whatever ... frankly again i have no freaking idea what they mean, their purpose etc .. but hey they have crossed my path enough times (mostly in yt where i exist rather than in real projects 😭)

# Project Name

A web application built with Django, Django REST Framework, PostgreSQL, GraphQL, Celery, Redis, Docker, and CI/CD pipelines.

## Technologies

- **Django**: Web framework for rapid development.
- **Django REST Framework (DRF)**: For building RESTful APIs.
- **PostgreSQL**: Relational database for data storage.
- **GraphQL**: Flexible querying language for APIs.
- **Celery**: Asynchronous task queue for background jobs.
- **Redis**: In-memory data store for caching and session management.
- **Docker**: Containerization for consistent environments.
- **CI/CD Pipelines**: Automates testing and deployment.

## Setup

### Prerequisites

- Python 3.x
- Docker (for containerization)
- PostgreSQL (or Dockerized PostgreSQL)
- Redis (or Dockerized Redis)
  
### Install

1. Clone this repo:
    ```bash
    git clone https://github.com/yourusername/yourprojectname.git
    cd yourprojectname
    ```

2. Set up a virtual environment:
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # Linux/MacOS
    venv\Scripts\activate     # Windows
    ```

3. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

4. Set up environment variables (copy and edit `.env.example`):
    ```bash
    cp .env.example .env
    ```

5. Run migrations:
    ```bash
    python manage.py migrate
    ```

6. Start the app with Docker:
    ```bash
    docker-compose up --build
    ```

## Features

- **Django Admin**: Manage your data through the auto-generated admin interface.
- **RESTful API**: Built with Django REST Framework for easy CRUD operations.
- **GraphQL API**: Flexible querying with GraphQL.
- **Background Tasks**: Use Celery for background jobs.
- **Caching**: Speed up app with Redis caching.
- **Docker**: Containerize the app for consistent environments.
- **CI/CD**: Automated testing and deployment.

## CI/CD

The project uses CI/CD pipelines for:

- **Automated Testing**: Runs tests on every push.
- **Docker Builds**: Ensures consistent deployments.
- **Deployments**: Automatically deploys after successful tests.

## License

MIT License. See the [LICENSE](LICENSE) file for details.

