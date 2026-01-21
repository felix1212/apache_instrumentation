# Apache APM Trace Instrumentation PoC

This Proof of Concept (PoC) demonstrates Application Performance Monitoring (APM) trace instrumentation for Apache HTTP Server using Datadog.

## Purpose

The primary goal is to test and validate APM tracing capabilities for Apache web server requests, enabling performance monitoring and tracing of HTTP transactions.

## Components

### Docker Compose Setup (`docker-compose.yaml`)
- **Apache Server**: Runs Apache HTTP Server 2.4 with Datadog APM module (`mod_datadog.so`) loaded
- **Datadog Agent**: Collects and forwards APM traces, logs, and metrics to Datadog
- **Network**: Isolated network (`hkjc-lm`) for container communication

### Apache Configuration (`status.conf`)
- Enables Apache's server-status module
- Configures basic authentication for the `/server-status` endpoint
- Provides server performance and connection statistics

### Test Webpage (`public_html/index.html`)
- Simple HTML page served by Apache
- Includes JavaScript functionality test
- Link to Apache server status page
- Displays connection information and local time

## Key Features

- **APM Tracing**: Automatic instrumentation of Apache requests via Datadog module
- **Server Monitoring**: Real-time server status and performance metrics
- **Authentication**: Secure access to sensitive status information
- **Containerized**: Fully containerized setup using Docker Compose

## Usage

1. Ensure Docker and Docker Compose are installed
2. Place the Datadog APM module (`mod_datadog.so`) in the project root
3. Run `docker-compose up` to start the services
4. Access the test page at `http://localhost:8080`
5. View server status at `http://localhost:8080/server-status` (requires authentication: `hkjc` / `pass1234`)
6. Monitor traces and metrics in Datadog dashboard

## Environment Variables

- `DD_SERVICE`: Service name for Datadog (my-apache-service)
- `DD_ENV`: Environment (dev)
- `DD_AGENT_HOST`: Datadog agent hostname (dd-agent)
- `DD_API_KEY`: Datadog API key (configured in compose file)

## Security Notes

- Basic authentication is enabled for server-status endpoint
- Default credentials: username `hkjc`, password `pass1234`
- In production, use stronger authentication and restrict access