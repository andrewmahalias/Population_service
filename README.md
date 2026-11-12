# Population Data Service

A REST API service for retrieving, storing, and serving country population data. The project uses **FastAPI**, **SQLAlchemy**, and **PostgreSQL**, with Docker Compose for containerized deployment.

## Contents

- [Features](#features)
- [Installation and Setup](#installation-and-setup)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Environment Configuration](#environment-configuration)

## Features

- Fetches population data from a public data source.
- Parses and stores population records in PostgreSQL.
- Provides an API built with FastAPI.
- Aggregates population data by region.
- Uses Docker Compose to manage application services and database containers.

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/andrewmagalyas/population_service.git
cd population_service
```

### 2. Start the services

Make sure Docker and Docker Compose are installed.

```bash
docker-compose up -d
```

This starts the application and PostgreSQL database containers.

### 3. Fetch and store population data

```bash
docker-compose up get_data
```

This runs the data collection process, parses the source data, and stores the results in the database.

### 4. Display aggregated population data

```bash
docker-compose up print_data
```

This reads the stored records and displays aggregated population statistics by region.

## Usage

The project provides two main data-processing commands:

- **`get_data`** – Fetches population data from the configured source, parses it, and saves it to PostgreSQL.
- **`print_data`** – Retrieves stored population data and displays regional aggregates.

The FastAPI application exposes the API endpoints defined in `app/routers/data_router.py`.

## Project Structure

```text
population_service/
├── app/
│   ├── routers/
│   │   └── data_router.py
│   ├── __init__.py
│   ├── main.py
│   ├── models.py
│   ├── database.py
│   ├── get_data.py
│   ├── print_data.py
│   └── config.py
├── migrations/
│   ├── versions/
│   └── README
├── README.md
├── docker-compose.yml
├── Dockerfile
└── requirements.txt
```

### Key Components

| File | Description |
|---|---|
| `app/main.py` | Initializes the FastAPI application. |
| `app/routers/data_router.py` | Defines API endpoints. |
| `app/models.py` | Contains SQLAlchemy database models. |
| `app/database.py` | Configures the database connection. |
| `app/get_data.py` | Fetches, parses, and stores population data. |
| `app/print_data.py` | Retrieves and aggregates population data. |
| `app/config.py` | Manages application configuration. |
| `migrations/` | Contains database migration files. |
| `docker-compose.yml` | Defines and manages application services. |
| `Dockerfile` | Defines the Docker image build process. |
| `requirements.txt` | Lists Python dependencies. |

## Environment Configuration

Create a `.env` file in the project root:

```env
DATABASE_URL=postgresql://user:password@postgres/population_db
SOURCE_URL=https://en.wikipedia.org/w/index.php?title=List_of_countries_by_population_(United_Nations)&oldid=1215058959
```

Replace the database credentials with your own configuration.

## Contact

For questions or further information:

**Email:** andrewmahalias@gmail.com
