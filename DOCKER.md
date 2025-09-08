# Docker Setup

This project includes Docker configuration for both development and production environments.

## Environment Variables

The following environment variables are required for the application to function properly:

- `E2B_API_KEY` - API key for E2B code execution service
- `FIRECRAWL_API_KEY` - API key for Firecrawl web scraping service
- `OPENAI_API_KEY` - API key for OpenAI services

## Setup

1. Copy the example environment file:

   ```bash
   cp env.example .env
   ```

2. Edit `.env` and add your actual API keys:
   ```bash
   E2B_API_KEY=your_actual_e2b_api_key
   FIRECRAWL_API_KEY=your_actual_firecrawl_api_key
   OPENAI_API_KEY=your_actual_openai_api_key
   ```

## Running with Docker

### Production

Build and run the production container:

```bash
docker-compose up
```

Or build manually:

```bash
docker build -t open-lovable .
docker run -p 3000:3000 \
  -e E2B_API_KEY=your_key \
  -e FIRECRAWL_API_KEY=your_key \
  -e OPENAI_API_KEY=your_key \
  open-lovable
```

### Development

Run the development container with hot reloading:

```bash
docker-compose --profile dev up
```

### Using Environment File

You can also use a `.env` file with docker-compose:

```bash
# Create .env file with your keys
echo "E2B_API_KEY=your_key" > .env
echo "FIRECRAWL_API_KEY=your_key" >> .env
echo "OPENAI_API_KEY=your_key" >> .env

# Run with docker-compose
docker-compose up
```

## Health Check

The application includes a health check endpoint at `/api/health` that returns the application status and uptime.

## Ports

- Production: `http://localhost:3000`
- Development: `http://localhost:3001`
