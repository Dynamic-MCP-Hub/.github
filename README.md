# Dynamic MCP Hub

A secure, AI-powered API management platform that enables Claude AI to dynamically discover and execute APIs through the Model Context Protocol (MCP).

## What Does It Do?

This project lets you:
- Upload OpenAPI specifications to make APIs available to Claude AI
- Control which clients can access which APIs
- Monitor API usage with detailed audit logs
- Let Claude AI automatically discover and use your APIs without manual tool configuration

## Architecture

The system consists of three integrated components:

### 1. Dashboard ([mcp-dashboard](https://github.com/Dynamic-MCP-Hub/mcp-dashboard))
**Frontend web interface for managing APIs and clients**

- React + TypeScript dashboard
- Admin tools for uploading OpenAPI specs
- Client management and access control
- Real-time audit log viewing
- Vector search powered by Google Vertex AI

### 2. Backend ([mcp-backend](https://github.com/Dynamic-MCP-Hub/mcp-backend))
**Core API server handling authentication, storage, and permissions**

- FastAPI backend with PostgreSQL database
- Manages API collections and client profiles
- Handles authentication via Firebase
- Enforces rate limits and access control
- Tracks audit events
- Provides vector search across API specs

### 3. MCP Server ([mcp-server](https://github.com/Dynamic-MCP-Hub/mcp-server))
**Model Context Protocol server for Claude Desktop**

- Connects to Claude Desktop via MCP protocol
- Dynamically discovers APIs from the backend
- Generates tools automatically from OpenAPI specs
- Executes API calls on behalf of Claude
- Enforces rate limits and logs usage

## How It Works

```
┌─────────────┐
│   Admin     │  Uploads OpenAPI specs & manages access
└──────┬──────┘
       │
       ▼
┌─────────────────┐
│   Dashboard     │  Web UI
│ (mcp-dashboard) │
└────────┬────────┘
         │
         ▼
┌─────────────────┐      ┌──────────────┐
│     Backend     │◄─────┤ PostgreSQL   │
│  (mcp-backend)  │      │   Database   │
└────────┬────────┘      └──────────────┘
         │
         │ Discovers APIs
         ▼
┌─────────────────┐
│   MCP Server    │  Exposes tools to Claude
│  (mcp-server)   │
└────────┬────────┘
         │
         │ MCP Protocol
         ▼
┌─────────────────┐
│ Claude Desktop  │  Uses APIs naturally in conversation
└─────────────────┘
```

## Technology Stack

- **Frontend**: React 18, TypeScript, Tailwind CSS, Firebase Auth
- **Backend**: Python FastAPI, PostgreSQL (Cloud SQL), Firebase Admin SDK
- **MCP Server**: Python FastMCP, Redis, OpenAPI 3.x
- **Infrastructure**: Google Cloud Platform (Cloud Run, Pub/Sub, Vertex AI)

## Key Features

- **Dynamic Tool Generation**: No manual tool configuration - APIs become available automatically
- **Secure Access Control**: Fine-grained permissions per client and API
- **Rate Limiting**: Configurable limits with Redis-backed enforcement
- **Audit Logging**: Complete audit trail of all API calls
- **Vector Search**: AI-powered search across API documentation
- **Stateless Design**: Scalable, cloud-native architecture

## Getting Started

Each component has its own setup instructions:

1. **[Dashboard Setup](./api-vault-guard/README.md)** - Start the web interface
2. **[Backend Setup](./mcp-backend/README.md)** - Launch the API server
3. **[MCP Server Setup](./dynamic-openapi-mcp/README.md)** - Connect Claude Desktop

## Use Cases

- **API Aggregation**: Centralize access to multiple APIs for AI agents
- **Controlled API Access**: Distribute API keys with fine-grained permissions
- **AI-Powered Workflows**: Let Claude orchestrate complex multi-API tasks
- **API Discovery**: Enable semantic search across API collections
- **Usage Monitoring**: Track how AI agents use your APIs

## Development Status

All components are actively developed and deployed on Google Cloud Platform. Each repository maintains its own issue tracker and release cycle.

## License

See individual component repositories for license information.
