# Jenkins Docker CI/CD Pipeline

A basic CI/CD pipeline using Jenkins, GitHub, Docker, and Docker Hub.

The pipeline automatically:

1. Checks out source code from GitHub.
2. Installs application dependencies.
3. Runs automated tests.
4. Builds a Docker image.
5. Pushes the image to Docker Hub.

## Project Structure

```text
jenkins-docker-demo/
├── app.py
├── test_app.py
├── requirements.txt
├── Dockerfile
├── Jenkinsfile
└── README.md
```

## Technologies Used

- Jenkins
- GitHub
- Git
- Docker
- Docker Hub
- Python
- pytest
- Linux

## Application

The sample Python application returns the following message:

```text
Jenkins Docker CI/CD pipeline is working
```

## Run the Application Locally

Clone the repository:

```bash
git clone [https://github.com/nisha-subramaniyan/jenkins-docker-demo.git](https://github.com/nisha-subramaniyan/jenkins-docker-demo.git)
cd jenkins-docker-demo
```

Create a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the application:

```bash
python app.py
```

Run the automated test:

```bash
pytest -v
```

Expected test result:

```text
1 passed
```

## Build and Run with Docker

Build the image:

```bash
docker build -t nishasubramaniyan/jenkins-docker-demo:latest .
```

Run the container:

```bash
docker run --rm \
  nishasubramaniyan/jenkins-docker-demo:latest
```

Expected output:

```text
Jenkins Docker CI/CD pipeline is working
```

## Jenkins Configuration

Create a Jenkins Pipeline job with the following configuration:

```text
Definition: Pipeline script from SCM
SCM: Git
Repository URL: [https://github.com/nisha-subramaniyan/jenkins-docker-demo.git](https://github.com/nisha-subramaniyan/jenkins-docker-demo.git)
Branch: main
Script Path: Jenkinsfile
```

Install or enable these Jenkins plugins:

- Pipeline
- Git
- GitHub Integration
- Credentials Binding
- Docker Pipeline

## Jenkins Credentials

Add Docker Hub credentials in Jenkins:

```text
Credential type: Username with password
Credential ID: dockerhub-creds
Username: nishasubramaniyan
Password: Docker Hub access token
```

The password should be a Docker Hub access token, not the normal account password.

The credentials are used in the Jenkinsfile through `withCredentials`. Secrets are not stored directly in the source code.

## Pipeline Stages

| Stage | Description |
|---|---|
| Checkout | Retrieves the source code from GitHub |
| Build | Installs Python dependencies |
| Test | Runs the pytest automated test |
| Package | Builds the Docker image |
| Push | Pushes the image to Docker Hub |

## Docker Image

Docker Hub image:

```text
[https://hub.docker.com/r/nishasubramaniyan/jenkins-docker-demo](https://hub.docker.com/r/nishasubramaniyan/jenkins-docker-demo)
```

The pipeline publishes two tags:

```text
latest
BUILD_NUMBER
```

Example:

```text
nishasubramaniyan/jenkins-docker-demo:latest
nishasubramaniyan/jenkins-docker-demo:15
```

## Environment Variables

The Jenkinsfile uses these variables:

```groovy
environment {
    DOCKER_IMAGE = "nishasubramaniyan/jenkins-docker-demo"
    IMAGE_TAG = "${BUILD_NUMBER}"
}
```

`BUILD_NUMBER` creates a unique tag for every Jenkins build.

## GitHub Webhook

To trigger Jenkins automatically after a GitHub push:

1. Open the GitHub repository.
2. Select `Settings`.
3. Select `Webhooks`.
4. Select `Add webhook`.
5. Enter:

```text
http://YOUR_JENKINS_HOST/github-webhook/
```

6. Select content type:

```text
application/json
```

7. Select `Just the push event`.
8. Save the webhook.

For local Jenkins, use a public tunnel or manually trigger the Jenkins job because GitHub cannot directly reach `localhost`.

## Blue-Green Deployment

Blue-Green deployment uses two environments:

- Blue: current production version.
- Green: new version being tested.

The new application version is deployed to Green. After testing, traffic is switched from Blue to Green. If a problem occurs, traffic can quickly be switched back to Blue.

### Advantages

- Fast rollback.
- Low downtime.
- New version can be tested before receiving production traffic.

### Disadvantages

- Requires two environments.
- Requires additional infrastructure.
- Database changes need careful coordination.

## Rolling Deployment

Rolling deployment updates application instances gradually. A small number of instances are updated while the remaining instances continue serving users.

### Advantages

- Uses fewer resources than Blue-Green.
- Supports gradual deployment.
- Service can remain available during deployment.

### Disadvantages

- Multiple application versions may run temporarily.
- Rollback can take longer.
- Backward compatibility may be required.

## Submission Evidence

The following evidence should be included:

- Jenkinsfile.
- GitHub repository link.
- Jenkins pipeline screenshot.
- Successful build screenshot.
- Docker image screenshot.
- PDF report.

## Repository

GitHub repository:

```text
[https://github.com/nisha-subramaniyan/jenkins-docker-demo.git](https://github.com/nisha-subramaniyan/jenkins-docker-demo.git)
```
