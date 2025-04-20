# Projet E-Commerce MCP Agent AI

## Description
An e-commerce application integrating a conversational AI agent powered by Anthropic's Claude 3 via Spring AI. The agent helps customers during their shopping journey by providing information about products and services.

## Technologies
- Java 17+
- Spring Boot
- Spring AI
- Anthropic Claude API
- H2 Database (development)
- WebFlux for SSE streaming

## Key Features
- Conversational API to interact with the AI agent
- Support for streaming responses (Server-Sent Events)
- Integration with MCP (Model Context Protocol)
- Customer management tools (search, registration)
- Integrated web testing interface

## Prerequisites
- JDK 17 or higher
- Maven
- Anthropic API key

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/haytamAroui/ecom-mcp-agent-ai.git
cd ecom-mcp-agent-ai
```

### 2. Configure the Anthropic API key
Set your API key as an environment variable:
```bash
# Linux/macOS
export ANTHROPIC_API_KEY=your-api-key

# Windows PowerShell
$env:ANTHROPIC_API_KEY="your-api-key"
```

Or add it in your IDE (IntelliJ):
1. Run > Edit Configurations
2. Environment variables: `ANTHROPIC_API_KEY=your-api-key`

### 3. Build and run
```bash
mvn clean install
mvn spring-boot:run
```

## Usage

### Test Interface
Access the test interface via: http://localhost:8686/test

### REST API
The API exposes two main endpoints:

#### Standard conversation
```http
POST /api/chat
Content-Type: application/json

{
  "question": "What products do you offer?"
}
```

#### Streaming conversation
```http
POST /api/chat/stream
Content-Type: application/json

{
  "question": "Can you recommend a product?"
}
```

## Configuration

The `application.yml` file allows customization of:
- Claude model used (default: claude-3-sonnet-20240229)
- Database configuration
- MCP server parameters
- Logging levels

## Architecture

### Main Components
- `ChatController`: Handles conversation API requests
- `ChatService`: Orchestrates conversations with Claude API
- `CustomerTools`: MCP tools for customer management
- `SpringAiConfig`: Claude model configuration
- `McpAsyncClient`: Model Context Protocol client implementation

### Database
Uses in-memory H2 for development, with console accessible at http://localhost:8686/h2-console

## License
All rights reserved
