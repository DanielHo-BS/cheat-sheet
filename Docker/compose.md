# Docker Compose Cheat Sheet

Here's the cheat sheet about docker compose.

## Common
```bash
# Start containers in detached mode
docker-compose up -d

# Stop and remove containers
docker-compose down

# Build/rebuild services
docker-compose build

# List running containers
docker-compose ps

# Display logs
docker-compose logs

# Execute command in a container
docker-compose exec <service_name> <command>

# Run a one-off command
docker-compose run --rm <service_name> <command>
```

## Compose Watch Mode

### Overview
- Available in Docker Compose **v2.24 and higher**
- Automatically detects file changes and updates containers accordingly
- Reduces development cycle time by automating rebuilds

### Configuration Options

#### Watch Actions
- `rebuild`: Completely rebuilds the image and recreates the container when files change
- `sync`: Performs hot loading by copying changed files directly into the running container without rebuilding
- `build`: Rebuilds the image only but doesn't recreate or restart the containers
- `sync+restart`: Syncs files to the container and then restarts the container (faster than rebuild)

#### Path Configuration
- `path`: Specifies which directory or files to monitor for changes (source location)
- `target`: Defines where synced files should be placed inside the container (destination location)
- Multiple watch configurations can be specified for different paths and actions

### Example Configuration
```yaml
# docker-compose.yml
services:
  app:
    build: .
    command: python app.py
    watch:
      # Rebuild when source code changes
      - path: ./app/src/**/*.py   # Monitor Python source files
        action: rebuild           # Rebuild container when changed
      
      # Hot reload static assets
      - path: ./static            # Monitor static files
        action: sync              # Sync without rebuilding
        target: /app/static       # Destination path in container
        
      # Sync config and restart container
      - path: ./config/*.json     # Monitor config files
        action: sync+restart      # Sync files and restart container
        target: /app/config       # Destination in container
```

### Usage
```bash
# Start services with watch mode enabled
docker compose up --watch

# Run in background with watch mode
docker compose up -d --watch
```

When files in the configured paths change, Docker Compose will automatically perform the specified action (rebuild, sync, or build) without manual intervention.

### Important Requirements for Watch Mode

1. **Required Binaries**  
   The container image must include these utilities:
   - `stat` - For checking file status
   - `mkdir` - For creating directories
   - `rmdir` - For removing directories

2. **User Permissions**  
   The user running in the container must have write permissions for the target directories.
   
   Example in Dockerfile:
   ```dockerfile
   # Set correct permissions
   COPY --chown=appuser:appgroup ./app /app
   
   # Or explicitly set user
   USER appuser
   ```

## Environment Variables

### 1. Using .env File (Auto-loaded)
Docker Compose automatically loads variables from a `.env` file located in the same directory as your `docker-compose.yml` file.

```yaml
# docker-compose.yml
services:
  web:
    image: nginx
    environment:
      - DEBUG=1
      - API_KEY=${API_KEY}  # Value comes from .env file
```

### 2. Using env_file Directive
Explicitly specify environment file(s) to load variables into containers:

```yaml
# docker-compose.yml
services:
  web:
    image: nginx
    env_file:
      - .env
      - ./config/dev.env  # You can specify multiple files
```

### 3. Passing Variables to Dockerfile During Build
When building images with a Dockerfile, environment variables from `.env` aren't automatically available during build time. You need to pass them explicitly:

```bash
# Command line
docker-compose build --build-arg VAR_NAME=value

# In docker-compose.yml
services:
  web:
    build:
      context: .
      args:
        - VAR_NAME=${VAR_NAME}  # Passed to Dockerfile's ARG instruction
```

### 4. Command Line Override
Override or set environment variables directly from command line:

```bash
docker-compose run -e DEBUG=1 -e API_KEY=secret web

# List all environment variables in a running container
docker-compose exec web env
```