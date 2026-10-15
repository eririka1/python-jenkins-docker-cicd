# Python CI/CD Pipeline with Jenkins and Docker

## Project Overview

This is a hands-on DevOps project focused on building an automated CI/CD pipeline for a Python Flask application using Jenkins, GitHub, and Docker.

The pipeline will automate source code checkout, application testing, Docker image creation, and local container deployment.

## Technologies

- **Python** – Application programming language
- **Flask** – Web framework for building the application
- **Pytest** – Automated application testing
- **Git & GitHub** – Source code management
- **Jenkins** – CI/CD pipeline automation
- **Docker & Docker Desktop** – Containerization and container management
- **Windows** – Local development environment
## Project Structure

```text
python-jenkins-docker-cicd/
├── app.py
├── test_app.py
├── requirements.txt
├── .gitignore
└── README.md
```

Additional files, including `Dockerfile` and `Jenkinsfile`, will be added during development.

## Application

The Flask application exposes two HTTP endpoints:

| Endpoint | Description |
|---|---|
| `/` | Returns a welcome message |
| `/health` | Returns the application health status |

## CI/CD Pipeline Workflow

The planned pipeline will execute the following stages:

1. **Checkout** – Retrieve application code from GitHub.
2. **Build** – Build a Docker image containing the Flask application.
3. **Test** – Execute automated tests using Pytest.
4. **Deploy** – Run the application inside a Docker container.
5. **Verify** – Check that the deployed application responds correctly.

## Local Testing

Install the dependencies:

```bash
python3 -m pip install -r requirements.txt
```

Run the automated tests:

```bash
python3 -m pytest -v
```

Start the Flask application:

```bash
python3 app.py
```

Open the application at:

`http://localhost:5000`

Health check:

`http://localhost:5000/health`

## Learning Objectives

- Understand Jenkins Declarative Pipelines.
- Integrate Jenkins with GitHub.
- Automate Python application testing.
- Build and manage Docker images.
- Deploy containerized applications locally.
- Understand CI/CD stages and execution logs.
- Practice DevOps automation and troubleshooting.

## Project Status

**In Development**

Completed:
- Initial Flask application
- Home and health endpoints
- Python test scripts
- Dependency configuration

Planned:
- Dockerfile and Docker image
- Jenkinsfile and automated Pipeline
- Container deployment and verification
- Automated build triggers

## Future Improvements

- Introduce GitHub webhook triggers.
- Push Docker images to a container registry.
- Deploy the application to Kubernetes.
- Introduce security scanning and monitoring.

