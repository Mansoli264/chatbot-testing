# Chatbot Theme Identifier

This is a simple Chatbot Theme Identifier service that can identify the theme or intent of a user's message using basic NLP techniques or a trained model. The project is containerized using Docker and orchestrated via Docker Compose, with persistent volume support.

## Features

* Identifies the theme of chatbot messages
* Containerized with Docker
* Managed with Docker Compose
* Uses a mounted volume for persistent data (e.g., logs, configs, models)

---
## Getting Started

### Prerequisites

* [Docker](https://www.docker.com/)
* [Docker Compose](https://docs.docker.com/compose/)

---

### Directory Structure

```
chatbot-theme-identifier/
│
├── app/                      # Application source code
│   └── main.py               # Entry point for chatbot theme identifier
│
├── data/                     # Persisted volume data (created automatically)
│
├── Dockerfile                # Dockerfile for building the app container
├── docker-compose.yml        # Docker Compose setup
└── README.md                 # Project documentation
```

---

### Dockerfile

Example `Dockerfile`:

```Dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY app/ /app/

RUN pip install --no-cache-dir -r requirements.txt

CMD ["python", "main.py"]
```

---

### docker-compose.yml

```yaml
version: '3.8'

services:
  chatbot:
    build: .
    volumes:
      - ./data:/app/data
    ports:
      - "8000:8000"
```

---

## Usage

1. **Clone the repository**:

   ```bash
   git clone https://github.com/your-username/chatbot-theme-identifier.git
   cd chatbot-theme-identifier
   ```

2. **Build and run with Docker Compose**:

   ```bash
   docker-compose up --build
   ```

3. The service will be accessible at `http://localhost:8000` (or whichever port your app uses).

---

## Data Persistence

The `./data` directory is mounted as a volume to store logs, model outputs, or any other data generated during runtime. This ensures your data persists even if the container is stopped or removed.
