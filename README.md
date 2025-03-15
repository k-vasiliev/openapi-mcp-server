# OpenAPI MCP Server for Todoist

This project provides a Model Context Protocol (MCP) server that proxies the Todoist REST API v2. It allows AI models (like Claude or ChatGPT) to interact with your Todoist tasks through a standardized interface.

## Setup

### Prerequisites

- Node.js 16 or higher
- A Todoist account and API token (get it from [Todoist Integrations settings](https://todoist.com/app/settings/integrations))

### Installation

1. Clone this repository
2. Install dependencies:
   ```
   npm install
   ```
3. Build the project:
   ```
   npm run build
   ```

### Configuration

1. Copy `.env.example` to `.env`:
   ```
   cp .env.example .env
   ```
2. Edit `.env` and replace `YOUR_TODOIST_API_TOKEN` with your actual Todoist API token.

## Usage

### Starting the server

Run the server with:

```
npm start
```

This will start the MCP server using the included Todoist OpenAPI specification.

### Connecting to AI Models

The server is designed to work with MCP-compatible AI systems. It provides a standardized interface for models to:

- List available tools (Todoist API endpoints)
- Call specific tools with parameters
- Receive structured responses

## Deployment

### Railway

This project is configured for deployment on Railway. Just connect your repository to Railway, and it will automatically build and deploy.

Make sure to set the `OPENAPI_MCP_HEADERS` environment variable in your Railway project settings with your Todoist API token:

```
{"Authorization":"Bearer YOUR_TODOIST_API_TOKEN"}
```

## Docker

You can also run the application using Docker:

1. Build the Docker image:
   ```
   docker build -t openapi-mcp-server .
   ```

2. Run the container:
   ```
   docker run -p 3000:3000 -e OPENAPI_MCP_HEADERS='{"Authorization":"Bearer YOUR_TODOIST_API_TOKEN"}' openapi-mcp-server
   ```

## Troubleshooting

If the server fails to start or doesn't respond correctly:

1. Check that your Todoist API token is valid and correctly formatted in the environment variable
2. Ensure the OpenAPI specification file is valid and accessible
3. Look for error messages in the console output

## License

MIT
