# FastAPI Docker Application

A simple FastAPI application containerized with Docker for easy deployment and development.

## Project Overview

This project demonstrates a basic FastAPI application with Docker support, including:

- A minimal FastAPI REST API
- Docker containerization
- Docker Compose for development
- Health check endpoint

## Features

- **Root Endpoint** (`/`): Returns a simple "Hello World" message
- **Health Check** (`/health`): Returns application health status
- **Hot Reload**: Automatic code reload during development
- **Containerized**: Fully Dockerized for consistent environments

## Project Structure

```
fastapi/
├── app/
│   └── main.py           # FastAPI application code
├── Docker-compose.yml    # Docker Compose configuration
├── Dockerfile            # Docker image definition
├── requirements.txt      # Python dependencies
└── README.md            # Project documentation
```

## Prerequisites

- [Docker](https://www.docker.com/get-started) (version 20.x or higher)
- [Docker Compose](https://docs.docker.com/compose/install/) (version 2.x or higher)

## Getting Started

### Option 1: Using Docker Compose (Recommended for Development)

1. **Clone the repository**

   ```powershell
   git clone https://github.com/Rudraksh121a/fastapi-docker.git
   cd fastapi-docker
   ```

2. **Start the application**

   ```powershell
   docker-compose up --build
   ```

3. **Access the application**

   - API: http://localhost:8000
   - Interactive API docs: http://localhost:8000/docs
   - Alternative API docs: http://localhost:8000/redoc

4. **Stop the application**
   ```powershell
   docker-compose down
   ```

### Option 2: Using Docker Directly

1. **Build the Docker image**

   ```powershell
   docker build -t fastapi-app .
   ```

2. **Run the container**

   ```powershell
   docker run -d -p 8000:8000 --name fastapi-container fastapi-app
   ```

3. **Stop and remove the container**
   ```powershell
   docker stop fastapi-container
   docker rm fastapi-container
   ```

### Option 3: Local Development (Without Docker)

1. **Create a virtual environment**

   ```powershell
   python -m venv venv
   .\venv\Scripts\Activate.ps1
   ```

2. **Install dependencies**

   ```powershell
   pip install -r requirements.txt
   ```

3. **Run the application**
   ```powershell
   uvicorn app.main:app --reload
   ```

## API Endpoints

### GET `/`

Returns a welcome message.

**Response:**

```json
{
  "Hello": "World"
}
```

### GET `/health`

Health check endpoint for monitoring.

**Response:**

```json
{
  "status": "healthy"
}
```

## Development

The Docker Compose setup includes:

- **Volume mounting**: Your local code is mounted into the container for live updates
- **Hot reload**: Changes to the code automatically restart the server
- **Port mapping**: The application is accessible at `localhost:8000`

### Making Changes

1. Edit files in the `app/` directory
2. The server will automatically reload with your changes
3. Test your changes at http://localhost:8000/docs

## Dependencies

- **FastAPI**: Modern, fast web framework for building APIs
- **Uvicorn**: ASGI web server implementation with performance focus

## Docker Configuration

### Dockerfile

- Base image: `python:3.11-slim`
- Working directory: `/app`
- Exposed port: `8000`
- Entry point: Uvicorn server

### Docker Compose

- Service name: `web`
- Port mapping: `8000:8000`
- Volume mounting for development
- Auto-reload enabled

## License

This project is open source and available under the [MIT License](LICENSE).

## Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Contact

For questions or support, please open an issue in the repository.

---

**Built with FastAPI and Docker**
