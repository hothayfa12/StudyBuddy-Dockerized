# StudyBuddy — Dockerized Student Productivity App

StudyBuddy is a web-based student productivity application designed to help students organize their study tasks, track habits, and explore educational resources.

This repository contains a Dockerized version of StudyBuddy, allowing developers to run the application consistently using Docker and Nginx.

## Features

- **Task Management:** Organize and manage study-related tasks.
- **Habit Tracking:** Track study habits and personal progress.
- **Educational Resources:** Explore useful learning resources.
- **Local Storage:** Save application data locally in the browser.
- **Docker Support:** Run the application in a containerized environment.

## Tech Stack

| Technology | Purpose |
|---|---|
| HTML5 | Application structure |
| CSS3 | Styling and layout |
| JavaScript | Application logic and interactivity |
| Browser LocalStorage | Client-side data persistence |
| Nginx | Web server |
| Docker | Application containerization |
| Docker Compose | Container configuration and management |
| Git & GitHub | Version control and collaboration |

## Project Structure

```text
StudyBuddy-Dockerized/
├── src/
│   ├── index.html
│   ├── app.js
│   ├── style.css
│   ├── resources.json
│   └── logo.png
├── Dockerfile
├── .dockerignore
├── .gitignore
├── docker-compose.yml
├── README.md
└── docs/
    ├── screenshots/
    └── notes.md
```

The `docs/` directory contains technical notes and screenshots documenting the Docker setup and testing process.

## Prerequisites

Before running the application, ensure you have:

- Docker Desktop or Docker Engine installed.
- Docker Compose available (for the Compose method).
- Git installed to clone the repository.

No Node.js installation, additional application dependencies, or external database is required.

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/hothayfa12/StudyBuddy-Dockerized.git
cd StudyBuddy-Dockerized
```

### 2. Build the Docker Image

```bash
docker build -t studybuddy:dev .
```

Docker builds an image using the provided `Dockerfile` and the Nginx Alpine-based image.

### 3. Run the Docker Container

```bash
docker run -d --name studybuddy-container -p 8080:80 studybuddy:dev
```

### 4. Verify Container Status

```bash
docker ps
```

Confirm that `studybuddy-container` appears with a running status.

### 5. Access the Application

Open your browser and visit:

**http://localhost:8080**

You should see the StudyBuddy application.

## Running with Docker Compose (Bonus A)

Docker Compose provides an easier way to build, start, and manage the application.

Start the application:

```bash
docker compose up -d --build
```

Check the container status:

```bash
docker compose ps
```

Open the application at:

**http://localhost:8080**

Stop and remove the Compose-managed containers and network:

```bash
docker compose down
```

**Note:** Do not run the standalone Docker container and Docker Compose version simultaneously on port `8080`, because they would conflict.

## Application Configuration

| Setting | Value |
|---|---|
| Container HTTP port | `80` |
| Host HTTP port | `8080` |
| Docker image | `studybuddy:dev` |
| Web server | Nginx |
| Required environment variables | None |
| External database | Not required |

The host port can be changed by modifying the port mapping in the Docker command or `docker-compose.yml`.

## Testing the Application

After starting the container:

1. Open `http://localhost:8080` in a browser.
2. Confirm that the StudyBuddy interface loads.
3. Add or manage a study task.
4. Test the available habit-tracking features.
5. Open the educational resources section.
6. Refresh the page and verify that locally saved data persists.

You can also check the HTTP response using:

```bash
curl -I http://localhost:8080
```

A successful response should include:

```text
HTTP/1.1 200 OK
```

## Data Persistence

StudyBuddy stores user-generated data using the browser's LocalStorage.

This means:

- Data is stored locally in the user's browser.
- No MySQL or external database is required.
- Restarting or recreating the Docker container does not normally remove browser LocalStorage data.
- Clearing browser storage may delete saved application data.

## Stopping and Cleaning Up

For a container started with `docker run`:

Stop the container:

```bash
docker stop studybuddy-container
```

Remove the container:

```bash
docker rm studybuddy-container
```

For Docker Compose:

```bash
docker compose down
```

Optional — remove the local Docker image after all containers using it have been removed:

```bash
docker rmi studybuddy:dev
```

## Troubleshooting

**Port 8080 is already in use**

Stop the existing container or change the host port mapping.

**Docker daemon is unavailable**

Make sure Docker Desktop or Docker Engine is running.

**Application does not load**

Check the container status and inspect its logs:

```bash
docker ps -a
docker logs studybuddy-container
```

For Docker Compose, use:

```bash
docker compose logs studybuddy
```

## Project Origin and Attribution

This project is based on my previous StudyBuddy web application.

Original repository:

https://github.com/hothayfa12/web-prioect-StudyBuddy

The application was adapted and containerized for **OS Lab — Assignment #2: Docker & GitHub Basics**.

The Docker configuration, documentation, and Git workflow were developed as part of this assignment.

## Author

**GitHub:** [hothayfa12](https://github.com/hothayfa12)

**Project:** StudyBuddy-Dockerized
